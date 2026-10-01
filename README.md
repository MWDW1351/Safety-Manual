# Safety manual chat: deploy steps (Azure Static Web Apps)

Layout: `public/` = web page + the .docx; `api/` = chat function + `manual.md` (the manual text, server-side only).

1. Push this folder to a GitHub repo.
2. Azure Portal > Create > Static Web App. Source: your repo. Build preset: Custom.
   App location: `public`   API location: `api`   Output location: (blank).
3. In the app's Environment variables, add `ANTHROPIC_API_KEY` (from console.anthropic.com).
   Set a monthly spend limit on that key's workspace.
4. The site is public (no login). Protect your bill: set a monthly spend limit on the
   Anthropic workspace for this key. The function also caps each visitor at 15 questions
   per 10 minutes and the whole site at 1,500 per day (edit PER_IP / DAILY_CAP in chat.js).
5. Open the site URL, test a few questions, then generate the QR code from that URL
   and paste it into the Word manual's cover or "Find help quickly" page.

To update the manual: re-export the text into `api/manual.md`, replace the .docx in `public/`, push.
