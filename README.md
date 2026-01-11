# Spin Wheel

Aplikasi web interaktif berbasis PHP untuk spin wheel (roda putar) yang menggunakan database MySQL. Cocok untuk acara undian, kuis, atau permainan interaktif.

## Deskripsi

Spin Wheel adalah aplikasi sederhana yang memungkinkan pengguna untuk:
- Memutar roda dengan item-item yang diambil dari database.
- Mengelola data item melalui tabel interaktif.
- Menambahkan, mengimport, atau menghapus data.
- Memutar audio latar saat spin.

Aplikasi ini menggunakan UI modern dengan Tailwind CSS dan komponen seperti DataTables untuk pengalaman pengguna yang baik.

## Fitur Utama

- **Spin Wheel Interaktif**: Roda putar dengan animasi, data diambil dari tabel `soal`.
- **Manajemen Data**: Tabel untuk melihat, menambah, mengedit, dan menghapus data soal.
- **Import Data**: Upload file Excel untuk mengimport data massal.
- **Audio Player**: Pilih dan putar lagu latar dari 4 opsi.
- **Login Sistem**: Halaman login sederhana (perlu pengembangan lebih lanjut).
- **Responsive Design**: Kompatibel dengan desktop dan mobile.

## Teknologi yang Digunakan

- **Backend**: PHP 7+ dengan PDO untuk koneksi database.
- **Database**: MySQL.
- **Frontend**: HTML, CSS (Tailwind CSS), JavaScript (jQuery, DataTables).
- **Library Eksternal**:
  - Tailwind CSS: Styling.
  - DataTables: Tabel interaktif.
  - SweetAlert2: Notifikasi popup.
  - SimpleXLSX: Parsing file Excel.
  - Remixicon: Ikon.

## Persyaratan Sistem

- PHP 7.4 atau lebih baru.
- MySQL 5.7 atau lebih baru.
- Server web (Apache, Nginx, atau PHP built-in server).
- Browser modern dengan dukungan JavaScript.

## Instalasi dan Setup

1. **Clone atau Download Proyek**:
   - Pastikan proyek berada di direktori `/workspaces/spin` atau direktori web server Anda.

2. **Setup Database**:
   - Jalankan MySQL server.
   - Buat database baru:
     ```sql
     CREATE DATABASE spin-wheel;
     ```
   - Buat tabel `soal`:
     ```sql
     USE spin-wheel;
     CREATE TABLE soal (
         id INT AUTO_INCREMENT PRIMARY KEY,
         nama VARCHAR(255) NOT NULL,
         soal TEXT
     );
     ```
   - (Opsional) Tambahkan data contoh:
     ```sql
     INSERT INTO soal (nama, soal) VALUES ('Hadiah 1', 'Apa warna langit?');
     ```

3. **Konfigurasi Database**:
   - Edit file `app/config/config.php` jika perlu (default: host=localhost, user=root, password='', db=spin-wheel).

4. **Jalankan Server**:
   - Gunakan PHP built-in server:
     ```bash
     cd /workspaces/spin
     php -S localhost:8000
     ```
   - Atau konfigurasikan Apache/Nginx dengan document root ke folder proyek.

## Cara Menjalankan

1. Akses `http://localhost:8000/login.php` di browser.
2. Login dengan username dan password (logika login belum lengkap; gunakan apa saja untuk sementara).
3. Di halaman utama (`index.php`):
   - Lihat spin wheel di kiri, tabel data di kanan.
   - Klik "SPIN" untuk memutar roda.
   - Gunakan tombol "New Data" untuk tambah item baru.
   - Klik "Import Data" untuk upload file Excel.
   - Pilih lagu dan klik "Play Audio" untuk musik latar.
4. Kelola data di tabel: centang item dan klik "Delete" untuk hapus.

## Struktur Proyek

```
/workspaces/spin/
├── index.php              # Halaman utama dengan spin wheel dan tabel
├── login.php              # Halaman login
├── app/
│   ├── components/        # Komponen UI (spin.php, tabel-data.php, dll.)
│   ├── config/            # Konfigurasi database (config.php)
│   └── controller/        # Logika backend (post-login.php, upload-file.php, dll.)
└── src/
    ├── assets/            # Gambar dan ikon
    ├── audio/             # File audio (show.mp3, dll.)
    ├── file/              # Upload file
    └── js/                # JavaScript (spin.js, main.js, dll.)
```

## Catatan

- **Login**: Sistem login belum sepenuhnya diimplementasi. File `app/controller/post-login.php` hanya include config; perlu tambahkan validasi user.
- **Error Handling**: Beberapa error database belum ditangani dengan baik; periksa console browser jika ada masalah.
- **Keamanan**: Tidak ada validasi input atau proteksi SQL injection lengkap; gunakan di environment development saja.
- **Pengembangan**: Jika ingin menambah fitur, edit file di `app/components/` atau `app/controller/`.

## Lisensi

Proyek ini untuk tujuan edukasi dan pribadi. Tidak ada lisensi resmi.

## Kontak

Jika ada pertanyaan, hubungi pemilik repository: [andri-creative/spin](https://github.com/andri-creative/spin).
