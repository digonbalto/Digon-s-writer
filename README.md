# Academic Writer

Humanize AI text, draft academic sections, and critique writing — powered by Claude.

## Setup

### 1. Install dependencies
```bash
npm install
```

### 2. Add your API key
Edit the `.env` file and replace the placeholder with your real key:
```
ANTHROPIC_API_KEY=sk-ant-your-real-key-here
```
Get a key at https://console.anthropic.com

### 3. Run locally
```bash
npm start
```
Open http://localhost:3000 in your browser.

---

## Deploy to the web (free options)

### Option A — Railway (easiest, recommended)
1. Push this folder to a GitHub repo
2. Go to https://railway.app → New Project → Deploy from GitHub
3. Add environment variable: `ANTHROPIC_API_KEY=sk-ant-...`
4. Done — Railway gives you a public URL instantly

### Option B — Render
1. Push to GitHub
2. Go to https://render.com → New Web Service → connect repo
3. Build command: `npm install`
4. Start command: `node server.js`
5. Add env var: `ANTHROPIC_API_KEY=sk-ant-...`

### Option C — Fly.io
```bash
npm install -g flyctl
fly launch
fly secrets set ANTHROPIC_API_KEY=sk-ant-your-key
fly deploy
```

### Option D — VPS (DigitalOcean / Hetzner)
```bash
git clone your-repo && cd academic-writer
npm install
# Set env var, then:
npm start
# Use nginx + pm2 for production
```

---

## File structure
```
academic-writer/
├── server.js        # Express backend (proxies Anthropic API)
├── package.json
├── .env             # Your API key (never commit this!)
├── .gitignore       # Ignores .env and node_modules
└── public/
    └── index.html   # The full frontend app
```

## How it works
- The frontend sends requests to `/api/chat` on your own server
- Your server adds the secret API key and forwards to Anthropic
- Users never see your API key
