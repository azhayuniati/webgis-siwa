# Candi Siwa — Virtual Tour

Virtual tour 3D interaktif Candi Siwa (Kompleks Prambanan) berbasis WebGL menggunakan Three.js.

## Struktur Folder

```
├── index.html      # Halaman utama (markup)
├── css/
│   └── style.css    # Seluruh styling tampilan (dark theme, UI panel, animasi)
├── js/
│   └── main.js       # Logic aplikasi: scene, kamera, kontrol orbit/street view, minimap, dll
├── library/           # Library pihak ketiga (di-host lokal, bukan CDN)
│   ├── three/          # Three.js r158 (core + GLTFLoader, DRACOLoader, BufferGeometryUtils)
│   └── three-mesh-bvh/ # Percepatan collision detection (BVH) untuk mode Street View
└── assets/
    └── candi_siwa.glb  # Model 3D hasil scan/modeling (~13MB)
```

## Cara Menjalankan

Karena menggunakan ES Modules, file harus dibuka lewat local server (tidak bisa dibuka langsung via `file://`):

```bash
python3 -m http.server 8000
# lalu buka http://localhost:8000
```

## Catatan

- Font (Google Fonts) dan Draco decoder (untuk kompresi model) tetap dimuat dari CDN eksternal saat runtime — butuh koneksi internet.
- Semua library Three.js sudah di-download lokal ke folder `library/` (versi three@0.158.0, three-mesh-bvh@0.7.4) agar tidak bergantung ke unpkg.com.
