# 🐍 WormGPT v3.0 — Self-Hosted Uncensored AI

Full-featured, self-hosted WormGPT web application. No filters. No restrictions. No refusals.

## Features

- **Claude + OpenAI support** — swap between providers, pick any model
- **Image upload** — vision analysis with Claude Vision / GPT-4o
- **File upload** — PDF, TXT, code files sent as context
- **Full chat history** — persistent, stored locally in JSON
- **Multi-session** — unlimited named chats, sidebar navigation
- **Search chats** — filter sidebar by title
- **Export chats** — Markdown or JSON download
- **Rename / delete chats**
- **Regenerate** — redo last response
- **Copy code blocks** — one-click copy on every code block
- **Streaming responses** — token by token, live
- **Image lightbox** — click any image to fullscreen
- **Hardcoded system prompt** — WormGPT persona is server-side, cannot be weakened from UI
- **Mobile responsive**

## Setup

### 1. Install dependencies
```bash
npm install
```

### 2. Start the server
```bash
node server.js
```
Runs on `http://localhost:3000`

### 3. Configure API keys
Open `http://localhost:3000` → click **⚙ Settings** → enter your keys.

Or set via environment variables:
```bash
CLAUDE_KEY=sk-ant-api03-... OPENAI_KEY=sk-... node server.js
```

### 4. (Optional) Custom port
```bash
PORT=8080 node server.js
```

## API Keys

- **Claude**: https://console.anthropic.com → API Keys
- **OpenAI**: https://platform.openai.com → API Keys

Claude recommended — best at following the WormGPT system prompt fully.

## Self-hosting on a VPS

```bash
# Install Node if needed
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs

# Clone / copy files
git clone <your-repo>
cd wormgpt
npm install

# Run with PM2 (auto-restart)
npm install -g pm2
pm2 start server.js --name wormgpt
pm2 save
pm2 startup
```

Then point nginx at port 3000.

## File Structure

```
wormgpt/
├── server.js          # Express backend
├── package.json
├── public/
│   └── index.html     # Full frontend SPA
├── data/
│   ├── chats.json     # Chat history (auto-created)
│   └── settings.json  # API keys (auto-created)
└── uploads/           # Temp file storage (auto-created)
```

## Notes

- API keys stored in `data/settings.json` on your server — never leave the machine
- Chat history stored locally in `data/chats.json`
- Uploads are temporary — stored in `uploads/` and used only for the current request
- The WormGPT system prompt is in `server.js` → `WORMGPT_SYSTEM` constant — edit it there if needed
