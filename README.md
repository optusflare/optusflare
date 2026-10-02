# AstraSpec

**A free, browser-based PC diagnostic and toolkit — no installs, no accounts, nothing leaves your device.**

🌐 Live: [astraspec.vercel.app](https://astraspec.vercel.app)
🚀 Launching on Product Hunt — October 6th, 2026

---

## What is this?

AstraSpec is a single-page web app packed with 25+ tools for benchmarking your PC, testing your peripherals, checking your security, and optimizing your setup — all running entirely in your browser. Nothing is uploaded, nothing is tracked beyond anonymous page views, and there's nothing to download or install (unless you want the PWA — see below).

It started as a simple hardware benchmark page and grew from there.

---

## Features

### ⚡ Hardware Benchmark & System HUD
Live FPS counter, estimated refresh rate, CPU core count, RAM estimate, GPU renderer detection (via WebGL), screen resolution, and computed "gaming" and "productivity" scores.

### 🌐 Network
DNS provider directory (Cloudflare, Google, Quad9, AdGuard) with one-click IP copy and an approximate latency test, plus a rough network speed test.

### 🖱️ Peripherals Lab
Individual testers for:
- Keyboard (full key-press visualization)
- Mouse (click, scroll, movement tracking)
- Monitor (full-screen color swatches for dead-pixel/backlight checks)
- Headset / speakers (tone generator, left/right balance)
- Microphone (live waveform)
- Typing speed (WPM + accuracy)
- Color blindness (Ishihara-style screening plates)
- Battery health (Chrome/Edge only — the Battery API isn't exposed in Firefox/Safari)
- Reaction time

### 🔏 Privacy Hub
Client-side AES-256 encryption/decryption and a hash generator (SHA-256, SHA-512, MD5) — everything computed locally, nothing transmitted.

### 🔐 Security Toolkit
- Password strength tester
- Password generator (character-based or memorable passphrase mode)
- Password breach check — uses the [Have I Been Pwned Pwned Passwords API](https://haveibeenpwned.com/API/v3#PwnedPasswords) via k-anonymity, meaning only the first 5 characters of your password's hash are ever sent — your real password never leaves your browser
- Email breach check — built but requires a paid HIBP API key to activate (left unconfigured since that endpoint isn't free; the UI says so honestly instead of pretending to work)
- Browser fingerprint viewer — shows you exactly what sites can silently read about your browser
- Username search across common platforms
- Full privacy report (your public IP, approximate location, and browser exposure, via a public IP geolocation API)
- QR code generator
- Password-protected encrypted notes
- A transparency panel showing exactly what AstraSpec itself has stored in your browser's local storage, with a one-click "clear everything" option

### ❤️ Health Score
Combines your Benchmark and Security-tool usage into a single session grade.

### 🖥️ Optimization Guides
Step-by-step performance guides for Windows, Linux, and macOS, with embedded video walkthroughs and realistic (not fabricated) FPS gain ranges.

### 💿 Change Your OS
A general, OS-agnostic guide to doing a clean install from a USB drive (Rufus/balenaEtcher, BIOS/UEFI boot order, Secure Boot).

### 💻 Terminal
A themed, simulated shell — try `help`, `neofetch`, `sudo`, `theme retro`, and a few hidden ones if you go looking.

### 🎮 Games
- **Flappy Byte** — pick Windows, macOS, or Tux and flap through pipes
- **Glide** — an original flying-ship dodge mode
- **Aim Trainer** — click targets fast, tracks accuracy and reaction time
- **Crosshair Generator** — design and export a custom crosshair as a PNG
- **Frame Pacing Visualizer** — a side-by-side demo of smooth vs. stuttery frame pacing

### 🧰 Dev & Utility Toolkit
JSON formatter/validator, Base64/URL encoder-decoder, a unit converter (GB↔GiB, Mbps↔MB/s, Hz↔ms), a resolution/DPI simulator, and an ASCII art generator.

### 🧮 Quick Tools
World clock, "is it down?" reachability checker, in-site clipboard history, live weather, currency converter, bill splitter, and a speech-to-text / text-to-speech demo.

### 🏆 Achievements
Ten unlockable badges tracked locally as you try different tools — includes a working [Konami code](https://en.wikipedia.org/wiki/Konami_Code) easter egg.

### 🎨 Extras
Retro/CRT visual mode, an optional cursor-trail effect, and a site-wide search bar (press `/` to focus it) that jumps straight to any tool.

---

## Tech stack

**No frameworks. No build step. No bundler.** Just HTML, CSS, and vanilla JavaScript in a single `index.html`, deployed as a static site.

- Canvas 2D for all visualizations (particle backgrounds, benchmark wireframe, games)
- Web Crypto API for AES-GCM encryption and SHA hashing
- Web Audio API for the tone generator and mic waveform
- Web Speech API for speech-to-text / text-to-speech
- `localStorage` for achievements, high scores, and user preferences (everything stays on your device)
- A real [Service Worker](./sw.js) + [Web App Manifest](./manifest.json) make it installable as a Progressive Web App

### Why no framework?
Keeping it dependency-free means zero build step, instant deploys, and anyone can view-source the entire thing and understand it. That tradeoff was intentional.

---

## 📲 Installing as an app (PWA)

AstraSpec is a full Progressive Web App — you can install it like a real desktop/mobile app:

- **Desktop (Chrome/Edge):** look for the install icon in the address bar, or use the browser menu → "Install AstraSpec"
- **Android (Chrome):** menu → "Add to Home screen" / "Install app"
- **iOS (Safari):** tap Share → "Add to Home Screen"

Once installed, it opens in its own window with no browser UI, and has basic offline support via its service worker.

---

## Running it locally

There's nothing to build. Clone the repo and open `index.html` in a browser, or serve it with any static file server:

```bash
git clone https://github.com/optusflare/optusflare.git
cd optusflare
npx serve .
```

That's it — no `npm install`, no config.

---

## Deployment

Currently deployed on [Vercel](https://vercel.com) as a static site, auto-deploying from the `main` branch. Also includes:

- `sitemap.xml` and `robots.txt` for search engine crawling
- Full Open Graph / Twitter Card metadata, a `WebSite` + `WebApplication` JSON-LD schema, and a Google Search Console verification tag
- A proper multi-format favicon setup (SVG for modern browsers, PNG + ICO for search engines and legacy support — Google Search specifically does not support SVG favicons)
- A custom 404 page
- [Vercel Web Analytics](https://vercel.com/docs/analytics), privacy-friendly and cookie-free

---

## Feedback

Found a bug, have an idea, or just want to say something? There's a feedback form right in the **Roadmap** section of the site — every submission goes straight to the maker via [Formspree](https://formspree.io).

You can also open an [issue](https://github.com/optusflare/optusflare/issues) directly on this repo.

---

## Roadmap

See the in-app **Roadmap & Changelog** section for the full shipped/planned history. In short:

- **v1.0** — Hardware benchmark, DNS directory, keyboard/display/audio testing, encryption, hashing
- **v1.1** — Security Toolkit: password strength, breach checking, fingerprinting, username search
- **v2.0** — The big expansion: Optimization guides, Change OS, Terminal, Games, Health Score, Network Speed Test, QR Generator, Achievements, Retro Mode, full per-device Peripheral testing, and everything in between

---

## A note on honesty

A few things worth knowing, in the spirit of not overselling what this is:

- The "ping" / latency tests are approximate — browser JavaScript cannot send a real ICMP ping, so these are measured round-trip HTTP timings instead, and the UI says so.
- The Email Breach Check tool is intentionally left unconfigured, since the underlying API isn't free — it tells you that honestly rather than faking a result.
- The Terminal is a themed simulation, not real shell access to anything.
- Optimization guide FPS numbers are realistic ranges based on general, well-established tuning knowledge — not a benchmark run on your exact hardware.

---

## License

This project is personal/independent work. Feel free to look around, learn from it, or reach out with feedback — see the Feedback section above.

---

Built by a solo developer who kept thinking "oh, that'd be cool too" until it turned into this. 🌌
