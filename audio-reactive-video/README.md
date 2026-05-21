# Audio Reactive Video

This folder contains the SeeSound web app and optional macOS companion.

## Parts

- [`web/`](./web): the Vite + TypeScript browser app.
- [`macos-companion/`](./macos-companion): optional macOS menu bar companion for system audio capture.
- [`docs/`](./docs): implementation and deployment notes.

## Web App

```bash
cd audio-reactive-video/web
npm install
npm run dev
```

Useful commands:

```bash
npm run check
npm run build
npm run preview
```

`npm run check` validates shader files and runs TypeScript checking.

## Audio Sources

`File` is the lowest-latency and most reliable path. It keeps playback, analysis, and rendering inside the browser page.

`Browser Tab` uses browser screen/tab sharing. Choose a tab and enable audio sharing when prompted.

`Desktop App` uses the macOS companion when system output is needed.

## Visual Modes

- `Spectral`: the main resonant field renderer, with WebGPU preferred and legacy fallback support.
- `Crystal`: a dedicated WebGPU harmonic membrane renderer.

When WebGPU is unavailable, the dedicated `Crystal` renderer may not display; `Spectral` has the broader fallback path.
