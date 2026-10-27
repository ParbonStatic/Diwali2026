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
| **Markup & Structure** | Semantic HTML5, Open Graph & Twitter Card Meta Tags |
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
├── favicon.svg           # Custom vector glowing clay diya favicon
├── og-image.svg          # 1200×630 Open Graph social sharing banner
├── index.html            # Complete single-page application (HTML, CSS, SVG & JS)
├── LICENSE               # The Unlicense (Public Domain)
├── GEMINI.md             # AI assistant architectural context & guide
└── README.md             # Project documentation
```

---

## 🚀 Getting Started Locally

Because this project is built with a **zero-build static architecture**, no package installation or compilation step is required.

### Option 1: Open Directly
Simply double-click [`index.html`](./index.html) or open it in any modern browser.

### Option 2: Run a Local Static Server
If you prefer serving over `http://localhost`:

```bash
# Using Python 3
python -m http.server 8080

# Or using Node.js (npx)
npx serve .
```

Then visit `http://localhost:8080` in your browser.

---

## 📜 License

This project is released into the public domain under **[The Unlicense](./LICENSE)**. You are free to copy, modify, distribute, and use this work for any purpose without restriction.

---

<p align="center">
  <strong>🪔 शुभ दीपावली • तमसो मा ज्योतिर्गमय 🪔</strong><br/>
  <em>May the eternal light of Deepavali illuminate every heart and home.</em>
</p>

