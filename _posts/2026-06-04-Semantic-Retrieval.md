---
layout: single
title: "Semantic Retrieval"
---

Every search system faces the same fundamental challenge: a user expresses an information need in a few words, and the system must find the most relevant documents from a corpus that may contain millions—or billions—of items. For decades, keyword matching was the dominant paradigm. But language is ambiguous, synonymous, and context-dependent. The query "how to fix a leaking pipe" and the document titled "plumbing repair guide for dripping faucets" share almost no tokens, yet they address the same need. This is the gap that **semantic retrieval** was built to close.

This article provides a comprehensive guide to modern semantic retrieval systems: from dense embeddings and evaluation methodology, through query expansion and hybrid architectures, to production system design.

---

## 1. What is Semantic Retrieval?

Semantic retrieval is the practice of finding documents based on **meaning** rather than exact word overlap. Instead of matching query tokens against document tokens, semantic retrieval represents both queries and documents as dense vectors in a shared embedding space, then retrieves documents whose vectors are closest to the query vector.

### Dense Embeddings

At the core of semantic retrieval are **dense embeddings**—fixed-length vectors (typically 384 to 1536 dimensions) that encode the semantic content of text. These embeddings are produced by neural encoder models trained on large corpora with contrastive objectives: similar texts are pulled together in the embedding space, while dissimilar texts are pushed apart.

Given an encoder function $$f_\theta$$, the embedding of a text $$x$$ is:

$$\mathbf{e} = f_\theta(x) \in \mathbb{R}^d$$

These models are typically trained with a **contrastive loss** (e.g., InfoNCE):

$$\mathcal{L} = -\log \frac{\exp(\text{sim}(f_\theta(q), f_\theta(d^+)) / \tau)}{\sum_{i=1}^{N} \exp(\text{sim}(f_\theta(q), f_\theta(d_i)) / \tau)}$$

where $$d^+$$ is a positive (relevant) document, $$d_i$$ includes the positive and $$N-1$$ negatives, $$\tau$$ is a temperature parameter, and $$\text{sim}$$ is a similarity function (typically cosine or dot product).

Popular embedding models include:

- **Sentence-BERT (SBERT)** — Reimers & Gurevych, 2019
- **E5** — Wang et al., 2022
- **OpenAI text-embedding-ada-002 / text-embedding-3**
- **Cohere Embed v3**
- **BGE (BAAI General Embedding)** — Xiao et al., 2023

### Semantic Similarity

Once queries and documents are embedded in the same vector space, retrieval reduces to a **nearest-neighbor search**. Common similarity measures include:

- **Cosine similarity**: $$\text{cos}(\mathbf{q}, \mathbf{d}) = \frac{\mathbf{q} \cdot \mathbf{d}}{\|\mathbf{q}\| \|\mathbf{d}\|}$$
- **Dot product**: $$\mathbf{q} \cdot \mathbf{d}$$ (when vectors are normalized, equivalent to cosine)
- **Euclidean distance**: $$\|\mathbf{q} - \mathbf{d}\|_2$$

Approximate nearest neighbor (ANN) algorithms—such as HNSW (Hierarchical Navigable Small World graphs) and IVF (Inverted File Index)—make this search tractable at scale (Malkov & Yashunin, 2018).

### Why Lexical Search Alone is Insufficient

Traditional lexical search (e.g., BM25, TF-IDF) works by matching query terms against document terms. It excels when users know the exact vocabulary used in documents. However, it fails in several scenarios:

**TF-IDF** scores a term $$t$$ in document $$d$$ from corpus $$D$$ as:

$$\text{TF-IDF}(t, d, D) = \text{tf}(t, d) \cdot \log \frac{|D|}{|\{d' \in D : t \in d'\}|}$$

**BM25** extends TF-IDF with saturation and document-length normalization:

$$\text{BM25}(q, d) = \sum_{t \in q} \text{IDF}(t) \cdot \frac{\text{tf}(t, d) \cdot (k_1 + 1)}{\text{tf}(t, d) + k_1 \cdot \left(1 - b + b \cdot \frac{|d|}{\text{avgdl}}\right)}$$

where $$k_1$$ controls term frequency saturation (typically 1.2–2.0), $$b$$ controls length normalization (typically 0.75), and $$\text{avgdl}$$ is the average document length in the corpus. The IDF component is:

$$\text{IDF}(t) = \log \frac{N - n(t) + 0.5}{n(t) + 0.5}$$

where $$N$$ is the total number of documents and $$n(t)$$ is the number of documents containing term $$t$$.

Despite being mathematically well-motivated, these lexical methods fail in several scenarios:

- **Synonym mismatch**: "automobile" vs. "car"
- **Paraphrase mismatch**: "how to lose weight" vs. "strategies for reducing body mass"
- **Conceptual queries**: "why do leaves change color" vs. a document explaining chlorophyll degradation
- **Cross-lingual retrieval**: queries and documents in different languages

Semantic retrieval addresses all of these by operating in a continuous meaning space rather than a discrete token space.

### The Retrieval Pipeline

A modern retrieval pipeline typically consists of multiple stages:

1. **Candidate generation** (retrieval) — fast, high-recall search over the full corpus
2. **Reranking** — slower, higher-precision scoring of top candidates
3. **Post-processing** — deduplication, filtering, business logic

> **Key Insight**: Retrieval systems optimize for *recall* at the first stage and *precision* at later stages. You cannot rerank a document you never retrieved.

---

## 2. Retrieval Evaluation

Evaluating retrieval systems requires measuring both **what** is retrieved and **where** it appears in the ranked list.

### Recall@K

Recall@K measures the fraction of relevant documents that appear in the top K results:

$$\text{Recall@K} = \frac{|\text{relevant documents in top K}|}{|\text{total relevant documents}|}$$

**Example**: If there are 5 relevant documents for a query and 3 appear in the top 10 results, then Recall@10 = 3/5 = 0.6.

Recall@K is the primary metric for the **candidate generation** stage because the reranker can only improve the ordering of documents that were already retrieved.

### Mean Reciprocal Rank (MRR)

MRR measures how high the *first* relevant result appears:

$$\text{MRR} = \frac{1}{|Q|} \sum_{i=1}^{|Q|} \frac{1}{\text{rank}_i}$$

where $$\text{rank}_i$$ is the position of the first relevant document for query $$i$$.

**Example**: For three queries where the first relevant result appears at positions 1, 3, and 5:

$$\text{MRR} = \frac{1}{3}\left(\frac{1}{1} + \frac{1}{3} + \frac{1}{5}\right) = \frac{1}{3}(1 + 0.33 + 0.2) = 0.51$$

MRR is particularly important for systems where users primarily look at the top result (e.g., question answering, autocomplete).

### Latency Percentiles

Retrieval latency is measured in percentiles rather than averages because tail latency matters:

| Percentile | Meaning |
|-----------|---------|
| p50 | Median latency — half of requests are faster |
| p90 | 90% of requests complete within this time |
| p95 | Only 5% of requests are slower |
| p99 | Tail latency — worst-case (excluding extreme outliers) |

**Why percentiles matter**: An average latency of 50ms might hide that 5% of users experience 500ms+ latency. Production systems typically set SLOs (Service Level Objectives) on p95 or p99.

### Ranking Quality vs. Retrieval Quality

These are distinct measurements:

- **Retrieval quality** (Recall@K): Did we find the relevant documents at all?
- **Ranking quality** (MRR, NDCG): Are the relevant documents near the top?

**Normalized Discounted Cumulative Gain (NDCG@K)** is a standard ranking metric that accounts for graded relevance and position:

$$\text{DCG@K} = \sum_{i=1}^{K} \frac{2^{\text{rel}_i} - 1}{\log_2(i + 1)}$$

$$\text{NDCG@K} = \frac{\text{DCG@K}}{\text{IDCG@K}}$$

where $$\text{rel}_i$$ is the relevance grade of the document at position $$i$$, and $$\text{IDCG@K}$$ is the DCG of the ideal (perfectly sorted) ranking. NDCG ranges from 0 to 1, where 1 means the ranking is optimal.

**Average Precision (AP)** for a single query considers both precision and recall at every rank position where a relevant document is found:

$$\text{AP} = \frac{1}{|\text{Rel}|} \sum_{k=1}^{n} P(k) \cdot \text{rel}(k)$$

where $$P(k)$$ is precision at rank $$k$$, $$\text{rel}(k)$$ is 1 if the document at rank $$k$$ is relevant (0 otherwise), and $$|\text{Rel}|$$ is the total number of relevant documents. **Mean Average Precision (MAP)** averages AP across all queries.

A system with high recall but low MRR retrieves relevant documents but buries them in the list. A system with high MRR but low recall finds a few relevant documents quickly but misses others. Both dimensions must be measured independently.

> **Key Insight**: Improving retrieval (recall) and improving ranking (precision/ordering) often require different techniques and should be evaluated separately.

---

## 3. Evaluation Dataset Design

The quality of your evaluation directly determines the quality of your retrieval system. Poorly designed benchmarks lead to misleading conclusions.

### Hard Evaluation Sets

A **hard evaluation set** contains queries paired with relevant documents that are semantically similar but lexically distinct, or documents that are lexically similar but semantically different (hard negatives).

**Purpose**: Tests whether the system truly understands meaning rather than relying on surface-level token overlap.

**Example hard negative**: For the query "Python memory management," a hard negative might be "Python snake habitat management"—lexically similar but semantically irrelevant.

### Paraphrase Evaluation Sets

A **paraphrase evaluation set** contains queries that are rewordings of each other, paired with the same relevant documents.

**Purpose**: Tests whether the system retrieves the same documents regardless of how the query is phrased.

**Example**:
- "How do I reset my password?" → should retrieve the same document as
- "I forgot my login credentials, what do I do?"

### Exact-Token Evaluation Sets

An **exact-token evaluation set** contains queries where the relevant document contains the exact query terms (e.g., product names, error codes, identifiers).

**Purpose**: Tests whether the system preserves exact-match capability alongside semantic understanding.

**Example**: The query "error code 0x80070005" must retrieve documents containing that exact string—semantic similarity alone may not surface it.

### Why Different Techniques Excel on Different Benchmarks

| Evaluation Type | Dense Retrieval | Lexical Retrieval | Hybrid |
|----------------|-----------------|-------------------|--------|
| Hard (semantic) | ✓✓✓ | ✗ | ✓✓ |
| Paraphrase | ✓✓✓ | ✗ | ✓✓ |
| Exact-token | ✗ | ✓✓✓ | ✓✓✓ |

This is why reporting a single aggregate metric can be misleading. A system that scores 90% overall might completely fail on exact-token queries—which could be the most critical use case for your users.

### Common Benchmark Pitfalls

- **Leakage**: Training data overlapping with evaluation data
- **Distribution mismatch**: Evaluating on academic benchmarks but deploying on domain-specific queries
- **Lack of hard negatives**: Easy benchmarks where any reasonable system scores well
- **Single-metric reporting**: Hiding weaknesses behind aggregate numbers

---

## 4. Baseline Retrieval Systems

Before adding complexity, establish a strong baseline. Many sophisticated techniques provide only marginal improvements over well-tuned baselines.

### Single-Vector Retrieval

The simplest dense retrieval system:

1. Encode each document into a single embedding vector
2. Store vectors in an ANN index (e.g., FAISS, Pinecone, Weaviate, Qdrant)
3. At query time, encode the query and find the K nearest vectors

**Exact nearest-neighbor search** requires computing similarity to all $$N$$ documents:

$$d^* = \arg\max_{d \in \mathcal{D}} \text{sim}(\mathbf{q}, \mathbf{d})$$

This has $$O(N \cdot d)$$ complexity (where $$d$$ is the embedding dimension), which is prohibitive for large corpora.

**Approximate nearest neighbor (ANN)** methods trade a small amount of recall for dramatic speedup. HNSW achieves $$O(\log N)$$ query time with high recall (typically > 0.95). IVF partitions the space into $$\sqrt{N}$$ Voronoi cells and searches only the $$n_{\text{probe}}$$ nearest cells, achieving sub-linear query time:

$$O(n_{\text{probe}} \cdot N / \sqrt{N}) = O(n_{\text{probe}} \cdot \sqrt{N})$$

This approach is fast, simple, and surprisingly effective for many use cases.

### Candidate Generation

Candidate generation is the first stage of retrieval. Its job is to reduce the search space from millions of documents to hundreds or thousands of candidates with **high recall**. Speed is prioritized over precision.

Common approaches:
- ANN search over dense embeddings
- BM25 over inverted indexes
- Multiple retrieval paths combined (see Hybrid Retrieval below)

### Deduplication

Real-world corpora contain near-duplicate documents. Deduplication at retrieval time prevents the top-K results from being dominated by copies of the same content.

Techniques include:
- **MinHash / LSH** for approximate deduplication
- **Embedding similarity threshold** — collapse documents above a cosine similarity of, e.g., 0.95
- **URL/ID-based deduplication** for web corpora

The **Jaccard similarity** between two document shingle sets $$A$$ and $$B$$ is commonly used to detect near-duplicates:

$$J(A, B) = \frac{|A \cap B|}{|A \cup B|}$$

MinHash provides an efficient approximation: by hashing shingle sets with $$k$$ independent hash functions, the probability that two documents share a MinHash signature equals their Jaccard similarity:

$$P[h_{\min}(A) = h_{\min}(B)] = J(A, B)$$

Documents with $$J(A, B) > \theta$$ (typically $$\theta = 0.8$$) are considered near-duplicates.

### Retrieval vs. Ranking

| Aspect | Retrieval (Stage 1) | Ranking (Stage 2) |
|--------|---------------------|-------------------|
| Corpus size | Millions–billions | Hundreds–thousands |
| Latency budget | < 50ms | < 200ms |
| Model complexity | Bi-encoder (independent encoding) | Cross-encoder (joint encoding) |
| Primary metric | Recall@K | NDCG, MRR |
| Tradeoff | Speed for coverage | Accuracy for latency |

### Why Baselines Matter

Baselines serve three purposes:

1. **Sanity check** — ensures more complex systems actually improve over simple ones
2. **Cost comparison** — the marginal improvement may not justify the added complexity/cost
3. **Failure analysis** — comparing outputs to baseline helps diagnose *why* a new approach fails

> **Key Insight**: Always measure your fancy new technique against BM25 + a good embedding model. You might be surprised how often the baseline wins.

---

## 5. Query Expansion with LLMs

Users often write short, ambiguous queries. **Query expansion** enriches the original query with additional terms or reformulations to improve recall.

### Query Rewriting

An LLM rewrites the user's query into a more complete, unambiguous form:

- Original: "apple not charging"
- Rewritten: "Apple MacBook laptop not charging when plugged in, battery issue"

### Paraphrase Generation

Generate multiple phrasings of the same query and retrieve documents for each:

- "machine learning deployment best practices"
- "how to put ML models into production"
- "serving trained models at scale"

Union the results to improve recall. Formally, given $$m$$ query variants $$\{q_1, q_2, \ldots, q_m\}$$, the expanded result set is:

$$\mathcal{R}_{\text{expanded}} = \bigcup_{i=1}^{m} \text{TopK}(q_i, \mathcal{D})$$

The theoretical recall upper bound increases with $$m$$, but with diminishing returns. If each variant independently retrieves relevant documents with probability $$p$$, the probability of missing a relevant document across $$m$$ variants is $$(1-p)^m$$, giving expected recall:

$$\text{Recall}_m = 1 - (1 - p)^m$$

### Acronym and Synonym Expansion

- "NLP" → "natural language processing"
- "k8s" → "Kubernetes"
- "CV" → "computer vision" OR "curriculum vitae" (disambiguation!)

### Open-Vocabulary Retrieval Challenges

Embedding models are trained on fixed vocabularies. Novel terms, brand names, and domain jargon may not have good representations. LLM expansion helps by generating descriptions or definitions that *do* map well in embedding space.

### Benefits and Limitations

| Aspect | Benefit | Limitation |
|--------|---------|------------|
| Recall | Significantly improved | May introduce drift (irrelevant expansions) |
| Precision | Can improve via disambiguation | Risk of topic drift |
| Latency | — | Adds 100–500ms+ (LLM inference) |
| Cost | — | LLM API calls at query time |
| Robustness | Handles ambiguity | Hallucinated expansions possible |

### Practical Considerations

- **Caching**: Common queries can have expansions precomputed
- **Lightweight models**: Smaller LLMs or fine-tuned T5 models reduce latency
- **Selective expansion**: Only expand queries that perform poorly on the first retrieval attempt
- **Fusion**: Combine results from original and expanded queries (see RRF below)

---

## 6. Pseudo-Relevance Feedback (PRF)

Pseudo-Relevance Feedback is a classical technique that refines a query based on the assumption that top-retrieved documents are relevant. It predates LLMs by decades but remains highly effective.

### The Intuition

1. Issue the original query
2. Assume the top-K retrieved documents are relevant (the "pseudo-relevance" assumption)
3. Use information from those documents to refine the query
4. Re-issue the refined query

The key insight: even if the original query is imperfect, the top results likely contain useful signal about what the user wants.

### The Rocchio Algorithm

The Rocchio algorithm (Rocchio, 1971) is the most well-known PRF method. Originally developed for vector-space models, it adapts naturally to dense embeddings.

**Mathematical Formulation**:

$$\mathbf{q}_{new} = \alpha \cdot \mathbf{q}_{orig} + \beta \cdot \frac{1}{|D_r|} \sum_{\mathbf{d} \in D_r} \mathbf{d} - \gamma \cdot \frac{1}{|D_{nr}|} \sum_{\mathbf{d} \in D_{nr}} \mathbf{d}$$

Where:
- $$\mathbf{q}_{orig}$$ — original query vector
- $$D_r$$ — set of (assumed) relevant documents
- $$D_{nr}$$ — set of (assumed) non-relevant documents
- $$\alpha$$ — weight of original query (typically 0.5–1.0)
- $$\beta$$ — weight of relevant documents (typically 0.5–0.8)
- $$\gamma$$ — weight of non-relevant documents (typically 0.1–0.2, often set to 0)

### Feedback Vectors and Centroids

In embedding space, the centroid of the top-K document vectors represents the "average meaning" of the initial results. The refined query vector is shifted toward this centroid:

$$\mathbf{q}_{refined} = \alpha \cdot \mathbf{q} + \beta \cdot \text{centroid}(D_{top-K})$$

This is the simplified Rocchio formulation with $$\gamma = 0$$ (ignoring non-relevant documents), which is common in practice.

### Parameter Tuning

| Parameter | Effect of Increasing | Typical Range |
|-----------|---------------------|---------------|
| $$\alpha$$ | More weight on original query intent | 0.5 – 1.0 |
| $$\beta$$ | More influence from retrieved documents | 0.3 – 0.8 |
| $$\gamma$$ | More aggressive avoidance of non-relevant topics | 0.0 – 0.2 |
| K (feedback docs) | More diverse signal but higher noise risk | 3 – 10 |

### Strengths and Weaknesses vs. LLM Expansion

| Dimension | PRF | LLM Expansion |
|-----------|-----|---------------|
| Latency | Low (vector arithmetic) | High (LLM inference) |
| Cost | Negligible | API call per query |
| Recall improvement | Moderate | High |
| Risk of drift | Moderate (topic drift if top-K irrelevant) | Moderate (hallucination) |
| Domain adaptation | Adapts via corpus | Requires prompt engineering |
| Interpretability | High (vector operations) | Low (black box) |

> **Key Insight**: PRF is essentially "free" at inference time—it only requires vector arithmetic on already-retrieved results. It's an excellent complement to more expensive techniques.

---

## 7. Hybrid Retrieval

No single retrieval method excels at everything. **Hybrid retrieval** combines multiple retrieval signals—typically dense (semantic) and sparse (lexical)—to cover each other's weaknesses.

### Dense Retrieval

Uses embedding vectors to find semantically similar documents. Excels at:
- Paraphrase matching
- Conceptual queries
- Cross-lingual retrieval

Struggles with:
- Exact token matching (product codes, error numbers)
- Rare terms not well-represented in embedding space
- Highly specific named entities

### Lexical Retrieval and Full-Text Search

Uses term-based matching (BM25, TF-IDF). Excels at:
- Exact keyword matching
- Rare terms and identifiers
- Known-item search (when users know exactly what they want)

Struggles with:
- Synonyms and paraphrases
- Conceptual queries
- Vocabulary mismatch

### Sparse vs. Dense Representations

| Property | Sparse (Lexical) | Dense (Semantic) |
|----------|-------------------|------------------|
| Vector dimensionality | Vocabulary size (10K–100K+) | Fixed (384–1536) |
| Vector density | Mostly zeros | All dimensions active |
| Similarity basis | Token overlap | Learned semantics |
| Index type | Inverted index | ANN index |
| Exact match | Excellent | Poor |
| Semantic match | Poor | Excellent |

### Inverted Indexes and GIN Indexes

**Inverted indexes** map each token to the list of documents containing it. They are the backbone of lexical search (Elasticsearch, Lucene, Solr).

**GIN (Generalized Inverted Index)** indexes in PostgreSQL provide similar functionality for full-text search within relational databases, supporting tsvector/tsquery operations efficiently.

### Why Exact Tokens are Difficult for Dense Embeddings

Dense embedding models compress text into fixed-dimensional vectors. This compression necessarily loses fine-grained token-level information. Mathematically, an encoder maps variable-length text to a fixed-size vector:

$$f: \mathcal{V}^* \rightarrow \mathbb{R}^d$$

where $$\mathcal{V}^*$$ is the set of all possible token sequences. This mapping is necessarily lossy—you cannot preserve all token-level information in a fixed $$d$$-dimensional space (by the pigeonhole principle, when $$|\mathcal{V}^*| \gg \mathbb{R}^d$$).

The embedding for "error 0x80070005" may be close to "Windows error code" in general, but it cannot distinguish it from "error 0x80070002" because the model doesn't memorize arbitrary character sequences—it encodes *meaning*.

**Learned sparse representations** (e.g., SPLADE) attempt to bridge this gap by learning sparse, high-dimensional vectors where each dimension corresponds to a vocabulary term:

$$\mathbf{w}_d = \max_{t \in d}\left(\log(1 + \text{ReLU}(W \cdot h_t + b))\right) \in \mathbb{R}^{|\mathcal{V}|}$$

This produces a sparse vector with non-zero weights for semantically relevant terms—including terms not present in the original text—combining the benefits of learned representations with the exact-match capability of inverted indexes.

This is the fundamental reason hybrid systems exist: dense retrieval handles meaning, lexical retrieval handles identity.

---

## 8. Reciprocal Rank Fusion (RRF)

When combining results from multiple retrieval systems, how do you merge their ranked lists? **Reciprocal Rank Fusion** (Cormack et al., 2009) provides an elegant solution.

### Why Score Normalization is Difficult

Different retrieval systems produce scores on different scales:
- BM25 scores might range from 0 to 25
- Cosine similarity ranges from -1 to 1
- A reranker might produce logits from -10 to 10

A naive weighted combination:

$$s_{\text{hybrid}}(q, d) = \lambda \cdot s_{\text{dense}}(q, d) + (1 - \lambda) \cdot s_{\text{sparse}}(q, d)$$

requires normalizing both scores to a comparable range. Common normalization approaches include:

**Min-max normalization** per query:

$$\hat{s}(d) = \frac{s(d) - \min_{d' \in \mathcal{R}} s(d')}{\max_{d' \in \mathcal{R}} s(d') - \min_{d' \in \mathcal{R}} s(d')}$$

**Z-score normalization**:

$$\hat{s}(d) = \frac{s(d) - \mu_s}{\sigma_s}$$

Both are fragile because:
- Score distributions differ across queries
- The relationship between score and relevance differs across systems
- Outliers can distort normalization

### How RRF Works

RRF ignores scores entirely and uses only **ranks**:

$$\text{RRF}(d) = \sum_{r \in R} \frac{1}{k + r(d)}$$

Where:
- $$R$$ — set of ranked lists being fused
- $$r(d)$$ — rank of document $$d$$ in list $$r$$ (starting from 1)
- $$k$$ — constant that mitigates the impact of high rankings (typically 60)

Documents are sorted by their RRF score in descending order.

### Worked Example

Suppose we have two retrieval systems and their top-5 results for a query:

**Dense retrieval ranked list**: [A, B, C, D, E]

**Lexical retrieval ranked list**: [C, F, A, G, B]

Computing RRF scores (k = 60):

| Document | Dense Rank | Lexical Rank | RRF Score |
|----------|-----------|-------------|-----------|
| A | 1 | 3 | 1/61 + 1/63 = 0.0164 + 0.0159 = **0.0323** |
| B | 2 | 5 | 1/62 + 1/65 = 0.0161 + 0.0154 = **0.0315** |
| C | 3 | 1 | 1/63 + 1/61 = 0.0159 + 0.0164 = **0.0323** |
| D | 4 | — | 1/64 + 0 = **0.0156** |
| E | 5 | — | 1/65 + 0 = **0.0154** |
| F | — | 2 | 0 + 1/62 = **0.0161** |
| G | — | 4 | 0 + 1/64 = **0.0156** |

**Final fused ranking**: A ≈ C > B > F > D ≈ G > E

Documents that appear in *both* lists (A, B, C) are boosted. Document A and C tie because they hold rank 1 and 3 in opposite lists.

### Advantages Over Score-Based Fusion

- **No calibration needed** — works regardless of score scales
- **Robust** — a single system giving anomalous scores doesn't dominate
- **Simple** — easy to implement and debug
- **Effective** — consistently strong performance across diverse settings (Cormack et al., 2009)

---

## 9. Reranking

Retrieval finds candidates; **reranking** puts the best ones on top.

### Candidate Generation vs. Reranking

The retrieval stage uses efficient models (bi-encoders) that encode queries and documents *independently*. This enables fast ANN search but limits the model's ability to capture fine-grained query-document interactions.

**Bi-encoder scoring**:

$$s_{\text{bi}}(q, d) = \text{sim}(f_\theta(q), g_\phi(d)) = \frac{f_\theta(q) \cdot g_\phi(d)}{\|f_\theta(q)\| \|g_\phi(d)\|}$$

The key property is that document embeddings $$g_\phi(d)$$ can be precomputed and indexed offline—only the query needs to be encoded at search time.

Rerankers use **cross-encoders** that process the query and document *jointly*, allowing deep token-level interactions. This is far more accurate but too slow to run over millions of documents.

**Cross-encoder scoring**:

$$s_{\text{cross}}(q, d) = \sigma\left(W \cdot \text{BERT}([q; \text{[SEP]}; d])_{\text{[CLS]}} + b\right)$$

where the query and document are concatenated as input, allowing full cross-attention between all query and document tokens. The $$\text{[CLS]}$$ token representation captures the joint interaction and is projected to a relevance score via a learned linear layer.

### Cross-Encoders and LLM Rerankers

**Cross-encoders** (e.g., based on BERT or similar transformers) take the concatenated [query; document] pair as input and output a relevance score. They can attend to fine-grained interactions between query and document tokens.

**LLM rerankers** use large language models to assess relevance, either through:
- **Pointwise scoring**: "Rate the relevance of this document to this query on a scale of 1-5"
- **Listwise ranking**: "Rank these documents by relevance to the query"
- **Pairwise comparison**: "Which document is more relevant to this query?"

Examples include Cohere Rerank, RankGPT (Sun et al., 2023), and fine-tuned models like BGE-Reranker.

### Why Reranking Improves Precision

Cross-encoders can capture:
- **Negation**: "cars that are NOT electric" — a bi-encoder might retrieve electric car documents
- **Specificity**: distinguish between a general overview and a detailed technical guide
- **Context-dependent relevance**: whether a passage actually *answers* the query vs. merely *mentioning* the topic

### Latency and Cost Tradeoffs

| Approach | Latency per Document | Typical Budget | Documents Scored |
|----------|---------------------|----------------|-----------------|
| Bi-encoder retrieval | ~0.01ms | < 50ms total | Millions (via ANN) |
| Cross-encoder rerank | ~5–20ms | < 200ms total | 10–100 candidates |
| LLM rerank | ~50–200ms | < 1–2s total | 10–30 candidates |

### Common Reranking Architectures

1. **Single-stage rerank**: Retrieve K candidates → Rerank with cross-encoder → Return top N
2. **Cascading rerank**: Retrieve 1000 → Light reranker (top 100) → Heavy reranker (top 10)
3. **Hybrid + rerank**: Dense retrieval + Lexical retrieval → RRF fusion → Rerank top candidates

### Late Interaction: ColBERT

ColBERT (Khattab & Zaharia, 2020) represents a middle ground between bi-encoders and cross-encoders using **late interaction**. Each query token and document token gets its own embedding, and relevance is computed via the **MaxSim** operator:

$$s_{\text{ColBERT}}(q, d) = \sum_{i=1}^{|q|} \max_{j=1}^{|d|} \mathbf{q}_i \cdot \mathbf{d}_j$$

For each query token embedding $$\mathbf{q}_i$$, find the maximum similarity to any document token embedding $$\mathbf{d}_j$$, then sum across all query tokens. This preserves token-level interaction while allowing document representations to be precomputed—achieving better quality than bi-encoders with much lower latency than cross-encoders.

---

## 10. Designing Production Retrieval Systems

Building a retrieval system for production requires balancing quality, cost, and latency under real-world constraints.

### Cost vs. Quality Tradeoffs

| Component | Cost Driver | Quality Impact |
|-----------|-------------|----------------|
| Embedding model | GPU inference, API calls | Embedding quality determines retrieval ceiling |
| Vector index | RAM/storage, index rebuild time | Index type affects recall |
| Query expansion | LLM API calls per query | +5–15% recall improvement |
| Reranking | Cross-encoder inference | +10–20% NDCG improvement |
| Hybrid retrieval | Maintaining two indexes | Covers more query types |

### Latency Budgets

A typical production system might allocate:

- **Total budget**: 500ms (p95)
- Embedding query: 20ms
- ANN search: 30ms
- BM25 search: 20ms
- RRF fusion: 5ms
- Reranking (top 50): 150ms
- Post-processing: 25ms
- **Total**: ~250ms (with headroom for variance)

The total end-to-end latency for a multi-stage pipeline with $$S$$ sequential stages is:

$$T_{\text{total}} = \sum_{s=1}^{S} T_s + T_{\text{network}}$$

For stages that can run in parallel (e.g., dense and sparse retrieval simultaneously):

$$T_{\text{parallel}} = \max(T_{\text{dense}}, T_{\text{sparse}}) + T_{\text{fusion}} + T_{\text{rerank}}$$

The cost-per-query for a reranking stage scoring $$n$$ candidates with a model of inference cost $$c$$ per document:

$$\text{Cost}_{\text{rerank}} = n \cdot c$$

This makes the choice of $$n$$ (how many candidates to rerank) a direct tradeoff between quality and cost.

### Multi-Stage Retrieval Architectures

Production systems typically use a **funnel architecture**:

```
Full Corpus (millions)
    ↓ Candidate Generation (ANN + BM25)
Top 500-1000 candidates
    ↓ Lightweight Reranker
Top 50-100 candidates
    ↓ Heavy Reranker / LLM
Top 10-20 results
    ↓ Business Logic & Filtering
Final results presented to user
```

Each stage reduces the candidate set while increasing scoring quality.

### When to Use Semantic Search

Semantic search is most valuable when:
- Users express needs in natural language (not exact keywords)
- The corpus uses varied vocabulary for similar concepts
- Cross-lingual retrieval is needed
- Query-document vocabulary mismatch is common

### When Hybrid Retrieval is Preferable

Add lexical retrieval alongside semantic when:
- The corpus contains identifiers, codes, or exact-match content
- Users frequently search for specific named entities
- Exact recall on known items is critical
- The embedding model doesn't cover domain-specific vocabulary well

### When Reranking is Worth the Cost

Invest in reranking when:
- The top-K results from retrieval contain many relevant documents but in poor order
- Precision at the top (MRR, NDCG@5) is more important than recall
- The latency budget allows an additional 100–200ms
- The use case is sensitive to incorrect top results (e.g., customer-facing search, RAG pipelines)

> **Key Insight**: Start simple. A well-tuned BM25 + single dense retrieval + RRF fusion is a remarkably strong baseline. Add complexity (query expansion, PRF, reranking) only when evaluation shows clear gaps.

---

## Summary

Modern semantic retrieval is not a single algorithm but a **system of systems**. The most effective retrieval architectures combine:

1. **Dense embeddings** for semantic understanding
2. **Lexical retrieval** for exact-match precision
3. **Hybrid fusion** (RRF) to combine diverse signals
4. **Query expansion** (LLM or PRF) to handle ambiguity
5. **Reranking** to maximize precision at the top

The key principles to remember:

- **Measure separately**: Recall and ranking quality are distinct. Evaluate them independently.
- **Design evaluations carefully**: Your benchmark determines what you optimize for.
- **Start with baselines**: Simple systems are surprisingly strong.
- **Add complexity incrementally**: Each component should demonstrably improve metrics on your evaluation set.
- **Budget for latency**: Every technique has a latency cost. Design within your SLO.

The field continues to evolve rapidly. Late-interaction models (ColBERT), learned sparse retrieval (SPLADE), and multi-vector representations are pushing the boundaries further. But the fundamentals covered here—embedding, retrieval, fusion, and reranking—form the foundation that all advanced techniques build upon.

---

## Suggested Diagrams and Visualizations

For each major section, the following visuals would enhance understanding:

1. **Semantic Retrieval Architecture** — A flow diagram showing query → embedding → ANN index → candidates → reranker → results. *Source: Adapt from Pinecone's retrieval architecture diagrams or create original.*

2. **Dense vs. Sparse Retrieval Comparison** — Side-by-side showing a query matched against documents via token overlap (sparse) vs. vector proximity (dense). *Source: Adapt from Weaviate's hybrid search documentation.*

3. **Rocchio Feedback Visualization** — 2D embedding space showing original query vector, top-K document vectors, their centroid, and the refined query vector shifted toward the centroid. *Source: Create original based on Manning et al., Introduction to Information Retrieval, Figure 9.3.*

4. **Reciprocal Rank Fusion Example** — Visual showing two ranked lists being merged into a single fused list, with RRF scores annotated. *Source: Create original.*

5. **Multi-Stage Retrieval Pipeline** — Funnel diagram showing corpus → candidates → reranked → final results with latency budgets at each stage. *Source: Adapt from Google's multi-stage retrieval illustrations.*

6. **Recall vs. MRR Illustration** — Two result lists side by side: one with high recall but low MRR (relevant docs scattered), one with lower recall but high MRR (fewer relevant docs but all at top). *Source: Create original.*

7. **Candidate Generation and Reranking Flow** — Diagram contrasting bi-encoder (independent encoding) with cross-encoder (joint encoding) architectures. *Source: Adapt from Sentence-BERT paper (Reimers & Gurevych, 2019), Figure 1.*

---

## References

1. Cormack, G. V., Clarke, C. L. A., & Buettcher, S. (2009). Reciprocal Rank Fusion outperforms Condorcet and individual Rank Learning Methods. *Proceedings of SIGIR 2009*.

2. Karpukhin, V., Oğuz, B., Min, S., Lewis, P., Wu, L., Edunov, S., Chen, D., & Yih, W. (2020). Dense Passage Retrieval for Open-Domain Question Answering. *Proceedings of EMNLP 2020*.

3. Khattab, O., & Zaharia, M. (2020). ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction over BERT. *Proceedings of SIGIR 2020*.

4. Malkov, Y. A., & Yashunin, D. A. (2018). Efficient and Robust Approximate Nearest Neighbor Search Using Hierarchical Navigable Small World Graphs. *IEEE Transactions on Pattern Analysis and Machine Intelligence*.

5. Manning, C. D., Raghavan, P., & Schütze, H. (2008). *Introduction to Information Retrieval*. Cambridge University Press.

6. Reimers, N., & Gurevych, I. (2019). Sentence-BERT: Sentence Embeddings using Siamese BERT-Networks. *Proceedings of EMNLP 2019*.

7. Robertson, S. E., & Zaragoza, H. (2009). The Probabilistic Relevance Framework: BM25 and Beyond. *Foundations and Trends in Information Retrieval*.

8. Rocchio, J. J. (1971). Relevance Feedback in Information Retrieval. In G. Salton (Ed.), *The SMART Retrieval System: Experiments in Automatic Document Processing*. Prentice-Hall.

9. Sun, W., Yan, L., Ma, X., Ren, P., Yin, D., & Ren, Z. (2023). Is ChatGPT Good at Search? Investigating Large Language Models as Re-Ranking Agents. *Proceedings of EMNLP 2023*.

10. Wang, L., Yang, N., Huang, X., Jiao, B., Yang, L., Jiang, D., Majumder, R., & Wei, F. (2022). Text Embeddings by Weakly-Supervised Contrastive Pre-training. *arXiv preprint arXiv:2212.03533*.

11. Xiao, S., Liu, Z., Zhang, P., & Muennighoff, N. (2023). C-Pack: Packaged Resources To Advance General Chinese Embedding. *arXiv preprint arXiv:2309.07597*.

12. Formal, T., Piwowarski, B., & Clinchant, S. (2021). SPLADE: Sparse Lexical and Expansion Model for First Stage Ranking. *Proceedings of SIGIR 2021*.

---

## Further Reading

- **MTEB Leaderboard** — Massive Text Embedding Benchmark for comparing embedding models: [huggingface.co/spaces/mteb/leaderboard](https://huggingface.co/spaces/mteb/leaderboard)

- **BEIR Benchmark** — Heterogeneous benchmark for zero-shot evaluation of retrieval models: Thakur et al., 2021. [github.com/beir-cellar/beir](https://github.com/beir-cellar/beir)

- **Pinecone Learning Center** — Practical guides on vector search and retrieval: [pinecone.io/learn](https://www.pinecone.io/learn/)

- **Weaviate Blog** — Technical articles on hybrid search and vector databases: [weaviate.io/blog](https://weaviate.io/blog)

- **Pretrained Transformers for Text Ranking: BERT and Beyond** (Lin et al., 2021) — Comprehensive survey of neural ranking methods.

- **ColBERTv2** (Santhanam et al., 2022) — Efficient late-interaction retrieval pushing the quality-latency frontier.

- **RAG Survey** (Gao et al., 2023) — Retrieval-Augmented Generation: connecting retrieval to LLM generation.

- **The Anatomy of a Large-Scale Hypertextual Web Search Engine** (Brin & Page, 1998) — Foundational work on web-scale retrieval architecture.
