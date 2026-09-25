# Portolan — AI-ready proposals (POC)

Drop a proposal (.pptx or .pdf). Portolan shows where a client's AI assistant will misread it, lets you confirm or edit an explicit statement for each case, and exports an AI-ready package (Markdown + JSON) to send alongside the PDF.

- **100% in the browser.** The file is never uploaded, and no AI model or API key is involved.
- **Deterministic.** Rules read the slide structure (positions, shapes, tables, connectors, charts). The same deck always gives the same result.

## What it detects

| Rule | How |
|---|---|
| Visual timeline | Gantt grids (week or month headers) combined with bars, milestones and coloured cells, turned into dated items |
| Diagram, no text | Chevron sequences, grouped boxes, and connectors between shapes |
| Complex table | Matrix-like tables, linearised row by row |
| Numbers in a chart | Chart series read from the embedded chart XML |
| Ambiguous reading order | Columns that an extractor reads right-to-left |
| Placeholder left in | `XXX`, `xxxx`, `lorem ipsum`… plus the real amounts found elsewhere in the deck |
| Acronyms & jargon | Acronyms never defined in the deck, with a built-in glossary |
| Text in image | Large pictures without alt text (PPTX), pages dominated by images (PDF) |

A PPTX gives the richest reading (structural previews). A PDF gives real page previews but fewer rules.

## Run / deploy

Static site, no build step: `index.html` and `vendor/` (JSZip, pdf.js).

- **Locally:** double-click `index.html`.
- **GitHub Pages:** push `index.html`, `vendor/` and this README, then go to Settings → Pages → Deploy from branch (`main`, `/root`).

`.gitignore` excludes `*.pptx`, `*.pdf` and `*.zip`, so client material never gets pushed.
