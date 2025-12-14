---
title: "Exam Review Bot"
excerpt: "A custom hybrid RAG-based chatbot for exam preparation<br/><img src='/images/Projects/exam-review-bot.png'>"
collection: portfolio
date: 2024-07-01
tags:
  - Python
  - TypeScript
  - RAG
  - LangChain
  - FastAPI
---

## Overview

Exam Review Bot (ERB) is a custom intelligent retrieval and hybrid RAG system for final exam preparation. The system combines document processing, vector search, and LLM-powered responses to help students efficiently review course materials.

## Key Features

* **Document Processing**: Extracts specific lecture PDFs from your course schedule
* **Intelligent Matching**: Matches documents to user questions using semantic search
* **Knowledge Augmentation**: Supplements with internet knowledge through external search
* **Smart Summarization**: Generates intelligent summaries and explanations

## Technical Stack

* **Backend**: FastAPI, Python
* **Frontend**: React, TypeScript, Vite
* **AI/ML**: OpenAI API, Langchain, ChromaDB
* **Vector Store**: FAISS/Chroma for efficient similarity search

## Architecture

The system follows a modular RAG pipeline:

1. **Document Ingestion**: PDF loader and text chunker process course materials
2. **Embedding Layer**: Creates vector embeddings for semantic search
3. **Vector Store**: Stores embeddings in ChromaDB for fast retrieval
4. **Retriever**: Searches the database for relevant context
5. **LLM Integration**: OpenAI/Claude models generate contextual answers

## Features in Development

* Custom indexing and vectorstore database
* File upload interface enhancements
* Progress tracking
* User authentication
* Interactive demo integration

## Links

* [GitHub Repository](https://github.com/nicolehao34/Exam-Review-Bot)
* Topics: JavaScript, CSS, Python, TypeScript, Hybrid RAG
