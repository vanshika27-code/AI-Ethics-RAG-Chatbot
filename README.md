RAG Chatbot with Flowise

A smart *Retrieval-Augmented Generation (RAG) Chatbot* built using *Flowise* that allows users to upload documents and ask context-aware questions. The chatbot retrieves relevant document chunks using *Google Gemini Embeddings* and generates accurate answers with *Mistral AI*.

---

 Overview

This project demonstrates how to build a *document-based conversational AI system* using the RAG architecture in Flowise. It processes uploaded documents, converts them into embeddings, stores them in a vector store, and uses an LLM to answer user queries based on retrieved context.

---

 Features

- Upload and analyze documents
- Context-aware question answering
- Semantic document retrieval using embeddings
- Maintains chat history using memory
- Fast retrieval with in-memory vector storage
- Built visually using Flowise nodes

---

Technologies Used

- *Flowise*
- *Google Gemini Embeddings*
- *Mistral AI*
- *Recursive Character Text Splitter*
- *File Loader*
- *In-Memory Vector Store*
- *Buffer Memory*
- *Conversational Retrieval QA Chain*

---

 Workflow

The chatbot flow includes the following components:

1. *Recursive Character Text Splitter*
   - Splits the document into smaller chunks
   - Chunk Size: 1000
   - Chunk Overlap: 200

2. *File Loader*
   - Loads the source document into the workflow

3. *Google Gemini Embeddings*
   - Model: gemini-embedding-001
   - Task Type: RETRIEVAL_DOCUMENT

4. *In-Memory Vector Store*
   - Stores document embeddings for retrieval
   - Top K: 4

5. *Mistral AI*
   - Model: mistral-tiny
   - Temperature: 0.9

6. *Buffer Memory*
   - Stores previous conversation context

7. *Conversational Retrieval QA Chain*
   - Combines retriever, memory, and language model
   - Produces context-based answers
<img width="1847" height="873" alt="rag" src="https://github.com/user-attachments/assets/09ff2c57-7489-4821-b419-e6419fa68312" />

---

 How It Works

1. A document is uploaded using the *File Loader*
2. The text is split into chunks using the *Recursive Character Text Splitter*
3. Each chunk is converted into embeddings using *Google Gemini Embeddings*
4. Embeddings are stored in the *In-Memory Vector Store*
5. When the user asks a question:
   - Relevant chunks are retrieved from the vector store
   - Mistral AI generates a response using retrieved context
   - Buffer Memory maintains the conversation flow

---

 Project Structure

```bash
RAG-Chatbot-Flowise/
│── README.md
│── RAG CHATBOT Chatflow.json
│── screenshot.png
│── sample-document.pdf
This project demonstrates how to:

Build a complete RAG pipeline
Improve AI accuracy using retrieval
Reduce hallucination in LLMs
👩‍💻 Author

Vanshika
