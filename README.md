# Download Speed Test

A clean, single-file website to check your **current download speed**, right in the browser. Dark mode, colorful gradient typography, and a live-updating speed readout in Mbps.

![Status](https://img.shields.io/badge/status-ready-2dd4bf) ![No Dependencies](https://img.shields.io/badge/dependencies-none-38bdf8) ![Single File](https://img.shields.io/badge/build-single%20HTML-a78bfa)

---

## ✨ Features

- 🌙 **Dark mode** UI with a glassy card, gradient border, and ambient glows
- 🎨 **Colorized fonts** — gradient title, big multi-color speed value, and accented labels
- ⚡ **Live download speed** that updates in real time as data streams in
- 📊 Final result showing total data downloaded and elapsed time
- 🔁 **Automatic fallback** to a second test server if the first fails
- 📦 **Single HTML file** — no frameworks, no build step, no dependencies
- 📱 Responsive and lightweight

---

## 🚀 Getting Started

1. Download or clone this repository.
2. Open **`speedtest.html`** in any modern web browser (Chrome, Edge, Firefox, Safari).
3. Click **Start Test** and wait a few seconds for your result.

> 💡 No installation or server required — just open the file.

---

## 🌐 Requirements

- A modern browser that supports the **Fetch API** and **ReadableStream**.
- An **active internet connection** (the test downloads a real file to measure throughput).

---

## ⚙️ How It Works

When you click **Start Test**, the page downloads a test file (~25 MB) from a public speed-test endpoint and measures how fast the bytes arrive:

1. A `fetch()` request streams the file body using a `ReadableStream` reader.
2. As each chunk arrives, the app tracks total bytes received and elapsed time.
3. Speed is calculated continuously:

   ```
   speed (Mbps) = (bytes received × 8) / elapsed seconds / 1,000,000
   ```

4. The on-screen number updates live and settles on your final download speed.

**Test servers used (with fallback):**

| Order | Source |
|-------|--------|
| 1 | `speed.cloudflare.com` |
| 2 | `proof.ovh.net` |

A cache-busting query parameter is added to each request to ensure fresh data is always downloaded.

---

## 🛠️ Customization

Everything lives in `speedtest.html`. A few easy tweaks:

- **Test file size** — change the `bytes=25000000` value in the `TEST_FILES` array (larger = more accurate on fast connections).
- **Colors** — edit the CSS variables at the top of the `<style>` block:
  ```css
  --accent:  #2dd4bf;  /* teal  */
  --accent2: #38bdf8;  /* blue  */
  --accent3: #a78bfa;  /* purple */
  ```
- **Test servers** — add or reorder URLs in the `TEST_FILES` array.

---

## 📁 Project Structure

```
.
├── speedtest.html   # The entire website (HTML + CSS + JS)
└── README.md        # This file
```

---

## ⚠️ Notes & Limitations

- Results depend on your network, the test server's load, and your geographic distance from it.
- For best accuracy, close other downloads/streams while testing and run the test more than once.
- This tool measures **download speed only** (no upload or ping).

---

## 📄 License

© **Bappa Ghosh**. All rights reserved.
