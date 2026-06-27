# Production-Ready n8n AI Agent with Pinecone Vector RAG & MCP Concepts

A high-performance, event-driven asynchronous data workflow built on n8n that empowers an AI Agent to dynamically query a Pinecone vector database. This architecture enables low-latency retrieval-augmented generation (RAG) and introduces Model Context Protocol (MCP) structural insights for enterprise-level semantic QA.


## 🚀 Architecture Overview

The pipeline orchestrates an advanced AI Agent stack designed to eliminate context window bottlenecks while maintaining high response precision:
* **Orchestration & Logic:** `n8n AI Agent` node managing conversational state and multi-tool routing.
* **Vector Database:** `Pinecone` (Serverless/Dense index) storing highly dimensional chunked document embeddings.
* **Embedding Model:** `text-embedding-3-small` (OpenAI) converting real-time queries into multi-dimensional vectors.
* **LLM Core:** `OpenAI Chat Model (gpt-4o / gpt-3.5-turbo)` evaluating contexts and delivering synthesized markdown responses.
* **Memory Management:** Asynchronous `Simple Memory` variable tracking to maintain chat history gracefully across multi-turn sessions.

---

## 📊 Performance & Metrics

Based on internal load testing and Pinecone metrics:
* **Vector Footprint:** Stable indexing with low read/write latency overhead.
* **RAG Ingestion:** Seamless spike handling during upserts without compromising query throughput (Requests per second stable under sustained agent invocation).

---

## 🛠️ Tech Stack

* **Workflow Engine:** n8n (Advanced AI Agent Router)
* **Vector DB:** Pinecone
* **LLM & Embeddings:** OpenAI API
* **Concepts Implemented:** Semantic Search, RAG, Asynchronous Context Injection, Chat Memory Persistence

---

## 📦 How to Deploy This Workflow

1. **Prerequisites:**
   * An active **n8n** instance (Self-hosted via Docker or n8n Cloud).
   * **Pinecone** API Key and an initialized index named `n8nfile`.
   * **OpenAI** API Key.

2. **Importing the Workflow:**
   * Download the `workflow.json` from this repository.
   * Open your n8n canvas -> Click Top-Right Menu -> **Import from File**.

3. **Environment Credentials:**
   * Configure `OpenAI Chat Model` and `Embeddings OpenAI` with your OpenAI credentials.
   * Configure `Pinecone Vector Store` with your Pinecone environment variables and API Key.

4. **Test the Setup:**
   * Click **Execute Workflow**.
   * Use the n8n Chat interface to send a prompt (e.g., *"What is MCP?"*). The Agent will automatically vectorize the prompt, fetch matching contexts from Pinecone, and reply.
