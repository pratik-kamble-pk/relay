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

## Repository Structure

```
chatbot-platform/
├── nextjs-app/          # Next.js 15 + Auth.js v5 + MongoDB
├── python-rag-service/  # FastAPI + Pinecone + OpenAI RAG
├── docker-compose.yml
└── README.md
```

## Technology Stack

### Next.js Service
| Technology | Version |
|---|---|
| Next.js | 15.x |
| React | 19.x |
| TypeScript | 5.x |
| Auth.js (NextAuth) | 5.x (beta) |
| Mongoose | 8.x |
| bcryptjs | 2.x |
| Tailwind CSS | 3.x |

### Python Service
| Technology | Version |
|---|---|
| Python | 3.11+ |
| FastAPI | ≥ 0.115 |
| Pinecone SDK | ≥ 6.0 |
| OpenAI SDK | ≥ 1.50 |
| Pydantic | ≥ 2.9 |

---

## Prerequisites

- Node.js 20+
- Python 3.11+
- Docker & Docker Compose (optional, for containerized setup)
- MongoDB (local or Atlas)
- OpenAI API key
- Pinecone account + API key

---

