# RAG Chatbot Backend

A Retrieval-Augmented Generation (RAG) chatbot application that processes PDF documents and provides intelligent responses using OpenAI's language models with Qdrant vector database for semantic search.

## Features

- **PDF Upload & Processing** - Upload and process PDF documents
- **Vector Embeddings** - Generate embeddings using OpenAI API
- **Semantic Search** - Query documents using Qdrant vector database
- **AI Chat** - Get intelligent responses augmented with document context
- **RESTful API** - Easy-to-use Express.js API endpoints

## Prerequisites

- Node.js (v14 or higher)
- npm or yarn
- OpenAI API key
- Qdrant instance (local or cloud)

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd backend
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file in the project root:
```
OPENAI_API_KEY=your_openai_api_key_here
QDRANT_URL=http://localhost:6333
QDRANT_API_KEY=your_qdrant_api_key_here
```

## Configuration

### Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `OPENAI_API_KEY` | OpenAI API key for embeddings and chat | `sk-...` |
| `QDRANT_URL` | Qdrant server URL | `http://localhost:6333` |
| `QDRANT_API_KEY` | Qdrant API key for authentication | `your-key` |

## Running the Application

Start the development server:
```bash
npm start
```

The server will run on `http://localhost:3000` (or your configured port).

## API Endpoints

### Upload PDF
**POST** `/api/upload`
- Upload a PDF file for processing
- Returns collection ID and document count

### Chat
**POST** `/api/chat`
- Send a query and get AI-powered response
- Uses RAG to retrieve relevant context from uploaded documents

### Health Check
**GET** `/api/health`
- Check if the server is running

## Project Structure

```
backend/
├── server.js           # Main server file
├── routes/             # API routes
├── controllers/        # Business logic
├── utils/              # Helper functions
├── uploads/            # Temporary PDF storage
├── .env                # Environment variables (not in git)
├── .gitignore          # Git ignore rules
├── package.json        # Dependencies
└── README.md           # This file
```

## Dependencies

- **express** - Web framework
- **dotenv** - Environment variable management
- **axios** - HTTP client
- **multer** - File upload handling
- **pdfparse** - PDF text extraction
- **openai** - OpenAI API client
- **qdrant-js-client** - Qdrant vector database client

## Getting API Keys

### OpenAI API Key
1. Visit [OpenAI Platform](https://platform.openai.com)
2. Sign up or log in
3. Navigate to API keys section
4. Create a new API key
5. Add to `.env` file

### Qdrant API Key
1. Set up a Qdrant instance locally or use cloud
2. For local: `docker run -p 6333:6333 qdrant/qdrant`
3. For cloud: Visit [Qdrant Cloud](https://cloud.qdrant.io)
4. Get your API key and URL

## Usage Example

```bash
# Upload a PDF
curl -X POST -F "file=@document.pdf" http://localhost:3000/api/upload

# Send a query
curl -X POST http://localhost:3000/api/chat \
  -H "Content-Type: application/json" \
  -d '{"query":"What is this document about?"}'
```

## Troubleshooting

### Issue: OPENAI_API_KEY not found
- Ensure `.env` file exists in project root
- Check variable name matches exactly
- Restart the server after adding `.env`

### Issue: Cannot connect to Qdrant
- Verify Qdrant is running on the specified URL
- Check QDRANT_URL is correct
- Ensure API key is valid

### Issue: PDF upload fails
- Check file size limits
- Ensure uploads/ folder exists and has write permissions
- Verify multer configuration

## License

MIT

## Support

For issues and questions, please create an issue in the repository.
