Berikut adalah **README.md** yang sudah **diperbaiki, rapi, dan siap digunakan** — langsung bisa **copy-paste ke editor** (seperti Notepad, VS Code, dll), lalu simpan dengan nama `README.md`.

---

# Flippy v1.0.0 - Modern PDF Viewer
> Ultra-fast PDF viewer dengan 3 mode tampilan - **100% Vanilla JS, NO jQuery!**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-red.svg)](https://github.com/bobbyfajarc/flippy-release)
[![Author](https://img.shields.io/badge/author-bobbyfajarc-orange.svg)](https://instagram.com/bobbyfajarc)
[![No jQuery](https://img.shields.io/badge/jQuery-NO-green.svg)](https://github.com/bobbyfajarc/flippy-release)

## Fitur Utama

Flippy adalah PDF viewer modern dengan dukungan **3 mode tampilan**:

- **Book Flip Mode** - Efek flip halaman 3D yang realistis seperti membaca buku sungguhan  
- **Webtoon Mode** - Scroll vertikal yang sempurna untuk komik, manga, dan konten digital  
- **Single Mode** - Mode slide horizontal untuk navigasi per halaman  

## Keunggulan

### Performance
- **Pure Vanilla JavaScript** - Tidak ada jQuery, tidak ada bloat  
- **Fast Rendering** - Sequential batch rendering untuk stabilitas  
- **Memory Efficient** - Aggressive memory cleanup & URL revocation  
- **Lightweight** - File JS hanya ~50KB  

### Features
- **Sharp Quality** - Scale 2.0 + 0.92 JPEG quality  
- **Zoom & Pan** - Scroll wheel untuk zoom, drag untuk pan saat zoomed  
- **Responsive Design** - Mobile-optimized UI  
- **Fun Loading Messages** - Loading dengan emoji yang menyenangkan  
- **Page Flip Sound** - Sound effect saat flip halaman  
- **Daftar Halaman** - Sidebar dengan thumbnail preview  
- **Keyboard Shortcuts** - Navigasi dengan keyboard  
- **Multi-language** - Dukungan ID, EN, JP, ZH  

### Browser Support
- Chrome 90+  
- Firefox 88+  
- Safari 14+  
- Edge 90+  
- Mobile browsers (iOS Safari, Chrome Android)

## Requirements

### Server
- Web server (PHP, Python, Node.js - **BUKAN file://**)  
- Minimal 50MB storage untuk PDF  

### Browser
- Modern browser dengan ES6 support  
- Internet connection (untuk load CDN)  

### CDN Dependencies (Tidak perlu install!)
- **Bootstrap 5.3.2** - UI framework  
- **PDF.js 3.11.174** - PDF rendering engine  
- **Remix Icons (Latest)** - Icon library  
- **Flag Icons 7.2.3** - Country flags  
- **Google Fonts (Inter)** - Typography  

## Quick Start

### 1. Download & Setup
```
flippy-optimized/
├── index.html          # File HTML utama
├── README.md           # Dokumentasi
├── LICENSE             # MIT License
├── dist/
│   ├── css/
│   │   └── flippy.min.css     # Styling Flippy (minified)
│   ├── js/
│   │   └── flippy.min.js      # Core library (minified)
│   └── sound/
│       └── turnPage.mp3       # Sound effect (optional)
└── example/
    └── sip.pdf                # PDF untuk testing
```

### 2. Jalankan Web Server

**Option 1: PHP (Recommended)**
```bash
cd path/to/flippy-optimized
php -S localhost:8000
```
Buka: http://localhost:8000

**Option 2: Python 3**
```bash
cd path/to/flippy-optimized
python -m http.server 8000
```
Buka: http://localhost:8000

**Option 3: Node.js**
```bash
npm install -g http-server
cd path/to/flippy-optimized
http-server -p 8000
```
Buka: http://localhost:8000

**Option 4: VS Code Live Server**
1. Install extension "Live Server" di VS Code  
2. Right-click `index.html`  
3. Pilih "Open with Live Server"  
4. Browser auto-open

### 3. Buka di Browser
http://localhost:8000

## Cara Penggunaan

### Setup CDN
```html
<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Flippy - PDF Viewer</title>
  <!-- Bootstrap 5.3.2 -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
  <!-- Remix Icons (Latest) -->
  <link href="https://cdn.jsdelivr.net/npm/remixicon@latest/fonts/remixicon.css" rel="stylesheet">
  <!-- Flippy CSS -->
  <link rel="stylesheet" href="dist/css/flippy.min.css">
</head>
<body>
  <!-- Tombol untuk buka PDF -->
  <button class="btn btn-primary" onclick="openPDF()">
    Buka PDF
  </button>

  <!-- Bootstrap JS Bundle -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
  <!-- PDF.js -->
  <script src="https://cdn.jsdelivr.net/npm/pdfjs-dist@3.11.174/build/pdf.min.js"></script>
  <script>
    if (typeof pdfjsLib !== 'undefined') {
      pdfjsLib.GlobalWorkerOptions.workerSrc =
        'https://cdn.jsdelivr.net/npm/pdfjs-dist@3.11.174/build/pdf.worker.min.js';
    }
  </script>
  <!-- Flippy JS -->
  <script src="dist/js/flippy.min.js"></script>
  <script>
    function openPDF() {
      const flippy = new Flippy({
        pdfUrl: 'example/your-file.pdf',
        mode: 'book', // 'book', 'webtoon', 'single'
        title: 'My PDF Document',
        soundEnabled: true
      });
      flippy.open();
    }
  </script>
</body>
</html>
```

### Konfigurasi Opsi
```js
const flippy = new Flippy({
  // Required
  pdfUrl: 'path/to/file.pdf',
  // Optional
  mode: 'book', // 'book' | 'webtoon' | 'single'
  title: 'PDF Viewer',
  scale: 2.0,           // Kualitas render (1.0 - 3.0)
  pageWidth: 450,       // Lebar halaman book mode (px)
  pageHeight: 600,      // Tinggi halaman book mode (px)
  minZoom: 0.5,
  maxZoom: 3.0,
  zoomStep: 0.1,
  soundEnabled: true,
  soundUrl: 'dist/sound/turnPage.mp3',
  parallelRender: 2,    // Parallel rendering (untuk stabilitas)
  jpegQuality: 0.92     // JPEG quality (0.0 - 1.0)
});
flippy.open();
```

## Keyboard Shortcuts

| Tombol         | Fungsi                              |
|----------------|-------------------------------------|
| `←` / `→`      | Halaman sebelumnya / berikutnya     |
| `Home`         | Halaman pertama                     |
| `End`          | Halaman terakhir                    |
| `Scroll Up`    | Zoom in (Book & Webtoon)            |
| `Scroll Down`  | Zoom out (Book & Webtoon)           |
| `ESC`          | Tutup viewer / Keluar fullscreen    |

## Mouse & Touch Controls

### Book Flip Mode
- Klik Sisi Kiri → Halaman sebelumnya  
- Klik Sisi Kanan → Halaman berikutnya  
- Hold & Drag → Pan saat zoomed  
- Mouse Wheel → Zoom in/out  
- Pinch (Mobile) → Zoom  

### Webtoon Mode
- Scroll Up/Down → Navigate pages  
- Mouse Wheel → Zoom in/out  
- Hold & Drag → Pan saat zoomed  

### Single Mode
- Tombol Next/Prev → Navigate halaman  
- Hold & Drag → Pan saat zoomed  
- Mouse Wheel → Zoom in/out  

## Customization

### Ubah Warna
Edit `dist/css/flippy.min.css`:
```css
/* Ubah warna primary (blue) */
:root {
  --primary-blue: #1E40AF; /* Ganti warna ini */
  --primary-blue-light: #3B82F6;
  --accent-cyan: #06B6D4;
  --bg-dark: #0F172A;
}
```

### Disable Sound
```js
const flippy = new Flippy({
  soundEnabled: false
});
```

### Adjust Kualitas
```js
const flippy = new Flippy({
  scale: 1.5,           // Lower = lebih cepat, Higher = lebih tajam
  jpegQuality: 0.85,    // Lower = lebih cepat, Higher = lebih bagus
  parallelRender: 4     // Higher = lebih cepat (gunakan lebih banyak RAM)
});
```

## Troubleshooting

| Error                        | Penyebab                          | Solusi                                                                 |
|-----------------------------|-----------------------------------|------------------------------------------------------------------------|
| "Gunakan web server"        | Membuka dengan `file://`          | Gunakan PHP/Python/Node.js                                             |
| "pdfjsLib is not defined"   | PDF.js gagal load dari CDN        | Cek internet, refresh, buka Console (F12)                              |
| "Cannot load PDF from..."   | Path salah atau file tidak ada    | Cek `example/`, nama file (case-sensitive)                         |
| Loading Lambat              | PDF besar atau kualitas tinggi    | Kurangi `scale` & `jpegQuality`, compress PDF (<10MB)                  |
| Animasi Laggy               | RAM penuh atau browser lambat     | Tutup tab, aktifkan hardware acceleration, gunakan Chrome/Edge        |

## API Reference

### Constructor
```js
const flippy = new Flippy(options)
```

### Methods
```js
flippy.open()
flippy.close()
flippy.nextPage()
flippy.prevPage()
flippy.firstPage()
flippy.lastPage()
flippy.goToPage(pageNumber)
flippy.zoomIn()
flippy.zoomOut()
flippy.toggleFullscreen()
```

### Events
```js
document.addEventListener('flippy:open', (e) => {
  console.log('Flippy opened');
});
document.addEventListener('flippy:close', (e) => {
  console.log('Flippy closed');
});
document.addEventListener('flippy:page-changed', (e) => {
  console.log('Page changed to:', e.detail.page);
});
```

## License

**MIT License**  
Copyright (c) 2025 Bobby Fajar Christian (@bobbyfajarc)  
[Full License](LICENSE)

## Author

**Bobby Fajar Christian**  
Instagram: [@bobbyfajarc](https://instagram.com/bobbyfajarc)  
Twitter/X: [@bobbyfajarc](https://x.com/bobbyfajarc)  
Facebook: [bobbyfajarc](https://facebook.com/bobbyfajarc)  
Location: Jakarta, Indonesia

## Credits
- [PDF.js](https://mozilla.github.io/pdf.js/) - Mozilla  
- [Bootstrap 5](https://getbootstrap.com/)  
- [Remix Icons](https://remixicon.com/)  

## Performance
- Bundle Size: ~50KB  
- Zero jQuery - Pure Vanilla JS  
- Memory Safe - Aggressive cleanup  
- Fast Loading - Sequential batch rendering  

## Changelog

**v1.0.0 (2025-10-30)**  
- First stable release  
- Book Flip Mode dengan 3D animation realistis  
- Webtoon Mode untuk continuous vertical scroll  
- Single Mode untuk horizontal slide  
- 100% Pure Vanilla JS (NO jQuery)  
- Click sides untuk flip halaman  
- Hold & drag untuk pan saat zoomed  
- Sharp quality rendering (scale 2.0)  
- Page flip sound effect  
- Multi-language support (ID, EN, JP, ZH)  
- Fully responsive & mobile-optimized  
- Fun loading messages dengan emoji  
- Aggressive memory cleanup  
- Complete documentation & examples  

---

**Made with love in Jakarta, Indonesia**  
**Last Updated: October 30, 2025**
```
