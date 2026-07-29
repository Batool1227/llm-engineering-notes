# Retrieval-Augmented Generation (RAG)

RAG combines information retrieval with a Large Language Model to answer questions using external knowledge instead of relying only on the model's internal knowledge.

## Pipeline

```text
User Question
      │
      ▼
Embedding Model
      │
      ▼
Vector Database
      │
      ▼
Top-k Retrieved Chunks
      │
      ▼
Prompt Construction
      │
      ▼
Large Language Model
      │
      ▼
Final Response
```

## Topics

- What is RAG?
- Why do we need RAG?
- Embeddings
- Chunking
- Vector Databases
- Retrieval
- Reranking
- Prompt Construction
- Evaluation
- Common Challenges