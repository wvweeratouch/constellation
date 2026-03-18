# Constellation

Multi-person pose-tracking constellation generator. Bodies become stars, connections span across people.

**Live demo**: https://wvweeratouch.github.io/constellation/
**Mirror**: https://wvweeratouch.github.io/constellation/mirror.html

## How it works

MediaPipe PoseLandmarker tracks up to 3 people via webcam. All visible landmarks are pooled as "stars" regardless of which person they belong to. Random subsets are selected and connected to nearest neighbors, forming constellations that hold briefly then fade.

Open `mirror.html` in a second browser tab or window (same device) for a fullscreen display via BroadcastChannel.

## Controls

| Control | Range | Default | Description |
|---------|-------|---------|-------------|
| Persons | 1-3 | 2 | Number of people to track |
| Hold | 0.5-5s | 2s | How long constellation stays solid |
| Fade | 0.3-2s | 0.8s | Fade-out duration |
| PtMin | 3-20 | 3 | Minimum points per constellation |
| PtMax | 3-20 | 10 | Maximum points per constellation |
| ConnMax | 1-5 | 3 | Max connections per point |
| ConnDist | 0.1-0.5 | 0.3 | Max distance for connections (normalized) |
| Color | — | #d4af37 | Constellation color |
| Trail | 0.01-0.3 | 0.15 | Background fade opacity |
| PoseT | 0.01-0.20 | 0.05 | Velocity dead zone threshold |

## Keyboard shortcuts

| Key | Action |
|-----|--------|
| Space | Pause / Play |
| S | SNAP (3-2-1 countdown, freeze, save dialog) |
| P | Toggle pose skeleton |
| Escape | Resume from SNAP freeze |

## Tech

- MediaPipe Tasks Vision PoseLandmarker v0.10.14 (ESM from jsDelivr CDN)
- Single HTML files, no build step
- BroadcastChannel for mirror sync at 30fps
