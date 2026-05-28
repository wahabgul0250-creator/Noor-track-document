# Random Joke Generator - Setup Guide

## Prerequisites

- Node.js 18+
- npm or yarn
- Docker & Docker Compose (optional)

## Quick Start with Docker

```bash
cd joke-generator

# Start services
docker-compose up

# Access application
# Frontend: http://localhost:3001
# Backend API: http://localhost:5001
```

## Local Development Setup

### Backend Setup

```bash
cd joke-generator/backend

# Copy environment template
cp .env.example .env

# Install dependencies
npm install

# Start development server
npm run dev

# API runs on http://localhost:5001
```

### Frontend Setup

```bash
cd joke-generator/frontend

# Install dependencies
npm install

# Start development server
npm run dev

# Application runs on http://localhost:3001
```

## Environment Variables

### Backend (.env)

```
PORT=5001
NODE_ENV=development
JOKE_API_URL=https://v2.jokeapi.dev/joke
CACHE_TTL=300
```

### Frontend (.env.local)

```
NEXT_PUBLIC_API_URL=http://localhost:5001/api
```

## API Testing

### Get Random Joke
```bash
curl http://localhost:5001/api/jokes/random
```

### Get Programming Joke
```bash
curl "http://localhost:5001/api/jokes/random?category=Programming"
```

### Get Joke Without Explicit Content
```bash
curl "http://localhost:5001/api/jokes/random?blacklist=nsfw"
```

### Get Two-Part Joke
```bash
curl "http://localhost:5001/api/jokes/random?type=twopart"
```

## Features

✅ Random joke generation  
✅ Multiple categories  
✅ Content filtering  
✅ Joke history  
✅ Copy to clipboard  
✅ Share on Twitter  
✅ Beautiful UI with animations  
✅ Responsive design  

## Deployment

### Using Docker

```bash
docker-compose up -d
```

### Manual Deployment

**Backend:**
```bash
cd backend
npm install --production
npm start
```

**Frontend:**
```bash
cd frontend
npm install --production
npm run build
npm start
```

## Troubleshooting

### Port Already in Use

```bash
# Kill process on port 5001
lsof -ti:5001 | xargs kill -9

# Kill process on port 3001
lsof -ti:3001 | xargs kill -9
```

### API Connection Error

Ensure `NEXT_PUBLIC_API_URL` matches your backend URL.

### Docker Build Issues

```bash
docker-compose down -v
docker-compose up --build
```

## Performance

- Backend caches jokes for 5 minutes
- Frontend stores joke history in localStorage
- Optimized for mobile and desktop

## Next Steps

1. Deploy to cloud platform (Vercel, Heroku, AWS)
2. Add user authentication
3. Implement joke ratings
4. Create joke categories/tags
5. Add social sharing features

