# Noor Track Document

**An AI-powered Interview Question Generator and Document Analysis Platform**

Transform your standards, manuals, and documentation into interactive learning materials with automatic interview question generation and intelligent answer extraction.

---

## 🎯 Features

| Feature | Description |
|---------|-------------|
| 📄 **Document Upload** | Upload PDFs, DOCX, and text files (up to 50MB) |
| ❓ **Auto-Generate Questions** | Generate interview questions with answers from documents |
| 💬 **Answer Extraction** | Extract relevant answers for any question using semantic search |
| 📝 **AI Summaries** | Generate study notes using ChatGPT |
| 🔍 **Semantic Search** | Find relevant content using vector embeddings |
| 🚀 **Fast & Scalable** | Built with modern tech stack for performance |

---

## 🏗️ Architecture

```
Frontend (Next.js)
      ↓ HTTP/REST
Backend (Express.js)
      ↓
┌─────────────────────────────┐
│  Services & Processors      │
├─────────────────────────────┤
│ • Document Processing       │
│ • Vector Embeddings         │
│ • OpenAI Integration        │
└─────────────────────────────┘
      ↓
┌─────────────────────────────┐
│  Data Storage               │
├─────────────────────────────┤
│ • PostgreSQL (relational)   │
│ • Pinecone (vectors)        │
│ • Redis (cache)             │
└─────────────────────────────┘
```

**[View Full Architecture](./docs/ARCHITECTURE.md)**

---

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- Docker & Docker Compose (recommended)
- OpenAI API Key
- Pinecone API Key

### Option 1: Docker (Recommended)

```bash
# Clone repository
git clone https://github.com/wahabgul0250-creator/Noor-track-document.git
cd Noor-track-document

# Set environment variables
export OPENAI_API_KEY=sk-your-key
export PINECONE_API_KEY=your-key

# Start all services
docker-compose up

# Access application
# Frontend: http://localhost:3000
# API: http://localhost:5000
```

### Option 2: Local Development

```bash
# Backend
cd backend
cp .env.example .env
# Edit .env with your keys
npm install
npm run dev

# Frontend (in another terminal)
cd frontend
npm install
npm run dev
```

**[Detailed Setup Guide](./docs/SETUP.md)**

---

## 📖 Usage

### 1. Upload Document
- Click "Upload Documents" tab
- Select PDF, DOCX, or TXT file
- File is processed and indexed

### 2. Generate Questions
- Click "Generate Questions" tab
- Select uploaded document
- Specify number of questions
- AI generates Q&A pairs

### 3. Extract Answers
- Click "Extract Answers" tab
- Type any question
- Select document (or search all)
- Get contextual answer with source

### 4. Get AI Summary
- Use API endpoint `/api/summary/generate`
- Provide topic and document IDs
- Receive study notes

---

## 🔌 API Reference

### Upload Document
```bash
curl -F "file=@document.pdf" http://localhost:5000/api/documents/upload
```

### Generate Questions
```bash
curl -X POST http://localhost:5000/api/questions/generate \
  -H "Content-Type: application/json" \
  -d '{"documentId": "doc_123", "numQuestions": 5}'
```

### Extract Answer
```bash
curl -X POST http://localhost:5000/api/answers/extract \
  -H "Content-Type: application/json" \
  -d '{"question": "What is AI?", "documentId": "doc_123"}'
```

**[Full API Documentation](./docs/API.md)**

---

## 🏗️ Project Structure

```
Noor-track-document/
├── backend/
│   ├── src/
│   │   ├── index.js
│   │   ├── routes/
│   │   │   ├── documents.js
│   │   │   ├── questions.js
│   │   │   ├── answers.js
│   │   │   └── summary.js
│   │   └── services/
│   │       ├── documentProcessor.js
│   │       ├── vectorStore.js
│   │       └── openaiService.js
│   ├── package.json
│   ├── .env.example
│   └── Dockerfile
├── frontend/
│   ├── pages/
│   │   ├── index.js
│   │   ├── dashboard.js
│   │   └── _app.js
│   ├── components/
│   │   ├── Layout.js
│   │   ├── DocumentUpload.js
│   │   ├── QuestionGenerator.js
│   │   └── AnswerExtractor.js
│   ├── package.json
│   ├── tailwind.config.js
│   └── Dockerfile
├── docs/
│   ├── ARCHITECTURE.md
│   ├── SETUP.md
│   └── API.md
├── docker-compose.yml
├── setup.sh
└── README.md
```

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| **Frontend** | React 18, Next.js 14, Tailwind CSS |
| **Backend** | Node.js, Express.js |
| **Database** | PostgreSQL, Redis |
| **Vector Store** | Pinecone |
| **AI/ML** | OpenAI GPT-3.5-turbo |
| **DevOps** | Docker, Docker Compose |

---

## 📚 Documentation

- **[Setup Guide](./docs/SETUP.md)** - Installation and configuration
- **[Architecture](./docs/ARCHITECTURE.md)** - System design and data flow
- **[API Reference](./docs/API.md)** - Complete endpoint documentation
- **[Contributing](./CONTRIBUTING.md)** - Contribution guidelines

---

## 🗺️ Roadmap

### Phase 1 (Current)
- ✅ Document upload & processing
- ✅ Question generation
- ✅ Answer extraction
- ✅ AI summaries
- ✅ Basic UI

### Phase 2 (Planned)
- 🔄 User authentication & multi-user support
- 🔄 Document tagging & categorization
- 🔄 Batch operations
- 🔄 Advanced search filters
- 🔄 Export to PDF/Excel

### Phase 3 (Future)
- 📋 Practice quiz mode
- 📋 Analytics dashboard
- 📋 Team collaboration
- 📋 Mobile app
- 📋 Real-time collaboration

---

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](./CONTRIBUTING.md) for:
- Code style guidelines
- Pull request process
- Testing requirements
- Issue reporting

---

## 📄 License

This project is licensed under the MIT License - see LICENSE file for details.

---

## 🆘 Support

- **Issues**: Report bugs on [GitHub Issues](https://github.com/wahabgul0250-creator/Noor-track-document/issues)
- **Discussions**: Join [GitHub Discussions](https://github.com/wahabgul0250-creator/Noor-track-document/discussions)
- **Documentation**: Check [docs/](./docs/) directory

---

## 👤 Author

**Wahabgul0250**
- GitHub: [@wahabgul0250-creator](https://github.com/wahabgul0250-creator)

---

## ⭐ Show Your Support

If you find this project helpful, please give it a star! ⭐

---

**Made with ❤️ for learning and development**
