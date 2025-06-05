---
layout: post
title: NeuroSymbolic AI - What, WHy, and How?
---
I've been hearing NeuroSymbolic AI A LOT these days, but really, what is it? Why was it invented? How do we use it?

Executive Summary (Human-Readable Version)
Neurosymbolic AI (NSAI) is a fast-emerging field that blends deep learning with symbolic reasoning to overcome the limitations of using either approach alone. 


By combining the pattern recognition strengths of neural networks with the logic and transparency of symbolic systems, NSAI creates AI that is more explainable, reliable, and capable of real reasoning—qualities that are essential in sensitive domains like healthcare and finance. Since 2020, research has surged, leading to new architectures and applications that point toward smarter, more human-aligned AI.

# NeuroSymbolic AI 101 (NSAI 101) 
Neurosymbolic AI brings together two historically separate fields: 

1. **Symbolic AI**, which, to put it simply, uses logic and rules to represent knowledge, and 

2. **Neural AI**, which learns patterns from large datasets. 

Symbolic AI excels at structured reasoning and transparency but struggles with messy, unstructured data; whereas Neural networks are great at recognizing patterns in raw inputs like images and speech, but they often act like black boxes and have trouble explaining their decisions.

![](post-images/AG-NSAI-Graphic.png)


By integrating these two approaches, [NSAI aims to build AI systems that can learn flexibly, reason logically, and explain their actions](https://allegrograph.com/what-is-neuro-symbolic-ai/). It's often likened to combining two types of human thinking

1. **fast, intuitive responses** (like neural networks) and slower

2. **more deliberate reasoning** (like symbolic logic). 

This hybrid approach mitigates and addresses many of the current weaknesses in AI, for example, the lack of interpretability or failure to generalize, and moves us closer to artificial general intelligence (AGI).

![](post-images/NSAI-Paper-Graphic-2.png)

# How We Got Here: A Brief History
**AI has cycled between symbolic and neural methods for decades.**

Symbolic AI dominated in the early years but hit a wall due to its brittleness. Neural networks then took over with deep learning breakthroughs—but at the cost of explainability and reasoning.

Researchers eventually realized that combining the two isn't just useful, it's **necessary**.

## More History: "AI Winters"
The periods known as "AI winters"  were characterized by reduced funding and waning interest in AI research

They  were partly a direct consequence of the overly optimistic predictions made by early AI pioneers regarding the imminent achievement of human-level intelligence solely through symbolic methods.

The growing recognition that the strengths and weaknesses of neural networks and symbolic AI are largely complementary became the primary catalyst for their eventual integration.3 Early conceptualizations and calls for hybrid models date back as far as the 1990s, a period when terms like "symbolic" and "sub-symbolic AI" were commonly used.

The sustained interest in this synthesis is further evidenced by dedicated workshops on neuro-symbolic AI that have been held annually since at least 2005.


Prominent researchers such as Leslie Valiant and Gary Marcus have argued that the effective construction of rich computational cognitive models and the development of robust, knowledge-driven AI systems necessitate the combination of symbolic reasoning with efficient machine learning and the incorporation of rich prior knowledge.


The repeated limitations encountered by single-paradigm AI approaches in achieving robust, general intelligence led to a pragmatic evolution within the field. 

## AI Summer?
Instead of maintaining a philosophical divide between symbolic and neural AI, the community increasingly recognized their synergistic potential. 

This historical lesson is a foundational aspect of the current "third AI summer," where hybridization is no longer just a theoretical concept but a practical imperative for building reliable and versatile AI systems. These integrated systems are designed to effectively handle both complex pattern recognition and rigorous logical reasoning, particularly in "high-stakes applications" where accuracy and explainability are critical.11 

This shift shows a mature response to the complexities of real-world intelligence.

## Recent Research Highlights

Over the period of 2020 to 2024, NSAI research has surged across five main areas :

1. Knowledge Representation (~ 44%): Building structured commonsense databases, event-based representations, and symbolic enhancements to reduce training data needs .

2. Learning & Inference (63%): Combining symbolic logic with neural learning to support zero-shot learning, few-shot reasoning, and advanced planning (e.g., Logical Neural Networks, Plan-SOFAI) .

3. Logic & Reasoning (35%): Merging logic with probability for more flexible inference, especially in language understanding (e.g., DeepStochLog, LinkBERT) .

4. Explainability (28%): Creating AI that explains its reasoning through structures like Braid, FactPEGASUS, and logical summarization models .

5. Meta-Cognition (5%): A newer focus—using reinforcement learning and cognitive architectures (e.g., CMC) to help AI reflect on and improve its own decisions .

## How can NSAI be applied in real life?

TLDR: Many, many ways across different fields.

Here's a list (non-comprehensive):
- Medicine

    In the medical field, NSAI enhances diagnostic accuracy by integrating neural networks with symbolic reasoning. This combination allows AI systems to process complex medical data and align their outputs with established medical knowledge, thereby reducing the incidence of AI-generated hallucinations and improving the reliability of clinical decisions. 

- Finance (because I currently work at the intersection of AI and Finance)

    Financial institutions are leveraging NSAI to bolster fraud detection and risk management. By combining pattern recognition capabilities of neural networks with the logical inference of symbolic AI, these systems can identify fraudulent activities more accurately and in real-time. For instance, JPMorgan Chase has implemented AI tools that significantly reduce false positives and enhance the efficiency of transaction monitoring, leading to substantial cost savings and improved customer trust. 
amitysolutions.com
+1
ijsret.com
+1

- Natural Language Processing (NLP)

    NSAI is revolutionizing NLP by addressing semantic ambiguities and enhancing language understanding. By integrating symbolic reasoning with neural language models, NSAI systems can disambiguate entities with multiple meanings—such as distinguishing between the EGFR gene and the EGFR test—thereby improving the accuracy of information extraction and question-answering systems. 

- Robotics

    In robotics, NSAI facilitates adaptive control and learning from experience. NVIDIA's Eureka project exemplifies this by using GPT-4 to autonomously generate reward functions, enabling robots to acquire complex skills through reinforcement learning. This approach allows for more efficient training of robotic systems, enhancing their ability to perform intricate tasks and adapt to dynamic environments. 

- Software & Enterprise

    NSAI is empowering software development by automating coding tasks and enhancing developer productivity. Tools like GitHub Copilot utilize NSAI to suggest code snippets and functions, allowing developers to focus on higher-level design and problem-solving. This not only accelerates the development process but also reduces the cognitive load on programmers, fostering a more creative and efficient workflow. 


**There will be more sections, WIP.**
