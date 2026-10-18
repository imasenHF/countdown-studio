# Countdown Studio — UI and Export Rules

## Layout
- Use a compact editor panel and a large preview surface. Keep controls readable on desktop and stack the editor below the preview on narrow screens.
- The checkerboard denotes transparency in the preview only; it must never be included in exported files.
- Keep the preview centered and display the actual cropped output aspect ratio.

## Content trimming
- The main output canvas is an internal rendering surface, not the final exported frame.
- Detect visible alpha pixels, then crop to their bounding rectangle with a user-controlled padding margin.
- The crop control must be described as trimming transparent space, not changing the slide aspect ratio.
- When trimming is disabled, retain the full 16:9 internal scene.
- MP4/GIF frames must keep consistent dimensions throughout a single export.

## Visual themes
- Preserve the nine existing presets and manual color inputs.
- A palette preset updates text, accent, card, background, and label/track colors together.
- Keep contrast sufficient for countdown numerals and labels.

## Export
- MP4 generation uses offline frame rendering with explicit timestamps; do not reintroduce real-time MediaRecorder capture for file export.
- Transparent GIF uses a single transparent color and therefore cannot preserve partial alpha. Avoid claiming perfect antialiasing.
- MP4/H.264 output is opaque; fill the cropped frame with the selected background color.
- Show progress and errors in the page; do not report export success before a file is produced.
