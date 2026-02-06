# Retrieval-Augmented Generation (RAG) Chatbot

This notebook provides a high-level, end-to-end overview of how to build a RAG chatbot. A RAG chatbot connects a large language model (LLM) to data sources like PDFs and websites, allowing the chatbot to give context-aware and accurate answers to frequently-asked questions.

**WARNING:** This is my very first attempt, so please don't judge too harshly! If you learned something new from this notebook, or have suggestions for improvement, I would love to hear from you.

## Prepare Data

- Scrape text from the UW-Madison DAPIR website.
- Clean text to remove whitespace and special characters.
- Chunk text into smaller, semantically-meaningful units (500 words).

## Convert and Store Embeddings

- Convert text chunks into vector embeddings with a pre-trained model (HuggingFace sentence-transformers).
- Store embeddings and metadata in an open-source vector database (ChromaDB) to index chunks with embeddings and metadata like URLs.
- Whereas traditional databases use exact matching, vector databases use similarity search to find relevant content.

## Retrieval

- Convert user prompts into embeddings using the same, pre-trained model.
- Execute similarity search to find the most relevant text chunks.

## Generation

- Pass the retrieved chunks as **context** to an open-source LLM.
- LLM prompts = user prompt + retrieved context + guardrails like "Answer only based on the provided context."
- Generate an answer grounded in the source documents.
- Include citations for source documents (URLs).

## Model Evaluation

- Test the chatbot with sample FAQs.
- Are the answers accurate and helpful?
