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
#!/bin/bash
# Penggunaan: ./kalkulator.sh [angka1] [operator] [angka2] 

ANGKA1=${1:-"Tidak dikenal"}
OPERATOR=${2:-"Tidak dikenal"}
ANGKA2=${3:-"Tidak dikenal"}

echo "ANGKA1  : $ANGKA1 "
echo "Operator: $OPERATOR"
echo "Angka 2 : $ANGKA2 "

case $OPERATOR in
-)
echo "Hasil : $@ = $((ANGKA1 - ANGKA2))"
;;
+)
echo "Hasil : $@ = $((ANGKA1 + ANGKA2))"
;;
\*)
echo "Hasil : $@ = $((ANGKA1 * ANGKA2))"
;;
/)
echo "Hasil : $@ = $((ANGKA1 / ANGKA2))"
;;
*)
echo "Terdapat kesalahan"
;;
esac
```

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./kalkulator.sh 100 + 5
ANGKA1  : 100 
Operator: +
Angka 2 : 5 
Hasil : 100 + 5 = 105
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./kalkulator.sh 100 - 5
ANGKA1  : 100 
Operator: -
Angka 2 : 5 
Hasil : 100 - 5 = 95
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./kalkulator.sh 100 / 5
ANGKA1  : 100 
Operator: /
Angka 2 : 5 
Hasil : 100 / 5 = 20
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./kalkulator.sh 100 "*" 5
ANGKA1  : 100 
Operator: *
Angka 2 : 5 
Hasil : 100 * 5 = 500
```

## Praktikum 7.3 Script Grading dan Menu Interaktif

### 1. Buat script grading (menggunakan if dan for)

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ nano ~/praktikum-os/week09/scripts/grading-batch.sh
```

### 2. Ketik isi berikut

```
#!/bin/bash
# Script : grading-batch.sh
# Proses daftar nilai mahasiswa
MAHASISWA=("Andi:92" "Budi:73" "Citra:55" "Deni:80" "Eka:45")
echo "=== HASIL GRADING ==="
for ENTRI in "${MAHASISWA[@]}"; do
NAMA=$(echo "$ENTRI" | cut -d: -f1)
NILAI=$(echo "$ENTRI" | cut -d: -f2)
if [ "$NILAI" -ge 85 ]; then
GRADE="A"
elif [ "$NILAI" -ge 75 ]; then
GRADE="B"
elif [ "$NILAI" -ge 65 ]; then
GRADE="C"
elif [ "$NILAI" -ge 55 ]; then
GRADE="D"
else
GRADE="E"
fi
printf " %-10s %3d %s\n" "$NAMA" "$NILAI" "$GRADE"
done
echo "====================="
```

### 3. Simpan, beri izin, dan jalankan

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/grading-batch.sh
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./grading-batch.sh
=== HASIL GRADING ===
 Andi        92 A
 Budi        73 C
 Citra       55 D
 Deni        80 B
 Eka         45 E
=====================
```

### 4. Buat script menu interaktif (while + case)

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ nano ~/praktikum-os/week09/scripts/menu-sistem.sh
```

### 5. Ketik isi berikut

```
#!/bin/bash
# Menu interaktif pemantauan sistem
while true; do
echo ""
echo "===== MENU MONITOR ====="
echo "1) Info disk"
echo "2) Info memori"
echo "3) Proses teratas"
echo "4) Keluar"
echo -n "Pilih [1-4]: "
read PILIHAN
case $PILIHAN in
1) df -h ;;
2) free -h ;;
3) ps aux --sort=-%cpu | head -6 ;;
4) echo "Sampai jumpa!"; exit 0 ;;
*) echo "Pilihan tidak valid." ;;
esac
done
```

### 6. Beri izin dan jalankan, coba setiap opsi

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/menu-sistem.sh 
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./menu-sistem.sh 

===== MENU MONITOR =====
1) Info disk
2) Info memori
3) Proses teratas
4) Keluar
Pilih [1-4]: 1
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           392M  1.9M  390M   1% /run
/dev/sda2        25G   15G  8.9G  62% /
tmpfs           2.0G   24M  1.9G   2% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           392M  132K  392M   1% /run/user/1000

===== MENU MONITOR =====
1) Info disk
2) Info memori
3) Proses teratas
4) Keluar
Pilih [1-4]: 2
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.4Gi       128Mi       226Mi       1.7Gi       1.5Gi
Swap:          2.0Gi       308Mi       1.7Gi

===== MENU MONITOR =====
1) Info disk
2) Info memori
3) Proses teratas
4) Keluar
Pilih [1-4]: 3
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
pradita+    6500  200  0.1  22428  4928 pts/0    R+   16:26   0:00 ps aux --sort=-%cpu
pradita+    2114  3.6 10.2 4231060 410632 ?      Ssl  14:01   5:20 /usr/bin/gnome-shell
pradita+    5905  3.6  8.7 1463047432 351452 ?   Sl   16:05   0:45 /snap/code/234/usr/share/code/code --type=zygote --no-sandbox
pradita+    5984  2.0  9.5 1461340244 383936 ?   Sl   16:05   0:25 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService --lang=en-US --service-sandbox-type=none --no-sandbox --dns-result-order=ipv4first --experimental-network-inspection --inspect-port=0 --js-flags=--nodecommit_pooled_pages --crashpad-handler-pid=5832 --enable-crash-reporter=e9bfb98a-f4aa-4b21-89a7-bd4f93b569d0,no_channel --user-data-dir=/home/praditadf/.config/Code --standard-schemes=vscode-webview,vscode-file --secure-schemes=vscode-webview,vscode-file --cors-schemes=vscode-webview,vscode-file --fetch-schemes=vscode-webview,vscode-file --service-worker-schemes=vscode-webview --code-cache-schemes=vscode-webview,vscode-file --shared-files=v8_context_snapshot_data:100 --field-trial-handle=3,i,17666756547840335739,4359113908049617285,262144 --enable-features=DocumentPolicyIncludeJSCallStacksInCrashReports,EarlyEstablishGpuChannel,EstablishGpuChannelAsync --disable-features=CalculateNativeWinOcclusion,LocalNetworkAccessChecks,ScreenAIOCREnabled,SpareRendererForSitePerProcess,TraceSiteInstanceGetProcessCreation --variations-seed-version --trace-process-track-uuid=3190708994745248135
pradita+    3038  1.8  9.9 3504072 399500 ?      Sl   14:02   2:35 /snap/firefox/7967/usr/lib/firefox/firefox

===== MENU MONITOR =====
1) Info disk
2) Info memori
3) Proses teratas
4) Keluar
Pilih [1-4]: 4
Sampai jumpa!
```

## Latihan 9.3

### Tambahkan ke script grading-batch.sh sebuah ringkasan di bagian bawah yang menampilkan: jumlah mahasiswa per grade (A, B, C, D, E) menggunakan perulangan for kedua yang mengiterasi array MAHASISWA

```
#!/bin/bash
# Script : grading-batch.sh
# Proses daftar nilai mahasiswa
MAHASISWA=("Andi:92" "Budi:73" "Citra:55" "Deni:80" "Eka:45")
echo "=== HASIL GRADING ==="
for ENTRI in "${MAHASISWA[@]}"; do
NAMA=$(echo "$ENTRI" | cut -d: -f1)
NILAI=$(echo "$ENTRI" | cut -d: -f2)
if [ "$NILAI" -ge 85 ]; then
GRADE="A"
elif [ "$NILAI" -ge 75 ]; then
GRADE="B"
elif [ "$NILAI" -ge 65 ]; then
GRADE="C"
elif [ "$NILAI" -ge 55 ]; then
GRADE="D"
else
GRADE="E"
fi
printf " %-10s %3d %s\n" "$NAMA" "$NILAI" "$GRADE"
done
echo "====================="

echo "=== JUMLAH MAHASISWA PER GRADE ==="
for G in A B C D E; do
COUNT=0
for ENTRI in "${MAHASISWA[@]}"; do
NILAI=$(echo "$ENTRI" | cut -d: -f2)
if [ "$NILAI" -ge 85 ]; then
GRADE="A"
elif [ "$NILAI" -ge 75 ]; then
GRADE="B"
elif [ "$NILAI" -ge 65 ]; then
GRADE="C"
elif [ "$NILAI" -ge 55 ]; then
GRADE="D"
else
GRADE="E";
fi
if [ "$GRADE" == "$G" ]; then
((COUNT++))
fi
done
echo "Grade $G: $COUNT"
done

praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./grading-batch.sh 
=== HASIL GRADING ===
 Andi        92 A
 Budi        73 C
 Citra       55 D
 Deni        80 B
 Eka         45 E
=====================
=== JUMLAH MAHASISWA PER GRADE ===
Grade A: 1
Grade B: 1
Grade C: 1
Grade D: 1
Grade E: 1
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
