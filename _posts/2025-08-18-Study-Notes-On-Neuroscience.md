---
layout: single
title: Study Notes on Neuroscience
---


My study notes on neuroscience, starting from molecular mechanisms and neural circuits to cognitive functions, brain disorders, and the intersection with artificial intelligence. Work In Progress.

## Contents

1. [Introduction](#1-introduction)
   - What is neuroscience?
   - Major questions and scope

2. [Nervous System Overview](#2-nervous-system-overview)
   - [Central Nervous System (CNS)](#central-nervous-system-cns)
   - [Peripheral Nervous System (PNS)](#peripheral-nervous-system-pns)
   - [CNS vs. PNS](#central-nervous-system-vs-peripheral-nervous-system)
   - Basic cell types: neurons vs. glia

3. [Neurons](#3-neurons)
   - Neuron structure
   - Action potentials & signal transmission
   - Neurotransmitters & receptors

4. [Neuroanatomy](#4-neuroanatomy)
   - [Early brain development](#early-brain-development)
   - [Lesions](#lesions)
   - [Major brain regions](#major-brain-regions-cortex-cerebellum-brainstem-limbic-system)
   - [Functional areas](#functional-areas-frontal-parietal-temporal-occipital-lobes)

5. [Neural Communication and Embodied Emotions](#5-neural-communication-and-embodied-emotions)
   - [Neural communications](#neural-communications)
   - [Neurotransmitters](#neurotransmitters)
   - [Embodied emotions](#embodied-emotions)

6. [Perception and Vision](#6-perception-and-vision)
   - Sensory systems
   - Motor pathways & control

7. [Hearing](#7-hearing)
   - Auditory system

8. [Higher Cognitive Functions](#8-higher-cognitive-functions)
   - Memory and learning
   - Language
   - Attention and consciousness
   - Emotion and motivation

9. [Methods in Neuroscience](#9-methods-in-neuroscience)
   - Imaging techniques
   - Electrophysiology
   - Lesion studies
   - Computational models

10. [Disorders of the Nervous System](#10-disorders-of-the-nervous-system)
    - Neurological disorders
    - Psychiatric disorders
    - Developmental disorders

11. [Neuroscience & Artificial Intelligence](#11-neuroscience--artificial-intelligence)
    - Inspiration from neuroscience
    - Feedback from AI to neuroscience
    - Shared challenges
    - Frontiers

12. [Applications & Future Directions](#12-applications--future-directions)
    - Neurotechnology
    - AI and computational neuroscience
    - Neuroethics

---

## 1. Introduction

**Neuroscience** is the scientific study of the nervous system — its structure, function, development, genetics, biochemistry, physiology, pharmacology, and pathology. It spans multiple levels of analysis:

| Level | Focus | Example |
|-------|-------|---------|
| **Molecular** | Ion channels, receptors, gene expression | NMDA receptor structure |
| **Cellular** | Individual neuron properties | Action potential generation |
| **Systems** | Neural circuits and pathways | Visual processing pathway |
| **Behavioral** | How neural activity produces behavior | Motor control, decision-making |
| **Cognitive** | Higher-order functions | Memory, language, consciousness |

**Major questions in neuroscience:**
- How does the brain develop and wire itself?
- How do neurons encode and transmit information?
- How do neural circuits give rise to perception, thought, and action?
- What goes wrong in neurological and psychiatric disorders?
- How does experience reshape the brain (plasticity)?
- What is the neural basis of consciousness?

**Scope:** Neuroscience is inherently interdisciplinary, drawing from biology, chemistry, physics, psychology, computer science, mathematics, medicine, and philosophy. The field ranges from studying single ion channels at the molecular level to understanding complex cognitive phenomena like language and decision-making.

---

## 2. Nervous System Overview

The nervous system is the body's primary communication and control network. It is divided into two major components:

### Central Nervous System (CNS)

The **CNS** consists of the **brain** and **spinal cord**. It is the integration and command center of the body.

- **Brain:** ~86 billion neurons; responsible for perception, cognition, emotion, motor control, and homeostasis
- **Spinal cord:** Conduit for signals between brain and body; mediates reflexes independently of the brain
- **Protected by:**
  - **Skull** (cranium) — encases the brain
  - **Vertebral column** — encases the spinal cord
  - **Meninges** — three protective membranes:
    1. **Dura mater** (outermost, tough)
    2. **Arachnoid mater** (middle, web-like)
    3. **Pia mater** (innermost, delicate, adheres to brain surface)
  - **Cerebrospinal fluid (CSF)** — cushions the brain, removes waste, circulates nutrients

### Peripheral Nervous System (PNS)

The **PNS** includes all neural structures outside the brain and spinal cord:

- **Somatic nervous system:** Voluntary control of skeletal muscles; carries sensory information to the CNS
- **Autonomic nervous system (ANS):** Involuntary control of internal organs
  - **Sympathetic division:** "Fight or flight" — increases heart rate, dilates pupils, inhibits digestion
  - **Parasympathetic division:** "Rest and digest" — decreases heart rate, constricts pupils, stimulates digestion
  - **Enteric nervous system:** Semi-independent network governing the gastrointestinal tract (~500 million neurons)
- **Cranial nerves:** 12 pairs emerging directly from the brain (e.g., optic nerve, vagus nerve)
- **Spinal nerves:** 31 pairs emerging from the spinal cord

### Central Nervous System vs. Peripheral Nervous System

| Feature | CNS | PNS |
|---------|-----|-----|
| **Components** | Brain + spinal cord | Nerves + ganglia outside CNS |
| **Protection** | Bone + meninges + CSF | Minimal (connective tissue sheaths) |
| **Regeneration** | Very limited | Some regeneration possible |
| **Glial cells** | Oligodendrocytes (myelination), astrocytes, microglia | Schwann cells (myelination), satellite cells |

**Meninges:**
The meninges are the three membranes (dura, arachnoid, pia) that envelop the CNS. Inflammation of the meninges is called **meningitis**, which can be caused by bacterial or viral infection and is a medical emergency.

**Peripheral diseases:**
- **Peripheral neuropathy:** Damage to peripheral nerves causing weakness, numbness, and pain (e.g., diabetic neuropathy)
- **Guillain-Barré syndrome:** Autoimmune attack on peripheral nerve myelin
- **Carpal tunnel syndrome:** Compression of the median nerve

**Brain tumors:**
- **Primary tumors:** Originate in the brain (e.g., gliomas from glial cells, meningiomas from meninges)
- **Secondary (metastatic) tumors:** Spread from cancers elsewhere in the body
- Tumors are classified by cell type, location, and grade (I–IV, with IV being most aggressive, e.g., glioblastoma multiforme)

**Basic cell types: neurons vs. glia**

| Property | Neurons | Glia |
|----------|---------|------|
| **Function** | Electrical signaling, information processing | Support, insulation, immune defense, homeostasis |
| **Number** | ~86 billion in human brain | ~85 billion (roughly equal to neurons) |
| **Excitability** | Generate action potentials | Generally non-excitable (no APs) |
| **Types** | Sensory, motor, interneurons | Astrocytes, oligodendrocytes, microglia, Schwann cells |

**Glial cell types:**
- **Astrocytes:** Regulate the blood-brain barrier, provide metabolic support, modulate synaptic transmission, maintain ion homeostasis
- **Oligodendrocytes (CNS) / Schwann cells (PNS):** Produce myelin sheaths that insulate axons and speed up signal conduction
- **Microglia:** Resident immune cells of the CNS; phagocytose debris and pathogens; involved in neuroinflammation
- **Ependymal cells:** Line the ventricles; produce and circulate CSF

---

## 3. Neurons

### Parts of a Neuron

A typical neuron has four main structural regions:

1. **Dendrites:** Branching extensions that receive incoming signals from other neurons. Covered in **dendritic spines** — small protrusions that form the postsynaptic side of most excitatory synapses.

2. **Soma (cell body):** Contains the nucleus and most organelles. Integrates incoming signals. If the summed input exceeds a threshold, an action potential is initiated.

3. **Axon:** A long, thin projection that conducts electrical impulses (action potentials) away from the soma toward other neurons, muscles, or glands.
   - **Axon hillock:** The junction between soma and axon; the site of action potential initiation (highest density of voltage-gated Na⁺ channels)
   - **Myelin sheath:** Insulating layer formed by oligodendrocytes (CNS) or Schwann cells (PNS); increases conduction velocity
   - **Nodes of Ranvier:** Gaps in the myelin sheath where ion channels are concentrated; enable **saltatory conduction** (signal "jumps" between nodes)

4. **Synapse:** The junction between two neurons (or a neuron and a target cell). Consists of:
   - **Presynaptic terminal:** Contains synaptic vesicles filled with neurotransmitter
   - **Synaptic cleft:** ~20 nm gap between pre- and postsynaptic cells
   - **Postsynaptic membrane:** Contains receptors that bind neurotransmitter

**Neuron classification by structure:**
- **Unipolar:** Single process (common in invertebrates)
- **Bipolar:** Two processes — one axon, one dendrite (e.g., retinal bipolar cells)
- **Multipolar:** One axon, many dendrites (most common in the CNS)
- **Pseudounipolar:** Single process that splits into two branches (e.g., dorsal root ganglion sensory neurons)

### Action Potentials & Signal Transmission

An **action potential (AP)** is a rapid, transient reversal of the membrane potential that propagates along the axon. It is the fundamental unit of neural signaling over long distances.

**Resting membrane potential:**
- Typical value: \\(-70\\) mV (inside negative relative to outside)
- Maintained by the **Na⁺/K⁺ ATPase pump** (3 Na⁺ out, 2 K⁺ in per cycle) and selective ion channel permeability
- At rest, the membrane is most permeable to K⁺ → resting potential is close to the K⁺ equilibrium potential

**Nernst equation** (equilibrium potential for a single ion):

$$
E_{\text{ion}} = \frac{RT}{zF} \ln \frac{[\text{ion}]_{\text{outside}}}{[\text{ion}]_{\text{inside}}}
$$

At body temperature (37°C), for a monovalent cation:

$$
E_{\text{ion}} \approx \frac{61.5 \text{ mV}}{z} \log_{10} \frac{[\text{ion}]_{\text{outside}}}{[\text{ion}]_{\text{inside}}}
$$

**Goldman-Hodgkin-Katz (GHK) equation** (resting potential considering multiple ions):

$$
V_m = \frac{RT}{F} \ln \frac{P_{\text{K}}[\text{K}^+]_o + P_{\text{Na}}[\text{Na}^+]_o + P_{\text{Cl}}[\text{Cl}^-]_i}{P_{\text{K}}[\text{K}^+]_i + P_{\text{Na}}[\text{Na}^+]_i + P_{\text{Cl}}[\text{Cl}^-]_o}
$$

**Phases of the action potential:**

1. **Resting state** (\\(-70\\) mV): Voltage-gated Na⁺ and K⁺ channels are closed
2. **Depolarization:** Stimulus reaches threshold (\\(\approx -55\\) mV) → voltage-gated Na⁺ channels open → Na⁺ rushes in → membrane potential shoots toward \\(+30\\) mV
3. **Repolarization:** Na⁺ channels inactivate; voltage-gated K⁺ channels open → K⁺ flows out → membrane potential returns toward resting
4. **Hyperpolarization (undershoot):** K⁺ channels close slowly → membrane potential briefly dips below \\(-70\\) mV
5. **Return to resting:** Na⁺/K⁺ pump restores ion gradients

**Key properties:**
- **All-or-none:** Once threshold is reached, the AP fires at full amplitude regardless of stimulus strength
- **Refractory periods:**
  - *Absolute refractory period:* No new AP can be generated (Na⁺ channels inactivated)
  - *Relative refractory period:* A stronger-than-normal stimulus can trigger an AP (some K⁺ channels still open)
- **Saltatory conduction:** In myelinated axons, APs jump between Nodes of Ranvier, increasing speed from ~2 m/s (unmyelinated) to ~120 m/s (myelinated)

**Synaptic transmission:**
1. AP arrives at the presynaptic terminal
2. Voltage-gated Ca²⁺ channels open → Ca²⁺ influx
3. Ca²⁺ triggers vesicle fusion with the presynaptic membrane (via SNARE proteins)
4. Neurotransmitter is released into the synaptic cleft (exocytosis)
5. Neurotransmitter binds to postsynaptic receptors
6. Postsynaptic response: excitatory (EPSP) or inhibitory (IPSP)
7. Signal termination: reuptake, enzymatic degradation, or diffusion

### Neurotransmitters & Receptors

**Major neurotransmitters:**

| Neurotransmitter | Type | Key Functions |
|-----------------|------|---------------|
| **Glutamate** | Amino acid | Primary excitatory NT in CNS; learning & memory |
| **GABA** | Amino acid | Primary inhibitory NT in CNS; reduces neuronal excitability |
| **Acetylcholine (ACh)** | Small molecule | Neuromuscular junction; attention, memory (cholinergic system) |
| **Dopamine (DA)** | Monoamine | Reward, motivation, motor control; implicated in Parkinson's & addiction |
| **Serotonin (5-HT)** | Monoamine | Mood regulation, sleep, appetite; target of SSRIs |
| **Norepinephrine (NE)** | Monoamine | Arousal, alertness, fight-or-flight response |
| **Endorphins** | Neuropeptide | Pain modulation, pleasure |

**Receptor types:**
- **Ionotropic receptors (ligand-gated ion channels):** Fast response (~ms). Neurotransmitter binding directly opens an ion channel.
  - Examples: AMPA receptors (Na⁺), NMDA receptors (Na⁺/Ca²⁺), GABA-A receptors (Cl⁻), nicotinic ACh receptors (Na⁺)
- **Metabotropic receptors (G-protein coupled receptors, GPCRs):** Slower response (~seconds). Neurotransmitter binding activates intracellular signaling cascades via G-proteins and second messengers (cAMP, IP₃, DAG).
  - Examples: Muscarinic ACh receptors, metabotropic glutamate receptors (mGluRs), dopamine receptors (D1–D5), serotonin receptors (most subtypes)

**Excitatory vs. inhibitory postsynaptic potentials:**
- **EPSP:** Depolarization of the postsynaptic membrane (e.g., Na⁺ influx via AMPA receptors) → increases probability of AP
- **IPSP:** Hyperpolarization of the postsynaptic membrane (e.g., Cl⁻ influx via GABA-A receptors) → decreases probability of AP
- **Spatial summation:** EPSPs/IPSPs from multiple synapses combine simultaneously
- **Temporal summation:** EPSPs/IPSPs from the same synapse combine over rapid successive firing

---

## 4. Neuroanatomy

### Early Brain Development

The nervous system develops from the **ectoderm** (outermost germ layer) of the embryo through a process called **neurulation**:

1. **Neural plate** forms (~day 18): Thickening of ectoderm induced by signals from the underlying notochord
2. **Neural groove** and **neural folds** form as the plate invaginates
3. **Neural tube** closes (~day 28): The folds fuse, forming the precursor to the entire CNS
   - Failure to close → **neural tube defects** (e.g., spina bifida, anencephaly)
4. **Neural crest cells** migrate from the edges of the neural folds → give rise to PNS neurons, Schwann cells, melanocytes, and other structures

**Primary brain vesicles** (week 4):

| Vesicle | Becomes | Adult Structure |
|---------|---------|-----------------|
| **Prosencephalon** (forebrain) | Telencephalon | Cerebral cortex, basal ganglia, hippocampus |
| | Diencephalon | Thalamus, hypothalamus |
| **Mesencephalon** (midbrain) | Mesencephalon | Superior/inferior colliculi, substantia nigra |
| **Rhombencephalon** (hindbrain) | Metencephalon | Pons, cerebellum |
| | Myelencephalon | Medulla oblongata |

**Key developmental processes:**
- **Neurogenesis:** Birth of new neurons (primarily prenatal; limited adult neurogenesis in hippocampus and olfactory bulb)
- **Migration:** Neurons travel from their birthplace to their final position (guided by radial glia)
- **Differentiation:** Neurons acquire specific identities (neurotransmitter type, morphology, connectivity)
- **Synaptogenesis:** Formation of synapses (peaks in early postnatal life)
- **Pruning:** Elimination of excess synapses based on activity ("use it or lose it")
- **Myelination:** Wrapping of axons in myelin; continues into the mid-20s (prefrontal cortex myelinates last)

### Lesions

A **lesion** is any area of tissue damage in the nervous system. Lesions can be:

- **Natural:** Stroke, tumor, infection, traumatic brain injury (TBI), neurodegenerative disease
- **Experimental:** Surgically or chemically induced in animal models to study function

**Why lesions matter for neuroscience:**
- Lesion studies follow the logic: if damage to region X impairs function Y, then region X is necessary for function Y
- **Classic examples:**
  - **Phineas Gage (1848):** Damage to the prefrontal cortex → personality changes, impaired decision-making
  - **Patient H.M. (Henry Molaison):** Bilateral medial temporal lobe removal (including hippocampus) → severe anterograde amnesia, demonstrating the hippocampus is critical for forming new declarative memories
  - **Broca's patient "Tan":** Left frontal lobe lesion → expressive aphasia (could understand language but not produce fluent speech)

**Types of lesions:**
- **Ischemic stroke:** Blood supply blocked → tissue death from oxygen deprivation
- **Hemorrhagic stroke:** Blood vessel rupture → bleeding into brain tissue
- **Tumors:** Space-occupying lesions that compress or infiltrate neural tissue
- **Demyelinating lesions:** Loss of myelin (e.g., multiple sclerosis plaques)
- **Traumatic lesions:** Contusions, diffuse axonal injury from TBI

**Limitations of lesion studies:**
- Lesions are rarely confined to a single functional area
- Compensation and plasticity can mask deficits
- Correlation between lesion location and deficit does not prove exclusive localization of function

### Major Brain Regions (Cortex, Cerebellum, Brainstem, Limbic System)

**Cerebral cortex:**
- The outermost layer of the cerebrum; ~2–4 mm thick; highly folded (gyri = ridges, sulci = grooves)
- Contains ~16 billion neurons organized in **6 layers** (neocortex)
- Responsible for higher-order functions: perception, cognition, language, voluntary movement, planning
- Divided into two **hemispheres** connected by the **corpus callosum** (~200 million axons)

**Cerebellum ("little brain"):**
- Located posterior to the brainstem
- Contains ~50% of all brain neurons despite being ~10% of brain volume
- Functions: motor coordination, balance, motor learning, timing
- Receives input from the cortex (via pons) and spinal cord; sends output primarily to motor cortex (via thalamus)
- Damage → **ataxia** (uncoordinated movement), dysmetria, intention tremor

**Brainstem:**
- Connects the cerebrum to the spinal cord; consists of:
  - **Midbrain:** Visual and auditory reflexes (superior and inferior colliculi); contains substantia nigra (dopamine, motor control)
  - **Pons:** Relay between cortex and cerebellum; involved in sleep, respiration, swallowing, bladder control
  - **Medulla oblongata:** Controls vital autonomic functions (breathing, heart rate, blood pressure, vomiting reflex)
- Contains nuclei for cranial nerves III–XII
- Houses the **reticular formation:** Network involved in arousal, attention, sleep-wake cycles

**Limbic system:**
- A set of interconnected structures involved in emotion, memory, and motivation:
  - **Hippocampus:** Critical for forming new declarative memories (episodic and semantic); spatial navigation
  - **Amygdala:** Processes emotions, especially fear and threat detection; emotional memory
  - **Hypothalamus:** Regulates homeostasis (temperature, hunger, thirst, circadian rhythms); controls the pituitary gland (neuroendocrine interface)
  - **Cingulate cortex:** Involved in emotion regulation, error detection, decision-making
  - **Thalamus:** Major relay station; routes sensory information (except olfaction) to appropriate cortical areas

**Other important structures:**
- **Basal ganglia:** Group of subcortical nuclei (caudate, putamen, globus pallidus, subthalamic nucleus, substantia nigra) involved in action selection, motor planning, habit formation, and reward processing. Dysfunction → Parkinson's disease (loss of dopaminergic neurons in substantia nigra), Huntington's disease
- **Thalamus:** "Gateway to the cortex" — nearly all sensory and motor signals pass through it

### Functional Areas (Frontal, Parietal, Temporal, Occipital Lobes)

The cerebral cortex is divided into four lobes, each associated with distinct functions:

**Frontal lobe** (anterior to the central sulcus):
- **Primary motor cortex** (precentral gyrus): Direct control of voluntary movement; somatotopically organized (motor homunculus)
- **Premotor cortex:** Motor planning and preparation
- **Prefrontal cortex (PFC):** Executive functions — working memory, decision-making, planning, impulse control, personality
  - Dorsolateral PFC: Working memory, cognitive flexibility
  - Ventromedial PFC: Emotion regulation, value-based decision-making
  - Orbitofrontal cortex: Reward processing, social behavior
- **Broca's area** (left inferior frontal gyrus): Speech production and language processing

**Parietal lobe** (posterior to the central sulcus, superior):
- **Primary somatosensory cortex** (postcentral gyrus): Processes touch, pressure, temperature, pain; somatotopically organized (sensory homunculus)
- **Posterior parietal cortex:** Spatial awareness, attention, sensorimotor integration
  - Damage → **hemispatial neglect** (typically right parietal damage → neglect of left visual field)
- **Intraparietal sulcus:** Numerical cognition, eye-hand coordination

**Temporal lobe** (lateral, below the lateral sulcus):
- **Primary auditory cortex** (Heschl's gyrus): Processes sound
- **Wernicke's area** (left posterior superior temporal gyrus): Language comprehension
- **Inferior temporal cortex:** Object recognition, face recognition (fusiform face area)
- **Medial temporal lobe:** Contains hippocampus and surrounding cortex — critical for memory

**Occipital lobe** (posterior):
- **Primary visual cortex (V1):** Receives input from the lateral geniculate nucleus (LGN) of the thalamus; processes basic visual features (edges, orientation, color)
- **Extrastriate visual areas (V2, V3, V4, V5/MT):** Progressively more complex visual processing
  - V4: Color processing
  - V5/MT: Motion processing
- **Two visual processing streams:**
  - **Dorsal stream** ("where/how" pathway): Parietal lobe — spatial location, motion, guiding actions
  - **Ventral stream** ("what" pathway): Temporal lobe — object identification, face recognition

---

## 5. Neural Communication and Embodied Emotions

### Neural Communications

**Electrical language of the nervous system:**

Neurons communicate using two types of electrical signals:

1. **Graded potentials:** Local, decremental signals that vary in amplitude proportional to stimulus strength
   - **EPSPs** (excitatory postsynaptic potentials): Depolarize the membrane
   - **IPSPs** (inhibitory postsynaptic potentials): Hyperpolarize the membrane
   - Decay with distance from the synapse; summate spatially and temporally at the axon hillock

2. **Action potentials:** All-or-none, non-decremental signals that propagate along the axon
   - Generated when the sum of graded potentials at the axon hillock reaches threshold (\\(\approx -55\\) mV)
   - Propagate without loss of amplitude due to regeneration at each point along the axon

**Action potential in detail:**

The Hodgkin-Huxley model describes the ionic basis of the action potential using conductance equations:

$$
C_m \frac{dV}{dt} = -g_{\text{Na}} m^3 h (V - E_{\text{Na}}) - g_{\text{K}} n^4 (V - E_{\text{K}}) - g_L (V - E_L) + I_{\text{ext}}
$$

Where:
- \\(C_m\\): Membrane capacitance
- \\(g_{\text{Na}}, g_{\text{K}}, g_L\\): Maximum conductances for Na⁺, K⁺, and leak channels
- \\(m, h, n\\): Gating variables (activation/inactivation)
- \\(E_{\text{Na}}, E_{\text{K}}, E_L\\): Reversal potentials
- \\(I_{\text{ext}}\\): External current

**Conduction velocity** depends on:
- **Axon diameter:** Larger diameter → faster conduction (less internal resistance)
- **Myelination:** Myelinated axons conduct much faster via saltatory conduction
- **Temperature:** Higher temperature → faster conduction (up to a limit)

### Neurotransmitters

**Neurotransmitter Synthesis:**
- **Small-molecule neurotransmitters** (e.g., glutamate, GABA, ACh, dopamine, serotonin): Synthesized locally in the presynaptic terminal by cytoplasmic enzymes
- **Neuropeptides** (e.g., endorphins, substance P, neuropeptide Y): Synthesized in the soma (ribosome → ER → Golgi) and transported to the terminal via axonal transport

**Key biosynthetic pathways:**
- **Catecholamines:** Tyrosine → L-DOPA (tyrosine hydroxylase, rate-limiting) → Dopamine (DOPA decarboxylase) → Norepinephrine (dopamine β-hydroxylase) → Epinephrine (PNMT)
- **Serotonin:** Tryptophan → 5-HTP (tryptophan hydroxylase) → Serotonin (aromatic amino acid decarboxylase)
- **Acetylcholine:** Choline + Acetyl-CoA → ACh (choline acetyltransferase, ChAT)

**Neurotransmitter Release:**
1. Action potential invades the presynaptic terminal
2. Depolarization opens voltage-gated **Ca²⁺ channels**
3. Ca²⁺ influx triggers vesicle docking and fusion via the **SNARE complex:**
   - **Synaptobrevin** (v-SNARE, on vesicle)
   - **Syntaxin** and **SNAP-25** (t-SNAREs, on target membrane)
   - **Synaptotagmin** acts as the Ca²⁺ sensor
4. Vesicle contents are released into the synaptic cleft by **exocytosis**
5. Release is **quantal:** Each vesicle releases a fixed amount of neurotransmitter

**Clostridial Toxins: Botox**
- **Botulinum toxin (Botox)** and **tetanus toxin** are produced by *Clostridium* bacteria
- Both are **zinc-dependent proteases** that cleave SNARE proteins, blocking neurotransmitter release
- **Botulinum toxin:** Cleaves SNAP-25 or synaptobrevin at the **neuromuscular junction** → flaccid paralysis (muscle cannot contract). Medical uses: treating muscle spasticity, migraines, cosmetic wrinkle reduction
- **Tetanus toxin:** Transported retrogradely to inhibitory interneurons in the spinal cord → blocks GABA/glycine release → spastic paralysis (muscles cannot relax)

**Signal Termination:**
Neurotransmitter action must be terminated to allow precise signaling:
1. **Reuptake:** Transporter proteins on the presynaptic terminal (or glia) pump neurotransmitter back in
   - Examples: DAT (dopamine transporter), SERT (serotonin transporter), NET (norepinephrine transporter)
   - **SSRIs** (e.g., fluoxetine/Prozac) block SERT → increase serotonin in the cleft
   - **Cocaine** blocks DAT → increase dopamine in the cleft
2. **Enzymatic degradation:**
   - **Acetylcholinesterase (AChE):** Breaks down ACh → choline + acetate (choline is recycled)
   - **MAO (monoamine oxidase):** Degrades monoamines (DA, NE, 5-HT) inside the presynaptic terminal
   - **COMT (catechol-O-methyltransferase):** Degrades catecholamines extracellularly
3. **Diffusion:** Neurotransmitter drifts away from the synaptic cleft

**Receptors:**
- **Ionotropic (ligand-gated ion channels):** Direct, fast transmission (~1 ms)
  - Neurotransmitter binds → channel opens → ions flow → rapid change in membrane potential
  - Examples: Nicotinic ACh receptor (Na⁺), AMPA receptor (Na⁺), NMDA receptor (Na⁺/Ca²⁺), GABA-A receptor (Cl⁻)
- **Metabotropic (G-protein coupled receptors):** Indirect, slower, longer-lasting effects (~seconds to minutes)
  - Neurotransmitter binds → G-protein activated → second messenger cascade → diverse cellular effects

**Metabotropic Receptors in detail:**
- Consist of **7 transmembrane domains** coupled to intracellular **G-proteins** (Gα, Gβ, Gγ subunits)
- **G-protein signaling:**
  1. Neurotransmitter binds receptor → conformational change
  2. Gα subunit exchanges GDP for GTP → G-protein dissociates into Gα-GTP and Gβγ
  3. Subunits activate effector enzymes (adenylyl cyclase, phospholipase C)
  4. **Second messengers** produced:
     - **cAMP** (from adenylyl cyclase) → activates **PKA** (protein kinase A)
     - **IP₃** and **DAG** (from phospholipase C) → IP₃ releases Ca²⁺ from ER; DAG activates **PKC**
  5. Kinases phosphorylate target proteins → alter ion channels, gene expression, synaptic strength
- **Gs** (stimulatory): Increases cAMP
- **Gi** (inhibitory): Decreases cAMP
- **Gq:** Activates phospholipase C → IP₃/DAG pathway

### Embodied Emotions

**Enteric Nervous System (ENS):**
- Often called the "second brain" — a semi-autonomous network of ~500 million neurons embedded in the walls of the gastrointestinal tract
- Organized into two plexuses:
  - **Myenteric (Auerbach's) plexus:** Between muscle layers; controls motility (peristalsis)
  - **Submucosal (Meissner's) plexus:** In the submucosa; controls secretion and blood flow
- Can function independently of the CNS but is modulated by the autonomic nervous system
- Produces ~95% of the body's serotonin
- **Gut-brain axis:** Bidirectional communication between the ENS and CNS via the vagus nerve, immune signaling, and microbial metabolites. Implicated in mood disorders, stress responses, and conditions like irritable bowel syndrome (IBS)

**Parasympathetics & Sympathetics:**

The **autonomic nervous system (ANS)** regulates involuntary bodily functions through two opposing divisions:

| Feature | Sympathetic | Parasympathetic |
|---------|-------------|-----------------|
| **Nickname** | "Fight or flight" | "Rest and digest" |
| **Origin** | Thoracolumbar spinal cord (T1–L2) | Craniosacral (brainstem + S2–S4) |
| **Ganglia** | Close to spinal cord (paravertebral chain) | Close to or within target organs |
| **Preganglionic NT** | ACh (nicotinic receptors) | ACh (nicotinic receptors) |
| **Postganglionic NT** | Norepinephrine (adrenergic receptors) | ACh (muscarinic receptors) |
| **Heart rate** | Increases | Decreases |
| **Pupils** | Dilates (mydriasis) | Constricts (miosis) |
| **Digestion** | Inhibits | Stimulates |
| **Bronchi** | Dilates | Constricts |
| **Blood pressure** | Increases | Decreases |

**Parasympathetic/Sympathetic Balance:**
- Health depends on appropriate balance between the two divisions
- **Chronic sympathetic activation** (chronic stress) → hypertension, immune suppression, anxiety, digestive problems
- **Vagal tone** (parasympathetic activity via the vagus nerve) is associated with emotional regulation, social engagement, and resilience
- **Heart rate variability (HRV):** A measure of autonomic balance; higher HRV generally indicates better parasympathetic tone and cardiovascular health

**Autonomic Pharmacology:**
- **Cholinergic agonists** (e.g., pilocarpine): Mimic parasympathetic activation → constrict pupils, increase secretions
- **Cholinergic antagonists** (e.g., atropine): Block parasympathetic effects → dilate pupils, increase heart rate, dry mouth
- **Adrenergic agonists** (e.g., epinephrine): Mimic sympathetic activation → increase heart rate, dilate bronchi
  - **α-agonists:** Vasoconstriction
  - **β-agonists:** Bronchodilation (β₂), increased heart rate (β₁)
- **Adrenergic antagonists (beta-blockers)** (e.g., propranolol): Block sympathetic effects → decrease heart rate, lower blood pressure
- **Nerve agents** (e.g., sarin): Inhibit acetylcholinesterase → excess ACh → overstimulation of both muscarinic and nicotinic receptors → paralysis, death

**Spinal Cord Injury:**
- Damage to the spinal cord disrupts communication between the brain and the body below the level of injury
- **Effects depend on the level and completeness of injury:**
  - **Cervical (C1–C8):** Quadriplegia/tetraplegia (all four limbs affected)
  - **Thoracic (T1–T12):** Paraplegia (lower limbs affected)
  - **Complete injury:** Total loss of motor and sensory function below the lesion
  - **Incomplete injury:** Some function preserved (Brown-Séquard syndrome, central cord syndrome, etc.)
- **Autonomic dysreflexia:** In injuries above T6, noxious stimuli below the injury can trigger a massive sympathetic response (dangerously high blood pressure) because descending inhibitory signals from the brain cannot reach the sympathetic neurons
- **Neurogenic shock:** Loss of sympathetic tone immediately after injury → hypotension, bradycardia
- **Spinal cord injury research:** Stem cell therapy, electrical stimulation, neuroprosthetics, and pharmacological approaches are active areas of investigation

---

## 6. Perception and Vision

**Sensory systems** transduce physical stimuli into neural signals through specialized receptors:

| Sense | Stimulus | Receptor Type | Primary Cortical Area |
|-------|----------|---------------|----------------------|
| **Vision** | Light (photons) | Photoreceptors (rods, cones) | V1 (occipital lobe) |
| **Hearing** | Sound waves | Hair cells (cochlea) | A1 (temporal lobe) |
| **Touch** | Mechanical pressure | Mechanoreceptors | S1 (parietal lobe) |
| **Taste** | Chemical (dissolved) | Gustatory receptor cells | Gustatory cortex (insula) |
| **Smell** | Chemical (airborne) | Olfactory receptor neurons | Olfactory cortex (piriform) |

**General principles of sensory processing:**
- **Transduction:** Conversion of stimulus energy into electrical signals (receptor potentials)
- **Labeled line coding:** Each sensory pathway carries information about a specific modality
- **Topographic mapping:** Spatial organization of the stimulus is preserved in cortical maps (retinotopy, tonotopy, somatotopy)
- **Adaptation:** Decreased response to sustained stimuli (allows detection of changes)
- **Receptive field:** The region of sensory space that activates a given neuron

### Vision

**The visual pathway:**
1. Light enters the eye → focused by the cornea and lens onto the **retina**
2. **Photoreceptors** transduce light:
   - **Rods** (~120 million): High sensitivity, low acuity, no color; scotopic (dim light) vision
   - **Cones** (~6 million): Low sensitivity, high acuity, color vision; photopic (bright light) vision
     - Three types: S-cones (blue, ~420 nm), M-cones (green, ~530 nm), L-cones (red, ~560 nm)
3. Signal passes through retinal layers: photoreceptors → bipolar cells → retinal ganglion cells (RGCs)
   - Lateral processing by **horizontal cells** and **amacrine cells** enhances contrast
4. RGC axons form the **optic nerve** → partial crossing at the **optic chiasm** (nasal fibers cross, temporal fibers don't)
5. **Lateral geniculate nucleus (LGN)** of the thalamus: Relay station with 6 layers
   - Magnocellular layers (1–2): Motion, depth (from M-type RGCs)
   - Parvocellular layers (3–6): Color, fine detail (from P-type RGCs)
6. LGN → **Primary visual cortex (V1)** via optic radiations

**Visual cortex processing:**
- **V1 (striate cortex):** Organized in columns
  - **Simple cells:** Respond to oriented edges/bars at specific positions (Hubel & Wiesel, Nobel Prize 1981)
  - **Complex cells:** Respond to oriented edges regardless of exact position (position invariance)
  - **Hypercomplex cells:** Respond to edges of specific length (end-stopping)
  - **Ocular dominance columns:** Alternating columns preferring input from left or right eye
  - **Orientation columns:** Neurons with similar preferred orientations are grouped together
- **V2:** Processes illusory contours, texture boundaries
- **V4:** Color processing, shape recognition
- **V5/MT:** Motion processing, direction selectivity

**Two visual streams:**
- **Ventral stream** (V1 → V2 → V4 → inferior temporal cortex): "What" pathway — object recognition, face perception
- **Dorsal stream** (V1 → V2 → V5/MT → posterior parietal cortex): "Where/How" pathway — spatial location, motion, visually guided action

### Motor Pathways & Control

**Motor hierarchy:**
1. **Motor cortex** (planning and initiation):
   - **Primary motor cortex (M1):** Direct control of voluntary movement; somatotopically organized
   - **Premotor cortex:** Motor planning, selecting movements based on context
   - **Supplementary motor area (SMA):** Planning complex sequences, bimanual coordination
2. **Basal ganglia** (action selection and modulation):
   - **Direct pathway:** Facilitates desired movements (cortex → striatum → GPi/SNr → thalamus → cortex)
   - **Indirect pathway:** Suppresses competing movements (cortex → striatum → GPe → STN → GPi/SNr → thalamus)
   - Dopamine from substantia nigra modulates both pathways
3. **Cerebellum** (coordination and error correction):
   - Compares intended movement with actual movement; corrects errors in real-time
   - Critical for motor learning, timing, and smooth execution
4. **Brainstem and spinal cord** (execution):
   - **Upper motor neurons:** Originate in cortex/brainstem; project to spinal cord
   - **Lower motor neurons:** In spinal cord ventral horn; directly innervate muscles
   - **Corticospinal (pyramidal) tract:** Primary pathway for voluntary movement; ~90% of fibers cross at the medullary pyramids (decussation)

**Reflexes:**
- **Monosynaptic reflex (stretch reflex):** Sensory neuron → motor neuron (e.g., knee-jerk reflex)
- **Polysynaptic reflex (withdrawal reflex):** Involves interneurons; more complex (e.g., pulling hand from hot surface)

---

## 7. Hearing

### Auditory System

**Sound** is a mechanical wave characterized by:
- **Frequency** (Hz): Perceived as pitch (human range: ~20 Hz – 20,000 Hz)
- **Amplitude** (dB): Perceived as loudness
- **Timbre:** Complexity of the waveform (distinguishes instruments/voices)

**The auditory pathway:**

1. **Outer ear:**
   - **Pinna:** Collects and funnels sound waves
   - **Ear canal (external auditory meatus):** Directs sound to the tympanic membrane
   - **Tympanic membrane (eardrum):** Vibrates in response to sound waves

2. **Middle ear:**
   - Three **ossicles** (smallest bones in the body): **Malleus** → **Incus** → **Stapes**
   - Amplify sound vibrations (~22× gain) and transmit them to the oval window
   - **Impedance matching:** Overcomes the air-to-fluid transition (air → cochlear fluid)
   - **Stapedius reflex:** Contracts to dampen loud sounds and protect the inner ear

3. **Inner ear (cochlea):**
   - Fluid-filled, snail-shaped structure with three chambers:
     - **Scala vestibuli** (perilymph)
     - **Scala media / cochlear duct** (endolymph)
     - **Scala tympani** (perilymph)
   - **Organ of Corti:** Sits on the basilar membrane; contains **hair cells** (the sensory receptors)
     - **Inner hair cells (~3,500):** Primary sensory transducers; convert mechanical vibration into electrical signals
     - **Outer hair cells (~12,000):** Amplify and sharpen the traveling wave via electromotility (prestin protein)
   - **Tonotopic organization:** The basilar membrane is tuned to different frequencies along its length
     - **Base:** Narrow, stiff → high frequencies
     - **Apex:** Wide, flexible → low frequencies
   - **Mechanoelectrical transduction:** Stereocilia on hair cells bend → tip links open mechanically gated ion channels → K⁺ influx (from endolymph) → depolarization → neurotransmitter release onto auditory nerve fibers

4. **Central auditory pathway:**
   - **Auditory nerve (CN VIII)** → **Cochlear nuclei** (brainstem) → **Superior olivary complex** (first site of binaural processing; sound localization) → **Inferior colliculus** (midbrain) → **Medial geniculate nucleus (MGN)** of the thalamus → **Primary auditory cortex (A1)** (Heschl's gyrus, temporal lobe)
   - **Tonotopic maps** are preserved at each level of the pathway

**Sound localization cues:**
- **Interaural time difference (ITD):** Difference in arrival time between the two ears (for low frequencies)
- **Interaural level difference (ILD):** Difference in sound intensity between the two ears (for high frequencies, due to head shadow)

**Hearing loss:**
- **Conductive:** Problem in outer/middle ear (e.g., otosclerosis, fluid in middle ear)
- **Sensorineural:** Damage to hair cells or auditory nerve (e.g., noise exposure, aging/presbycusis, ototoxic drugs)
- **Central:** Damage to central auditory pathways (rare)
- **Cochlear implants:** Bypass damaged hair cells; directly stimulate the auditory nerve with electrical signals

---

## 8. Higher Cognitive Functions

### The Vestibular Sense and Gaze

The **vestibular system** detects head position and movement, enabling balance and stable gaze:

- Located in the **inner ear** (vestibular labyrinth):
  - **Three semicircular canals:** Detect rotational acceleration (angular motion) in three planes
    - Each canal contains a **cupula** with hair cells that bend when endolymph moves
  - **Otolith organs (utricle and saccule):** Detect linear acceleration and head tilt (gravity)
    - Hair cells embedded in a gelatinous membrane weighted with **otoconia** (calcium carbonate crystals)

- **Vestibulo-ocular reflex (VOR):** Stabilizes gaze during head movement by producing compensatory eye movements in the opposite direction
  - Three-neuron arc: Vestibular nerve → vestibular nuclei → oculomotor nuclei → extraocular muscles
  - Gain ≈ 1.0 (eye movement magnitude matches head movement)

- **Vestibular disorders:**
  - **Benign paroxysmal positional vertigo (BPPV):** Displaced otoconia in semicircular canals
  - **Ménière's disease:** Excess endolymph → vertigo, hearing loss, tinnitus
  - **Vestibular neuritis:** Inflammation of the vestibular nerve

### Memory and Learning

**Memory** is the ability to encode, store, and retrieve information. It is not a single system but a collection of distinct processes:

**Memory taxonomy:**
- **Sensory memory:** Ultra-brief storage (~250 ms for iconic/visual; ~3–4 s for echoic/auditory)
- **Short-term / Working memory:** Limited capacity (~7 ± 2 items, or ~4 chunks); duration ~20–30 s without rehearsal
  - **Baddeley's model of working memory:**
    - **Central executive:** Attentional control system
    - **Phonological loop:** Verbal/acoustic information
    - **Visuospatial sketchpad:** Visual/spatial information
    - **Episodic buffer:** Integrates information from multiple sources
- **Long-term memory:**
  - **Declarative (explicit):** Conscious recall
    - *Episodic:* Personal experiences (hippocampus-dependent)
    - *Semantic:* Facts and general knowledge (can become hippocampus-independent over time)
  - **Non-declarative (implicit):** Unconscious
    - *Procedural:* Skills and habits (basal ganglia, cerebellum)
    - *Priming:* Facilitated processing of previously encountered stimuli (cortex)
    - *Classical conditioning:* Associative learning (cerebellum for motor; amygdala for emotional)

**Neural basis of memory:**
- **Hippocampus:** Essential for consolidating new declarative memories; spatial memory (place cells, grid cells)
- **Long-term potentiation (LTP):** A persistent strengthening of synaptic connections following high-frequency stimulation — widely considered a cellular mechanism of learning

$$
\Delta w_{ij} \propto x_i \cdot x_j
$$

This Hebbian principle ("neurons that fire together wire together") underlies LTP:
  - **Early LTP:** Requires AMPA receptor phosphorylation and trafficking (minutes to hours)
  - **Late LTP:** Requires new protein synthesis and structural changes (hours to days)
  - **NMDA receptors** act as coincidence detectors: require both presynaptic glutamate release AND postsynaptic depolarization to open → Ca²⁺ influx → triggers LTP

- **Memory consolidation:**
  - **Synaptic consolidation:** Rapid (hours); molecular changes at the synapse
  - **Systems consolidation:** Slow (weeks to years); memories gradually become independent of the hippocampus and stored in neocortex (standard consolidation theory)
  - **Sleep** plays a critical role: replay of neural activity patterns during slow-wave sleep strengthens memories

### Language

**Language** is a uniquely human cognitive capacity involving the production and comprehension of structured symbolic communication.

**Key brain areas:**
- **Broca's area** (left inferior frontal gyrus, BA 44/45): Speech production, syntactic processing
  - Damage → **Broca's aphasia:** Non-fluent, effortful speech; relatively preserved comprehension; impaired grammar
- **Wernicke's area** (left posterior superior temporal gyrus, BA 22): Language comprehension
  - Damage → **Wernicke's aphasia:** Fluent but meaningless speech ("word salad"); impaired comprehension
- **Arcuate fasciculus:** White matter tract connecting Broca's and Wernicke's areas
  - Damage → **Conduction aphasia:** Impaired repetition; relatively preserved production and comprehension
- **Angular gyrus:** Reading, writing, semantic processing
- **Supplementary motor area:** Speech initiation

**Dual-stream model of language (Hickok & Poeppel):**
- **Ventral stream:** Sound → meaning (temporal lobe)
- **Dorsal stream:** Sound → articulation (parietal-frontal pathway)

**Lateralization:** Language is predominantly left-lateralized in ~95% of right-handers and ~70% of left-handers.

### Attention and Consciousness

**Attention** is the selective allocation of cognitive resources to specific stimuli or tasks.

**Types of attention:**
- **Selective attention:** Focusing on one stimulus while ignoring others (e.g., cocktail party effect)
- **Sustained attention (vigilance):** Maintaining focus over extended periods
- **Divided attention:** Attending to multiple tasks simultaneously
- **Executive attention:** Resolving conflict between competing responses (e.g., Stroop task)

**Neural basis of attention:**
- **Dorsal attention network:** Top-down, voluntary attention (frontal eye fields + intraparietal sulcus)
- **Ventral attention network:** Bottom-up, stimulus-driven attention (temporoparietal junction + ventral frontal cortex)
- **Thalamic reticular nucleus:** Gates sensory information reaching the cortex
- **Neurotransmitters:** Acetylcholine (enhances signal-to-noise), norepinephrine (arousal and alerting)

**Consciousness** remains one of the deepest unsolved problems in neuroscience:
- **Neural correlates of consciousness (NCC):** The minimal set of neural events sufficient for a specific conscious experience
- **Key theories:**
  - **Global Workspace Theory (Baars, Dehaene):** Consciousness arises when information is broadcast widely across cortical areas via a "global workspace" (frontoparietal network)
  - **Integrated Information Theory (Tononi):** Consciousness corresponds to integrated information (\\(\Phi\\)); a system is conscious to the degree that it is both differentiated and integrated
  - **Higher-Order Theories:** Consciousness requires a higher-order representation of one's own mental states (prefrontal cortex)
  - **Predictive Processing:** Consciousness is the brain's best prediction about the causes of sensory input

### Emotion and Motivation

**Emotion** involves subjective experience, physiological arousal, and behavioral expression.

**Key theories of emotion:**
- **James-Lange theory:** Emotion is the perception of bodily changes (stimulus → physiological response → emotion)
- **Cannon-Bard theory:** Physiological response and emotional experience occur simultaneously
- **Schachter-Singer (two-factor) theory:** Emotion = physiological arousal + cognitive interpretation
- **Appraisal theories:** Emotions arise from cognitive evaluation of events relative to goals
- **Constructionist theories (Lisa Feldman Barrett):** Emotions are constructed from domain-general ingredients (interoception, affect, conceptual knowledge)

**Neural circuits of emotion:**
- **Amygdala:** Central hub for threat detection and fear conditioning
  - Receives sensory input via two routes:
    - **Low road (thalamus → amygdala):** Fast, crude processing
    - **High road (thalamus → cortex → amygdala):** Slower, detailed processing
  - Damage → impaired fear recognition and conditioning (patient S.M.)
- **Prefrontal cortex:** Emotion regulation, reappraisal
  - vmPFC: Extinction of conditioned fear
  - dlPFC: Cognitive reappraisal
- **Insula:** Interoception (awareness of internal bodily states); disgust
- **Anterior cingulate cortex (ACC):** Conflict monitoring, emotional pain

**Motivation and reward:**
- **Mesolimbic dopamine pathway:** Ventral tegmental area (VTA) → nucleus accumbens (NAc) → prefrontal cortex
- **Reward prediction error (Schultz et al.):** Dopamine neurons fire when reward exceeds expectation; pause when reward is less than expected

$$
\delta_t = r_t + \gamma V(s_{t+1}) - V(s_t)
$$

This is the **temporal difference (TD) error**, which mirrors the firing pattern of dopamine neurons and is a foundational concept in reinforcement learning.

- **Wanting vs. liking (Berridge):**
  - *Wanting* (incentive salience): Dopamine-mediated; drives approach behavior
  - *Liking* (hedonic pleasure): Opioid/endocannabinoid-mediated; smaller "hedonic hotspots" in NAc and brainstem

---

## 9. Methods in Neuroscience

### Imaging (fMRI, PET, EEG, MEG)

| Method | Measures | Spatial Resolution | Temporal Resolution | Invasive? |
|--------|----------|-------------------|---------------------|-----------|
| **fMRI** | Blood oxygenation (BOLD signal) | ~1–3 mm | ~1–2 s | No |
| **PET** | Radiotracer distribution (metabolism, receptor binding) | ~4–6 mm | ~30–60 s | Yes (radiotracer injection) |
| **EEG** | Electrical potentials at scalp | ~1–2 cm | ~1 ms | No |
| **MEG** | Magnetic fields from neural currents | ~2–3 mm | ~1 ms | No |
| **CT** | X-ray absorption (structural) | ~0.5–1 mm | N/A (structural) | Radiation exposure |
| **MRI** | Proton relaxation (structural) | ~0.5–1 mm | N/A (structural) | No |
| **DTI** | Water diffusion along white matter tracts | ~2 mm | N/A (structural) | No |

**fMRI (functional Magnetic Resonance Imaging):**
- Measures the **BOLD (Blood-Oxygen-Level-Dependent)** signal: active brain regions consume more oxygen → local increase in oxygenated hemoglobin → detectable change in MRI signal
- Excellent spatial resolution but limited temporal resolution (hemodynamic response peaks ~5–6 s after neural activity)
- Common analyses: activation maps, functional connectivity, multivariate pattern analysis (MVPA)

**EEG (Electroencephalography):**
- Records electrical activity from electrodes on the scalp
- Excellent temporal resolution (~ms) but poor spatial resolution (volume conduction, inverse problem)
- **Event-related potentials (ERPs):** Averaged EEG responses time-locked to stimuli
  - N170: Face processing
  - P300: Attention and working memory updating
  - N400: Semantic processing
  - P600: Syntactic processing

### Electrophysiology

- **Single-unit recording:** Microelectrode inserted near or into a neuron; records action potentials from individual neurons (gold standard for spatial and temporal precision; invasive)
- **Multi-electrode arrays:** Record from many neurons simultaneously; reveal population coding
- **Patch clamp:** Records ionic currents through individual ion channels (whole-cell, cell-attached, inside-out, outside-out configurations)
- **Local field potential (LFP):** Summed electrical activity from a local population of neurons
- **Optogenetics:** Genetically express light-sensitive ion channels (e.g., channelrhodopsin) in specific neuron types → activate or silence neurons with light (millisecond precision, cell-type specificity)

### Lesion Studies

- **Natural lesions:** Stroke, TBI, tumors, neurodegenerative disease → correlate damage location with behavioral deficits
- **Experimental lesions (animal models):**
  - **Ablation:** Surgical removal of brain tissue
  - **Electrolytic lesion:** Destroy tissue with electrical current (damages both cell bodies and fibers of passage)
  - **Excitotoxic lesion:** Inject excitatory amino acids (e.g., ibotenic acid) → selectively destroys cell bodies, spares fibers of passage
  - **Reversible inactivation:** Cooling, muscimol (GABA-A agonist), or optogenetic silencing → temporary "lesion"
- **Transcranial magnetic stimulation (TMS):** Non-invasive; creates a temporary "virtual lesion" in humans by disrupting cortical activity with magnetic pulses

**Limitations:** Lesions are rarely clean; diaschisis (remote effects of local damage); plasticity and compensation

### Computational Models

- **Biophysical models:** Hodgkin-Huxley equations, compartmental models of neurons (simulate ion channel dynamics, dendritic integration)
- **Neural network models:** Connectionist models, rate-based networks, spiking neural networks
- **Bayesian models:** Model perception and decision-making as probabilistic inference
- **Reinforcement learning models:** TD learning, actor-critic models (link to dopamine reward prediction error)
- **Dynamical systems models:** Describe neural population activity as trajectories in state space
- **Encoding/decoding models:** Predict neural activity from stimuli (encoding) or reconstruct stimuli from neural activity (decoding / brain-computer interfaces)

---

## 10. Disorders of the Nervous System

### Neurological Disorders

**Epilepsy:**
- Characterized by recurrent, unprovoked seizures caused by abnormal, excessive, or synchronous neuronal activity
- **Types:** Focal (partial) seizures vs. generalized seizures (absence, tonic-clonic)
- **Mechanisms:** Imbalance between excitation (glutamate) and inhibition (GABA); ion channel mutations (channelopathies)
- **Treatment:** Antiepileptic drugs (e.g., valproate, carbamazepine, levetiracetam); surgery for drug-resistant cases; vagus nerve stimulation

**Stroke:**
- Sudden interruption of blood supply to the brain
- **Ischemic stroke (~85%):** Blood clot blocks a cerebral artery → tissue death (infarction)
- **Hemorrhagic stroke (~15%):** Blood vessel rupture → bleeding into brain tissue
- **Treatment:** Thrombolytics (tPA) for ischemic stroke within ~4.5 hours; mechanical thrombectomy; rehabilitation
- Deficits depend on location: motor, sensory, language, cognitive, visual

**Parkinson's disease:**
- Progressive loss of dopaminergic neurons in the **substantia nigra pars compacta**
- **Cardinal symptoms:** Resting tremor, rigidity, bradykinesia (slowness), postural instability
- **Pathology:** Lewy bodies (α-synuclein aggregates)
- **Treatment:** L-DOPA (dopamine precursor), dopamine agonists, MAO-B inhibitors, deep brain stimulation (DBS) of the subthalamic nucleus

**Alzheimer's disease:**
- Most common cause of dementia; progressive neurodegeneration
- **Pathology:** Amyloid-β plaques (extracellular) and neurofibrillary tangles (intracellular, hyperphosphorylated tau protein)
- **Symptoms:** Memory loss (hippocampus affected early), language difficulties, disorientation, personality changes
- **Treatment:** Cholinesterase inhibitors (donepezil), NMDA receptor antagonists (memantine); anti-amyloid antibodies (lecanemab, aducanumab — recent, controversial)

**Multiple sclerosis (MS):**
- Autoimmune demyelination of CNS axons → disrupted signal conduction
- **Symptoms:** Variable — visual disturbances, motor weakness, sensory changes, fatigue, cognitive impairment
- **Relapsing-remitting** (most common) vs. progressive forms

### Psychiatric Disorders

**Major depressive disorder (MDD):**
- Persistent low mood, anhedonia, fatigue, sleep/appetite changes, cognitive impairment, suicidal ideation
- **Monoamine hypothesis:** Deficiency in serotonin, norepinephrine, and/or dopamine (supported by efficacy of SSRIs, SNRIs, MAOIs — but oversimplified)
- **Neuroplasticity hypothesis:** Reduced BDNF, hippocampal atrophy, impaired neurogenesis
- **Network dysfunction:** Hyperactive default mode network (rumination), hypoactive prefrontal cortex (cognitive control)
- **Treatment:** Antidepressants, psychotherapy (CBT), ECT, ketamine (rapid-acting, NMDA antagonist), TMS

**Schizophrenia:**
- Chronic disorder with positive symptoms (hallucinations, delusions, disorganized thought), negative symptoms (flat affect, avolition, social withdrawal), and cognitive deficits
- **Dopamine hypothesis:** Excess dopamine in mesolimbic pathway (positive symptoms); deficit in mesocortical pathway (negative/cognitive symptoms)
- **Glutamate hypothesis:** NMDA receptor hypofunction (supported by PCP/ketamine-induced psychosis)
- **Neurodevelopmental factors:** Genetic risk, prenatal infection, synaptic pruning abnormalities in adolescence
- **Treatment:** Antipsychotics (D2 receptor antagonists: typical and atypical), psychosocial interventions

### Developmental Disorders

**Autism spectrum disorder (ASD):**
- Characterized by persistent deficits in social communication/interaction and restricted, repetitive behaviors
- **Neural basis:** Altered connectivity (both over- and under-connectivity); differences in mirror neuron system, amygdala, prefrontal cortex
- **Genetics:** Highly heritable (~80%); hundreds of risk genes identified; often de novo mutations
- **Synaptic theories:** Excitation/inhibition imbalance; altered synaptic pruning

**Attention-deficit/hyperactivity disorder (ADHD):**
- Persistent inattention, hyperactivity, and impulsivity
- **Neural basis:** Reduced prefrontal cortex volume and activity; altered dopamine and norepinephrine signaling in fronto-striatal circuits
- **Treatment:** Stimulant medications (methylphenidate, amphetamines) increase dopamine/norepinephrine in PFC; behavioral therapy

---

## 11. Neuroscience & Artificial Intelligence

**Inspiration from Neuroscience:**
- **Neurons → artificial neural networks:** The perceptron (Rosenblatt, 1958) was directly inspired by biological neurons. Modern deep learning uses artificial neurons with weighted inputs, nonlinear activation functions, and layered architectures
- **Hebbian learning → learning rules in AI:** "Neurons that fire together wire together" (Hebb, 1949) inspired associative learning rules. Backpropagation, while not biologically realistic, achieves a similar goal of adjusting connection strengths based on error
- **Visual cortex → convolutional neural networks (CNNs):** Hubel & Wiesel's discovery of simple and complex cells in V1 directly inspired the architecture of CNNs (Fukushima's Neocognitron, 1980; LeCun's LeNet, 1989) — hierarchical feature extraction with local receptive fields and weight sharing
- **Reinforcement learning:** TD learning in AI mirrors dopamine reward prediction error signals in the basal ganglia (Schultz et al., 1997)
- **Attention mechanisms:** The attention mechanism in Transformers (Vaswani et al., 2017) draws loose inspiration from selective attention in the brain

**Feedback from AI to Neuroscience:**
- **Deep learning models as brain models:** Deep neural networks (especially CNNs for vision and RNNs/Transformers for language) are used as computational models of brain processing. Representational similarity analysis (RSA) compares internal representations of DNNs with neural recordings
- **Tools for analyzing neural data:** Machine learning techniques (dimensionality reduction, decoding, clustering) are essential for analyzing high-dimensional neural data from multi-electrode arrays, calcium imaging, and fMRI
- **Brain-computer interfaces (BCIs):** Deep learning decodes neural signals for prosthetic control, speech synthesis from brain activity, and communication for locked-in patients

**Shared Challenges:**
- **Representation and abstraction:** How do brains and AI systems form useful internal representations of the world? Both face the challenge of extracting invariant features from high-dimensional, noisy input
- **Learning, memory, and generalization:** Biological systems excel at few-shot learning and transfer; AI systems require massive data but can generalize in different ways. Understanding the gap is a frontier for both fields
- **Catastrophic forgetting:** Neural networks forget old tasks when trained on new ones; the brain uses complementary learning systems (hippocampus for rapid learning, neocortex for slow consolidation) to avoid this
- **Credit assignment:** How does the brain determine which synapses to strengthen or weaken? Backpropagation solves this in AI but is considered biologically implausible; alternatives (e.g., predictive coding, feedback alignment) are active research areas

**Frontiers:**
- **Brain-inspired computing (neuromorphic chips):** Hardware that mimics neural architecture — event-driven, massively parallel, energy-efficient (e.g., Intel Loihi, IBM TrueNorth, SpiNNaker)
- **Cognitive architectures & large language models:** LLMs exhibit emergent capabilities (reasoning, in-context learning) that invite comparison with human cognition. Do they understand, or merely pattern-match? This question connects to debates about consciousness and intentionality
- **Ethical considerations of human-AI parallels:** As AI systems become more brain-like, questions arise about machine consciousness, moral status, and the implications of brain-reading technology for privacy and autonomy

---

## 12. Applications & Future Directions

### Neurotechnology

- **Brain-computer interfaces (BCIs):**
  - **Invasive:** Implanted electrode arrays (e.g., Utah array, Neuralink) → high-resolution neural recording → control of prosthetic limbs, computer cursors, speech synthesizers
  - **Non-invasive:** EEG-based BCIs → slower but safer → spelling devices, wheelchair control, neurofeedback
  - **Recent milestones:** Paralyzed patients typing via imagined handwriting (Willett et al., 2021); speech decoding from neural activity (Moses et al., 2021; Metzger et al., 2023)

- **Neuroprosthetics:**
  - **Cochlear implants:** Bypass damaged hair cells; directly stimulate auditory nerve → restore hearing
  - **Retinal implants:** Stimulate remaining retinal neurons → partial vision restoration
  - **Deep brain stimulation (DBS):** Implanted electrodes deliver electrical pulses to specific brain regions → treat Parkinson's, essential tremor, dystonia, treatment-resistant depression, OCD

- **Neurostimulation:**
  - **Transcranial magnetic stimulation (TMS):** Non-invasive; magnetic pulses modulate cortical excitability → treat depression, study brain function
  - **Transcranial direct current stimulation (tDCS):** Weak electrical current through scalp electrodes → modulate neural excitability
  - **Focused ultrasound:** Non-invasive, deep brain stimulation with millimeter precision

### AI and Computational Neuroscience

- **Neural data analysis:** Machine learning for spike sorting, calcium imaging analysis, fMRI decoding, connectomics
- **In silico neuroscience:** Large-scale brain simulations (e.g., Human Brain Project, Blue Brain Project) → test hypotheses about neural circuit function
- **Normative models:** Use optimization principles (e.g., efficient coding, Bayesian inference, reward maximization) to predict what neural circuits *should* compute
- **Digital twins:** Personalized computational models of individual brains for treatment planning (e.g., epilepsy surgery planning)

### Neuroethics

- **Cognitive enhancement:** Is it ethical to use neurostimulation or pharmacology to enhance cognition in healthy individuals? Fairness, access, and coercion concerns
- **Brain privacy:** As neural decoding improves, can thoughts be "read"? Implications for legal systems, surveillance, and personal autonomy
- **Consciousness and moral status:** If AI systems or brain organoids develop consciousness-like properties, what moral obligations do we have?
- **Neurodeterminism and free will:** If behavior is determined by neural processes, what are the implications for moral responsibility and the justice system?
- **Dual use:** Neurotechnology developed for medical purposes could be repurposed for military applications, interrogation, or manipulation
- **Informed consent:** Patients with brain disorders may have impaired decision-making capacity — how do we ensure ethical consent for experimental neurotechnologies?

---

### References
- Kandel, E. R., Schwartz, J. H., Jessell, T. M., Siegelbaum, S. A., & Hudspeth, A. J. (2013). *Principles of Neural Science* (5th ed.). McGraw-Hill.
- Bear, M. F., Connors, B. W., & Paradiso, M. A. (2016). *Neuroscience: Exploring the Brain* (4th ed.). Wolters Kluwer.
- Goodfellow, I., Bengio, Y., & Courville, A. (2016). *Deep Learning*. MIT Press.
- Hubel, D. H., & Wiesel, T. N. (1962). Receptive fields, binocular interaction and functional architecture in the cat's striate cortex. *Journal of Physiology*, 160(1), 106–154.
- Hodgkin, A. L., & Huxley, A. F. (1952). A quantitative description of membrane current and its application to conduction and excitation in nerve. *Journal of Physiology*, 117(4), 500–544.
- Schultz, W., Dayan, P., & Montague, P. R. (1997). A neural substrate of prediction and reward. *Science*, 275(5306), 1593–1599.
- Hickok, G., & Poeppel, D. (2007). The cortical organization of speech processing. *Nature Reviews Neuroscience*, 8(5), 393–402.
- Tononi, G. (2004). An information integration theory of consciousness. *BMC Neuroscience*, 5, 42.
- Dehaene, S., & Changeux, J.-P. (2011). Experimental and theoretical approaches to conscious processing. *Neuron*, 70(2), 200–227.
- Barrett, L. F. (2017). *How Emotions Are Made: The Secret Life of the Brain*. Houghton Mifflin Harcourt.
