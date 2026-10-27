# 🪔 Deepavali | Festival of Lights — Five-Day Cultural Tribute

[![Deploy static content to Pages](https://github.com/parbonstatic/Diwali2026/actions/workflows/static.yml/badge.svg)](https://github.com/parbonstatic/Diwali2026/actions/workflows/static.yml)
[![License: Unlicense](https://img.shields.io/badge/license-Unlicense-gold.svg)](./LICENSE)

> ***"Illuminating Hearts & Homes | Deepavali"***  
> *Celebrating the triumph of light over darkness, knowledge over ignorance, and good over evil.*

**Deepavali 2026** is an interactive, richly illustrated single-page web experience dedicated to India's most luminous five-day festival. Crafted with royal Indian aesthetics—midnight violet skies, marigold blooms, vermilion accents, and metallic gold-foil framing—it guides visitors through the spiritual origins, the five sacred days of Diwali, timeless traditions, Vedic mantras, and an interactive **Virtual Diya & Personalized Blessing Card Studio**.

🌐 **Live Demo:** [https://parbonstatic.github.io/Diwali2026/](https://parbonstatic.github.io/Diwali2026/)

---

## ✨ Key Features

- **🪔 Interactive Virtual Diya Studio**:
  - Click the unlit terracotta lamp or submit the blessing form to ignite a realistic flickering SVG flame with a **36-particle golden spark burst** on an HTML5 Canvas.
  - Increments the live session counter of *"Diyas of Hope Lit"*.
- **🖼️ High-Resolution PNG Greeting Card Generator**:
  - Personalize your greeting with your **Sender Name**, **Recipient Name**, and one of **5 Sacred Festive Blessings** (*Prosperity & Abundance*, *Vibrant Health & Longevity*, *Inner Peace & Spiritual Clarity*, *Wisdom & Success*, or *Family Harmony*).
  - **Download Card**: Procedurally renders and downloads a crisp **`1200×800` PNG greeting card** directly in the browser using the HTML5 2D Canvas API—complete with an ornate gold-foil border, mandala watermark, glowing diya illustration, and Devanagari sign-off.
  - **Copy & Share**: One-click clipboard copy and native mobile sharing via the **Web Share API** (`navigator.share`).
- **📅 Interactive 5-Day Deepavali Timeline & Stepper**:
  - Explore all five sacred chapters with interactive tabs, spotlight cards, previous/next navigation, and footer quick-jump links:
    1. **Day 1 — Dhanteras** (*Kartika Krishna Trayodashi*): Honoring Lord Dhanvantari, Goddess Lakshmi & Kubera.
    2. **Day 2 — Naraka Chaturdashi / Choti Diwali** (*Kartika Krishna Chaturdashi*): Victory of Lord Krishna & Satyabhama over Narakasura.
    3. **Day 3 — Lakshmi Puja / Main Deepavali** (*Kartika Amavasya*): Sacred Pradosh Kaal worship and illumination.
    4. **Day 4 — Govardhan Puja / Annakut & Bestu Varas** (*Kartika Shukla Pratipada*): Ecological gratitude and New Year observances.
    5. **Day 5 — Bhai Dooj / Yama Dwitiya** (*Kartika Shukla Dwitiya*): Celebrating the eternal bond between brothers and sisters.
- **🕉️ Spiritual Significance, Rituals & Sacred Shlokas**:
  - Detailed storytelling cards on the **Return of Lord Rama to Ayodhya**, **Emergence of Goddess Lakshmi**, and the **Atma Jyoti philosophy** of the earthen diya.
  - Showcases the **Pavamana Mantra** (*Brihadaranyaka Upanishad 1.3.28* — *"Asato Ma Sadgamaya, Tamaso Ma Jyotirgamaya, Mrityorma Amritam Gamaya"*) in Sanskrit Devanagari, transliteration, and philosophical commentary.
  - Ready-to-share festive wishes grid with instant copy buttons.
- **✨ Ambient Visual Craftsmanship**:
  - Full-viewport floating golden light particles canvas (`#particles-canvas`), rotating geometric rangoli mandalas, smooth scroll-reveal animations (`IntersectionObserver`), and full mobile responsiveness.

---

## 🛠️ Tech Stack

| Layer | Technology |
| :--- | :--- |
| **Markup & Structure** | Semantic HTML5, Canonical, Open Graph & Twitter Card Meta Tags |
| **Styling & Theme** | [Tailwind CSS](https://tailwindcss.com/) (CDN) + Custom CSS Variables, Keyframes & Gold-Foil Masks |
| **Typography** | Google Fonts (`Rozha One`, `Cinzel Decorative`, `Playfair Display`, `Poppins`) |
| **Graphics & Animation** | Custom Inline SVGs, HTML5 2D Canvas (Particle Systems & `1200×800` PNG Card Renderer) |
| **Interactivity** | Vanilla JavaScript (ES6+), Web Share API, Clipboard API, IntersectionObserver API |
| **Deployment** | GitHub Actions (`.github/workflows/static.yml`) → GitHub Pages |

---

## 📂 Project Structure

```text
Diwali2026/
├── .github/
│   └── workflows/
│       └── static.yml    # Automated GitHub Pages deployment workflow
├── favicon.svg           # Custom vector glowing clay diya favicon (64×64)
├── og-image.png          # 1200×630 PNG Open Graph banner for social media link previews
├── og-image.svg          # 1200×630 SVG editable vector master of the Open Graph banner
├── index.html            # Complete single-page application (HTML, CSS, SVG & JS)
├── LICENSE               # The Unlicense (Public Domain)
├── GEMINI.md             # AI assistant architectural context & guide
└── README.md             # Project documentation
```

---

## 🔗 Open Graph (OG) & Social Sharing Setup

To ensure rich preview cards render properly when sharing the link on **WhatsApp, Facebook, LinkedIn, X (Twitter), Discord, and Slack**, [`index.html`](./index.html) is configured with complete Open Graph and Twitter Card metadata.

### Why Absolute URLs & PNG Are Required
1. **Absolute HTTPS Links**: Social media crawlers do not resolve relative file paths (like `./og-image.png`). All URL properties (`og:url`, `og:image`, `og:image:secure_url`, `twitter:url`, `twitter:image`, and `canonical`) **must** be full `https://` URLs pointing to your live deployed site.
2. **Raster PNG Format (`1200×630`)**: Most social platforms (especially WhatsApp, Facebook, and X) ignore `.svg` images in Open Graph tags. This repository includes both [`og-image.svg`](./og-image.svg) (vector design source) and [`og-image.png`](./og-image.png) (the `1200×630` raster PNG served to social crawlers).

### How to Add or Update OG Links for Your Own Deployment
If you fork this repository or deploy it under a custom domain, update lines **17–39** inside the `<head>` of [`index.html`](./index.html) by replacing `https://parbonstatic.github.io/Diwali2026/` with your own live deployment URL:

```html
<!-- Canonical & Open Graph / Facebook / WhatsApp / LinkedIn Meta Tags -->
<link rel="canonical" href="https://YOUR-DOMAIN-OR-USERNAME.github.io/YOUR-REPO/" />
<meta property="og:type" content="website" />
<meta property="og:site_name" content="Deepavali | Festival of Lights" />
<meta property="og:locale" content="en_IN" />
<meta property="og:url" content="https://YOUR-DOMAIN-OR-USERNAME.github.io/YOUR-REPO/" />
<meta property="og:title" content="Illuminating Hearts & Homes | Deepavali — Five-Day Festival of Lights" />
<meta property="og:description" content="Explore the spiritual significance, the 5 sacred days of Diwali (Dhanteras to Bhai Dooj), timeless traditions, and light a virtual diya to download a personalized blessing card." />
<meta property="og:image" content="https://YOUR-DOMAIN-OR-USERNAME.github.io/YOUR-REPO/og-image.png" />
<meta property="og:image:secure_url" content="https://YOUR-DOMAIN-OR-USERNAME.github.io/YOUR-REPO/og-image.png" />
<meta property="og:image:type" content="image/png" />
<meta property="og:image:width" content="1200" />
<meta property="og:image:height" content="630" />
<meta property="og:image:alt" content="Glowing earthen clay diya lamp surrounded by golden rangoli motifs with the headline Illuminating Hearts & Homes | Deepavali" />

<!-- Twitter / X Card Meta Tags -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:url" content="https://YOUR-DOMAIN-OR-USERNAME.github.io/YOUR-REPO/" />
<meta name="twitter:title" content="Illuminating Hearts & Homes | Deepavali — Festival of Lights" />
<meta name="twitter:description" content="Celebrate the triumph of light over darkness. Explore the 5 days of Diwali, light an interactive virtual diya, and download your custom festive blessing card." />
<meta name="twitter:image" content="https://YOUR-DOMAIN-OR-USERNAME.github.io/YOUR-REPO/og-image.png" />
<meta name="twitter:image:alt" content="Shubh Deepavali — Illuminating Hearts & Homes | Five-Day Festival Tribute" />
```

### Customizing the Social Preview Banner
1. Edit the vector artwork or text in [`og-image.svg`](./og-image.svg).
2. Export/convert [`og-image.svg`](./og-image.svg) to [`og-image.png`](./og-image.png) at **`1200×630` pixels**.
3. Commit and push both files so your deployed `https://<your-domain>/og-image.png` serves the updated preview image.

---

## 🚀 Getting Started Locally

Because this project uses a **zero-build static architecture**, no package installation or build step is required.

### Option 1: Open Directly
Simply double-click [`index.html`](./index.html) or open it in any modern web browser.

### Option 2: Run a Local Static Server
If you prefer serving over `http://localhost`:

```bash
# Using Python 3
python -m http.server 8080

# Or using Node.js (npx)
npx serve .
```

Then open `http://localhost:8080` in your browser.

---

## 📜 License

This project is released into the public domain under **[The Unlicense](./LICENSE)**. You are free to copy, modify, distribute, and use this work for any purpose without restriction.

---

<p align="center">
  <strong>🪔 शुभ दीपावली • तमसो मा ज्योतिर्गमय 🪔</strong><br/>
  <em>May the eternal light of Deepavali illuminate every heart and home.</em>
</p>
