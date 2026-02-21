# Manajemen Perangkat Keras & Perintah Dasar Sistem Operasi

## Praktikum 2.1 — Identifikasi CPU dan Memori

### 1. Tampilkan informasi CPU:

![Informasi CPU](images/lscpu.png)

### 2. Tampilkan ringkasan memori:

![Ringkasan Memori](images/free-h.png)

### 3. Cek informasi hardware dari DMI/BIOS (butuh sudo):

![Ringkasan Hardware](images/free-h.png)

## Praktikum 2.2 — Identifikasi Perangkat PCI/USB dan Driver

### 1. Lihat daftar perangkat PCI:

![Daftar perangkat PCI](images/lspci.png)

### 2. Lihat perangkat PCI beserta driver kernel yang digunakan:

![Perangkat Pci & kernel](images/lspci-nnk.png)

### 3. Fokus pada NIC (Ethernet) untuk mencari modul driver:

![Ethernet](images/lspci-ethernet.png)

### 4. Lihat perangkat USB:

![Perangkat USB](images/lsusb.png)

### 5. Lihat topologi USB (tree):

![Topologi USB](images/lsusb-t.png)

## Praktikum 2.3 — Identifikasi Storage dan Filesystem

### 1. Lihat daftar disk/partisi:

![Daftar disk/partisi](images/3lsblk-f.png)

### 2. Tampilkan UUID dan tipe filesystem:

![UUID & tipe filesystem](images/3blkid.png)

### 3. Lihat mount point untuk root filesystem:

![Mount point](images/3findmnt.png)

## Praktikum 2.4 — Melihat Modul Aktif dan Informasinya

### 1. Cek versi kernel:

![Versi Kernel](images/4uname-r.png)

### 2. Tampilkan daftar modul aktif:

![Daftar Modul Aktif](images/4lsmodhead.png)

### 3. Pilih salah satu modul (contoh aman: loop) dan lihat detailnya:

![Pilih Modul](images/4modinfo.png)

### 4. Muat modul (jika belum aktif), lalu verifikasi:

![Muat Modul](images/4modprobe.png)

## Praktikum 2.5 — Konfigurasi Auto-load dan Blacklist

### 1. Buat file auto-load:

![Auto-load](images/5autoload.png)

### 2. Simulasikan verifikasi (tanpa reboot) dengan memastikan modul sudah aktif:

![Verifikasi](images/5lsmod.png)

### 3. (Opsional, konsep) blacklist modul:

```
# echo " blacklist loop " | sudo tee / etc/ modprobe .d/blacklist - loop . conf
```

## Praktikum 2.6 — Mengenali Block vs Character Device

### 1. Lihat detail salah satu disk (sesuaikan dengan perangkat Anda, misal sda):

![detail disk](images/6sda2.png)

### 2. Lihat detail device terminal:

![Detail device terminal](images/6tty.png)

### 3. Lihat disk dan partisi untuk mengaitkan dengan /dev:

![List disk & partisi](images/6lsblk.png)

## Praktikum 2.7 — Melihat Informasi udev

### 1. Cek atribut udev untuk disk:

![Atrbut udec](images/7udev.png)

## Praktikum 2.8 — Membuat Workspace Praktikum

### 1. Buat direktori praktikum dan masuk ke dalamnya:

![Make directory](images/8mkdir.png)

### 2. Buat beberapa file contoh:

![New file](images/8touch.png)

### 3. Isi file log contoh (simulasi):

![Fill file](images/8cat.png)

### 4. Baca file dengan less:

![Read file](images/8less.png)

## Praktikum 2.9 — Pencarian Pola dengan grep

### 1. Cari baris yang mengandung ERROR pada data.log:

![Find Error](images/9error.png)

### 2. Cari tanpa memperhatikan huruf besar/kecil:

![Find](images/9error-i.png)

### 3. Tampilkan nomor baris:

![Print](images/9-n.png)

### 4. Tampilkan baris yang tidak cocok (invert match):

![Invert match](images/9-v.png)

## Praktikum 2.10 — Substitusi dengan sed (Aman di File Latihan)

### 1. Siapkan file konfigurasi latihan:

![Create file](images/10cat.png)

### 2. Ganti dev menjadi prod (tanpa mengubah file asli):

![Switch dev](images/10sed.png)

### 3. Terapkan perubahan langsung ke file (-i):

![Aplly](images/10sed-i.png)

### 4. Ganti semua kemunculan kata (g untuk global), contoh ubah myserver menjadi node:

![Switch](images/10.png)

## Praktikum 2.11 — Ekstraksi Kolom dengan awk

### 1. Lihat output df-h:

![df-h](images/11df-h.png)

### 2. Ambil kolom filesystem dan persentase pemakaian:

![Put colom](images/11df-hawk.png)

### 3. Filter hanya yang pemakaian disk di atas 80%:

![Filter disk](images/11df-hawk80.png)

## Praktikum 2.12 — Melihat Proses dengan ps

### 1. Tampilkan semua proses (format BSD):

![Show all](images/12psaux.png)

### 2. Cari proses tertentu (misal sshd):

![Specific process](images/12sshd.png)

## Praktikum 2.13 — Monitoring Real-time dengan top

### 1. Jalankan top:

![run tup](images/13top.png)

## Praktikum 2.14 — Menghentikan Proses dengan kill

### 1. Jalankan proses dummy di background:

![run dummy](images/14sleep.png)

### 2. Cari PID proses sleep:

![Pid process sleep](images/14psaux.png)

### 3. Hentikan dengan SIGTERM:

![Stop With Sigterm](images/14kill7078.png)

### 4. Verifikasi proses berhenti:

![Process stops](images/14term.png)

## Praktikum 2.15  — Cek Disk, Load, dan Service

### 1. Cek penggunaan disk:

![Use disk](images/15df-h.png)

### 2. Cari direktori yang besar (contoh pada /var):

![Large directory](images/15var.png)

### 3. Cek load dan uptime:

![Load & uptime](images/15uptime.png)

### 4. Cek service yang gagal:

![Service failed](images/15systemctl.png)

### 5. Ambil log error terbaru (jika ada indikasi masalah):

![Log](images/15journalctl.png)

## Praktikum 2.16 — Monitoring Port dan Koneksi (Network Basics)

### 1. Lihat interface dan IP:

![Interface and IP](images/16ipa.png)

### 2. Lihat routing table:

![Routing table](images/16ipr.png)

### 3. Lihat port yang sedang listening:

![port list](images/16ss-tulpn.png)

## Latihan

## Latihan 2.1

Catat: (1) jumlah CPU(s), core/thread, (2) total RAM, (3) total swap. Jelaskan perbedaan RAM vs swap dalam 2–3 kalimat.

### Catat: (1) jumlah CPU(s), core/thread

```
CPU(s)               : 1
Tread(s) per core    : 1
Core(s) per socket   : 1
Socket(s)            : 1
```

### (2) total RAM

```
Mem                  : 1.9Gi
```

### (3) total swap. Jelaskan perbedaan RAM vs swap dalam 2–3 kalimat.

```
Swap                 : 2.0Gi
Perbedaan Ram dan scap adalah...
```

## Latihan 2.2

Temukan 1 perangkat PCI (misal NIC) dan tuliskan: Vendor:Device ID (angka heksadesimal), nama driver/modul kernel, dan deskripsi singkat fungsinya.

## Latihan 2.3

Dari output ls -l, jelaskan perbedaan penanda file untuk block device dan character device. (Hint: karakter pertama pada permission string)

## Latihan 2.4

Gunakan grep untuk menampilkan hanya baris yang mengandung INFO atau WARN dari data.log. (Hint: gunakan grep -E dengan pola alternatif)
![](images/lat2.4.png)

## Latihan 2.5

Pilih satu port yang listening dari output ss -tulpn(misal port 22), lalu tuliskan service/proses yang membukanya. Jelaskan kegunaan port tersebut secara singkat.
