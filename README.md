# RAG Basics

A hands-on learning project for understanding **Retrieval-Augmented Generation (RAG)** pipelines using Python and LangChain.

## What is RAG?

RAG is a technique that combines information retrieval with text generation. Instead of relying solely on an LLM's trained knowledge, RAG retrieves relevant documents from an external knowledge base and uses them as context when generating responses — reducing hallucinations and improving accuracy.

## Pipeline Overview

```
Documents → Load → Split → Embed → Store → Retrieve → Generate
```

| Stage | Description | Tools |
|---|---|---|
| Load | Ingest documents from files/directories | LangChain document loaders |
| Split | Chunk documents into smaller pieces | RecursiveCharacterTextSplitter, TokenTextSplitter |
| Embed | Convert chunks into vector representations | sentence-transformers, OpenAI embeddings |
| Store | Persist vectors in a vector database | ChromaDB, FAISS |
| Retrieve | Find relevant chunks for a query | Similarity search |
| Generate | Produce a grounded response using an LLM | OpenAI, Groq |

## Project Structure

```
rag-basics/
├── data-parsing/
│   └── data-ingestion.ipynb   # Document loading & splitting exploration
├── docs/
│   └── text_file/             # Sample documents (AI concepts, cloud computing)
├── main.py                    # Entry point
├── .env.example               # Environment variable template
├── pyproject.toml             # Project dependencies
└── requirements.txt
```

## Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/16mdiqbal/rag-basics.git
cd rag-basics
```

### 2. Set up environment

```bash
cp .env.example .env
# Fill in your API keys in .env
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
# or with uv
uv sync
```

### 4. Run the notebook

Open `data-parsing/data-ingestion.ipynb` in Jupyter and run the cells.

## Environment Variables

| Variable | Description |
|---|---|
| `OPENAI_API_KEY` | OpenAI API key for embeddings and LLM |
| `GROQ_API_KEY` | Groq API key for fast LLM inference |

## Tech Stack

- **Orchestration:** LangChain
- **LLMs:** OpenAI, Groq
- **Vector DBs:** ChromaDB, FAISS
- **Embeddings:** sentence-transformers, tiktoken
- **Runtime:** Python 3.12, uv, Jupyter
