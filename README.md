# Tax-simplicity-advisor-
My teams submission for craft and code iiit bhubaneshwar hackathon 2026



Tax-Simplicity Advisor
PS-12 · Craft-n-Code 2026 · Informal Economy Tax-Simplicity Advisor

Describe a small business in plain language and get back its likely tax bracket, an estimated dues figure, and the government benefits (Udyam, MUDRA, PMEGP, PM SVANidhi) it can unlock — without needing to understand tax law first. Built to de-mystify formalization instead of policing informality.

Live demo
👉 https://YOUR-GITHUB-USERNAME.github.io/YOUR-REPO-NAME/

(Update this link once GitHub Pages is enabled — see Deployment below.)

How it works
Input — a plain-text description of the business, either typed or picked from three worked examples (a vegetable cart, a home tailor, a welding workshop) spanning different tax brackets.
Fact extraction — the description is parsed into structured facts (business type, turnover, location, employee count):
Live, via Google's free Gemini API, if a key is set, or
Offline, via a local regex parser, if no key is set or the API call fails.
Rule engine (deterministic, not AI) — those facts are mapped to a tax bracket, an estimated dues figure using marginal income-tax slabs, and a list of unlocked schemes. This split matters: the AI only ever extracts facts from free text, it never invents a tax number — every figure traces back to a rule you can point to and defend, visible via the "Why this number?" breakdown in the UI.
Output — results render as a stamped passbook entry, plus a second-step "Start Udyam Registration" action pre-filled from the parsed facts.
Running it locally
Just open index.html in a browser — the three worked examples run fully offline, no setup needed.

For live AI parsing of any free-text description (not just the presets), click AI settings and paste a free Gemini API key:

Go to https://aistudio.google.com/apikey (no credit card required).
Create a key and paste it into the panel — it's kept only in that browser tab's memory, never written to disk or sent anywhere except directly to Google's API.
Note on file://: opening the file directly by double-clicking it can trigger inconsistent browser security restrictions on the live-AI network call in some setups. If AI parsing acts up locally, serve the folder with a simple local server instead (e.g. python -m http.server) and open http://localhost:8000/index.html — or just use the deployed GitHub Pages link below, which sidesteps the issue entirely. The offline preset examples work fine either way.

Deployment (GitHub Pages)
Push index.html and this README.md to a public GitHub repo.
In the repo: Settings → Pages → Source: Deploy from a branch → Branch: main, folder: / (root) → Save.
Your live URL appears at the top of that page within a minute or two, in the form https://YOUR-USERNAME.github.io/YOUR-REPO-NAME/.
Known limitations
Tax slabs, GST thresholds, and scheme eligibility figures are simplified, indicative estimates for demo purposes — not verified against the latest official rates, and not a substitute for advice from a CA or the official GST/Udyam helpdesks.
Gemini's free tier has real rate limits; the app retries automatically on transient 503/429 responses, but sustained heavy testing right before a demo can still hit a daily cap — generate your key a day or two ahead of time.
No persistence, backend, or real Udyam/GST API integration — this is a single-session MVP, not a production tool.
Roadmap
Real-time GST/Udyam API integration instead of the static rule table
Regional language support
Voice input for lower-literacy users


