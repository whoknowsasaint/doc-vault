

📄 README.md 

```
# StreamVault — Cinema‑Grade Streaming Discovery

A premium, cinematic streaming discovery platform built with Next.js, TMDB, and custom embedding logic. Designed for speed, elegance, and a truly immersive browsing experience.

---

## 📖 Overview

StreamVault is a full‑stack web application that allows users to search for movies and TV shows, browse trending content, and watch media through a clean, Apple‑TV‑inspired interface. The platform features dynamic routing, real‑time search, TV episode browsers, and a premium glass‑morphism UI with smooth animations.

Built as a personal project, it demonstrates advanced Next.js patterns, API proxying, client‑side state management, and responsive design.

---

## 🏗️ Architecture

```

┌─────────────────────────────────────────────────────────────┐
│                      Next.js App Router                     │
├─────────────────────────────────────────────────────────────┤
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐   │
│  │  Home    │  │  Search  │  │   TV     │  │  Watch   │   │
│  │  (SSR)   │  │  (CSR)   │  │  (CSR)   │  │  (CSR)   │   │
│  └──────────┘  └──────────┘  └──────────┘  └──────────┘   │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐    │
│  │              API Routes (Next.js)                   │    │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐          │    │
│  │  │  /omdb   │  │  /tmdb   │  │ /discover│          │    │
│  │  └──────────┘  └──────────┘  └──────────┘          │    │
│  └─────────────────────────────────────────────────────┘    │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────────────────────────────────────────────┐    │
│  │              External APIs                          │    │
│  │  ┌──────────┐  ┌──────────┐  ┌──────────┐          │    │
│  │  │   OMDb   │  │   TMDB   │  │ VidSrc   │          │    │
│  │  └──────────┘  └──────────┘  └──────────┘          │    │
│  └─────────────────────────────────────────────────────┘    │
└─────────────────────────────────────────────────────────────┘

```

---

## ⚙️ Tech Stack

| Layer | Technology |
|-------|------------|
| **Framework** | Next.js 16 (App Router) |
| **Styling** | Tailwind CSS + Custom CSS Variables |
| **Animations** | Framer Motion |
| **Icons** | Lucide React |
| **API Proxying** | Next.js API Routes + Middleware |
| **Data Fetching** | TMDB API, OMDb API |
| **Fonts** | Acorn (heading) + Lexend (body) |
| **Hosting** | Pxxl (production) |
| **State Management** | React Hooks (no external store) |

---

## ✨ Key Features

### 🎬 Search & Discovery
- **Real‑time search** with "Did you mean?" suggestions
- **Search by movie or TV show** with tabbed filtering
- **Premium loading states** with rotating messages
- **Dynamic greeting** based on user's local time (cinematic entrance)

### 📺 TV Show Browsing
- **Season & episode browser** with collapsible seasons
- **Next episode countdown** with air date tracking
- **"Series Complete" banner** for finished shows
- **Episode thumbnails** from TMDB
- **"Watching" indicator** for current episode

### 🎞️ Movie Browsing
- **Detailed movie pages** with poster, synopsis, and rating
- **"More Like This" recommendations** (similar movies from TMDB)
- **Play button** with smooth transitions

### 🎨 Premium UI
- **Glass‑morphism navbar** (full‑width bar → pill on scroll)
- **Cinematic ambient glow** behind navbar
- **Staggered word animations** on hero greeting
- **Smooth page transitions** with Framer Motion
- **Dark mode only** (cinematic aesthetic)

### ⚡ Performance
- **24‑hour caching** for discovery data
- **Rate‑limited API routes** (50 requests per minute per IP)
- **Origin/referer validation** for API protection
- **Server‑side rendering** for static content
- **Dynamic imports** for heavy components

---

## 🧩 Component Highlights

| Component | Purpose |
|-----------|---------|
| `DynamicGreeting` | Time‑based hero greeting with animated accent word |
| `FilterableSection` | Language‑filtered content rows (All, American, Korean, Japanese, Chinese) |
| `PosterRow` | Horizontal scrolling poster grid with hover effects |
| `SectionDivider` | Premium divider with centered label |
| `VideoPlayer` | Embed player with server switching (3 sources) |
| `TVEpisodes` | Season accordion + episode grid with thumbnails |
| `NextEpisodeCard` | Upcoming episode countdown |

---

## 🛡️ Security Features

- **API proxy** hides OMDb and TMDB keys
- **Rate limiting** per IP (50 requests/minute)
- **Origin/referer validation** (only your domain can call APIs)
- **Middleware protection** for all API routes
- **Anti‑devtools protection** (redirects to home if DevTools is opened)

---

## 📂 Project Structure

```

doc-streamvaultt.org/
├── src/
│   ├── app/
│   │   ├── api/
│   │   │   ├── discover/    # TMDB discovery endpoint
│   │   │   ├── omdb/       
│   │   │   └── tmdb/       
│   │   ├── movie/[id]/      # Movie detail page
│   │   ├── search/          # Search results page
│   │   ├── tv/[id]/         # TV show page
│   │   └── watch/[id]/      # Video player page
│   ├── components/
│   │   ├── DynamicGreeting.jsx
│   │   ├── FilterableSection.jsx
│   │   ├── Navbar.jsx
│   │   ├── PosterRow.jsx
│   │   ├── SectionDivider.jsx
│   │   ├── TVEpisodes.jsx
│   │   └── VideoPlayer.jsx
│   └── lib/
│       ├── omdb.js          
│       └── tmdb.js          
├── public/
│   └── fonts/
│       └── acorn-semibold.woff2
├── .env.local
├── next.config.mjs
├── tailwind.config.js
└── package.json

```

---

## 🚀 Deployment

The app is deployed on **Pxxl** (production) and **Vercel**.

**Live URL:** *

---

## 📚 Lessons Learned

- **Next.js 15+ dynamic routing:** `params` and `searchParams` are now Promises that must be `await`ed.
- **TMDB API integration:** Handling rate limits, fallbacks, and language filters.
- **Hydration errors:** Avoiding whitespace mismatches in `className` strings.
- **SSR fetch errors:** Using `NEXT_PUBLIC_APP_URL` for absolute URLs during build.
- **Client‑side vs Server‑side:** Knowing when to use `'use client'` and when to keep components server‑side.
- **Premium UI design:** Glass‑morphism, ambient glow, staggered animations, and restraint with accent colors.

---

## 📜 License

Private — All rights reserved. 

---

## 🤝 Contact

- **GitHub:** [whoknowsasaint](https://github.com/whoknowsasaint)
```
