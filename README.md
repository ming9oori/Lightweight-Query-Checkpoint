# Lightweight Query Checkpoint (LQC)

**Classifying Faulty User Queries to Mitigate Hallucinations in Large Language Model Question Answering**

[![Paper](https://img.shields.io/badge/Paper-ACL%202025-blue)](https://aclanthology.org/2025.findings-acl.756/)
[![PDF](https://img.shields.io/badge/PDF-Download-red)](https://aclanthology.org/2025.findings-acl.756.pdf)

## Overview

This repository contains the implementation of **Lightweight Query Checkpoint (LQC)**, a novel approach to reduce hallucinations in Large Language Model (LLM) question answering systems. LQC is a small classification model that proactively detects verification-required queries before the LLM generates potentially faulty answers.

## Key Features

- 🎯 **Proactive Hallucination Detection**: Identifies problematic queries before answer generation
- 🚀 **Lightweight Architecture**: Uses hidden states from intermediate layers of smaller-scale LLMs
- 📊 **Binary Classification**: Distinguishes between verification-required and clear queries
- 🔍 **Contrastive Learning**: Trained using binary contrastive learning methodology
- ⚡ **Pipeline Integration**: Easily integrates into existing QA systems

## Problem Statement

Large Language Models often hallucinate when faced with:
- ❌ **Incorrect premises** in user queries
- ❌ **Insufficient context** for accurate answering  
- ❌ **Linguistic ambiguity** that leads to misinterpretation

LQC addresses these issues by creating a checkpoint that flags potentially problematic queries for verification.

## Method

### Architecture
- Utilizes hidden states from intermediate layers of non-instruct-tuned LLMs
- Implements binary contrastive learning for query classification
- Lightweight design for efficient real-time processing

### Query Categories
LQC systematically categorizes queries into:
1. **Verification-Required Queries**: Contain potential issues requiring fact-checking
2. **Clear Queries**: Well-formed queries that can be answered directly

## Installation

```bash
git clone https://github.com/your-username/lightweight-query-checkpoint.git
cd lightweight-query-checkpoint
pip install -r requirements.txt


from lqc import LightweightQueryCheckpoint

# Initialize LQC model
lqc = LightweightQueryCheckpoint.from_pretrained('path/to/model')

# Check if query requires verification
query = "What is the capital of the fictional country Atlantis?"
requires_verification = lqc.classify(query)

if requires_verification:
    print("Query flagged for verification")
    # Implement verification logic
else:
    print("Query is clear - proceed with LLM")
    # Generate answer directly



@inproceedings{son-etal-2025-lightweight,
    title = "Lightweight Query Checkpoint: Classifying Faulty User Queries to Mitigate Hallucinations in Large Language Model Question Answering",
    author = "Son, Minjoo and Jang, Jonghak and Kim, Misuk",
    booktitle = "Findings of the Association for Computational Linguistics: ACL 2025",
    month = jul,
    year = "2025",
    address = "Vienna, Austria",
    publisher = "Association for Computational Linguistics",
    pages = "14664--14677",
    url = "https://aclanthology.org/2025.findings-acl.756/",
    doi = "10.18653/v1/2025.findings-acl.756"
}
