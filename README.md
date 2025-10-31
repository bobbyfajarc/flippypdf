
<p align="center">
  <img src="README.png" width="200" alt="Flippy Logo">
</p>

# **FlippyPDF — Modern PDF Viewer**
> ⚡ Ultra-fast PDF viewer dengan 3 mode tampilan — **100% Pure Vanilla JS, no framework**.

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-blue.svg">
  <img src="https://img.shields.io/badge/Version-1.0.0-red.svg">
  <img src="https://img.shields.io/badge/Pure%20JS-✓-brightgreen.svg">
  <img src="https://img.shields.io/badge/Made%20in-🇮🇩%20Indonesia-orange.svg">
  <img src="https://img.shields.io/badge/CDN-Ready-purple.svg">
</p>

---

## 🔎 Table of Contents
- [🎮 Demo (Try It First)](#-demo-try-it-first)
- [🔗 Required CDN](#-required-cdn)
- [🚀 Cara Penggunaan](#-cara-penggunaan)
  - [1) Init `.mode-btn` (WAJIB)](#1-init-mode-btn-wajib)
  - [2) HTML Button (Data Attributes)](#2-html-button-data-attributes)
  - [3) JavaScript (Full Options)](#3-javascript-full-options)
  - [4) Mode List](#4-mode-list)
  - [5) Keyboard Shortcuts](#5-keyboard-shortcuts)
- [⚙️ Setup & Quick Start](#️-setup--quick-start)
- [✨ Fitur Utama](#-fitur-utama)
- [🌐 Browser Support](#-browser-support)
- [📦 Struktur Project](#-struktur-project)
- [🛠️ Customization](#️-customization)
- [🐛 Troubleshooting](#-troubleshooting)
- [📄 License](#-license)
- [👤 Author](#-author)
- [🙏 Credits](#-credits)
- [📜 Changelog](#-changelog)

---

## 🎮 Demo (Try It First)
Di halaman contoh (`index.html`), **card demo** ada di atas: pilih **Book Flip / Webtoon / Single** dan klik **Buka PDF**.  
Contoh file demo: `example/limarayamusic.pdf`.

---

## 🔗 Required CDN
> Pakai Flippy di project lain? Include CDN ini.

**Bootstrap 5.3.2**
```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
```

**PDF.js 3.11.174 + Worker**
```html
<script src="https://cdn.jsdelivr.net/npm/pdfjs-dist@3.11.174/build/pdf.min.js"></script>
<script>
  if (typeof pdfjsLib !== 'undefined') {
    pdfjsLib.GlobalWorkerOptions.workerSrc =
      'https://cdn.jsdelivr.net/npm/pdfjs-dist@3.11.174/build/pdf.worker.min.js';
  }
</script>
```

**Remix Icons (latest)**
```html
<link href="https://cdn.jsdelivr.net/npm/remixicon@latest/fonts/remixicon.css" rel="stylesheet">
```

**Flippy (LOCAL)**
```html
<link rel="stylesheet" href="dist/css/flippy.min.css">
<script src="dist/js/flippy.min.js"></script>
```

**Flippy (CDN – Latest, no version)**
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/bobbyfajarc/flippypdf/dist/css/flippy.min.css">
<script src="https://cdn.jsdelivr.net/gh/bobbyfajarc/flippypdf/dist/js/flippy.min.js"></script>
```
---

## 🚀 Cara Penggunaan

### 1) Init `.mode-btn` (WAJIB)
Kalau kamu pakai button dengan class `.mode-btn`, bind dulu supaya klik-nya membuka viewer.
```html
<script>
document.addEventListener('DOMContentLoaded', () => {
  const ready = setInterval(() => {
    if (typeof pdfjsLib !== 'undefined' && typeof Flippy !== 'undefined') {
      clearInterval(ready);
      document.querySelectorAll('.mode-btn').forEach(btn => {
        btn.disabled = false;
        btn.addEventListener('click', () => {
          const pdf = btn.dataset.pdf;
          if (!pdf || !pdf.endsWith('.pdf')) return alert('❌ Invalid PDF file path');
          const flippy = new Flippy({
            pdfUrl: pdf,
            title: btn.dataset.title || 'PDF Viewer',
            mode: btn.dataset.mode || 'book',
            soundEnabled: true
          });
          flippy.open();
        });
      });
    }
  }, 200);
});
</script>
```

### 2) HTML Button (Data Attributes)
Cara paling cepat:
```html
<button class="btn btn-primary mode-btn"
        data-pdf="example/your-file.pdf"
        data-title="My PDF Document"
        data-mode="book"
        data-scale="2.0"
        data-page-width="450"
        data-page-height="600"
        data-sound-enabled="true"
        data-sound-url="dist/sound/turnPage.mp3">
  Buka PDF
</button>
```

**Available Data Attributes**
- `data-pdf` *(required)* — path PDF  
- `data-title` — judul dokumen  
- `data-mode` — `book` | `webtoon` | `single`  
- `data-scale` — 1.0–3.0  
- `data-page-width` / `data-page-height` — px  
- `data-sound-enabled` — `true|false`  
- `data-sound-url` — path MP3

### 3) JavaScript (Full Options)
```js
const flippy = new Flippy({
  // Required
  pdfUrl: 'example/your-file.pdf',

  // Display
  mode: 'book',               // 'book' | 'webtoon' | 'single'
  title: 'My PDF Document',

  // Render Quality
  scale: 2.0,                 // 1.0 - 3.0 (default: 2.0)
  jpegQuality: 0.92,          // 0.0 - 1.0 (default: 0.92)

  // Book Mode Size
  pageWidth: 450,
  pageHeight: 600,

  // Zoom
  minZoom: 0.5,
  maxZoom: 3.0,
  zoomStep: 0.1,

  // Performance
  parallelRender: 2,          // 1-4

  // Sound
  soundEnabled: true,
  soundUrl: 'dist/sound/turnPage.mp3'
});
flippy.open();
```

**All Available Options**
- `pdfUrl` *(string, required)*  
- `mode` *(string)* — `book|webtoon|single` (default: `book`)  
- `title` *(string)* — header title (default: `PDF Viewer`)  
- `scale` *(number)* — 1.0–3.0 (default: 2.0)  
- `jpegQuality` *(number)* — 0.0–1.0 (default: 0.92)  
- `pageWidth` / `pageHeight` *(number)* — px (default: 450 / 600)  
- `minZoom` / `maxZoom` / `zoomStep` *(number)* — zoom control  
- `parallelRender` *(number)* — 1–4 (default: 2)  
- `soundEnabled` *(boolean)* — default: `true`  
- `soundUrl` *(string)* — default: `dist/sound/turnPage.mp3`

### 4) Mode List
- `book` — 3D flip effect  
- `webtoon` — vertical scroll  
- `single` — horizontal slide

### 5) Keyboard Shortcuts
| Tombol      | Fungsi                         |
|-------------|--------------------------------|
| ← / →       | Halaman sebelumnya / berikutnya |
| Home / End  | Halaman pertama / terakhir     |
| Scroll      | Zoom in/out                    |
| Esc         | Tutup viewer                   |

---

## ⚙️ Setup & Quick Start

**Requirements**
- Web Server: PHP / Python / Node.js / VS Code Live Server  
- Browser: Chrome 90+, Firefox 88+, Safari 14+, Edge 90+  
- Internet (untuk CDN)  
- Storage: min 50MB untuk PDF

**Struktur Folder**
```
flippypdf/
├── index.html
├── LICENSE
├── README.md
├── dist/
│   ├── js/
│   │   └── flippy.min.js
│   ├── css/
│   │   └── flippy.min.css
│   └── sound/
│       └── turnPage.mp3
└── example/
    └── limarayamusic.pdf
```

**Jalankan Server**
```bash
# PHP
php -S localhost:8000

# Python 3
python -m http.server 8000

# Node.js
npm install -g http-server
http-server -p 8000
```

**VS Code Live Server**
- Install extension **Live Server**
- Right-click `index.html` → **Open with Live Server**

**Akses**
```
http://localhost:8000
```

---

## ✨ Fitur Utama
- 📖 **Book Flip Mode** (3D flip real)  
- 📜 **Webtoon Mode** (scroll vertikal)  
- 📄 **Single Mode** (1 halaman per view)  
- 🔊 Page flip sound  
- 🌏 Multi-language: **ID / EN / JA / ZH**  
- 📱 Mobile optimized, gestures & keyboard  
- 🧭 Sidebar thumbnails, zoom & pan, sharp render

---

## 🌐 Browser Support
- Chrome 90+ · Firefox 88+ · Safari 14+ · Edge 90+ · Mobile (iOS/Android)

---

## 📦 Struktur Project
```
flippypdf/
├── index.html
├── LICENSE
├── README.md
├── dist/
│   ├── js/
│   │   └── flippy.min.js
│   ├── css/
│   │   └── flippy.min.css
│   └── sound/
│       └── turnPage.mp3
└── example/
    └── limarayamusic.pdf
```

---

## 🛠️ Customization
- 🎨 **Ubah warna:** edit di `dist/css/flippy.min.css`  
- 🔇 **Nonaktifkan suara:** `soundEnabled: false`  
- 🖼️ **Atur kualitas render:** ubah `scale`, `jpegQuality`, dll

---

## 🐛 Troubleshooting
| Masalah               | Penyebab                          | Solusi                                        |
|-----------------------|-----------------------------------|-----------------------------------------------|
| "Gunakan web server"  | Dibuka via `file://`              | Jalankan via server (PHP/Python/Node/Live)    |
| PDF tidak tampil      | Path salah / file hilang          | Cek `example/limarayamusic.pdf`               |
| Animasi lag           | RAM/browser lambat                | Turunkan scale, tutup tab, gunakan Chrome     |

---

## 📄 License
**MIT License**  
Copyright (c) 2025 Bobby Fajar Christian  
[Full License](LICENSE)

---

## 👤 Author
- Bobby Fajar Christian  
- Instagram: https://instagram.com/bobbyfajarc  
- X (Twitter): https://x.com/bobbyfajarc  
- Jakarta, Indonesia

---

## 🙏 Credits
- PDF.js — https://mozilla.github.io/pdf.js/  
- Bootstrap 5 — https://getbootstrap.com/  
- Remix Icons — https://remixicon.com/

---


<p align="center">Made with ❤️ in Jakarta, Indonesia</p>
