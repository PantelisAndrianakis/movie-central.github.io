# 🎬 Movie Central

**A love letter to the golden age of cinema — delivered fresh to your screen, every single day.**

Welcome to [moviecentral.net](https://moviecentral.net), a handcrafted daily movie showcase wrapped in the warm glow of a vintage theater. No frameworks. No build tools. No bloat. Just pure, beautiful, static web magic hosted on GitHub Pages.

## ✨ What Is This?

Imagine walking up to an old-school movie theater every day and seeing a brand new film on the marquee. The lights flicker, the posters change, and the ticket stub tells you what's playing. That's Movie Central.

Born from one simple problem: *what movie should we watch tonight?* When you're settling in for another evening of cinema, sometimes the endless scroll through streaming catalogs kills the vibe before it even starts. Movie Central solves this with a year of pre-selected films — one for every single day — so you can skip the decision paralysis and get straight to the good stuff.

Every day of the year has its own featured movie — complete with a full poster, preview thumbnails for the surrounding week, direct links to IMDB and Rotten Tomatoes, and silky smooth navigation that lets you scroll through the calendar like you're flipping through a film reel. It's a curated film calendar, not a streaming service.

The whole thing is dressed up in a gorgeous theater aesthetic — a full-screen cinematic backdrop, a glowing marquee banner, a vintage ticket stub with dynamically sized text, and hover effects that make every element feel alive. It's not just a website. It's an experience.

## 🔥 What Makes It Special

- **365 days of curated cinema.** Every day of the year gets its own movie. That's a full year of hand-picked films, ready to discover.
- **Zero dependencies.** No React. No Vue. No Node. No npm install. Just raw HTML, CSS, and vanilla JavaScript doing exactly what they were born to do. The entire site loads in a blink — under 75 KB of code for a full year of cinema.
- **Buttery smooth navigation.** Click the arrows, tap the keyboard, click any preview thumbnail, or punch a date straight into the URL. Every transition fades gracefully with anti-spam protection so nothing ever stutters or breaks.
- **The ticket stub is a masterpiece.** It uses CSS container query units (`cqi`) for perfectly scaled typography inside an aspect-ratio-locked container. The movie title auto-sizes based on length, and the year rotates 90° on the right edge — just like a real vintage ticket. It's a small detail that took real craft to get right.
- **Fully responsive down to mobile.** The three-column theater grid gracefully collapses into a single-column layout on smaller screens. The side previews reorganize into horizontal rows, the ticket takes center stage above the controls, and it all just *works* — across five carefully tuned breakpoints.
- **Browser history integration.** Every day you navigate to gets its own URL via `pushState`, so the back and forward buttons work perfectly. You can bookmark any day, share a link to a specific date, or deep-link directly with query parameters.
- **A custom 404 page that actually slaps.** Instead of a generic error, you get a cinematic "Movie not found!" screen with a glowing popcorn icon and text that looks like it belongs on a neon theater sign. Even getting lost on this site feels good.

## ⚡ By The Numbers

The entire site is ridiculously lightweight — proving that great experiences don't need bloated frameworks:

| Component | Size | Notes |
|---|---|---|
| `index.html` | < 12 KB | The entire main page structure |
| `style.css` | < 6 KB | All styles, animations, and 5 breakpoints |
| All 366 JS files | < 55 KB | Every day of the year (~150 bytes/day avg) |
| Static UI images | < 370 KB | Theater, marquee, ticket, arrows, popcorn buttons |
| 366 poster images | < 45 MB | Full-size feature artwork |
| 366 preview images | < 8 MB | Thumbnail grid images |

**What this means:** The entire "engine" (HTML + CSS + JS for a full year) weighs in under **75 KB**. Even with 732 total images, the complete site is ~55 MB — and images only load as you navigate. The initial page load is *instant*.

## 🎞️ How It Works

### Daily Movie Data

Each day maps to a tiny JavaScript file in `js/`, named by month and day:

```
js/1_1.js    → January 1st
js/6_15.js   → June 15th
js/12_25.js  → December 25th
```

Each file defines a single movie object — dead simple:

```js
movieData = {
    movie: "The Shawshank Redemption",
    year: "1994",
    imdb_id: "tt0111161",
    rotten_tomatoes_slug: "the_shawshank_redemption"
};
```

When you load the site, it grabs today's data plus three days in each direction, giving you a full week-at-a-glance view with clickable preview thumbnails flanking the main poster.

### Image Assets

Every movie needs two images:

- **Poster** → `images/posters/{rotten_tomatoes_slug}.jpg` — The big, beautiful center artwork.
- **Preview** → `images/previews/{rotten_tomatoes_slug}.jpg` — The smaller side column thumbnails.

Static UI assets that bring the theater to life:

| File | Purpose |
|---|---|
| `images/theater.jpg` | The full-screen cinematic background |
| `images/marquee.png` | The glowing marquee banner frame |
| `images/ticket.png` | The vintage ticket stub frame |
| `images/arrow_left.png` | Navigate to the previous day |
| `images/arrow_right.png` | Navigate to the next day |
| `images/popcorn.png` | Favicon and 404 page star |
| `images/popcorn_imdb.png` | Clickable IMDB link |
| `images/popcorn_rt.png` | Clickable Rotten Tomatoes link |

## 🏛️ Layout

The interface is built around three persistent sections that work together like a real theater facade:

1. **The Marquee** (top, always visible) — A decorative banner image with "Movie Central" rendered in the Philosopher font, floating over the frame with text shadow for that authentic lit-sign look.

2. **The Stage** (center, fades on navigation) — A three-column CSS grid that's the heart of the experience:
   - **Left column** — Three stacked thumbnails showing the past 3 days. Click any to jump back in time.
   - **Center feature** — Today's movie poster, front and center, as it should be.
   - **Right column** — Three stacked thumbnails showing the next 3 days. Click any to jump forward.

3. **The Controls** (bottom, always visible) — Navigation arrows on the edges, IMDB and Rotten Tomatoes popcorn buttons flanking the center, and the crown jewel — a ticket stub displaying the current movie's title and year with pixel-perfect typography.

## 🎮 Navigation

There are five ways to move through the schedule — because great UX means meeting people where they are:

| Method | How |
|---|---|
| **Arrow buttons** | Click the left/right arrows in the bottom row |
| **Keyboard** | Press `←` / `→` arrow keys |
| **Side thumbnails** | Click any preview image to jump directly to that day |
| **URL parameters** | Go to `?year=2025&month=12&day=25` for any date |
| **Browser history** | Back and forward buttons work seamlessly |

Every navigation triggers a fade transition on the content grid, and there's built-in anti-spam protection with a cooldown timer so rapid clicks never cause chaos.

## 📱 Responsive Design

Five breakpoints ensure the theater looks incredible on everything from ultrawide monitors to phone screens:

| Breakpoint | Content Width | What Changes |
|---|---|---|
| > 1400px | 45% | Full three-column theater grid |
| ≤ 1400px | 62% | Wider container for medium-large screens |
| ≤ 1200px | 70% | Continues expanding |
| ≤ 1024px | 78% | Grid proportions adjust |
| ≤ 768px | 86% | Single column — side images become horizontal rows, ticket moves above controls |
| ≤ 480px | 92% | Side images stack vertically for the smallest screens |

## 📁 Project Structure

```
├── CNAME                  # Custom domain → moviecentral.net
├── index.html             # The main stage
├── 404.html               # The best-looking 404 you've ever seen
├── style.css              # Every style, animation, and breakpoint
├── images/
│   ├── theater.jpg        # Cinematic background
│   ├── marquee.png        # Marquee banner frame
│   ├── ticket.png         # Ticket stub frame
│   ├── arrow_left.png     # Navigation arrow
│   ├── arrow_right.png    # Navigation arrow
│   ├── popcorn.png        # Favicon & 404 icon
│   ├── popcorn_imdb.png   # IMDB link button
│   ├── popcorn_rt.png     # Rotten Tomatoes link button
│   ├── posters/           # Full movie poster images
│   └── previews/          # Thumbnail preview images
└── js/
    └── {month}_{day}.js   # One file per day of the year
```

## 🎬 Adding a New Movie

It takes about 60 seconds:

1. **Create the data file** for the target date in `js/`:
   ```js
   // js/2_14.js — Valentine's Day pick
   movieData = {
       movie: "When Harry Met Sally",
       year: "1989",
       imdb_id: "tt0098635",
       rotten_tomatoes_slug: "when_harry_met_sally"
   };
   ```
2. **Drop in the poster** → `images/posters/when_harry_met_sally.jpg`
3. **Drop in the preview** → `images/previews/when_harry_met_sally.jpg`
4. **Push to GitHub.** Done. The site updates automatically.

## 🏗️ Hosting

Hosted on **GitHub Pages** with a custom domain via the `CNAME` file pointing to `moviecentral.net`. No CI/CD pipeline, no build step, no server. Push your changes, and the world sees them. That's the beauty of going fully static.

## 🖋️ Fonts

- [**Philosopher**](https://fonts.google.com/specimen/Philosopher) — The soul of the theater. Used for the marquee title, ticket text, and the 404 page. Bold, elegant, and cinematic.
- [**Source Sans Pro**](https://fonts.google.com/specimen/Source+Sans+Pro) — Clean and precise. Used for the rotated year on the ticket stub.

Both loaded from Google Fonts — no self-hosting overhead.

## 📜 License

All movie metadata, poster artwork, and associated trademarks belong to their respective owners and studios. This project is a fan-built showcase celebrating the art of cinema — a digital marquee, not a movie theater. It points you toward great films; it doesn't deliver them. For that, you'll need your preferred streaming service, rental platform, or a good old-fashioned DVD collection.

---

*Built with nothing but passion, vanilla code, and an unreasonable love for movies.* 🍿
