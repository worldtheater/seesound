# SeeSound

SeeSound is a browser-based audio visualizer that turns music and live audio into resonant geometry. It is inspired by Chladni figures, modal interference, and projected spatial forms.

Live app: [https://worldtheater.github.io/seesound/](https://worldtheater.github.io/seesound/)

The live link is served by GitHub Pages from the web app build.

## Features

The main application lives in [`audio-reactive-video/web`](./audio-reactive-video/web). It supports:

- Local audio file playback with realtime analysis.
- Browser tab audio capture through `getDisplayMedia`.
- Optional macOS desktop audio capture through the local companion app.
- Three visual modes:
  - `Spectral`: resonant field / nodal geometry.
  - `Crystal`: harmonic membrane renderer.
  - `Lattice`: projected spatial wireframe renderer.
- WebGPU rendering where available, with legacy canvas/WebGL fallback paths for the spectral renderer.

## Run Locally

```bash
cd audio-reactive-video/web
npm install
npm run dev
```

Then open the Vite URL, usually:

```text
http://localhost:5173
```

## macOS Desktop Audio

The web app can visualize browser files and shared browser-tab audio on its own. To use the `Desktop App` source, start the macOS companion in another terminal:

```bash
cd audio-reactive-video/macos-companion
swift run
```

The companion listens only on localhost:

- HTTP control/status: `127.0.0.1:43821`
- PCM WebSocket stream: `127.0.0.1:43822`

macOS may ask for Screen Recording permission before system audio can be captured.

## Publish To GitHub Pages

This repo includes a GitHub Actions workflow at [`.github/workflows/pages.yml`](./.github/workflows/pages.yml). On each configured publish branch, it builds `audio-reactive-video/web` and publishes the generated `dist` folder to GitHub Pages.

Manual build check:

```bash
cd audio-reactive-video/web
npm run build
```

## Project Docs

- [Web app notes](./audio-reactive-video/README.md)
- [Architecture overview](./audio-reactive-video/docs/architecture.md)
- [Render flow](./audio-reactive-video/docs/main_flow.md)
- [GitHub Pages deployment](./audio-reactive-video/docs/github_pages.md)
- [macOS companion](./audio-reactive-video/macos-companion/README.md)
