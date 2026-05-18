# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Static marketing website for **LeonAI**, an indie mobile game studio. The site showcases the *Puzzle Competition* Android app. There is no build system, no package manager, and no JavaScript framework — everything is plain HTML, CSS, and JS written inline in each file.

## Testing locally

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

Alternatively, use the VS Code **Live Server** extension (right-click any `.html` → Open with Live Server). Opening via `file://` works for layout but the browser may block the `<video>` assets.

## Architecture

All CSS and JS live inline inside `<style>` and `<script>` tags within each HTML file — there are no external `.css` or `.js` files.

### Design system

Every page uses the same CSS custom properties (defined in `:root`):

| Variable | Purpose |
|---|---|
| `--bg` / `--surface` / `--surface2` | Dark navy backgrounds |
| `--text` / `--muted` | Primary and secondary text |
| `--accent` / `--accent2` | Blue CTA colours |
| `--gold`, `--blue`, `--cyan`, `--green`, `--red` | Per-game and per-mode accent colours |

Fonts: **Inter** (body) and **Fredoka** (headings/display), loaded from Google Fonts.

### Game cards in `puzzle-competition.html`

Games are displayed in a 3-column CSS grid (`.games-split`), collapsing to 2 columns below 900px. Each card is a `.game-panel` with a colour-modifier class (`tap`, `block`, `fire`). That class drives the top border colour, subtitle colour, and arrow colour via scoped CSS rules. The back face of the card contains a `<video>` that plays on flip.

**Adding a new game** requires:
1. Adding CSS rules for the new modifier class (border, `.game-sub` color, `.spec-list li::before` color).
2. Adding the HTML card with `onclick="flipGame(this)"` once a video is available; omit the onclick and back face while video is pending.
3. Updating the section label ("Three Games" → "Four Games") and the hero tagline.

The construction placeholder (slot 4) uses `.game-face-front.construction` — no onclick, no back face.

### Pages

| File | Purpose |
|---|---|
| `index.html` | Studio home — about section + game catalogue |
| `puzzle-competition.html` | App landing page — game cards, modes, leaderboard preview |
| `puzzle-competition-privacy-policy.html` | Privacy policy |
| `google09796cf65f7c4c90.html` | Google Search Console verification (do not edit) |

### Assets

```
assets/Puzzle Competition/
  game_icons/       # PNG icons per game (used in cards and og tags)
  game_recordings/  # MP4 gameplay videos (used in card back faces)
  gems/             # PNG gem images shown in the hero row
  game_construction.png  # placeholder image for unreleased games
```
