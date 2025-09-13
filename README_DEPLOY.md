# Full RAG Project (Frontend + Backend) — Quick Deploy Guide

This package contains a static frontend (folder `frontend/`) and a simple FastAPI backend (`main.py`) that implements ingestion into FAISS and a query endpoint using OpenAI embeddings and ChatCompletion.

## Quick local run
1. Unzip the project.
2. cd rag_full_project/backend
3. Create virtualenv and install: `python -m venv venv && source venv/bin/activate` (Windows different)
4. `pip install -r requirements.txt`
5. Set env var: `export OPENAI_API_KEY=sk-...`
6. `python main.py`
7. Visit http://localhost:8000

## Deploying to Render (example)
1. Create a Render Web Service, connect your GitHub repo (or push this code to a repo).
2. Build command: `pip install -r requirements.txt`
3. Start command: `uvicorn main:app --host 0.0.0.0 --port $PORT`
4. Set environment variable `OPENAI_API_KEY` in Render dashboard.
5. Deploy — you'll get a public URL like `https://your-service.onrender.com`

## How to use
- Ingest a document:
  POST /api/ingest
  JSON body: { "doc_id": "doc1", "title": "My Doc", "text": "Full text of the document" }

- Query:
  POST /api/query
  JSON body: { "question": "What is RAG?", "top_k": 4 }

The backend will return 'answer' and 'sources'.

## Final notes
- This is a working scaffold. For full Google OAuth+Google Drive integration, you will need to implement OAuth flow and call Drive API; I can provide that code as the next step.
