# 🐍 WormGPT v4.1 — Free Provider Waterfall

Self-hosted uncensored AI. No filters. Runs on free APIs.

## Provider Chain (all FREE)

| # | Provider | Free Model | Get Key |
|---|----------|-----------|---------|
| 1 | **Google Gemini** | gemini-2.0-flash | aistudio.google.com |
| 2 | **Groq** | llama-3.3-70b-versatile | console.groq.com |
| 3 | **OpenRouter** | qwen/qwen3-coder:free → openai/gpt-oss-120b:free | openrouter.ai |

Auto-switches on 402 / 429 / 5xx. Claude & OpenAI dormant until credited key added.

## Features

- ⚡ **Auto provider waterfall** — zero cost, zero downtime
- 🔑 **In-app key management** — Settings modal, saved to disk
- 🔴 **Key tester** — test each key before saving
- 😈 **Dark GOD Mode** — hardened system prompt via toggle or Dark tab
- 💬 **Chat / Agent / Dark modes** — sidebar tab switcher
- 📎 **File attachments** — images, PDF, code files, CSV, JSON
- 🖼 **Image vision** — with Gemini Vision & OpenRouter vision models
- 🔍 **Chat search** — sidebar filter
- 📋 **Quick commands bar** — one-tap common payloads
- 💾 **Persistent history** — survives restarts, stored in data/chats.json
- ✎ **Rename chats** — from topbar or sidebar
- ↻ **Regenerate** — redo last response
- 📤 **Share / copy** — message actions
- ⬇ **Export** — Markdown or JSON
- 📱 **Mobile responsive** — sidebar overlay, safe-area aware

## Setup

```bash
npm install
node server.js
# → http://localhost:3000
```

Then open Settings (⚙) → enter keys → Save.

Or via env vars (overrides UI keys):
```bash
GEMINI_KEY=AIza... GROQ_KEY=gsk_... OPENROUTER_KEY=sk-or-... node server.js
```

## Get Free Keys (5 minutes total)

**Gemini** — fastest, best quality:
→ aistudio.google.com → Get API key

**Groq** — ultra-fast LLaMA inference:
→ console.groq.com → API Keys → Create

**OpenRouter** — free model pool:
→ openrouter.ai → Keys → Create key

## Deploy to Railway (free hosting)

1. Push to GitHub (private)
2. railway.app → New → Deploy from GitHub
3. Variables tab → add: GEMINI_KEY, GROQ_KEY, OPENROUTER_KEY
4. Live in ~90 seconds

## File Structure

```
wormgpt/
├── server.js          # Express backend + provider waterfall
├── package.json
├── public/
│   └── index.html     # Full SPA — all UI in one file
├── data/              # Auto-created
│   ├── chats.json     # Chat history
│   └── settings.json  # API keys + preferences
└── uploads/           # Temp file storage (auto-created)
```
