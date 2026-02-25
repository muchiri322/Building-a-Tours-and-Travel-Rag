
---

# Building a Travel and Tourism Retrieval-Augmented Generation (RAG) System

## Project Overview

This project implements a Travel and Tourism Retrieval-Augmented Generation (RAG) system designed to answer user queries using a custom-built tourism knowledge base.

Instead of relying on the general knowledge of a Large Language Model (LLM), the system retrieves relevant tourism data from curated sources and generates responses grounded strictly in retrieved documents.

The goal is to build a reliable, domain-specific AI assistant for travel and tourism in Kenya.

---

## Project Objectives

By completing this project, the system demonstrates the ability to:

* Collect and clean real-world tourism data
* Structure and chunk textual information
* Generate embeddings using an embedding model
* Store embeddings in a vector database
* Implement semantic similarity retrieval
* Integrate an LLM for grounded response generation
* Evaluate hallucination risk and retrieval quality

---

## System Architecture

### High-Level Architecture

```
User Query
    ↓
Query Embedding
    ↓
Vector Database (Similarity Search)
    ↓
Top-K Retrieved Documents
    ↓
Prompt Construction (Context + Question)
    ↓
LLM (Grounded Response Generation)
    ↓
Final Answer
```

### Core Components

1. Data Collection Layer
2. Text Cleaning and Chunking
3. Embedding Generation
4. Vector Database Storage
5. Retrieval Pipeline
6. LLM Response Generation
7. User Interface

---

## Data Sources

Tourism data was collected from reputable platforms including:

### Official Tourism Sources

* Kenya Tourism Board
  [https://magicalkenya.com/](https://magicalkenya.com/)

* National Tourism Service
  [https://tourkenya.go.ke/](https://tourkenya.go.ke/)

* Tourism Research Institute
  [https://tri.go.ke/](https://tri.go.ke/)

### Open Travel Knowledge Platforms

* Wikivoyage
  [https://wikivoyage.org/](https://wikivoyage.org/)

### Example Destinations Covered

* Maasai Mara National Reserve
* Mount Kenya
* Mombasa

The knowledge base contains:

* 50–200 structured documents
* 10,000+ words of cleaned tourism content

---

## Data Processing Pipeline

### Cleaning

* Removed HTML and irrelevant formatting
* Normalized spacing and text
* Eliminated duplicate content

### Chunking

* Documents split into 300–500 token chunks
* Optimized for retrieval precision and token efficiency

### Metadata Storage

Each chunk stores structured metadata including:

* Location
* Category (hotel, attraction, restaurant)
* Price range
* Best season
* Activities

---

## Embeddings and Vector Storage

### Embedding Model

Embeddings were generated using a Sentence Transformer model (HuggingFace).

### Vector Database

Embeddings were stored in:

* Chroma (primary implementation)

Each stored record contains:

* Text chunk
* Embedding vector
* Metadata

---

## Retrieval Pipeline

The retrieval system performs the following steps:

1. Accept user query
2. Convert query to embedding
3. Retrieve top 3–5 most similar chunks
4. Construct prompt with retrieved context
5. Send structured prompt to LLM
6. Generate grounded response

### Hallucination Prevention

The prompt explicitly instructs the model:

> "Answer strictly using the provided context. If the answer is not found in the context, respond with 'Information not available in the knowledge base.'"

---

## User Interface

The project supports:

* Command Line Interface (CLI)

Optional implementations:

* Streamlit web app
* FastAPI backend

The interface allows users to:

* Submit travel-related queries
* View grounded answers
* Optionally view retrieved sources

---

## Example Queries

The system successfully answers queries such as:

* Best wildlife destinations in Kenya
* 3-day itinerary in Mombasa
* Best time to visit Mount Kenya
* Budget-friendly hotels near Maasai Mara National Reserve
* Family-friendly coastal activities

All responses are generated strictly from retrieved documents.

---

## Evaluation

The system was evaluated on:

* Retrieval relevance
* Answer correctness
* Hallucination rate
* Response latency
* Metadata filtering effectiveness

At least 10 predefined travel questions were tested and documented.

---

## Installation Instructions

### Clone Repository

```bash
git clone https://github.com/your-username/travel-rag-system.git
cd travel-rag-system
```

### Create Virtual Environment

```bash
python -m venv venv
source venv/bin/activate   # Mac/Linux
venv\Scripts\activate      # Windows
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Run Application

```bash
python app.py
```

---

## Repository Structure

```
├── data/
│   ├── raw/
│   ├── cleaned/
├── embeddings/
├── vector_db/
├── app.py
├── rag_pipeline.py
├── evaluation_report.pdf
├── requirements.txt
└── README.md
```

---

## Grading Rubric Alignment

| Component                      | Weight |
| ------------------------------ | ------ |
| Data quality and structure     | 20%    |
| RAG implementation correctness | 25%    |
| Retrieval performance          | 20%    |
| Code quality and organization  | 15%    |
| Interface design               | 10%    |
| Evaluation and analysis        | 10%    |

---

## Advanced Extensions (Optional)

* Hybrid search (BM25 + vector search)
* Metadata filtering
* Itinerary generation module
* Budget filtering system
* Multi-language query handling
* Reranking models
* Graph-based tourism relationships

---

## Learning Outcomes

Through this project, students gain practical understanding of:

* Why LLMs hallucinate
* How retrieval grounding improves reliability
* Chunking and embedding trade-offs
* Vector database fundamentals
* Prompt engineering for production systems
* Designing deployable AI applications

---


