# Digital Discovery RSA Generator

A Google Ads RSA copy generator that produces 15 headlines and 4 descriptions per ad group across 6 copywriting frameworks. Fill in your client brief, add ad groups, and export a CSV ready for Google Sheets.

## Copywriting frameworks

**AIDA** — Attention, Interest, Desire, Action. The classic all-rounder. Headlines are distributed across each stage, ending with a strong call to action. Works for most service businesses.

**PAS** — Problem, Agitate, Solution. Name the pain, intensify the urgency, then position the client as the fix. Best for emergency or high-intent services (electricians, plumbers, locksmiths).

**BAB** — Before, After, Bridge. Paint the current struggle, show the better outcome, then bridge to the client as the way there. Works well for education, health, and transformation-led clients.

**4Ps** — Promise, Picture, Proof, Push. Lead with the core benefit, help the reader visualise the result, back it up with evidence, then push them to act. Strong for lead gen and service businesses.

**USP-led** — Pure differentiator focus. Every headline must contain a concrete, specific point of difference. Best used when the client has a clear competitive advantage (price, speed, credentials, exclusivity).

**Social proof-led** — Trust signals front and centre. Reviews, ratings, years in business, number of clients served. Best when the client has strong numbers to back up their reputation.

---

## Setup

### 1. Get an Anthropic API key
Go to [platform.anthropic.com](https://platform.anthropic.com) → API Keys → Create key.

### 2. Push to GitHub
Create a new repo and upload all files, making sure the folder structure is preserved:

```
rsa-generator/
├── public/
│   └── index.html
├── netlify/
│   └── functions/
│       └── generate.js
├── netlify.toml
└── README.md
```

### 3. Deploy on Netlify
1. Go to [netlify.com](https://netlify.com) and sign up free
2. Click **Add new site** → **Import an existing project** → connect your GitHub repo
3. Build settings are auto-detected from `netlify.toml` — no changes needed
4. Go to **Site configuration** → **Environment variables** → **Add a variable**
   - Key: `ANTHROPIC_API_KEY`
   - Value: your API key from step 1
5. Go to **Deploys** → **Trigger deploy** → **Deploy site**

Netlify gives you a shareable URL like `https://your-site-name.netlify.app`.

---

## How it works

The browser never touches your API key. All requests go through a server-side Netlify function:

```
Browser → /.netlify/functions/generate → Anthropic API
```

The API key only exists as a Netlify environment variable — it is never in the code or visible in GitHub.

---

## Cost

- GitHub: free
- Netlify: free (125,000 function calls/month)
- Anthropic API: pay-as-you-go per token — fractions of a cent per generation session
