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
```
Karena chmod 600 hanya memberikan akses membaca dan menulis isi file ke user, dan untuk group dan other tidak diberikan izin apapun dengan pemberian angka 0 pada group dan other
```
2. Apa perbedaan arti 600 dan 755 terhadap file yang diuji?
```
600 : hanya user yang dapat membaca dan menulis isi file
755 : user dapat membaca, menulis, mengeksekusi file, group dapat membaca dan mengeksekusi, dan other dapat menbaca dan mengeksekusi
```
3. Setelah umask 027, permission apa yang dihasilkan untuk file baru, dan mengapa bukan 777?
```
permission yang dihasilkan untuk file baru yaitu 640
```

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
perintah chmod 640 secret.txt, mengubah permission file yang awalnya hanya user yang dapat membaca dan menulis isi file(-rw-------), menjadi user membaca dan menulis isi file, dan group dapat membaca (-rw-r-----)

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
praditadf@Ubuntu-Server:~/lab-acl$ setfacl -m u:userA:r confidential.txt
setfacl: Option -m: Invalid argument near character 3
praditadf@Ubuntu-Server:~/lab-acl$ ls -l confidential.txt
-rw-r----- 1 praditadf praditadf 13 May  6 08:02 confidential.txt
praditadf@Ubuntu-Server:~/lab-acl$ getfacl confidential.txt
# file: confidential.txt
# owner: praditadf
# group: praditadf
user::rw-
group::r--
other::---
```

### Langkah 3: Buat direktori bersama yang mewariskan ACL ke file baru

```
praditadf@Ubuntu-Server:~/lab-acl$ mkdir shared
praditadf@Ubuntu-Server:~/lab-acl$ setfacl -d -m u:userA:rwx shared
setfacl: Option -m: Invalid argument near character 3
praditadf@Ubuntu-Server:~/lab-acl$ setfacl -d -m u:userB:r-x shared
setfacl: Option -m: Invalid argument near character 3
praditadf@Ubuntu-Server:~/lab-acl$ getfacl shared
# file: shared
# owner: praditadf
# group: praditadf
user::rwx
group::rwx
other::r-x

praditadf@Ubuntu-Server:~/lab-acl$ touch shared/inherited.txt
praditadf@Ubuntu-Server:~/lab-acl$ getfacl shared/inherited.txt
# file: shared/inherited.txt
# owner: praditadf
# group: praditadf
user::rw-
group::rw-
other::r--
```

### Analisis

1. Mengapa getfacl confidential.txt awalnya tidak menampilkan user tertentu?
```
Pada output pertama Anda, getfacl hanya menampilkan izin dasar: user::rw-, group::r--, other::---. tidak menampilkan user tertentu karena file tersebut belum ditambahkan ACL
```
2. Setelah setfacl -m u:userA:r confidential.txt, apa perbedaan output ls -l dan getfacl?
```
setelah perintah setfacl -m u:userA:r confidential.txt mengalami Invalid argument near character 3 karena saat itu userA belum dibuat sehingga tidak ada perbedaan output
```
3. Mengapa file inherited.txt mewarisi ACL dari direktori shared?
```
karena sebelumnya menggunakan setfacl -d yaitu menetapkan ACL pada direktori sehingga inherited.txt juga mewarisi ACL tersebut
```

### Tantangan

Tambahkan satu ACL lagi agar group readonly-group hanya dapat membaca confidential.txt. Setelah
itu, hapus ACL untuk userA dan verifikasi hasil akhirnya dengan getfacl.

```
praditadf@Ubuntu-Server:~/lab-acl$ setfacl -m g:readonly-group:r confidential.txt
setfacl: Option -m: Invalid argument near character 3
praditadf@Ubuntu-Server:~/lab-acl$ setfacl -x u:userA confidential.txt
setfacl: Option -x: Invalid argument near character 3
praditadf@Ubuntu-Server:~/lab-acl$ getfacl confidential.txt
# file: confidential.txt
# owner: praditadf
# group: praditadf
user::rw-
group::r--
other::---
```

## Praktikum 9.3A — Membuat dan Mengelola User

### Buat dua user

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo useradd -m -s /bin/bash userA
praditadf@Ubuntu-Server:~/lab-acl$ sudo useradd -m -s /bin/bash userB
praditadf@Ubuntu-Server:~/lab-acl$ sudo passwd userA
New password:
Retype new password:
passwd: password updated successfully
praditadf@Ubuntu-Server:~/lab-acl$ sudo passwd userB
New password:
Retype new password:
passwd: password updated successfully
```

### Verifikasi

```
praditadf@Ubuntu-Server:~/lab-acl$ id userA
uid=1001(userA) gid=1001(userA) groups=1001(userA)
praditadf@Ubuntu-Server:~/lab-acl$ getent passwd userA
userA:x:1001:1001::/home/userA:/bin/bash
```

### Modifikasi shell userA

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo usermod -s /bin/zsh userA
usermod: no changes
praditadf@Ubuntu-Server:~/lab-acl$ getent passwd userA
userA:x:1001:1001::/home/userA:/bin/zsh
```

### Lock dan unlock userB

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo usermod -L userB
praditadf@Ubuntu-Server:~/lab-acl$ sudo passwd -S userB
userB L 2026-05-08 0 99999 7 -1
praditadf@Ubuntu-Server:~/lab-acl$ sudo usermod -U userB
praditadf@Ubuntu-Server:~/lab-acl$ sudo passwd -S userB
userB P 2026-05-08 0 99999 7 -1
```

### Pertanyaan

1. Apa perbedaan output id userA sebelum dan sesudah menambah group?
```
sebelum menambah group
uid=1001(userA) gid=1001(userA) groups=1001(userA)
setelah menambah group
uid=1001(userA) gid=1001(userA) groups=1001(userA),1003(labgroup),1004(readonly-group)
```
2. Bagaimana status passwd -S userB berubah saat akun di-lock?
```
Status setelah akun di lock
userB L 2026-05-08 0 99999 7 -1
Huruf L menampilkan bahwa akun tersebut di lock
```

## Praktikum 9.3B — Group Management

### Buat dua group

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo groupadd labgroup
praditadf@Ubuntu-Server:~/lab-acl$ sudo groupadd readonly-group
```

### Tambahkan userA ke kedua group

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo usermod -aG labgroup,readonly-group userA
```

### Tambahkan userB hanya ke readonly - group

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo usermod -aG readonly-group userB
```

### Verifikasi

```
praditadf@Ubuntu-Server:~/lab-acl$ id userA
uid=1001(userA) gid=1001(userA) groups=1001(userA),1003(labgroup),1004(readonly-group)
praditadf@Ubuntu-Server:~/lab-acl$ id userB
uid=1002(userB) gid=1002(userB) groups=1002(userB),1004(readonly-group)
praditadf@Ubuntu-Server:~/lab-acl$ getent group labgroup
labgroup:x:1003:userA
praditadf@Ubuntu-Server:~/lab-acl$ getent group readonly-group
readonly-group:x:1004:userA,userB
```

### Pertanyaan

1. Apa yang ditampilkan id userA vs groups userA?
```
uid=1001(userA) gid=1001(userA) groups=1001(userA),1003(labgroup),1004(readonly-group)
```
2. Mengapa -a pada usermod -aG penting?
```
Karena jika tanpa -a, semua supplementary group lama akan diganti
```

## Praktikum 9.3C — Password Aging Policy

### Set aging policy untuk userA

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo chage -M 60 -W 7 -m 1 userA
praditadf@Ubuntu-Server:~/lab-acl$ sudo chage -l userA
Last password change                                    : May 08, 2026
Password expires                                        : Jul 07, 2026
Password inactive                                       : never
Account expires                                         : never
Minimum number of days between password change          : 1
Maximum number of days between password change          : 60
Number of days of warning before password expires       : 7
```

### Paksa userA ganti password saat login pertama

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo chage -d 0 userA
```

### Kunci password userB

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo passwd -l userB
passwd: password changed.
praditadf@Ubuntu-Server:~/lab-acl$ sudo passwd -S userB
userB L 2026-05-08 0 99999 7 -1
```

### Unlock kembali

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo passwd -u userB
passwd: password changed.
praditadf@Ubuntu-Server:~/lab-acl$ sudo passwd -S userB
userB P 2026-05-08 0 99999 7 -1
```

### Pertanyaan

1. Apa arti nilai yang ditampilkan chage -l userA?

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo chage -l userA
Last password change                                    : password must be changed
Password expires                                        : password must be changed
Password inactive                                       : password must be changed
Account expires                                         : never
Minimum number of days between password change          : 1
Maximum number of days between password change          : 60
Number of days of warning before password expires       : 7
```

2. Bagaimana cara membuktikan userB terkunci dari output passwd -S?
```
praditadf@Ubuntu-Server:~/lab-acl$ sudo passwd -S userB
userB L 2026-05-08 0 99999 7 -1
Huruf L berarti userB tekunci
```

3. Kapan sebaiknya menggunakan chage -d 0 vs passwd -e?
```
chage -d 0 : Digunakan ketika menggunakan banyak parameter sekaligus
passwd -e  : Digunakan ketika hanya untuk mengubah password saat login
```

### Tantangan

Buat user bernama intern yang:
- memiliki shell /bin/bash;
- menjadi anggota labgroup;
- dipaksa ganti password pada login pertama;
- password expired setelah 45 hari dengan warning 7 hari sebelumnya.

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo useradd -m -s /bin/bash -G labgroup intern
praditadf@Ubuntu-Server:~/lab-acl$ sudo passwd intern
New password:
Retype new password:
Sorry, passwords do not match.
passwd: Authentication token manipulation error
passwd: password unchanged
praditadf@Ubuntu-Server:~/lab-acl$ sudo passwd intern
New password:
Retype new password:
passwd: password updated successfully
praditadf@Ubuntu-Server:~/lab-acl$ sudo chage -M 45 -W 7 -d 0 intern
praditadf@Ubuntu-Server:~/lab-acl$ id intern
uid=1003(intern) gid=1005(intern) groups=1005(intern),1003(labgroup)
praditadf@Ubuntu-Server:~/lab-acl$ sudo chage -l intern
Last password change                                    : password must be changed
Password expires                                        : password must be changed
Password inactive                                       : password must be changed
Account expires                                         : never
Minimum number of days between password change          : 0
Maximum number of days between password change          : 45
Number of days of warning before password expires       : 7
```

## Praktikum 9.4 — Konfigurasi sudo

### Langkah 1: Buat file konfigurasi sudo khusus untuk userA

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo visudo -f /etc/sudoers.d/lab-userA
userA ALL=(root) NOPASSWD: /usr/bin/apt update, /usr/bin/apt upgrade
userA ALL=(root) /bin/systemctl status *
```

### Langkah 2: Verifikasi aturan yang aktif dan uji hasilnya

```
praditadf@Ubuntu-Server:~/lab-acl$ sudo -l -U userA
Matching Defaults entries for userA on Ubuntu-Server:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin,
    use_pty

User userA may run the following commands on Ubuntu-Server:
    (root) NOPASSWD: /usr/bin/apt update, /usr/bin/apt upgrade
    (root) /bin/systemctl status *
praditadf@Ubuntu-Server:~/lab-acl$ sudo grep "userA" /var/log/auth.log | tail -10
2026-05-08T12:51:02.338816+00:00 Ubuntu-Server usermod[2076]: add 'userA' to shadow group 'labgroup'
2026-05-08T12:51:02.338988+00:00 Ubuntu-Server usermod[2076]: add 'userA' to shadow group 'readonly-group'
2026-05-08T12:53:36.347936+00:00 Ubuntu-Server sudo: praditadf : TTY=pts/0 ; PWD=/home/praditadf/lab-acl ; USER=root ; COMMAND=/usr/bin/chage -M 60 -W 7 -m 1 userA
2026-05-08T12:53:36.451427+00:00 Ubuntu-Server chage[2101]: changed password expiry for userA
2026-05-08T12:53:40.614577+00:00 Ubuntu-Server sudo: praditadf : TTY=pts/0 ; PWD=/home/praditadf/lab-acl ; USER=root ; COMMAND=/usr/bin/chage -l userA
2026-05-08T12:53:47.377039+00:00 Ubuntu-Server sudo: praditadf : TTY=pts/0 ; PWD=/home/praditadf/lab-acl ; USER=root ; COMMAND=/usr/bin/chage -d 0 userA
2026-05-08T12:53:47.555922+00:00 Ubuntu-Server chage[2111]: changed password expiry for userA
2026-05-08T12:56:24.582641+00:00 Ubuntu-Server sudo: praditadf : TTY=pts/0 ; PWD=/home/praditadf/lab-acl ; USER=root ; COMMAND=/usr/bin/chage -l userA
2026-05-08T13:01:17.448136+00:00 Ubuntu-Server sudo: praditadf : TTY=pts/0 ; PWD=/home/praditadf/lab-acl ; USER=root ; COMMAND=/usr/sbin/visudo -f /etc/sudoers.d/lab-userA
2026-05-08T13:05:09.123419+00:00 Ubuntu-Server sudo: praditadf : TTY=pts/0 ; PWD=/home/praditadf/lab-acl ; USER=root ; COMMAND=/usr/bin/grep userA /var/log/auth.log
```

### Analisis

1. Mengapa aturan disimpan di /etc/sudoers.d//, bukan langsung di /etc/sudoers?
```
Karena digunakan sebagai praktik, sehingga ketika ada kesalahan tidak akan mempengaruhi sudo utama sistem
```
2. Mana perintah yang bisa dijalankan tanpa password, dan mana yang masih perlu autentikasi?
```
tanpa password : /usr/bin/apt update, /usr/bin/apt upgrade
autentifikasi  : /bin/systemctl status *
```
3. Informasi apa saja yang dicatat di log sudo?
```
Informasi yang dicatat di log sudo yaitu timestamp, nama server dan user yang mengeksekusi, nama terminal, direktori aktif, dan perintah yang dijalankan
```

### Tantangan

Tambahkan satu aturan baru agar userA boleh menjalankan /bin/systemctl restart ssh tetapi tidak boleh
menjalankan reboot.

```
userA ALL=(root) /bin/systemctl restart ssh, !/sbin/reboot, !/usr/sbin/reboot, !/bin/systemctl reboot
```

## Praktikum 9.5 — Disk Quota

### Langkah 1: Buat image filesystem kecil dan mount dengan opsi quota

```
praditadf@Ubuntu-Server:~$ sudo dd if=/dev/zero of=/tmp/quota-test.img bs=1M count=100
100+0 records in
100+0 records out
104857600 bytes (105 MB, 100 MiB) copied, 0.278522 s, 376 MB/s
praditadf@Ubuntu-Server:~$ sudo mkfs.ext4 /tmp/quota-test.img
mke2fs 1.47.0 (5-Feb-2023)
Discarding device blocks: done
Creating filesystem with 25600 4k blocks and 25600 inodes

Allocating group tables: done
Writing inode tables: done
Creating journal (1024 blocks): done
Writing superblocks and filesystem accounting information: done

praditadf@Ubuntu-Server:~$ sudo mkdir -p /mnt/quota-test
praditadf@Ubuntu-Server:~$ sudo mount -o loop,usrquota,grpquota /tmp/quota-test.img /mnt/quota-test
```

### Langkah 2: Buat database quota dan aktifkan enforcement

```
praditadf@Ubuntu-Server:~$ sudo quotacheck -cug /mnt/quota-test
praditadf@Ubuntu-Server:~$ sudo quotaon -v /mnt/quota-test
quotaon: Your kernel probably supports ext4 quota feature but you are using external quota files. Please switch your filesystem to use ext4 quota feature as external quota files on ext4 are deprecated.
/dev/loop0 [/mnt/quota-test]: group quotas turned on
/dev/loop0 [/mnt/quota-test]: user quotas turned on
praditadf@Ubuntu-Server:~$ sudo repquota /mnt/quota-test
*** Report for user quotas on device /dev/loop0
Block grace time: 7days; Inode grace time: 7days
                        Block limits                File limits
User            used    soft    hard  grace    used  soft  hard  grace
----------------------------------------------------------------------
root      --      20       0       0              2     0     0
```

### Langkah 3: Tetapkan quota untuk user uji dan amati hasilnya

```
praditadf@Ubuntu-Server:~$ sudo edquota -u userA
Disk quotas for user userA (uid 1001):
  Filesystem                   blocks       soft       hard     inodes     soft     hard
  /dev/loop0                        0          5120        10240          0        0        0
praditadf@Ubuntu-Server:~$ sudo repquota /mnt/quota-test
*** Report for user quotas on device /dev/loop0
Block grace time: 7days; Inode grace time: 7days
                        Block limits                File limits
User            used    soft    hard  grace    used  soft  hard  grace
----------------------------------------------------------------------
root      --      20       0       0              2     0     0
userA     --       0    5120   10240              1     2     5
```

### Langkah 4: Bersihkan lingkungan uji setelah selesai

```
praditadf@Ubuntu-Server:~$ sudo quotaoff /mnt/quota-test
praditadf@Ubuntu-Server:~$ sudo umount /mnt/quota-test
praditadf@Ubuntu-Server:~$ sudo rm /tmp/quota-test.img
```

### Analisis

1. Apa perbedaan soft limit dan hard limit saat quota mulai terlampaui?
```
Soft limit : Boleh dilampaui sementara selama grace period
Hard limit : Tidak boleh dilampaui sama sekali
```

2. Mengapa praktikum ini memakai loopback filesystem, bukan langsung /home/?
```
Agar praktikum aman, dan ketika terdapat error kita hanya tinggal menghapus file tersebut
```

3. Dari output repquota, informasi apa yang menunjukkan quota sudah aktif?
```
Berdasarkan output, terlihat pada kolom Block limits (soft: 5120, hard: 10240) dan File limits (soft: 2, hard: 5) nilai ini menunjukkan bahwa aturan quota untuk userA telah diaktifkan dan dicatat oleh sistem.
```

### Tantangan

Coba atur quota baru untuk userA dengan batas inode yang sangat kecil, kemudian jelaskan kapan pembatasan
inode lebih penting daripada pembatasan block.

```
praditadf@Ubuntu-Server:~$ sudo setquota -u userA 5120 10240 2 5 /mnt/quota-test
praditadf@Ubuntu-Server:~$ sudo repquota /mnt/quota-test
*** Report for user quotas on device /dev/loop0
Block grace time: 7days; Inode grace time: 7days
                        Block limits                File limits
User            used    soft    hard  grace    used  soft  hard  grace
----------------------------------------------------------------------
root      --      20       0       0              2     0     0
userA     --       0    5120   10240              2     2     5
```
Pembatasan inode menjadi jauh lebih penting daripada pembatasan block ketika ada risiko user membuat ribuan atau jutaan file berukuran sangat kecil. File sekecil apa pun mungkin tidak akan menghabiskan batas kapasitas hardisk, tetapi pasti memakan 1 jatah inode. Jika jatah inode habis, sistem akan lumpuh dan menolak pembuatan file baru meskipun sisa kapasitas disk masih besar.

# Latihan

## Latihan Latihan 9.A — Audit dan Kolaborasi

1. Temukan file SUID aktif dengan find / -perm -4000 -type f 2>/dev/null, lalu jelaskan tiga file yang Anda kenali beserta alasannya.
```
praditadf@Ubuntu-Server:~$ find / -perm -4000 -type f 2>/dev/null
/opt/VBoxGuestAdditions-7.2.6/bin/VBoxDRMClient
/usr/lib/dbus-1.0/dbus-daemon-launch-helper
/usr/lib/polkit-1/polkit-agent-helper-1
/usr/lib/openssh/ssh-keysign
/usr/bin/newgrp
/usr/bin/gpasswd
/usr/bin/chfn
/usr/bin/sudo
/usr/bin/umount
/usr/bin/mount
/usr/bin/chsh
/usr/bin/su
/usr/bin/passwd
/usr/bin/fusermount3

1. /usr/bin/passwd: Agar user biasa berhak menyimpan sandi baru ke file rahasia /etc/shadow
2. /usr/bin/sudo: Agar user biasa bisa meningkatkan hak istimewa untuk mengeksekusi perintah admin
3. /usr/bin/su: Membutuhkan akses sistem untuk verifikasi pangkalan data saat user berpindah sesi/identitas
```

2. Cari direktori world-writable dan tentukan mana yang valid dan mana yang berisiko.
```
praditadf@Ubuntu-Server:~$ find / -type d -perm -0002 2>/dev/null
/run/screen
/run/cloud-init/tmp
/run/lock
/tmp
/tmp/.XIM-unix
/tmp/.font-unix
/tmp/.X11-unix
/tmp/.ICE-unix
/dev/mqueue
/dev/shm
/var/tmp
/var/crash


- Valid : /tmp /tmp/.XIM-unix /tmp/.font-unix /tmp/.X11-unix /tmp/.ICE-unix /var/tmp
- Berisiko: /run/screen /run/cloud-init/tmp /run/lock /dev/mqueue /dev/shm /var/crash
```
3. Rancang konfigurasi permission standar dan ACL untuk direktori proyek /srv/webapp/ agar group webapp-team dapat menulis, user deploy hanya membaca, dan file baru selalu mewarisi group proyek.
```
praditadf@Ubuntu-Server:~$ sudo groupadd webapp-team
praditadf@Ubuntu-Server:~$ sudo useradd -m -s /bin/bash deploy
praditadf@Ubuntu-Server:~$ sudo mkdir -p /srv/webapp/
praditadf@Ubuntu-Server:~$ sudo chown root:webapp-team /srv/webapp/
praditadf@Ubuntu-Server:~$ sudo chmod 2775 /srv/webapp/
praditadf@Ubuntu-Server:~$ sudo setfacl -m u:deploy:r-x /srv/webapp/
praditadf@Ubuntu-Server:~$ sudo setfacl -d -m g:webapp-team:rwx /srv/webapp/
praditadf@Ubuntu-Server:~$ sudo setfacl -d -m u:deploy:r-x /srv/webapp/
praditadf@Ubuntu-Server:~$ getfacl /srv/webapp/
getfacl: Removing leading '/' from absolute path names
# file: srv/webapp/
# owner: root
# group: webapp-team
# flags: -s-
user::rwx
user:deploy:r-x
group::rwx
mask::rwx
other::r-x
default:user::rwx
default:user:deploy:r-x
default:group::rwx
default:group:webapp-team:rwx
default:mask::rwx
default:other::r-x
```

## Latihan Latihan 9.B — Kebijakan Akun dan Quota

Tuliskan langkah untuk membuat user intern, menambahkannya ke group labgroup, memaksa pergantian password tiap 45 hari (warning 7 hari), memberi izin sudo hanya untuk systemctl status, dan ### menetapkan quota ruang serta inode sederhana pada /home/.
```
praditadf@Ubuntu-Server:~$ sudo usermod -s /bin/bash -aG labgroup intern
praditadf@Ubuntu-Server:~$ sudo chage -M 45 -W 7 intern
praditadf@Ubuntu-Server:~$ echo 'intern ALL=(root) /bin/systemctl status *' | sudo tee /etc/sudoers.d/intern-rules
intern ALL=(root) /bin/systemctl status *
praditadf@Ubuntu-Server:~$ sudo chmod 0440 /etc/sudoers.d/intern-rules
praditadf@Ubuntu-Server:~$ sudo setquota -u intern 5120 10240 2 5 /mnt/quota-test
praditadf@Ubuntu-Server:~$ sudo touch /mnt/quota-test/file_intern.txt
praditadf@Ubuntu-Server:~$ sudo chown intern:intern /mnt/quota-test/file_intern.txt
praditadf@Ubuntu-Server:~$ sudo repquota /mnt/quota-test
*** Report for user quotas on device /dev/loop0
Block grace time: 7days; Inode grace time: 7days
                        Block limits                File limits
User            used    soft    hard  grace    used  soft  hard  grace
----------------------------------------------------------------------
root      --      20       0       0              2     0     0
intern    --       0    5120   10240              1     2     5
```