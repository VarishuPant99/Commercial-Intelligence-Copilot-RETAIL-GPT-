# Commercial-Intelligence-Copilot-RETAIL-GPT-
An Agentic AI assistant for FMCG Commercial Analytics.  Features  ✓ SQL Analytics  ✓ Enterprise RAG  ✓ Tool Calling  ✓ Hybrid Retrieval  ✓ Agno Agent  ✓ LanceDB  ✓ Gemini  Architecture

## 🏗️ System Architecture

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
