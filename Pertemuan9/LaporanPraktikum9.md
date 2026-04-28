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
praditadf@praditadf-VirtualBox:~$ nano ~/praktikum-os/week09/scripts/lib-validasi.sh
```

### 2. Ketik isi berikut

```
#!/bin/bash
# lib-validasi.sh - Library fungsi validasi

adalah_angka() {
[[ "$1" =~ ^[0-9]+$ ]]
}
file_bisa_dibaca() {
[ -f  "$1" ] && [ -r "$1" ]
}
error_exit() {
echo "ERROR: $1" >&2
exit 1
}
info() { echo "[ INFO ] $1"; }
sukses() { echo "[ OK ] $1"; }
```

### 3. Buat script yang menggunakan library

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ nano ~/praktikum-os/week09/scripts/pakai-library.sh
```

### 4. Ketik isi berikut

```
#!/bin/bash
# Muat library (seperti import di Java)
source ~/praktikum-os/week09/scripts/lib-validasi.sh
ANGKA=$1
FILE=$2
[ -z "$ANGKA" ] || [ -z "$FILE" ] && \
error_exit "Penggunaan: $0 <angka> <path-file>"
if adalah_angka "$ANGKA"; then
sukses "Input '$ANGKA' adalah angka valid"
else
error_exit "'$ANGKA' bukan angka"
fi
if file_bisa_dibaca "$FILE"; then
sukses "File '$FILE' bisa dibaca"
info "Jumlah baris: $(wc -l < "$FILE")"
else
error_exit "File '$FILE' tidak ada atau tidak bisa dibaca "
fi
```

### 5. Beri izin dan uji semua skenario

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/pakai-library.sh 
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./pakai-library.sh 42 /etc/hostname
[ OK ] Input '42' adalah angka valid
[ OK ] File '/etc/hostname' bisa dibaca
[ INFO ] Jumlah baris: 1
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./pakai-library.sh abc /etc/hostname
ERROR: 'abc' bukan angka
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./pakai-library.sh 42 /tidak-ada.txt
[ OK ] Input '42' adalah angka valid
ERROR: File '/tidak-ada.txt' tidak ada atau tidak bisa dibaca 
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./pakai-library.sh
ERROR: Penggunaan: ./pakai-library.sh <angka> <path-file>
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ 
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./pakai-library.sh 42 /etc/hostname
[ OK ] Input '42' adalah angka valid
[ OK ] File '/etc/hostname' bisa dibaca
[ INFO ] Jumlah baris: 1
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./pakai-library.sh abc /etc/hostname
ERROR: 'abc' bukan angka
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./pakai-library.sh 42 /tidak-ada.txt
[ OK ] Input '42' adalah angka valid
ERROR: File '/tidak-ada.txt' tidak ada atau tidak bisa dibaca 
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./pakai-library.sh
ERROR: Penggunaan: ./pakai-library.sh <angka> <path-file>
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ 
```

## Latihan 9.4

### Tambahkan fungsi konfirmasi() ke lib-validasi.sh. Fungsi ini menampilkan pertanyaan, membaca input Y/N dari user, mengembalikan 0 jika Y dan 1 jika N. Buat script demo yang memanggil fungsi ini sebelum menghapus sebuah file

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ nano ~/praktikum-os/week09/scripts/lib-validasi.sh

konfirmasi() {
read -rp "$1 (Y/N): " hasil
case "$hasil" in
[Yy]) return 0 ;;
[Nn]) return 1 ;;
*) echo "Masukkan Y atau N." ;;
esac
}

praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ nano hapus-file.sh
#!/bin/bash
# Load library
source ./lib-validasi.sh
file="$1"
[ -z "$file" ] && error_exit "Nama file harus diberikan."
file_bisa_dibaca "$file" || error_exit "File tidak ditemukan atau tidak bisa dibaca."
if konfirmasi "Apakah Anda yakin ingin menghapus file '$file'?"; then
    rm "$file" && sukses "File berhasil dihapus."
else
    info "Penghapusan dibatalkan."
fi

praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ chmod +x hapus-file.sh 
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ touch a.txt
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./hapus-file.sh a.txt
Apakah Anda yakin ingin menghapus file 'a.txt'? (Y/N): n
[ INFO ] Penghapusan dibatalkan.
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./hapus-file.sh a.txt
Apakah Anda yakin ingin menghapus file 'a.txt'? (Y/N): y
[ OK ] File berhasil dihapus.
```

## Praktikum 7.5 Script Backup dengan Opsi

### 1. Buat script

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ nano ~/praktikum-os/week09/scripts/backup-data.sh
```

### 2. Ketik isi berikut

```
#!/bin/bash
# Penggunaan: ./backup-data.sh [-v] [-c] [-l logfile] <sumber> <tujuan>

VERBOSE=false
COMPRESS=false
LOG_FILE=""

while getopts "vcl:" OPSI; do
case $OPSI in
v) VERBOSE=true ;;
c) COMPRESS=true ;;
l) LOG_FILE="$OPTARG" ;;
*) echo "Penggunaan: $0 [-v] [-c] [-l logfile] <sumber> <tujuan>"
exit 1 ;;
esac
done

shift $((OPTIND - 1))

SUMBER=$1
TUJUAN=$2

log() {
local MSG="[$(date '+%T')] $1"
echo "$MSG"
[ -n "$LOG_FILE" ] && echo "$MSG" >> "$LOG_FILE"
}

[ -z "$SUMBER" ] || [ -z "$TUJUAN" ] && {
echo "ERROR: sumber dan tujuan wajib diisi"; exit 1; }

[ ! -d "$SUMBER" ] && { log "ERROR: $SUMBER tidak ada"; exit 2; }

mkdir -p "$TUJUAN"

TANGGAL=$(date '+%F-%H%M%S')

[ "$VERBOSE" = true ] && log "Sumber: $SUMBER | Tujuan: $TUJUAN"

if [ "$COMPRESS" = true ]; then
ARSIP="$TUJUAN/backup-$(basename "$SUMBER")-$TANGGAL.tar.gz"
tar -czf "$ARSIP" -C "$(dirname "$SUMBER")" "$(basename "$SUMBER")"
log "Arsip: $ARSIP ($(du -sh "$ARSIP" | cut -f1))"
else
cp -r "$SUMBER" "$TUJUAN/backup-$(basename "$SUMBER")-$TANGGAL"
log "Backup selesai."
fi
```

### 3. Beri izin dan uji

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/backup-data.sh 
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ cd ~/praktikum-os/week09/scripts
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./backup-data.sh ~/praktikum-os/week09/data ~/praktikum-os/week09/logs
[19:23:55] Backup selesai.
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./backup-data.sh -v -c -l ../logs/backup.log \
> ~/praktikum-os/week09/data ~/praktikum-os/week09/logs
[19:34:07] Sumber: /home/praditadf/praktikum-os/week09/data | Tujuan: /home/praditadf/praktikum-os/week09/logs
[19:34:07] Arsip: /home/praditadf/praktikum-os/week09/logs/backup-data-2026-04-28-193407.tar.gz (4.0K)

```

## Praktikum 7.6 Debugging Script

### 1. Buat script untuk dianalisis

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ nano ~/praktikum-os/week09/scripts/debug-latihan.sh
```

### 2. Ketik isi berikut

```
#!/bin/bash
# Script: debug-latihan.sh
# Penggunaan: ./debug-latihan.sh <direktori> <batas-MB>

DIREKTORI=$1
BATAS=$2

if [ $# -ne 2 ]; then
    echo "Penggunaan: $0 <direktori> <batas-MB>"
    exit 1
fi

UKURAN=$(du -sm "$DIREKTORI" | cut -f1)

echo "Direktori: $DIREKTORI"
echo "Ukuran: ${UKURAN} MB"
echo "Batas: ${BATAS} MB"

if [ "$UKURAN" -gt "$BATAS" ]; then
    echo "PERINGATAN: Ukuran melebihi batas!"
    echo "Kelebihan: $((UKURAN - BATAS)) MB"
else
    echo "Status: Normal (sisa: $((BATAS - UKURAN)) MB)"
fi
```

### 3. Cek sintaks, lalu jalankan dengan tracing

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/debug-latihan.sh
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ bash -n debug-latihan.sh && echo "Sintaks OK"
Sintaks OK
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ bash -x debug-latihan.sh /etc 10
+ DIREKTORI=/etc
+ BATAS=10
+ '[' 2 -ne 2 ']'
++ du -sm /etc
++ cut -f1
du: cannot read directory '/etc/credstore.encrypted': Permission denied
du: cannot read directory '/etc/ssl/private': Permission denied
du: cannot read directory '/etc/cups/ssl': Permission denied
du: cannot read directory '/etc/polkit-1/rules.d': Permission denied
du: cannot read directory '/etc/sssd': Permission denied
du: cannot read directory '/etc/credstore': Permission denied
+ UKURAN=12
+ echo 'Direktori: /etc'
Direktori: /etc
+ echo 'Ukuran: 12 MB'
Ukuran: 12 MB
+ echo 'Batas: 10 MB'
Batas: 10 MB
+ '[' 12 -gt 10 ']'
+ echo 'PERINGATAN: Ukuran melebihi batas!'
PERINGATAN: Ukuran melebihi batas!
+ echo 'Kelebihan: 2 MB'
Kelebihan: 2 MB
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./debug-latihan.sh /vat 50
du: cannot access '/vat': No such file or directory
Direktori: /vat
Ukuran:  MB
Batas: 50 MB
./debug-latihan.sh: line 19: [: : integer expression expected
Status: Normal (sisa: 50 MB)
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./debug-latihan.sh
Penggunaan: ./debug-latihan.sh <direktori> <batas-MB>
```

## Latihan 9.5

### Script debug-latihan.sh tidak menangani direktori yang tidak ada. Perbaiki dengan menambahkan

* set -e di baris kedua
* Pengecekan -d "$DIREKTORI" sebelum memanggil du
* Pesan error yang informatif jika direktori tidak ditemukan

Uji dengan direktori yang tidak ada.

```
#!/bin/bash
set -e
# Script: debug-latihan.sh
# Penggunaan: ./debug-latihan.sh <direktori> <batas-MB>

DIREKTORI=$1
BATAS=$2

if [ $# -ne 2 ]; then
echo "Penggunaan: $0 <direktori> <batas-MB>"
exit 1
fi

if [ ! -d "$DIREKTORI" ]; then
echo "ERROR: Direktori '$DIREKTORI' tidak ditemukan."
exit 1
fi

UKURAN=$(du -sm "$DIREKTORI" | cut -f1)

echo "Direktori: $DIREKTORI"
echo "Ukuran: ${UKURAN} MB"
echo "Batas: ${BATAS} MB"

if [ "$UKURAN" -gt "$BATAS" ]; then
echo "PERINGATAN: Ukuran melebihi batas!"
echo "Kelebihan: $((UKURAN - BATAS)) MB"
else
echo "Status: Normal (sisa: $((BATAS - UKURAN)) MB)"
fi
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./debug-latihan.sh /folder-tidak-ada 10
ERROR: Direktori '/folder-tidak-ada' tidak ditemukan.
```

## Tugas Praktikum

### Tugas 1 Script Absensi Kelas

#### Konteks: instruktur mencatat kehadiran mahasiswa dari command line

Instruksi

1. Buat script absensi.sh yang:

* Menerima argumen nama mahasiswa dan status (hadir/izin/alpha)
* Menyimpan entri ke absensi-YYYY-MM-DD.txt dengan format [HH:MM] NAMA - STATUS
* Opsi -r: tampilkan rekapitulasi (jumlah per status)
* Opsi -h: tampilkan bantuan

1. Rekam minimal 5 entri dan tampilkan rekapitulasinya.
Konsep wajib: variabel, parameter posisional, getopts, if, for, fungsi, dan redirection ke file.

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ nano ~/praktikum-os/week09/scripts/absensi.sh
#!/bin/bash
# Script: absensi.sh
# Pencatatan kehadiran mahasiswa

FILE="$HOME/praktikum-os/week09/logs/absensi-$(date +%F).txt"
mkdir -p "$(dirname "$FILE")"

bantuan() { echo "Gunakan: $0 [-h] [-r] [NAMA STATUS]"; exit 0; }
rekap() {
echo "=== REKAP ==="
for S in hadir izin alpha; do
echo "$S: $(grep -ic "\- $S" "$FILE" 2>/dev/null || echo 0)"
done
exit 0
}

while getopts "hr" OPSI; do
case $OPSI in
h) bantuan ;;
r) rekap ;;
*) exit 1 ;;
esac
done
shift $((OPTIND - 1))

if [ $# -lt 2 ]; then
bantuan;
fi

STATUS=${2,,}
if [[ ! "$STATUS" =~ ^(hadir|izin|alpha)$ ]]; then 
echo "Error: Status harus hadir/izin/alpha";
exit 1 
fi

echo "[$(date +%H:%M)] $1 - $STATUS" >> "$FILE"
echo "Tercatat: $1 - $STATUS"

praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/absensi.sh
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./absensi.sh "Aldi" izin
Tercatat: Aldi - izin
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./absensi.sh "Bobi" sakit
Error: Status harus hadir/izin/alpha
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./absensi.sh "Bobi" alpha
Tercatat: Bobi - alpha
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./absensi.sh "Albi" hadir
Tercatat: Albi - hadir
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./absensi.sh "Abil" izin
Tercatat: Abil - izin
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./absensi.sh "bila" hadir
Tercatat: bila - hadir
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./absensi.sh -r
=== REKAP ===
hadir: 2
izin: 2
alpha: 1
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ cat ../logs/absensi-2026-04-28.txt 
[19:55] Aldi - izin
[19:55] Bobi - alpha
[19:55] Albi - hadir
[19:56] Abil - izin
[19:56] bila - hadir
```

### Tugas 2 Script Health Check Sistem

#### Konteks: administrator membuat pemeriksaan kondisi server sebelum maintenance

Instruksi

1. Buat script healthcheck.sh menggunakan template profesional dari bagian Best Practices.
2. Script menampilkan: tanggal/waktu, hostname, uptime, penggunaan CPU, memori, dan disk untuk setiap filesystem yang terpasang.
3. Jika penggunaan disk mana pun melebihi 80%, tampilkan peringatan.
4. Simpan hasil ke healthcheck-YYYY-MM-DD.log dan tampilkan ke terminal sekaligus menggunakan tee.
5. Opsi -t <persen> mengubah batas peringatan disk (default 80).
Konsep wajib: set -euo pipefail, trap, getopts, fungsi dengan local, for, if, dan tee.

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ nano ~/praktikum-os/week09/scripts/healthcheck.sh
#!/bin/bash
set -euo pipefail

BATAS=80
LOG="$HOME/praktikum-os/week09/logs/healthcheck-$(date +%F).log"
mkdir -p "${LOG%/*}"

trap 'echo "[INFO] Selesai."' EXIT

while getopts "t:h" OPT; do
case "$OPT" in
t) BATAS="$OPTARG" ;;
h) echo "Gunakan: $0 [-t batas_persen] [-h]"; exit 0 ;;
*) exit 1 ;;

esac
done

cek_sistem() {
local WAKTU=$(date '+%F %T')
local HOST=$(hostname)
local UPTIME=$(uptime -p)
local CPU=$(top -bn1 | awk '/Cpu\(s\)/ {print $2+$4}')
local RAM=$(free -h | awk '/^Mem/ {print $4}')

echo "=== HEALTH CHECK ==="
echo "Waktu    : $WAKTU"
echo "Host     : $HOST"
echo "Uptime   : $UPTIME"
echo "CPU      : $CPU%" 
echo "Sisa RAM : $RAM"
echo "--- Disk ---"

local DISKS=$(df -h | awk '/^\/dev\// {print $5","$6}')
for d in $DISKS; do
local P=$(echo "$d" | cut -d, -f1 | tr -d %)
local M=$(echo "$d" | cut -d, -f2)
if [ "$P" -ge "$BATAS" ]; then
echo "[PERINGATAN] $M terpakai $P% (Batas: $BATAS%)"
else
echo "[OK] $M terpakai $P%"
fi
done
}

cek_sistem | tee -a "$LOG"
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ chmod +x ~/praktikum-os/week09/scripts/healthcheck.sh
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./healthcheck.sh
=== HEALTH CHECK ===
Waktu    : 2026-04-28 20:17:18
Host     : praditadf-VirtualBox
Uptime   : up 1 hour, 50 minutes
CPU      : 0%
Sisa RAM : 159Mi
--- Disk ---
[OK] / terpakai 63%
[INFO] Selesai.
praditadf@praditadf-VirtualBox:~/praktikum-os/week09/scripts$ ./healthcheck.sh -t 50
=== HEALTH CHECK ===
Waktu    : 2026-04-28 20:17:20
Host     : praditadf-VirtualBox
Uptime   : up 1 hour, 50 minutes
CPU      : 0%
Sisa RAM : 159Mi
--- Disk ---
[PERINGATAN] / terpakai 63% (Batas: 50%)
[INFO] Selesai.

```
