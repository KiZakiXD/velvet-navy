# Velvet Navy — Undangan Pernikahan Digital

Template undangan pernikahan digital satu file HTML dengan gaya editorial majalah: bab bernomor, tipografi serif elegan, palet navy & emas. Bahasa Indonesia formal.

Satu folder ini adalah satu undangan utuh yang **standalone** — tanpa server, tanpa database, tanpa akun apa pun. Upload ke hosting statis mana pun dan undangan langsung jalan.

## Fitur

- Cover tirai belah dengan efek pintu 3D, bab 01–08 ala majalah, kalender bulan acara, countdown, partikel debu emas melayang, pita awan di dasar hero.
- Nama tamu personal di sampul (dari link `?to=Nama+Tamu`) + tombol bagikan WhatsApp.
- Musik latar (MP3 di folder `audio/`, bisa diganti), tombol musik melayang.
- Galeri foto, kisah cinta, info akad & resepsi, peta Google Maps + QR lokasi.
- Amplop digital: kartu bank/e-wallet + kartu QRIS (diatur dari CONFIG, bisa ditambah dari halaman owner).
- RSVP & ucapan: tersimpan lokal di browser tamu (lihat catatan di bawah).
- **Halaman owner** (`owner.html`) untuk membuat link personal per tamu + teks WhatsApp siap kirim, termasuk pengaturan tata letak foto dan kartu amplop tambahan.

## Cara Pakai

### 1. Ganti isi undangan

Semua pengaturan utama ada di blok `CONFIG` di dalam `index.html` (cari tulisan `CONFIG —` di bagian `<script>` menjelang akhir file):

- `target` — tanggal & jam acara (untuk countdown dan kalender). Format: `new Date("2027-03-20T10:00:00+07:00")`.
- `addr` — alamat lengkap venue (tombol "Salin Alamat").
- `gifts` — daftar kartu amplop bawaan: `type` (nama bank/e-wallet), `kind` (`"Bank"` / `"E-Wallet"`), `number`, `holder` (atas nama). Tambah/kurangi/hapus entri bebas.
- `qris` — kartu QRIS: `show: true/false`, `image` (file gambar QRIS), `holder`.
- `demoWishes` — ucapan contoh yang tampil menemani ucapan tamu.
- `scriptURL` — biarkan kosong (`""`). Mode ini membuat RSVP tersimpan lokal di browser tamu.

Teks lain (nama mempelai, tanggal dalam huruf, nama orang tua, cerita, jam akad/resepsi, tautan peta) ditulis langsung di HTML — ubah dengan cara cari teks lama lalu ganti (Ctrl+F / Cmd+F), misalnya cari nama mempelai contoh dan ganti dengan nama kamu. Judul tab browser ada di tag `<title>`.

### 2. Ganti foto & musik

- Foto ada di folder `foto/`: `couple.jpg` (foto berdua utama), `ava-Adam.jpg` & `ava-Hawa.jpg` (foto sendiri-sendiri untuk layout pisah), `g1.jpg`–`g9.jpg` (galeri). Ganti file-nya dengan foto kamu, **nama file tetap sama** — tidak perlu edit kode.
- Musik: ganti file di `audio/` (nama bebas, sesuaikan `src` tag `<audio>` di `index.html` bila nama berubah).
- Gambar QRIS bawaan: `qris-demo.png` — ganti dengan QRIS kamu (atau atur lewat CONFIG).

### 3. Halaman Owner (`owner.html`)

Buka `owner.html` di alamat yang sama dengan undangan (mis. `https://domainkamu.com/owner.html`).

- **PIN default: `123456`** — ganti di kode: buka `owner.html`, cari `const PIN = "123456";` lalu ubah isinya. PIN dicek lokal di browser (tanpa server), jadi halaman ini untuk kenyamanan pengiriman, bukan kunci keamanan tingkat tinggi — jangan sebarkan alamat owner.html ke tamu.
- **Daftar tamu**: satu nama per baris; format `Nama | 08xxxx` bila ingin tombol kirim langsung ke nomor WA tamu itu. Daftar tersimpan otomatis di HP/browser ini.
- **Template pesan WA**: pakai `{nama}` dan `{link}`. Satu link saja per tamu, dengan label "Detail undangan:".
- **Tata letak foto**: pilih *Menyatu* (satu bingkai foto berdua) atau *Pisah* (dua bingkai sendiri-sendiri), dan pilih foto berdua dari `couple.jpg` / galeri `g1`–`g9`.
- **Kartu amplop tambahan**: tambah baris bank/e-wallet (layanan, nomor, atas nama) dan pilih gambar QRIS (bawaan / file `qris-demo.png` / URL gambar sendiri). Total kartu di undangan maksimal 6 termasuk bawaan.
- Semua pilihan di atas **ikut terbawa di link tiap tamu** (sebagai parameter link) dan tersimpan di browser owner.

### 4. Deploy

Folder ini statis murni — pilih salah satu:

- **GitHub Pages**: buat repo, upload semua isi folder ini, aktifkan Settings → Pages (branch `main`, folder `/`). Undangan di `https://username.github.io/nama-repo/`, owner di `.../owner.html`.
- **Netlify / Vercel**: drag & drop folder ini (Netlify Drop) atau import repo; tanpa build command, tanpa pengaturan khusus.
- **Hosting statis / cPanel / VPS**: upload isi folder ke `public_html` atau folder domain kamu.

Halaman bekerja dari subfolder mana pun (semua alamat aset relatif), jadi ditaruh di subpath seperti `/undangan/` pun aman.

## Catatan RSVP

Versi standalone ini tidak memakai server: ucapan yang dikirim tamu **tersimpan di browser tamu itu sendiri** (localStorage) dan tampil kembali saat ia membuka undangan di perangkat yang sama. Ucapan tidak terkumpul ke satu tempat. Bila kamu butuh RSVP terpusat, isi `CONFIG.scriptURL` dengan URL Google Apps Script milikmu dan sesuaikan format kirimnya di bagian RSVP `index.html`.

## Lisensi

Bebas dipakai, disalin, dan dimodifikasi untuk keperluan pribadi maupun acara kamu. Kredit kecil **"Design by N'Zey"** di footer mohon dipertahankan.

## Pembuat

- Instagram: [instagram.com/iamkizakixd](https://instagram.com/iamkizakixd)
- Telegram: [t.me/kizakixd](https://t.me/kizakixd)
