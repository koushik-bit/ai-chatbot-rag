# AI Chatbot RAG Backend

Backend-only Retrieval Augmented Generation (RAG) chatbot built using **FastAPI**, **LangChain**, **PostgreSQL (pgvector)** and configurable LLM providers (OpenAI / Gemini / Anthropic).

---

## Features

- Chat endpoint with conversational memory
- File upload endpoint for contextual RAG (PDF / text files)
- Conversation history stored and reused from database
- Retrieval Augmented Generation using user-provided documents
- Session-based chat and document isolation
- PostgreSQL with pgvector for vector storage
- Configurable LLM provider via environment variables
- Dockerized setup using docker-compose
- No frontend UI (API-only)

---

## Tech Stack

- FastAPI
- LangChain
- PostgreSQL + pgvector
- OpenAI / Gemini / Anthropic (configurable)
- Docker & Docker Compose

---

## API Endpoints

### 1. Chat Endpoint
`POST /chat`

Send a message to the chatbot.

**Request Body**
```json
{
  "session_id": "string",
  "message": "string"
}
```
**Response**
```json
{
  "response": "string"
}
```

---


###2. Upload File Endpoint
POST /upload

Upload a document to be used as contextual knowledge for the chatbot.

Form Data

session_id (string)

file (PDF or text file)
---


###Environment Variables
Create a .env file using the example below.
```env
LLM_PROVIDER=openai

OPENAI_API_KEY=your_openai_api_key
OPENAI_MODEL=gpt-4o-mini

DATABASE_URL=postgresql+psycopg2://postgres:postgres@db:5432/postgres

APP_DEBUG=true
```
Local Setup (Docker)
Prerequisites
Docker

Docker Compose

###Steps

git clone https://github.com/koushik-bit/ai-chatbot-rag.git
cd ai-chatbot-rag
cp .env.example .env
docker-compose up --build
The backend will be available at:
http://localhost:8000
Swagger API Docs:
http://localhost:8000/docs
Notes
All chats and uploaded documents are scoped by session_id

Conversation history is retrieved from the database and reused for response generation

No frontend UI is included
