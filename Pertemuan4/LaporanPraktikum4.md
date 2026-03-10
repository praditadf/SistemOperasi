## TUGAS PENDAHULUAN:

Jawablah pertanyaan-pertanyaan di bawah ini :

1. Apa yang dimaksud perintah-perintah direktory : pwd, cd, mkdir, rmdir.
2. Apa yang dimaksud perintah-perintah manipulasi file : cp, mv, dan rm (sertakan format yang digunakan)
3. Jelaskan perbedaan *Symbolic link* menggunakan *hard link (direct)* dan *soft link (indirect)*
4. Tuliskan maksud perintah-perintah : file, find, which, locate dan grep.
   
**Jawaban**

1. * pwd   : berfungsi untuk menampilkan lokasi direktori saat ini
   * cd    : Digunakan untuk mengubah lokai direktori yang digunakan
   * mkdir : Digunakan untuk membuat direktori baru
   * rmdir : berfungsi untuk menghapus direktori

2. * cp   : Perintah untuk menyalin file atau direktori ke lokasi lain
   * mv   : Perintah untuk memindahkan file atau direktori ke lokasi lain
   * rm   : Perintah untuk menghapus file atau direktori

3. * *Symbolic link* *hard link (direct)*   : kedua file akan muncul identik, dan jika file asli atau file duplikat diubah perubahan akan terjadi pada file lainnya
   * *Symbolic link* *soft link (indirect)* : file akan menjadi 1 (link) dan file tersebut merujuk ke tempat asal

4. * file      : Digunakan untuk melihat jenis file
   * find      : Digunakan untuk melihat pohon direktori serta melihat file dengan nama tersebut
   * which     : Digunakan untuk mengetahui letak system utility
   * locate    : Digunakan untuk mecari mencari file pada semua directori dengan lebih cepat dan ditampilkan dengan path yang penuh
   * grep      : Dogunakan untuk mencari file yang bernama sesuai pattern yang diberikan dan akan menampilkan baris yang sesuai
  
## PERCOBAAN:

1. Login sebagai user.
2. Bukalah Console Terminal dan lakukan percobaan-percobaan di bawah ini.
   Perhatikan hasilnya.
3. Selesaikan soal-soal latihan

### Percobaan 1 : Direktory

1. Melihat direktori HOME

   *$ pwd*

   *$ echo* $HOME*

   ```
   praditadf@praditadf-VirtualBox:~$ pwd
   /home/praditadf
   praditadf@praditadf-VirtualBox:~$ echo $HOME
   /home/praditadf

2. Melihat direktori aktual dan parent direktori

   *$ pwd*

   *$ cd .*

   *$ pwd*

   *$ cd ..*

   *$ pwd*

   *$ cd*
   ```
   praditadf@praditadf-VirtualBox:~$ pwd
   /home/praditadf
   praditadf@praditadf-VirtualBox:~$ cd .
   praditadf@praditadf-VirtualBox:~$ pwd
   /home/praditadf
   praditadf@praditadf-VirtualBox:~$ cd ..
   praditadf@praditadf-VirtualBox:/home$ pwd
   /home
   praditadf@praditadf-VirtualBox:/home$ cd
   praditadf@praditadf-VirtualBox:~$ 

3. Membuat satu direktori, lebih dari satu direktori atau sub direktori

   *$ pwd*

   *$ mkdir A B C A/D A/E B/F A/D/A*

   *$ ls -l*

   *$ ls -l A*

   *$ ls -l A/D*
```
praditadf@praditadf-VirtualBox:~$ pwd
/home/praditadf
praditadf@praditadf-VirtualBox:~$ mkdir A B C A/D A/E B/F A/D/A
praditadf@praditadf-VirtualBox:~$ ls -l
total 228
drwxrwxr-x 4 praditadf praditadf   4096 Mar 10 19:17 A
-rw-r--r-- 1 praditadf praditadf   1761 Feb 24 18:16 aaaaaaa
drwxrwxr-x 3 praditadf praditadf   4096 Mar 10 19:17 B
-rw-rw-r-- 1 praditadf praditadf   3229 Mar  4 10:46 backup-error.log
-rwxrwxr-x 1 praditadf praditadf    151 Mar  4 10:45 backup.sh
-rw-rw-r-- 1 praditadf praditadf    951 Mar  4 10:46 backup-succes.log
-rw-rw-r-- 1 praditadf praditadf      0 Mar  3 18:51 backup-success.log
-rw-rw-r-- 1 praditadf praditadf     45 Mar  4 10:46 backup.tar.gz
drwxrwxr-x 2 praditadf praditadf   4096 Mar 10 19:17 C
-rw-rw-r-- 1 praditadf praditadf     44 Feb 24 18:20 config.txt
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Desktop
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Documents
drwxr-xr-x 2 praditadf praditadf   4096 Mar  4 13:14 Downloads
-rw-rw-r-- 1 praditadf praditadf      0 Mar  3 17:16 error.log
drwxrwxr-x 3 praditadf praditadf   4096 Mar  4 11:55 Github
-rw-rw-r-- 1 praditadf praditadf    799 Mar  3 17:16 large-logs.txt
-rw-rw-r-- 1 praditadf praditadf   3432 Mar  3 18:13 log.txt
-rw-rw-r-- 1 praditadf praditadf    139 Mar  4 10:11 monitor.sh
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Music
-rw-rw-r-- 1 praditadf praditadf 110870 Mar  3 18:26 path.txt
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Pictures
-rw-rw-r-- 1 praditadf praditadf   9947 Mar  3 17:41 ping-log.txt
drwxrwxr-x 3 praditadf praditadf   4096 Mar  9 20:53 praktikum-os
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Public
drwx------ 7 praditadf praditadf   4096 Mar  4 11:45 snap
-rw-rw-r-- 1 praditadf praditadf    411 Mar  3 17:31 sorted-users.txt
-rw-rw-r-- 1 praditadf praditadf    112 Mar  3 17:48 system
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Templates
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Videos
-rw-rw-r-- 1 praditadf praditadf    381 Mar  4 11:09 wget-log
praditadf@praditadf-VirtualBox:~$ ls -l A
total 8
drwxrwxr-x 3 praditadf praditadf 4096 Mar 10 19:17 D
drwxrwxr-x 2 praditadf praditadf 4096 Mar 10 19:17 E
praditadf@praditadf-VirtualBox:~$ ls -l A/D
total 4
drwxrwxr-x 2 praditadf praditadf 4096 Mar 10 19:17 A
```

4. Menghapus satu atau lebih direktori hanya dapat dilakukan pada direktori kosong dan hanya dapat dihapus oleh pemiliknya kecuali bila diberikan ijin aksesnya

   *$ rmdir B* (Terdapat pesan error, mengapa ?) Karena direktori tersebut tidak kosong terdapat direktori F

   *$ ls -l B*

   *$ rmdir B/F B*

   *$ ls -l B* (Terdapat pesan error, me ngapa ?) Karena direktori tersebut sudah di hapus

``` praditadf@praditadf-VirtualBox:~$ rmdir B
rmdir: failed to remove 'B': Directory not empty
praditadf@praditadf-VirtualBox:~$ ls -l B
total 4
drwxrwxr-x 2 praditadf praditadf 4096 Mar 10 19:17 F
praditadf@praditadf-VirtualBox:~$ rmdir B/F B
praditadf@praditadf-VirtualBox:~$ ls -l B
ls: cannot access 'B': No such file or directory
```

5. Navigasi direktori dengan instruksi cd untuk pindah dari satu direktori ke direktori lain.

   *$ pwd*

   *$ ls -l*

   *$ cd A*

   *$ pwd*

   *$ cd ..*

   *$ pwd*

   *$ cd /home/<user>/C*

   *$ pwd*

   *$ cd /<user/C* (Terdapat pesan error, mengapa ?) Karena sistem mencari folder user pada yang berada direktori paling dasar sedangkan folder root terdapat pada direktori home

   *$ pwd*
```
praditadf@praditadf-VirtualBox:~$ pwd
/home/praditadf
praditadf@praditadf-VirtualBox:~$ ls -l
total 224
drwxrwxr-x 4 praditadf praditadf   4096 Mar 10 19:17 A
-rw-r--r-- 1 praditadf praditadf   1761 Feb 24 18:16 aaaaaaa
-rw-rw-r-- 1 praditadf praditadf   3229 Mar  4 10:46 backup-error.log
-rwxrwxr-x 1 praditadf praditadf    151 Mar  4 10:45 backup.sh
-rw-rw-r-- 1 praditadf praditadf    951 Mar  4 10:46 backup-succes.log
-rw-rw-r-- 1 praditadf praditadf      0 Mar  3 18:51 backup-success.log
-rw-rw-r-- 1 praditadf praditadf     45 Mar  4 10:46 backup.tar.gz
drwxrwxr-x 2 praditadf praditadf   4096 Mar 10 19:17 C
-rw-rw-r-- 1 praditadf praditadf     44 Feb 24 18:20 config.txt
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Desktop
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Documents
drwxr-xr-x 2 praditadf praditadf   4096 Mar  4 13:14 Downloads
-rw-rw-r-- 1 praditadf praditadf      0 Mar  3 17:16 error.log
drwxrwxr-x 3 praditadf praditadf   4096 Mar  4 11:55 Github
-rw-rw-r-- 1 praditadf praditadf    799 Mar  3 17:16 large-logs.txt
-rw-rw-r-- 1 praditadf praditadf   3432 Mar  3 18:13 log.txt
-rw-rw-r-- 1 praditadf praditadf    139 Mar  4 10:11 monitor.sh
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Music
-rw-rw-r-- 1 praditadf praditadf 110870 Mar  3 18:26 path.txt
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Pictures
-rw-rw-r-- 1 praditadf praditadf   9947 Mar  3 17:41 ping-log.txt
drwxrwxr-x 3 praditadf praditadf   4096 Mar  9 20:53 praktikum-os
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Public
drwx------ 7 praditadf praditadf   4096 Mar  4 11:45 snap
-rw-rw-r-- 1 praditadf praditadf    411 Mar  3 17:31 sorted-users.txt
-rw-rw-r-- 1 praditadf praditadf    112 Mar  3 17:48 system
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Templates
drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Videos
-rw-rw-r-- 1 praditadf praditadf    381 Mar  4 11:09 wget-log
praditadf@praditadf-VirtualBox:~$ cd A
praditadf@praditadf-VirtualBox:~/A$ pwd
/home/praditadf/A
praditadf@praditadf-VirtualBox:~/A$ cd ..
praditadf@praditadf-VirtualBox:~$ pwd
/home/praditadf
praditadf@praditadf-VirtualBox:~$ cd /home/praditadf/C
praditadf@praditadf-VirtualBox:~/C$ pwd
/home/praditadf/C
praditadf@praditadf-VirtualBox:~/C$ cd /praditadf/C
bash: cd: /praditadf/C: No such file or directory
praditadf@praditadf-VirtualBox:~/C$ pwd
/home/praditadf/C
```

### Percobaan 2 : Manipulasi file

1. Perintah cp untuk mengkopi file atau seluruh direktori

   *$ cat* > contoh

   Membuat sebuah file

   *[Ctrl-d]*

   *$ cp* contoh contoh1

   *$ ls -l*

   *$ cp contoh A*

   *$ ls –l A*

   *$ cp contoh contoh1 A/D*

   *$ ls –l A/D*

2. Perintah mv untuk memindah file

   *$ mv contoh contoh2*

   *$ ls -l*

   *$ mv contoh1 contoh2 A/D*

   *$ ls –l A/D*

   *$ mv contoh contoh1 C*
*
   *$ ls –l C*

3. Perintah rm untuk menghapus file

   *$ rm contoh2*

   *$ ls -l*

   *$ rm –i contoh*

   *$ rm –rf A C*

   *$ ls -l*

### Percobaan 3 : Symbolic Link

1. Membuat shortcut (file link)

   *$ echo "Hallo apa khabar" > halo.txt*
   
   *$ ls -l*
   
   *$ ln halo.txt z*
   
   *$ ls -l*
   
   *$ cat z*
   
   *$ mkdir mydir*
   
   *$ ln z mydir/halo.juga*
   
   *$ cat mydir/halo.juga*
   
   *$ ln -s z bye.txt*
   
   *$ ls -l bye.txt*
   
   *$ cat bye.txt*

### Percobaan 4 : Melihat Isi File

1. *$ ls –l*

   *$ file halo.txt*

   *$ file bye.txt*

### Percobaan 5 : Mencari file

1. Perintah find

   *$ find /home –name “_.txt” –print > myerror.txt*
   
   *$ cat myerror.txt*
   
   *$ find . –name “_.txt” –exec wc –l ‘{}’ ‘;’*
2. Perintah which

   *$ which ls*

3. Perintah locate

   *$ locate “\*.txt”*

### Percobaan 6 : Mencari text pada file

1. *$ grep Hallo \*.txt*

## LATIHAN:

1. Cobalah urutan perintah berikut :

   *$ cd*
   
   *$ pwd*
   
   *$ ls –al*
   
   *$ cd .*
   
   *$ pwd*
   
   *$ cd ..*
   
   *$ pwd*
   
   *$ ls -al*
   
   *$ cd ..*
   
   *$ pwd*
   
   *$ ls -al*
   
   *$ cd /etc*
   
   *$ ls –al | more*
   
   *$ cat passwd*
   
   *$ cd –*
   
   *$ pwd*

2. Lanjutkan penelusuran pohon pada sistem file menggunakan cd, ls, pwd dan cat.
   Telusuri direktory /bin, /usr/bin, /sbin, /tmp dan /boot.
3. Telusuri direktory /dev. Identifikasi perangkat yang tersedia. Identifikasi tty
   (termninal) Anda (ketik who am i); siapa pemilih tty Anda (gunakan ls –l).
4. Telusuri derectory /proc. Tampilkan isi file interrupts, devices,
   cpuinfo, meminfo dan uptime menggunakan perintah cat. Dapatkah Anda
   melihat mengapa directory /proc disebut pseudo -filesystem yang memungkinkan
   akses ke struktur data kernel ?
5. Ubahlah direktory home ke user lain secara langsung menggunakan cd ~username.
6. Ubah kembali ke direktory home Anda.
7. Buat subdirektory work dan play.
8. Hapus subdirektory work.
9. Copy file /etc/passwd ke direktory home Anda.
10. Pindahkan ke subirectory play.
11. Ubahlah ke subdirektory play dan buat symbolic link dengan nama terminal yang
    menunjuk ke perangkat tty. Apa yang terjadi jika melakukan hard link ke perangkat
    tty ?
12. Buatlah file bernama hello.txt yang berisi kata ”hello word”. Dapatkah Anda
    gunakan ”cp” menggunakan ”terminal” sebagai file asal untuk menghasilkan efek
    yang sama ?
13. Copy hello.txt ke terminal. Apa yang terjadi ?
14. Masih direktory home, copy keseluruhan direktory play ke direktory bernama work
    menggunakan symbolic link.
15. Hapus direktory work dan isinya dengan satu perintah

## LAPORAN RESMI:

1. Analisa hasil percobaan yang Anda lakukan.
   a. Analisa setiap hasil tampilannya.
   b. Pada Percobaan 1 point 3 buatlah pohon dari struktur file dan direktori
   c. Bila terdapat pesan error, jelaskan penyebabnya.
2. Kerjakan latihan diatas dan analisa hasil tampilannya.
3. Berikan kesimpulan dari praktikum ini.
