# SmartPay — product & UX case study

A portfolio case study for the SmartPay prototype in this repository.

| File | Format | Use it for |
|---|---|---|
| [`SmartPay-UX-Case-Study.md`](SmartPay-UX-Case-Study.md) | Markdown | Reading on GitHub, or as the source for a portfolio site |
| [`SmartPay-UX-Case-Study.docx`](SmartPay-UX-Case-Study.docx) | Word, 24 pages | Editing, printing, attaching to an application |
| [`SmartPay-UX-Case-Study.pdf`](SmartPay-UX-Case-Study.pdf) | PDF, 24 pages | Sending or uploading without layout risk |
| [`assets/`](assets) | 27 PNGs | Dropping individual screens into a deck or portfolio page |

## What is in the assets folder

| Prefix | Count | What it is |
|---|---|---|
| `flow-*` | 2 | User flow for the send journey including the offline branch, and the information architecture |
| `wireframe-*` | 3 | Lo-fi wireframes: core send flow, offline branch, web |
| `mobile-*` | 19 | High-fidelity mobile screens, captured from the working prototype |
| `web-*` | 3 | High-fidelity web screens: personal dashboard, send, merchant console |

The mobile screens are real captures of `index.html` at the repository root, driven through each
state with Playwright. They are not mockups, so they stay accurate as the prototype changes.

## Before you publish this

The product sections are verifiable against the prototype. The **research findings and impact
figures are a stated model, not measured results** — every assumption is listed in the Impact model
section of the case study. Replace them with your own study and telemetry data before presenting
this as your own work history.

## Regenerating the visuals

The capture scripts live outside the repository. To rebuild the mobile screens, drive `index.html`
with Playwright, setting `S.screen` and calling `render()` for each state, then screenshot the
`.stage-phone` element at a 440×900 viewport and a device scale factor of 2.
