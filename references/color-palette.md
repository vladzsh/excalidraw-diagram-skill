# Color Palette & Brand Style — Raccoon Gang

**This is the single source of truth for all colors and brand-specific styles.** To customize diagrams for your own brand, edit this file — everything else in the skill is universal.

Source: [raccoongang.com](https://raccoongang.com/) brand palette.

---

## Brand Swatches (the only colors allowed)

| Role | Hex |
|------|-----|
| Primary green | `#559479` |
| Warm orange | `#F89D6A` |
| Ink | `#323232` |
| Near-black | `#232323` |
| Cream (canvas + light text) | `#F9F3ED` |

No off-brand colors. No lime accents, no blues, no yellows, no derived tints. Differentiation comes from **fill vs. outline** and **stroke weight**, not from expanding the palette.

---

## Shape Colors (Semantic)

Four visual treatments. Each carries a distinct meaning.

| Semantic Purpose | Fill | Stroke | Text |
|------------------|------|--------|------|
| Hero / Primary (main components, central truth) | `#559479` | `#232323` | `#F9F3ED` |
| Start/Trigger / Alert / Audit | `#F89D6A` | `#323232` | `#323232` |
| Supporting / Derived (outlined, green-tied) | `transparent` | `#559479` | `#323232` |
| External / Neutral (outlined, ink) | `transparent` | `#323232` | `#323232` |

**Rule**: Hero shapes get filled primary green with cream text. Triggers and audit artifacts get filled warm orange. Everything else is outlined — transparent fill with either a green stroke (if conceptually tied to the primary flow) or an ink stroke (if external / neutral).

---

## Text Colors (Hierarchy)

| Level | Color | Use For |
|-------|-------|---------|
| Title | `#232323` | Section headings, major labels |
| Subtitle | `#559479` | Subheadings, secondary labels |
| On light fills / canvas | `#323232` | Default body text |
| On dark fills (primary green) | `#F9F3ED` | Text inside `#559479` shapes |

---

## Evidence Artifact Colors

Used for code snippets, data examples, and other concrete evidence inside technical diagrams.

| Artifact | Background | Text Color |
|----------|-----------|------------|
| Code snippet | `#232323` | `#F9F3ED` |
| JSON/data example | `#232323` | `#F9F3ED` |

---

## Default Stroke & Line Colors

| Element | Color |
|---------|-------|
| Arrows (all — regardless of flow type) | `#323232` |
| Structural lines, dividers, async boundaries | `#323232` |
| Hero element strokes | `#232323` |
| Outlined shape strokes | `#559479` or `#323232` (per semantic) |

**Rule**: Arrows are always ink `#323232`. Do not color-code arrows by flow type — semantic meaning comes from the shapes they connect, not the arrow color.

---

## Background

| Property | Value |
|----------|-------|
| Canvas background | `#F9F3ED` |

---

## Brand Logo (required on every diagram)

Every diagram MUST include the Raccoon Gang logo as a watermark in the **bottom-right corner**. No exceptions — this is the brand signature.

**Source file:** `references/brand-logo.svg` (local copy of [logo-simple.svg](https://y7b6t9n6.delivery.rocketcdn.me/wp-content/themes/generatepress/assets/images/logo-simple.svg)). Native size 235×90, aspect ratio ~2.61:1.

**Placement & size:**
- Position: bottom-right, 40–60px inner padding from the diagram's max x/y bounds.
- Default render size: 120×46 (small) or 160×61 (standard). Never wider than 200px — it's a signature, not a headline.
- Do not rotate, recolor, or crop.

### How to embed in Excalidraw JSON

Excalidraw image elements reference an entry in the top-level `files` object via `fileId`. Steps:

1. **Generate the data URL** from the local SVG:
   ```bash
   printf 'data:image/svg+xml;base64,%s' "$(base64 -i .claude/skills/excalidraw-diagram/references/brand-logo.svg | tr -d '\n')"
   ```

2. **Add the image element** to `elements`:
   ```json
   {
     "type": "image",
     "id": "brand_logo",
     "x": 1700,
     "y": 900,
     "width": 160,
     "height": 61,
     "angle": 0,
     "strokeColor": "transparent",
     "backgroundColor": "transparent",
     "fillStyle": "solid",
     "strokeWidth": 1,
     "strokeStyle": "solid",
     "roughness": 0,
     "opacity": 100,
     "groupIds": [],
     "frameId": null,
     "roundness": null,
     "seed": 900001,
     "version": 1,
     "versionNonce": 900002,
     "isDeleted": false,
     "boundElements": null,
     "updated": 1,
     "link": null,
     "locked": false,
     "status": "saved",
     "fileId": "rg_brand_logo",
     "scale": [1, 1]
   }
   ```

3. **Add the file entry** to the top-level `files` object:
   ```json
   "files": {
     "rg_brand_logo": {
       "mimeType": "image/svg+xml",
       "id": "rg_brand_logo",
       "dataURL": "data:image/svg+xml;base64,<paste base64 from step 1>",
       "created": 1
     }
   }
   ```

The `fileId` on the image element must match the key in `files`. Reuse `"rg_brand_logo"` across diagrams for consistency.
