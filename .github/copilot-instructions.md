<!-- Copilot instructions for the coaching_site repo -->
# Copilot / AI agent instructions

Purpose: make small, safe, and context-aware edits to this single-page static site.

- **Project type:** simple static website (no build tool). Key files: `index.html`, `CNAME`, `README.md`.
- **Hosting:** intended for GitHub Pages; `CNAME` controls the custom domain. Preserve it unless domain changes are explicitly requested.

Quick architecture notes
- Single-page HTML located at `index.html`. Styles are inline in the file (no separate CSS files). Content, SEO meta tags, structured data (JSON-LD) and contact info are embedded in `index.html`.
- `index.html` uses Hebrew (`lang="he"`, `dir="rtl"`) and Google Fonts. Keep RTL layout and font links when editing content.

Editing rules for agents
- Make minimal, atomic edits: prefer changing text, meta tags, or small markup fragments over large refactors.
- Do NOT remove or rename `CNAME`. If updating domain placeholders (currently `https://www.example.com/`), update canonical and all JSON-LD URLs consistently.
- When updating contact details in `index.html`, keep formats intact (telephone, email, structured data). Example locations: the JSON-LD `telephone` and `email` fields near the top of `index.html`.

Local preview & quick checks
- Preview by opening `index.html` in a browser or serve a local HTTP server from the repo root:
```powershell
python -m http.server 8000
# then browse to http://localhost:8000/
```
- After edits, validate that page renders RTL correctly and that structured data remains valid (use Google's Rich Results Test externally).

Commit & PR guidance
- Use small commits. Example commit message: `fix(site): update meta description and contact info`.
- PR checklist for agents:
  - Preview locally and confirm visual/RTL correctness.
  - Search `index.html` for duplicate placeholders (e.g., `example.com`) and update all occurrences.
  - Do not change file layout (moving inline CSS into external files) unless requested.

Examples of safe edits
- Update meta description: edit the `<meta name="description" ...>` tag in `index.html`.
- Change headline text: edit the `<h1>` inside the hero section.
- Add a new FAQ entry: append another object to the `FAQPage` JSON-LD `mainEntity` array, preserving the JSON structure.

What agents should not do
- Do not introduce build tools or new frameworks without explicit instruction.
- Avoid mass reformatting of `index.html` (preserve indentation/encodings).
- Don’t remove or change tracking/SEO structured-data fields unless asked.

If you need more context
- Check `README.md` for author / site purpose notes.
- Ask a human if a change affects the `CNAME` or external domain settings.

If unclear or incomplete, ask for guidance specifying which file and which fragment you plan to modify.
