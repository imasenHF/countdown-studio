# Countdown Studio — Agent Instructions

## Read first
1. Read this file and [docs/PROJECT_CONTEXT.md](docs/PROJECT_CONTEXT.md).
2. Read [docs/STYLE_GUIDE.md](docs/STYLE_GUIDE.md) before changing UI, layout, palettes, trimming, or export behavior.
3. Inspect the latest `main` code before editing. The current app is a single self-contained `index.html`.

## Implementation constraints
- Preserve the compact PowerPoint-component use case. The default export should crop to visible content and retain only a user-adjustable transparent margin; do not confuse content trimming with changing slide aspect ratio.
- Reuse the official site mark at `/assets/images/imasen_phi_logo/imasen-phi-64.png` and mirror the shared Workshop brand markup and typography. Do not approximate the mark with text or a substitute icon.
- Render every option previously shown as a dropdown (animation style, export background, output resolution, and MP4 frame rate) as selectable buttons matching the palette cards. Keep option state, accessibility attributes, and rendering/export values synchronized.
- Keep rendering local in the browser. Do not add an upload endpoint, analytics, or account requirement.
- MP4 must use timestamped offline frame rendering and encoding, not MediaRecorder/captureStream real-time recording.
- Keep GIF transparency limitations explicit. MP4/H.264 has no alpha channel; use a solid background for MP4.
- External encoder libraries are loaded only when the corresponding export is requested. Document the network dependency.
- Update README and project context when behavior, limits, or dependencies change.
- Do not claim browser, export, or PowerPoint acceptance without actually testing it.

## Verification
- Check JavaScript syntax and the HTML DOM IDs after changes.
- Test crop boundaries for all four styles and several timer values.
- Test GIF transparency, MP4 output duration/dimensions, and playback in PowerPoint when a browser environment is available.
- A successful GitHub Pages build is deployment verification, not a substitute for interactive export tests.
