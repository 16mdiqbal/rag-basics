# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
# Install dependencies
uv sync

# Run main entry point
uv run main.py

# Launch Jupyter for notebooks
uv run jupyter notebook

# Add a new dependency
uv add <package>
```

## Architecture

This is a learning project exploring RAG pipeline construction. The work lives primarily in Jupyter notebooks under `data-parsing/`, with `docs/` holding sample documents used as the knowledge base.

**RAG pipeline stages (in order):**
1. **Load** — `TextLoader` / `DirectoryLoader` ingest `.txt` files from `docs/text_file/`
2. **Split** — `RecursiveCharacterTextSplitter`, `CharacterTextSplitter`, or `TokenTextSplitter` chunk documents
3. **Embed** — `sentence-transformers` (local) or `langchain-openai` embeddings convert chunks to vectors
4. **Store** — `ChromaDB` (persistent) or `FAISS` (in-memory) hold the vector index
5. **Retrieve** — similarity search against the vector store for a given query
6. **Generate** — `langchain-groq` or `langchain-openai` LLM produces the final answer with retrieved context as input

**LLM providers available:** OpenAI (via `OPENAI_API_KEY`) and Groq (via `GROQ_API_KEY`). Both are configured via `.env` — copy `.env.example` to get started.

**Vector store choice:** ChromaDB is preferred for persistence across notebook runs; FAISS is faster for in-memory experimentation.
