# LeonAI — Puzzle Competition

Static website for the **Puzzle Competition** app — includes the landing page, privacy policy, and game showcase.

## Testing Locally

This is a plain static site (HTML + CSS + JS). No build step needed.

### Option A — Python (nothing to install)

```bash
python3 -m http.server 8000
```

Then open [http://localhost:8000](http://localhost:8000) in your browser.

### Option B — VS Code Live Server

1. Install the [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension.
2. Right-click any `.html` file in the Explorer → **Open with Live Server**.

> **Note:** Opening files directly via `file://` works for basic layout checks, but the browser may block video assets (`<video>` tags). Use one of the options above to test gameplay previews correctly.

## Pages

| File | URL |
|---|---|
| `index.html` | `/` — LeonAI home |
| `puzzle-competition.html` | `/puzzle-competition.html` — App landing page |
| `puzzle-competition-privacy-policy.html` | `/puzzle-competition-privacy-policy.html` — Privacy policy |
