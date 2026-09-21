# Dream Catcher

A full-stack dream journal. Write down a dream, get an AI-generated interpretation, and browse your past entries.

## Features

- Create, view, and delete dream entries
- AI-generated dream interpretations (OpenAI by default, with a Gemini implementation available as a drop-in swap)
- Server-side input validation with clear error responses
- Database-aware `/health` endpoint reporting connection status and uptime
- Graceful shutdown of the HTTP server and database pool on `SIGTERM`
- Production security headers via Helmet
- Dockerized, deployed on Render

## Tech Stack

- Node.js + Express (ESM)
- PostgreSQL (via `pg`)
- OpenAI API for interpretations
- Helmet for security headers
- Vanilla HTML/CSS/JS frontend
- Docker

## API

| Method | Endpoint          | Description                                      |
| ------ | ----------------- | ------------------------------------------------- |
| GET    | `/api/dreams`      | List all dreams, newest first                     |
| GET    | `/api/dreams/:id`  | Get a single dream                                |
| POST   | `/api/dreams`      | Create a dream; validates text, then generates and stores an AI interpretation |
| DELETE | `/api/dreams/:id`  | Delete a dream                                    |
| GET    | `/health`          | DB connectivity check + process uptime            |

## Getting Started

```bash
npm install
```

Create a `.env` file:

```
DATABASE_URL=postgres://user:password@host:port/dbname
OPENAI_API_KEY=your-openai-key
OPENAI_MODEL=gpt-4o-mini   # optional, defaults to gpt-4o-mini
PORT=3001                  # optional
```

```bash
npm run dev    # nodemon, for local development
npm start      # plain node
```

The app initializes the database schema on startup and serves the frontend from `/public`.

## Notes

- Security headers (Helmet) are only enabled when `NODE_ENV=production`.
- To use Gemini instead of OpenAI, swap the import in `routes/dreams.js` from `utils/ai-openai.js` to `utils/ai-gemini.js` and set the corresponding API key.
