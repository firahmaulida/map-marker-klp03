# Web GIS Sekolah di Banda Aceh

Aplikasi **Web GIS** berbasis browser untuk menampilkan sebaran data sekolah di Kota Banda Aceh secara interaktif menggunakan peta. Data bersumber dari **OpenStreetMap** dan ditampilkan menggunakan library **Leaflet.js**.

---

## Struktur Proyek

```
MK/
├── index.html          # Halaman utama aplikasi
├── style.css           # Stylesheet tampilan
└── data/
    └── data.geojson    # Data spasial sekolah (112 fitur)
```

---

## Fitur

- **Peta Interaktif** — Menampilkan lokasi sekolah dengan marker berwarna berdasarkan jenis sekolah
- **Pencarian Sekolah** — Cari sekolah berdasarkan nama atau atribut lainnya
- **Filter Jenis Sekolah** — Saring tampilan berdasarkan jenis: TK, SD, SMP, SMA, SMK, Universitas, dll.
- **Marker Clustering** — Marker dikelompokkan otomatis saat zoom keluar untuk kemudahan tampilan
- **Popup Informasi** — Klik marker untuk melihat detail lengkap sekolah
- **Info Panel** — Panel info tambahan yang muncul saat marker diklik
- **Pilihan Basemap** — Beralih antara OpenStreetMap dan Citra Satelit (Esri)
- **Skala Peta** — Kontrol skala ditampilkan di peta
- **Legenda** — Keterangan warna untuk setiap jenis sekolah

---

## Kode Warna Marker

| Warna      | Jenis Sekolah                   |
| ---------- | ------------------------------- |
| 🟣 Ungu    | TK (Taman Kanak-kanak)          |
| 🟢 Hijau   | SD (Sekolah Dasar)              |
| 🔵 Biru    | SMP (Sekolah Menengah Pertama)  |
| 🟡 Kuning  | SMA (Sekolah Menengah Atas)     |
| 🟠 Oranye  | SMK (Sekolah Menengah Kejuruan) |
| 🔴 Merah   | Universitas / Perguruan Tinggi  |
| ⚫ Abu-abu | Lainnya                         |

---

## Data

- **Sumber:** OpenStreetMap (via Overpass Turbo)
- **Format:** GeoJSON
- **Total Data:** 112 fitur sekolah
- **Wilayah:** Kota Banda Aceh

Distribusi jenis sekolah dalam data:

| Jenis   | Jumlah |
| ------- | ------ |
| SD      | 46     |
| SMA     | 15     |
| SMP     | 12     |
| SMK     | 4      |
| Lainnya | 35     |

> Data mendukung format geometri **Point**, **Polygon**, dan **MultiPolygon**. Polygon dan MultiPolygon secara otomatis dikonversi ke titik centroid untuk keperluan tampilan marker.

---

## Teknologi yang Digunakan

| Library                                                                   | Versi | Kegunaan                  |
| ------------------------------------------------------------------------- | ----- | ------------------------- |
| [Leaflet.js](https://leafletjs.com/)                                      | 1.9.4 | Rendering peta interaktif |
| [Leaflet.markercluster](https://github.com/Leaflet/Leaflet.markercluster) | 1.5.3 | Pengelompokan marker      |
| OpenStreetMap Tiles                                                       | —     | Basemap default           |
| Esri World Imagery                                                        | —     | Basemap citra satelit     |

Tidak ada dependensi tambahan yang perlu diinstall — semua library dimuat via CDN.

---

## Cara Menjalankan

Karena aplikasi memuat file `data.geojson` menggunakan `fetch()`, aplikasi harus dijalankan melalui web server lokal (tidak bisa langsung membuka file `index.html` di browser).

### Menggunakan Python

```bash
# Masuk ke folder proyek
cd MK

# Python 3
python -m http.server 8000
```

Kemudian buka browser dan akses: **http://localhost:8000**

### Menggunakan VS Code Live Server

Install ekstensi **Live Server** di VS Code, lalu klik kanan `index.html` → **Open with Live Server**.

### Menggunakan Node.js

```bash
npx serve .
```

---

## Cara Penggunaan

1. **Navigasi Peta** — Scroll untuk zoom, klik dan geser untuk panning
2. **Klik Marker** — Klik marker sekolah untuk melihat informasi detail
3. **Cari Sekolah** — Ketik nama sekolah di kolom pencarian, tekan **Enter**
4. **Filter Jenis** — Pilih jenis sekolah dari dropdown Filter untuk menyaring tampilan
5. **Ganti Basemap** — Gunakan kontrol layer (pojok kanan atas peta) untuk beralih antara OpenStreetMap dan Citra Satelit
6. **Sembunyikan Info Panel** — Klik area kosong di peta untuk menutup panel informasi

---
