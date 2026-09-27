# Card Scan Carousel

An animated, Evervault.com-inspired card showcase built with Next.js — a 3D "card scanner" hero where cards stream across the screen with physics-based dragging, particle effects (THREE.js), and a scan line, plus reusable infinite/sliding carousel components with pause-on-hover.

> Inspired by [evervault.com](https://evervault.com); originally generated with [v0.app](https://v0.app), then refined and documented.

## Features

- 🃏 **Card scanner hero** — cards stream across a scan line with velocity, friction, and direction physics
- 🖱️ **Draggable card stream** — grab the stream and fling it with mouse-velocity-based momentum
- ✨ **THREE.js particle effects** layered behind the scanner
- 🎞️ **InfiniteCarousel** — seamless looping carousel, configurable speed/direction/gap, pause-on-hover
- 🖼️ **SlidingCarousel** + **CarouselSlide** — additional sliding carousel primitives
- 🌙 **Dark / light mode** toggle (next-themes)
- 🖼️ Local card artwork (`public/cards/`) plus remote image support
- 📦 Typed, reusable components ready to drop into other projects

## Tech Stack

- [Next.js](https://nextjs.org/) 15 (App Router, static export)
- [React](https://react.dev/) 19
- [TypeScript](https://www.typescriptlang.org/)
- [THREE.js](https://threejs.org/) for particle effects
- [Tailwind CSS](https://tailwindcss.com/) 3 + `tailwindcss-animate`
- [Lucide React](https://lucide.dev/) icons
- [next-themes](https://github.com/pacocoursey/next-themes) for theming

## Quick Start

### Prerequisites

- Node.js 18+ and npm

### Install & run

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Build (static export)

```bash
npm run build
```

The fully static site is emitted to `out/` and can be hosted on any static host (Cloudflare Pages, GitHub Pages, Netlify, Vercel).

## Project Structure

```
card-scan-carousel/
├── app/
│   ├── page.tsx                      # Entry — renders CardScanner
│   ├── layout.tsx                    # Root layout + theme provider
│   └── globals.css
├── components/
│   ├── card-scanner/
│   │   └── card-scanner.tsx          # Scanner hero: physics stream + particles
│   ├── carousel/
│   │   ├── infinite-carousel.tsx     # Seamless looping carousel
│   │   ├── sliding-carousel.tsx      # Sliding carousel primitive
│   │   └── carousel-slide.tsx        # Slide wrapper
│   └── theme-provider.tsx
├── lib/
│   └── utils.ts                      # cn() class-name helper
├── public/
│   └── cards/                        # Local card artwork (v0card1–4.png)
├── next.config.mjs                   # output: 'export', unoptimized images
└── tailwind.config.ts
```

## Usage

Drop the carousel into any page:

```tsx
import { InfiniteCarousel } from "@/components/carousel/infinite-carousel"
import { CarouselSlide } from "@/components/carousel/carousel-slide"

<InfiniteCarousel speed={50} direction="left" pauseOnHover gap={16}>
  {[<CarouselSlide key="1">…</CarouselSlide>]}
</InfiniteCarousel>
```

## Environment Variables

None required — all rendering is client-side.

## Deployment

The app is a **static export** (`output: 'export'`), so it deploys to any static host:

- **Cloudflare Pages** — point the build output at `out/`
- **GitHub Pages / Netlify / Vercel** — same, serve the `out/` directory

No server, no API routes, no secrets needed.

## Notes

- The scanner effect is canvas/WebGL-based; it needs a real browser with JS enabled (no SSR interactivity).
- Lint and TypeScript errors are ignored during builds (v0 default).

---

Built by Girish Lade · [ladestack.in](https://ladestack.in)
