# Embun

**Cermin kamera interaktif yang dapat berembun, ditulis dengan gerakan tangan, dan mengambil foto tanpa menyentuh layar.**

Embun berjalan langsung di browser. Buka mulut seperti sedang meniup kaca untuk menambahkan embun, lalu cubit ibu jari dan telunjuk untuk menulis atau menyeka permukaannya. Tidak memerlukan instalasi aplikasi, mikrofon, ataupun server pemrosesan video.

## Cara kerja

- **Buat embun dengan mulut** — buka mulut seperti sedang meniup kaca. Face Mesh mendeteksi bukaan mulut dan menambahkan embun lembut yang menyebar ke samping dan ke atas.
- **Tulis dengan cubitan** — satukan ibu jari dan telunjuk, lalu gerakkan tangan. Posisi dan status cubitan diperhalus agar garis lebih stabil.
- **Gunakan sentuhan sebagai alternatif** — pada ponsel, stylus, atau komputer, permukaan kaca juga dapat diseka langsung dengan drag.
- **Ambil foto tanpa menyentuh layar** — tahan kedua telapak tangan terbuka selama kurang lebih satu detik. Embun memulai hitung mundur `3 · 2 · 1`, lalu menampilkan hasil foto.
- **Simpan hasil** — setelah foto diambil, pilih **Simpan foto** untuk mengunduh PNG atau **Tutup** untuk kembali ke cermin.
- **Bersihkan atau kembali** — tombol **Bersihkan** menghapus embun, sedangkan **Kembali** menghentikan kamera dan membuka halaman awal.

## Menjalankan secara lokal

Browser hanya mengizinkan akses kamera melalui `localhost` atau HTTPS. Membuka `index.html` langsung melalui `file://` tidak disarankan.

```bash
cd embun
python3 -m http.server 4173 --directory dist
```

Kemudian buka:

```text
http://localhost:4173/
```

Izinkan akses kamera saat diminta. Chrome atau browser berbasis Chromium direkomendasikan untuk dukungan MediaPipe yang paling konsisten.

## Deployment

Embun adalah situs statis tanpa proses build. Folder yang perlu dipublikasikan adalah:

```text
dist/
```

Situs dapat dipasang di GitHub Pages, Vercel, Netlify, Cloudflare Pages, atau layanan hosting statis lain. Gunakan HTTPS agar izin kamera berfungsi.

## Teknologi

- HTML, CSS, dan JavaScript
- Canvas 2D untuk lapisan embun dan tulisan
- MediaPipe Hands untuk pelacakan tangan dan gestur cubit
- MediaPipe Face Mesh untuk mendeteksi bukaan mulut
- `getUserMedia` untuk kamera browser

MediaPipe dimuat dari CDN sehingga browser memerlukan koneksi internet saat pertama kali membuka aplikasi.

## Privasi

- Kamera diproses langsung di perangkat pengguna.
- Aplikasi tidak meminta akses mikrofon.
- Video dan landmark wajah/tangan tidak dikirim ke server proyek.
- Foto hanya dibuat di browser dan baru disimpan ketika pengguna menekan **Simpan foto**.

## Struktur proyek

```text
embun/
├── dist/
│   └── index.html
├── .openai/
│   └── hosting.json
└── README.md
```

## Catatan penggunaan

- Gunakan pencahayaan yang cukup agar tangan dan wajah mudah terdeteksi.
- Hadapkan telapak ke kamera saat menggunakan gestur foto.
- Jaga ibu jari dan telunjuk tetap terlihat ketika menulis.
- Jika pelacakan tidak tersedia, gunakan mouse atau sentuhan sebagai alternatif.

## Kredit

Konsepnya terinspirasi oleh eksperimen kreatif *breath mirror*, kemudian dikembangkan sebagai implementasi orisinal dengan antarmuka, perilaku embun, stabilisasi cubitan, dan alur foto sendiri.
