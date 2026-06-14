# 🔍 Hybrid Search System with Semantic + Keyword Retrieval

## Overview
This project implements a **hybrid document retrieval system** that combines **semantic vector search** with **BM25-based keyword matching** to achieve high recall and high precision simultaneously.  
Unlike a standard RAG pipeline that emphasizes generation, this project focuses on **optimizing the retrieval layer**, which is often the true bottleneck in real-world ML systems.

The system is designed with **production-scale considerations** such as ANN indexing, retriever–reranker architecture, and retrieval quality evaluation.

---

## Motivation
Most RAG implementations treat retrieval as a black box and rely solely on dense embeddings.  
However, in large-scale systems (e.g., e-commerce search, knowledge discovery, enterprise QA), **exact keyword matching and semantic understanding must coexist**.

This project explores:
- Why dense-only retrieval fails in keyword-sensitive queries
- How hybrid search improves robustness
- How retrieval quality can be systematically evaluated and tuned

---

## System Architecture


---

## Key Components

### 1. Dense Semantic Retrieval
- Model: `all-MiniLM-L6-v2`
- Embedding Dimension: 384
- Captures semantic similarity beyond exact word overlap
- Robust to paraphrasing and natural language queries

---

### 2. Sparse Keyword Retrieval (BM25)
- Captures exact keyword importance
- Penalizes common terms via IDF
- Normalizes for document length
- Prevents dense retrieval failure modes (e.g., missing rare entities)

---

### 3. Hybrid Scoring
Final score is computed as:


- α and β are tuned using retrieval evaluation metrics
- Enables domain-specific tradeoffs between semantic recall and keyword precision

---

### 4. Approximate Nearest Neighbor Search
- Uses HNSW-style graph-based ANN indexing
- Achieves sub-linear search complexity (~O(log N))
- Scales to millions of documents with low latency

---

### 5. Retriever–Reranker Design
- Retriever optimized for **high recall**
- Reranker optimized for **high precision**
- Mirrors production-grade search architectures used in large ML systems

---

## Evaluation Strategy

Retrieval quality is evaluated using standard IR metrics:

- **Recall@K** – measures whether relevant documents appear in top-K
- **MRR (Mean Reciprocal Rank)** – measures how early the correct result is ranked

These metrics guide:
- Hybrid weight tuning (α, β)
- ANN parameters
- Candidate set size for reranking

---

## Why Not a Standard RAG Pipeline?
Traditional RAG demos emphasize text generation, but:
- Generation quality is bounded by retrieval quality
- Poor retrieval cannot be fixed downstream
- Production systems prioritize **retrieval robustness and latency guarantees**

This project intentionally focuses on **retrieval-first ML system design**, aligning more closely with real-world Applied ML roles.

---

## Technologies Used
- LangChain
- Pinecone (Vector Database)
- HuggingFace Sentence Transformers
- BM25 Sparse Encoding
- ANN / HNSW Indexing
- Python

---

## Future Improvements
- Learned rerankers using cross-encoders
- Query-dependent dynamic α/β weighting
- Online evaluation with user feedback signals
- Domain-adaptive embedding fine-tuning

---

## Key Takeaway
This project demonstrates that **retrieval is not just a preprocessing step**, but a core ML problem involving ranking theory, approximate search, and system-level tradeoffs—critical for building scalable, high-quality ML applications.
