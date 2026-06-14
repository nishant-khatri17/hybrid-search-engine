# Hybrid Search Engine

A retrieval system that combines lexical search (BM25) and semantic search (Sentence Transformers) to improve search relevance and better capture user intent.

## Overview

Traditional search engines rely on keyword matching, which performs well for exact matches but struggles with semantic understanding.

Semantic search using transformer embeddings can understand meaning, but often misses exact identifiers, keywords, abbreviations, and domain-specific terminology.

This project implements a **Hybrid Search Engine** that combines both approaches to retrieve documents that are both semantically relevant and lexically accurate.

## Motivation

Each retrieval method has limitations:

### BM25 Search

* Strong at exact keyword matching
* Works well for rare terms and identifiers
* Struggles with synonyms and paraphrases

### Semantic Search

* Understands contextual meaning
* Handles paraphrases and natural language queries
* Can miss exact keywords or domain-specific terms

Hybrid retrieval combines both signals to improve search quality.

## Architecture

Query
↓
BM25 Retrieval
↓
Top-K Documents

Query
↓
Sentence Transformer Embeddings
↓
Vector Similarity Search

↓
Score Fusion
↓
Final Ranked Results

## Features

* BM25 keyword retrieval
* Transformer-based semantic retrieval
* Dense vector embeddings
* Hybrid score fusion
* Ranking and reranking
* Search relevance evaluation
* Retrieval experimentation notebook

## Methodology

### Step 1: Lexical Retrieval

Documents are indexed using BM25.

The BM25 score measures relevance using:

* Term Frequency (TF)
* Inverse Document Frequency (IDF)
* Document length normalization

### Step 2: Semantic Retrieval

Queries and documents are embedded using transformer models.

Similarity is computed using cosine similarity in embedding space.

### Step 3: Hybrid Fusion

Final ranking combines:

Hybrid Score = α × BM25 + (1 − α) × Semantic Similarity

where α controls the contribution of lexical and semantic retrieval.

## Technologies Used

* Python
* Sentence Transformers
* BM25
* NumPy
* Pandas
* Scikit-Learn
* Jupyter Notebook

## Repository Structure

```text
Hybrid-Search/
│
├── experiments.ipynb
├── bm25_values.json
├── requirements.txt
└── README.md
```

## Example Queries

### Query

```text
machine learning for document ranking
```

### BM25 Result

Returns documents containing exact terms.

### Semantic Result

Returns conceptually related documents discussing:

* ranking systems
* retrieval models
* information retrieval

### Hybrid Result

Combines both signals for improved relevance.

## Applications

* Enterprise Search
* Research Paper Discovery
* Knowledge Management Systems
* Document Retrieval
* Retrieval-Augmented Generation (RAG)
* Recommendation Systems

## Future Improvements

* Reciprocal Rank Fusion (RRF)
* Cross-Encoder Reranking
* FAISS Vector Indexing
* Dense Passage Retrieval (DPR)
* Hybrid RAG Pipelines
* Query Expansion using LLMs

## Key Concepts

* Information Retrieval
* BM25
* Semantic Search
* Embeddings
* Vector Similarity
* Ranking Systems
* Hybrid Retrieval
* Retrieval-Augmented Generation

## Author

Nishant Khatri

Built as an exploration of modern information retrieval systems combining lexical and semantic search techniques.
