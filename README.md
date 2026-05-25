# Financial News Summarizer 📈🤖

An end-to-end NLP data pipeline that fetches live news related to Artificial Intelligence and utilizes a Retrieval-Augmented Generation (RAG) framework to generate semantic, context-aware summaries. 

---

## 🚀 Key Features
* **Live Data Mining:** Fetches latest market and tech news using the `NewsData.io` API connection.
* **Semantic Embeddings:** Utilizes the pre-trained `all-MiniLM-L6-v2` transformer model to convert unstructured text into dense vector spaces.
* **Educational Codebase:** Fully documented data science workflows tracking the mathematical foundation of RAG (chunking strategies, overlapping, and similarity search).

## 🛠️ Tech Stack & Architecture
* **Language:** Python
* **Data Source:** NewsData.io API
* **Embedding Model:** HuggingFace `sentence-transformers/all-MiniLM-L6-v2`
* **Orchestration / Notebook:** Jupyter Notebook

---

## 📂 Project Structure & Navigation

The primary entry point, execution logic, and architectural breakdowns are stored within a single notebook for clean reproducibility:

* **`Financial_News_Summarizer_v1.ipynb`**: The complete production notebook containing:
  * API connection setup and JSON parsing.
  * Data preprocessing and cleaning functions.
  * Implementation notes on core RAG concepts (Text chunking mechanics, Vector space distance metrics).
  * Setup guides and package prerequisites.
