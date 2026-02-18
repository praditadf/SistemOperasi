# Manajemen Perangkat Keras & Perintah Dasar Sistem Operasi

## Praktikum 2.1 — Identifikasi CPU dan Memori

### 1. Tampilkan informasi CPU:
![Informasi CPU](images/lscpu.png "CPU")

### 2. Tampilkan ringkasan memori:
![Ringkasan Memori](images/free-h.png "RAM")

### 3. Cek informasi hardware dari DMI/BIOS (butuh sudo):
![Ringkasan Hardware](images/free-h.png "dmicode")

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

## Praktikum 2.2 — Identifikasi Perangkat PCI/USB dan Driver


### 1. Lihat daftar perangkat PCI:
![Daftar perangkat PCI](images/lspci.png "PCI")

### 2. Lihat perangkat PCI beserta driver kernel yang digunakan:
![Perangkat Pci & kernel](images/lspci-nnk.png "lspsci-nnk")

### 3. Fokus pada NIC (Ethernet) untuk mencari modul driver:
![Ethernet](images/lspci-ethernet.png "ethernet")

### 4. Lihat perangkat USB:
![Perangkat USB](images/lsusb.png "lsusb")

### 5. Lihat topologi USB (tree):
![Topologi USB](images/lsusb-t.png "lsusb -t")

## Latihan 2.2
Temukan 1 perangkat PCI (misal NIC) dan tuliskan: Vendor:Device ID (angka heksadesimal), nama driver/modul kernel, dan deskripsi singkat fungsinya.


## Praktikum 2.3 — Identifikasi Storage dan Filesystem

### 1.  Lihat daftar disk/partisi:
![Daftar disk/partisi](images/3lsblk-f.png "lsblk")

### 2. Tampilkan UUID dan tipe filesystem:
![UUID & tipe filesystem](images/3blkid.png "blkid")

### 3. Lihat mount point untuk root filesystem:
![Mount point](images/3findmnt.png "3findmnt")


## Praktikum 2.4

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")




## Praktikum 2.5

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")




## Praktikum 2.6

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")

## Latihan 2.3


## Praktikum 2.7

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")




## Praktikum 2.8

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")




## Praktikum 2.9

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")

## Latihan 2.4


## Praktikum 2.10

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")




## Praktikum 2.11

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")




## Praktikum 2.12

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")




## Praktikum 2.13

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")




## Praktikum 2.14

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")




## Praktikum 2.15

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")




## Praktikum 2.16

### 1. 
![](images/.png "")

### 2. 
![](images/.png "")

### 3. 
![](images/.png "")

## Latihan 2.5
Pilih satu port yang listening dari output ss -tulpn(misal port 22), lalu tuliskan service/proses yang membukanya. Jelaskan kegunaan port tersebut secara singkat.
