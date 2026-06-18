# doc-Vault

A premium streaming discovery platform built with Next.js, TMDB, and custom embedding logic. Designed for speed, elegance, and an immersive browsing experience.

## Overview

Vault is a full-stack web application for searching movies and TV shows, browsing trending content, and watching media through a clean, Apple TV-inspired interface. It features dynamic routing, real-time search, TV episode browsers, and a glassmorphism UI with smooth animations.

## Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | Next.js 16 (App Router) |
| Styling | Tailwind CSS + custom CSS variables |
| Animations | Framer Motion |
| Icons | Lucide React |
| API Proxying | Next.js API routes + middleware |
| Data Fetching | TMDB API, OMDb API |
| Fonts | Acorn (heading), Lexend (body) |
| Hosting | Pxxl (production) |
| State Management | React hooks |

## Features

**Search & Discovery**
- Real-time search with "Did you mean?" suggestions
- Tabbed filtering by movie or TV show
- Premium loading states with rotating messages
- Dynamic greeting based on local time

**TV Show Browsing**
- Season and episode browser with collapsible seasons
- Next episode countdown with air date tracking
- "Series Complete" banner for finished shows
- Episode thumbnails from TMDB
- "Watching" indicator for current episode

**Movie Browsing**
- Detailed pages with poster, synopsis, and rating
- "More Like This" recommendations from TMDB
- Play button with smooth transitions

**Premium UI**
- Glassmorphism navbar (full-width bar to pill on scroll)
- Cinematic ambient glow behind navbar
- Staggered word animations on hero greeting
- Smooth page transitions with Framer Motion
- Dark mode only

**Performance**
- 24-hour caching for discovery data
- Rate-limited API routes (50 requests per minute per IP)
- Origin and referer validation for API protection
- Server-side rendering for static content
- Dynamic imports for heavy components

## Component Highlights

| Component | Purpose |
|-----------|---------|
| DynamicGreeting | Time-based hero greeting with animated accent word |
| FilterableSection | Language-filtered content rows |
| PosterRow | Horizontal scrolling poster grid with hover effects |
| SectionDivider | Premium divider with centered label |
| VideoPlayer | Embed player with server switching (3 sources) |
| TVEpisodes | Season accordion + episode grid with thumbnails |
| NextEpisodeCard | Upcoming episode countdown |

## Security

- API proxy hides OMDb and TMDB keys
- Rate limiting per IP (50 requests per minute)
- Origin and referer validation
- Middleware protection for all API routes
- Anti-devtools protection

## Screenshots

| Homepage | Search Results | TV Show Page |
|----------|---------------|--------------|
| ![Home](Home.png) | ![Search](Search.png) | ![TV](Tv.png) |

| Watch Page | Movie Page | Episode Browser |
|-----------|------------|-----------------|
| ![Watch](Watch.png) | ![Movie](Movie.png) | ![Episodes](Tv-detail.png) |

## Demo

[Watch Demo Video](Demo.webm)

## Project Structure

**App Routes**
- `src/app/api/discover/` — TMDB discovery endpoint
- `src/app/api/omdb/` — OMDb API proxy
- `src/app/api/tmdb/` — TMDB API proxy
- `src/app/movie/[id]/` — Movie detail page
- `src/app/search/` — Search results page
- `src/app/tv/[id]/` — TV show page
- `src/app/watch/[id]/` — Video player page

**Components**
- `src/components/DynamicGreeting.jsx` — Time-based hero greeting
- `src/components/FilterableSection.jsx` — Language-filtered content rows
- `src/components/Navbar.jsx` — Glassmorphism navigation
- `src/components/PosterRow.jsx` — Horizontal poster grid
- `src/components/SectionDivider.jsx` — Premium divider with label
- `src/components/TVEpisodes.jsx` — Season accordion + episode grid
- `src/components/VideoPlayer.jsx` — Embed player with server switching

**Libraries**
- `src/lib/omdb.js` — OMDb API wrapper
- `src/lib/tmdb.js` — TMDB API wrapper

**Assets & Config**
- `public/fonts/acorn-semibold.woff2` — Heading font
- `env.local` — Environment variables
- `next.config.mjs` — Next.js configuration
- `tailwind.config.js` — Tailwind CSS configuration
- `package.json` — Dependencies and scripts


## Deployment

Deployed

## Lessons Learned

- Next.js 15+ dynamic routing: params and searchParams are now Promises
- TMDB API integration: handling rate limits, fallbacks, and language filters
- Hydration errors: avoiding whitespace mismatches in className
- SSR fetch errors: using NEXT_PUBLIC_APP_URL for absolute URLs
- Premium UI design: glassmorphism, ambient glow, staggered animations

## License

Private. All rights reserved.

## Contact

- GitHub: [whoknowsasaint](https://github.com/whoknowsasaint)

