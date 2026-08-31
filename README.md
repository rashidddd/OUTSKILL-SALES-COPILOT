# Outskill Dispatch — AI Sales Copilot

A single-file, browser-only tool that turns one lead into a full set of outreach drafts — call opening, discovery questions, pitch, email, WhatsApp, LinkedIn message, and objection handling — powered by the Gemini API.

No backend, no build step, no install. Open the HTML file and go.

## Features

- **Two dispatch modes**
  - **Basic** — call opening, one email draft, objection handling. One short request, built to stretch a free-tier quota across many leads.
  - **Full Kit** — everything: profile summary, fit score, call opening, discovery questions, pitch, email, WhatsApp, LinkedIn message, and objection handling.
- **Paste-from-LinkedIn import** — paste a profile's headline, About section, or experience, and it auto-extracts Name, Role, Company, Country, and a sales-relevant notes summary into the form.
- **Structured, schema-enforced output** — every Gemini response is constrained to a strict JSON schema, so Full Kit's longer, multi-field responses come back reliably instead of getting cut off mid-object.
- **Per-card copy, plus copy-all** — copy a single draft or the entire dispatch in one click.
- **Bring your own key** — your Gemini API key lives only in your browser's local storage. Nothing is sent anywhere but Google's API.

## Getting started

1. Get a free Gemini API key at [aistudio.google.com/apikey](https://aistudio.google.com/apikey).
2. Open `index.html` in any modern browser (double-click it, or serve it with any static file server).
3. Expand **API configuration**, paste your key, and click **save**.
4. Pick a model (Gemini 2.5 Flash is the recommended free-tier default).

## Usage

1. **(Optional) Paste from LinkedIn** — under Lead Intake, expand "Paste from LinkedIn," paste the profile text, and click **Extract & fill**. Review the auto-filled fields before continuing.
2. **Fill in the lead** — name, role, company, country, notes/pain points, and what you're pitching. At minimum, provide a name or some notes.
3. **Choose a dispatch mode** — Basic for quick, quota-friendly drafts; Full Kit for the complete set.
4. **Click Generate dispatch** — outreach drafts appear as transmission cards below, ready to copy individually or all at once.

## Tech stack

- Plain HTML/CSS/JavaScript — no framework, no bundler.
- [Google Gemini API](https://ai.google.dev/gemini-api/docs) (`generateContent` endpoint) with `responseSchema` for structured JSON output.
- Fonts: Space Grotesk, Inter, JetBrains Mono (Google Fonts).

## Privacy & data

- Your API key is stored only in your browser's `localStorage`, under the key `outskill_gemini_key`. It is never hard-coded and never sent to any server other than Google's Gemini API.
- Lead data you type or paste stays in your browser for the duration of the session — it isn't persisted or transmitted anywhere except as part of the prompt sent to Gemini.

## Notes on free-tier usage

- Basic mode issues one short request per lead (~700 output tokens).
- Full Kit issues one longer request per lead (~3072 output tokens) to comfortably fit all nine fields without truncation.
- If you hit a `429` rate-limit error, you've used up your current free-tier quota — wait a bit, switch to Basic mode, or use a lighter model.

## License

Add a license of your choice here (e.g. MIT) before publishing.
