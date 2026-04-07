Overview
This project showcases the creation of a document-driven conversational AI system using the RAG framework in Flowise. It processes uploaded files, converts their content into embeddings, stores them in a vector database, and uses a language model to generate answers based on the most relevant retrieved information.
🚀 Key Features
Upload and process documents easily
Ask context-aware questions
Semantic search using embeddings
Maintains conversation history
Fast retrieval with in-memory storage
Built using Flowise’s visual interface
🛠️ Tech Stack
Flowise
Google Gemini Embeddings
Mistral AI
Recursive Character Text Splitter
File Loader
In-Memory Vector Store
Buffer Memory
Conversational Retrieval QA Chain
🧩 Workflow
The chatbot pipeline consists of the following components:
Recursive Character Text Splitter
Breaks documents into smaller chunks
Chunk Size: 1000
Chunk Overlap: 200
File Loader
Imports the document into the system
Google Gemini Embeddings
Model: gemini-embedding-001
Task Type: RETRIEVAL_DOCUMENT
In-Memory Vector Store
Stores embeddings for fast retrieval
Top K: 4
Mistral AI
Model: mistral-tiny
Temperature: 0.9
Buffer Memory
Keeps track of conversation history
Conversational Retrieval QA Chain
Integrates retriever, memory, and LLM
Generates context-aware responses
⚙️ Working Process
The user uploads a document via the File Loader
The content is split into chunks using the Text Splitter
Each chunk is transformed into embeddings with Gemini Embeddings
These embeddings are stored in the Vector Store
When a query is asked:
Relevant chunks are retrieved
Mistral AI generates a response based on context
Buffer Memory ensures conversational continuity.
Author

Vanshika
