---
title: "InkSight AI"
excerpt: "AI-driven accessible note-taking platform for STEM students with disabilities WIP <br/><img src='/images/Projects/inksight-ai.png'>"
collection: portfolio
date: 2024-12-01
tags:
  - Django
  - Python
  - React
  - Computer Vision
  - FCN
  - Google Cloud
  - Docker
  - Accessibility
---

Note: This entire page is currently under construction. Stay tuned for upcoming changes.

## Overview

InkSight AI is an AI-driven, accessible note-taking platform designed to support students with vision impairment and auditory processing disorders. The system integrates visual input capture, VLM-based content extraction, and lecture summarization to create accurate notes tailored to individual needs. Unlike traditional tools, InkSight AI is optimized for STEM courses, capable of capturing complex content like equations and diagrams.

**UI Design**: [View on Figma](https://www.figma.com/proto/bLwidAx4HhY7wd8zkWLwTn/InkSight?node-id=471-897&p=f&t=hL2UCDhF2KfqDZvQ-1&scaling=min-zoom&content-scaling=fixed&page-id=0%3A1&starting-point-node-id=277%3A897&show-proto-sidebar=1)

## The Problem

In 2019, 41% of U.S. colleges hired student note-takers to assist students requiring note-taking accommodations—a process that is:
* **Labor-intensive and expensive**: Some institutions paid up to $100 per hour for LaTeX typesetting
* **Delayed access**: Students often lacked immediate access to notes after class for review
* **Quality variability**: Inconsistent note quality across different note-takers
* **STEM challenges**: Existing tools struggle with mathematical equations and scientific diagrams

This leaves many students, particularly those with disabilities, at a disadvantage when processing and retaining lecture content.

## The Solution

InkSight AI creates a more inclusive, equitable, and independent classroom learning experience by:

* **AI-Powered Processing**: Automatically converts lecture videos into structured notes
* **STEM Optimization**: Handles complex equations, diagrams, and scientific notation
* **Quality Control**: Enables professors and TAs to review and proofread notes before distribution
* **SDS Integration**: Centralized workflow reduces administrative time costs
* **Free Access**: Released as a free, open-access web application for Cornell University students

### Three User Groups

1. **Students**: Request and access notes for their courses
2. **Professors and Teaching Assistants**: Review and approve generated notes
3. **Student Disability Services Coordinators**: Manage accommodation requests and workflows

## Technical Architecture

### Backend
* **Framework**: Django for handling complex data relationships across multiple user groups
* **Containerization**: Docker for consistent deployment
* **Hosting**: Google Cloud Platform (GCP) for scalability
* **Key Modules**:
  - SDS management system
  - Course management
  - User management and authentication
  - Note-taking request processing

### Frontend
* **Hosting**: Cloudflare Pages for fast, secure, and reliable access
* **Framework**: Modern web interface for three distinct user personas
* **API Integration**: Communicates with backend through GCP-hosted endpoints
* **Features**:
  - User account management
  - Note-taking request submission
  - Course viewing and management
  - Real-time status updates

### Machine Learning Pipeline

We initially used a **FCN-Lecture Net**, a Fully Convolutional Network with three specialized branches:

1. **Background Estimation**: Separates static content from dynamic elements
2. **Handwritten Text Mask Prediction**: Identifies handwritten regions
3. **Handwritten Content Binarization**: Extracts clear text for OCR

We later found many limitations with this approach, which is why InkSight also became a research initiative. The paper associated with the project is still in progress. Later explorations will be updated as soon as the paper is released!

## Key Capabilities of InkSight
* **Temporal Segmentation**: Detects key events like erasures or board movement
* **Multi-modal Processing**: Handles whiteboard, tablet, and presentation content
* **STEM Specialization**: Optimized for mathematical notation and scientific diagrams

## System Workflow

1. **Recording**: Lecture videos are captured and uploaded to the system
2. **Storage**: Videos stored in secure database infrastructure
3. **AI Processing**: AI system extracts handwritten content, equations, and diagrams
4. **Note Generation**: Extracted content structured into coherent notes
5. **Review**: Professors/TAs proofread and approve notes
6. **Distribution**: Approved notes made available to students through SDS

## Impact and Accessibility

### Benefits for Students
* Immediate access to quality notes after lectures
* Consistent formatting and accuracy
* Support for diverse learning styles
* Independence in learning process

### Benefits for Institutions
* Reduced administrative overhead for SDS
* Scalable accommodation system
* Cost-effective compared to manual note-taking
* Improved student success rates

### STEM-Specific Advantages
* Accurate transcription of mathematical equations
* Preservation of diagram structures and annotations
* Temporal tracking of multi-step derivations
* Support for various notation systems

## Technology Stack

**Backend**
* Django
* Python
* Docker
* Google Cloud Platform
* PostgreSQL

**Frontend**
* React/Modern JS Framework
* Cloudflare Pages
* RESTful API integration

**Machine Learning**
* FCN-Lecture Net
* Computer Vision (OpenCV)
* OCR engines
* Custom STEM notation parsers

**Infrastructure**
* Google Cloud API
* Docker containerization
* Cloudflare CDN
* Secure video storage

## Team

* **Nicole Hao**: AI model research, development, and maintenance; API management
* **Arjun Maitra**: Backend development and maintenance; API management
* **Clément Roze**: Frontend design and development; UI/UX design


## Advisory Board

* **Prof. Stephen Sauer** - Cornell SC Johnson College of Business
* **Jamey Edwards** - President and CSO at Cairns Health
* **Illiava Paleva** - Investor at Hyperspace Ventures
* **Frank Fu** - CIO at Proprietary Trading Firm

## Links

* [UI Design Prototype](https://www.figma.com/proto/bLwidAx4HhY7wd8zkWLwTn/InkSight?node-id=471-897&p=f&t=hL2UCDhF2KfqDZvQ-1&scaling=min-zoom&content-scaling=fixed&page-id=0%3A1&starting-point-node-id=277%3A897&show-proto-sidebar=1)
* Website
* Demo