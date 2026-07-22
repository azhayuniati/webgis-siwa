# WebGIS Candi Siwa Prambanan

Ini adalah hasil compile langsung dari source code React asli project kalian
(`artifacts/webgis-prambanan`), jadi tampilan & fungsinya **sama persis** dengan
website aslinya — bukan ditulis ulang dari mockup.

## Struktur Folder

```
webgis-siwa/
├── index.html          → halaman utama (isi/DOM di-render oleh app.js)
├── css/
│   └── style.css        → seluruh styling (hasil compile Tailwind CSS)
├── lib/
│   └── app.js             → seluruh kode aplikasi + library (React, Leaflet,
│                            Framer Motion, Radix UI, dll) dibundel jadi satu file
├── favicon.svg
├── opengraph.jpg
└── robots.txt
```

## Cara Menjalankan

Karena ini React yang sudah di-build, jalankan lewat local server (bukan
dobel klik langsung ke index.html), contoh:

```bash
npx serve .
# atau
python3 -m http.server 8080
```

lalu buka `http://localhost:8080` di browser. Live Server di VS Code juga
bisa dipakai seperti biasa.

## Kenapa Isinya Beda dari Percobaan Sebelumnya?

Di project asli ternyata ada 2 versi:
1. File HTML/CSS statis polos di `attached_assets/` — cuma **rancangan awal**
   yang dipakai sebagai referensi desain (foto-fotonya juga belum ada/broken).
2. Aplikasi React lengkap di `artifacts/webgis-prambanan/` — ini yang jadi
   **website final** yang kalian pakai (pakai Tailwind, Framer Motion, Radix UI).

Percobaan pertama salah ambil yang nomor 1, makanya tampilannya beda jauh.
Versi ini di-build langsung dari source code nomor 2, jadi dijamin identik
dengan yang biasa kalian lihat.

## Kenapa Sempat Kosong Waktu Dibuka Lewat Live Server?

Ini bug dari versi build sebelumnya, sudah diperbaiki. Penyebabnya: web ini
React SPA yang pakai library routing (`wouter`). Router-nya semula cuma
dikonfigurasi mengenali alamat `/`, jadi begitu dibuka lewat URL yang eksplisit
menyertakan nama file (`.../index.html`, seperti yang otomatis dibuat "Open
with Live Server" di VS Code), router-nya menganggap itu halaman tak dikenal
dan tidak merender apa-apa. Sudah ditambahkan route tambahan untuk
`/index.html` di source code sebelum di-build ulang, supaya tetap merender
halaman utama baik diakses lewat `/` maupun `/index.html`.

Sudah dites otomatis pakai headless browser (buka persis lewat URL
`.../index.html`) dan halaman tampil lengkap.

## Library / Teknologi yang Dipakai

- **React 19** + **wouter** (routing) + **Tailwind CSS v4**
- **Leaflet.js 1.9.4** — peta interaktif
- **Framer Motion**, **Radix UI**, **lucide-react** — animasi & komponen UI
- Semua di atas dibundel jadi satu file `lib/app.js` lewat Vite (build tool
  React), bukan ditulis manual — ini normal untuk aplikasi React yang sudah
  di-build untuk production.
- Tile peta: OpenStreetMap, Esri World Imagery, OpenTopoMap — dimuat langsung
  dari server penyedia peta saat aplikasi jalan (wajar untuk WebGIS).
