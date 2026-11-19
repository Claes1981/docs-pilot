# Project plan: DocsPilot

## What is new

I will learn **RAG (Retrieval-Augmented Generation)**: how to split documents into chunks, create embeddings, store and search them in a vector database, and evaluate how well retrieval answers questions.

Why this one:
- It is new to me — I have not built with RAG, chunking, or vector search before. But I have an interest in AI technology and been experimenting with local AI inference.
- It is the **core** of the project: the answers are only as good as the retrieval, not the chat UI.
- RAG is explicitly in demand in Swedish job ads (together with local LLMs and IaC).
- It runs **fully local and free** on my laptop (32 GB, Intel 140V iGPU): Llama.cpp with a 3B–8B model for answers, a small embedding model, and a local vector DB.

Alongside RAG I will work with **local LLM inference via Llama.cpp** and **infrastructure as code (Bicep)** to deploy the finished system.

---

## What I build

**DocsPilot** — (project name) a local-first RAG assistant that answers questions with **citations** over a curated set of 10–30 Markdown documents.

How it works:
1. **Ingestion (Python):** read the docs → chunk (300–800 tokens, with overlap) → embed (Llama.cpp) → store in a local vector DB (sqlite-vec).
2. **API (FastAPI):** `POST /ask` → retrieve the top-5 chunks → the local model answers **only from that context** → the answer returns its sources.
3. **UI:** a minimal chat page.
4. **Deployment:** Docker Compose for one-command local start; IaC (Bicep) for a cloud deployment I can `xxx` → `yyy` in the demo.

Where the new thing is used: steps 1–2 are the RAG core (chunking, embeddings, vector search, retrieval evaluation) — that is what gets graded.

Building on what I already have: Python, Docker, and GitHub. The teacher approved this direction on 13 November (see Changes below).

**The smallest version that counts as done:**
1. Ask a question in the chat UI and get an answer that cites the document(s) it came from.
2. The answer is based only on the indexed documents — no invented sources.
3. The whole thing starts with one Docker Compose command.

---

## Plan, week by week

| Course week | What I do |
|---|---|
| 1 | Plan approved, repo set up, doc corpus chosen; learn RAG basics (chunking, embeddings, vector search); Docker Compose skeleton |
| 2 | Ingestion: chunking with overlap, embeddings via Llama.cpp, vector DB, top-5 retrieval |
| 3 | `POST /ask` API + local LLM answers with citations |
| 4 | Chat UI; evaluation set (20–30 questions) with retrieval hit-rate and citation checks |
| 5 | Docker images, IaC, optional cloud deployment, README + docs |
| 6 | If time: retrieval experiment (chunk sizes 400/800/1200, vector vs keyword vs hybrid). Polish, logbook catch-up |
| Break | |
| 7 | The report, final submission (14 Jan) |
| 8 | Presentation, demo + opposition (19/21 Jan) |

**The biggest risk, and what I do then:** The LIA-searching takes too much time. Then move work to the holidays
 If a piece is harder than expected, I build the smallest version first.

---

## Changes

| Date | What I changed | Why |
|---|---|---|
| 2026-11-19 | Filled in the plan: DocsPilot (local-first RAG assistant) | Teacher approved the direction 13 Nov; plan due 19 Nov |
