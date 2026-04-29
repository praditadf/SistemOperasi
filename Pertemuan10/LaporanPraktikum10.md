# Manajemen Memori & System Call

## Praktikum 10.1 — Melihat Penggunaan Memori

### 1. Jalankan free -h untuk melihat ringkasan RAM dan swap

### 2. Lihat detail memori dari kernel melalui /proc/meminfo

### Analisis

1. Hitung persentase memori tersedia: available / total × 100%. Jika hasilnya di bawah 10%, sistem mulai kekurangan memori.
2. Pada baris Swap, apakah kolom used bernilai 0? Jika lebih dari 0, kernel sudah pernah memindahkan data ke disk karena RAM tidak cukup.
3. Perhatikan field Cached dan Buffers di /proc/meminfo. Nilai ini sesuai dengan kolom buff/cache pada free -h.

## Studi Kasus 10.1 — Server Lambat karena Memori

### 1. Periksa kondisi memori secara keseluruhan

### 2. Pantau proses secara real-time

### Analisis

1. Apakah nilai available sangat kecil (misalnya di bawah 200 MB pada server dengan RAM 2 GB)? Jika ya, server kemungkinan kekurangan memori.
2. Apakah kolom used pada baris Swap lebih dari 0? Jika ya, kernel sedang enggunakan swap, yang berarti performa menurun.
3. Di tampilan top, proses apa yang memiliki %MEM terbesar? Proses tersebut enjadi kandidat utama penyebab lambatnya server.

## Praktikum 10.2 — Mengamati Aktivitas Paging

### 1. Jalankan vmstat dengan interval 1 detik, 5 sampel

### Analisis

1. Amati nilai si dan so pada kelima baris. Pada sistem normal dengan RAM cukup, kedua nilai ini selalu 0.
2. Jika nilai si atau so sesekali muncul lebih dari 0, artinya pernah ada aktivitas swap. Ini masih wajar jika tidak terus-menerus.
3. Jika si dan so terus-menerus lebih dari 0, sistem dalam kondisi memory pressure serius — performa turun drastis karena akses disk jauh lebih lambat
dari RAM.
4. Perhatikan juga kolom free (RAM kosong) dan buff (buffer) untuk memahami kondisi keseluruhan RAM saat itu.

## Praktikum 10.3 — Membuat dan Mengonfigurasi Swap File

### 1. Buat file berukuran 512 MB sebagai calon swap

### 2. Atur permission file menjadi 600 — hanya root yang boleh membaca dan menulis

### 3. Format file sebagai area swap, lalu aktifkan

### 4. Verifikasi swap aktif. Anda akan melihat entri /swapfile-week10 dengan ukuran 512M, dan nilai total pada baris Swap di free -h bertambah 512M

### 5. Periksa nilai swappiness, ubah sementara, dan verifikasi perubahan

### Analisis

1. Berapa nilai swappiness default? Apa artinya bagi perilaku kernel dalam menggunakan swap?
2. Setelah diubah ke 10, konfirmasi nilai berubah pada output cat kedua. Apa dampak nilai 10 terhadap penggunaan swap dibanding nilai 60?
3. Apakah entri /swapfile-week10 muncul di swapon –show? Jika tidak, pastikan Langkah 2 (chmod 600) sudah dijalankan sebelum Langkah 3.

## Praktikum 10.4 — Monitoring Memory

### 1. Ambil snapshot proses diurutkan dari penggunaan memori terbesar

### 2. Pantau secara real-time dengan top

### Analisis

1. Proses apa yang berada di urutan pertama? Catat nilai %MEM dan RSS-nya.
2. Konversikan RSS dari KB ke MB (bagi 1024). Misalnya, RSS=524288 berarti proses menggunakan 512 MB RAM. Apakah wajar untuk jenis program tersebut?
3. Mengapa VSZ selalu lebih besar dari RSS pada proses yang sama?
4. Apakah urutan proses di ps konsisten dengan tampilan top saat diurutkan berdasarkan %MEM?

## Praktikum 10.5 — Script Monitor Memori

### 1. Masuk ke direktori kerja dan buat file script

### 2. Ketik isi script berikut

### 3. Beri izin eksekusi dan jalankan script

### Analisis

1. Variabel THRESHOLD=20 menetapkan batas persentase. Perintah free | awk ’/Mem/ {printf "%d", $7/$2*100}’ mengambil kolom ke-7 (available) dibagi kolom ke-2 (total) dari baris Mem, lalu dikalikan 100 untuk menghasilkan persentase bilangan bulat.
2. Kondisi if [ "$AVAIL" -lt "$THRESHOLD" ] bernilai benar jika persentase memori tersedia di bawah 20.
3. Ubah THRESHOLD menjadi 90 dan jalankan ulang. Apa yang berubah pada output? Mengapa demikian?

## Studi Kasus 10.2 — Gagal Akses File

### 1. Buat direktori dan file konfigurasi contoh

### 2. Simulasikan permission bermasalah

### 3. Kembalikan permission dan verifikasi

### Analisis

1. Mengapa cat menghasilkan Permission denied setelah chmod 000? System call apa yang gagal?
2. Apa perbedaan pesan error Permission denied vs No such file or directory? Coba rm app.conf lalu cat app.conf untuk melihat perbedaannya.
3. Permission 644 berarti apa untuk owner, group, dan others?

## Praktikum 10.6 — Mengamati System Call dengan strace

### 1. Lihat 30 baris pertama system call dari perintah ls

### 2. Lihat ringkasan statistik dan bandingkan dua direktori berbeda

### Analisis

1. Dari output Langkah 1, identifikasi minimal 4 system call berbeda. Jelaskan fungsi singkat masing-masing berdasarkan argumen yang terlihat.
2. Dari ringkasan strace -c, system call mana yang paling sering dipanggil? Mengapa?
3. Apakah ada system call dengan errors lebih dari 0? Apakah itu berarti program bermasalah, ataukah bagian normal dari logika program?
4. Apakah jumlah system call berbeda antara ls dan ls /etc? Faktor apa yang menyebabkan perbedaan tersebut?

## Tugas Praktikum

### 1. Tugas 10.1 Audit Penggunaan Memori Sistem

### Instruksi: Buat script memory-audit.sh yang menghasilkan laporan kondisi memori sistem secara otomatis

### Analisis

1. Hitung persentase memori tersedia (available / total × 100%). Apakah sistem dalam kondisi normal?
2. Mengapa buff/cache tidak dihitung sebagai memori yang terpakai dari sudut pandang ketersediaan untuk aplikasi?
3. Dari /proc/meminfo, apakah SwapTotal lebih besar dari 0? Berapa nilai SwapFree?

### 2. Tugas 10.2 Identifikasi Proses dengan Memori Tertinggi

### Instruksi: Simpan daftar 10 proses pengguna memori terbesar ke file

### Analisis

1. Proses apa di urutan pertama? Catat nilai %MEM dan RSS.
2. Konversikan RSS ke MB (bagi 1024). Apakah wajar?
3. Jumlahkan %MEM dari 5 proses teratas. Berapa persen RAM yang mereka gunakan bersama?

### 3. Tugas 10.3 Membuat dan Memverifikasi Swap File

### Instruksi: Buat swap file khusus tugas sebesar 256 MB dan verifikasi

### Analisis

1. Identifikasi kolom NAME, TYPE, SIZE, dan USED pada output swapon –show.
2. Apakah nilai total pada baris Swap di free -h bertambah 256 MB?
3. Mengapa permission 600 penting? Apa risiko jika diatur ke 644?

### 4. Tugas 10.4 Analisis System Call dengan strace

### Instruksi: Analisis system call yang dipanggil perintah ls

### Analisis

1. Sebutkan minimal 5 system call dari strace-summary.txt beserta fungsi singkatnya.
2. System call mana yang paling sering dipanggil? Mengapa?
3. Apakah ada errors lebih dari 0? Apakah program tetap berjalan normal meskipun ada kegagalan tersebut?

### 5. Tugas 10.5 Studi Kasus Diagnosa Server Lambat

### Skenario: Server terasa lambat. Buat script diagnosa yang menggabungkan semua pemeriksaan dari bab ini menggunakan fungsi Bash

### Analisis

1. Jelaskan peran masing-masing fungsi: cek_memori, cek_swap, cek_proses, cek_paging, dan ringkasan. Mengapa diagnosa dipecah menjadi fungsi terpisah?
2. Berdasarkan bagian RINGKASAN, apakah kondisi sistem normal atau kritis? Jelaskan berdasarkan nilai threshold yang digunakan script.
3. Mengapa script menggunakan tee "$LAPORAN" bukan redirection biasa > "$LAPORAN"? Apa keuntungannya?
4. Dari output cek_paging, apakah ada aktivitas si atau so? Jika ada, apa implikasinya terhadap performa server?
