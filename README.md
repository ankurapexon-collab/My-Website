# Ankur Singh — Portfolio

A single-page portfolio (`index.html`) with a working contact form backed by
a Vercel serverless function (`api/contact.js`) that emails submissions to you.

## Project structure

```
ankur-portfolio/
├── index.html        ← the whole site (static, no build step)
├── api/
│   └── contact.js     ← serverless function, handles POST /api/contact
├── package.json        ← declares the nodemailer dependency
├── .env.example         ← template for the environment variables you need
└── README.md
```

## Setting up email sending (SMTP)

The backend needs SMTP credentials to actually send mail. Two easy free options:

**Option A — Gmail (quickest if you already have a Gmail account)**
1. Turn on 2-Step Verification on your Google account.
2. Go to https://myaccount.google.com/apppasswords and create an "app password".
3. Use these values:
   - `SMTP_HOST=smtp.gmail.com`
   - `SMTP_PORT=587`
   - `SMTP_SECURE=false`
   - `SMTP_USER=<your gmail address>`
   - `SMTP_PASS=<the 16-character app password>`

**Option B — Resend (built for this, generous free tier, no app-password fuss)**
1. Create a free account at https://resend.com and verify a sending domain or use their test domain.
2. Use these values:
   - `SMTP_HOST=smtp.resend.com`
   - `SMTP_PORT=587`
   - `SMTP_SECURE=false`
   - `SMTP_USER=resend`
   - `SMTP_PASS=<your Resend API key>`

Either way, also set `CONTACT_TO_EMAIL` to the inbox you want messages delivered to
(defaults to `ankur.singh@apexon.com` if you don't set it).

## Local testing (optional)

```bash
npm install -g vercel
npm install
vercel dev
```

This runs the site and the `/api/contact` function locally at `http://localhost:3000`.
Create a real `.env` file (not committed) with the values from `.env.example` first.
