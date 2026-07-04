# 📡 Telecom Multi-Source RAG Chatbot

> **An enterprise-ready Retrieval-Augmented Generation (RAG) system for automated telecom customer care and technical diagnostics.**

This application dynamically routes customer questions across decoupled data sources—merging **unstructured documents**, **tabular policies**, and **relational resolution histories** to deliver accurate, low-hallucination customer support through high-speed inference.

---

## ✨ Features

- 📄 Multi-source knowledge retrieval
- 🔍 Semantic search across FAQs, manuals, and historical tickets
- 🧠 Retrieval-Augmented Generation (RAG) with deterministic reasoning
- ⚡ High-speed inference powered by Groq
- 💬 Interactive Streamlit chatbot interface
- 🗄️ Persistent local vector database using ChromaDB

---

## 🏗️ Core Architecture

The chatbot leverages a **multi-source ingestion pipeline** that standardizes heterogeneous data into isolated vector collections before context fusion.

| Layer | Description |
|--------|-------------|
| **Tabular Layer (FAQs)** | Ingests structured policy items directly from CSV files, mapping answers 1:1 to documents. |
| **Relational Layer (Tickets)** | Queries historical SQL records to retrieve resolved anomalies and troubleshooting workflows. |
| **Unstructured Layer (Manuals)** | Parses PDF documentation using recursive character splitting with a sliding token window strategy. |

All collections share the same embedding encoder:

```text
sentence-transformers/all-MiniLM-L6-v2
```

The retrieved contexts are fused into a single prompt for the reasoning layer powered by:

```text
qwen3-32b (via Groq)
```

---

## 📷 Streamlit Dashboard

> Replace the image below with a screenshot of your chatbot.

<p align="center">
  <img src="assets/dashboard.png" alt="Telecom RAG Chatbot Dashboard" width="900"/>
</p>

---

## 📁 Project Structure

```text
telecom-rag-chatbot/
│
├── app.py                  # Streamlit chatbot interface
├── main.py                 # Terminal testing script
├── rag_chain.py            # LangChain Expression Language (LCEL) pipeline
├── retriever.py            # Multi-source retrieval router
├── ingest_faq.py           # CSV ingestion pipeline
├── ingest_pdf.py           # PDF parsing & chunking pipeline
├── ingest_tickets.py       # SQLite ticket ingestion pipeline
├── requirements.txt
├── .gitignore
├── README.md
│
└── data/
    ├── faq.csv             # Customer service policies
    ├── telecom_guide.pdf   # Device manuals
    └── tickets.db          # Historical support tickets
```

---

## 🛠️ Technology Stack

| Category | Technologies |
|----------|--------------|
| **Framework** | LangChain Core, LangChain Community |
| **Vector Database** | ChromaDB (Persistent Local Storage) |
| **Embeddings** | sentence-transformers/all-MiniLM-L6-v2 |
| **LLM** | Groq (`qwen3-32b`) |
| **Frontend** | Streamlit |

---

## 🚀 Getting Started

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/MakramMuhammed/telecom-rag-chatbot.git

cd telecom-rag-chatbot
```

---

### 2️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

---

### 3️⃣ Configure Environment Variables

Create a `.env` file in the project root.

```env
GROQ_API_KEY=your_groq_api_key_here
```

---

### 4️⃣ Build the Knowledge Base

Before launching the chatbot, generate the local vector stores by running the ingestion scripts once.

```bash
python ingest_faq.py

python ingest_tickets.py

python ingest_pdf.py
```

This creates the local `chroma_store/` directory containing vector embeddings built from the files inside `data/`.

---

### 5️⃣ Launch the Application

```bash
streamlit run app.py
```

The chatbot will be available locally through your browser.

---

## 🔧 Key Implementation Highlights

- Multi-source retrieval across structured and unstructured knowledge.
- Independent ingestion pipelines for each data source.
- Semantic search using transformer embeddings.
- Context fusion before LLM inference.
- Deterministic response generation with Groq.
- Modular and production-oriented architecture.

---

## 🎯 Skills Demonstrated

- Retrieval-Augmented Generation (RAG)
- LangChain Expression Language (LCEL)
- Multi-source document ingestion
- Vector databases with ChromaDB
- Semantic search and embeddings
- Prompt engineering
- Streamlit application development
- End-to-end AI system integration

---

## 🤝 Contributing

Contributions are welcome!

Feel free to open an issue or submit a pull request.

---

## 📄 License

This project is licensed under the **MIT License**.

---

<div align="center">

Made with ❤️ by **Makram Muhammed**

</div>
