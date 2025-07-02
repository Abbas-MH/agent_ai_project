# Local AI Agent with LangChain, Ollama, and ChromaDB

This project demonstrates how to build a local AI agent that can answer questions about pizza restaurant reviews. It leverages **LangChain** for chaining prompts and models, **Ollama** for language models and embeddings, and **ChromaDB** for vector storage and retrieval.

## Overview

The AI agent works by embedding restaurant reviews using the Ollama embedding model, storing these embeddings in a Chroma vector database, and then using an Ollama language model to answer user questions based on the most relevant reviews retrieved from the vector store.

## Project Structure

- `vector.py`  
  - Loads restaurant reviews from a CSV file.  
  - Creates document embeddings using the Ollama embedding model (`mxbai-embed-large`).  
  - Stores the embeddings in a persistent ChromaDB vector store.  
  - Exposes a retriever to find the top relevant reviews for a given query.

- `main.py`  
  - Defines a LangChain chat prompt template that integrates retrieved reviews and a user question.  
  - Uses the Ollama LLM model (`llama3.2`) to generate answers.  
  - Runs an interactive loop where users can input questions and get answers based on the review data.

## Prerequisites

- Install [Ollama](https://ollama.com/) locally and make sure it is running.
- Download and load the following Ollama models locally:  
  - Embedding model: `mxbai-embed-large`  
  - Language model: `llama3.2`

## How to Run

1. Make sure Ollama is installed and the required models (`mxbai-embed-large` and `llama3.2`) are downloaded.
2. Prepare your Python environment and install dependencies (LangChain, pandas, etc.).
3. Run `vector.py` once to create and persist the vector database from your reviews CSV.
4. Run `main.py` to start the interactive question-answer loop.
5. Type your question at the prompt, or q to quit.

## Notes

- The project uses LangChain's prompt chaining with Ollama's local models for efficient and private AI interaction without relying on external cloud APIs.
- The vector store enables semantic search on large text collections, improving answer relevance.
- Feel free to customize the prompt template or expand the dataset to fit your use case.
