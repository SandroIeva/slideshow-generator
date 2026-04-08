# 🎞 Slideshow Generator

A minimalist, zero-dependency browser tool for building animated slideshows from images and exporting them as video files. No server, no install, no account — just open and use.

**[→ Live Demo]([https://sandro.ieva](https://slideshow-generator.sandroieva.com)**

---

## Features

### 📁 Image Management
- Drag & drop images directly onto the canvas or click to upload
- Supports **JPG, PNG, WebP, GIF**
- Reorder images by dragging thumbnails in the settings panel
- Remove individual images with one click
- Add more images at any time

### 🎬 Transitions
**2D Transitions**
- Fade
- Dissolve
- Slide (left, right, up, down)
- Zoom in / Zoom out
- Wipe (left, right)
- Cross zoom

**3D Transitions**
- Cube (left, right) — perspective cube rotation
- Flip (horizontal, vertical) — card-flip with shadow
- Door open — splits frame down the middle
- Page turn — paper curl effect with shadow gradient
- Swap push — outgoing slides off while incoming scales in

### ⚙️ Controls
- **Transition duration** — 0.2s to 4s
- **Stop time per image** — 0.5s to 10s
- **Easing curves** — Linear, Ease in, Ease out, Ease in-out, Cubic out, Quint out, Bounce, Spring

### 🖼 Canvas Options
- **Aspect ratios** — 16:9, 4:3, 1:1, 9:16, 3:4, 21:9
- **Image fit modes** — Cover, Contain, Stretch
- **Background color** — 5 presets + custom color picker

### 🔁 Playback
- Preview the slideshow directly in the browser
- Toggle play/stop with the round play button
- Choose 1–5 loops for preview
- Live progress bar at the bottom

### 📤 Export
- **WebM (VP9/VP8)** — fast real-time capture via `MediaRecorder`, works in all modern browsers
- **MP4 (H.264)** — frame-by-frame encoding via the [WebCodecs API](https://developer.mozilla.org/en-US/docs/Web/API/WebCodecs_API), Chrome/Edge 94+ only
- Choose 1–5 loops to export
- Live encoding progress bar + ring indicator on the export button
- Files download directly to your machine

### 📱 Responsive & Mobile
- Fully responsive canvas that adapts to any screen size
- Touch-friendly tap targets throughout
- Settings panel slides in from the left on all screen sizes

---

## Browser Support

| Feature | Chrome | Edge | Firefox | Safari |
|---|---|---|---|---|
| Preview | ✅ | ✅ | ✅ | ✅ |
| WebM export | ✅ | ✅ | ✅ | ⚠️ partial |
| MP4 export | ✅ 94+ | ✅ 94+ | ❌ | ❌ |

> MP4 export uses the WebCodecs `VideoEncoder` API which requires hardware H.264 encoding support. If unavailable, use WebM — it plays in Chrome, Firefox, and most modern video players.

---

## Getting Started

### Use online
Visit the [live demo](https://your-project.vercel.app) — no installation needed.

### Run locally
Just open `index.html` in Chrome or Edge:

```bash
git clone https://github.com/your-username/slideshow-generator
cd slideshow-generator
open index.html   # macOS
# or double-click index.html in your file explorer
```

No build step, no dependencies, no `npm install`.

### Deploy to Vercel
```bash
npm install -g vercel
vercel
```

Or connect the GitHub repo directly in the [Vercel dashboard](https://vercel.com/new).

---

## How It Works

The entire app is a single `index.html` file (~43 KB). Key technologies:

- **HTML5 Canvas** — all rendering, transitions and animations
- **Offscreen canvas cache** — each image is baked once per canvas size for smooth playback
- **MediaRecorder API** — real-time WebM capture from `canvas.captureStream()`
- **WebCodecs API** — offline frame-by-frame H.264 encoding for true MP4 output
- **Inline MP4 muxer** — hand-written ISO Base Media File Format box builder (no external library)
- **RequestAnimationFrame** — smooth 60fps animation loop with tab-visibility handling

---

## Project Structure

```
slideshow-generator/
├── index.html      # Complete app — HTML + CSS + JS in one file
├── README.md       # This file
└── vercel.json     # Vercel deployment config
```

---

## License

MIT — free to use, modify and distribute.
