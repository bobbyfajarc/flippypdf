# Flippy v1.0.0 · Modern PDF Viewer
> Ultra‑fast, touch‑friendly, **100% Vanilla JS** PDF viewer with 3 display modes. No jQuery, no bloat.

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-red.svg)](https://github.com/bobbyfajarc/flippypdf)
[![Author](https://img.shields.io/badge/author-bobbyfajarc-orange.svg)](https://instagram.com/bobbyfajarc)
[![No jQuery](https://img.shields.io/badge/jQuery-NO-green.svg)](https://github.com/bobbyfajarc/flippypdf)
[![Made in Jakarta](https://img.shields.io/badge/Made%20in-Jakarta-ff69b4.svg)](#)
[![JS Only](https://img.shields.io/badge/Runtime-JavaScript-informational.svg)](#)

---

<p align="center">
  <img src="https://raw.githubusercontent.com/placeholder/flippypdf-assets/main/cover.png" alt="Flippy PDF Viewer cover" width="820" />
</p>

<p align="center">
  <b>Book Flip</b> · <b>Webtoon</b> · <b>Single</b><br/>
  Zoom • Pan • Thumbnails • Keyboard Shortcuts • Page Flip Sound
</p>

---

## 🧭 Daftar Isi
- [Fitur Utama](#-fitur-utama)
- [Keunggulan](#-keunggulan)
- [Demo Cepat](#-demo-cepat)
- [Instalasi](#-instalasi)
  - [Via CDN](#via-cdn)
  - [Local Dev Server](#local-dev-server)
- [Pemakaian](#-pemakaian)
  - [HTML Data Attributes](#html-data-attributes)
  - [JavaScript (Full Options)](#javascript-full-options)
- [Keyboard Shortcuts](#-keyboard-shortcuts)
- [Kustomisasi](#-kustomisasi)
- [Browser Support](#-browser-support)
- [Struktur Project](#-struktur-project)
- [Troubleshooting](#-troubleshooting)
- [Roadmap](#-roadmap)
- [Kontribusi](#-kontribusi)
- [Lisensi](#-lisensi)
- [Kredit](#-kredit)
- [Changelog](#-changelog)

---

## ✨ Fitur Utama
- **Book Flip Mode** — Efek flip halaman 3D realistis seperti buku sungguhan.
- **Webtoon Mode** — Scroll vertikal mulus; ideal untuk komik/manga.
- **Single Mode** — Slide halaman satu‑per‑satu secara horizontal.
- **Sidebar Thumbnails** — Pratinjau cepat semua halaman.
- **Zoom & Pan** — Mouse, trackpad, dan gesture mobile.
- **Keyboard Shortcuts** — Navigasi ringkas untuk power users.
- **Page Flip Sound** — Suara realistis (opsional).
- **Multi‑language** — ID, EN, JP, ZH.
- **Mobile Optimized** — UI responsif, gesture‑friendly.

## 🚀 Keunggulan
- **Pure Vanilla JS** — Tanpa jQuery, tanpa dependency berat.
- **Fast Rendering** — Batch rendering stabil untuk PDF panjang.
- **Memory Efficient** — Auto cleanup & `URL.revokeObjectURL()`.
- **Sharp Quality** — `scale: 2.0` + `jpegQuality: 0.92` (tweakable).
- **Lightweight** — Hanya file CSS/JS + aset suara.

---

## 🧪 Demo Cepat
Buka `index.html` di server lokal atau Live Server VS Code untuk melihat ketiga mode sekaligus.

```bash
# PHP
php -S localhost:8000

# Python 3
python -m http.server 8000

# Node.js
npm i -g http-server
http-server -p 8000
```

Lalu akses: `http://localhost:8000`

---

## 📦 Instalasi

### Via CDN
Copy–paste dan ganti `pdfUrl` sesuai berkas Anda.

```html
<!-- Flippy CSS & JS via jsDelivr CDN -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/bobbyfajarc/flippypdf@v1.0.0/dist/css/flippy.min.css">
<script src="https://cdn.jsdelivr.net/gh/bobbyfajarc/flippypdf@v1.0.0/dist/js/flippy.min.js"></script>
<script>
  const flippy = new Flippy({
    pdfUrl: 'example/sample.pdf',
    soundUrl: 'https://cdn.jsdelivr.net/gh/bobbyfajarc/flippypdf@v1.0.0/dist/sound/turnPage.mp3'
  });
</script>
```

### Local Dev Server
- **VS Code Live Server** → klik kanan `index.html` → *Open with Live Server*
- Atau gunakan salah satu perintah server di atas.

---

## 🧰 Pemakaian

### HTML Data Attributes
Gunakan tombol yang memanggil viewer dengan konfigurasi via atribut data.

```html
<button class="mode-btn"
        data-pdf="example/sample.pdf"
        data-title="Demo PDF"
        data-mode="book"           <!-- 'book' | 'webtoon' | 'single' -->
        data-scale="2.0"
        data-page-width="450"
        data-page-height="600"
        data-sound-enabled="true"
        data-sound-url="dist/sound/turnPage.mp3">
  Buka PDF
</button>
```

### JavaScript (Full Options)
API ringkas dengan opsi granular untuk performa & kualitas.

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

> **Tip performa:** Kurangi `scale` atau tingkatkan `parallelRender` sesuai kemampuan perangkat. Untuk PDF ultra‑panjang, gunakan `webtoon` agar scrolling lebih stabil.

---

## 🎹 Keyboard Shortcuts

| Tombol        | Fungsi                                  |
|---------------|------------------------------------------|
| ← / →         | Halaman sebelumnya / berikutnya          |
| Home / End    | Halaman pertama / terakhir               |
| Wheel / Pinch | Zoom in / out                            |
| Esc           | Tutup viewer / keluar fullscreen         |

---

## 🎨 Kustomisasi
- **Warna & tema** → edit `dist/css/flippy.min.css`.
- **Matikan suara** → `soundEnabled: false`.
- **Kualitas render** → atur `scale` & `jpegQuality`.
- **Ukuran halaman default** → `pageWidth` & `pageHeight`.

---

## 🌐 Browser Support
- Chrome 90+, Edge 90+, Firefox 88+, Safari 14+
- iOS Safari & Chrome Android (teroptimasi sentuhan)

> Catatan: Kinerja dapat bervariasi pada perangkat low‑end. Gunakan `scale` lebih kecil bila perlu.

---

## 🗂️ Struktur Project

```
flippypdf/
├── index.html           # Demo page
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

## 🛠️ Troubleshooting

| Masalah               | Penyebab                           | Solusi                                         |
|-----------------------|------------------------------------|-----------------------------------------------|
| “Gunakan web server”  | Buka file langsung (`file://`)     | Jalankan server (PHP/Python/Node/Live Server) |
| PDF tidak tampil      | Path salah / file hilang           | Pastikan path benar & `example/sample.pdf` ada |
| Animasi lag           | Perangkat/Browser kewalahan        | Turunkan `scale`, tutup tab lain, coba Chrome/Edge |
| Suara tidak muncul    | File audio tidak termuat           | Periksa `soundUrl`, pastikan HTTPS & CORS     |

---

## 🗺️ Roadmap
- [ ] Event hooks (`onOpen`, `onPageChange`, `onClose`)
- [ ] Lazy thumbnail generation
- [ ] Theme system (light/dark)
- [ ] Accessibility labels (improved ARIA hints)

---

## 🤝 Kontribusi
PR & issue dipersilakan. Gunakan bahasa yang jelas, sertakan langkah reproduksi, dan screenshot bila relevan.

```bash
# Clone
git clone https://github.com/bobbyfajarc/flippypdf
cd flippypdf

# (opsional) jalankan server lokal seperti di bagian Demo
```

---

## 📄 Lisensi
**MIT License** © 2025 Bobby Fajar Christian — Lihat [LICENSE](LICENSE) untuk detail.

---

## 🙏 Kredit
- [PDF.js](https://mozilla.github.io/pdf.js/)
- [Bootstrap 5](https://getbootstrap.com/)
- [Remix Icons](https://remixicon.com/)

---

## 📜 Changelog
**v1.0.0 — 30 Oktober 2025**  
- Rilis stabil pertama  
- Tiga mode tampilan: *book*, *webtoon*, *single*  
- Demo page + `sample.pdf`  
- Multi‑language & responsif  
- 100% Vanilla JS, MIT License

---

<p align="center">Made with ❤️ in Jakarta, Indonesia<br/><em>Last updated: 30 Oktober 2025</em></p>
