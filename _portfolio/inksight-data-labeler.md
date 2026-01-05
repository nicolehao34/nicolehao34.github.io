---
title: "InkSight DataLabeler"
excerpt: "A multimodal STEM lecture video dataset and annotation platform for AI-assisted accessibility WIP <br/><img src='/images/Projects/inksight.png'>"
collection: portfolio
date: 2025-05-01
tags:
  - React
  - Node.js
  - PostgreSQL
  - WebSocket
  - Computer Vision
  - Multimodal AI
  - Accessibility
---

Note: This entire page is currently under construction. Stay tuned for upcoming changes.

## Overview

InkSight DataLabeler is a robust multimodal dataset and annotation platform tailored to AI-assisted accessibility in STEM education. The platform enables frame-level precision annotation of lecture videos, capturing dynamic handwritten content, complex diagrams, and spoken explanations to train AI models that can understand and transcribe multimodal educational material.

**Demo**: [InkSight Data Labeler](https://inksight-data-labeler.replit.app/)

## Motivation

STEM lectures present significant challenges for students with auditory or visual processing difficulties. In 2019, 41% of U.S. colleges hired student note-takers to assist students requiring accommodations—a labor-intensive and expensive process prone to quality variability. Existing tools struggle with the complexity of STEM content, including mathematical equations, diagrams, and rapid multimodal delivery.

InkSight addresses this gap by providing precise annotation tools that enable the development of AI models capable of transcribing and understanding dynamic educational content.

## Key Features

### Dynamic Content Capture
* **Live Handwriting**: Captures evolving handwritten notes, equations, and annotations in real-time
* **Complex Diagrams**: Annotates step-by-step creation of scientific and mathematical diagrams
* **Speech Synchronization**: Aligns spoken explanations with corresponding visual elements
* **Frame-Level Precision**: Provides fine-grained annotations for every video frame

### Collaborative Annotation System
* **Real-Time Collaboration**: WebSocket-powered multi-user annotation sessions
* **Live Cursors**: View other annotators' work in progress
* **Three-Tiered Roles**: Annotator, Lead Annotator, and Administrator for quality control
* **Validation Pipeline**: Structured review process before inclusion in training dataset

### Annotation Tools
Five primary annotation categories with dedicated tooling:
1. **Handwritten Text** (amber) - For lecture notes and written content
2. **Mathematical Notation** (emerald) - For equations and formulas
3. **Diagrams** (blue) - For visual representations and figures
4. **Background Content** (gray) - For static slide material
5. **Erasure Regions** (red) - For tracking content removal

### Efficiency Enhancements
* **Smart Frame Suggestion**: Algorithms highlight frames with new content
* **Pre-Annotation**: Existing models propose initial annotations for human validation
* **Batch Operations**: Replicate annotations across multiple frames
* **Keyboard Shortcuts**: Streamlined navigation and workflow
* **Active Learning**: Prioritizes high-impact frames for maximum dataset value

## Technical Architecture

### Frontend
* **React** with **Tailwind CSS** for responsive, modular UI
* Video playback controls with timeline navigation
* Canvas-based drawing tools for precise annotation
* Real-time collaboration features

### Backend
* **Node.js** with **Express** for API services
* **PostgreSQL** with JSONB for flexible coordinate storage
* **WebSocket** broadcasting for real-time synchronization
* Video processing pipeline for frame extraction

### Data Storage
* Per-frame annotation schema for consistency across frame rates
* Structured metadata: frame number, tool type, coordinates, labels, confidence scores
* Supporting tables for user activity, video metadata, and temporal events
* Future integration with **AWS S3** for scalable video storage

### Deployment
* Docker containerization for portability
* Cloud deployment on Replit for demo access
* Production-ready AWS architecture (S3, CloudFront CDN, Redis)

## Dataset Characteristics

InkSight fills critical gaps identified in existing multimodal lecture datasets:

### Advantages Over Existing Datasets
* **Dynamic Content**: Unlike datasets focused on static slides (LPM), captures live handwriting evolution
* **Fine-Grained Annotations**: Frame-by-frame detail vs. coarse bounding boxes
* **Strong Cross-Modal Alignment**: Precise links between speech and visual elements
* **STEM Focus**: Specialized for mathematical equations and scientific diagrams

### Comparison with Related Work
* **LectureVideoDB (2018)**: Limited to OCR text recognition, lacks handwriting process
* **Google I/O (2014)**: Static slides only, no dynamic content
* **LectureBank (2019)**: Text-centric PDFs, no video or temporal data
* **LPM (2022-2023)**: Best match but focuses on typed slides, not handwritten content
* **SlideSpeech (2023)**: ASR enhancement, doesn't analyze visual reasoning

## Export Formats

Annotated data exports in training-ready formats:
* **JSON**: Full annotation metadata and relationships
* **CSV**: Tabular format for statistical analysis
* **COCO**: Compatible with common ML frameworks
* **FCN-Optimized**: Tailored for Fully Convolutional Networks

Each export includes video metadata, coordinate geometries, content types, validation status, and quality metrics (inter-annotator agreement, validation coverage).

## Applications

### Accessibility in STEM Education
* Automated note-taking for students with disabilities
* Real-time transcription of handwritten content
* Diagram-to-text conversion for screen readers
* Multimodal learning support

### AI for Science (AI4S)
* **Symbolic Reasoning**: Multi-step derivation reconstruction
* **Diagram Understanding**: Visual-to-structured representation translation
* **Scientific Retrieval**: Equation/diagram-based search in literature
* **Workflow Modeling**: Problem-solving pattern extraction
* **Knowledge Graphs**: Entity and relation extraction for prerequisite mapping

### Vision-Language Model Training
Designed to support pre-training and fine-tuning of:
* **OpenAI CLIP**: Joint vision-text representations for concept matching
* **OpenAI GPT-4V**: Rich reasoning over diagrams and dense text
* **DeepMind Flamingo**: Few-shot learning for educational adaptability
* **Google Gemini**: Advanced multimodal integration

## Future Work

* Enhanced semantic relationship annotations for VLM training
* Semi-automated workflows with pre-trained models as partial annotators
* Expanded dataset coverage across more STEM disciplines
* Performance benchmarking on handwriting recognition, math parsing, and diagram detection
* Public dataset release via Zenodo and Hugging Face
* Community-driven annotation portal with filtered downloads

## Research Paper

Developed as part of research at Cornell University in collaboration with Jennifer Sun. The work aims to advance multimodal learning systems that foster inclusive learning environments and improve AI model training for educational applications.

**Contact**: inksight882@gmail.com

## Links

* [Live Demo](https://inksight-data-labeler.replit.app/)
* Email: inksight882@gmail.com
