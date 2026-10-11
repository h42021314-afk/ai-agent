# StudyAI Agent

A polished AI study assistant dashboard for turning prompts and study material into quizzes and flashcards.

## Run locally

```bash
npm install
npm run dev
```

Open http://localhost:5173. The Vite frontend proxies `/api` requests to the demo API on port 8787.

For a production build:

```bash
npm run build
npm start
```

## Project structure

- `src/App.tsx` - responsive dashboard, creators, quiz player, flashcards, library, and settings UI
- `src/styles.css` - visual system and responsive layout
- `server/index.js` - `POST /api/generate` endpoint and demo agent service
- `.env.example` - server-only configuration template

## API contract

`POST /api/generate` accepts:

```json
{ "type": "quiz", "prompt": "Create a quiz about photosynthesis", "difficulty": "medium", "count": 10 }
```

Set `type` to `flashcards` for flashcard output. The response includes structured `content`, `title`, `difficulty`, and `mode` fields.

## Connecting a real AI provider

The app intentionally ships without a secret or hard-coded API key. Add `AI_API_KEY` and, if needed, `AI_API_URL` to a server-side `.env` file based on your chosen provider. Replace the demo `createQuiz` and `createFlashcards` calls in `server/index.js` with a server-side provider request that validates the returned JSON against the same response shape. Never expose the key through React or `VITE_*` variables.
