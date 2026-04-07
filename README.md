Overview

This project shows how to build a Retrieval-Augmented Generation (RAG) chatbot from scratch using document processing, embeddings, vector search, and a conversational AI model.

⚙️ Setup & Code Creation
1️⃣ Initialize Project
mkdir rag-chatbot
cd rag-chatbot
npm init -y
2️⃣ Install Dependencies
npm install langchain @google/generative-ai @langchain/mistralai dotenv
3️⃣ Configure Environment Variables

Create a .env file:

GOOGLE_API_KEY=your_google_api_key
MISTRAL_API_KEY=your_mistral_api_key
4️⃣ Create Main File

Create index.js and add the following code:

🧠 Full Implementation Code
import dotenv from "dotenv";
dotenv.config();

import { TextLoader } from "langchain/document_loaders/fs/text";
import { RecursiveCharacterTextSplitter } from "langchain/text_splitter";
import { GoogleGenerativeAIEmbeddings } from "@langchain/google-genai";
import { MemoryVectorStore } from "langchain/vectorstores/memory";
import { ChatMistralAI } from "@langchain/mistralai";
import { ConversationalRetrievalQAChain } from "langchain/chains";

async function runRAG() {
  // 1. Load document
  const loader = new TextLoader("data/ai_ethics.txt");
  const docs = await loader.load();

  // 2. Split text
  const splitter = new RecursiveCharacterTextSplitter({
    chunkSize: 1000,
    chunkOverlap: 200,
  });
  const splitDocs = await splitter.splitDocuments(docs);

  // 3. Create embeddings
  const embeddings = new GoogleGenerativeAIEmbeddings({
    modelName: "gemini-embedding-001",
  });

  // 4. Store in vector DB
  const vectorStore = await MemoryVectorStore.fromDocuments(
    splitDocs,
    embeddings
  );

  // 5. Initialize LLM
  const model = new ChatMistralAI({
    apiKey: process.env.MISTRAL_API_KEY,
    modelName: "mistral-tiny",
    temperature: 0.9,
  });

  // 6. Create RAG chain
  const chain = ConversationalRetrievalQAChain.fromLLM(
    model,
    vectorStore.asRetriever(),
    {
      returnSourceDocuments: true,
    }
  );

  // 7. Ask question
  const chatHistory = [];

  const response = await chain.call({
    question: "What is AI ethics?",
    chat_history: chatHistory,
  });

  console.log(response.text);
}

runRAG();
📂 Project Structure
rag-chatbot/
│── data/
│   └── ai_ethics.txt
│── index.js
│── .env
│── package.json
🚀 Run the Code
node index.js
🧠 How It Works
Load document
Split into chunks
Convert chunks → embeddings
Store embeddings in vector database
Retrieve relevant chunks on query
Pass context to LLM
Generate final response
📊 Key Parameters
Chunk Size: 1000
Chunk Overlap: 200
Temperature: 0.9
Retrieval: Top relevant chunks
📈 Future Improvements
Use FAISS / Pinecone (persistent DB)
Add UI (React / Streamlit)
Support multiple documents
Deploy as API
🎯 Key Learning

This project demonstrates how to:

Build a complete RAG pipeline
Improve AI accuracy using retrieval
Reduce hallucination in LLMs
👩‍💻 Author

Vanshika
