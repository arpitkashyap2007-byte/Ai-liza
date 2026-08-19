# LIZA / Leeza — Vercel deployment

## 1. Deploy
Import this project into Vercel and deploy with the default settings. `vercel.json` already configures Vite + the serverless API function.

## 2. Add the Gemini API key
In Vercel:
**Project → Settings → Environment Variables → Add New**

Name:
`GEMINI_API_KEY`

Value:
`YOUR_GEMINI_API_KEY`

Enable it for **Production**, **Preview**, and **Development** if you want it in all environments, then redeploy.

## 3. Important security note
The current Live voice implementation in `src/App.tsx` reads `process.env.GEMINI_API_KEY` in the browser bundle. That means a Vite build can expose the key to users. For a public production app, use a server-issued ephemeral Gemini Live token instead of shipping the permanent API key to the browser.

The server-side `/chat` and `/api/admin/*` routes keep the key on the server.

## 4. Local development
Create `.env.local`:

`GEMINI_API_KEY=YOUR_GEMINI_API_KEY`

Then run:

`npm install`
`npm run dev`

## 5. Admin password
Set `OWNER_PASSWORD` in Vercel as a secret instead of relying on the fallback password.
