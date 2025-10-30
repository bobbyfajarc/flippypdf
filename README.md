# Flippy v1.0.0 - Modern PDF Viewer
> Ultra-fast PDF viewer dengan 3 mode tampilan — **100% Vanilla JS, NO jQuery!**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-red.svg)](https://github.com/bobbyfajarc/flippypdf)
[![Author](https://img.shields.io/badge/author-bobbyfajarc-orange.svg)](https://instagram.com/bobbyfajarc)
[![No jQuery](https://img.shields.io/badge/jQuery-NO-green.svg)](https://github.com/bobbyfajarc/flippypdf)

---

## 🧩 Pilihan Instalasi

Kamu bisa pakai **Flippy** dengan dua cara:

### 🔹 1. Local (Clone Project)
Clone repo ke lokal, lalu gunakan asset langsung dari folder `dist/`:

```bash
git clone https://github.com/bobbyfajarc/flippypdf.git
cd flippypdf
php -S localhost:8000
```

Gunakan di HTML:
```html
<link rel="stylesheet" href="dist/css/flippy.min.css">
<script src="dist/js/flippy.min.js"></script>
```

### 🔹 2. CDN (Auto Latest)
Gunakan langsung versi **terbaru** dari jsDelivr tanpa harus download:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/bobbyfajarc/flippypdf/dist/css/flippy.min.css">
<script src="https://cdn.jsdelivr.net/gh/bobbyfajarc/flippypdf/dist/js/flippy.min.js"></script>
```

> 💡 Flippy otomatis bisa deteksi mode *local* atau *cdn* jika kamu menambahkan URL param `?assets=cdn` atau `?assets=local`

---

## ⚡ Quick Start

### Jalankan Server

```
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

## 📄 License

**MIT License**  
Copyright (c) 2025 Bobby Fajar Christian  
[Full License](LICENSE)

---

Made with ❤️ in Jakarta, Indonesia  
_Last updated: 30 Oktober 2025_
