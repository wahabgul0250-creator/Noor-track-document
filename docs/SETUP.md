# Setup Guide - Noor Track Document

## Prerequisites

- Node.js 18+
- Docker & Docker Compose (optional but recommended)
- OpenAI API Key (Get from https://platform.openai.com/api-keys)
- Pinecone API Key (Get from https://www.pinecone.io)
- PostgreSQL 14+ (if running locally)
- Redis (if running locally)

## Quick Start with Docker (Recommended)

### Step 1: Clone Repository
```bash
git clone https://github.com/wahabgul0250-creator/Noor-track-document.git
cd Noor-track-document
```

### Step 2: Set Environment Variables
```bash
export OPENAI_API_KEY=sk-your-key-here
export PINECONE_API_KEY=your-pinecone-key
```

### Step 3: Start Services
```bash
docker-compose up
```

### Step 4: Access Application
- Frontend: http://localhost:3000
- Backend API: http://localhost:5000
- API Health: http://localhost:5000/health

## Local Development Setup

### Backend Setup

```bash
# Navigate to backend
cd backend

# Copy environment template
cp .env.example .env

# Edit .env with your keys
# OPENAI_API_KEY=sk-...
# DATABASE_URL=postgresql://user:password@localhost:5432/noor_track
# etc.

# Install dependencies
npm install

# Start development server
npm run dev
```

Server runs on http://localhost:5000

### Frontend Setup

```bash
# Navigate to frontend
cd frontend

# Install dependencies
npm install

# Start development server
npm run dev
```

Application runs on http://localhost:3000

## Environment Variables

Create a `.env` file in the `backend` directory:

```bash
# OpenAI Configuration
OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxxx

# Database Configuration
DATABASE_URL=postgresql://user:password@localhost:5432/noor_track
REDIS_URL=redis://localhost:6379

# Pinecone Vector Database
PINECONE_API_KEY=xxxxxxxxxxxxxxxxxxxxxxxx
PINECONE_INDEX=interview-qa
PINECONE_ENVIRONMENT=us-west1-gcp

# Server Configuration
PORT=5000
NODE_ENV=development
MAX_FILE_SIZE=52428800
ALLOWED_FORMATS=pdf,doc,docx,txt
```

## Database Setup (Local)

### PostgreSQL

```bash
# Create database
createdb noor_track

# Connect and setup tables (coming soon)
psql noor_track < migrations/init.sql
```

### Redis

```bash
# Start Redis server
redis-server

# Or with Docker
docker run -d -p 6379:6379 redis:7-alpine
```

## API Testing

### Health Check
```bash
curl http://localhost:5000/health
```

### Upload Document
```bash
curl -F "file=@sample.pdf" http://localhost:5000/api/documents/upload
```

### Generate Questions
```bash
curl -X POST http://localhost:5000/api/questions/generate \
  -H "Content-Type: application/json" \
  -d '{
    "documentId": "doc_123",
    "numQuestions": 5
  }'
```

### Extract Answer
```bash
curl -X POST http://localhost:5000/api/answers/extract \
  -H "Content-Type: application/json" \
  -d '{
    "question": "What is the main topic?",
    "documentId": "doc_123"
  }'
```

## Troubleshooting

### Port Already in Use
```bash
# macOS/Linux - Kill process on port 5000
lsof -ti:5000 | xargs kill -9

# Windows
netstat -ano | findstr :5000
taskkill /PID <PID> /F
```

### Database Connection Error
- Check DATABASE_URL in .env
- Ensure PostgreSQL is running
- Check credentials match

### OpenAI API Error
- Verify OPENAI_API_KEY is valid
- Check API key has sufficient credits
- Test with: https://platform.openai.com/playground

### Pinecone Connection Error
- Verify PINECONE_API_KEY is correct
- Check index name matches
- Ensure environment is correct

### Docker Compose Issues
```bash
# Rebuild containers
docker-compose build --no-cache

# Reset everything
docker-compose down -v
docker-compose up

# View logs
docker-compose logs -f
```

## Development Workflow

### Backend Development
```bash
cd backend
npm run dev        # Start with hot reload
npm run test       # Run tests
npm run lint       # Run linter
```

### Frontend Development
```bash
cd frontend
npm run dev        # Start Next.js dev server
npm run build      # Build for production
npm run start      # Run production build
```

## Production Deployment

### Using Docker
```bash
# Build production images
docker-compose -f docker-compose.yml build

# Start services
docker-compose -f docker-compose.yml up -d
```

### Manual Deployment

Backend:
```bash
cd backend
npm install --production
npm start
```

Frontend:
```bash
cd frontend
npm install --production
npm run build
npm start
```

## Next Steps

1. ✅ Set up environment variables
2. ✅ Configure database
3. ✅ Start backend and frontend
4. ✅ Test file upload
5. ✅ Generate questions
6. ✅ Extract answers
7. ✅ Implement authentication
8. ✅ Deploy to production

## Support

For issues or questions:
1. Check GitHub Issues
2. Review documentation in `/docs`
3. Check error logs: `docker-compose logs`
4. Test with Postman or cURL

