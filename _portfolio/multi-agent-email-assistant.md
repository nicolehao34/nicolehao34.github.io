---
title: "Multi-Agent Email Assistant"
excerpt: "AI agent that writes emails based on natural language instructions<br/><img src='/images/Projects/multi-agent-email-assistant.png'>"
collection: portfolio
date: 2024-06-01
tags:
  - AI Agents
  - LangChain
  - LangGraph
  - Gemini API
  - Python
---

## Overview

An intelligent multi-agent system that automates email writing and management based on natural language instructions. The system uses LangGraph to orchestrate multiple AI agents that monitor, categorize, and respond to emails automatically.

## Motivation

This project was created to learn:

* **LangGraph & LangChain**: For developing AI agent workflows
* **LangServe**: For simplified API development & deployment using FastAPI
* **Gmail API**: For building workflow and productivity tools

## How It Works

### Email Workflow Pipeline

1. **Email Monitoring**
   - Constantly checks for new emails using Gmail API
   - Triggers processing pipeline for each new message

2. **Email Categorization**
   - AI agents sort emails into predefined categories
   - Identifies email type (complaint, feedback, question, etc.)

3. **Response Generation**
   - **Complaints/Feedback**: Drafts tailored responses quickly
   - **Service Questions**: Uses RAG (Retrieval Augmented Generation) to pull accurate information from agency documents

4. **Quality Assurance**
   - AI quality checks for tone and content
   - Formatting validation
   - Ensures professional communication standards

5. **Sending**
   - Approved emails sent automatically
   - Ensures timely communication with clients

## Technical Architecture

### Multi-Agent System

* **Monitor Agent**: Watches inbox for new emails
* **Classifier Agent**: Categorizes email types
* **Response Agent**: Generates appropriate responses
* **QA Agent**: Validates quality and formatting
* **Sender Agent**: Handles email dispatch

### Technology Stack

* **Framework**: LangGraph for agent orchestration
* **LLM**: Google Gemini API for text generation
* **Embeddings**: Gemini embeddings for RAG
* **API**: Gmail API for email operations
* **Deployment**: FastAPI via LangServe
* **Development**: Python

## Features

* Automatic email monitoring and processing
* Intelligent categorization of email types
* Context-aware response generation
* RAG-based information retrieval from documents
* Quality assurance checks
* Seamless integration with Gmail

## Prerequisites

* Python 3.7+
* Groq API key
* Google Gemini API key (for embeddings)
* Gmail API credentials

## Project Status

Work in progress - continuously improving agent capabilities and adding new features.

## Links

* [GitHub Repository](https://github.com/nicolehao34/multi-agent-email-assistant)
* Topics: Multi-Agent Systems, Gemini API, LangChain, LangServe, LangGraph
