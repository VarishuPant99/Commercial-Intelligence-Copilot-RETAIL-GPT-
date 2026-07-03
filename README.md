# Commercial-Intelligence-Copilot-RETAIL-GPT-
An Agentic AI assistant for FMCG Commercial Analytics. 
Features:
SQL Analytics
Enterprise RAG
Tool Calling
Hybrid Retrieval
Agno Agent
LanceDB
Gemini Architecture

## 🏗️ System Architecture
                    Business User
                          │
                          ▼
        ┌─────────────────────────────────┐
        │  Commercial Intelligence Agent  │
        │             (Agno)              │
        └───────────────┬─────────────────┘
                        │
        ┌───────────────┴────────────────┐
        │                                │
        ▼                                ▼
 ┌───────────────┐              ┌────────────────┐
 │ Sales Tool    │              │ Knowledge API  │
 └──────┬────────┘              └──────┬─────────┘
        │                              │
        ▼                              ▼
 ┌───────────────┐              ┌────────────────┐
 │ Gemini SQL    │              │ LanceDB        │
 │ Generation    │              │ Vector Store   │
 └──────┬────────┘              └──────┬─────────┘
        │                              │
        ▼                              ▼
 ┌───────────────┐              ┌────────────────┐
 │ SQLite        │              │ Commercial PDFs│
 │ Sales DB      │              │ + Embeddings   │
 └───────────────┘              └────────────────┘
```mermaid
flowchart TB

    USER[Business User]

    USER --> AGENT[Commercial Intelligence Copilot<br>Agno Agent]

    AGENT --> DECISION{Determine Query Type}

    DECISION -->|Sales Analytics| SQLTOOL[Sales Analytics Tool]

    DECISION -->|Knowledge Search| KNOWLEDGE[Agno Knowledge]

    DECISION -->|Hybrid Query| SQLTOOL
    DECISION -->|Hybrid Query| KNOWLEDGE

    SQLTOOL --> GEMINI[Gemini 2.5 Flash<br>Generate SQL]

    GEMINI --> SQLITE[(SQLite Database)]

    SQLITE --> RESULTS[Structured Results]

    KNOWLEDGE --> LANCEDB[(LanceDB)]

    LANCEDB --> EMBEDDER[SentenceTransformer<br>BAAI bge-small-en-v1.5]

    EMBEDDER --> PDFS[Commercial PDF Documents]

    PDFS --> INGEST[Knowledge Ingestion]

    RESULTS --> AGENT

    LANCEDB --> AGENT

    AGENT --> RESPONSE[Grounded Business Response]

    RESPONSE --> USER
```
## 📚 Knowledge Ingestion Pipeline

```mermaid
flowchart LR

A[Commercial PDFs]

--> B[Agno Knowledge]

--> C[PDF Reader]

--> D[Automatic Chunking]

--> E[SentenceTransformer Embeddings]

--> F[(LanceDB)]
```

## 🚀 Runtime Query Flow

```mermaid
sequenceDiagram

actor User

participant Agent as Agno Agent

participant Tool as Sales Tool

participant Gemini

participant SQL as SQLite

participant KB as LanceDB

User->>Agent: Which SKU generated highest sales and what allergens does it contain?

Agent->>Tool: sales_analytics(question)

Tool->>Gemini: Generate SQL

Gemini-->>Tool: SQL Query

Tool->>SQL: Execute SQL

SQL-->>Tool: Top Selling SKU

Tool-->>Agent: Pringles Original

Agent->>KB: Search knowledge

KB-->>Agent: Product Information

Agent-->>User: Final Combined Response
```
