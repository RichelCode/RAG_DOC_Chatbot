# RAG Document Chatbot

*A Retrieval-Augmented Generation (RAG) system for querying custom documents using LLMs*

---

## Overview

This project implements a **Retrieval-Augmented Generation (RAG)** pipeline that enables users to ask questions over their own documents and receive context-aware answers.

The system combines:

* document ingestion and preprocessing
* vector embeddings
* similarity-based retrieval
* large language model (LLM) generation

The goal is to bridge the gap between **raw unstructured data** and **useful, interpretable answers**, making it possible to interact with documents in a conversational way.

---

## Motivation

Most language models generate responses based only on pre-trained knowledge, which limits their ability to:

* access up-to-date or domain-specific information
* reason over private datasets
* provide grounded, verifiable answers

This project addresses that limitation by implementing a RAG pipeline where the model:

1. retrieves relevant context from a document store
2. uses that context to generate accurate responses

This approach improves **accuracy, relevance, and transparency** of model outputs.

---

## Key Features

* Document ingestion from local files (Markdown, extensible to PDFs)
* Text chunking using recursive splitting strategies
* Embedding generation using OpenAI embeddings
* Vector storage using ChromaDB
* Semantic similarity search for retrieval
* Context-aware response generation using an LLM
* Modular pipeline for easy extension and experimentation

---

## System Architecture

The system follows a standard RAG pipeline:

### 1. Data Ingestion

Documents are loaded from a local directory using a document loader.

### 2. Text Splitting

Documents are split into overlapping chunks to preserve context and improve retrieval quality.

### 3. Embedding Generation

Each chunk is converted into a vector representation using OpenAI embeddings.

### 4. Vector Storage

Embeddings are stored in a Chroma vector database for efficient similarity search.

### 5. Retrieval

Given a user query, the system retrieves the most relevant chunks using semantic similarity.

### 6. Generation

The retrieved context is passed to an LLM, which generates a grounded response.

---

## Installation

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd rag-doc-chatbot
```

### 2. Create virtual environment

```bash
python -m venv venv
venv\Scripts\activate    # Windows
# or
source venv/bin/activate # Mac/Linux
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## Environment Setup

Create a `.env` file in the root directory:

```env
OPENAI_API_KEY=your_api_key_here
```

---

## Usage

###  Add Documents

Place your documents inside:

```text
data/books/
```

Supported format:

* `.md` (Markdown)

---

### Create Vector Database

```bash
python create_database.py
```

This will:

* load documents
* split them into chunks
* generate embeddings
* store them in Chroma

---

### Query Your Data

```bash
python query_data.py "Your question here"
```

Example:

```bash
python query_data.py "What is AWS Lambda?"
```

The system will:

* retrieve relevant document chunks
* generate an answer using those chunks
* display sources and relevance scores

---

## Example Workflow

1. Add domain-specific documents (e.g., research notes, technical docs)
2. Build the vector database
3. Ask natural language questions
4. Receive grounded, context-aware responses

---

## Technical Decisions

### Chunking Strategy

Used overlapping chunks to:

* preserve semantic continuity
* improve retrieval relevance

### Vector Store (Chroma)

Chosen for:

* simplicity and local persistence
* fast similarity search
* ease of integration with LangChain

### Embeddings

OpenAI embeddings provide a strong semantic representation for:

* improved retrieval accuracy
* better contextual matching

---

## Skills Demonstrated

* End-to-end ML system design
* Working with LLMs and embeddings
* Vector databases and semantic search
* Data preprocessing and pipeline structuring
* API integration and environment management
* Modular and scalable code organization

---

## Conclusion

This project demonstrates how modern AI systems can be designed to move beyond static predictions and toward **interactive, context-aware intelligence**.

By combining retrieval with generation, the system produces responses that are not only fluent but also **grounded in real data**, making it more useful for real-world applications.

---
