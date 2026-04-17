# Color Palette & Brand Style — Raccoon Gang

**This is the single source of truth for all colors and brand-specific styles.** To customize diagrams for your own brand, edit this file — everything else in the skill is universal.

Source: [raccoongang.com](https://raccoongang.com/) brand palette.

---

## Brand Swatches (reference)

| Role | Hex |
|------|-----|
| Primary green | `#559479` |
| Deep green | `#37604f` |
| Lime accent | `#72bb25` |
| Light lime | `#abe271` |
| Warm orange | `#f89d6a` |
| Cream (canvas) | `#f9f3ed` |
| Warm beige | `#e8e1de` |
| Ink | `#323232` |
| Near-black | `#181a19` |
| Mid-grey | `#747474` |
| Alert red | `#dc3232` |
| Sky blue | `#5897fb` |
| Muted blue | `#778fcf` |
| Signal yellow | `#ffb900` |

---

## Shape Colors (Semantic)

Colors encode meaning, not decoration. Each semantic purpose has a fill/stroke pair.

| Semantic Purpose | Fill | Stroke |
|------------------|------|--------|
| Primary/Neutral | `#d0e6d7` | `#37604f` |
| Secondary | `#abe271` | `#37604f` |
| Tertiary | `#e8e1de` | `#323232` |
| Start/Trigger | `#fde0d1` | `#c85a1f` |
| End/Success | `#abe271` | `#37604f` |
| Warning/Reset | `#f89d6a` | `#c85a1f` |
| Decision | `#fff0b3` | `#b8860b` |
| AI/LLM | `#d7defa` | `#3a5293` |
| Inactive/Disabled | `#e8e1de` | `#747474` (use dashed stroke) |
| Error | `#ffd5d5` | `#dc3232` |

**Rule**: Always pair a darker stroke with a lighter fill for contrast.

---

## Text Colors (Hierarchy)

Use color on free-floating text to create visual hierarchy without containers.

| Level | Color | Use For |
|-------|-------|---------|
| Title | `#37604f` | Section headings, major labels |
| Subtitle | `#559479` | Subheadings, secondary labels |
| Body/Detail | `#747474` | Descriptions, annotations, metadata |
| On light fills | `#323232` | Text inside light-colored shapes |
| On dark fills | `#f9f3ed` | Text inside dark-colored shapes |

---

## Evidence Artifact Colors

Used for code snippets, data examples, and other concrete evidence inside technical diagrams.

| Artifact | Background | Text Color |
|----------|-----------|------------|
| Code snippet | `#181a19` | Syntax-colored (language-appropriate) |
| JSON/data example | `#181a19` | `#72bb25` (lime) |

---

## Default Stroke & Line Colors

| Element | Color |
|---------|-------|
| Arrows | Use the stroke color of the source element's semantic purpose |
| Structural lines (dividers, trees, timelines) | Deep green (`#37604f`) or Mid-grey (`#747474`) |
| Marker dots (fill + stroke) | Primary green (`#559479`) |

---

## Background

| Property | Value |
|----------|-------|
| Canvas background | `#f9f3ed` |

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
