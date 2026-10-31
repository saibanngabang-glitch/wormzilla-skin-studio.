# Wormzilla Skin Studio

Editor tekstur berbasis HTML Canvas, berjalan lokal di browser tanpa API, login, atau backend. Ekspor utama dirender langsung pada Canvas **1500 × 500 px** menjadi PNG.

## Menjalankan lokal

1. Unduh/ekstrak folder proyek.
2. Buka `index.html` di Chrome, Safari, atau browser modern. Karena ini aplikasi statis tanpa modul JavaScript, tidak wajib menjalankan server.
3. Untuk workflow lokal yang lebih konsisten, jalankan server statis dari folder proyek:

   ```bash
   python -m http.server 8000
   ```

   lalu buka `http://localhost:8000`.

## Deploy ke GitHub dan Vercel

1. Buat repository baru di GitHub.
2. Unggah `index.html`, folder `src/`, `README.md`, dan `vercel.json`.
3. Di Vercel pilih **Add New → Project**, impor repository GitHub.
4. Framework preset pilih **Other**. Build command dan output directory tidak diperlukan untuk situs statis; jika diminta, gunakan output directory `.`.
5. Deploy. Setiap push ke branch produksi akan memicu deployment baru.

Tidak ada dependency atau API key.

## Fitur

- 15 algoritma kategori tekstur Canvas, seed untuk pola deterministik, kontrol warna/pola/komposisi, kunci randomisasi, palet siap pakai.
- Editor teks/logo, layer visibility/opacity, gambar logo PNG/SVG, gambar referensi PNG/JPEG/WebP, undo/redo, localStorage, impor/ekspor konfigurasi JSON, galeri perangkat.
- Ekspor PNG dirender ulang di Canvas 1500 × 500; pratinjau tidak dipakai sebagai sumber ekspor.
- Antarmuka responsif untuk desktop dan mobile, tema terang/gelap, kontrol zoom dan fullscreen.

## Catatan teknis

- Data gambar referensi dan logo yang diunggah tidak disimpan ke localStorage atau ke file JSON proyek; file perlu diunggah ulang setelah memuat proyek. Parameter dan seed tetap disimpan.
- Seed dan parameter pola menghasilkan gambar pola dasar deterministik. Jika memakai gambar referensi atau logo yang diunggah, hasil lengkap bergantung pada file lokal yang diunggah ulang.
- PNG adalah tekstur datar. Kompatibilitas dengan format skin Wormzilla tertentu tidak diklaim tanpa spesifikasi format resmi.
- Perilaku unduhan di iOS dapat berbeda menurut versi Safari; jika unduhan tidak langsung dimulai, buka file hasil ekspor dari pratinjau/daftar unduhan browser.

## Pengujian dasar

Buka halaman dan pastikan tombol RANDOM SKIN mengubah pola/seed; pilih kategori berbeda untuk melihat algoritma masing-masing; ubah warna; coba kunci warna/pola/kepadatan; gunakan undo/redo; simpan/muat proyek; tambahkan dan geser teks logo; ekspor PNG lalu periksa dimensinya di properti file. Kode ekspor membuat canvas baru dengan lebar 1500 dan tinggi 500, terlepas dari ukuran pratinjau.
