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
## System Architecture

                    Commercial Intelligence Copilot

                           Business User
                                  │
                                  ▼
                  ┌─────────────────────────┐
                  │     Agno AI Agent       │
                  └──────────┬──────────────┘
                             │
             ┌───────────────┴────────────────┐
             │                                │
             ▼                                ▼
    Sales Analytics Tool             Agno Knowledge
             │                                │
             ▼                                ▼
     Gemini SQL Generator               LanceDB
             │                                ▲
             ▼                                │
        SQLite Database          SentenceTransformer
                                               ▲
                                               │
                                       Commercial PDFs

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
