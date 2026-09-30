# RAG Customer Support Agent

An AI-powered customer support chatbot that answers questions based on a company's own documents using Retrieval-Augmented Generation (RAG).

## What it does

- Answers customer questions 24/7 based on company documents
- Only answers from the knowledge base — no hallucinations
- Detects when it can't help and escalates automatically
- Logs unanswered questions to Google Sheets for follow-up
- Supports multiple document categories (FAQ, returns, payments, technical)

## Stack

- **n8n** — workflow orchestration
- **OpenAI GPT-4o-mini** — conversational AI
- **Supabase (pgvector)** — persistent vector store
- **OpenAI Embeddings** — text-embedding-ada-002
- **Google Docs** — knowledge base source
- **Google Sheets** — escalation logging

## Architecture

Website visitor
→ Chat Widget
→ n8n Chat Trigger
→ AI Agent + RAG Tool
→ Supabase Vector Store (similarity search)
→ Answer from knowledge base
→ IF no answer found
→ Escalation message + log to Google Sheets

## Knowledge Base

- FAQ
- Return Policy
- Payment Methods
- Technical Support

## Key Features

- Similarity threshold: 0.7 (only answers when confident)
- Recursive character text splitting (chunk size: 500, overlap: 50)
- Metadata per document (source, category, updated_at)
- Persistent storage — survives server restarts
