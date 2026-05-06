# Manajemen File & User/Group

## Praktikum 9.1 — Permissions

### Langkah 1: Buat direktori kerja dan dua file uji

```
praditadf@praditadf-VirtualBox:~$ mkdir ~/lab-permissions && cd ~/lab-permissions
praditadf@praditadf-VirtualBox:~/lab-permissions$ echo "data rahasia" > secret.txt
praditadf@praditadf-VirtualBox:~/lab-permissions$ echo '#!/bin/bash' > myscript.sh
praditadf@praditadf-VirtualBox:~/lab-permissions$ echo 'echo Hello' >> myscript.sh
praditadf@praditadf-VirtualBox:~/lab-permissions$ ls -la
total 16
drwxrwxr-x  2 praditadf praditadf 4096 May  6 10:51 .
drwxr-x--- 30 praditadf praditadf 4096 May  6 10:50 ..
-rw-rw-r--  1 praditadf praditadf   23 May  6 10:51 myscript.sh
-rw-rw-r--  1 praditadf praditadf   13 May  6 10:50 secret.txt
```

### Langkah 2: Jadikan secret.txt privat hanya untuk owner

```
praditadf@praditadf-VirtualBox:~/lab-permissions$ chmod 600 secret.txt
praditadf@praditadf-VirtualBox:~/lab-permissions$ ls -l secret.txt 
-rw------- 1 praditadf praditadf 13 May  6 10:50 secret.txt
```

### Langkah 3: Jadikan myscript.sh dapat dijalankan

```
praditadf@praditadf-VirtualBox:~/lab-permissions$ chmod 755 myscript.sh
praditadf@praditadf-VirtualBox:~/lab-permissions$ ls -l myscript.sh 
-rwxr-xr-x 1 praditadf praditadf 23 May  6 10:51 myscript.sh
praditadf@praditadf-VirtualBox:~/lab-permissions$ ./myscript.sh 
Hello
```

### Langkah 4: Buat direktori bersama dan amati efek SGID sederhana

```
praditadf@praditadf-VirtualBox:~/lab-permissions$ mkdir shared-dir
praditadf@praditadf-VirtualBox:~/lab-permissions$ chmod g+s shared-dir
praditadf@praditadf-VirtualBox:~/lab-permissions$ ls -ld shared-dir
drwxrwsr-x 2 praditadf praditadf 4096 May  6 10:55 shared-dir
```

### Langkah 5: Uji efek umask pada file baru

```
praditadf@praditadf-VirtualBox:~/lab-permissions$ umask
0002
praditadf@praditadf-VirtualBox:~/lab-permissions$ umask 027
praditadf@praditadf-VirtualBox:~/lab-permissions$ touch testfile-027
praditadf@praditadf-VirtualBox:~/lab-permissions$ ls -l testfile-027
-rw-r----- 1 praditadf praditadf 0 May  6 10:56 testfile-027
```

### Analisis

1. Mengapa secret.txt tidak dapat dibaca oleh group dan others setelah chmod 600?
2. Apa perbedaan arti 600 dan 755 terhadap file yang diuji?
3. Setelah umask 027, permission apa yang dihasilkan untuk file baru, dan mengapa bukan 777?

### Tantangan

Ubah owner atau group salah satu file uji ke akun atau group lain yang tersedia di sistem, kemudian jelaskan
perubahan output ls -l sebelum dan sesudahnya.

```
praditadf@praditadf-VirtualBox:~/lab-permissions$ ls -l
total 12
-rwxr-xr-x 1 praditadf praditadf   23 May  6 10:51 myscript.sh
-rw------- 1 praditadf praditadf   13 May  6 10:50 secret.txt
drwxrwsr-x 2 praditadf praditadf 4096 May  6 10:55 shared-dir
-rw-r----- 1 praditadf praditadf    0 May  6 10:56 testfile-027
praditadf@praditadf-VirtualBox:~/lab-permissions$ chmod 640 secret.txt
praditadf@praditadf-VirtualBox:~/lab-permissions$ ls -l
total 12
-rwxr-xr-x 1 praditadf praditadf   23 May  6 10:51 myscript.sh
-rw-r----- 1 praditadf praditadf   13 May  6 10:50 secret.txt
drwxrwsr-x 2 praditadf praditadf 4096 May  6 10:55 shared-dir
-rw-r----- 1 praditadf praditadf    0 May  6 10:56 testfile-027
```

## Praktikum 9.2 — ACL

### Langkah 1: Siapkan file dan lihat permission standar tanpa ACL tambahan

```
praditadf@praditadf-VirtualBox:~$ mkdir ~/lab-acl && cd ~/lab-acl
praditadf@praditadf-VirtualBox:~/lab-acl$ echo "Data penting" > confidential.txt
praditadf@praditadf-VirtualBox:~/lab-acl$ chmod 640 confidential.txt
praditadf@praditadf-VirtualBox:~/lab-acl$ ls -l confidential.txt 
-rw-r----- 1 praditadf praditadf 13 May  6 11:14 confidential.txt
praditadf@praditadf-VirtualBox:~/lab-acl$ getfacl confidential.txt 
# file: confidential.txt
# owner: praditadf
# group: praditadf
user::rw-
group::r--
other::---
```

### Langkah 2: Beri akses baca ke satu user tertentu tanpa mengubah owner atau group

```
praditadf@praditadf-VirtualBox:~/lab-acl$ setfacl -m u:praditadf:r confidential.txt
praditadf@praditadf-VirtualBox:~/lab-acl$ ls -l confidential.txt 
-rw-r-----+ 1 praditadf praditadf 13 May  6 11:14 confidential.txt
praditadf@praditadf-VirtualBox:~/lab-acl$ getfacl confidential.txt 
# file: confidential.txt
# owner: praditadf
# group: praditadf
user::rw-
user:praditadf:r--
group::r--
mask::r--
other::---
```

### Langkah 3: Buat direktori bersama yang mewariskan ACL ke file baru

```
```

### Analisis

1. Mengapa getfacl confidential.txt awalnya tidak menampilkan user tertentu?
2. Setelah setfacl -m u:userA:r confidential.txt, apa perbedaan output ls -l dan getfacl?
3. Mengapa file inherited.txt mewarisi ACL dari direktori shared?

### Tantangan

Tambahkan satu ACL lagi agar group readonly-group hanya dapat membaca confidential.txt. Setelah
itu, hapus ACL untuk userA dan verifikasi hasil akhirnya dengan getfacl.

## Praktikum 9.3A — Membuat dan Mengelola User

### Buat dua user

```
```

### Verifikasi

```
```

### Modifikasi shell userA

```
```

### Lock dan unlock userB

```
```

### Pertanyaan

1. Apa perbedaan output id userA sebelum dan sesudah menambah group?
2. Bagaimana status passwd -S userB berubah saat akun di-lock?

## Praktikum 9.3B — Group Management

### Buat dua group

```
```

### Tambahkan userA ke kedua group

```
```

### Tambahkan userB hanya ke readonly - group

```
```

### Verifikasi

### Pertanyaan

1. Apa yang ditampilkan id userA vs groups userA?
2. Mengapa -a pada usermod -aG penting?

## Praktikum 9.3C — Password Aging Policy

### Set aging policy untuk userA

```
```

### Paksa userA ganti password saat login pertama

```
```

### Kunci password userB

```
```

### Unlock kembali

```
```

### Pertanyaan

1. Apa arti nilai yang ditampilkan chage -l userA?
2. Bagaimana cara membuktikan userB terkunci dari output passwd -S?
3. Kapan sebaiknya menggunakan chage -d 0 vs passwd -e?
Tantangan
Buat user bernama intern yang:
• memiliki shell /bin/bash;
• menjadi anggota labgroup;
• dipaksa ganti password pada login pertama;
• password expired setelah 45 hari dengan warning 7 hari sebelumnya.

## Praktikum 9.4 — Konfigurasi sudo

### Langkah 1: Buat file konfigurasi sudo khusus untuk userA

```
```

### Langkah 2: Verifikasi aturan yang aktif dan uji hasilnya

```
```

### Analisis

1. Mengapa aturan disimpan di /etc/sudoers.d//, bukan langsung di /etc/sudoers?
2. Mana perintah yang bisa dijalankan tanpa password, dan mana yang masih perlu autentikasi?
3. Informasi apa saja yang dicatat di log sudo?

### Tantangan

Tambahkan satu aturan baru agar userA boleh menjalankan /bin/systemctl restart ssh tetapi tidak boleh
menjalankan reboot.

## Praktikum 9.5 — Disk Quota

### Langkah 1: Buat image filesystem kecil dan mount dengan opsi quota

```
```

### Langkah 2: Buat database quota dan aktifkan enforcement

```
```

### Langkah 3: Tetapkan quota untuk user uji dan amati hasilnya

```
```

### Langkah 4: Bersihkan lingkungan uji setelah selesai

```
```

### Analisis

1. Apa perbedaan soft limit dan hard limit saat quota mulai terlampaui?
2. Mengapa praktikum ini memakai loopback filesystem, bukan langsung /home/?
3. Dari output repquota, informasi apa yang menunjukkan quota sudah aktif?

### Tantangan

Coba atur quota baru untuk userA dengan batas inode yang sangat kecil, kemudian jelaskan kapan pembatasan
inode lebih penting daripada pembatasan block.

# Latihan

## Latihan Latihan 9.A — Audit dan Kolaborasi

1. Temukan file SUID aktif dengan find / -perm -4000 -type f 2>/dev/null, lalu jelaskan tiga file yang Anda kenali beserta alasannya.
2. Cari direktori world-writable dan tentukan mana yang valid dan mana yang berisiko.
3. Rancang konfigurasi permission standar dan ACL untuk direktori proyek /srv/webapp/ agar group webapp-team dapat menulis, user deploy hanya membaca, dan file baru selalu mewarisi group proyek.

## Latihan Latihan 9.B — Kebijakan Akun dan Quota

Tuliskan langkah untuk membuat user intern, menambahkannya ke group labgroup, memaksa pergantian password tiap 45 hari (warning 7 hari), memberi izin sudo hanya untuk systemctl status, dan ### menetapkan quota ruang serta inode sederhana pada /home/.
