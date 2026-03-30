# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static HTML/CSS/JS website for a family camper road trip through France (August 21-31, 2025), planned for 4 families with children. No build process, no dependencies — open `index.html` directly in a browser.

## Development

No build, test, or lint commands. To preview:
- Open `index.html` directly in a browser, or
- Run a local static server: `python -m http.server 8000`

## Architecture

### File Structure

The project has three iterations:

| Version | HTML | KML (Google My Maps) | Excel (logistics) |
|---------|------|----------------------|-------------------|
| v1 | `v1/` | `v1/francia_camper_mymaps.kml` | `v1/itinerario_francia_camper_v1.xlsx` |
| v2 | `v2/index.html` | `v2/francia_camper_mymaps_v2.kml` | `v2/itinerario_francia_camper_v2.xlsx` |
| **v3 (current)** | **`index.html`** (root) | `v3/francia_finale_mymaps.kml` | `v3/itinerario_finale.xlsx` |

**`index.html`** at the root is the canonical final version.

### HTML Structure

All content is in a single `index.html` with inline CSS and JS. Key sections, in order:

1. **Hero** — trip title, dates, stats
2. **Disney Banner** — urgent booking callout
3. **Route Strip** — horizontally scrollable stop list
4. **Days Grid** — 11-row accordion; each row expands via `toggle(i)`
5. **Booking Cards** — critical reservations with urgency levels
6. **Tips Grid** — logistics advice
7. **Return Box** — return journey warnings

### JavaScript Pattern

All day content is stored in a `days[]` array (one object per day). A loop generates the accordion HTML dynamically. `toggle(i)` shows/hides the expanded detail panel.

### CSS Design Tokens

```css
--cream: #F5F0E8   /* page background */
--sand:  #E8DCC8
--ink:   #1A1612   /* body text */
--muted: #6B6256
--accent: #C4531A  /* CTAs */
--gold:  #B8922A   /* highlights */
/* Day zone colors: --blue, --green, --pink */
```

### KML Files

Used with Google My Maps for shared navigation among all families. Contains camping spots, attractions, and the driving route. Edit with any KML-compatible tool or a text editor (it's XML).
