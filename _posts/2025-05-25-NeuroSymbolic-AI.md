---
layout: single
title: NeuroSymbolic AI - What, Why, and How?
---
I've been hearing the term **NeuroSymbolic AI** a lot these days, but really - **What** is it? **Why** was it invented? **How** do we use it?


# NeuroSymbolic AI 101 (NSAI 101) 

Neurosymbolic AI (abbreviated as NSAI) is a fast-emerging field now in 2025, that blends deep learning with symbolic reasoning to overcome the limitations of using either approach alone. 

Neurosymbolic AI brings together two historically separate fields: 

1. **Symbolic AI**, which, to put it simply, uses logic and rules to represent knowledge.

2. **Neural AI**, which learns patterns from large datasets. 

Symbolic AI is best at structured reasoning and transparency but struggles with messy, unstructured data; whereas Neural AI, like Neural networks, are great at recognizing patterns in raw inputs like images and speech, but they often act like black boxes and have trouble explaining their decisions.

![Symbolic AI vs. Neural AI vs. LLM/Vector](/images/NSAI/AG-NSAI-Graphic.png)

(**Note**: It's thought-provoking that, here in this diagram, LLM is listed as a completely distinct category, perhaps because it aims to achieve language related tasks. I can definitely see some slight overlap between LLM and both Neural and Symbolic AI though. )


By integrating these two approaches, [NSAI allows engineer to build AI systems that can learn flexibly, reason logically, and explain their actions](https://allegrograph.com/what-is-neuro-symbolic-ai/). 

Because we are humans, the AI systems we design, are often compared to the different ways we think. This is also the case for NeuroSymbolic AI. 

NSAI is often likened to combining two types of human thinking:

1. **Fast, intuitive responses**, like [neural networks](https://en.wikipedia.org/wiki/Neural_network_(machine_learning))

2. **Slower, Deliberate reasoning**, like [formal/symbolic logic](https://en.wikipedia.org/wiki/Logic#:~:text=Formal%20logic%20(also%20known%20as,independent%20of%20their%20concrete%20content.))

This hybrid of 2 different types of thinking, actually mitigates and addresses **many** of the current weaknesses in AI.

For example, the lack of interpretability or failure to generalize, and moves us closer to artificial general intelligence (AGI).

(**Note**: I personally don't like using the term AGI just because it feels like such a nothing-statement. I agree a lot with what [Prof. Feifei Li says regarding AGI...](https://youtu.be/0jMgskLxw3s?si=FN6AP6kOfHHQF3zv) However, for now, I think this is the best word we have to describe what research in NSAI is aiming to achieve.)


# How We Got Here: A Brief History
**This might be news to a lot of people, but AI has cycled between symbolic and neural methods for decades.**

Symbolic AI dominated in the early years but hit a wall due to its brittleness. Neural networks then took over with deep learning breakthroughs—but at the cost of explainability and reasoning.

Researchers eventually realized that combining the two isn't just useful, it's **necessary**.

## More History: "AI Winters" (1970 - 1980, 1987 - 2000)

The periods known as [**"AI winters"**](https://en.wikipedia.org/wiki/AI_winter)  were typiecally characterized by reduced funding and waning interest in AI research. 

In human history, there were two major AI "winters", approximately 1974–1980 and 1987–2000 (Reference: [Artificial Intelligence: A Modern Approach,](https://aima.cs.berkeley.edu/)).

These setbacks, alongside [other shorter AI winters over the past few decades](https://en.wikipedia.org/wiki/AI_winter#The_setbacks_of_the_late_1980s_and_early_1990s), were largely driven by the failure of early symbolic AI systems to live up to bold promises of achieving human-level intelligence. And it was hard to sustain interest on the topic among research communities.

This repeated cycle of **overpromise** and **underdelivery**, the obvious limitations of single-paradigm systems, namely symbolic-AI-only systems, coupled with the continued ambition to reach artificial general intelligence, finally catalyzed a shift toward neurosymbolic AI (NSAI)—a fusion of both paradigms.

By the 1990s, researchers began to explore hybrid systems, then referred to using terms like "symbolic" and "sub-symbolic AI", that aimed to bridge the gap between logic-based reasoning and data-driven learning. When revisiting the idea of a hyrbid approach, combining neural and symbolic system, they realized

**the strengths of symbolic and neural approaches are complementary rather than competing.**

Today, we are entering what may be a new, and more promising era for  NSAI.

## Welcome to the "AI Spring" (2000 - Present)
In the early 2000s, as mentioned previously, the community is starting to increasingly recognize the synergistic potential of Neural+Symbolic AI, so much that they created a new, official term for the hybrid approach:

    "Neural" + "Symbolic" AI = "NeuroSymbolic" AI       

Despite experiencing several AI winters, the CS and AI communities, alongside mutliple promiment cognitive scientists sustained interest in this monumental synthesis of neural and symbolic AI. 

NeSy, [the International Workshop on
Neural-Symbolic Learning and Reasonings](https://sites.google.com/view/nesy20/home), is a dedicated serioes of workshops, also "the longest standing gathering for the presentation and discussion of cutting edge research in NSAI", has been held annually since at least 2005.

In the late 2000s and 2010s, prominent researchers such as [Leslie Valiant](https://en.wikipedia.org/wiki/Leslie_Valiant) and [Gary Marcus](https://en.wikipedia.org/wiki/Gary_Marcus) have argued that the [effective construction of rich computational cognitive models](https://dl.acm.org/doi/10.1145/602382.602410) and the development of knowledge-driven AI systems necessitate the combination of symbolic reasoning with efficient machine learning and the incorporation of sufficient prior knowledge (Check out this pape for a summary of the new surge in interest in NSAI in the 2000s: [Neurosymbolic AI: The 3rd Wave](https://arxiv.org/pdf/2012.05876)). 

In recent year, NeurIPS attract sometimes over 12,000 attendees from over 60 countries, and [has started consistently holding NeuroAI workshops since 2024](https://neuroai-workshop.github.io/speakers/).

Now, in 2025, these integrated systems are designed to effectively handle both complex pattern recognition and rigorous logical reasoning, particularly in "high-stakes applications" where **accuracy** and **explainability** are people's top priority.


## How can NSAI be applied in real life?

Here's a critical question to ask, after decades of efforts from AI researchers, engineers, cognitive scientists to develop NSAI:

**What are the real-world applications of NSAI?**


**TLDR: Many, many ways across different fields.**

Here's a list (non-comprehensive) of what NSAI helps to achieves in different fields, and some examples:

### Medicine

- NSAI enhances diagnostic accuracy using NNs with symbolic reasoning
- Reduces the incidence of AI-generated hallucinations and improves the reliability of clinical decision, because NSAI can process complex medical data and align their outputs with established medical knowledge

### Finance 

-  NSAI can bolster fraud detection and risk management. By combining pattern recognition capabilities of neural networks with the logical inference of symbolic AI, 

- Identify fraudulent activities more accurately and in real-time using pattern recognition of NNs with logical inference of symbolic AI
    
- Example: [JPMorgan Chase](https://www.jpmorgan.com/technology/artificial-intelligence/ai-research-publications) has implemented AI tools that significantly reduce false positives and enhance the efficiency of transaction monitoring -> substantial cost savings and improved customer trust


### Natural Language Processing (NLP)

- NSAI can help tackle semantic ambiguities and enhancing language understanding for machines.
    
- Example: [ProSLM](https://arxiv.org/abs/2409.11589). A very recent framework, published in 2024, it enhances the robustness and explainability of large language models (LLMs) in domain-specific (e.g. telecommunications, clean energy, healthcare) question-answering tasks by integrating symbolic reasoning with neural language models. See the diagram below for the framework's workflow. 

    ![ProSLM Sytem Workflow Diagram](/images/NSAI/Pro-SLM.png)
    ProSLM Sytem Workflow Diagram (Vakharia et al., 2024)





### Robotics

- NSAI also enables adaptive control and learning from experience
- Example: NVIDIA's Eureka project uses GPT-4 to autonomously (1) generate reward functions, and (2) let robots to acquire complex skills through RL -> more efficient training of robotic systems +  enhance their ability to perform intricate tasks and adapt to more dynamic environments with moving objects

### Software Engineering for Enterprises

- NSAI is the engine of tools that automate coding tasks using logical reasoning to improve enterprise productivity. 
- Examples: GitHub Copilot (uses NSAI to suggest code snippets and functions), and many other "AI reasoning" softwares you see on the internet these days.


## Recent Research Highlights

Based on [Neuro-Symbolic AI in 2024: A Systematic Review](https://arxiv.org/html/2501.05435v1), over the period of 2020 to 2024, NSAI research has surged across five main areas :

Knowldge Representation, Learning & Inference, Logic & Reasoning, Explainability, and Meta-Cognition.

(**Note**: For more specific information, I **implore you** to read [this amazing review on the most recent research in NSAI](https://arxiv.org/html/2501.05435v1)! It's the most comprehensive review in this field I've found so far. If you have more recommendations like this one, leave a comment and let me know :D )

Here's a breakdown of what each of these terms means:

1. **Knowledge Representation** 

    This refers to the process of building structured commonsense databases, event-based representations, and symbolic enhancements to reduce training data needs .

2. **Learning & Inference** 
    
    There seemed to be a particularly [notable surge in learning and inference using NSAI starting from 2020 to 2024](https://arxiv.org/html/2501.05435v1). Essentially, by combining two paradigms (neural + symbolic AI), we can now support tasks like zero-shot learning, where the system makes accurate predictions about concepts it hasn’t explicitly seen before, and few-shot reasoning, where it learns or infers with only a handful of examples.  
    
    **This is a big step forward from traditional neural networks that often require massive datasets to generalize well.**
    

    This is where the hybrid approach wins again: The symbolic component provides structured, rule-based knowledge (essentially a prior) while the neural side provides flexibility.

    Here are some more speicifc examples to supplement your understanding: Models like [Logical Neural Networks](https://arxiv.org/abs/2006.13155) and architectures like [Plan-SOFAI](https://github.com/FrancescoFabiano/SOFAI-x-Planning), allow systems to perform more advanced **planning**, **logical reasoning**, and even **abstract problem-solving** by learning patterns that respect known symbolic constraints. 

3. **Logic & Reasoning**

    Merging logic with probability for more flexible inference, especially in language understanding (e.g., DeepStochLog, LinkBERT) .

4. **Explainability**

    This one is straight-forward - The focus on creating AI that explains its reasoning through structures like [Braid](https://ojs.aaai.org/index.php/AAAI/article/view/21333), [FactPEGASUS](https://arxiv.org/abs/2205.07830), and some logical summarization models such as [Abstract Text Summarization](https://arxiv.org/html/2409.02413v1) and [RAG-based summarization](https://arxiv.org/html/2403.19889v1).

5. **Meta-Cognition**

    This seems to be a newer focus compared to the other four.
    
    It essentially means using reinforcement learning and cognitive architectures to help AI reflect on and improve its own decisions. 
    
    [Here's a good paper on this topic](https://arxiv.org/html/2403.18827v1), which presents a framework that adapts the [Common Model of Cognition (CMC)](https://www.sciencedirect.com/science/article/pii/S1877050918323184) to large generative networks.

    (**Note**: I will read more papers and add more intuitive explanations to this section, stay tuned!)


## Mathematical Foundations of Neurosymbolic AI 
Considering that you made it this far into this article, I believe it's reasonable to assume that you want to learn even more about NSAI.

**Now that's where the math comes in.**

To help you kickstart self-learning,  I summarized some of the most essestial mathematics that you might want to know.

### Linear Algebra and Calculus (as always)
Lin alg and calculus are and will always be the foundations of the foundations of AI... So of course it's the first door one needs to open to eventually get to NSAI.

The required math courses for a CS degree should cover all of these (if not then I'd be a bit concerned), but for the sake of completion of the article, I'll list the main topics here:

- Matrix Operations. **Fundamental** in neural network computations, including transformations and activations. I'd recommend taking one or two advanced courses in linear algebra beyond the introductory course to hone a good foundation.
- Differentiation: **Equally fundamental** for NNs, specificaly, for training neural networks through backpropagation. 


### Probability and Statistics (again, as always)
- Bayesian Inference. Used in models like DeepProbLog, combining probabilistic reasoning with logic.

- Markov Models. Used in sequential decision-making processes.

### Optimization (as always x3)

- Gradient Descent. A core algorithm for training neural networks. 
- Constrained optimization + constraints satisfaction. Used to make sure that AI systems [adhere to basic and sometimes more advanced logic and symbolic rules](https://research.kuleuven.be/portal/en/project/3E231238#:~:text=Project%20summary,as%20well%20as%20its%20applications.) during learning and inference.

### Graph Theory

This is a more intereting topic. 

When I was doing my routine  online "research" on neurosymbolic AI, I've found [Knowledge Graphs (KGs)](https://en.wikipedia.org/wiki/Knowledge_graph) to be a reoccurring topic/tool for representing structured information. 

To put it simply, **[KGs model entities (objects, concepts, or events, ...) and their interrelations](https://dl.acm.org/doi/10.1145/3227609.3227689)** using nodes and edges in a graph structure. 

For example, a KG can represent the fact "Paris is the capital of France" by linking the entities/nodes "Paris" and "France" with the relationship/edge "is the capital of". 

Or, similarly, as illustrated in the image below, a KG can link the entities "Arnold S." and "California" with the rrelationship "is the Governor of".

**And KGs are crucial to helping NSAI systems perform logical reasoning tasks.**

Thanks to the relational structure inherent in graphs, NSAI systems can traverse and infer new knowledge from existing connections, and the structure even embed semantics of relationship, which then allows NSAI to capture even more complex patterns, beyond simple ones like  "this is that".

Representations like KGs also allow for complex queries and inferencing, which significantly aids applications in search engines, recommendation systems, and question-answering platforms. 

**It's kind of like giving the machine a tool that human uses, so that it can learn to think more like one, but even more efficiently.**


But there's also problems in these KGs that we need to solve. 

Here's a visual example of two hypothetical knowledge graphs representing disparate topics, each contains a node that corresponds to the **same entity** in the real world (Arnold Schwarzenegger). 

![](/images/NSAI/KG-Example.png)

In this case, the AI system **cannot automatically link these two entities and label them as the same**. 

This specific task, called [Entity Alignment](https://arxiv.org/abs/2205.08777), has seen increasing research efforts since 2023. And to achieve significant enhancement, deep understand of graph theory is needed.

Specifically, some entity alignment methods use [structural similarities between generally non-isomorphic graphs to predict which nodes corresponds to the same entity](https://arxiv.org/abs/2205.08777).

Hope this gives you more motivation to learn graph theory!


### Mathematical Logic / Formal Logic
**In NSAI, logic-based frameworks are the building blocks for representing and manipulating symbolic knowledge.**

![](/images/NSAI/NSAI-Paper-Graphic-2.png)

Now that you understand the basic defintion of KGs, [the above diagram](https://allegrograph.com/what-is-neuro-symbolic-ai/) will help you undertsand why formal logic is also needed in NSAI, and how it connects to KGs.

For Neuro-Symbolic KGs, a critical structure for NSAI reasoning and logic, **symbolic knowledge** (like rules and logical relationships) is **embedded** into a neural space where learning and induction happen. 

This Neural KG then **generates\induce rules** that follow the input symbolic knowledge structure and updated embeddings. 

These neural outputs are then **decoded** back into symbolic form, which then enables logical deduction and further refinement upon the rules the Neural KG generated.

This creates a continuous loop of 

using NNs to, for example, interpret a complex image and then use the symbolic KGs, and predefined symbolic rules/axioms to answer questions about the image’s content or to infer the relationships between objects within it.

**But to know what symbolic rules and axioms we need to define, we first need to knw a few basic mathematical logic concepts:**

**[Propositional logic](https://en.wikipedia.org/wiki/Propositional_calculus)** serves as a foundational system of logic-based frameworks. Specifically, it deals with statements that are either true or false.



 However, the expressiveness of propositional logic is limited to simple, declarative facts. 


 For example, propositional logic can represent simple facts like:

    Human_Socrates → Mortal_Socrates

This translates to, "If Socrates is human, then Socrates is mortal."

But it cannot generalize to statements like:

    “All humans are mortal.”


 
 If the goal is to capture **more complex relationships**, (math majors you're gonna love this)
 
 then you will need [First-Order Logic (FOL)](https://en.wikipedia.org/wiki/First-order_logic), which is often used to extend propositional logic, by introducing 
 
 - [Quantifiers](https://en.wikipedia.org/wiki/Quantifier_(logic)) (basically, specifies quantity, like "for all"/"∀") and 
 - [Predicates](https://en.wikipedia.org/wiki/Predicate_(logic)) (property or relation).
 
 Why? 
 
 Because using FOL allows for the representation of objects, their properties, and the relationships between them, which add to the complexity of the KG we can build into our NSAI system.
 
 For example, FOL can express statements like
 
    "All humans are mortal"
 
  using universal quantification, 
  
    ∀ x (Human(x) → Mortal(x))

This expression reads: 

    "For every x, if x is a human, then x is mortal." 
    
Here, Human(x) and Mortal(x) are predicates indicating that the object x possesses the properties of being human and being mortal, respectively.


Now you can probably see that why using formal logic is so important in NSAI - **it gives us a language that both Humans and AI systems can understand to model real-world scenarios and relations.**

There's more to the logics that are used in NSAI. 

Another big one is **[Description Logics (DLs)](https://en.wikipedia.org/wiki/Description_logic)**, which form the basis of ontologies and semantic web technologies. 

DLs enable systems to **model domain knowledge explicitly**, which is the **core** of reasoning about the relationships and hierarchies within data.

Recent research advancements have focused on benchmarking [neuro-symbolic DL reasoners](https://neurosymbolic-ai-journal.com/paper/benchmarking-neuro-symbolic-description-logic-reasoners-existing-challenges-and-way-forward?utm_source=chatgpt.com) to address challenges in integrating DLs with neural networks. 

For example, [Singh et al. (2023)](https://neurosymbolic-ai-journal.com/paper/benchmarking-neuro-symbolic-description-logic-reasoners-existing-challenges-and-way-forward?utm_source=chatgpt.com), in their paper Benchmarking Neuro-Symbolic Description Logic Reasoners: *Existing Challenges and A Way Forward*, discuss current challenges and propose ways forward for neuro-symbolic DL reasoners. 

Specifically, they emphasized the need for systems that can handle ontological reasoning within NSAI frameworks. 

Again, to advance research in this specific area requires a deep understanding of formal logic.


Also, as a side note, **[Automated Theorem Proving]()** althought technically more of an application of NSAI, is exactly at the intersection for mathematical logic and NSAI systems. 

There are existing techniques like [resolution and tableau methods](https://www.sciencedirect.com/topics/computer-science/tableau-method#:~:text=The%20Tableau%20Method%20is%20a,process%20of%20rules%20and%20semantics.) that allow machines to derive conclusions from premises.

Researcher have even been developing methods to conduct mathematical research using NSAI systems. 

Professor Terrence Tao, UCLA, in his AMS Colloquium lecture at 2024 Joint Mathematics Conference in San Francisco, summarized "3 promising new ways" to use AI in mathematical research:

![](/images/NSAI/machine-assisted-proofs-tao.png)

This further proves that there is truly a huge potential in the capabilities of NSAI, as even some of the most brilliant mathematics in the world are exploring machine-assisted mathematical logic & reasoning, which has been always considered one of the most fundamental, and yet diffucult mental tasks humans can take on.


(An Anecdote: I was there at JMM 2024, but too bad I couldn't make it to Terrence Tao's lecture due to scheduling. I watched it [on youtube](https://www.youtube.com/watch?v=AayZuuDDKP0) later though. It was a great lecture. I'd recommend watching the whole thing if this topic interests you.)


**2025-06-05, Nicole Hao**
