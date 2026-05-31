# Financial News Summarizer

A local, privacy-first news summarization tool that fetches the latest **Artificial Intelligence** news from [NewsData.io](https://newsdata.io), processes them through a full RAG (Retrieval-Augmented Generation) pipeline, and generates concise summaries using a local LLM — all running on your own machine at no cost.

---

## Project Overview

This project demonstrates how to build an end-to-end NLP pipeline using free and open-source tools:

- **NewsData.io** — Free news API to fetch real-time AI-related articles
- **LangChain** — Text splitting and chunking
- **Sentence Transformers** — Local embedding model (`all-MiniLM-L6-v2`)
- **ChromaDB** — Local vector database for storing and retrieving chunks
- **Ollama + Llama** — Local LLM for generating summaries

Since this project runs entirely on your local machine, no data is sent to external AI services and no paid API credits are required beyond the free NewsData.io tier.

---

## Full Pipeline

```
NewsData.io API          ← Free API, keyword: "Artificial Intelligence"
      ↓
  Append_article         ← Extract title + description from each article
      ↓
  documents              ← Format each article as plain text
      ↓
  all_chunks             ← Split using RecursiveCharacterTextSplitter
      ↓                     chunk_size=300, chunk_overlap=50
  embeddings             ← Convert chunks to vectors via all-MiniLM-L6-v2
      ↓
  ChromaDB               ← Persist indexed chunks to ./news_chroma_db
      ↓
  Query                  ← Embed user query using same local model
      ↓
  Top-K Chunks           ← Retrieve most relevant chunks by distance score
      ↓
  Summarization          ← Pass chunks to Llama via Ollama for final answer
```

---

## How to Navigate This Project

| File / Folder | Description |
|---|---|
| `Financial_News_Summarizer_v1.ipynb` | 📓 Main notebook — contains the full end-to-end script |
| `Reference: Setup/Llama 3B Light Model.ipynb` | 🤖 Setup guide for installing Ollama and running Llama locally |
| `Reference: Setup/Setup NewsData.io API Connection.ipynb` | 🔑 Quick setup guide for the NewsData.io API key and connection |
| `Notes/Step 1: Chunking.ipynb` | ✂️ Explanation of chunking, `chunk_size`, and `chunk_overlap` |
| `Notes/Step2: Local Embedding Model.ipynb` | 📐 Explanation of local embedding models and how they work |
| `Notes/Step 3: Indexing Vhunks using ChromaDB.ipynb` | 🗄️ Guide to indexing and querying chunks using ChromaDB |

> **Start here:** Open `Financial_News_Summarizer_v1.ipynb` for the complete working script. Refer to the `Notes/` and `Reference: Setup/` folder for explanations and setup guides for each component.

---

## Prerequisites

- Python 3.9+
- [Ollama](https://ollama.com/download) installed and running locally
- A free NewsData.io API key from [newsdata.io](https://newsdata.io)

Install all dependencies:

```bash
pip install requests python-dotenv langchain sentence-transformers chromadb ollama
```

Pull the local models:

```bash
ollama pull llama3.2
ollama pull nomic-embed-text
```

---

## Notes & Limitations

- The **free tier** of NewsData.io returns a limited number of articles per request — monitor usage at [newsdata.io/dashboard](https://newsdata.io/dashboard)
- The local LLM quality depends on your machine's RAM — `llama3.2` (3B) is recommended for most laptops
- ChromaDB index is persisted to `./news_chroma_db` and reused across sessions — no need to re-index unless new articles are fetched

---

## Reading Materials

- Complete Guide to Embeddings and RAG [link](https://medium.com/@sharanharsoor/the-complete-guide-to-embeddings-and-rag-from-theory-to-production-758a16d747ac)
- DataNews.io API Documentation [link](https://newsdata.io/documentation?gad_source=1&gad_campaignid=21223993572&gclid=CjwKCAjwuO_QBhAWEiwAIkVhU8jCJJD2R0URZ2pUq3KtSBzNxaj735Vus-Kem7MwjHIzpcl_2axoIxoCC1YQAvD_BwE)
- Writing on GitHub [link](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/about-writing-and-formatting-on-github)
