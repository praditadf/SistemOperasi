# Bash Shell dan Shell Basic

## Praktikum 6.1 — Mengenali Bash dan Menyiapkan Workspace

### 1. Lihat shell login dan shell aktif saat ini

### 2. Lihat proses shell yang sedang berjalan

### 3. Buat workspace praktikum

### 4. Buat beberapa file contoh yang akan dipakai pada praktikum berikutnya

## Praktikum 6.2 — Membuat Ringkasan Sesi Terminal

### 1. Masuk ke workspace praktikum

### 2. Simpan informasi sesi terminal ke file laporan

### 3. Verifikasi isi file laporan

## Praktikum 6.3 — Menambahkan Konfigurasi Aman pada .bashrc

### 1. Lihat file konfigurasi Bash pada home directory

### 2. Buat backup .bashrc

### 3. Tambahkan blok konfigurasi praktikum

### 4. Terapkan konfigurasi tanpa logout

## Praktikum 6.4 — Menyiapkan .bash_profile untuk Shell Login

### 1. Backup .bash_profile jika sudah ada

### 2. Tambahkan konfigurasi login shell

### 3. Uji dengan membuka login shell baru

## Praktikum 6.5 — Membedakan Variabel Shell dan Environment Variable

### 1. Buat variabel lokal

### 2. Buka subshell dan cek apakah variabel masih ada

### 3. Sekarang ubah menjadi environment variable

### 4. Lihat isi PATH dan lokasi beberapa perintah

## Praktikum 6.6 — Menambahkan Direktori Script Pribadi ke PATH

### 1. Pastikan direktori bin praktikum tersedia

### 2. Tambahkan direktori tersebut ke PATH melalui .bashrc

### 3. Buat script ringkasan sistem

### 4. Jalankan script dari direktori yang berbeda

## Praktikum 6.6 — Menambahkan Direktori Script Pribadi ke PATH

### 1. Pastikan direktori bin praktikum tersedia:

### 2. Tambahkan direktori tersebut ke PATH melalui .bashrc:

### 3. Buat script ringkasan sistem:

### 4. Jalankan script dari direktori yang berbeda:

## Praktikum 6.7 — Membuat Alias Produktivitas Dasar

### 1. Tambahkan alias ke .bashrc:

### 2. Uji alias:

## Praktikum 6.8 — Membuat Fungsi Backup Konfigurasi

### 1. Siapkan file konfigurasi contoh:

### 2. Tambahkan fungsi ke .bashrc:

### 3. Uji fungsi:

## Praktikum 6.9 — Menggunakan Completion Dasar dan Melihat History

### 1. Pastikan file contoh tersedia:

### 2. Uji completion file:

### 3. Jalankan beberapa perintah sederhana:

Praktikum 6.10 — Menelusuri Perintah Diagnostik dengan History

1. Jalankan beberapa perintah diagnostik:
   
3. Cari ulang perintah diagnostik dari history:

3. Jalankan ulang salah satu perintah berdasarkan nomor history:

4. Simpan potongan history ke file dokumentasi:

Praktikum 6.11 — Mencoba Wildcard Dasar

1. Masuk ke direktori sampel:
2. Coba beberapa pola wildcard:
3. Coba beberapa ekspansi lain:

Praktikum 6.12 — Mengarsipkan Banyak Log Sekaligus

1. Siapkan file log tambahan:
2. Preview file yang akan diproses:
3. Pindahkan semua file log ke folder arsip:
4. Kompres folder arsip:

Praktikum 6.13 — Membedakan Single Quote, Double Quote, dan Escape

1. Uji single quote dan double quote:
2. Uji escape karakter spasi:
3. Uji akses file yang sama dengan double quote:

Praktikum 6.14 — Menangani File dengan Nama Sulit Secara Aman

1. Pastikan file target tersedia:
2. Salin file dengan nama kompleks ke folder backup:
3. Gunakan variabel untuk memproses path dengan aman:
4. Tampilkan daftar file hasil backup:

# 1.8 Tugas Praktikum

## Tugas Praktikum 1 — Toolkit Bash Administrator Pribadi
Konteks riil: seorang administrator sering mengulang perintah yang sama setiap hari. Agar pekerjaan lebih efisien dan konsisten, ia perlu memiliki toolkit Bash pribadi yang otomatis aktif setiap login.
Instruksi tugas:
1. Tambahkan konfigurasi pada .bashrc untuk:
• menambahkan direktori bin pribadi ke PATH,
• membuat minimal 2 alias yang membantu kerja harian,
• membuat minimal 1 fungsi shell yang berguna untuk administrasi.
2. Pastikan konfigurasi tersebut aktif kembali saat membuka shell login.
3. Buat satu script sederhana di direktori bin pribadi, misalnya script untuk menampilkan ringkasan sistem.
4. Uji dari direktori yang berbeda untuk memastikan script dapat dipanggil tanpa menuliskan path lengkap.
5. Simpan bukti pengujian ke file toolkit-bash-report.txt.
Minimal luaran:
• isi blok konfigurasi yang ditambahkan ke .bashrc,
• output echo $PATH,
• output type untuk alias, fungsi, dan script,
• file laporan toolkit-bash-report.txt.

## Tugas Praktikum 2 — Audit File Konfigurasi dan Logging Aman
Konteks riil: saat troubleshooting, administrator sering perlu menginventarisasi file konfigurasi dan memisahkan output normal dari pesan error.
Instruksi tugas:
1. Buat file laporan bernama audit-konfigurasi-$(date +%F).txt.
2. Cari file *.conf di dalam /etc dan simpan hasilnya ke file laporan.
3. Catat jumlah total file konfigurasi yang ditemukan.
4. Jika ada pesan error, simpan ke file terpisah, misalnya audit-error.log.
5. Tampilkan isi laporan ke terminal dan sekaligus simpan menggunakan tee.
6. Tambahkan ringkasan singkat 3–5 baris yang menjelaskan mengapa pemisahan stdout dan stderr penting dalam audit sistem.
Syarat konsep yang harus muncul:
• redirection >, 2>, atau &>,
• pipeline,
• tee,
• penggunaan variabel atau command substitution.
Minimal luaran:
• file laporan audit,
• file log error,
• perintah yang digunakan,
• analisis singkat hasil audit.

## Tugas Praktikum 3 — Mini Health Check Harian Server
Konteks riil: administrator perlu membuat pemeriksaan cepat (health check) untuk mengetahui kondisi dasar server sebelum dan sesudah maintenance.
Instruksi tugas:
1. Buat script Bash bernama daily-healthcheck pada direktori bin pribadi.
2. Script minimal harus menampilkan:
• tanggal dan waktu,
• hostname,
• user aktif,
• shell aktif,
• uptime,
• penggunaan memori,
• penggunaan filesystem root,
• 10 baris terakhir history command yang relevan dengan pengecekan.
3. Simpan hasil ke file log harian, misalnya healthcheck-$(date +%F).log.
4. Tampilkan hasil ke terminal dan ke file secara bersamaan.
5. Jika Anda menggunakan pipeline dengan tee, cek juga status exit command utama.
Syarat konsep yang harus muncul:
• environment variable,
• PATH,
• alias atau fungsi pendukung,
• history,
• tee,
• penanganan error dasar.
Minimal luaran:
• file script yang executable,
• contoh isi file log hasil eksekusi,
• penjelasan singkat fungsi tiap bagian script.

## Tugas Praktikum 4 — Penanganan File dengan Nama Kompleks dan Arsip Aman
Konteks riil: file hasil backup, ekspor, atau laporan sering memiliki nama yang mengandung spasi atau karakter khusus. Administrator harus tetap dapat memproses file-file tersebut tanpa salah target.
Instruksi tugas:
1. Buat minimal 4 file contoh dengan nama yang bervariasi, termasuk:
• nama file yang mengandung spasi,
• nama file yang mengandung tanda kurung siku atau karakter khusus,
• file dengan pola nama serupa untuk diuji dengan wildcard.
2. Tunjukkan perbedaan hasil jika file diakses tanpa quoting dan dengan quoting yang benar.
3. Lakukan preview wildcard dengan echo sebelum dipakai untuk operasi nyata.
4. Salin file-file tersebut ke direktori backup dengan nama yang aman.
5. Buat arsip tar.gz dari hasil backup.
6. Simpan riwayat perintah yang Anda gunakan ke file riwayat-arsip.txt. Syarat konsep yang harus muncul:
• single quote, double quote, dan escaping,
• wildcard,
• variabel path,
• history,
• operasi file lanjutan yang aman.
Minimal luaran:
• daftar file awal,
• daftar file hasil backup,
• file arsip tar.gz,
• file riwayat-arsip.txt,
• refleksi singkat tentang pentingnya quoting di Bash
