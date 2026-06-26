#  RAG Intelligence Pipeline

An advanced **Retrieval-Augmented Generation (RAG)** pipeline for analyzing complex financial documents such as **corporate annual reports**, **SEC filings**, and **financial statements**. This project demonstrates the evolution of modern RAG systems, progressing from simple vector similarity search to production-ready retrieval architectures.

---

# 🚀 Overview

Large Language Models often struggle to retrieve the most relevant context from lengthy financial documents using standard semantic search alone. This project addresses that limitation by implementing three advanced retrieval strategies:

- **HyDE (Hypothetical Document Embeddings)**
- **Multi-Query Retrieval**
- **Cross-Encoder Reranking**

Each approach tackles a different weakness of traditional vector search, resulting in higher retrieval accuracy, better contextual understanding, and more reliable financial question answering.

---

# ✨ Features

- 📄 Automatic PDF ingestion
- ✂️ Intelligent document chunking
- 🧠 OpenAI Embeddings
- 🗂️ ChromaDB Vector Store
- 🔍 HyDE Retrieval
- 🔄 Multi-Query Retrieval
- 🎯 Cross-Encoder Reranking
- 📈 UMAP Embedding Visualization
- 💬 Financial Question Answering

---

# 🏗️ Pipeline Architecture

```text
                    Financial PDF
                          │
                          ▼
                Document Loader (PyPDF)
                          │
                          ▼
                  Text Splitter
                          │
                          ▼
                OpenAI Embeddings
                          │
                          ▼
                  Chroma Vector DB
                          │
          ┌───────────────┼────────────────┐
          │               │                │
          ▼               ▼                ▼
       HyDE        Multi-Query       Standard Search
          │               │
          └───────┬───────┘
                  ▼
         Candidate Documents
                  │
                  ▼
      Cross-Encoder Reranker
                  │
                  ▼
      Top Relevant Context
                  │
                  ▼
            GPT Response
```

---

# 🧠 Retrieval Techniques

## 1. HyDE (Hypothetical Document Embeddings)

HyDE improves retrieval by generating a hypothetical answer before embedding the query.

Instead of embedding the user's short question, the LLM first creates a likely answer. That generated paragraph is embedded and used for similarity search.

This bridges the semantic gap between short questions and lengthy financial reports.

### Best For

- Short questions
- Ambiguous queries
- Natural language search

### Example

**User Query**

```text
Why did Microsoft's cloud revenue increase?
```

**Generated Hypothetical Answer**

```text
Microsoft's cloud revenue increased due to Azure growth,
enterprise adoption, and AI infrastructure investments.
```

---

## 2. Multi-Query Retrieval

Instead of relying on a single query, the LLM generates multiple variations.

Example:

Original Query

```text
What risks does Microsoft face?
```

Generated Queries

```text
Business risks

Operational risks

Future challenges

Market competition

Financial uncertainties
```

Each query retrieves different document chunks.

The retrieved documents are merged before reranking.

### Benefits

- Better recall
- More complete context
- Reduced information loss

---

## 3. Advanced Cross-Encoder Reranking

Traditional vector search retrieves candidate documents efficiently but cannot always rank them optimally.

A Cross-Encoder evaluates every **(query, document)** pair directly and assigns a relevance score.

Only the highest-ranked chunks are passed to GPT.

### Benefits

- Higher precision
- Less irrelevant context
- Better final responses

---

# 📊 Technique Comparison

| Technique | Core Mechanism | Best Used For |
|-----------|----------------|---------------|
| Standard RAG | Vector Similarity Search | Basic semantic retrieval |
| HyDE | Hypothetical Document Embeddings | Short or vague questions |
| Multi-Query | Multiple LLM-generated queries | Broad information retrieval |
| Cross-Encoder Reranking | Query-document scoring | High precision retrieval |

---

# 📦 Installation

Clone the repository

```bash
git clone https://github.com/yourusername/financial-rag-intelligence.git

cd financial-rag-intelligence
```

Install dependencies

```bash
pip install openai langchain chromadb pypdf sentence-transformers umap-learn matplotlib python-dotenv langchain-community
```

---

# ⚙️ Configuration

Create a `.env` file

```env
OPENAI_API_KEY=sk-your-api-key
```

Place your financial report inside:

```text
data/
└── microsoft-annual-report.pdf
```

---


# 📈 Embedding Visualization

The project includes UMAP visualizations showing:

- 🔴 Original Query
- 🟠 Augmented Queries (HyDE / Multi-Query)
- 🟢 Retrieved Documents

These plots clearly demonstrate why advanced retrieval techniques outperform traditional vector similarity search.

---

# 💡 Example Questions

```text
How did Microsoft's operating income change?

What are Microsoft's biggest business risks?

Explain the company's AI strategy.

What factors contributed to Azure's growth?

Summarize Microsoft's financial outlook.
```

---

# 🛠 Technologies

- Python
- OpenAI
- LangChain
- ChromaDB
- Sentence Transformers
- Cross-Encoder
- UMAP
- Matplotlib
- PyPDF

---



# 📜 License

This project is intended for **educational and research purposes**.

Feel free to modify, extend, and use it for learning.

---

# ⭐ Acknowledgements

Built using:

- OpenAI
- LangChain
- ChromaDB
- Hugging Face
- Sentence Transformers
