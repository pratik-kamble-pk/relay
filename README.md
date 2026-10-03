# Multi-Tenant AI Chatbot Platform

A production-ready multi-tenant AI chatbot platform that allows users to create independent chatbots, each with its own document-based RAG knowledge base.

## Architecture

```
┌─────────────────────────────────────────────┐
│             NEXT.JS MICROSERVICE            │
│                                             │
│  Authentication / Authorization (Auth.js)   │
│  MongoDB + Mongoose                         │
│  User & Chatbot Management                  │
│  Document Upload UI                         │
│  Chat Interface                             │
└──────────────────────┬──────────────────────┘
                       │ HTTP API (x-api-key)
                       ▼
┌─────────────────────────────────────────────┐
│             PYTHON MICROSERVICE             │
│                                             │
│  FastAPI                                    │
│  Document ingestion (PDF/DOCX/TXT)          │
│  OpenAI embeddings                          │
│  Pinecone vector storage                    │
│  Vector search (per-chatbot filtered)       │
│  RAG answer generation                      │
└─────────────────────────────────────────────┘
                       │
             ┌─────────┴──────────┐
             ▼                    ▼
        ┌─────────┐          ┌──────────┐
        │Pinecone │          │  OpenAI  │
        │Vectors  │          │  API     │
        └─────────┘          └──────────┘
```

