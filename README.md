# Countdown Studio

A browser-based countdown animation generator for PowerPoint.

**Live app:** [plastocyanin.org/countdown-studio](https://plastocyanin.org/countdown-studio/) · **Source:** this repository

Author: **hyphoon** · Contact: wuhaifeng@ustc.edu.cn

## Features

- Four countdown styles: flip cards, circular timer, minimal digits, and linear progress.
- Nine preset palettes plus manual text, progress, card, and background colors.
- Live preview with Start, Pause, Continue, and Reset controls.
- Content-aware trimming that detects visible pixels and removes transparent margins.
- Adjustable padding around the cropped content.
- Transparent GIF export for overlaying the animation on a PowerPoint slide.
- Offline frame-by-frame H.264 MP4 encoding with WebCodecs and MP4 muxing; export does not wait for wall-clock playback.
- Browser-side rendering. Countdown frames are generated locally and are not uploaded to a server.

## Use

Open the live app in a current Chrome or Edge browser. Set the duration, style, palette, and background. Keep **automatic content trimming** enabled to export a tightly cropped component rather than a full-slide canvas. Adjust the padding slider to control the empty margin around the visible animation.

Choose **transparent** background for overlays. GIF supports binary transparency only, so antialiased edges may look slightly harder than in the preview. MP4/H.264 does not carry an alpha channel; MP4 exports use the selected background color.

## Export limits and compatibility

- MP4 uses the browser's WebCodecs H.264 encoder and the `mp4-muxer` module loaded from jsDelivr. Use an up-to-date Chrome or Edge over HTTPS.
- MP4 export is offline frame rendering and encoding, not a real-time screen recording. Duration is limited to 10 minutes in the current UI.
- GIF uses `gif.js` loaded from jsDelivr and is limited to 180 seconds. Long countdowns are better exported as MP4.
- GIF and MP4 exports require an internet connection on first use to load their encoder libraries.
- Actual encoding speed and supported resolutions depend on the browser, hardware encoder, and device memory.
- This project currently has no license file. Public visibility alone does not grant general redistribution or commercial-use rights.

## Development

The app is a single self-contained `index.html` with no build step. Open it in a browser or serve the repository directory over HTTP. GitHub Actions publishes the root HTML to GitHub Pages after pushes to `main`.

## Project records

- [Current project context](docs/PROJECT_CONTEXT.md)
- [UI and export rules](docs/STYLE_GUIDE.md)
