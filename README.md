# CodedexBot

CodedexBot is an AI-powered backend service that runs entirely offline. It uses open-source generative AI and Retrieval-Augmented Generation (RAG) to answer natural language questions from your personal documents—without any internet access.

---

## 🔑 Key Features

- ✅ **Offline AI**: Runs locally with no cloud or internet dependencies using [Ollama](https://ollama.com) and open-source models.
- 🌐 **Multilingual**: Understands and responds to questions in multiple languages, including **Hindi**.
- 📄 **Document-Aware**: Combines search and generation using your personal `.txt` documents.
- 🧠 **Custom Knowledge Base**: Load plain text files and query them like your own AI assistant.

---

## 🧰 Tech Stack

| Component       | Technology                    |
|----------------|-------------------------------|
| **Backend**     | FastAPI (Python)              |
| **Model Runtime** | Ollama with `mistral` model  |
| **Embeddings**   | `all-MiniLM-L6-v2`           |
| **Vector Store** | FAISS                        |
| **RAG Engine**   | LangChain’s `RetrievalQA`    |
| **Text Loader**  | Plain text via `TextLoader`  |

---

## 🚀 Getting Started

### 1. **Install Dependencies**

```bash
pip install -r requirements.txt



⚠️ Make sure Ollama is installed and running with the mistral model:
ollama run mistral

## 2. Run the Server
uvicorn backend.main:app --host 0.0.0.0 --port 8000

