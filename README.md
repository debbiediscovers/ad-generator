# Digital Discovery RSA Generator

Google Ads RSA copy generator — produces 15 headlines and 4 descriptions across 6 copywriting frameworks (AIDA, PAS, BAB, 4Ps, USP-led, Social proof) for each ad group.

## Setup

### 1. Get an Anthropic API key
Go to [platform.anthropic.com](https://platform.anthropic.com) → API Keys → Create key.

### 2. Push to GitHub
Create a new repo and push this folder to it.

### 3. Deploy on Netlify
1. Go to [netlify.com](https://netlify.com) and sign up free
2. Click **Add new site** → **Import an existing project** → connect your GitHub repo
3. Build settings are auto-detected from `netlify.toml` — no changes needed
4. Go to **Site configuration** → **Environment variables** → **Add a variable**
   - Key: `ANTHROPIC_API_KEY`
   - Value: your API key from step 1
5. Click **Deploy site**

Netlify gives you a shareable URL like `https://your-site-name.netlify.app`.

## Folder structure

```
/
├── public/
│   └── index.html          # The app
├── netlify/
│   └── functions/
│       └── generate.js     # Proxy — keeps API key server-side
└── netlify.toml            # Build config
```

## How it works

The browser never touches your API key. All requests go:

```
Browser → /.netlify/functions/generate → Anthropic API
```

The API key only exists as a Netlify environment variable, never in the code.
