# 🧠 PDF Question Answering with RAG Pipeline (Vector + Knowledge Graph + Claude LLM)

This project implements a **hybrid Retrieval-Augmented Generation (RAG)** pipeline for intelligent question-answering on PDF documents. It uses both:

- 🔍 **Vector similarity search** via Hugging Face embeddings
- 🧩 **Knowledge graph search** via Neo4j
- 🤖 **Answer generation** using Anthropic Claude LLM

---

## 🚀 Features

- Upload and process PDFs to extract unstructured and structured knowledge
- Embed text chunks using Hugging Face models and store in a vector store
- Extract entities and relations to build a knowledge graph in Neo4j
- Perform hybrid retrieval: vector similarity + Cypher-based KG query
- Generate accurate, context-rich answers using Claude with both sources

---

## 🧠 Hybrid RAG Strategy

> **Final answers are generated using context retrieved from BOTH vector search and knowledge graph search.**

Claude receives a prompt that includes:
- Top-k similar document chunks (semantic retrieval)
- Entities and relationships from Neo4j (structured retrieval)

---

## 📊 Tech Stack

| Component          | Tech                                      |
|-------------------|-------------------------------------------|
| LLM               | Anthropic Claude                          |
| Embeddings        | Hugging Face (`sentence-transformers`)    |
| Vector DB         | FAISS / Chroma                            |
| Knowledge Graph   | Neo4j                                     |
| PDF Parsing       | `PyMuPDF` / `pdfminer.six`                |
| UI                | Gradio                                    |
| Orchestration     | LangChain / Custom Python Code            |

---

## 📁 Project Structure

```bash
rag-pdf-qa/
├── app.py                  # Main app entrypoint
├── pipeline/
│   ├── pdf_parser.py       # PDF to text
│   ├── chunker.py          # Text splitting
│   ├── embedder.py         # Hugging Face embeddings
│   ├── kg_builder.py       # Extract triples for Neo4j
│   ├── retriever.py        # Vector + KG retrieval
│   └── qa_generator.py     # Combine context + Claude prompt
├── neo4j/
│   └── init.cypher         # Neo4j schema setup
├── requirements.txt
└── README.md
