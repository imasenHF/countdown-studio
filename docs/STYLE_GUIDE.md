# Countdown Studio — UI and Export Rules

## Layout
- On desktop, organize all editor functions in four compact cards arranged as a two-column grid: timer/style, palettes, trimming/output, and preview/export controls. Show all tools without requiring a long vertical sidebar.
- Give the cropped-component preview a restrained width and height. Keep it centered and display the actual cropped output aspect ratio; the output file's pixel dimensions must remain independent of the on-page preview size.
- On narrower screens, stack the preview above the settings, with settings in two columns where space allows and one column on phones.
- The upper-left site identity reuses the exact shared Workshop brand structure: official image `/assets/images/imasen_phi_logo/imasen-phi-64.png` at 48 × 48 px, Georgia / serif wordmark `plastocyanin.`, with the brand `o` and final period colored `#b68c37`, and `Countdown Studio` centered beneath. The mark and wordmark link to the main site; the project name links to this tool. Use the shared wordmark font sizes, weights, line heights, and hover/focus behavior rather than approximating the brand independently.
- All former dropdown controls (animation style, export background, export resolution, and MP4 frame rate) are represented by compact button groups styled like the palette cards. Each group has one active button with `aria-pressed`; changes synchronize with the underlying setting used by rendering and export. There should be no visible native select menus.
- The checkerboard denotes transparency in the preview only; it must never be included in exported files.

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
