# Tender Package Builder

AI DevFest 2026 Vibe Coding Contest — frontend-only Tender Document Package Builder.
**URL:** https://tuhi567.github.io/devfest-naima_rahman_tuhi/

## Participant

**Name:** Naima Rahman Tuhi
**Registration number:** 242-15-567

## Project Overview

Tender Package Builder is a browser-based application that helps office staff prepare a complete tender document package from a set of PDF files.

The application reads the tender requirements, lets the user upload and match PDF documents, checks document status and expiry dates, detects duplicate files, and generates one correctly ordered PDF package ready for submission.

All document processing is performed in the browser. No participant-controlled backend, database, or online storage service is required.

## Main Features

- Load and validate `requirements.json`
- Display tender ID, title, procuring entity, bidder name, and submission deadline
- Display required documents in the specified order
- English and Bangla user interface with a language switch
- Upload multiple PDF files at once
- Enforce the 30-file and 50 MB total upload limits
- Validate that uploaded files are PDFs
- Count PDF pages in the browser
- Remove uploaded files when necessary
- SHA-256 exact duplicate-content detection, including files with different names
- Prevent duplicate files from being matched to different requirements
- One-to-one manual document matching
- Filename-based automatic match suggestions
- Enter and validate expiry dates for documents that require expiry checking
- Validate expiry dates against the tender submission deadline
- Show the required document statuses:
  - `OK`
  - `Missing`
  - `Expiry date needed`
  - `Expired`
  - `Not provided`
- Keep package generation blocked while a required blocking problem remains
- Generate the final package in the required document order
- Generate an English cover page with tender and package information
- Add an optional index page showing where documents start
- Add `Tender ID | Page X of Y` footer to every page of the generated package
- Download the final package as `<tender_id>_Package.pdf`
- Export the document checklist as CSV
- Save and reopen project work using browser IndexedDB storage
- Upload a PNG seal/signature and place it on selected pages
- Safely report invalid or problematic PDF files instead of crashing
- Work as a static frontend without a custom backend

## Bonus Features Implemented

The project also implements several optional features from the problem statement:

- Index page after the cover
- PNG seal/signature placement
- CSV checklist export
- Browser-local save and reopen using IndexedDB
- Bangla/English interface
- Filename-based auto-match suggestions
- Handling of damaged or password-protected PDFs with clear error messages

## How to Run Locally

### Option 1 — Open directly

Open `index.html` in a modern Google Chrome browser.

### Option 2 — Use a local static server

From the project directory, run any simple static web server. For example, with Python:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

The application does not require a backend server or database.

## How to Use

1. Open the application.
2. Load the provided `requirements.json` file.
3. Review the tender details and required documents.
4. Upload the PDF documents.
5. Review page counts and duplicate-file warnings.
6. Match each document to the appropriate requirement.
7. Enter expiry dates where required.
8. Resolve every blocking status.
9. Optionally add a seal/signature and export the checklist.
10. Generate the final tender package.
11. Download `<tender_id>_Package.pdf`.

## Output Included in This Repository

The repository contains the sample output required for the problem statement:

```text
output/T-2026-0417_Package.pdf
```

A screenshot demonstrating the document-status interface is included at:

```text
screenshots/statuses.png
```

## Technologies Used

- HTML5
- CSS3
- JavaScript
- PDF.js for browser-side PDF reading and page counting
- pdf-lib for PDF merging and package generation
- IndexedDB for browser-local project storage
- Web Crypto API for SHA-256 duplicate detection
- Vercel-compatible static hosting

## AI Tools Used

- ChatGPT — used for AI-assisted planning, implementation, debugging, feature development, documentation, and testing guidance.

## Most Useful Prompt

> Build a frontend-only Tender Document Package Builder for the AI DevFest Vibe Coding problem. It must load requirements.json, accept up to 30 PDF files with a 50 MB total limit, count pages, detect exact duplicate files using SHA-256, support one-to-one document matching, validate expiry dates against the submission deadline, show the required document statuses, block generation when there are unresolved mandatory problems, generate one correctly ordered PDF with an English cover page and `Tender ID | Page X of Y` footer on every page, and provide a bilingual English/Bangla interface. Add the optional index, CSV checklist export, browser-local save/reopen, PNG seal/signature placement, filename-based auto-match, and safe PDF error handling where practical. Keep everything frontend-only and suitable for static HTTPS deployment.

## Deployment

The application is designed for public static HTTPS deployment using services such as Vercel, GitHub Pages, Netlify, or Cloudflare Pages.

**Live URL:** Add the final public HTTPS deployment URL here before submission.

## Known Limitations

- Bangla text rendering has not been embedded into the generated PDF cover/index in this static build; the application interface itself is bilingual.
- The optional in-app AI-help feature is not included because the main workflow is designed to work without an API key or backend service.
- PDF.js and pdf-lib are loaded from public CDNs, so PDF processing requires an internet connection when the libraries are not already cached by the browser.
- The application is intended for modern Google Chrome, as required by the competition problem statement.

## License

This project is released under the MIT License. See `LICENSE` for the complete license text.
