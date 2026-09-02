# Dream Catcher

A full-stack dream journal that stores dream entries and generates AI-powered interpretations using OpenAI.

## Features

- Create, view, and delete dream entries
- Generate AI interpretations with OpenAI
- Validate user input and handle API errors
- Store data in PostgreSQL
- Database-aware health check
- Graceful shutdown for HTTP and database connections
- Production security headers with Helmet
- Docker support

## Tech Stack

- Node.js and Express
- PostgreSQL
- OpenAI API
- HTML, CSS, and JavaScript
- Docker
- Render

## Environment Variables

Create a `.env` file:

```env
DATABASE_URL=your_postgresql_connection_string
OPENAI_API_KEY=your_openai_api_key
OPENAI_MODEL=gpt-4o-mini
PORT=3001
NODE_ENV=production