# FakeTrace — Fake Profile Detector

A dark-themed, single-page web application for detecting fake/reused profile images using reverse image search simulation.

## How to Use

1. Open `index.html` in any modern browser — no server required.
2. Upload or drag-and-drop a profile image (JPG, PNG, WEBP, GIF, max 10MB).
3. Click **Run Fake Profile Analysis** to start the scan.
4. Review the risk score, source breakdown, and AI findings.

## Features

- Drag & drop image upload with live preview
- Animated multi-engine scanning progress (TinEye, Google Vision, Bing, AI Engine)
- Risk score meter: Low / Medium / High (0–100)
- Source breakdown by platform
- Per-finding analysis with color-coded warnings
- Fully responsive, no dependencies, no server needed

## To Connect Real APIs

Replace the simulated scan logic in `startScan()` with a fetch call to your backend:

```js
const formData = new FormData();
formData.append('image', fileInput.files[0]);
const res = await fetch('/api/scan', { method: 'POST', body: formData });
const data = await res.json();
showResults(data); // pass { tineye, google, bing } counts
```

Your backend should call:
- **TinEye API** — https://services.tineye.com/developers/tineyeapi
- **Google Cloud Vision API** — Web Detection feature
- **Bing Visual Search API** — Microsoft Azure Cognitive Services

## Stack

- Pure HTML5 / CSS3 / Vanilla JS
- Google Fonts: Syne, DM Sans, DM Mono
- No frameworks, no build step
