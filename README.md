<p align="center">
  <img src="README.png" width="200" alt="Flippy Logo">
</p>

# **Flippy — The Modern PDF Viewer**
> ✨ Ultra-fast, cinematic PDF viewer dengan 3 mode tampilan — **100% Pure Vanilla JS, tanpa framework!**

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-blue.svg">
  <img src="https://img.shields.io/badge/Version-1.0.0-red.svg">
  <img src="https://img.shields.io/badge/Pure%20JS-✓-brightgreen.svg">
  <img src="https://img.shields.io/badge/Made%20in-🇮🇩%20Indonesia-orange.svg">
  <img src="https://img.shields.io/badge/CDN-Ready-purple.svg">
</p>

---

## 📖 Table of Contents
- [✨ Fitur Utama](#-fitur-utama)
- [🚀 Keunggulan](#-keunggulan)
- [🌐 Browser Support](#-browser-support)
- [📦 Struktur Project](#-struktur-project)
- [🧩 Pilihan Instalasi](#-pilihan-instalasi)
- [⚡ Quick Start](#-quick-start)
- [🔗 CDN Link (Local & CDN)](#-cdn-link-local--cdn)
- [🚀 Cara Penggunaan](#-cara-penggunaan)
- [🎹 Keyboard Shortcuts](#-keyboard-shortcuts)
- [💻 Customization](#-customization)
- [🐛 Troubleshooting](#-troubleshooting)
- [📄 License](#-license)
- [👤 Author](#-author)
- [🙏 Credits](#-credits)
- [📜 Changelog](#-changelog)

---

## ✨ Fitur Utama
- 📖 **Book Flip Mode** — efek halaman 3D realistis seperti buku sungguhan  
- 📜 **Webtoon Mode** — scroll vertikal (cocok untuk komik/manga digital)  
- 📄 **Single Mode** — tampil satu halaman per view (slide horizontal)

---

## 🚀 Keunggulan
- ⚡ **Pure Vanilla JavaScript** — tanpa jQuery, tanpa bloat
- 🧠 **Fast Rendering** — batch rendering stabil
- 💾 **Memory Efficient** — auto cleanup & revoke URL
- 🖼️ **Sharp Quality** — scale 2.0 + jpegQuality 0.92
- 🤏 **Zoom & Pan** — support mouse & gesture
- 📱 **Mobile Optimized** — UI responsif & gesture friendly
- 🔊 **Page Flip Sound** — efek suara realistik
- ⌨️ **Keyboard Shortcuts** — navigasi praktis
- 🌏 **Multi-language** — ID, EN, JP, ZH
- 😄 **Fun Loading** — emoji loading state
- 🧭 **Sidebar Thumbnails** — daftar halaman interaktif

---

## 🌐 Browser Support
- Chrome 90+  
- Firefox 88+  
- Safari 14+  
- Edge 90+  
- Mobile browsers (iOS Safari, Chrome Android)

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
    └── sample.pdf
```

---

## 🧩 Pilihan Instalasi

Kamu bisa pakai **Flippy** dengan dua cara — offline (Local) atau online (CDN).

### 🧱 1. Local (Clone Project)
Untuk pengembangan lokal atau offline:

```bash
git clone https://github.com/bobbyfajarc/flippypdf.git
cd flippypdf
php -S localhost:8000
```

Tambahkan ke HTML:
```html
<link rel="stylesheet" href="dist/css/flippy.min.css">
<script src="dist/js/flippy.min.js"></script>
```

---

### ☁️ 2. CDN (Auto Latest)
Gunakan versi **terbaru otomatis** tanpa perlu download:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/bobbyfajarc/flippypdf/dist/css/flippy.min.css">
<script src="https://cdn.jsdelivr.net/gh/bobbyfajarc/flippypdf/dist/js/flippy.min.js"></script>
```

> 💡 Gunakan `?assets=cdn` atau `?assets=local` pada URL untuk auto-switch mode asset.

---

## ⚡ Quick Start

### Jalankan Server

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
- Klik kanan **index.html** → Open with Live Server

---

### Buka di Browser

```
http://localhost:8000
```

---

## 🔗 CDN Link (Local & CDN)

### 🔹 LOCAL
```html
<link rel="stylesheet" href="dist/css/flippy.min.css">
<script src="dist/js/flippy.min.js"></script>
```

### 🔹 CDN (Latest)
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/bobbyfajarc/flippypdf/dist/css/flippy.min.css">
<script src="https://cdn.jsdelivr.net/gh/bobbyfajarc/flippypdf/dist/js/flippy.min.js"></script>
```

> 🧠 Tips: Versi CDN selalu auto-update ke versi terbaru tanpa ubah tag.

---

## 🚀 Cara Penggunaan

### 🧩 HTML Button (Data Attributes)
Cara termudah: cukup tambahkan atribut data di HTML button.

```html
<button class="mode-btn"
        data-pdf="example/sample.pdf"
        data-title="Demo PDF"
        data-mode="book"
        data-scale="2.0"
        data-page-width="450"
        data-page-height="600"
        data-sound-enabled="true"
        data-sound-url="dist/sound/turnPage.mp3">
    Buka PDF
</button>
```

### 💻 JavaScript (Full Options)
Gunakan jika butuh kontrol penuh:

```js
const flippy = new Flippy({
  pdfUrl: 'example/sample.pdf',
  mode: 'book',           // 'book' | 'webtoon' | 'single'
  title: 'Demo PDF',
  scale: 2.0,
  pageWidth: 450,
  pageHeight: 600,
  minZoom: 0.5,
  maxZoom: 3.0,
  zoomStep: 0.1,
  soundEnabled: true,
  soundUrl: 'dist/sound/turnPage.mp3',
  parallelRender: 2,
  jpegQuality: 0.92
}); 
flippy.open();
```

---

## 🎹 Keyboard Shortcuts

| Tombol           | Fungsi                                 |
|------------------|----------------------------------------|
| ← / →            | Halaman sebelumnya / berikutnya        |
| Home / End       | Halaman pertama / terakhir             |
| Mouse Wheel      | Zoom in/out                            |
| Esc              | Tutup viewer / exit fullscreen         |

---

## 💻 Customization
- 🎨 **Ubah warna:** edit di `dist/css/flippy.min.css`  
- 🔇 **Nonaktifkan suara:** `soundEnabled: false`  
- 🖼️ **Atur kualitas render:** ubah `scale`, `jpegQuality`, dll

---

## 🐛 Troubleshooting

| Masalah               | Penyebab                          | Solusi                                        |
|-----------------------|-----------------------------------|-----------------------------------------------|
| "Gunakan web server"  | File dibuka langsung (`file://`)  | Jalankan via server (PHP/Python/Node/Live)   |
| PDF tidak tampil      | Path salah / file hilang          | Cek `example/sample.pdf` dan nama file        |
| Animasi lag           | RAM/browser lambat                | Turunkan scale, tutup tab, gunakan Chrome     |

---

## 📄 License
**MIT License**  
Copyright (c) 2025 Bobby Fajar Christian  
[Full License](LICENSE)

---

## 👤 Author
- Bobby Fajar Christian  
- [Instagram @bobbyfajarc](https://instagram.com/bobbyfajarc)  
- [X (Twitter) @bobbyfajarc](https://x.com/bobbyfajarc)  
- Jakarta, Indonesia

---

## 🙏 Credits
- [PDF.js](https://mozilla.github.io/pdf.js/)  
- [Bootstrap 5](https://getbootstrap.com/)  
- [Remix Icons](https://remixicon.com/)

---

## 📜 Changelog
**v1.0.0 — 30 Oktober 2025**  
- First stable release  
- 3 display modes (Book/Webtoon/Single)  
- Multi-language & responsive  
- 100% Pure JS, MIT licensed

---

<p align="center">Made with ❤️ in Jakarta, Indonesia</p>
