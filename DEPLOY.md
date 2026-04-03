# BLOOM App — Deployment Guide

## What's in this folder

```
bloom-deploy/
├── public/
│   └── index.html          ← The full BLOOM app (all screens + Sage)
├── netlify/
│   └── functions/
│       └── sage.js         ← Serverless function (Sage AI proxy)
├── netlify.toml            ← Netlify config
└── DEPLOY.md               ← This file
```

---

## Deploy in 5 steps (15 minutes total)

### Step 1 — Create a Netlify account
Go to netlify.com and sign up (free). Connect your GitHub account.

### Step 2 — Push this folder to GitHub
Create a new GitHub repository called `bloom-app`.
Upload all files in this folder to it.

Or from terminal:
```bash
git init
git add .
git commit -m "BLOOM app initial deploy"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/bloom-app.git
git push -u origin main
```

### Step 3 — Connect to Netlify
1. In Netlify dashboard → "Add new site" → "Import an existing project"
2. Choose GitHub → select your `bloom-app` repo
3. Build settings are auto-detected from `netlify.toml`
4. Click "Deploy site"

### Step 4 — Add your Anthropic API key
1. In Netlify dashboard → Your site → "Site configuration" → "Environment variables"
2. Click "Add a variable"
3. Key: `ANTHROPIC_API_KEY`
4. Value: your Anthropic API key (get it from console.anthropic.com)
5. Click "Save"
6. Trigger a redeploy: Deploys → "Trigger deploy" → "Deploy site"

### Step 5 — Set your custom domain (optional)
1. In Netlify → Domain management → "Add custom domain"
2. Enter: `bloompregnancybook.com` (or whatever you registered)
3. Follow DNS instructions — usually takes 10-30 minutes to propagate

---

## Your app will be live at:
`https://your-site-name.netlify.app` (free Netlify subdomain)
or your custom domain once DNS propagates.

---

## How Sage works in production

The app calls `/api/sage` → Netlify routes it to `netlify/functions/sage.js` →
the function calls the Anthropic API with your secret key → returns Sage's reply.

Your API key never touches the browser. It lives only on the server.

---

## Anthropic API costs

At 1,000 monthly active users, Sage costs approximately $80–150/month in API usage.
At launch (first 100 users) it will be under $5/month.

Monitor usage at console.anthropic.com → Usage.

---

## Adding a waitlist email capture

Replace the form action in `bloom-waitlist.html` with a ConvertKit or Mailchimp embed:

1. Go to convertkit.com → Forms → Create a form
2. Copy the embed code
3. Replace the `<form onsubmit="joinWaitlist...">` section in the landing page

---

## Files to send to printer

When ready for print production, the design specs are:
- Trim size: 6" x 9"
- Interior paper: 90lb uncoated
- Cover: hardcover, linen or matte laminate
- Scratch-off panels: lottery scratch-off laminate on designated zones
- Color profile: CMYK, 300 DPI minimum
- Bleed: 0.125" on all sides

Export from Affinity Publisher as PDF/X-1a for print.

---

## Questions?
Everything built by Claude for BLOOM — Natalie's pregnancy journey book.
