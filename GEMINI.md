# GEMINI.md — Project Context & AI Assistant Guide

## Project Overview
**Deepavali | Festival of Lights — Five-Day Tribute (`Diwali2026`)** is a self-contained, zero-build static web application celebrating **Deepavali (Diwali)** — the five-day Indian festival of lights. It combines rich cultural storytelling, traditional Indian aesthetics, animated SVG illustrations, ambient HTML5 Canvas particle systems, and an interactive **Virtual Diya & Personalized Blessing Card Generator** capable of exporting high-resolution (`1200×800`) PNG greeting cards directly in the browser.

- **Live Deployment Target**: `https://parbonstatic.github.io/Diwali2026/`
- **Architecture**: Single-page static HTML5 application (`index.html`) with Tailwind CSS (via CDN), Google Fonts, inline custom CSS, and vanilla ES6+ JavaScript.
- **License**: The Unlicense (Public Domain)

---

## Repository Structure

```text
Diwali2026/
├── .github/
│   └── workflows/
│       └── static.yml    # GitHub Actions workflow for automated GitHub Pages deployment
├── favicon.svg           # Custom scalable vector Diya lamp app icon (64×64 viewBox)
├── og-image.png          # Rasterized Open Graph / social preview banner (1200×630 PNG for crawlers)
├── og-image.svg          # Editable vector source for the Open Graph banner (1200×630 viewBox)
├── index.html            # Main application containing markup, styles, SVGs, and JS logic
├── LICENSE               # The Unlicense (Public Domain dedication)
├── GEMINI.md             # AI assistant context and architectural reference
└── README.md             # Project documentation, features, OG link setup, and usage guide
```

---

## Open Graph (OG) & Social Preview Configuration

Social media crawlers (WhatsApp, Facebook, LinkedIn, X/Twitter, Discord, Slack) require **two strict rules** to display rich link previews properly:
1. **Absolute HTTPS URLs**: Relative paths (such as `./og-image.png`) fail on most social scrapers. Every URL in `<head>` (`canonical`, `og:url`, `og:image`, `og:image:secure_url`, `twitter:url`, `twitter:image`) must use the full deployed origin (e.g., `https://parbonstatic.github.io/Diwali2026/...`).
2. **Raster Image Format (`PNG` / `JPG`)**: Social platforms do **not** support `.svg` files for `og:image`. Therefore, `og-image.svg` serves as the editable vector master, while `og-image.png` (`1200×630`, `image/png`) is the production asset referenced in `index.html`.

### Current Meta Tags in `index.html` (Lines 17–39)
```html
<!-- Canonical & Open Graph / Facebook / WhatsApp / LinkedIn Meta Tags -->
<link rel="canonical" href="https://parbonstatic.github.io/Diwali2026/" />
<meta property="og:type" content="website" />
<meta property="og:site_name" content="Deepavali | Festival of Lights" />
<meta property="og:locale" content="en_IN" />
<meta property="og:url" content="https://parbonstatic.github.io/Diwali2026/" />
<meta property="og:title" content="Illuminating Hearts & Homes | Deepavali — Five-Day Festival of Lights" />
<meta property="og:description" content="Explore the spiritual significance, the 5 sacred days of Diwali (Dhanteras to Bhai Dooj), timeless traditions, and light a virtual diya to download a personalized blessing card." />
<meta property="og:image" content="https://parbonstatic.github.io/Diwali2026/og-image.png" />
<meta property="og:image:secure_url" content="https://parbonstatic.github.io/Diwali2026/og-image.png" />
<meta property="og:image:type" content="image/png" />
<meta property="og:image:width" content="1200" />
<meta property="og:image:height" content="630" />
<meta property="og:image:alt" content="Glowing earthen clay diya lamp surrounded by golden rangoli motifs with the headline Illuminating Hearts & Homes | Deepavali" />

<!-- Twitter / X Card Meta Tags -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:url" content="https://parbonstatic.github.io/Diwali2026/" />
<meta name="twitter:title" content="Illuminating Hearts & Homes | Deepavali — Festival of Lights" />
<meta name="twitter:description" content="Celebrate the triumph of light over darkness. Explore the 5 days of Diwali, light an interactive virtual diya, and download your custom festive blessing card." />
<meta name="twitter:image" content="https://parbonstatic.github.io/Diwali2026/og-image.png" />
<meta name="twitter:image:alt" content="Shubh Deepavali — Illuminating Hearts & Homes | Five-Day Festival Tribute" />
```

### How to Update OG Links for a Custom Domain or Fork
When deploying to a different GitHub Pages URL, custom domain, or Netlify/Vercel host:
1. Open `index.html` and locate the `<head>` meta block (lines 17–39).
2. Replace every instance of `https://parbonstatic.github.io/Diwali2026/` with your target production base URL:
   - `link[rel="canonical"]` (`href`)
   - `meta[property="og:url"]` (`content`)
   - `meta[property="og:image"]` (`content`)
   - `meta[property="og:image:secure_url"]` (`content`)
   - `meta[name="twitter:url"]` (`content`)
   - `meta[name="twitter:image"]` (`content`)
3. If `og-image.svg` is modified, re-export `og-image.png` at exactly `1200×630` pixels so the raster preview stays in sync with the vector source.

---

## Design System & Aesthetics

### Color Palette
Configured in both Tailwind (`tailwind.config`) and CSS custom properties (`:root`):
- **Gold (`gold`)**: `#D4AF37` (DEFAULT), `#F5E08E` (`light`), `#FFD700` (`bright`), `#9E7B1C` (`dark`)
- **Marigold (`marigold`)**: `#FF8F00` (DEFAULT), `#FFB300` (`light`), `#E65100` (`deep`)
- **Vermilion (`vermilion`)**: `#B71C1C` (DEFAULT), `#D32F2F` (`light`), `#7F0000` (`dark`)
- **Midnight (`midnight`)**: `#1A0B2E` (DEFAULT), `#0F051D` (`deep`), `#24113E` (`card`), `#311852` (`soft`)
- **Ivory (`ivory`)**: `#FFFDF8` (DEFAULT), `#F7EFE1` (`warm`), `#E2D4BA` (`muted`)

### Typography
Loaded via Google Fonts:
- **`Rozha One`** (`font-rozha`): Display serif for headings, titles, and Sanskrit shlokas.
- **`Cinzel Decorative`** (`font-cinzel`): Ceremonial accent typography.
- **`Playfair Display`** (`font-playfair`): Italicized salutations, transliterations, and literary pull quotes.
- **`Poppins`** (`font-sans`): Clean body copy, UI controls, badges, and navigation.

### Custom Visual Components & Effects
- **`.gold-foil-card`**: Glassmorphic dark purple cards (`backdrop-filter: blur(12px)`) with composite CSS mask gradient borders (`::before`) and warm golden hover elevation.
- **`.text-gold-foil`**: Multi-stop metallic gold and marigold gradient text clip.
- **`.diya-flame` & `.diya-halo`**: Keyframe animations (`flameFlicker`, `haloPulse`) that simulate organic flickering flames and warm radial light bloom.
- **`.rangoli-spin` & `.rangoli-spin-reverse`**: Slow continuous 360-degree rotation for geometric mandala SVG backdrops.
- **`.rangoli-divider`**: Dotted radial-gradient horizontal section dividers.

---

## Application Sections & Interactive Modules (`index.html`)

1. **Sticky Navigation Header (`#navbar`)**:
   - Features mini animated SVG diya emblem, desktop navigation pills, "Light a Diya" CTA, and a responsive mobile navigation drawer (`#mobile-menu`).
2. **Hero Section (`#home`)**:
   - Headline *"Illuminating Hearts & Homes | Deepavali"*, live session community diya counter (`#hero-diya-count`, starting at `1,08,421+`), rotating lotus mandala, and a centerpiece ornate clay diya SVG.
3. **Spiritual Significance & Origin (`#significance`)**:
   - Three storytelling pillars:
     1. *Treta Yuga • The Ramayana*: Return of Lord Rama to Ayodhya.
     2. *Samudra Manthan • Cosmic Ocean*: Emergence of Goddess Lakshmi.
     3. *Atma Jyoti • Inner Awakening*: Spiritual philosophy of the clay diya, oil, wick, and flame.
4. **The 5 Sacred Days of Deepavali (`#five-days`)**:
   - Interactive tab stepper (`.day-tab`), spotlight detail card (`#day-spotlight`), prev/next cycle buttons (`#prev-day-btn`, `#next-day-btn`), and 5 clickable overview cards (`[data-day-card]`):
     - **Day 1**: Dhanteras (*Kartika Krishna Trayodashi*)
     - **Day 2**: Naraka Chaturdashi / Choti Diwali (*Kartika Krishna Chaturdashi*)
     - **Day 3**: Lakshmi Puja / Main Deepavali (*Kartika Amavasya*)
     - **Day 4**: Govardhan Puja / Annakut & Bestu Varas (*Kartika Shukla Pratipada*)
     - **Day 5**: Bhai Dooj / Yama Dwitiya (*Kartika Shukla Dwitiya*)
5. **Timeless Rituals & Celebrations (`#rituals`)**:
   - 4-card grid highlighting *Lighting of Earthen Diyas (Pradips)*, *Intricate Rangoli & Alpona Art*, *Mithai & Festive Feasts*, and *Fireworks, Phuljharis & Sparklers*.
6. **Interactive Virtual Diya & Blessing Generator (`#virtual-diya`)**:
   - **Interactive Diya Stage (`#virtual-diya-stage`)**: Clicking the diya or submitting `#diya-form` ignites `#virtual-flame`, triggers a 36-particle golden spark burst on `#diya-spark-canvas`, activates the radial bloom (`#virtual-diya-bloom`), and increments the community counter.
   - **Customization Form (`#diya-form`)**: Inputs for Sender Name (`#visitor-name`), Recipient (`#recipient-name`), and 5 curated blessing themes (`#blessing-select`: *Prosperity*, *Health*, *Inner Peace*, *Success*, *Harmony*).
   - **Live Greeting Card Preview & Export (`#greeting-card-preview`)**:
     - **Download Card (`#download-card-btn`)**: Uses an offscreen `1200×800` HTML5 2D Canvas (`downloadGreetingCardAsPNG()`) to procedurally render a framed greeting card complete with rangoli watermark, glowing diya vector drawing, wrapped typography, and sender signature, downloading as `Shubh-Deepavali-Card-<Sender>.png`.
     - **Copy Greeting (`#copy-wish-btn`)**: Copies formatted plain-text blessing to clipboard with fallback support.
     - **Share Wish (`#share-wish-btn`)**: Invokes Web Share API (`navigator.share`) on supported devices or falls back to clipboard copy.
7. **Sacred Shlokas & Festive Wishes (`#festive-wishes`)**:
   - Displays the *Pavamana Mantra* from the *Brihadaranyaka Upanishad (1.3.28)* (*"Asato Ma Sadgamaya, Tamaso Ma Jyotirgamaya, Mrityorma Amritam Gamaya"*) in Devanagari, transliteration, and 3-part philosophical breakdown, followed by 3 one-click copyable greeting cards (`.quick-copy-btn`).
8. **Ambient Background Canvas (`#particles-canvas`)**:
   - Full-viewport fixed canvas rendering up to 45 gently rising and pulsing golden light particles.

---

## Development & Maintenance Guidelines

- **Zero-Build Simplicity**: Keep the project runnable by directly opening `index.html` in any modern browser or serving via any static file server. Do not introduce bundlers or Node.js build steps unless explicitly requested.
- **Accessibility & Semantics**: Maintain `aria-selected`, `aria-expanded`, `role="tab"`, and descriptive `aria-label` attributes on interactive components.
- **Offline / Fallback Resilience**: Ensure all UI icons and illustrations remain inline SVGs or local assets (`favicon.svg`, `og-image.png`, `og-image.svg`), and keep clipboard/share fallbacks intact.
- **OG Tag Integrity**: Never revert `og:image` or `twitter:image` to relative paths or `.svg` URLs; always keep absolute HTTPS URLs pointing to `og-image.png`.
- **Canvas Card Export Consistency**: When modifying greeting themes in `blessingsLibrary`, ensure both the live DOM preview (`updateGreetingCard()`) and the 2D Canvas renderer (`downloadGreetingCardAsPNG()`) stay synchronized.
