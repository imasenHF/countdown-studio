# Countdown Studio — Project Context

Updated: 2026-10-18

## Purpose
Generate compact countdown animation assets for insertion as individual components on PowerPoint slides. The output is content-cropped; a full-slide 16:9 canvas is not required for the common workflow.

## Current implementation
- One self-contained `index.html`; static GitHub Pages deployment.
- Styles: flip cards with a progress bar, circular timer, minimal digits, and linear progress.
- Nine presets: Deep Sea Mint, Academic Blue/White, Charcoal Champagne, Violet Night, Forest Mint, Coral, Red/White, Electric Blue, and Minimal Gray/Blue.
- Custom text, progress, card, and background colors.
- Content-aware crop detects non-transparent pixels on a probe frame. The padding control adjusts transparent margin around the detected bounds.
- Preview is rendered from the cropped output so it approximates the exported component's dimensions.
- Desktop UI uses a compact two-column grid of tool cards and a smaller preview to keep all primary controls within the first viewport on common desktop resolutions; smaller screens stack the panels.
- Upper-left branding uses the exact shared Workshop brand markup, including the official 48 px `imasen-phi-64.png` symbol, Georgia wordmark, and gold `o` / terminal period; the `Countdown Studio` subtitle follows the same font sizing and alignment as the Workshop subtitle.
- Animation style, export background, resolution, and MP4 frame rate use palette-card-style button groups instead of visible dropdowns. The selected button and rendering/export settings remain synchronized.
- Footer uses the shared two-column copyright layout, displays the current year dynamically, names `hyphoon` as the public rights holder, and separates the copyright notice from the GitHub source link.
- GIF export uses `gif.js` and binary transparency; MP4 export uses WebCodecs and `mp4-muxer` for offline timestamped encoding.
- MP4 uses a solid background because common H.264 MP4 output does not preserve alpha.

## Constraints
- The project is browser-only and has no server-side rendering or file upload.
- GIF is capped at 180 seconds; MP4 is capped at 600 seconds.
- Encoder modules load from jsDelivr on demand.
- WebCodecs/H.264 availability depends on browser and device. Latest Chrome or Edge over HTTPS is recommended.
- Browser encoding performance, GIF edge appearance, MP4 decoding in PowerPoint, and all palette/style crop bounds still require interactive acceptance testing.

## Verification

- GitHub Actions validates the inline JavaScript syntax and checks that referenced DOM IDs exist before publishing.
- The deployment workflow performs an HTTP smoke test against the published URL; the latest run passed.
- Headless Chrome at 1440 × 900 verifies the official logo asset path, brand gold color, four button-based option groups, absence of visible native selects, option-to-setting synchronization, preview bounds, and that the editor fits in the first viewport.
- The main site's Jekyll build and deployment for the Workshop entry passed.
- Manual browser interaction, transparent GIF export, MP4 encoding on multiple devices, and playback in PowerPoint have not yet been tested.

## Deployment
- Source repository: https://github.com/imasenHF/countdown-studio
- GitHub Pages is deployed by `.github/workflows/pages.yml`.
- The main site exposes the project at https://plastocyanin.org/countdown-studio/ through the existing site path-routing arrangement. The Workshop entry and main-site records are maintained in https://github.com/imasenHF/imasenhf.github.io.
