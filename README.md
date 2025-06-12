# Seerror AI Assistant

An AI-powered chatbot that combines **Generative AI** with **Retrieval-Augmented Generation (RAG)** to provide context-aware answers based on your custom knowledge base.

---

## Project Overview

This project is a chatbot powered by a large language model (Mistral via Ollama) integrated with a retrieval system (LangChain + FAISS) to search and answer questions from your own notes.

- **Backend**: FastAPI app serving the AI chatbot.
- **Frontend**: Simple HTML UI for chat interaction.
- **Knowledge Base**: Custom text file (`my_notes.txt`) loaded and indexed for retrieval.
- **AI Model**: Mistral large language model accessed via Ollama.
- **Retrieval System**: FAISS vector store with SentenceTransformer embeddings.
- **Chain**: LangChain RetrievalQA combines retrieval and generation.

---

## How It Works

1. The custom knowledge base (`my_notes.txt`) is loaded and split into manageable chunks.
2. Each chunk is converted into a vector embedding using `all-MiniLM-L6-v2`.
3. FAISS indexes these embeddings for efficient similarity search.
4. When a user asks a question, the system:
   - Retrieves relevant chunks from FAISS.
   - Passes the chunks with the question to the Mistral model via Ollama.
   - Generates an answer based on retrieved context.
5. The backend returns the generated answer along with the source text snippets.

---

## Backend Code Explanation

- Uses **FastAPI** for the web server and API.
- **CORS** middleware allows cross-origin requests from frontend.
- **LangChain** handles document loading, splitting, embeddings, vector store, and QA chain.
- Async endpoint `/ask` receives a question, runs the retrieval+generation chain, and returns results.

---

## Installation & Setup

### Prerequisites

- Python 3.8+
- [Ollama API](https://ollama.com) (ensure access to the Mistral model)
- Node.js & any frontend server if needed (for `index.html` UI)

### Install Python dependencies

```bash
pip install -r backend/requirements.txt


## Project Structure
seerror-ai-assistant/
│
├── backend/
│ ├── data/
│ │ └── my_notes.txt # Custom knowledge base
│ ├── main.py # FastAPI backend app with AI logic
│ └── requirements.txt # Python dependencies
│
├── frontend/
│ └── index.html # Simple chatbot UI
│
└── README.md # This documentation file



## How It Works
1. Load notes from `my_notes.txt`.
2. Split text into chunks (~500 chars) for better context handling.
3. Generate vector embeddings using `all-MiniLM-L6-v2` model.
4. Store embeddings in FAISS vector store for quick retrieval.
5. When a question is asked:
   - Retrieve relevant chunks from FAISS.
   - Use Mistral LLM (via Ollama) with retrieved context to generate an answer.
6. Return answer along with source text snippets.


## Technologies Used
FastAPI: Backend web framework
LangChain: Chains, document loaders, retrieval QA
FAISS: Vector similarity search
SentenceTransformer: Embeddings generation
Ollama Mistral model: Large language model for generative answers
Gradio (optional): Simple web UI for chat frontend

Author: Jay Tiwari
Date: 2025

