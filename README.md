# AI Constitution — Join39 App

A values/principles provider that Join39 agents can call to load constitutional alignment principles inspired by Anthropic's Constitutional AI approach.

## What It Does

When an agent calls this tool, it receives a structured set of principles covering:

- **Safety & Harmlessness** — Prevent harm, refuse dangerous requests
- **Honesty & Transparency** — No fabrication, acknowledge limitations
- **Helpfulness & Quality** — Useful, relevant, balanced responses
- **Fairness & Non-Discrimination** — Equal respect, no stereotypes
- **Privacy & Data Respect** — Protect personal information

Plus **meta-guidance** on conflict resolution (safety > honesty > fairness > privacy > helpfulness) and edge case handling.

## Setup

```bash
npm install
npm start
```

The server runs on port 3000 (or set `PORT` env variable).

## Deploy

Deploy to any Node.js hosting platform:

- **Railway**: `railway up`
- **Render**: Connect your repo, set start command to `npm start`
- **Vercel**: Use the Express adapter or convert to a serverless function
- **Fly.io**: `fly launch && fly deploy`

Make sure your deployed URL uses **HTTPS** (required by Join39).


## Test Locally

```bash
# Full constitution
curl -X POST http://localhost:3000/api/constitution \
  -H "Content-Type: application/json" \
  -d '{}'

# Specific category
curl -X POST http://localhost:3000/api/constitution \
  -H "Content-Type: application/json" \
  -d '{"category": "safety"}'

# Without meta-guidance
curl -X POST http://localhost:3000/api/constitution \
  -H "Content-Type: application/json" \
  -d '{"include_meta": false}'
```

## Customization

Edit the `constitution` object in `server.js` to add your own principles, modify existing ones, or add new categories. The structure is straightforward — each category has a label and an array of rules.
