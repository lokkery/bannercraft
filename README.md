# 🎨 Quickbanner

**One HTML file. Zero dependencies. Infinite banners.**

Quickbanner is a fully client-side banner image generator. Drop the file on any static host, share a URL with your headline baked into it, and get a pixel-perfect PNG back — no server, no build step, no API key.

> **Origin story:** Built by [Lokkery](https://lokkery.com) to generate featured images for the [Lokkery Blog](https://lokkery.com/blog). Some article covers you see there was made with this tool. I needed a fast, repeatable way to create consistent title banners without Figma, Canva, or a designer — so i built it in a single HTML file and open-sourced it.

---

## ✨ Features

- **32 gradient themes** — Sunrise, Ember, Ocean, Retrowave, Matrix, and 27 more
- **14 Google Fonts** + 2 system fonts, loaded on demand
- **Custom resolution** — type any dimensions or pick from 9 social media presets (LinkedIn, Twitter/X, OG image, Full HD, 2K…)
- **Font size sliders** — independent controls for headline and brand text, with auto-fit mode
- **Padding sliders** — adjust horizontal and vertical spacing independently
- **Shareable URLs** — every setting is encoded as a query parameter; share a link and the recipient sees the exact same banner
- **Raw image mode** — append `&raw=1` to get just the canvas, no UI; embed directly in an `<img>` tag
- **One-click PNG download** — filename includes the resolution, e.g. `banner-1200x630.png`

---

## 🚀 Getting Started

No installation required.

Deploy to **GitHub Pages**, **Netlify**, **Vercel**, or **Cloudflare Pages** by uploading the single file.

---

## 🔗 URL API

Every option is a query parameter. Build banner URLs programmatically or share them directly.

```
index.html?text=Your+Headline+Here&theme=ocean&w=1200&h=630&raw=1
```

### Parameters

| Parameter | Default | Description |
|---|---|---|
| `text` | *(required)* | URL-encoded headline text |
| `tagline` | — | Small brand text in the bottom-right corner |
| `theme` | `sunrise` | Gradient theme ID (see list below) |
| `w` | `1200` | Canvas width in px |
| `h` | `400` | Canvas height in px |
| `textColor` | `dark` | `dark` or `white` |
| `font` | `Arial` | Font name (e.g. `Poppins`, `Bebas+Neue`) |
| `hs` | `0` | Headline font size (0 = auto-fit) |
| `bs` | `5` | Brand text size (1–10) |
| `px` | `9` | Horizontal padding % (1–25) |
| `py` | `16` | Vertical padding % (1–35) |
| `raw` | — | Set to `1` to render image only, no UI |
| `download` | — | Set to `1` to auto-trigger PNG download |

### Example URLs

```
# Simple OG image
index.html?text=Hello+World&theme=ocean&w=1200&h=630&raw=1

# LinkedIn banner with custom font and brand
index.html?text=We%27re+Hiring+Senior+Engineers&tagline=lokkery.com&theme=neon-dusk&font=Poppins&w=1200&h=628&textColor=white&raw=1

# Twitter/X header
index.html?text=New+Feature+Drop&theme=retrowave&w=1500&h=500&font=Bebas+Neue&textColor=white&raw=1

# Full HD wallpaper
index.html?text=Ship+Fast.+Test+Everything.&theme=midnight&w=1920&h=1080&px=12&py=20&raw=1
```

---

## 🎨 Themes

| Group | IDs |
|---|---|
| **Warm** | `sunrise` `ember` `peach` `rose-gold` `cherry` `autumn` `heatmap` `golden-hour` `candy` |
| **Cool** | `sky` `ocean` `cosmic` `nordic` `steel` `northern` `dusk` |
| **Green** | `mint` `forest` `teal-lime` `emerald` `matrix` |
| **Purple / Pink** | `lavender` `neon-dusk` `aurora` `plum` `blueberry` `retrowave` `watermelon` |
| **Neutral / Dark** | `sand` `slate` `midnight` `obsidian` |

---

## 🖋 Fonts

System fonts: `Arial`, `Georgia`

Google Fonts (loaded on demand): `Inter` `Montserrat` `Oswald` `Raleway` `Playfair Display` `Lato` `Nunito` `Poppins` `Roboto Slab` `DM Sans` `Space Grotesk` `Bebas Neue` `Righteous` `Merriweather`

---

## 📐 Resolution Presets

| Preset | Dimensions | Use case |
|---|---|---|
| Wide 3:1 | 1200 × 400 | Blog headers |
| OG 1.91:1 | 1200 × 630 | Open Graph / link previews |
| LinkedIn | 1200 × 628 | LinkedIn posts |
| Twitter / X | 1500 × 500 | Twitter header |
| Facebook Cover | 820 × 312 | Facebook page cover |
| GitHub | 1280 × 640 | GitHub social preview |
| Dev.to | 800 × 418 | Dev.to article cover |
| Full HD | 1920 × 1080 | Presentations / wallpapers |
| 2K | 2560 × 1440 | High-res displays |

---

## 🏗 How It Works

Quickbanner uses the browser's native **Canvas 2D API** — no image processing libraries, no third-party SDKs. Everything happens locally in your browser:

1. URL parameters are parsed on load and applied to state
2. The canvas is drawn: gradient → brand text → headline (auto-wrapped and auto-scaled, or manually sized)
3. `canvas.toDataURL('image/png')` produces the download
4. Google Fonts are fetched on demand and passed through `document.fonts.load()` before drawing to ensure the canvas sees the loaded typeface

In `raw=1` mode the UI is hidden and only the canvas is shown — making it embeddable as an `<img>` target on any same-origin page.

---

## 📄 License

MIT — do whatever you want with it.

---

## 🔒 Built by Lokkery

Quickbanner is a side tool built and open-sourced by **[Lokkery](https://lokkery.com)** — a shared development environment booking platform for software teams.

### What is Lokkery?

If your team shares staging servers, QA environments, or pre-production systems, you already know the problem: two developers deploy at the same time, someone's work gets overwritten, and half the morning is lost to a "who's using staging?" thread in Slack.

Lokkery fixes this with a **reservation system for your infrastructure** — like a calendar for your dev environments.

**Key capabilities:**

- **Environment booking** — reserve exclusive time-slotted access to any shared environment, eliminating conflicts before they happen
- **Team management** — assign environments to teams, manage members, and give everyone transparent visibility into who's booked what and when
- **CI/CD integration** — automation agents let pipelines programmatically reserve environments, so your deploy scripts and test runners play nicely with the rest of the team
- **Usage analytics** — real-time dashboard showing peak hours, utilization rates, and top users; right-size your infrastructure based on actual data rather than guesswork
- **Chrome extension** — book an environment in one click without leaving the browser

**Who it's for:** Engineering teams of 3+ people who share staging, QA, or pre-production environments and are tired of conflicts, wasted time, and "is anyone using X?" messages.

👉 **[lokkery.com](https://lokkery.com)**
