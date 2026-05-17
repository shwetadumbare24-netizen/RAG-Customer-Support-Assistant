# RAG-Based Customer Support Assistant

Production-level Retrieval-Augmented Generation (RAG) system built using Google Colab, LangGraph, ChromaDB, HuggingFace Embeddings, and Human-in-the-Loop (HITL) escalation.

---

# Project Objective

This project implements a scalable AI-powered customer support assistant capable of:

* Processing PDF documents
* Splitting documents into chunks
* Creating embeddings
* Storing embeddings in ChromaDB
* Retrieving relevant information
* Generating contextual answers
* Using LangGraph workflow orchestration
* Supporting Human-in-the-Loop (HITL) escalation

The system demonstrates practical implementation of Retrieval-Augmented Generation (RAG) architecture.

---

# System Architecture

```text id="k4bjlwm"
PDF File
   │
   ▼
┌──────────────────────────────┐
│      DOCUMENT INGESTION      │
│ PyPDFLoader → Text Splitter  │
└──────────────────────────────┘
                │
                ▼
┌──────────────────────────────┐
│        EMBEDDING MODEL       │
│ sentence-transformers        │
│ all-MiniLM-L6-v2             │
└──────────────────────────────┘
                │
                ▼
┌──────────────────────────────┐
│          CHROMADB            │
│       Vector Database        │
└──────────────────────────────┘
                │
                ▼
┌────────────────────────────────────┐
│        LANGGRAPH WORKFLOW          │
│                                    │
│ Query → Process Node → Router      │
│                     │              │
│             ┌───────┴───────┐      │
│             ▼               ▼      │
│         Answer         HITL Node   │
│                                    │
└────────────────────────────────────┘
                │
                ▼
          Final Response
```

---

# Technologies Used

| Technology            | Purpose                 |
| --------------------- | ----------------------- |
| Python                | Programming Language    |
| Google Colab          | Development Environment |
| LangChain             | RAG Framework           |
| LangGraph             | Workflow Orchestration  |
| ChromaDB              | Vector Database         |
| HuggingFace           | Embedding Model         |
| Transformers          | Free LLM                |
| PyPDFLoader           | PDF Processing          |
| Sentence Transformers | Embeddings              |
| GPT2 / FLAN-T5        | Response Generation     |

---

# Features

* PDF Knowledge Base Processing
* Document Chunking
* Semantic Search
* ChromaDB Vector Storage
* LangGraph Workflow
* Conditional Routing
* Human-in-the-Loop Escalation
* Customer Support Question Answering
* Retrieval-Augmented Generation (RAG)

---

# Project Workflow

## Step 1: Upload PDF

The user uploads a PDF document containing customer support information.

Example:

* Refund Policy
* College FAQ
* Bank Support
* Product Manual

---

## Step 2: Load PDF

The system extracts text from the PDF using:

```python id="76a2zr"
PyPDFLoader
```

---

## Step 3: Split Document

The extracted text is divided into smaller chunks using:

```python id="6i0qmf"
RecursiveCharacterTextSplitter
```

Parameters:

* Chunk Size = 500
* Chunk Overlap = 50

---

## Step 4: Create Embeddings

Embeddings are generated using:

```python id="j6v28t"
sentence-transformers/all-MiniLM-L6-v2
```

These embeddings convert text into vectors.

---

## Step 5: Store in ChromaDB

All embeddings are stored inside ChromaDB for semantic retrieval.

---

## Step 6: Query Processing

When a user asks a question:

```text id="70e4wf"
"What is refund policy?"
```

The retriever searches the most relevant chunks.

---

## Step 7: LLM Response Generation

The retrieved context is passed to the LLM.

Prompt Example:

```text id="y4h9rj"
Answer the question using the context below.
```

The model generates a contextual answer.

---

## Step 8: Conditional Routing

The system checks answer quality.

If confidence is low:

* Escalate to Human Support

Otherwise:

* Return generated answer

---

# LangGraph Workflow

## Nodes

| Node          | Function                  |
| ------------- | ------------------------- |
| Process_Query | Retrieves relevant chunks |
| Route_Query   | Checks answer quality     |
| Output        | Displays final response   |
| HITL          | Human escalation          |

---

# Human-in-the-Loop (HITL)

The system escalates queries when:

* No relevant information found
* Low confidence answer
* Complex query detected
* Missing context

Example escalation:

```text id="wzcjmk"
HUMAN ESCALATION REQUIRED
Forwarded to Human Support Team
```

---

# Installation

## Install Libraries

```python id="5uc1ix"
!pip install langchain
!pip install langchain-community
!pip install langgraph
!pip install chromadb
!pip install sentence-transformers
!pip install langchain-text-splitters
!pip install pypdf
!pip install transformers
!pip install torch
```

---

# Running the Project

## Step 1

Open Google Colab

---

## Step 2

Run all cells

---

## Step 3

Upload your PDF

---

## Step 4

Ask questions

Example:

```text id="ftjlwm"
What is the refund policy?
```

---

# Example Queries

* What is refund policy?
* How can I contact support?
* What are working hours?
* What is return process?
* How to reset password?

---

# Example Output

```text id="47vdo0"
Refund requests must be submitted within 30 days of purchase.
```

---

# Scalability Considerations

* Supports large PDF documents
* Efficient semantic retrieval
* Chunk-based indexing
* Vector database optimization
* Extendable workflow architecture

---

# Advantages

* Faster information retrieval
* Reduced hallucination
* Better contextual answers
* Modular workflow
* Human escalation support

---

# Challenges

| Challenge            | Solution        |
| -------------------- | --------------- |
| Large PDFs           | Chunking        |
| Irrelevant retrieval | Embeddings      |
| Wrong answers        | HITL escalation |
| Context loss         | Chunk overlap   |

---

# Future Enhancements

* Multi-PDF Support
* FastAPI Deployment
* Web Interface
* Memory Integration
* Real-time Chat
* OpenAI GPT Integration
* Better Confidence Scoring
* Authentication System

---

# Conclusion

This project successfully demonstrates a production-style Retrieval-Augmented Generation (RAG) system using LangGraph and ChromaDB.

The system processes PDF documents, retrieves relevant information semantically, generates contextual responses, and supports Human-in-the-Loop escalation for complex queries.

The project showcases practical implementation of:

* RAG Architecture
* Vector Databases
* Workflow Orchestration
* Semantic Retrieval
* AI-based Customer Support Systems

This project can be further extended into enterprise-level AI support solutions.
