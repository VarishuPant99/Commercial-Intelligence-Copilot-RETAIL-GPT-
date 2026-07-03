# Commercial-Intelligence-Copilot-RETAIL-GPT-
An Agentic AI assistant for FMCG Commercial Analytics.  Features  ✓ SQL Analytics  ✓ Enterprise RAG  ✓ Tool Calling  ✓ Hybrid Retrieval  ✓ Agno Agent  ✓ LanceDB  ✓ Gemini  Architecture

# 🏗️ Architecture

```mermaid
flowchart TB

    U[👤 Business User]

    U --> A[🤖 Commercial Intelligence Copilot<br/>Agno Agent]

    A --> D{Reasoning & Tool Selection}

    D -->|Sales / Revenue / SKU Queries| SQLT[📊 Sales Analytics Tool]

    D -->|Policies / Ingredients / FAQs| K[📚 Agno Knowledge]

    D -->|Hybrid Questions| SQLT
    D -->|Hybrid Questions| K

    SQLT --> G1[🧠 Gemini 2.5 Flash<br/>Natural Language → SQL]

    G1 --> SQL[(🗄️ SQLite Database)]

    SQL --> SR[Structured Results]

    K --> L[(🔍 LanceDB)]

    L --> E[SentenceTransformer<br/>BAAI/bge-small-en-v1.5]

    E --> PDF[(📄 Commercial PDFs)]

    PDF --> INGEST[Knowledge.insert()]

    SR --> A

    L --> A

    A --> R[💡 Grounded Business Answer]

    R --> U
```
