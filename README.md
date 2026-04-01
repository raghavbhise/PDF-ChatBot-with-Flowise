This project demonstrates how to build a Document Question Answering (PDF Chatbot) using Flowise.
It allows users to upload a PDF and ask questions based strictly on its content using a Retrieval-Augmented Generation (RAG) pipeline.

🚀 Overview

This chatbot works by:

Loading a PDF document
Splitting it into smaller chunks
Converting text into embeddings
Storing embeddings in a vector database
Retrieving relevant chunks
Generating answers using an LLM

The workflow is implemented visually using Flowise nodes.

🧰 Prerequisites

Before starting, ensure you have:

Node.js (v16 or above)
Internet connection (for API calls)
API Keys:
Groq API Key
Hugging Face API Key
📝 Step 1: Sign Up & Get API Keys
1. Groq API (LLM)
Visit Groq website
Sign up / log in
Generate an API key
Save it securely
2. Hugging Face API (Embeddings)
Visit Hugging Face
Create an account
Go to Access Tokens
Generate a new token
⚙️ Step 2: Install Flowise

Follow these steps to run Flowise locally:

npm install -g flowise
npx flowise start

Then open in browser:

http://localhost:3000

Flowise provides a drag-and-drop interface for building AI workflows.

🏗️ Step 3: Import or Create Chatflow
Option A: Import Existing Flow
Open Flowise UI
Click Import Chatflow
Upload the provided JSON file
Option B: Build Manually

Create the following nodes:

🔗 Step 4: Workflow Architecture
1. Text Splitter
Node: Recursive Character Text Splitter
Chunk Size: 1000
Chunk Overlap: 200

👉 Splits PDF into smaller chunks

2. PDF Loader
Node: PDF File Loader
Usage: Per Page

👉 Loads PDF and extracts content

3. Embeddings
Node: HuggingFace Inference Embeddings
Model: sentence-transformers/all-MiniLM-L6-v2
Add Hugging Face API key

👉 Converts text into vectors

4. Vector Store
Node: In-Memory Vector Store
Top K: 8

👉 Stores embeddings and retrieves relevant chunks

5. Chat Model
Node: Groq Chat Model
Model: llama-3.1-8b-instant
Add Groq API key

👉 Generates answers

6. Conversational Retrieval QA Chain
Connect:
Chat Model
Vector Store Retriever
Response Prompt:
Answer ONLY using the provided context.
If not found, say "Not in document".

👉 Ensures accurate, context-based answers

🔌 Step 5: Connect Nodes

Follow this connection flow:

Text Splitter → PDF Loader → Vector Store
Embeddings → Vector Store
Vector Store → QA Chain
Chat Model → QA Chain

This creates a complete RAG pipeline.

▶️ Step 6: Run the Chatbot
Upload a PDF
Ask questions like:
"What is the summary?"
"Explain key concepts"
The chatbot responds using only the document content
💡 Key Features
📄 PDF-based Q&A
🔍 Semantic search using embeddings
🧠 Context-aware responses
⚡ Fast inference using Groq
🧩 No-code visual workflow
🧠 How It Works
PDF is loaded
Text is split into chunks
Embeddings are generated
Stored in vector database
Query is matched with relevant chunks
LLM generates response
🛠️ Customization

You can:

Change embedding models
Use different LLMs (OpenAI, Gemini, etc.)
Adjust chunk size for performance
Add memory for conversation tracking
📌 Applications
Document Q&A systems
Research assistants
Customer support bots
Educational tools
⚠️ Notes
Answers are limited to document content
Large PDFs may increase processing time
API usage may incur cost
📚 Conclusion

This project showcases how Flowise simplifies building advanced AI applications without coding, using a powerful RAG architecture.
