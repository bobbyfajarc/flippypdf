
# Flippy v1.0.0 - Modern PDF Viewer
> Ultra-fast PDF viewer dengan 3 mode tampilan — **100% Vanilla JS, NO jQuery!**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-red.svg)](https://github.com/bobbyfajarc/flippypdf)
[![Author](https://img.shields.io/badge/author-bobbyfajarc-orange.svg)](https://instagram.com/bobbyfajarc)
[![No jQuery](https://img.shields.io/badge/jQuery-NO-green.svg)](https://github.com/bobbyfajarc/flippypdf)

---

## ✨ Fitur Utama

- **Book Flip Mode** — Efek flip halaman 3D realistis seperti buku sungguhan  
- **Webtoon Mode** — Scroll vertikal (cocok untuk komik/manga digital)  
- **Single Mode** — Slide halaman satu per satu (horizontal)  

## 🚀 Keunggulan

- **Pure Vanilla JavaScript** — tanpa jQuery, tanpa bloat
- **Fast Rendering** — batch rendering stabil
- **Memory Efficient** — auto cleanup & revoke URL
- **Sharp Quality** — scale 2.0 + jpegQuality 0.92
- **Zoom & Pan** — support mouse & gesture
- **Mobile Optimized** — UI responsif, gesture friendly
- **Page Flip Sound** — efek suara realistik
- **Keyboard Shortcuts** — navigasi praktis
- **Multi-language** — ID, EN, JP, ZH
- **Fun Loading** — loading state dengan emoji
- **Sidebar Thumbnails** — daftar halaman

## 🌐 Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
- Mobile browsers (iOS Safari, Chrome Android)

---

## 📦 Struktur Project


flippypdf/
├── index.html            # Demo page
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


---

## ⚡ Quick Start

### Jalankan Server

**PHP**

cd path/to/flippypdf
php -S localhost:8000


**Python 3**

cd path/to/flippypdf
python -m http.server 8000


**Node.js**

npm install -g http-server
cd path/to/flippypdf
http-server -p 8000


**VS Code Live Server**
- Install extension "Live Server"
- Klik kanan `index.html` > Open with Live Server

---

### Buka di Browser

http://localhost:8000


---

## 🚀 Cara Penggunaan

### HTML Button (Data Attributes)

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


### JavaScript Full Options

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

- **Ubah warna:** edit di `dist/css/flippy.min.css`
- **Nonaktifkan suara:** `soundEnabled: false`
- **Ubah kualitas/grafik:** edit `scale`, `jpegQuality`, dll

---

## 🐛 Troubleshooting

- **"Gunakan web server"** — Jangan buka langsung file, gunakan server (PHP/Python/Node.js)
- **PDF tidak tampil** — Cek path: `example/sample.pdf`
- **Animasi laggy** — Turunkan scale/kualitas, close tab lain, gunakan Chrome/Edge

---

## 📄 License

**MIT License**  
Copyright (c) 2025 Bobby Fajar Christian  
[Full License](LICENSE)

---

## 👤 Author

- Bobby Fajar Christian  
- [@bobbyfajarc (Instagram)](https://instagram.com/bobbyfajarc)  
- [@bobbyfajarc (X/Twitter)](https://x.com/bobbyfajarc)  
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
- Full 3 mode tampilan  
- Demo page + sample.pdf  
- Multi-language & responsive  
- 100% vanilla, MIT license

---

Made with ❤️ in Jakarta, Indonesia  
_Last updated: 30 Oktober 2025_