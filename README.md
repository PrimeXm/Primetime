# Alumni Trails Globe

Interactive 3D alumni connectivity globe built with plain HTML/CSS/JS and Three.js.

## Overview
A single `index.html` renders a glowing point-cloud globe, great‑circle trail animations, and UI panels that appear after an intro camera fly‑in. Capitals display alumni counts; trails animate in a typewriter cycle (draw / hold / fade). A top companies list aggregates employer frequency until a city is selected.

## Features
- Three.js r128 scene (no build tools, no frameworks)
- OrbitControls auto-rotate + eased intro zoom / recenter
- Point-cloud globe + country border GeoJSON lines
- Root university marker with breathing glow
- Capital markers with layered glow + CSS2D labels
- Label declutter (screen-space overlap suppression)
- Multi-layer additive glow trails (no bloom post-processing)
- Typewriter trail lifecycle (drawRange + per-phase opacity)
- Dynamic trail head gradient via vertex colors
- Starfield background
- Panels & header 3D fly-in (translateZ, blur, scale, rotate)
- Responsive layout (media queries)
- Top companies aggregation + revert when clicking empty space
- Google Fonts (Montserrat / Poppins) theming

## Data
`capitalsData` array embedded in the script: `{ city, country, lat, lon, alumni, companies[] }`. Root node (Shoolini University) added separately.

## How It Works
1. Init builds scene, camera, renderers (WebGL + CSS2D), controls.
2. Stars, globe points, borders, capitals, root marker are added.
3. Trails auto-generated from root to each capital (spherical interpolation).
4. Animation loop updates:
   - Camera intro zoom
   - Trail phase + head segment buffers
   - Marker hover selection + label visibility
   - Root breathing pulse
   - Label declutter pass
5. After zoom phase, body class triggers UI/header/credit reveal.

## Running
Just open `index.html` in a modern desktop browser (Chrome / Edge / Firefox). No build or server required. If local file geo fetch is blocked by CORS, serve with a simple static server (optional).

## Customization
Edit constants in the script:
- `globeRadius`
- Trail timing (`cycleDuration`, `writeFrac`, `holdFrac`, `fadeFrac`)
- Colors (`TRAIL_BASE_COLOR`, `TRAIL_TIP_COLOR`)
Add / modify entries in `capitalsData` to expand coverage.

## Performance Notes
Trail heads use a fixed small buffer updated per frame. Additive line materials disable depthWrite to reduce overdraw artifacts. Declutter limits DOM label overlap.

## Credits
Designed by MJS.

## License
All Rights Reserved.

Copyright (c) 2025 MJS.

This project and its source, assets, design, and animations are proprietary. No part of this work may be used, copied, modified, published, distributed, sublicensed, or hosted (publicly or privately) without prior written permission from MJS. Forking or derivative visualizations are not permitted. For collaboration or licensing inquiries, obtain explicit approval first.

Unauthorized use is expressly prohibited.
