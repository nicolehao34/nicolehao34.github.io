---
layout: single
title: "Compute Power, Geopolitics, and the AI Race"
---

In the AI boom, the NVIDIA H100 has become more than a chip. It has become a symbol of power — and an instrument of geopolitics.

A single H100 GPU can cost tens of thousands of dollars. In 2024, Elon Musk's xAI built Colossus, a supercomputer initially reported to run on 100,000 H100s to train Grok [1]. That image — rows of racks filled with elite chips — has come to represent the dominant belief of the AI era: whoever controls the most compute controls the future. The United States has taken that belief seriously enough to ban exports of H100s to China entirely.

But is AI really just a compute war? Compute matters enormously — without it, you cannot train frontier models, serve billions of users, or run advanced reasoning systems at scale. But the history of AI shows that hardware alone does not decide the outcome. The real race spans hardware, algorithms, data, industrial deployment, and the geopolitical contest over who can access the tools to do any of it.

---

## The H100 as the "Energy Source" of AI

To understand why GPUs matter so much, start with what they do.

Large AI models are built from enormous numbers of parameters: adjustable values learned during training. The more parameters a model has, the more knowledge, patterns, and relationships it can potentially encode. Training these models requires vast numbers of matrix operations, which GPUs are especially good at performing in parallel.

The NVIDIA H100 was designed for exactly this world. Based on NVIDIA's Hopper architecture, the H100 contains roughly 80 billion transistors and up to 144 streaming multiprocessors [2]. In systems like the NVIDIA DGX H100, eight H100 GPUs are connected with high-speed memory and networking to form an enterprise AI machine [3]. Scale those machines into racks, then into entire facilities, and you get the data center powering frontier AI.

But a data center is not just GPUs. It also needs power delivery, backup systems, cooling, networking, optical modules, storage, circuit boards, switches, and orchestration software. This is why AI is increasingly an industrial revolution rather than just a software revolution. The GPU is the glamorous component, but the real machine is the full stack.

---

## Why DeepSeek Challenged the "Compute Is Everything" Story

For several years, the consensus was simple: without access to top-tier NVIDIA chips, no company or country could compete with OpenAI, Google, Anthropic, or Meta.

Then DeepSeek complicated that story.

DeepSeek's V3 and R1 models showed that algorithmic efficiency could dramatically change the cost structure of building competitive models. DeepSeek-V3's technical report estimated its training compute cost at about $5.576 million, far below many public estimates for leading closed models [4]. DeepSeek-R1 then demonstrated strong reasoning performance and released open-weight distilled models, giving developers around the world access to reasoning-style capabilities at much lower cost [5].

The important lesson is not that compute no longer matters. It is that better algorithms can change the compute equation.

DeepSeek's work leaned on ideas such as mixture-of-experts architectures, efficient attention mechanisms, reinforcement learning, and reasoning-oriented training [4][5]. These are not cosmetic optimizations. They change how much useful intelligence can be extracted per dollar of compute.

That is why DeepSeek mattered: it showed that the AI race is not only about who can buy the most GPUs. It is also about who can use them most intelligently.

---

## Algorithms and Compute Rise Together

Still, it would be wrong to conclude that algorithms can simply replace compute.

Modern AI breakthroughs are usually the result of both. The transformer architecture, introduced in the 2017 paper "Attention Is All You Need," made it much easier to train large models efficiently by replacing recurrence and convolution with attention-based sequence modeling [6]. That algorithmic breakthrough helped unlock the scaling era. But the scaling era also depended on better GPUs, faster interconnects, more memory, and larger datasets.

The relationship is circular:

- Better algorithms make compute more useful.
- More compute makes more ambitious algorithms possible.
- More ambitious models create new bottlenecks.
- Those bottlenecks force the next wave of algorithmic innovation.

Reasoning models make this especially clear. Traditional language models spend most of their compute during training and relatively little during inference. Reasoning models shift more compute into the moment of answering. Instead of immediately producing a response, they spend more tokens and more computation working through the problem.

That means inference itself becomes more expensive. As reasoning models become more widely used in coding, math, research, planning, and agents, demand for compute may increase rather than decrease.

Efficiency does not necessarily reduce total compute demand. Sometimes it expands the market so much that total demand grows.

---

## The Next Bottleneck: Data

Compute and algorithms are not the only constraints. Data is becoming a major bottleneck.

Large language models have been trained on enormous amounts of human-generated text from the internet. But that supply is not infinite. Research on data-constrained scaling has warned that, if current trends continue, AI systems may be trained on datasets comparable in size to the available stock of public human-generated text sometime between 2026 and 2032 [7].

This is one reason the industry is moving toward new kinds of data:

- Synthetic data generated by models
- Multimodal data from images, video, audio, and sensors
- Domain-specific data from medicine, finance, law, education, and science
- Embodied data from robots and autonomous vehicles
- Interaction data from AI agents operating in real environments

This shift is key because it changes what AI companies need to win. The future may not belong only to the companies with the biggest text models. It may belong to those with the best data loops.

Tesla, for example, has long relied on driving data from vehicles in the real world. Robotics companies need sensorimotor data. Healthcare AI needs clinically valid medical data. Financial AI needs reliable market, transaction, and risk data. Education AI needs learning behavior and feedback data.

In other words, the next phase of AI may be less about scraping the internet and more about connecting AI to the physical and institutional world.

---

## From General Models to Industrial AI

The public conversation often treats AI as if it were only ChatGPT, Claude, Gemini, Grok, or DeepSeek. But the deeper economic impact of AI will likely come from its integration into industries.

AI will show up in autonomous vehicles, automated factories, robotics, medical diagnosis, financial systems, logistics, education platforms, scientific research, consumer hardware, enterprise software, and public services.

This is where China's position becomes especially interesting. China may not always lead in the most advanced frontier model, but it has enormous strengths in manufacturing, hardware supply chains, robotics, batteries, electric vehicles, consumer electronics, and large-scale deployment. China's national AI strategy has also explicitly framed AI as a strategic technology and set long-term goals for becoming a global AI leader [8].

The analogy to lithium batteries is useful. The foundational science behind lithium-ion batteries did not originate only in China. Japan's Sony commercialized the first lithium-ion battery in 1991. But over time, China became dominant in scaling batteries into a huge industrial ecosystem spanning materials, manufacturing, electric vehicles, and energy storage.

AI may follow a similar pattern. The country that wins is not necessarily the country that invents every core idea first. It may be the country that can industrialize the technology fastest.

The competition plays out across three interdependent layers. The **infrastructure layer** — chips, data centers, power, and cooling — determines what can be built at all. The **technology layer** — foundation models, inference systems, and AI development platforms — determines what gets built. The **application layer** — healthcare, logistics, manufacturing, robotics, finance, and autonomous vehicles — determines what reaches users and generates economic and strategic value. Countries and companies that lead across all three have compounding advantages. Countries blocked at the infrastructure layer must find ways to compensate at the others.

---

## The Geopolitics of Compute

The H100 is not just a product. It has become a controlled substance.

In October 2022, the United States imposed sweeping export controls on advanced semiconductors and chip-manufacturing equipment destined for China. The restrictions targeted NVIDIA's A100 and H100 GPUs directly. NVIDIA responded by producing downgraded variants — the A800 and H800 — calibrated to stay just below the export threshold. In October 2023, the Biden administration closed that gap too, banning the H800 and its successors from sale to China.

The chokepoint runs deeper than the chip itself. Advanced semiconductors require extreme ultraviolet (EUV) lithography machines made almost exclusively by ASML, a Dutch company. The United States, the Netherlands, and Japan coordinated to block ASML from exporting EUV equipment to China. Without EUV, China cannot manufacture chips at the leading edge — currently below 5nm — regardless of how much it invests in domestic capacity.

Taiwan adds a further dimension. The Taiwan Semiconductor Manufacturing Company (TSMC) fabricates chips for NVIDIA, Apple, AMD, and most of the world's leading semiconductor designers, producing roughly 90% of the world's most advanced chips. Taiwan's contested political status — claimed by China, defended by the United States — makes TSMC the most geopolitically exposed company in the world. Any disruption to TSMC, whether through conflict, blockade, or economic coercion, would halt frontier AI development globally.

China's response has been a sustained domestic push. Huawei's Ascend 910B has been positioned as a domestic H100 alternative, with performance adequate for some training workloads, though still meaningfully behind NVIDIA's leading hardware. SMIC, China's leading chipmaker, has reached 7nm-class production without EUV by using multi-patterning techniques — a slower and more expensive workaround that trades efficiency for independence. The Chinese government has committed hundreds of billions of yuan to domestic semiconductor programs under initiatives including Made in China 2025 and its successors.

None of this closes the gap quickly. But the strategic logic is clear: China is building enough redundancy to remain competitive even if cut off from the leading edge of the global supply chain. Whether it succeeds depends on how fast algorithmic efficiency improves, how much the next wave of AI relies on raw training compute versus data and deployment, and whether the export control regime holds across successive administrations.

The export controls are ultimately a bet that compute superiority translates to AI superiority — the same bet this article questions. If efficiency keeps compounding, the chip war may prove to be fighting the last battle.

---

## The AI Race Is Not Zero-Sum

It is tempting to frame AI as a war: the United States versus China, OpenAI versus DeepSeek, NVIDIA versus domestic chip alternatives, compute versus algorithms.

There is some truth to this. AI has become strategically important. Compute supply chains, export controls, talent migration, data access, and national industrial policy all matter.

But AI is also not purely zero-sum.

The transformer was introduced by researchers at Google [6]. OpenAI turned transformer-based models into a global consumer phenomenon. DeepSeek pushed open reasoning models forward [5]. NVIDIA built the hardware platform that made scaling possible [2][3]. Researchers from many countries, including many Chinese and Chinese American scientists, have contributed to the field's most important advances.

The future of AI will be shaped by competition, but also by diffusion. Ideas spread. Models are distilled. Papers are published. Open-source communities reproduce and improve techniques. Engineers leave companies and start new ones. Applications emerge in unexpected places.

The deeper story is not simply "who wins the AI war." It is how AI becomes part of civilization's operating system.

---

## So, Can Compute Win the AI Race?

Compute can give a company or country an enormous advantage. Without enough compute, it is hard to train frontier models, serve billions of users, or run advanced reasoning systems at scale.

But compute alone is not enough.

To win in AI, you need:

- Powerful hardware
- Efficient algorithms
- High-quality data
- Energy and cooling infrastructure
- Distribution
- Talent
- Product sense
- Industrial deployment
- Regulatory and social trust

The H100 may be the icon of the AI age, but the real advantage belongs to the full ecosystem.

AI is not just a race to build bigger models. It is a race to turn intelligence into infrastructure, products, workflows, and new forms of human capability.

The next winners may not be the ones who own the most GPUs.

They may be the ones who know what to do with them.

---

## References

[1] xAI / public reporting on Colossus, the Memphis AI supercomputer initially built with around 100,000 NVIDIA GPUs for Grok training.

[2] NVIDIA Hopper / H100 architecture documentation and technical summaries, including H100's 80-billion-transistor design and up to 144 streaming multiprocessors.

[3] NVIDIA DGX H100 documentation and technical summaries describing DGX H100 systems with eight H100 GPUs.

[4] DeepSeek-AI. "DeepSeek-V3 Technical Report." 2024.

[5] DeepSeek-AI. "DeepSeek-R1: Incentivizing Reasoning Capability in LLMs via Reinforcement Learning." 2025.

[6] Vaswani, Ashish, et al. "Attention Is All You Need." NeurIPS, 2017.

[7] Villalobos, Pablo, et al. "Will We Run Out of Data? Limits of LLM Scaling Based on Human-Generated Data." 2022.

[8] State Council of the People's Republic of China. "New Generation Artificial Intelligence Development Plan." 2017.
 