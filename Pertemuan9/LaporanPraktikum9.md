# Pemograman Bash

## Praktikum 7.1 Script Pertama: Laporan Sistem

### 1. Buat workspace praktikum

```
praditadf@praditadf-VirtualBox:~$ mkdir -p ~/praktikum-os/week09/{scripts,logs,data}
praditadf@praditadf-VirtualBox:~$ cd ~/praktikum-os/week09/scripts
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$
```

### 2. Buat script dengan nano

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ nano laporan-sistem.sh
```

### 3. Ketik isi berikut, simpan ( Ctrl+O Enter ), lalu keluar ( Ctrl+X )

```
#!/bin/bash
# Script: laporan-sistem.sh
echo " ================================"
echo "   LAPORAN SISTEM"
echo " ================================"
echo " Tanggal  : $(date '+%A, %d %B %Y')"
echo " Jam      : $(date '+%H:%M:%S')"
echo " Hostname : $(hostname)"
echo " User     : $(whoami)"
echo " CPU core : $(nproc)"
echo " RAM bebas: $(free -h | awk '/^Mem/ {print $4}')"
echo " Disk /   : $(df -h / | awk 'NR==2 {print $5}') terpakai "
echo " ================================"
```

### 4. Beri izin dan jalankan

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ chmod +x laporan-sistem.sh
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./laporan-sistem.sh
 ================================
   LAPORAN SISTEM
 ================================
 Tanggal  : Wednesday, 22 April 2026
 Jam      : 11:35:59
 Hostname : praditadf-VirtualBox
 User     : praditadf
 CPU core : 2
 RAM bebas: 149Mi
 Disk /   : 64% terpakai 
 ================================
```

## Latihan 9.1

### Modifikasi laporan-sistem.sh agar menyimpan output ke file laporan-YYYY-MM-DD.txt sekaligus menampilkannya di terminal. Petunjuk: gunakan tee yang sudah dipelajari di bab sebelumnya

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ nano laporan-sistem.sh
#!/bin/bash
# Script: laporan-sistem.sh
{
echo " ================================"
echo "   LAPORAN SISTEM"
echo " ================================"
echo " Tanggal  : $(date '+%A, %d %B %Y')"
echo " Jam      : $(date '+%H:%M:%S')"
echo " Hostname : $(hostname)"
echo " User     : $(whoami)"
echo " CPU core : $(nproc)"
echo " RAM bebas: $(free -h | awk '/^Mem/ {print $4}')"
echo " Disk /   : $(df -h / | awk 'NR==2 {print $5}') terpakai "
echo " ================================"
} | tee "laporan-$(date +%F).txt"

praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./laporan-sistem.sh
 ================================
   LAPORAN SISTEM
 ================================
 Tanggal  : Wednesday, 22 April 2026
 Jam      : 12:31:25
 Hostname : praditadf-VirtualBox
 User     : praditadf
 CPU core : 2
 RAM bebas: 181Mi
 Disk /   : 64% terpakai 
 ================================
```

<details>
<summary><b>Read More</b></summary>
<br>

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ls
laporan-2026-04-22.txt  laporan-sistem.sh
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ cat laporan-2026-04-22.txt 
 ================================
   LAPORAN SISTEM
 ================================
 Tanggal  : Wednesday, 22 April 2026
 Jam      : 12:31:25
 Hostname : praditadf-VirtualBox
 User     : praditadf
 CPU core : 2
 RAM bebas: 181Mi
 Disk /   : 64% terpakai 
 ================================
```

</details>

## Praktikum 7.2 Script Info Sistem dengan Argumen

### 1. Buat script

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ nano ~/praktikum-os/week09/scripts/info-sistem.sh
```

### 2. Ketik isi berikut

```
#!/bin/bash
# Penggunaan: ./info-sistem.sh [nama-admin] [batas-disk-persen]

ADMIN=${1:-"Tidak dikenal"}
BATAS=${2:-80}
TANGGAL=$(date '+%F %T')
DISK_PERSEN=$(df / | awk 'NR==2 {print $5}' | tr -d '%')

echo "Admin   : $ADMIN "
echo "Tanggal : $TANGGAL "
echo "Disk /  : ${DISK_PERSEN}% terpakai"
echo "Batas   : ${BATAS}% "

if [ "$DISK_PERSEN" -gt "$BATAS" ]; then
echo "STATUS  : PERINGATAN - disk melebihi batas !"
else
SISA=$((BATAS - DISK_PERSEN))
echo "STATUS  : Normal ( sisa toleransi ${SISA}%) "
fi
```

### 3. Simpan, beri izin, uji dengan berbagai kombinasi argumen

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./info-sistem.sh 
Admin   : Tidak dikenal 
Tanggal : 2026-04-22 12:44:58 
Disk /  : 64% terpakai
Batas   : 80% 
STATUS  : Normal ( sisa toleransi 16%) 
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./info-sistem.sh "Dian" 50
Admin   : Dian 
Tanggal : 2026-04-22 12:45:10 
Disk /  : 64% terpakai
Batas   : 50% 
STATUS  : PERINGATAN - disk melebihi batas !
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./info-sistem.sh "Dian" 10
Admin   : Dian 
Tanggal : 2026-04-22 12:45:15 
Disk /  : 64% terpakai
Batas   : 10% 
STATUS  : PERINGATAN - disk melebihi batas !
```

## Latihan 9.2

### Buat script kalkulator.sh yang menerima tiga argumen: <angka1> <operator> <angka2> dengan operator +, -, *, atau /. Contoh: ./kalkulator.sh 20 + 5 menghasilkan 25. Gunakan case untuk memilih operasi, dan validasi jika argumen tidak lengkap

```
```

## Praktikum 7.3 Script Grading dan Menu Interaktif

### 1. Buat script grading (menggunakan if dan for)

```
```

### 2. Ketik isi berikut

```
```

### 3. Simpan, beri izin, dan jalankan

```
```

### 4. Buat script menu interaktif (while + case)

```
```

### 5. Ketik isi berikut

```
```

### 6. Beri izin dan jalankan, coba setiap opsi

```
```

## Latihan 9.3

### Tambahkan ke script grading-batch.sh sebuah ringkasan di bagian bawah yang menampilkan: jumlah mahasiswa per grade (A, B, C, D, E) menggunakan perulangan for kedua yang mengiterasi array MAHASISWA.
```
```

## Praktikum 7.4 Library Fungsi Validasi

### 1. Buat file library

```
```

### 2. Ketik isi berikut

```
```

### 3. Buat script yang menggunakan library

```
```

### 4. Ketik isi berikut

```
```

### 5. Beri izin dan uji semua skenario

```
```

## Latihan 9.4

### Tambahkan fungsi konfirmasi() ke lib-validasi.sh. Fungsi ini menampilkan pertanyaan, membaca input Y/N dari user, mengembalikan 0 jika Y dan 1 jika N. Buat script demo yang memanggil fungsi ini sebelum menghapus sebuah file.
```
```

## Praktikum 7.5 Script Backup dengan Opsi

### 1. Buat script

```
```

### 2. Ketik isi berikut

```
```

### 3. Beri izin dan uji

```
```

## Praktikum 7.6 Debugging Script

### 1. Buat script untuk dianalisis

```
```

### 2. Ketik isi berikut

```
```

### 3. Cek sintaks, lalu jalankan dengan tracing

```
```
## Latihan 9.5

### Script debug-latihan.sh tidak menangani direktori yang tidak ada. Perbaiki dengan menambahkan:
* set -e di baris kedua
* Pengecekan -d "$DIREKTORI" sebelum memanggil du
* Pesan error yang informatif jika direktori tidak ditemukan

Uji dengan direktori yang tidak ada.
```
```

## Tugas Praktikum

### Tugas 1 Script Absensi Kelas

```
Konteks: instruktur mencatat kehadiran mahasiswa dari command line.
Instruksi:
1. Buat script absensi.sh yang:
• Menerima argumen nama mahasiswa dan status (hadir/izin/alpha)
• Menyimpan entri ke absensi-YYYY-MM-DD.txt dengan format [HH:MM]
NAMA - STATUS
• Opsi -r: tampilkan rekapitulasi (jumlah per status)
• Opsi -h: tampilkan bantuan
2. Rekam minimal 5 entri dan tampilkan rekapitulasinya.
Konsep wajib: variabel, parameter posisional, getopts, if, for, fungsi, dan redirection ke file.
```

### Tugas 2 Script Health Check Sistem

```
Konteks: administrator membuat pemeriksaan kondisi server sebelum maintenance.
Instruksi:
1. Buat script healthcheck.sh menggunakan template profesional dari bagian Best Practices.
2. Script menampilkan: tanggal/waktu, hostname, uptime, penggunaan CPU, memori, dan disk untuk setiap filesystem yang terpasang.
3. Jika penggunaan disk mana pun melebihi 80%, tampilkan peringatan.
4. Simpan hasil ke healthcheck-YYYY-MM-DD.log dan tampilkan ke terminal sekaligus menggunakan tee.
5. Opsi -t <persen> mengubah batas peringatan disk (default 80).
Konsep wajib: set -euo pipefail, trap, getopts, fungsi dengan local, for, if, dan tee.
```
