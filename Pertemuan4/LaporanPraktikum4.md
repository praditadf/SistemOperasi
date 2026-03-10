## TUGAS PENDAHULUAN

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
  
## PERCOBAAN

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

```   praditadf@praditadf-VirtualBox:~$ pwd
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

1. Menghapus satu atau lebih direktori hanya dapat dilakukan pada direktori kosong dan hanya dapat dihapus oleh pemiliknya kecuali bila diberikan ijin aksesnya

   *$ rmdir B* (Terdapat pesan error, mengapa ?) Karena direktori tersebut tidak kosong terdapat direktori F

   *$ ls -l B*

   *$ rmdir B/F B*

   *$ ls -l B* (Terdapat pesan error, me ngapa ?) Karena direktori tersebut sudah di hapus

```   praditadf@praditadf-VirtualBox:~$ rmdir B
   rmdir: failed to remove 'B': Directory not empty
   praditadf@praditadf-VirtualBox:~$ ls -l B
   total 4
   drwxrwxr-x 2 praditadf praditadf 4096 Mar 10 19:17 F
   praditadf@praditadf-VirtualBox:~$ rmdir B/F B
   praditadf@praditadf-VirtualBox:~$ ls -l B
   ls: cannot access 'B': No such file or directory
   ```

1. Navigasi direktori dengan instruksi cd untuk pindah dari satu direktori ke direktori lain.

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

   ```
   praditadf@praditadf-VirtualBox:~$ cat > contoh
   Membuat sebuah file
   praditadf@praditadf-VirtualBox:~$ cp contoh contoh1
   praditadf@praditadf-VirtualBox:~$ ls -l
   total 232
   drwxrwxr-x 4 praditadf praditadf   4096 Mar 10 19:17 A
   -rw-r--r-- 1 praditadf praditadf   1761 Feb 24 18:16 aaaaaaa
   -rw-rw-r-- 1 praditadf praditadf   3229 Mar  4 10:46 backup-error.log
   -rwxrwxr-x 1 praditadf praditadf    151 Mar  4 10:45 backup.sh
   -rw-rw-r-- 1 praditadf praditadf    951 Mar  4 10:46 backup-succes.log
   -rw-rw-r-- 1 praditadf praditadf      0 Mar  3 18:51 backup-success.log
   -rw-rw-r-- 1 praditadf praditadf     45 Mar  4 10:46 backup.tar.gz
   drwxrwxr-x 2 praditadf praditadf   4096 Mar 10 19:17 C
   -rw-rw-r-- 1 praditadf praditadf     44 Feb 24 18:20 config.txt
   -rw-rw-r-- 1 praditadf praditadf     20 Mar 10 19:53 contoh
   -rw-rw-r-- 1 praditadf praditadf     20 Mar 10 19:53 contoh1
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
   praditadf@praditadf-VirtualBox:~$ cp contoh A
   praditadf@praditadf-VirtualBox:~$ ls -l A
   total 12
   -rw-rw-r-- 1 praditadf praditadf   20 Mar 10 19:53 contoh
   drwxrwxr-x 3 praditadf praditadf 4096 Mar 10 19:17 D
   drwxrwxr-x 2 praditadf praditadf 4096 Mar 10 19:17 E
   praditadf@praditadf-VirtualBox:~$ cp contoh contoh1 A/D
   praditadf@praditadf-VirtualBox:~$ ls -l A/D
   total 12
   drwxrwxr-x 2 praditadf praditadf 4096 Mar 10 19:17 A
   -rw-rw-r-- 1 praditadf praditadf   20 Mar 10 19:53 contoh
   -rw-rw-r-- 1 praditadf praditadf   20 Mar 10 19:53 contoh1
   ```

2. Perintah mv untuk memindah file

   *$ mv contoh contoh2*

   *$ ls -l*

   *$ mv contoh1 contoh2 A/D*

   *$ ls –l A/D*

   *$ mv contoh contoh1 C*

   *$ ls –l C*

   ```praditadf@praditadf-VirtualBox:~$ mv contoh contoh2
   praditadf@praditadf-VirtualBox:~$ ls -l
   total 232
   drwxrwxr-x 4 praditadf praditadf   4096 Mar 10 19:53 A
   -rw-r--r-- 1 praditadf praditadf   1761 Feb 24 18:16 aaaaaaa
   -rw-rw-r-- 1 praditadf praditadf   3229 Mar  4 10:46 backup-error.log
   -rwxrwxr-x 1 praditadf praditadf    151 Mar  4 10:45 backup.sh
   -rw-rw-r-- 1 praditadf praditadf    951 Mar  4 10:46 backup-succes.log
   -rw-rw-r-- 1 praditadf praditadf      0 Mar  3 18:51 backup-success.log
   -rw-rw-r-- 1 praditadf praditadf     45 Mar  4 10:46 backup.tar.gz
   drwxrwxr-x 2 praditadf praditadf   4096 Mar 10 19:17 C
   -rw-rw-r-- 1 praditadf praditadf     44 Feb 24 18:20 config.txt
   -rw-rw-r-- 1 praditadf praditadf     20 Mar 10 19:53 contoh1
   -rw-rw-r-- 1 praditadf praditadf     20 Mar 10 19:53 contoh2
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
   praditadf@praditadf-VirtualBox:~$ mv contoh1 contoh2 A/D
   praditadf@praditadf-VirtualBox:~$ ls -l A/D
   total 16
   drwxrwxr-x 2 praditadf praditadf 4096 Mar 10 19:17 A
   -rw-rw-r-- 1 praditadf praditadf   20 Mar 10 19:53 contoh
   -rw-rw-r-- 1 praditadf praditadf   20 Mar 10 19:53 contoh1
   -rw-rw-r-- 1 praditadf praditadf   20 Mar 10 19:53 contoh2
   praditadf@praditadf-VirtualBox:~$ mv contoh contoh1 C
   mv: cannot stat 'contoh': No such file or directory
   mv: cannot stat 'contoh1': No such file or directory
   praditadf@praditadf-VirtualBox:~$ ls -l C
   total 0
   ```

3. Perintah rm untuk menghapus file

   *$ rm contoh2*

   *$ ls -l*

   *$ rm –i contoh*

   *$ rm –rf A C*

   *$ ls -l*

   ```praditadf@praditadf-VirtualBox:~$ rm contoh2
   rm: cannot remove 'contoh2': No such file or directory
   praditadf@praditadf-VirtualBox:~$ ls -l
   total 224
   drwxrwxr-x 4 praditadf praditadf   4096 Mar 10 19:53 A
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
   praditadf@praditadf-VirtualBox:~$ rm -i contoh
   rm: cannot remove 'contoh': No such file or directory
   praditadf@praditadf-VirtualBox:~$ rm -rf A C
   praditadf@praditadf-VirtualBox:~$ ls -l
   total 216
   -rw-r--r-- 1 praditadf praditadf   1761 Feb 24 18:16 aaaaaaa
   -rw-rw-r-- 1 praditadf praditadf   3229 Mar  4 10:46 backup-error.log
   -rwxrwxr-x 1 praditadf praditadf    151 Mar  4 10:45 backup.sh
   -rw-rw-r-- 1 praditadf praditadf    951 Mar  4 10:46 backup-succes.log
   -rw-rw-r-- 1 praditadf praditadf      0 Mar  3 18:51 backup-success.log
   -rw-rw-r-- 1 praditadf praditadf     45 Mar  4 10:46 backup.tar.gz
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
   ```

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

   ```praditadf@praditadf-VirtualBox:~$ echo "Hallo apa khabar" > halo.txt
   praditadf@praditadf-VirtualBox:~$ ls -l
   total 220
   -rw-r--r-- 1 praditadf praditadf   1761 Feb 24 18:16 aaaaaaa
   -rw-rw-r-- 1 praditadf praditadf   3229 Mar  4 10:46 backup-error.log
   -rwxrwxr-x 1 praditadf praditadf    151 Mar  4 10:45 backup.sh
   -rw-rw-r-- 1 praditadf praditadf    951 Mar  4 10:46 backup-succes.log
   -rw-rw-r-- 1 praditadf praditadf      0 Mar  3 18:51 backup-success.log
   -rw-rw-r-- 1 praditadf praditadf     45 Mar  4 10:46 backup.tar.gz
   -rw-rw-r-- 1 praditadf praditadf     44 Feb 24 18:20 config.txt
   drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Desktop
   drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Documents
   drwxr-xr-x 2 praditadf praditadf   4096 Mar  4 13:14 Downloads
   -rw-rw-r-- 1 praditadf praditadf      0 Mar  3 17:16 error.log
   drwxrwxr-x 3 praditadf praditadf   4096 Mar  4 11:55 Github
   -rw-rw-r-- 1 praditadf praditadf     17 Mar 10 20:02 halo.txt
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
   praditadf@praditadf-VirtualBox:~$ ln halo.txt z
   praditadf@praditadf-VirtualBox:~$ ls -l
   total 224
   -rw-r--r-- 1 praditadf praditadf   1761 Feb 24 18:16 aaaaaaa
   -rw-rw-r-- 1 praditadf praditadf   3229 Mar  4 10:46 backup-error.log
   -rwxrwxr-x 1 praditadf praditadf    151 Mar  4 10:45 backup.sh
   -rw-rw-r-- 1 praditadf praditadf    951 Mar  4 10:46 backup-succes.log
   -rw-rw-r-- 1 praditadf praditadf      0 Mar  3 18:51 backup-success.log
   -rw-rw-r-- 1 praditadf praditadf     45 Mar  4 10:46 backup.tar.gz
   -rw-rw-r-- 1 praditadf praditadf     44 Feb 24 18:20 config.txt
   drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Desktop
   drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Documents
   drwxr-xr-x 2 praditadf praditadf   4096 Mar  4 13:14 Downloads
   -rw-rw-r-- 1 praditadf praditadf      0 Mar  3 17:16 error.log
   drwxrwxr-x 3 praditadf praditadf   4096 Mar  4 11:55 Github
   -rw-rw-r-- 2 praditadf praditadf     17 Mar 10 20:02 halo.txt
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
   -rw-rw-r-- 2 praditadf praditadf     17 Mar 10 20:02 z
   praditadf@praditadf-VirtualBox:~$ cat z
   Hallo apa khabar
   praditadf@praditadf-VirtualBox:~$ mkdir mydir
   praditadf@praditadf-VirtualBox:~$ ln z mydir/halo.juga
   praditadf@praditadf-VirtualBox:~$ cat mydir/halo.juga
   Hallo apa khabar
   praditadf@praditadf-VirtualBox:~$ ln -s z bye.txt
   praditadf@praditadf-VirtualBox:~$ ls -l bye.txt
   lrwxrwxrwx 1 praditadf praditadf 1 Mar 10 20:03 bye.txt -> z
   praditadf@praditadf-VirtualBox:~$ cat bye.txt
   Hallo apa khabar
   ```

### Percobaan 4 : Melihat Isi File

1. *$ ls –l*

   *$ file halo.txt*

   *$ file bye.txt*

   ```praditadf@praditadf-VirtualBox:~$ ls -l
   total 228
   -rw-r--r-- 1 praditadf praditadf   1761 Feb 24 18:16 aaaaaaa
   -rw-rw-r-- 1 praditadf praditadf   3229 Mar  4 10:46 backup-error.log
   -rwxrwxr-x 1 praditadf praditadf    151 Mar  4 10:45 backup.sh
   -rw-rw-r-- 1 praditadf praditadf    951 Mar  4 10:46 backup-succes.log
   -rw-rw-r-- 1 praditadf praditadf      0 Mar  3 18:51 backup-success.log
   -rw-rw-r-- 1 praditadf praditadf     45 Mar  4 10:46 backup.tar.gz
   lrwxrwxrwx 1 praditadf praditadf      1 Mar 10 20:03 bye.txt -> z
   -rw-rw-r-- 1 praditadf praditadf     44 Feb 24 18:20 config.txt
   drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Desktop
   drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Documents
   drwxr-xr-x 2 praditadf praditadf   4096 Mar  4 13:14 Downloads
   -rw-rw-r-- 1 praditadf praditadf      0 Mar  3 17:16 error.log
   drwxrwxr-x 3 praditadf praditadf   4096 Mar  4 11:55 Github
   -rw-rw-r-- 3 praditadf praditadf     17 Mar 10 20:02 halo.txt
   -rw-rw-r-- 1 praditadf praditadf    799 Mar  3 17:16 large-logs.txt
   -rw-rw-r-- 1 praditadf praditadf   3432 Mar  3 18:13 log.txt
   -rw-rw-r-- 1 praditadf praditadf    139 Mar  4 10:11 monitor.sh
   drwxr-xr-x 2 praditadf praditadf   4096 Feb 14 18:36 Music
   drwxrwxr-x 2 praditadf praditadf   4096 Mar 10 20:02 mydir
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
   -rw-rw-r-- 3 praditadf praditadf     17 Mar 10 20:02 z
   praditadf@praditadf-VirtualBox:~$ file halo.txt
   halo.txt: ASCII text
   praditadf@praditadf-VirtualBox:~$ file bye.txt
   bye.txt: symbolic link to z
   ```

### Percobaan 5 : Mencari file

1. Perintah find

   *$ find /home –name “_.txt” –print > myerror.txt*

   *$ cat myerror.txt*

   *$ find . –name “_.txt” –exec wc –l ‘{}’ ‘;’*

   ```praditadf@praditadf-VirtualBox:~$ find /home -name "*.txt" -print > myerror.txt
   praditadf@praditadf-VirtualBox:~$ cat myerror.txt
   /home/praditadf/large-logs.txt
   /home/praditadf/sorted-users.txt
   /home/praditadf/path.txt
   /home/praditadf/config.txt
   /home/praditadf/snap/firefox/common/.mozilla/firefox/pgii4k5j.default/serviceworker.txt
   /home/praditadf/snap/firefox/common/.mozilla/firefox/pgii4k5j.default/cert_override.txt
   /home/praditadf/snap/firefox/common/.mozilla/firefox/pgii4k5j.default/Telemetry.FailedProfileLocks.txt
   /home/praditadf/snap/firefox/common/.mozilla/firefox/pgii4k5j.default/pkcs11.txt
   /home/praditadf/snap/firefox/common/.mozilla/firefox/pgii4k5j.default/datareporting/glean/client_id.txt
   /home/praditadf/bye.txt
   /home/praditadf/.cache/tracker3/files/last-crawl.txt
   /home/praditadf/.cache/tracker3/files/first-index.txt
   /home/praditadf/.config/Code/WebStorage/2/CacheStorage/index.txt
   /home/praditadf/praktikum-os/week2/config.txt
   /home/praditadf/praktikum-os/week2/notes.txt
   /home/praditadf/halo.txt
   /home/praditadf/ping-log.txt
   /home/praditadf/log.txt
   /home/praditadf/myerror.txt
   /home/praditadf/.vscode/extensions/davidanson.vscode-markdownlint-0.61.1/LICENSE.txt
   /home/praditadf/.vscode/extensions/github.copilot-chat-0.37.9/LICENSE.txt
   /home/praditadf/.vscode/extensions/github.copilot-chat-0.37.9/ThirdPartyNotices.txt
   /home/praditadf/.vscode/extensions/yzhang.markdown-all-in-one-3.6.3/LICENSE.txt
   /home/praditadf/.vscode/extensions/esbenp.prettier-vscode-12.3.0/LICENSE.txt
   /home/praditadf/.pki/nssdb/pkcs11.txt
   praditadf@praditadf-VirtualBox:~$ find . -name "*.txt" -exec wc -l '{}' ';'
   10 ./large-logs.txt
   49 ./sorted-users.txt
   2078 ./path.txt
   4 ./config.txt
   35 ./snap/firefox/common/.mozilla/firefox/pgii4k5j.default/serviceworker.txt
   5 ./snap/firefox/common/.mozilla/firefox/pgii4k5j.default/cert_override.txt
   0 ./snap/firefox/common/.mozilla/firefox/pgii4k5j.default/Telemetry.FailedProfileLocks.txt
   5 ./snap/firefox/common/.mozilla/firefox/pgii4k5j.default/pkcs11.txt
   0 ./snap/firefox/common/.mozilla/firefox/pgii4k5j.default/datareporting/glean/client_id.txt
   1 ./bye.txt
   0 ./.cache/tracker3/files/last-crawl.txt
   0 ./.cache/tracker3/files/first-index.txt
   2 ./.config/Code/WebStorage/2/CacheStorage/index.txt
   3 ./praktikum-os/week2/config.txt
   0 ./praktikum-os/week2/notes.txt
   1 ./halo.txt
   116 ./ping-log.txt
   60 ./log.txt
   25 ./myerror.txt
   21 ./.vscode/extensions/davidanson.vscode-markdownlint-0.61.1/LICENSE.txt
   46 ./.vscode/extensions/github.copilot-chat-0.37.9/LICENSE.txt
   45154 ./.vscode/extensions/github.copilot-chat-0.37.9/ThirdPartyNotices.txt
   21 ./.vscode/extensions/yzhang.markdown-all-in-one-3.6.3/LICENSE.txt
   21 ./.vscode/extensions/esbenp.prettier-vscode-12.3.0/LICENSE.txt
   5 ./.pki/nssdb/pkcs11.txt
   ```

2. Perintah which

   *$ which ls*

   ```praditadf@praditadf-VirtualBox:~$ which ls
   /usr/bin/ls
   ```

3. Perintah locate

   *$ locate “\*.txt”*

   ```praditadf@praditadf-VirtualBox:~$ locate "*.txt"
   /boot/grub/gfxblacklist.txt
   /etc/X11/rgb.txt
   /etc/brltty/Input/ba/all.txt
   /etc/brltty/Input/bd/all.txt
   /etc/brltty/Input/bl/18.txt
   /etc/brltty/Input/bl/40_m20_m40.txt
   /etc/brltty/Input/ec/all.txt
   /etc/brltty/Input/ec/spanish.txt
   /etc/brltty/Input/eu/all.txt
   /etc/brltty/Input/lb/all.txt
   /etc/brltty/Input/lt/all.txt
   /etc/brltty/Input/mb/all.txt
   /etc/brltty/Input/mn/all.txt
   /etc/brltty/Input/no/all.txt
   /etc/brltty/Input/tn/all.txt
   /etc/brltty/Input/tt/all.txt
   /etc/brltty/Input/vd/all.txt
   /etc/brltty/Input/vr/all.txt
   /etc/brltty/Input/vs/all.txt
   /home/praditadf/config.txt
   /home/praditadf/large-logs.txt
   /home/praditadf/log.txt
   /home/praditadf/path.txt
   /home/praditadf/ping-log.txt
   /home/praditadf/sorted-users.txt
   /home/praditadf/.cache/tracker3/files/first-index.txt
   /home/praditadf/.cache/tracker3/files/last-crawl.txt
   /home/praditadf/.config/Code/WebStorage/2/CacheStorage/index.txt
   /home/praditadf/.pki/nssdb/pkcs11.txt
   /home/praditadf/.vscode/extensions/davidanson.vscode-markdownlint-0.61.1/LICENSE.txt
   /home/praditadf/.vscode/extensions/esbenp.prettier-vscode-12.3.0/LICENSE.txt
   /home/praditadf/.vscode/extensions/github.copilot-chat-0.37.9/LICENSE.txt
   /home/praditadf/.vscode/extensions/github.copilot-chat-0.37.9/ThirdPartyNotices.txt
   /home/praditadf/.vscode/extensions/yzhang.markdown-all-in-one-3.6.3/LICENSE.txt
   /home/praditadf/praktikum-os/week2/config.txt
   /home/praditadf/praktikum-os/week2/notes.txt
   /home/praditadf/snap/firefox/common/.mozilla/firefox/pgii4k5j.default/Telemetry.FailedProfileLocks.txt
   /home/praditadf/snap/firefox/common/.mozilla/firefox/pgii4k5j.default/cert_override.txt
   /home/praditadf/snap/firefox/common/.mozilla/firefox/pgii4k5j.default/pkcs11.txt
   /home/praditadf/snap/firefox/common/.mozilla/firefox/pgii4k5j.default/serviceworker.txt
   /home/praditadf/snap/firefox/common/.mozilla/firefox/pgii4k5j.default/datareporting/glean/client_id.txt
   /snap/code/226/etc/X11/rgb.txt
   /snap/code/226/usr/share/X11/rgb.txt
   /snap/code/226/usr/share/code/resources/app/ThirdPartyNotices.txt
   /snap/code/226/usr/share/code/resources/app/extensions/git/dist/main.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/extensions/github/dist/extension.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/extensions/github-authentication/dist/extension.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/extensions/html-language-features/client/dist/node/htmlClientMain.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/extensions/json-language-features/client/dist/node/jsonClientMain.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/extensions/latex/cpp-bailout-license.txt
   /snap/code/226/usr/share/code/resources/app/extensions/latex/markdown-latex-combined-license.txt
   /snap/code/226/usr/share/code/resources/app/extensions/markdown-language-features/dist/extension.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/extensions/markdown-language-features/dist/serverWorkerMain.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/extensions/merge-conflict/dist/mergeConflictMain.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/extensions/microsoft-authentication/dist/extension.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/extensions/ms-vscode.js-debug/LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/extensions/ms-vscode.js-debug/ThirdPartyNotices.txt
   /snap/code/226/usr/share/code/resources/app/extensions/ms-vscode.js-debug-companion/LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/extensions/ms-vscode.js-debug-companion/ThirdPartyNotices.txt
   /snap/code/226/usr/share/code/resources/app/extensions/ms-vscode.vscode-js-profile-table/ThirdPartyNotices.txt
   /snap/code/226/usr/share/code/resources/app/extensions/npm/dist/npmMain.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/extensions/terminal-suggest/ThirdPartyNotices.txt
   /snap/code/226/usr/share/code/resources/app/extensions/theme-seti/ThirdPartyNotices.txt
   /snap/code/226/usr/share/code/resources/app/extensions/typescript-language-features/dist/extension.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/@vscode/deviceid/LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/@vscode/deviceid/NOTICE.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/@vscode/deviceid/owners.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/@vscode/iconv-lite-umd/lib/iconv-lite-umd.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/@vscode/vscode-languagedetection/dist/lib/index.js.LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/native-keymap/License.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/native-keymap/ThirdPartyNotices.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/tas-client/LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/tslib/CopyrightNotice.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/tslib/LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/v8-inspect-profiler/LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/vscode-oniguruma/LICENSE.txt
   /snap/code/226/usr/share/code/resources/app/node_modules/vscode-oniguruma/NOTICES.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/Jinja2-2.10.1.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/Jinja2-2.10.1.egg-info/entry_points.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/Jinja2-2.10.1.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/Jinja2-2.10.1.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/MarkupSafe-1.1.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/MarkupSafe-1.1.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/PyJWT-1.7.1.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/PyJWT-1.7.1.egg-info/entry_points.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/PyJWT-1.7.1.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/PyJWT-1.7.1.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/attrs-19.3.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/attrs-19.3.0.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/attrs-19.3.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/certifi-2019.11.28.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/certifi-2019.11.28.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/chardet-3.0.4.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/chardet-3.0.4.egg-info/entry_points.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/chardet-3.0.4.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/cloud_init-24.4.1.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/cloud_init-24.4.1.egg-info/entry_points.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/cloud_init-24.4.1.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/cloud_init-24.4.1.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/cryptography-2.8.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/cryptography-2.8.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/cryptography-2.8.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/idna-2.8.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/idna-2.8.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/importlib_metadata-1.5.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/importlib_metadata-1.5.0.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/importlib_metadata-1.5.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/jsonpatch-1.22.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/jsonpatch-1.22.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/jsonpatch-1.22.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/entry_points.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/more_itertools-4.2.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/more_itertools-4.2.0.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/more_itertools-4.2.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/netifaces-0.10.4.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/netifaces-0.10.4.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/oauthlib-3.1.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/oauthlib-3.1.0.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/oauthlib-3.1.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/pyrsistent-0.15.5.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/pyrsistent-0.15.5.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/pyrsistent-0.15.5.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/pyserial-3.4.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/pyserial-3.4.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/pyudev-0.21.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/pyudev-0.21.0.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/pyudev-0.21.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/requests-2.22.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/requests-2.22.0.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/requests-2.22.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/setuptools-45.2.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/setuptools-45.2.0.egg-info/entry_points.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/setuptools-45.2.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/six-1.14.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/six-1.14.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/urllib3-1.25.8.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/urllib3-1.25.8.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/urllib3-1.25.8.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/urwid-2.0.1.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/urwid-2.0.1.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/dependency_links.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/requires.txt
   /snap/core20/2717/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/top_level.txt
   /snap/core20/2717/usr/lib/python3.8/LICENSE.txt
   /snap/core20/2717/usr/lib/python3.8/lib2to3/Grammar.txt
   /snap/core20/2717/usr/lib/python3.8/lib2to3/PatternGrammar.txt
   /snap/core20/2717/usr/lib/python3.9/lib2to3/Grammar.txt
   /snap/core20/2717/usr/lib/python3.9/lib2to3/PatternGrammar.txt
   /snap/core20/2717/usr/share/doc/mount/mount.txt
   /snap/core20/2717/usr/share/subiquity/subiquity-0.0.5.egg-info/dependency_links.txt
   /snap/core20/2717/usr/share/subiquity/subiquity-0.0.5.egg-info/entry_points.txt
   /snap/core20/2717/usr/share/subiquity/subiquity-0.0.5.egg-info/top_level.txt
   /snap/core20/2717/usr/share/vim/vim81/doc/help.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/entry_points.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/entry_points.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/PyJWT-2.3.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/PyJWT-2.3.0.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/PyJWT-2.3.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/PyYAML-5.4.1.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/PyYAML-5.4.1.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/attrs-21.2.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/attrs-21.2.0.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/attrs-21.2.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/certifi-2020.6.20.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/certifi-2020.6.20.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/chardet-4.0.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/chardet-4.0.0.egg-info/entry_points.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/chardet-4.0.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/entry_points.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/cryptography-3.4.8.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/cryptography-3.4.8.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/cryptography-3.4.8.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/idna-3.3.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/idna-3.3.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/entry_points.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/oauthlib-3.2.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/oauthlib-3.2.0.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/oauthlib-3.2.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/pyrsistent-0.18.1.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/pyrsistent-0.18.1.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/entry_points.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/pytz-2022.1.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/pytz-2022.1.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/pyudev-0.22.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/pyudev-0.22.0.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/pyudev-0.22.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/requests-2.25.1.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/requests-2.25.1.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/requests-2.25.1.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/entry_points.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/six-1.16.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/six-1.16.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/urllib3-1.26.5.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/urllib3-1.26.5.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/urllib3-1.26.5.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/urwid-2.1.2.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/urwid-2.1.2.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/dependency_links.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/requires.txt
   /snap/core22/2292/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/top_level.txt
   /snap/core22/2292/usr/lib/python3.10/LICENSE.txt
   /snap/core22/2292/usr/lib/python3.10/lib2to3/Grammar.txt
   /snap/core22/2292/usr/lib/python3.10/lib2to3/PatternGrammar.txt
   /snap/core22/2292/usr/lib/python3.11/lib2to3/Grammar.txt
   /snap/core22/2292/usr/lib/python3.11/lib2to3/PatternGrammar.txt
   /snap/core22/2292/usr/share/subiquity/subiquity-0.0.5.egg-info/dependency_links.txt
   /snap/core22/2292/usr/share/subiquity/subiquity-0.0.5.egg-info/entry_points.txt
   /snap/core22/2292/usr/share/subiquity/subiquity-0.0.5.egg-info/top_level.txt
   /snap/core22/2292/usr/share/vim/vim82/doc/help.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/entry_points.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/entry_points.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/PyJWT-2.3.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/PyJWT-2.3.0.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/PyJWT-2.3.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/PyYAML-5.4.1.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/PyYAML-5.4.1.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/attrs-21.2.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/attrs-21.2.0.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/attrs-21.2.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/certifi-2020.6.20.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/certifi-2020.6.20.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/chardet-4.0.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/chardet-4.0.0.egg-info/entry_points.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/chardet-4.0.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/entry_points.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/cryptography-3.4.8.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/cryptography-3.4.8.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/cryptography-3.4.8.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/idna-3.3.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/idna-3.3.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/entry_points.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/oauthlib-3.2.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/oauthlib-3.2.0.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/oauthlib-3.2.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/pyrsistent-0.18.1.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/pyrsistent-0.18.1.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/entry_points.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/pytz-2022.1.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/pytz-2022.1.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/pyudev-0.22.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/pyudev-0.22.0.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/pyudev-0.22.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/requests-2.25.1.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/requests-2.25.1.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/requests-2.25.1.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/entry_points.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/six-1.16.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/six-1.16.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/urllib3-1.26.5.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/urllib3-1.26.5.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/urllib3-1.26.5.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/urwid-2.1.2.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/urwid-2.1.2.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/dependency_links.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/requires.txt
   /snap/core22/2339/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/top_level.txt
   /snap/core22/2339/usr/lib/python3.10/LICENSE.txt
   /snap/core22/2339/usr/lib/python3.10/lib2to3/Grammar.txt
   /snap/core22/2339/usr/lib/python3.10/lib2to3/PatternGrammar.txt
   /snap/core22/2339/usr/lib/python3.11/lib2to3/Grammar.txt
   /snap/core22/2339/usr/lib/python3.11/lib2to3/PatternGrammar.txt
   /snap/core22/2339/usr/share/subiquity/subiquity-0.0.5.egg-info/dependency_links.txt
   /snap/core22/2339/usr/share/subiquity/subiquity-0.0.5.egg-info/entry_points.txt
   /snap/core22/2339/usr/share/subiquity/subiquity-0.0.5.egg-info/top_level.txt
   /snap/core22/2339/usr/share/vim/vim82/doc/help.txt
   /snap/gnome-42-2204/247/etc/X11/rgb.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/Mako-1.1.3-py3.10.egg-info/dependency_links.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/Mako-1.1.3-py3.10.egg-info/entry_points.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/Mako-1.1.3-py3.10.egg-info/requires.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/Mako-1.1.3-py3.10.egg-info/top_level.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/Markdown-3.3.6.egg-info/dependency_links.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/Markdown-3.3.6.egg-info/entry_points.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/Markdown-3.3.6.egg-info/requires.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/Markdown-3.3.6.egg-info/top_level.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/dependency_links.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/top_level.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/PyGObject-3.42.1.egg-info/dependency_links.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/PyGObject-3.42.1.egg-info/requires.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/PyGObject-3.42.1.egg-info/top_level.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/dependency_links.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/top_level.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/dependency_links.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/requires.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/top_level.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/dependency_links.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/top_level.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/pip/_vendor/vendor.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/pip-22.0.2.dist-info/entry_points.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/pip-22.0.2.dist-info/top_level.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/dependency_links.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/entry_points.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/top_level.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/wheel-0.37.1.egg-info/dependency_links.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/wheel-0.37.1.egg-info/entry_points.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/wheel-0.37.1.egg-info/requires.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/wheel-0.37.1.egg-info/top_level.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/dependency_links.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/requires.txt
   /snap/gnome-42-2204/247/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/top_level.txt
   /snap/gnome-42-2204/247/usr/lib/python3.10/LICENSE.txt
   /snap/gnome-42-2204/247/usr/share/X11/rgb.txt
   /snap/gnome-42-2204/247/usr/share/presage/abbreviations_en.txt
   /snap/gnome-42-2204/247/usr/share/presage/abbreviations_it.txt
   /usr/lib/python3/dist-packages/Babel-2.10.3.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/Babel-2.10.3.egg-info/entry_points.txt
   /usr/lib/python3/dist-packages/Babel-2.10.3.egg-info/requires.txt
   /usr/lib/python3/dist-packages/Babel-2.10.3.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/Brlapi-0.8.5.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/Brlapi-0.8.5.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/entry_points.txt
   /usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/requires.txt
   /usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/MarkupSafe-2.1.5.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/MarkupSafe-2.1.5.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/PyJWT-2.7.0.dist-info/top_level.txt
   /usr/lib/python3/dist-packages/PyYAML-6.0.1.dist-info/top_level.txt
   /usr/lib/python3/dist-packages/bcc-0.29.1.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/bcc-0.29.1.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/certifi-2023.11.17.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/certifi-2023.11.17.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/chardet-5.2.0.dist-info/entry_points.txt
   /usr/lib/python3/dist-packages/chardet-5.2.0.dist-info/top_level.txt
   /usr/lib/python3/dist-packages/click-8.1.6.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/click-8.1.6.egg-info/requires.txt
   /usr/lib/python3/dist-packages/click-8.1.6.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/entry_points.txt
   /usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/requires.txt
   /usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/configobj-5.0.8.dist-info/top_level.txt
   /usr/lib/python3/dist-packages/cryptography-41.0.7.dist-info/top_level.txt
   /usr/lib/python3/dist-packages/cryptography.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/cryptography.egg-info/requires.txt
   /usr/lib/python3/dist-packages/cryptography.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/cupshelpers-1.0.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/cupshelpers-1.0.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/dbus_python-1.3.2.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/dbus_python-1.3.2.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/defer-1.0.6.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/defer-1.0.6.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/distro-1.9.0.dist-info/entry_points.txt
   /usr/lib/python3/dist-packages/distro-1.9.0.dist-info/top_level.txt
   /usr/lib/python3/dist-packages/distro_info-1.7+build1.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/distro_info-1.7+build1.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/httplib2-0.20.4.dist-info/top_level.txt
   /usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/requires.txt
   /usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/jsonschema-4.10.3.dist-info/entry_points.txt
   /usr/lib/python3/dist-packages/language_selector-0.1.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/language_selector-0.1.egg-info/entry_points.txt
   /usr/lib/python3/dist-packages/language_selector-0.1.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/launchpadlib-1.11.0.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/launchpadlib-1.11.0.egg-info/requires.txt
   /usr/lib/python3/dist-packages/launchpadlib-1.11.0.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/lazr.restfulclient-0.14.6.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/lazr.restfulclient-0.14.6.egg-info/namespace_packages.txt
   /usr/lib/python3/dist-packages/lazr.restfulclient-0.14.6.egg-info/requires.txt
   /usr/lib/python3/dist-packages/lazr.restfulclient-0.14.6.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/lazr.uri-1.0.6.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/lazr.uri-1.0.6.egg-info/namespace_packages.txt
   /usr/lib/python3/dist-packages/lazr.uri-1.0.6.egg-info/requires.txt
   /usr/lib/python3/dist-packages/lazr.uri-1.0.6.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/louis-3.29.0.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/louis-3.29.0.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/markdown_it_py-3.0.0.dist-info/entry_points.txt
   /usr/lib/python3/dist-packages/netaddr/eui/iab.txt
   /usr/lib/python3/dist-packages/netaddr/eui/oui.txt
   /usr/lib/python3/dist-packages/netaddr-0.8.0.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/netaddr-0.8.0.egg-info/entry_points.txt
   /usr/lib/python3/dist-packages/netaddr-0.8.0.egg-info/requires.txt
   /usr/lib/python3/dist-packages/netaddr-0.8.0.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/oauthlib-3.2.2.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/oauthlib-3.2.2.egg-info/requires.txt
   /usr/lib/python3/dist-packages/oauthlib-3.2.2.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/olefile-0.46.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/olefile-0.46.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/pexpect-4.9.0.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/pexpect-4.9.0.egg-info/requires.txt
   /usr/lib/python3/dist-packages/pexpect-4.9.0.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/pillow-10.2.0.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/pillow-10.2.0.egg-info/requires.txt
   /usr/lib/python3/dist-packages/pillow-10.2.0.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/pycups-2.0.1.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/pycups-2.0.1.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/pygments-2.17.2.dist-info/entry_points.txt
   /usr/lib/python3/dist-packages/pyrsistent-0.20.0.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/pyrsistent-0.20.0.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/pyserial-3.5.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/pyserial-3.5.egg-info/entry_points.txt
   /usr/lib/python3/dist-packages/pyserial-3.5.egg-info/requires.txt
   /usr/lib/python3/dist-packages/pyserial-3.5.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/python_apt-2.7.7+ubuntu5.2.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/python_apt-2.7.7+ubuntu5.2.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/python_dateutil-2.8.2.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/python_dateutil-2.8.2.egg-info/requires.txt
   /usr/lib/python3/dist-packages/python_dateutil-2.8.2.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/python_debian-0.1.49+ubuntu2.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/python_debian-0.1.49+ubuntu2.egg-info/requires.txt
   /usr/lib/python3/dist-packages/python_debian-0.1.49+ubuntu2.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/pytz-2024.1.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/pytz-2024.1.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/pyxdg-0.28.dist-info/top_level.txt
   /usr/lib/python3/dist-packages/requests-2.31.0.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/requests-2.31.0.egg-info/requires.txt
   /usr/lib/python3/dist-packages/requests-2.31.0.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/six-1.16.0.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/six-1.16.0.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/systemd_python-235.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/systemd_python-235.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/ubuntu_drivers_common-0.0.0.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/ubuntu_drivers_common-0.0.0.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/ubuntu_pro_client-8001.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/ubuntu_pro_client-8001.egg-info/entry_points.txt
   /usr/lib/python3/dist-packages/ubuntu_pro_client-8001.egg-info/requires.txt
   /usr/lib/python3/dist-packages/ubuntu_pro_client-8001.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/ufw-0.36.2.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/ufw-0.36.2.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/unattended_upgrades-0.1.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/unattended_upgrades-0.1.egg-info/top_level.txt
   /usr/lib/python3/dist-packages/wadllib-1.3.6.egg-info/dependency_links.txt
   /usr/lib/python3/dist-packages/wadllib-1.3.6.egg-info/requires.txt
   /usr/lib/python3/dist-packages/wadllib-1.3.6.egg-info/top_level.txt
   /usr/lib/python3.12/LICENSE.txt
   /usr/lib/xorg/protocol.txt
   /usr/share/X11/rgb.txt
   /usr/share/cups/doc-root/robots.txt
   /usr/share/doc/alsa-base/driver/Bt87x.txt
   /usr/share/doc/alsa-base/driver/ControlNames.txt
   /usr/share/doc/alsa-base/driver/Joystick.txt
   /usr/share/doc/alsa-base/driver/MIXART.txt
   /usr/share/doc/alsa-base/driver/VIA82xx-mixer.txt
   /usr/share/doc/alsa-base/driver/alsa-parameters.txt
   /usr/share/doc/alsa-base/driver/emu10k1-jack.txt
   /usr/share/doc/alsa-base/driver/powersave.txt
   /usr/share/doc/alsa-base/driver/serial-u16550.txt
   /usr/share/doc/bpfcc-tools/examples/doc/argdist_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/bashreadline_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/bindsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/biolatency_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/biolatpcts_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/biopattern_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/biosnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/biotop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/bitesize_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/bpflist_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/btrfsdist_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/btrfsslower_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/cachestat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/cachetop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/capable_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/cobjnew_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/compactsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/cpudist_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/cpuunclaimed_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/criticalstat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/cthreads_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/dbslower_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/dbstat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/dcsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/dcstat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/deadlock_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/dirtop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/drsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/execsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/exitsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/ext4dist_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/ext4slower_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/filegone_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/filelife_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/fileslower_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/filetop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/funccount_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/funcinterval_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/funclatency_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/funcslower_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/gethostlatency_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/hardirqs_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/inject_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/javacalls_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/javaflow_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/javagc_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/javaobjnew_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/javastat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/javathreads_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/killsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/klockstat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/kvmexit_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/llcstat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/mdflush_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/memleak_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/mountsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/mysqld_qslower_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/netqtop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/nfsdist_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/nfsslower_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/nodegc_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/nodestat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/offcputime_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/offwaketime_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/oomkill_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/opensnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/perlcalls_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/perlflow_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/perlstat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/phpcalls_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/phpflow_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/phpstat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/pidpersec_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/ppchcalls_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/profile_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/pythoncalls_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/pythonflow_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/pythongc_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/pythonstat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/rdmaucma_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/readahead_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/reset-trace_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/rubycalls_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/rubyflow_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/rubygc_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/rubyobjnew_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/rubystat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/runqlat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/runqlen_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/runqslower_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/shmsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/slabratetop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/sofdsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/softirqs_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/solisten_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/sslsniff_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/stackcount_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/statsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/swapin.txt
   /usr/share/doc/bpfcc-tools/examples/doc/swapin_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/syncsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/syscount_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tclcalls_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tclflow_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tclobjnew_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tclstat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcpaccept_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcpcong_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcpconnect_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcpconnlat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcpdrop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcplife_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcpretrans_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcprtt_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcpstates_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcpsubnet_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcpsynbl_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcptop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tcptracer_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/threadsnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/tplist_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/trace_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/ttysnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/vfscount_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/vfsstat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/virtiostat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/wakeuptime_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/xfsdist_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/xfsslower_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/zfsdist_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/zfsslower_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/lib/ucalls_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/lib/uflow_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/lib/ugc_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/lib/uobjnew_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/lib/ustat_example.txt
   /usr/share/doc/bpfcc-tools/examples/doc/lib/uthreads_example.txt
   /usr/share/doc/bpfcc-tools/examples/networking/neighbor_sharing/README.txt
   /usr/share/doc/bpfcc-tools/examples/networking/vlan_learning/README.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/CMakeLists.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/biolatpcts_example.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/bitehist_example.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/dddos_example.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/disksnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/kvm_hypercall.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/mysqld_query_example.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/nodejs_http_server_example.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/stacksnoop_example.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/tcpv4connect_example.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/undump_example.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/urandomread_example.txt
   /usr/share/doc/bpfcc-tools/examples/tracing/vfsreadlat_example.txt
   /usr/share/doc/bpftrace/examples/bashreadline_example.txt
   /usr/share/doc/bpftrace/examples/biolatency_example.txt
   /usr/share/doc/bpftrace/examples/biosnoop_example.txt
   /usr/share/doc/bpftrace/examples/biostacks_example.txt
   /usr/share/doc/bpftrace/examples/bitesize_example.txt
   /usr/share/doc/bpftrace/examples/capable_example.txt
   /usr/share/doc/bpftrace/examples/cpuwalk_example.txt
   /usr/share/doc/bpftrace/examples/dcsnoop_example.txt
   /usr/share/doc/bpftrace/examples/execsnoop_example.txt
   /usr/share/doc/bpftrace/examples/gethostlatency_example.txt
   /usr/share/doc/bpftrace/examples/killsnoop_example.txt
   /usr/share/doc/bpftrace/examples/loads_example.txt
   /usr/share/doc/bpftrace/examples/mdflush_example.txt
   /usr/share/doc/bpftrace/examples/naptime_example.txt
   /usr/share/doc/bpftrace/examples/oomkill_example.txt
   /usr/share/doc/bpftrace/examples/opensnoop_example.txt
   /usr/share/doc/bpftrace/examples/pidpersec_example.txt
   /usr/share/doc/bpftrace/examples/runqlat_example.txt
   /usr/share/doc/bpftrace/examples/runqlen_example.txt
   /usr/share/doc/bpftrace/examples/setuids_example.txt
   /usr/share/doc/bpftrace/examples/ssllatency_example.txt
   /usr/share/doc/bpftrace/examples/sslsnoop_example.txt
   /usr/share/doc/bpftrace/examples/statsnoop_example.txt
   /usr/share/doc/bpftrace/examples/swapin_example.txt
   /usr/share/doc/bpftrace/examples/syncsnoop_example.txt
   /usr/share/doc/bpftrace/examples/syscount_example.txt
   /usr/share/doc/bpftrace/examples/tcpaccept_example.txt
   /usr/share/doc/bpftrace/examples/tcpconnect_example.txt
   /usr/share/doc/bpftrace/examples/tcpdrop_example.txt
   /usr/share/doc/bpftrace/examples/tcplife_example.txt
   /usr/share/doc/bpftrace/examples/tcpretrans_example.txt
   /usr/share/doc/bpftrace/examples/tcpsynbl_example.txt
   /usr/share/doc/bpftrace/examples/threadsnoop_example.txt
   /usr/share/doc/bpftrace/examples/undump_example.txt
   /usr/share/doc/bpftrace/examples/vfscount_example.txt
   /usr/share/doc/bpftrace/examples/vfsstat_example.txt
   /usr/share/doc/bpftrace/examples/writeback_example.txt
   /usr/share/doc/bpftrace/examples/xfsdist_example.txt
   /usr/share/doc/cloud-init/status.txt
   /usr/share/doc/cloud-init/userdata.txt
   /usr/share/doc/cloud-init/var-lib-cloud.txt
   /usr/share/doc/cloud-init/examples/boothook.txt
   /usr/share/doc/cloud-init/examples/cloud-config-add-apt-repos.txt
   /usr/share/doc/cloud-init/examples/cloud-config-ansible-controller.txt
   /usr/share/doc/cloud-init/examples/cloud-config-ansible-managed.txt
   /usr/share/doc/cloud-init/examples/cloud-config-ansible-pull.txt
   /usr/share/doc/cloud-init/examples/cloud-config-apt.txt
   /usr/share/doc/cloud-init/examples/cloud-config-archive-launch-index.txt
   /usr/share/doc/cloud-init/examples/cloud-config-archive.txt
   /usr/share/doc/cloud-init/examples/cloud-config-boot-cmds.txt
   /usr/share/doc/cloud-init/examples/cloud-config-ca-certs.txt
   /usr/share/doc/cloud-init/examples/cloud-config-chef-oneiric.txt
   /usr/share/doc/cloud-init/examples/cloud-config-chef.txt
   /usr/share/doc/cloud-init/examples/cloud-config-datasources.txt
   /usr/share/doc/cloud-init/examples/cloud-config-disk-setup.txt
   /usr/share/doc/cloud-init/examples/cloud-config-gluster.txt
   /usr/share/doc/cloud-init/examples/cloud-config-install-packages.txt
   /usr/share/doc/cloud-init/examples/cloud-config-launch-index.txt
   /usr/share/doc/cloud-init/examples/cloud-config-lxd.txt
   /usr/share/doc/cloud-init/examples/cloud-config-mount-points.txt
   /usr/share/doc/cloud-init/examples/cloud-config-ntp.txt
   /usr/share/doc/cloud-init/examples/cloud-config-reporting.txt
   /usr/share/doc/cloud-init/examples/cloud-config-run-cmds.txt
   /usr/share/doc/cloud-init/examples/cloud-config-ssh-keys.txt
   /usr/share/doc/cloud-init/examples/cloud-config-update-apt.txt
   /usr/share/doc/cloud-init/examples/cloud-config-update-packages.txt
   /usr/share/doc/cloud-init/examples/cloud-config-user-groups.txt
   /usr/share/doc/cloud-init/examples/cloud-config-wireguard.txt
   /usr/share/doc/cloud-init/examples/cloud-config-write-files.txt
   /usr/share/doc/cloud-init/examples/cloud-config-yum-repo.txt
   /usr/share/doc/cloud-init/examples/cloud-config.txt
   /usr/share/doc/cloud-init/examples/include-once.txt
   /usr/share/doc/cloud-init/examples/include.txt
   /usr/share/doc/cloud-init/examples/kernel-command-line.txt
   /usr/share/doc/cloud-init/examples/part-handler-v2.txt
   /usr/share/doc/cloud-init/examples/part-handler.txt
   /usr/share/doc/cloud-init/examples/plain-ignored.txt
   /usr/share/doc/cloud-init/examples/user-script.txt
   /usr/share/doc/cups/HOWTO_BUGREPORT.txt
   /usr/share/doc/fonts-ubuntu/CONTRIBUTING.txt
   /usr/share/doc/fonts-ubuntu/README.txt
   /usr/share/doc/fonts-ubuntu/TRADEMARKS.txt
   /usr/share/doc/git/RelNotes/1.5.0.1.txt
   /usr/share/doc/git/RelNotes/1.5.0.2.txt
   /usr/share/doc/git/RelNotes/1.5.0.3.txt
   /usr/share/doc/git/RelNotes/1.5.0.4.txt
   /usr/share/doc/git/RelNotes/1.5.0.5.txt
   /usr/share/doc/git/RelNotes/1.5.0.6.txt
   /usr/share/doc/git/RelNotes/1.5.0.7.txt
   /usr/share/doc/git/RelNotes/1.5.0.txt
   /usr/share/doc/git/RelNotes/1.5.1.1.txt
   /usr/share/doc/git/RelNotes/1.5.1.2.txt
   /usr/share/doc/git/RelNotes/1.5.1.3.txt
   /usr/share/doc/git/RelNotes/1.5.1.4.txt
   /usr/share/doc/git/RelNotes/1.5.1.5.txt
   /usr/share/doc/git/RelNotes/1.5.1.6.txt
   /usr/share/doc/git/RelNotes/1.5.1.txt
   /usr/share/doc/git/RelNotes/1.5.2.1.txt
   /usr/share/doc/git/RelNotes/1.5.2.2.txt
   /usr/share/doc/git/RelNotes/1.5.2.3.txt
   /usr/share/doc/git/RelNotes/1.5.2.4.txt
   /usr/share/doc/git/RelNotes/1.5.2.5.txt
   /usr/share/doc/git/RelNotes/1.5.2.txt
   /usr/share/doc/git/RelNotes/1.5.3.1.txt
   /usr/share/doc/git/RelNotes/1.5.3.2.txt
   /usr/share/doc/git/RelNotes/1.5.3.3.txt
   /usr/share/doc/git/RelNotes/1.5.3.4.txt
   /usr/share/doc/git/RelNotes/1.5.3.5.txt
   /usr/share/doc/git/RelNotes/1.5.3.6.txt
   /usr/share/doc/git/RelNotes/1.5.3.7.txt
   /usr/share/doc/git/RelNotes/1.5.3.8.txt
   /usr/share/doc/git/RelNotes/1.5.3.txt
   /usr/share/doc/git/RelNotes/1.5.4.1.txt
   /usr/share/doc/git/RelNotes/1.5.4.2.txt
   /usr/share/doc/git/RelNotes/1.5.4.3.txt
   /usr/share/doc/git/RelNotes/1.5.4.4.txt
   /usr/share/doc/git/RelNotes/1.5.4.5.txt
   /usr/share/doc/git/RelNotes/1.5.4.6.txt
   /usr/share/doc/git/RelNotes/1.5.4.7.txt
   /usr/share/doc/git/RelNotes/1.5.4.txt
   /usr/share/doc/git/RelNotes/1.5.5.1.txt
   /usr/share/doc/git/RelNotes/1.5.5.2.txt
   /usr/share/doc/git/RelNotes/1.5.5.3.txt
   /usr/share/doc/git/RelNotes/1.5.5.4.txt
   /usr/share/doc/git/RelNotes/1.5.5.5.txt
   /usr/share/doc/git/RelNotes/1.5.5.6.txt
   /usr/share/doc/git/RelNotes/1.5.5.txt
   /usr/share/doc/git/RelNotes/1.5.6.1.txt
   /usr/share/doc/git/RelNotes/1.5.6.2.txt
   /usr/share/doc/git/RelNotes/1.5.6.3.txt
   /usr/share/doc/git/RelNotes/1.5.6.4.txt
   /usr/share/doc/git/RelNotes/1.5.6.5.txt
   /usr/share/doc/git/RelNotes/1.5.6.6.txt
   /usr/share/doc/git/RelNotes/1.5.6.txt
   /usr/share/doc/git/RelNotes/1.6.0.1.txt
   /usr/share/doc/git/RelNotes/1.6.0.2.txt
   /usr/share/doc/git/RelNotes/1.6.0.3.txt
   /usr/share/doc/git/RelNotes/1.6.0.4.txt
   /usr/share/doc/git/RelNotes/1.6.0.5.txt
   /usr/share/doc/git/RelNotes/1.6.0.6.txt
   /usr/share/doc/git/RelNotes/1.6.0.txt
   /usr/share/doc/git/RelNotes/1.6.1.1.txt
   /usr/share/doc/git/RelNotes/1.6.1.2.txt
   /usr/share/doc/git/RelNotes/1.6.1.3.txt
   /usr/share/doc/git/RelNotes/1.6.1.4.txt
   /usr/share/doc/git/RelNotes/1.6.1.txt
   /usr/share/doc/git/RelNotes/1.6.2.1.txt
   /usr/share/doc/git/RelNotes/1.6.2.2.txt
   /usr/share/doc/git/RelNotes/1.6.2.3.txt
   /usr/share/doc/git/RelNotes/1.6.2.4.txt
   /usr/share/doc/git/RelNotes/1.6.2.5.txt
   /usr/share/doc/git/RelNotes/1.6.2.txt
   /usr/share/doc/git/RelNotes/1.6.3.1.txt
   /usr/share/doc/git/RelNotes/1.6.3.2.txt
   /usr/share/doc/git/RelNotes/1.6.3.3.txt
   /usr/share/doc/git/RelNotes/1.6.3.4.txt
   /usr/share/doc/git/RelNotes/1.6.3.txt
   /usr/share/doc/git/RelNotes/1.6.4.1.txt
   /usr/share/doc/git/RelNotes/1.6.4.2.txt
   /usr/share/doc/git/RelNotes/1.6.4.3.txt
   /usr/share/doc/git/RelNotes/1.6.4.4.txt
   /usr/share/doc/git/RelNotes/1.6.4.5.txt
   /usr/share/doc/git/RelNotes/1.6.4.txt
   /usr/share/doc/git/RelNotes/1.6.5.1.txt
   /usr/share/doc/git/RelNotes/1.6.5.2.txt
   /usr/share/doc/git/RelNotes/1.6.5.3.txt
   /usr/share/doc/git/RelNotes/1.6.5.4.txt
   /usr/share/doc/git/RelNotes/1.6.5.5.txt
   /usr/share/doc/git/RelNotes/1.6.5.6.txt
   /usr/share/doc/git/RelNotes/1.6.5.7.txt
   /usr/share/doc/git/RelNotes/1.6.5.8.txt
   /usr/share/doc/git/RelNotes/1.6.5.9.txt
   /usr/share/doc/git/RelNotes/1.6.5.txt
   /usr/share/doc/git/RelNotes/1.6.6.1.txt
   /usr/share/doc/git/RelNotes/1.6.6.2.txt
   /usr/share/doc/git/RelNotes/1.6.6.3.txt
   /usr/share/doc/git/RelNotes/1.6.6.txt
   /usr/share/doc/git/RelNotes/1.7.0.1.txt
   /usr/share/doc/git/RelNotes/1.7.0.2.txt
   /usr/share/doc/git/RelNotes/1.7.0.3.txt
   /usr/share/doc/git/RelNotes/1.7.0.4.txt
   /usr/share/doc/git/RelNotes/1.7.0.5.txt
   /usr/share/doc/git/RelNotes/1.7.0.6.txt
   /usr/share/doc/git/RelNotes/1.7.0.7.txt
   /usr/share/doc/git/RelNotes/1.7.0.8.txt
   /usr/share/doc/git/RelNotes/1.7.0.9.txt
   /usr/share/doc/git/RelNotes/1.7.0.txt
   /usr/share/doc/git/RelNotes/1.7.1.1.txt
   /usr/share/doc/git/RelNotes/1.7.1.2.txt
   /usr/share/doc/git/RelNotes/1.7.1.3.txt
   /usr/share/doc/git/RelNotes/1.7.1.4.txt
   /usr/share/doc/git/RelNotes/1.7.1.txt
   /usr/share/doc/git/RelNotes/1.7.10.1.txt
   /usr/share/doc/git/RelNotes/1.7.10.2.txt
   /usr/share/doc/git/RelNotes/1.7.10.3.txt
   /usr/share/doc/git/RelNotes/1.7.10.4.txt
   /usr/share/doc/git/RelNotes/1.7.10.5.txt
   /usr/share/doc/git/RelNotes/1.7.10.txt
   /usr/share/doc/git/RelNotes/1.7.11.1.txt
   /usr/share/doc/git/RelNotes/1.7.11.2.txt
   /usr/share/doc/git/RelNotes/1.7.11.3.txt
   /usr/share/doc/git/RelNotes/1.7.11.4.txt
   /usr/share/doc/git/RelNotes/1.7.11.5.txt
   /usr/share/doc/git/RelNotes/1.7.11.6.txt
   /usr/share/doc/git/RelNotes/1.7.11.7.txt
   /usr/share/doc/git/RelNotes/1.7.11.txt
   /usr/share/doc/git/RelNotes/1.7.12.1.txt
   /usr/share/doc/git/RelNotes/1.7.12.2.txt
   /usr/share/doc/git/RelNotes/1.7.12.3.txt
   /usr/share/doc/git/RelNotes/1.7.12.4.txt
   /usr/share/doc/git/RelNotes/1.7.12.txt
   /usr/share/doc/git/RelNotes/1.7.2.1.txt
   /usr/share/doc/git/RelNotes/1.7.2.2.txt
   /usr/share/doc/git/RelNotes/1.7.2.3.txt
   /usr/share/doc/git/RelNotes/1.7.2.4.txt
   /usr/share/doc/git/RelNotes/1.7.2.5.txt
   /usr/share/doc/git/RelNotes/1.7.2.txt
   /usr/share/doc/git/RelNotes/1.7.3.1.txt
   /usr/share/doc/git/RelNotes/1.7.3.2.txt
   /usr/share/doc/git/RelNotes/1.7.3.3.txt
   /usr/share/doc/git/RelNotes/1.7.3.4.txt
   /usr/share/doc/git/RelNotes/1.7.3.5.txt
   /usr/share/doc/git/RelNotes/1.7.3.txt
   /usr/share/doc/git/RelNotes/1.7.4.1.txt
   /usr/share/doc/git/RelNotes/1.7.4.2.txt
   /usr/share/doc/git/RelNotes/1.7.4.3.txt
   /usr/share/doc/git/RelNotes/1.7.4.4.txt
   /usr/share/doc/git/RelNotes/1.7.4.5.txt
   /usr/share/doc/git/RelNotes/1.7.4.txt
   /usr/share/doc/git/RelNotes/1.7.5.1.txt
   /usr/share/doc/git/RelNotes/1.7.5.2.txt
   /usr/share/doc/git/RelNotes/1.7.5.3.txt
   /usr/share/doc/git/RelNotes/1.7.5.4.txt
   /usr/share/doc/git/RelNotes/1.7.5.txt
   /usr/share/doc/git/RelNotes/1.7.6.1.txt
   /usr/share/doc/git/RelNotes/1.7.6.2.txt
   /usr/share/doc/git/RelNotes/1.7.6.3.txt
   /usr/share/doc/git/RelNotes/1.7.6.4.txt
   /usr/share/doc/git/RelNotes/1.7.6.5.txt
   /usr/share/doc/git/RelNotes/1.7.6.6.txt
   /usr/share/doc/git/RelNotes/1.7.6.txt
   /usr/share/doc/git/RelNotes/1.7.7.1.txt
   /usr/share/doc/git/RelNotes/1.7.7.2.txt
   /usr/share/doc/git/RelNotes/1.7.7.3.txt
   /usr/share/doc/git/RelNotes/1.7.7.4.txt
   /usr/share/doc/git/RelNotes/1.7.7.5.txt
   /usr/share/doc/git/RelNotes/1.7.7.6.txt
   /usr/share/doc/git/RelNotes/1.7.7.7.txt
   /usr/share/doc/git/RelNotes/1.7.7.txt
   /usr/share/doc/git/RelNotes/1.7.8.1.txt
   /usr/share/doc/git/RelNotes/1.7.8.2.txt
   /usr/share/doc/git/RelNotes/1.7.8.3.txt
   /usr/share/doc/git/RelNotes/1.7.8.4.txt
   /usr/share/doc/git/RelNotes/1.7.8.5.txt
   /usr/share/doc/git/RelNotes/1.7.8.6.txt
   /usr/share/doc/git/RelNotes/1.7.8.txt
   /usr/share/doc/git/RelNotes/1.7.9.1.txt
   /usr/share/doc/git/RelNotes/1.7.9.2.txt
   /usr/share/doc/git/RelNotes/1.7.9.3.txt
   /usr/share/doc/git/RelNotes/1.7.9.4.txt
   /usr/share/doc/git/RelNotes/1.7.9.5.txt
   /usr/share/doc/git/RelNotes/1.7.9.6.txt
   /usr/share/doc/git/RelNotes/1.7.9.7.txt
   /usr/share/doc/git/RelNotes/1.7.9.txt
   /usr/share/doc/git/RelNotes/1.8.0.1.txt
   /usr/share/doc/git/RelNotes/1.8.0.2.txt
   /usr/share/doc/git/RelNotes/1.8.0.3.txt
   /usr/share/doc/git/RelNotes/1.8.0.txt
   /usr/share/doc/git/RelNotes/1.8.1.1.txt
   /usr/share/doc/git/RelNotes/1.8.1.2.txt
   /usr/share/doc/git/RelNotes/1.8.1.3.txt
   /usr/share/doc/git/RelNotes/1.8.1.4.txt
   /usr/share/doc/git/RelNotes/1.8.1.5.txt
   /usr/share/doc/git/RelNotes/1.8.1.6.txt
   /usr/share/doc/git/RelNotes/1.8.1.txt
   /usr/share/doc/git/RelNotes/1.8.2.1.txt
   /usr/share/doc/git/RelNotes/1.8.2.2.txt
   /usr/share/doc/git/RelNotes/1.8.2.3.txt
   /usr/share/doc/git/RelNotes/1.8.2.txt
   /usr/share/doc/git/RelNotes/1.8.3.1.txt
   /usr/share/doc/git/RelNotes/1.8.3.2.txt
   /usr/share/doc/git/RelNotes/1.8.3.3.txt
   /usr/share/doc/git/RelNotes/1.8.3.4.txt
   /usr/share/doc/git/RelNotes/1.8.3.txt
   /usr/share/doc/git/RelNotes/1.8.4.1.txt
   /usr/share/doc/git/RelNotes/1.8.4.2.txt
   /usr/share/doc/git/RelNotes/1.8.4.3.txt
   /usr/share/doc/git/RelNotes/1.8.4.4.txt
   /usr/share/doc/git/RelNotes/1.8.4.5.txt
   /usr/share/doc/git/RelNotes/1.8.4.txt
   /usr/share/doc/git/RelNotes/1.8.5.1.txt
   /usr/share/doc/git/RelNotes/1.8.5.2.txt
   /usr/share/doc/git/RelNotes/1.8.5.3.txt
   /usr/share/doc/git/RelNotes/1.8.5.4.txt
   /usr/share/doc/git/RelNotes/1.8.5.5.txt
   /usr/share/doc/git/RelNotes/1.8.5.6.txt
   /usr/share/doc/git/RelNotes/1.8.5.txt
   /usr/share/doc/git/RelNotes/1.9.0.txt
   /usr/share/doc/git/RelNotes/1.9.1.txt
   /usr/share/doc/git/RelNotes/1.9.2.txt
   /usr/share/doc/git/RelNotes/1.9.3.txt
   /usr/share/doc/git/RelNotes/1.9.4.txt
   /usr/share/doc/git/RelNotes/1.9.5.txt
   /usr/share/doc/git/RelNotes/2.0.0.txt
   /usr/share/doc/git/RelNotes/2.0.1.txt
   /usr/share/doc/git/RelNotes/2.0.2.txt
   /usr/share/doc/git/RelNotes/2.0.3.txt
   /usr/share/doc/git/RelNotes/2.0.4.txt
   /usr/share/doc/git/RelNotes/2.0.5.txt
   /usr/share/doc/git/RelNotes/2.1.0.txt
   /usr/share/doc/git/RelNotes/2.1.1.txt
   /usr/share/doc/git/RelNotes/2.1.2.txt
   /usr/share/doc/git/RelNotes/2.1.3.txt
   /usr/share/doc/git/RelNotes/2.1.4.txt
   /usr/share/doc/git/RelNotes/2.10.0.txt
   /usr/share/doc/git/RelNotes/2.10.1.txt
   /usr/share/doc/git/RelNotes/2.10.2.txt
   /usr/share/doc/git/RelNotes/2.10.3.txt
   /usr/share/doc/git/RelNotes/2.10.4.txt
   /usr/share/doc/git/RelNotes/2.10.5.txt
   /usr/share/doc/git/RelNotes/2.11.0.txt
   /usr/share/doc/git/RelNotes/2.11.1.txt
   /usr/share/doc/git/RelNotes/2.11.2.txt
   /usr/share/doc/git/RelNotes/2.11.3.txt
   /usr/share/doc/git/RelNotes/2.11.4.txt
   /usr/share/doc/git/RelNotes/2.12.0.txt
   /usr/share/doc/git/RelNotes/2.12.1.txt
   /usr/share/doc/git/RelNotes/2.12.2.txt
   /usr/share/doc/git/RelNotes/2.12.3.txt
   /usr/share/doc/git/RelNotes/2.12.4.txt
   /usr/share/doc/git/RelNotes/2.12.5.txt
   /usr/share/doc/git/RelNotes/2.13.0.txt
   /usr/share/doc/git/RelNotes/2.13.1.txt
   /usr/share/doc/git/RelNotes/2.13.2.txt
   /usr/share/doc/git/RelNotes/2.13.3.txt
   /usr/share/doc/git/RelNotes/2.13.4.txt
   /usr/share/doc/git/RelNotes/2.13.5.txt
   /usr/share/doc/git/RelNotes/2.13.6.txt
   /usr/share/doc/git/RelNotes/2.13.7.txt
   /usr/share/doc/git/RelNotes/2.14.0.txt
   /usr/share/doc/git/RelNotes/2.14.1.txt
   /usr/share/doc/git/RelNotes/2.14.2.txt
   /usr/share/doc/git/RelNotes/2.14.3.txt
   /usr/share/doc/git/RelNotes/2.14.4.txt
   /usr/share/doc/git/RelNotes/2.14.5.txt
   /usr/share/doc/git/RelNotes/2.14.6.txt
   /usr/share/doc/git/RelNotes/2.15.0.txt
   /usr/share/doc/git/RelNotes/2.15.1.txt
   /usr/share/doc/git/RelNotes/2.15.2.txt
   /usr/share/doc/git/RelNotes/2.15.3.txt
   /usr/share/doc/git/RelNotes/2.15.4.txt
   /usr/share/doc/git/RelNotes/2.16.0.txt
   /usr/share/doc/git/RelNotes/2.16.1.txt
   /usr/share/doc/git/RelNotes/2.16.2.txt
   /usr/share/doc/git/RelNotes/2.16.3.txt
   /usr/share/doc/git/RelNotes/2.16.4.txt
   /usr/share/doc/git/RelNotes/2.16.5.txt
   /usr/share/doc/git/RelNotes/2.16.6.txt
   /usr/share/doc/git/RelNotes/2.17.0.txt
   /usr/share/doc/git/RelNotes/2.17.1.txt
   /usr/share/doc/git/RelNotes/2.17.2.txt
   /usr/share/doc/git/RelNotes/2.17.3.txt
   /usr/share/doc/git/RelNotes/2.17.4.txt
   /usr/share/doc/git/RelNotes/2.17.5.txt
   /usr/share/doc/git/RelNotes/2.17.6.txt
   /usr/share/doc/git/RelNotes/2.18.0.txt
   /usr/share/doc/git/RelNotes/2.18.1.txt
   /usr/share/doc/git/RelNotes/2.18.2.txt
   /usr/share/doc/git/RelNotes/2.18.3.txt
   /usr/share/doc/git/RelNotes/2.18.4.txt
   /usr/share/doc/git/RelNotes/2.18.5.txt
   /usr/share/doc/git/RelNotes/2.19.0.txt
   /usr/share/doc/git/RelNotes/2.19.1.txt
   /usr/share/doc/git/RelNotes/2.19.2.txt
   /usr/share/doc/git/RelNotes/2.19.3.txt
   /usr/share/doc/git/RelNotes/2.19.4.txt
   /usr/share/doc/git/RelNotes/2.19.5.txt
   /usr/share/doc/git/RelNotes/2.19.6.txt
   /usr/share/doc/git/RelNotes/2.2.0.txt
   /usr/share/doc/git/RelNotes/2.2.1.txt
   /usr/share/doc/git/RelNotes/2.2.2.txt
   /usr/share/doc/git/RelNotes/2.2.3.txt
   /usr/share/doc/git/RelNotes/2.20.0.txt
   /usr/share/doc/git/RelNotes/2.20.1.txt
   /usr/share/doc/git/RelNotes/2.20.2.txt
   /usr/share/doc/git/RelNotes/2.20.3.txt
   /usr/share/doc/git/RelNotes/2.20.4.txt
   /usr/share/doc/git/RelNotes/2.20.5.txt
   /usr/share/doc/git/RelNotes/2.21.0.txt
   /usr/share/doc/git/RelNotes/2.21.1.txt
   /usr/share/doc/git/RelNotes/2.21.2.txt
   /usr/share/doc/git/RelNotes/2.21.3.txt
   /usr/share/doc/git/RelNotes/2.21.4.txt
   /usr/share/doc/git/RelNotes/2.22.0.txt
   /usr/share/doc/git/RelNotes/2.22.1.txt
   /usr/share/doc/git/RelNotes/2.22.2.txt
   /usr/share/doc/git/RelNotes/2.22.3.txt
   /usr/share/doc/git/RelNotes/2.22.4.txt
   /usr/share/doc/git/RelNotes/2.22.5.txt
   /usr/share/doc/git/RelNotes/2.23.0.txt
   /usr/share/doc/git/RelNotes/2.23.1.txt
   /usr/share/doc/git/RelNotes/2.23.2.txt
   /usr/share/doc/git/RelNotes/2.23.3.txt
   /usr/share/doc/git/RelNotes/2.23.4.txt
   /usr/share/doc/git/RelNotes/2.24.0.txt
   /usr/share/doc/git/RelNotes/2.24.1.txt
   /usr/share/doc/git/RelNotes/2.24.2.txt
   /usr/share/doc/git/RelNotes/2.24.3.txt
   /usr/share/doc/git/RelNotes/2.24.4.txt
   /usr/share/doc/git/RelNotes/2.25.0.txt
   /usr/share/doc/git/RelNotes/2.25.1.txt
   /usr/share/doc/git/RelNotes/2.25.2.txt
   /usr/share/doc/git/RelNotes/2.25.3.txt
   /usr/share/doc/git/RelNotes/2.25.4.txt
   /usr/share/doc/git/RelNotes/2.25.5.txt
   /usr/share/doc/git/RelNotes/2.26.0.txt
   /usr/share/doc/git/RelNotes/2.26.1.txt
   /usr/share/doc/git/RelNotes/2.26.2.txt
   /usr/share/doc/git/RelNotes/2.26.3.txt
   /usr/share/doc/git/RelNotes/2.27.0.txt
   /usr/share/doc/git/RelNotes/2.27.1.txt
   /usr/share/doc/git/RelNotes/2.28.0.txt
   /usr/share/doc/git/RelNotes/2.28.1.txt
   /usr/share/doc/git/RelNotes/2.29.0.txt
   /usr/share/doc/git/RelNotes/2.29.1.txt
   /usr/share/doc/git/RelNotes/2.29.2.txt
   /usr/share/doc/git/RelNotes/2.29.3.txt
   /usr/share/doc/git/RelNotes/2.3.0.txt
   /usr/share/doc/git/RelNotes/2.3.1.txt
   /usr/share/doc/git/RelNotes/2.3.10.txt
   /usr/share/doc/git/RelNotes/2.3.2.txt
   /usr/share/doc/git/RelNotes/2.3.3.txt
   /usr/share/doc/git/RelNotes/2.3.4.txt
   /usr/share/doc/git/RelNotes/2.3.5.txt
   /usr/share/doc/git/RelNotes/2.3.6.txt
   /usr/share/doc/git/RelNotes/2.3.7.txt
   /usr/share/doc/git/RelNotes/2.3.8.txt
   /usr/share/doc/git/RelNotes/2.3.9.txt
   /usr/share/doc/git/RelNotes/2.30.0.txt
   /usr/share/doc/git/RelNotes/2.30.1.txt
   /usr/share/doc/git/RelNotes/2.30.2.txt
   /usr/share/doc/git/RelNotes/2.30.3.txt
   /usr/share/doc/git/RelNotes/2.30.4.txt
   /usr/share/doc/git/RelNotes/2.30.5.txt
   /usr/share/doc/git/RelNotes/2.30.6.txt
   /usr/share/doc/git/RelNotes/2.30.7.txt
   /usr/share/doc/git/RelNotes/2.30.8.txt
   /usr/share/doc/git/RelNotes/2.30.9.txt
   /usr/share/doc/git/RelNotes/2.31.0.txt
   /usr/share/doc/git/RelNotes/2.31.1.txt
   /usr/share/doc/git/RelNotes/2.31.2.txt
   /usr/share/doc/git/RelNotes/2.31.3.txt
   /usr/share/doc/git/RelNotes/2.31.4.txt
   /usr/share/doc/git/RelNotes/2.31.5.txt
   /usr/share/doc/git/RelNotes/2.31.6.txt
   /usr/share/doc/git/RelNotes/2.31.7.txt
   /usr/share/doc/git/RelNotes/2.31.8.txt
   /usr/share/doc/git/RelNotes/2.32.0.txt
   /usr/share/doc/git/RelNotes/2.32.1.txt
   /usr/share/doc/git/RelNotes/2.32.2.txt
   /usr/share/doc/git/RelNotes/2.32.3.txt
   /usr/share/doc/git/RelNotes/2.32.4.txt
   /usr/share/doc/git/RelNotes/2.32.5.txt
   /usr/share/doc/git/RelNotes/2.32.6.txt
   /usr/share/doc/git/RelNotes/2.32.7.txt
   /usr/share/doc/git/RelNotes/2.33.0.txt
   /usr/share/doc/git/RelNotes/2.33.1.txt
   /usr/share/doc/git/RelNotes/2.33.2.txt
   /usr/share/doc/git/RelNotes/2.33.3.txt
   /usr/share/doc/git/RelNotes/2.33.4.txt
   /usr/share/doc/git/RelNotes/2.33.5.txt
   /usr/share/doc/git/RelNotes/2.33.6.txt
   /usr/share/doc/git/RelNotes/2.33.7.txt
   /usr/share/doc/git/RelNotes/2.33.8.txt
   /usr/share/doc/git/RelNotes/2.34.0.txt
   /usr/share/doc/git/RelNotes/2.34.1.txt
   /usr/share/doc/git/RelNotes/2.34.2.txt
   /usr/share/doc/git/RelNotes/2.34.3.txt
   /usr/share/doc/git/RelNotes/2.34.4.txt
   /usr/share/doc/git/RelNotes/2.34.5.txt
   /usr/share/doc/git/RelNotes/2.34.6.txt
   /usr/share/doc/git/RelNotes/2.34.7.txt
   /usr/share/doc/git/RelNotes/2.34.8.txt
   /usr/share/doc/git/RelNotes/2.35.0.txt
   /usr/share/doc/git/RelNotes/2.35.1.txt
   /usr/share/doc/git/RelNotes/2.35.2.txt
   /usr/share/doc/git/RelNotes/2.35.3.txt
   /usr/share/doc/git/RelNotes/2.35.4.txt
   /usr/share/doc/git/RelNotes/2.35.5.txt
   /usr/share/doc/git/RelNotes/2.35.6.txt
   /usr/share/doc/git/RelNotes/2.35.7.txt
   /usr/share/doc/git/RelNotes/2.35.8.txt
   /usr/share/doc/git/RelNotes/2.36.0.txt
   /usr/share/doc/git/RelNotes/2.36.1.txt
   /usr/share/doc/git/RelNotes/2.36.2.txt
   /usr/share/doc/git/RelNotes/2.36.3.txt
   /usr/share/doc/git/RelNotes/2.36.4.txt
   /usr/share/doc/git/RelNotes/2.36.5.txt
   /usr/share/doc/git/RelNotes/2.36.6.txt
   /usr/share/doc/git/RelNotes/2.37.0.txt
   /usr/share/doc/git/RelNotes/2.37.1.txt
   /usr/share/doc/git/RelNotes/2.37.2.txt
   /usr/share/doc/git/RelNotes/2.37.3.txt
   /usr/share/doc/git/RelNotes/2.37.4.txt
   /usr/share/doc/git/RelNotes/2.37.5.txt
   /usr/share/doc/git/RelNotes/2.37.6.txt
   /usr/share/doc/git/RelNotes/2.37.7.txt
   /usr/share/doc/git/RelNotes/2.38.0.txt
   /usr/share/doc/git/RelNotes/2.38.1.txt
   /usr/share/doc/git/RelNotes/2.38.2.txt
   /usr/share/doc/git/RelNotes/2.38.3.txt
   /usr/share/doc/git/RelNotes/2.38.4.txt
   /usr/share/doc/git/RelNotes/2.38.5.txt
   /usr/share/doc/git/RelNotes/2.39.0.txt
   /usr/share/doc/git/RelNotes/2.39.1.txt
   /usr/share/doc/git/RelNotes/2.39.2.txt
   /usr/share/doc/git/RelNotes/2.39.3.txt
   /usr/share/doc/git/RelNotes/2.4.0.txt
   /usr/share/doc/git/RelNotes/2.4.1.txt
   /usr/share/doc/git/RelNotes/2.4.10.txt
   /usr/share/doc/git/RelNotes/2.4.11.txt
   /usr/share/doc/git/RelNotes/2.4.12.txt
   /usr/share/doc/git/RelNotes/2.4.2.txt
   /usr/share/doc/git/RelNotes/2.4.3.txt
   /usr/share/doc/git/RelNotes/2.4.4.txt
   /usr/share/doc/git/RelNotes/2.4.5.txt
   /usr/share/doc/git/RelNotes/2.4.6.txt
   /usr/share/doc/git/RelNotes/2.4.7.txt
   /usr/share/doc/git/RelNotes/2.4.8.txt
   /usr/share/doc/git/RelNotes/2.4.9.txt
   /usr/share/doc/git/RelNotes/2.40.0.txt
   /usr/share/doc/git/RelNotes/2.40.1.txt
   /usr/share/doc/git/RelNotes/2.41.0.txt
   /usr/share/doc/git/RelNotes/2.42.0.txt
   /usr/share/doc/git/RelNotes/2.42.1.txt
   /usr/share/doc/git/RelNotes/2.43.0.txt
   /usr/share/doc/git/RelNotes/2.5.0.txt
   /usr/share/doc/git/RelNotes/2.5.1.txt
   /usr/share/doc/git/RelNotes/2.5.2.txt
   /usr/share/doc/git/RelNotes/2.5.3.txt
   /usr/share/doc/git/RelNotes/2.5.4.txt
   /usr/share/doc/git/RelNotes/2.5.5.txt
   /usr/share/doc/git/RelNotes/2.5.6.txt
   /usr/share/doc/git/RelNotes/2.6.0.txt
   /usr/share/doc/git/RelNotes/2.6.1.txt
   /usr/share/doc/git/RelNotes/2.6.2.txt
   /usr/share/doc/git/RelNotes/2.6.3.txt
   /usr/share/doc/git/RelNotes/2.6.4.txt
   /usr/share/doc/git/RelNotes/2.6.5.txt
   /usr/share/doc/git/RelNotes/2.6.6.txt
   /usr/share/doc/git/RelNotes/2.6.7.txt
   /usr/share/doc/git/RelNotes/2.7.0.txt
   /usr/share/doc/git/RelNotes/2.7.1.txt
   /usr/share/doc/git/RelNotes/2.7.2.txt
   /usr/share/doc/git/RelNotes/2.7.3.txt
   /usr/share/doc/git/RelNotes/2.7.4.txt
   /usr/share/doc/git/RelNotes/2.7.5.txt
   /usr/share/doc/git/RelNotes/2.7.6.txt
   /usr/share/doc/git/RelNotes/2.8.0.txt
   /usr/share/doc/git/RelNotes/2.8.1.txt
   /usr/share/doc/git/RelNotes/2.8.2.txt
   /usr/share/doc/git/RelNotes/2.8.3.txt
   /usr/share/doc/git/RelNotes/2.8.4.txt
   /usr/share/doc/git/RelNotes/2.8.5.txt
   /usr/share/doc/git/RelNotes/2.8.6.txt
   /usr/share/doc/git/RelNotes/2.9.0.txt
   /usr/share/doc/git/RelNotes/2.9.1.txt
   /usr/share/doc/git/RelNotes/2.9.2.txt
   /usr/share/doc/git/RelNotes/2.9.3.txt
   /usr/share/doc/git/RelNotes/2.9.4.txt
   /usr/share/doc/git/RelNotes/2.9.5.txt
   /usr/share/doc/git/contrib/buildsystems/CMakeLists.txt
   /usr/share/doc/git/contrib/contacts/git-contacts.txt
   /usr/share/doc/git/contrib/hg-to-git/hg-to-git.txt
   /usr/share/doc/git/contrib/subtree/git-subtree.txt
   /usr/share/doc/gnupg/examples/qualified.txt
   /usr/share/doc/gnupg/examples/trustlist.txt
   /usr/share/doc/gpg-agent/examples/trustlist.txt
   /usr/share/doc/hplip/users-guide.txt
   /usr/share/doc/libasound2t64/examples/asoundrc.txt
   /usr/share/doc/libauthen-sasl-perl/api.txt
   /usr/share/doc/libbpfcc/FAQ.txt
   /usr/share/doc/libdb5.3t64/build_signature_amd64.txt
   /usr/share/doc/libgphoto2-6/OUTDATED.txt
   /usr/share/doc/libio-socket-ssl-perl/debugging.txt
   /usr/share/doc/libsane-common/leo/leo.txt
   /usr/share/doc/libsane-common/plustek/Plustek-PARPORT-TODO.txt
   /usr/share/doc/libsane-common/plustek/Plustek-PARPORT.txt
   /usr/share/doc/libsane-common/plustek/Plustek-USB-TODO.txt
   /usr/share/doc/libsane-common/sceptre/s1200.txt
   /usr/share/doc/libsane-common/umax/negative-types.txt
   /usr/share/doc/libsynctex2/README.txt
   /usr/share/doc/mount/mount.txt
   /usr/share/doc/openssl/fingerprints.txt
   /usr/share/doc/openssl/HOWTO/keys.txt
   /usr/share/doc/powermgmt-base/power_supply.txt
   /usr/share/doc/publicsuffix/examples/test_psl.txt
   /usr/share/doc/sssd-common/BUILD.txt
   /usr/share/doc/util-linux/00-about-docs.txt
   /usr/share/doc/util-linux/PAM-configuration.txt
   /usr/share/doc/util-linux/blkid.txt
   /usr/share/doc/util-linux/cal.txt
   /usr/share/doc/util-linux/col.txt
   /usr/share/doc/util-linux/deprecated.txt
   /usr/share/doc/util-linux/getopt.txt
   /usr/share/doc/util-linux/getopt_changelog.txt
   /usr/share/doc/util-linux/howto-build-sys.txt
   /usr/share/doc/util-linux/howto-compilation.txt
   /usr/share/doc/util-linux/howto-debug.txt
   /usr/share/doc/util-linux/howto-man-page.txt
   /usr/share/doc/util-linux/howto-tests.txt
   /usr/share/doc/util-linux/hwclock.txt
   /usr/share/doc/util-linux/modems-with-agetty.txt
   /usr/share/doc/util-linux/mount.txt
   /usr/share/doc/util-linux/pg.txt
   /usr/share/doc/util-linux/release-schedule.txt
   /usr/share/doc/xorg/index.txt
   /usr/share/doc/xorg/upstream-features.txt
   /usr/share/doc/xorg/faq/general.txt
   /usr/share/doc/xorg/howto/report-bugs.txt
   /usr/share/doc/xorg/howto/triage-bugs.txt
   /usr/share/doc/xorg/reference/experimental.txt
   /usr/share/doc/xorg/reference/squeeze-backports.txt
   /usr/share/doc/xorg/reference/upstream-contacts.txt
   /usr/share/gnupg/help.be.txt
   /usr/share/gnupg/help.ca.txt
   /usr/share/gnupg/help.cs.txt
   /usr/share/gnupg/help.da.txt
   /usr/share/gnupg/help.de.txt
   /usr/share/gnupg/help.el.txt
   /usr/share/gnupg/help.eo.txt
   /usr/share/gnupg/help.es.txt
   /usr/share/gnupg/help.et.txt
   /usr/share/gnupg/help.fi.txt
   /usr/share/gnupg/help.fr.txt
   /usr/share/gnupg/help.gl.txt
   /usr/share/gnupg/help.hu.txt
   /usr/share/gnupg/help.id.txt
   /usr/share/gnupg/help.it.txt
   /usr/share/gnupg/help.ja.txt
   /usr/share/gnupg/help.nb.txt
   /usr/share/gnupg/help.pl.txt
   /usr/share/gnupg/help.pt.txt
   /usr/share/gnupg/help.pt_BR.txt
   /usr/share/gnupg/help.ro.txt
   /usr/share/gnupg/help.ru.txt
   /usr/share/gnupg/help.sk.txt
   /usr/share/gnupg/help.sv.txt
   /usr/share/gnupg/help.tr.txt
   /usr/share/gnupg/help.txt
   /usr/share/gnupg/help.zh_CN.txt
   /usr/share/gnupg/help.zh_TW.txt
   /usr/share/ibus-table/tables/template.txt
   /usr/share/ieee-data/iab.txt
   /usr/share/ieee-data/mam.txt
   /usr/share/ieee-data/oui.txt
   /usr/share/ieee-data/oui36.txt
   /usr/share/libcaca/caca.txt
   /usr/share/netpbm/rgb.txt
   /usr/share/perl/5.38.2/Unicode/Collate/allkeys.txt
   /usr/share/perl/5.38.2/Unicode/Collate/keys.txt
   /usr/share/perl/5.38.2/unicore/Blocks.txt
   /usr/share/perl/5.38.2/unicore/NamedSequences.txt
   /usr/share/perl/5.38.2/unicore/SpecialCasing.txt
   /usr/share/snmp/mibs/LM-SENSORS-MIB.txt
   /usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
   /usr/share/snmp/mibs/NET-SNMP-EXAMPLES-MIB.txt
   /usr/share/snmp/mibs/NET-SNMP-EXTEND-MIB.txt
   /usr/share/snmp/mibs/NET-SNMP-MIB.txt
   /usr/share/snmp/mibs/NET-SNMP-PASS-MIB.txt
   /usr/share/snmp/mibs/NET-SNMP-TC.txt
   /usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt
   /usr/share/snmp/mibs/UCD-DEMO-MIB.txt
   /usr/share/snmp/mibs/UCD-DISKIO-MIB.txt
   /usr/share/snmp/mibs/UCD-DLMOD-MIB.txt
   /usr/share/snmp/mibs/UCD-IPFWACC-MIB.txt
   /usr/share/snmp/mibs/UCD-SNMP-MIB.txt
   /usr/share/vim/vim91/doc/help.txt
   /usr/share/vim/vim91/doc/sponsor.txt
   /usr/share/vim/vim91/doc/uganda.txt
   /usr/share/vim/vim91/doc/version9.txt
   /usr/src/linux-headers-6.17.0-14-generic/scripts/head-object-list.txt
   /usr/src/linux-headers-6.17.0-14-generic/scripts/spelling.txt
   /usr/src/linux-hwe-6.17-headers-6.17.0-14/arch/sh/include/mach-ecovec24/mach/partner-jet-setup.txt
   /usr/src/linux-hwe-6.17-headers-6.17.0-14/arch/sh/include/mach-kfr2r09/mach/partner-jet-setup.txt
   /usr/src/linux-hwe-6.17-headers-6.17.0-14/scripts/head-object-list.txt
   /usr/src/linux-hwe-6.17-headers-6.17.0-14/scripts/spelling.txt
   /var/cache/dictionaries-common/ispell-dicts-list.txt
   /var/lib/cloud/instances/iid-datasource-none/cloud-config.txt
   /var/lib/cloud/instances/iid-datasource-none/user-data.txt
   /var/lib/cloud/instances/iid-datasource-none/vendor-data.txt
   /var/lib/cloud/instances/iid-datasource-none/vendor-data2.txt
   /var/lib/ieee-data/iab.txt
   /var/lib/ieee-data/mam.txt
   /var/lib/ieee-data/oui.txt
   /var/lib/ieee-data/oui36.txt
   /var/log/installer/installer-journal.txt
   ```

### Percobaan 6 : Mencari text pada file

1. *$ grep Hallo \*.txt*

   ```praditadf@praditadf-VirtualBox:~$ grep Hallo *.txt
   bye.txt:Hallo apa khabar
   halo.txt:Hallo apa khabar
   ```

## LATIHAN

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

   ```
   praditadf@praditadf-VirtualBox:~$ cd
   praditadf@praditadf-VirtualBox:~$ pwd
   /home/praditadf
   praditadf@praditadf-VirtualBox:~$ ls -al
   total 316
   drwxr-x--- 23 praditadf praditadf   4096 Mar 10 20:06 .
   drwxr-xr-x  3 root      root        4096 Feb 14 18:29 ..
   -rw-r--r--  1 praditadf praditadf   1761 Feb 24 18:16 aaaaaaa
   -rw-rw-r--  1 praditadf praditadf   3229 Mar  4 10:46 backup-error.log
   -rwxrwxr-x  1 praditadf praditadf    151 Mar  4 10:45 backup.sh
   -rw-rw-r--  1 praditadf praditadf    951 Mar  4 10:46 backup-succes.log
   -rw-rw-r--  1 praditadf praditadf      0 Mar  3 18:51 backup-success.log
   -rw-rw-r--  1 praditadf praditadf     45 Mar  4 10:46 backup.tar.gz
   -rw-------  1 praditadf praditadf  14427 Mar 10 20:12 .bash_history
   -rw-r--r--  1 praditadf praditadf    220 Mar 31  2024 .bash_logout
   -rw-r--r--  1 praditadf praditadf   3771 Mar 31  2024 .bashrc
   lrwxrwxrwx  1 praditadf praditadf      1 Mar 10 20:03 bye.txt -> z
   drwx------ 14 praditadf praditadf   4096 Mar  4 11:46 .cache
   drwxr-xr-x 19 praditadf praditadf   4096 Mar  4 12:50 .config
   -rw-rw-r--  1 praditadf praditadf     44 Feb 24 18:20 config.txt
   drwx------  3 praditadf praditadf   4096 Mar  4 11:48 .copilot
   drwxr-xr-x  2 praditadf praditadf   4096 Feb 14 18:36 Desktop
   drwxr-xr-x  2 praditadf praditadf   4096 Feb 14 18:36 Documents
   drwxrwxr-x  3 praditadf praditadf   4096 Mar  4 11:47 .dotnet
   drwxr-xr-x  2 praditadf praditadf   4096 Mar  4 13:14 Downloads
   -rw-rw-r--  1 praditadf praditadf      0 Mar  3 17:16 error.log
   -rw-rw-r--  1 praditadf praditadf     60 Mar  4 12:24 .gitconfig
   drwxrwxr-x  3 praditadf praditadf   4096 Mar  4 11:55 Github
   drwx------  2 praditadf praditadf   4096 Mar 10 20:13 .gnupg
   -rw-rw-r--  3 praditadf praditadf     17 Mar 10 20:02 halo.txt
   -rw-rw-r--  1 praditadf praditadf    799 Mar  3 17:16 large-logs.txt
   -rw-------  1 praditadf praditadf     20 Feb 25 12:29 .lesshst
   drwx------  4 praditadf praditadf   4096 Feb 14 18:36 .local
   -rw-rw-r--  1 praditadf praditadf   3432 Mar  3 18:13 log.txt
   -rw-rw-r--  1 praditadf praditadf    139 Mar  4 10:11 monitor.sh
   drwxr-xr-x  2 praditadf praditadf   4096 Feb 14 18:36 Music
   drwxrwxr-x  2 praditadf praditadf   4096 Mar 10 20:02 mydir
   -rw-rw-r--  1 praditadf praditadf   1411 Mar 10 20:06 myerror.txt
   -rw-rw-r--  1 praditadf praditadf 110870 Mar  3 18:26 path.txt
   drwxr-xr-x  2 praditadf praditadf   4096 Feb 14 18:36 Pictures
   -rw-rw-r--  1 praditadf praditadf   9947 Mar  3 17:41 ping-log.txt
   drwx------  3 praditadf praditadf   4096 Mar  4 11:46 .pki
   drwxrwxr-x  3 praditadf praditadf   4096 Mar  9 20:53 praktikum-os
   -rw-r--r--  1 praditadf praditadf    807 Mar 31  2024 .profile
   drwxr-xr-x  2 praditadf praditadf   4096 Feb 14 18:36 Public
   drwx------  7 praditadf praditadf   4096 Mar  4 11:45 snap
   -rw-rw-r--  1 praditadf praditadf    411 Mar  3 17:31 sorted-users.txt
   drwx------  2 praditadf praditadf   4096 Feb 14 18:37 .ssh
   -rw-r--r--  1 praditadf praditadf      0 Feb 15 07:12 .sudo_as_admin_successful
   -rw-rw-r--  1 praditadf praditadf    112 Mar  3 17:48 system
   drwxr-xr-x  2 praditadf praditadf   4096 Feb 14 18:36 Templates
   drwxr-xr-x  2 praditadf praditadf   4096 Feb 14 18:36 Videos
   drwxrwxr-x  4 praditadf praditadf   4096 Mar  4 11:46 .vscode
   -rw-rw-r--  1 praditadf praditadf    223 Mar  4 11:09 .wget-hsts
   -rw-rw-r--  1 praditadf praditadf    381 Mar  4 11:09 wget-log
   -rw-rw-r--  3 praditadf praditadf     17 Mar 10 20:02 z
   praditadf@praditadf-VirtualBox:~$ cd .
   praditadf@praditadf-VirtualBox:~$ pwd
   /home/praditadf
   praditadf@praditadf-VirtualBox:~$ cd ..
   praditadf@praditadf-VirtualBox:/home$ pwd
   /home
   praditadf@praditadf-VirtualBox:/home$ ls -al
   total 12
   drwxr-xr-x  3 root      root      4096 Feb 14 18:29 .
   drwxr-xr-x 23 root      root      4096 Feb 14 18:28 ..
   drwxr-x--- 23 praditadf praditadf 4096 Mar 10 20:06 praditadf
   praditadf@praditadf-VirtualBox:/home$ cd ..
   praditadf@praditadf-VirtualBox:/$ pwd
   /
   praditadf@praditadf-VirtualBox:/$ ls -al
   total 2097252
   drwxr-xr-x  23 root root       4096 Feb 14 18:28 .
   drwxr-xr-x  23 root root       4096 Feb 14 18:28 ..
   lrwxrwxrwx   1 root root          7 Apr 22  2024 bin -> usr/bin
   drwxr-xr-x   2 root root       4096 Feb 26  2024 bin.usr-is-merged
   drwxr-xr-x   3 root root       4096 Mar  4 11:21 boot
   dr-xr-xr-x   2 root root       4096 Feb 10 08:38 cdrom
   drwxr-xr-x  19 root root       4180 Mar 10 17:58 dev
   drwxr-xr-x 141 root root      12288 Mar  4 12:58 etc
   drwxr-xr-x   3 root root       4096 Feb 14 18:29 home
   lrwxrwxrwx   1 root root          7 Apr 22  2024 lib -> usr/lib
   lrwxrwxrwx   1 root root          9 Apr 22  2024 lib64 -> usr/lib64
   drwxr-xr-x   2 root root       4096 Apr  8  2024 lib.usr-is-merged
   drwx------   2 root root      16384 Feb 14 18:13 lost+found
   drwxr-xr-x   3 root root       4096 Feb 25 18:43 media
   drwxr-xr-x   2 root root       4096 Feb 10 07:19 mnt
   drwxr-xr-x   2 root root       4096 Feb 10 07:19 opt
   dr-xr-xr-x 287 root root          0 Mar 10 17:58 proc
   drwx------   5 root root       4096 Feb 25 10:37 root
   drwxr-xr-x  35 root root        880 Mar 10 18:44 run
   lrwxrwxrwx   1 root root          8 Apr 22  2024 sbin -> usr/sbin
   drwxr-xr-x   2 root root       4096 Mar 31  2024 sbin.usr-is-merged
   drwxr-xr-x  14 root root       4096 Mar  4 11:45 snap
   drwxr-xr-x   2 root root       4096 Feb 10 07:19 srv
   -rw-------   1 root root 2147483648 Feb 14 18:28 swap.img
   dr-xr-xr-x  13 root root          0 Mar 10 20:12 sys
   drwxrwxrwt  22 root root       4096 Mar 10 20:11 tmp
   drwxr-xr-x  12 root root       4096 Feb 10 07:19 usr
   drwxr-xr-x  14 root root       4096 Feb 14 18:35 var
   praditadf@praditadf-VirtualBox:/$ cd /etc
   praditadf@praditadf-VirtualBox:/etc$ ls -al | more
   total 1164
   drwxr-xr-x 141 root                 root                 12288 Mar  4 12:58 .
   drwxr-xr-x  23 root                 root                  4096 Feb 14 18:28 ..
   -rw-r--r--   1 root                 root                  3444 Jul  6  2023 addu
   ser.conf
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:28 alsa
   drwxr-xr-x   2 root                 root                  4096 Mar  4 12:58 alte
   rnatives
   -rw-r--r--   1 root                 root                   335 Apr  8  2024 anac
   rontab
   -rw-r--r--   1 root                 root                   433 Apr  8  2024 apg.
   conf
   drwxr-xr-x   5 root                 root                  4096 Feb 10 07:27 apm
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:27 appa
   rmor
   drwxr-xr-x   9 root                 root                  4096 Feb 10 07:31 appa
   rmor.d
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:29 appo
   rt
   drwxr-xr-x   9 root                 root                  4096 Feb 15 07:25 apt
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:29 avah
   i
   -rw-r--r--   1 root                 root                  2319 Mar 31  2024 bash
   .bashrc
   -rw-r--r--   1 root                 root                    45 Jan 25  2020 bash
   _completion
   drwxr-xr-x   2 root                 root                  4096 Mar  4 11:52 bash
   _completion.d
   -rw-r--r--   1 root                 root                   367 Aug  2  2022 bind
   resvport.blacklist
   drwxr-xr-x   2 root                 root                  4096 Apr 19  2024 binf
   mt.d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 blue
   tooth
   -rw-r-----   1 root                 root                    33 Feb 10 07:31 brla
   pi.key
   drwxr-xr-x   7 root                 root                  4096 Feb 10 07:28 brlt
   ty
   -rw-r--r--   1 root                 root                 30571 Mar 31  2024 brlt
   ty.conf
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:19 ca-c
   ertificates
   -rw-r--r--   1 root                 root                  6288 Feb 10 07:20 ca-c
   ertificates.conf
   drwxr-s---   2 root                 dip                   4096 Feb 10 07:29 chat
   scripts
   drwxr-xr-x   5 root                 root                  4096 Feb 14 18:37 clou
   d
   drwxr-xr-x   2 colord               colord                4096 Feb 14 18:36 colo
   rd
   drwxr-xr-x   2 root                 root                  4096 Feb 14 18:23 cons
   ole-setup
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 crac
   klib
   drwx------   2 root                 root                  4096 Apr 19  2024 cred
   store
   drwx------   2 root                 root                  4096 Apr 19  2024 cred
   store.encrypted
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 cron
   .d
   drwxr-xr-x   2 root                 root                  4096 Mar  4 12:58 cron
   .daily
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:19 cron
   .hourly
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:28 cron
   .monthly
   -rw-r--r--   1 root                 root                  1136 Mar 31  2024 cron
   tab
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 cron
   .weekly
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:19 cron
   .yearly
   drwxr-xr-x   5 root                 lp                    4096 Mar 10 19:56 cups
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 cups
   helpers
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:19 dbus
   -1
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:28 dcon
   f
   -rw-r--r--   1 root                 root                  2967 Apr 12  2024 debc
   onf.conf
   -rw-r--r--   1 root                 root                    11 Apr 22  2024 debi
   an_version
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:28 debu
   ginfod
   drwxr-xr-x   3 root                 root                  4096 Mar  4 11:20 defa
   ult
   -rw-r--r--   1 root                 root                  1706 Jul  6  2023 delu
   ser.conf
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:21 depm
   od.d
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:20 dhcp
   -rw-r--r--   1 root                 root                  1429 Mar 31  2024 dhcp
   cd.conf
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 dict
   ionaries-common
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:21 dpkg
   -rw-r--r--   1 root                 root                   685 Apr  8  2024 e2sc
   rub.conf
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:27 emac
   s
   -rw-r--r--   1 root                 root                   106 Feb 10 07:19 envi
   ronment
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 envi
   ronment.d
   -rw-r--r--   1 root                 root                  1853 Oct 18  2022 ethe
   rtypes
   drwxr-xr-x   5 root                 root                  4096 Feb 10 07:29 font
   s
   -rw-r--r--   1 root                 root                    20 Apr  4  2024 fpri
   ntd.conf
   -rw-r--r--   1 root                 root                   473 Feb 14 18:28 fsta
   b
   -rw-r--r--   1 root                 root                   694 Apr  8  2024 fuse
   .conf
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:29 fwup
   d
   -rw-r--r--   1 root                 root                  2584 Jan 31  2024 gai.
   conf
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:29 gdb
   drwxr-xr-x   8 root                 root                  4096 Feb 10 07:31 gdm3
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:31 geoc
   lue
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:27 ghos
   tscript
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:27 glvn
   d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:28 gnom
   e
   drwxr-xr-x   2 gnome-remote-desktop gnome-remote-desktop  4096 Feb 10 07:31 gnom
   e-remote-desktop
   drwxr-xr-x   2 root                 root                  4096 Feb 18 11:19 gnut
   ls
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 grof
   f
   -rw-r--r--   1 root                 root                  1149 Mar  4 12:58 grou
   p
   -rw-r--r--   1 root                 root                  1134 Feb 14 18:35 grou
   p-
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:33 grub
   .d
   -rw-r-----   1 root                 shadow                 973 Mar  4 12:58 gsha
   dow
   -rw-r-----   1 root                 shadow                 961 Feb 14 18:35 gsha
   dow-
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:19 gss
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 gtk-
   2.0
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 gtk-
   3.0
   -rw-r--r--   1 root                 root                  4436 Oct  6  2022 hdpa
   rm.conf
   -rw-r--r--   1 root                 root                    92 Apr 22  2024 host
   .conf
   -rw-r--r--   1 root                 root                    21 Feb 14 18:29 host
   name
   -rw-r--r--   1 root                 root                   235 Feb 14 18:29 host
   s
   -rw-r--r--   1 root                 root                   411 Feb 10 07:28 host
   s.allow
   -rw-r--r--   1 root                 root                   711 Feb 10 07:28 host
   s.deny
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 hp
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:28 ifpl
   ugd
   drwxr-xr-x   2 root                 root                  4096 Feb 18 20:18 Imag
   eMagick-6
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 init
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 init
   .d
   drwxr-xr-x   5 root                 root                  4096 Feb 10 07:29 init
   ramfs-tools
   -rw-r--r--   1 root                 root                  1875 Mar 31  2024 inpu
   trc
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 inss
   erv.conf.d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 ipp-
   usb
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:21 ipro
   ute2
   -rw-r--r--   1 root                 root                    26 Feb  6 14:23 issu
   e
   -rw-r--r--   1 root                 root                    19 Feb  6 14:23 issu
   e.net
   drwxr-xr-x   6 root                 root                  4096 Feb 14 18:25 kern
   el
   -rw-r--r--   1 root                 root                  1308 Mar 31  2024 kern
   eloops.conf
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 krb5
   .conf.d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:28 ldap
   -rw-r--r--   1 root                 root                 57607 Mar  4 12:58 ld.s
   o.cache
   -rw-r--r--   1 root                 root                    34 Aug  2  2022 ld.s
   o.conf
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:21 ld.s
   o.conf.d
   -rw-r--r--   1 root                 root                   267 Apr 22  2024 lega
   l
   -rw-r--r--   1 root                 root                    27 Apr  8  2024 liba
   o.conf
   -rw-r--r--   1 root                 root                   191 Mar 31  2024 liba
   udit.conf
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:28 libb
   lockdev
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 libi
   bverbs.d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 libn
   l-3
   drwxr-xr-x   2 root                 root                  4096 Apr  8  2024 libp
   aper.d
   -rw-r--r--   1 root                 root                  2996 Mar 30  2024 loca
   le.alias
   -rw-r--r--   1 root                 root                    17 Feb 14 18:36 loca
   le.conf
   -rw-r--r--   1 root                 root                  9563 Feb 14 18:36 loca
   le.gen
   lrwxrwxrwx   1 root                 root                    32 Feb 14 18:36 loca
   ltime -> /usr/share/zoneinfo/Asia/Jakarta
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:27 logc
   heck
   -rw-r--r--   1 root                 root                 12345 Feb 22  2024 logi
   n.defs
   -rw-r--r--   1 root                 root                   586 Apr  8  2024 logr
   otate.conf
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 logr
   otate.d
   -rw-r--r--   1 root                 root                   104 Feb  6 14:22 lsb-
   release
   -r--r--r--   1 root                 root                    33 Feb 14 18:23 mach
   ine-id
   -rw-r--r--   1 root                 root                   111 Mar 31  2024 magi
   c
   -rw-r--r--   1 root                 root                   111 Mar 31  2024 magi
   c.mime
   -rw-r--r--   1 root                 root                  5230 Apr  8  2024 manp
   ath.config
   -rw-r--r--   1 root                 root                 75113 Jul 12  2023 mime
   .types
   -rw-r--r--   1 root                 root                   744 Apr  8  2024 mke2
   fs.conf
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:28 Mode
   mManager
   drwxr-xr-x   2 root                 root                  4096 Mar  4 11:20 modp
   robe.d
   -rw-r--r--   1 root                 root                   212 Feb 10 07:20 modu
   les
   drwxr-xr-x   2 root                 root                  4096 Feb 18 13:55 modu
   les-load.d
   lrwxrwxrwx   1 root                 root                    19 Feb 10 07:19 mtab
   -> ../proc/self/mounts
   -rw-r--r--   1 root                 root                 11424 May 23  2023 nano
   rc
   -rw-r--r--   1 root                 root                   767 Mar 31  2024 netc
   onfig
   drwxr-xr-x   2 root                 root                  4096 Feb 14 18:29 netp
   lan
   drwxr-xr-x   6 root                 root                  4096 Feb 10 07:28 netw
   ork
   drwxr-xr-x   8 root                 root                  4096 Feb 10 07:20 netw
   orkd-dispatcher
   drwxr-xr-x   8 root                 root                  4096 Feb 10 07:31 Netw
   orkManager
   -rw-r--r--   1 root                 root                    91 Apr 22  2024 netw
   orks
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:20 newt
   -rwxr-xr-x   1 root                 root                   243 Oct 19  2023 nfta
   bles.conf
   -rw-r--r--   1 root                 root                   594 Feb 10 07:29 nssw
   itch.conf
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:29 open
   vpn
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:19 opt
   lrwxrwxrwx   1 root                 root                    21 Feb  6 14:23 os-r
   elease -> ../usr/lib/os-release
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 Pack
   ageKit
   -rw-r--r--   1 root                 root                   552 Oct 14  2022 pam.
   conf
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 pam.
   d
   -rw-r--r--   1 root                 root                     3 Feb 10 07:28 pape
   rsize
   -rw-r--r--   1 root                 root                  2873 Feb 14 18:29 pass
   wd
   -rw-r--r--   1 root                 root                  2815 Feb 10 07:31 pass
   wd-
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 pcmc
   ia
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:27 perl
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:28 pki
   drwxr-xr-x   2 root                 root                  4096 Feb 25  2025 plym
   outh
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:28 pm
   -rw-r--r--   1 root                 root                  7649 Feb 10 07:29 pnm2
   ppa.conf
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:28 polk
   it-1
   drwxr-xr-x   8 root                 dip                   4096 Feb 10 07:29 ppp
   -rw-r--r--   1 root                 root                   582 Apr 22  2024 prof
   ile
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 prof
   ile.d
   -rw-r--r--   1 root                 root                  3144 Oct 18  2022 prot
   ocols
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:29 puls
   e
   -rw-------   1 root                 root                     0 Feb 10 07:19 .pwd
   .lock
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:20 pyth
   on3
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:21 pyth
   on3.12
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 rc0.
   d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 rc1.
   d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 rc2.
   d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 rc3.
   d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 rc4.
   d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 rc5.
   d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 rc6.
   d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 rcS.
   d
   lrwxrwxrwx   1 root                 root                    39 Feb 10 07:20 reso
   lv.conf -> ../run/systemd/resolve/stub-resolv.conf
   -rw-r--r--   1 root                 root                   862 Feb 10 07:19 .res
   olv.conf.systemd-resolved.bak
   lrwxrwxrwx   1 root                 root                    13 Apr  8  2024 rmt 
   -> /usr/sbin/rmt
   -rw-r--r--   1 root                 root                   911 Oct 18  2022 rpc
   -rw-r--r--   1 root                 root                  1213 Mar 22  2024 rsys
   log.conf
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 rsys
   log.d
   -rw-r--r--   1 root                 root                  5772 Jan  7  2024 ryge
   l.conf
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:31 sane
   .d
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:28 secu
   rity
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:19 seli
   nux
   -rw-r--r--   1 root                 root                 10593 Mar 31  2024 sens
   ors3.conf
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:28 sens
   ors.d
   -rw-r--r--   1 root                 root                 12813 Mar 28  2021 serv
   ices
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:31 sgml
   -rw-r-----   1 root                 shadow                1342 Feb 14 18:35 shad
   ow
   -rw-r-----   1 root                 shadow                1342 Feb 14 18:29 shad
   ow-
   -rw-r--r--   1 root                 root                   118 Feb 10 07:19 shel
   ls
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:19 skel
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:28 snmp
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:29 spee
   ch-dispatcher
   drwxr-xr-x   3 root                 root                  4096 Feb 14 18:35 ssh
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:21 ssl
   drwx--x--x   3 root                 root                  4096 Feb 10 07:28 sssd
   -rw-r--r--   1 root                 root                    23 Feb 14 18:29 subg
   id
   -rw-r--r--   1 root                 root                     0 Feb 10 07:19 subg
   id-
   -rw-r--r--   1 root                 root                    23 Feb 14 18:29 subu
   id
   -rw-r--r--   1 root                 root                     0 Feb 10 07:19 subu
   id-
   -rw-r--r--   1 root                 root                  4343 Apr  8  2024 sudo
   .conf
   -r--r-----   1 root                 root                  1800 Jan 30  2024 sudo
   ers
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:21 sudo
   ers.d
   -rw-r--r--   1 root                 root                  9804 Apr  8  2024 sudo
   _logsrvd.conf
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:20 supe
   rcat
   -rw-r--r--   1 root                 root                  2209 Mar 24  2024 sysc
   tl.conf
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:21 sysc
   tl.d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 syss
   tat
   drwxr-xr-x   6 root                 root                  4096 Feb 10 07:29 syst
   emd
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:19 term
   info
   drwxr-xr-x   2 root                 root                  4096 Feb 14 18:27 ther
   mald
   -rw-r--r--   1 root                 root                    13 Feb 14 18:36 time
   zone
   drwxr-xr-x   2 root                 root                  4096 Apr 19  2024 tmpf
   iles.d
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:21 ubun
   tu-advantage
   -rw-r--r--   1 root                 root                  1260 Jan 27  2023 ucf.
   conf
   drwxr-xr-x   4 root                 root                  4096 Feb 10 07:21 udev
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 udis
   ks2
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:29 ufw
   -rw-r--r--   1 root                 root                   208 Feb 10 07:19 .upd
   ated
   -rw-r--r--   1 root                 root                   583 Aug  1  2023 upda
   tedb.conf
   drwxr-xr-x   3 root                 root                  4096 Feb 10 07:30 upda
   te-manager
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 upda
   te-motd.d
   drwxr-xr-x   2 root                 root                  4096 Apr  2  2025 upda
   te-notifier
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 UPow
   er
   -rw-r--r--   1 root                 root                  1523 Apr  8  2024 usb_
   modeswitch.conf
   drwxr-xr-x   2 root                 root                  4096 Dec 17  2023 usb_
   modeswitch.d
   lrwxrwxrwx   1 root                 root                    16 Feb 10 07:19 vcon
   sole.conf -> default/keyboard
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:21 vim
   lrwxrwxrwx   1 root                 root                    23 Feb 26  2024 vtrg
   b -> /etc/alternatives/vtrgb
   drwxr-xr-x   5 root                 root                  4096 Feb 10 07:27 vulk
   an
   drwxr-xr-x   2 root                 root                  4096 Feb 18 20:18 w3m
   -rw-r--r--   1 root                 root                  4942 Jun 19  2024 wget
   rc
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:29 wpa_
   supplicant
   drwxr-xr-x  12 root                 root                  4096 Feb 10 07:31 X11
   -rw-r--r--   1 root                 root                   681 Apr  8  2024 xatt
   r.conf
   drwxr-xr-x   6 root                 root                  4096 Feb 10 07:28 xdg
   drwxr-xr-x   2 root                 root                  4096 Feb 10 07:31 xml
   -rw-r--r--   1 root                 root                   460 Jan 20  2023 zsh_
   command_not_found
   praditadf@praditadf-VirtualBox:/etc$ cat passwd
   root:x:0:0:root:/root:/bin/bash
   daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
   bin:x:2:2:bin:/bin:/usr/sbin/nologin
   sys:x:3:3:sys:/dev:/usr/sbin/nologin
   sync:x:4:65534:sync:/bin:/bin/sync
   games:x:5:60:games:/usr/games:/usr/sbin/nologin
   man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
   lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
   mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
   news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
   uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
   proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
   www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
   backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
   list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
   irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
   _apt:x:42:65534::/nonexistent:/usr/sbin/nologin
   nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
   systemd-network:x:998:998:systemd Network Management:/:/usr/sbin/nologin
   systemd-timesync:x:996:996:systemd Time Synchronization:/:/usr/sbin/nologin
   dhcpcd:x:100:65534:DHCP Client Daemon,,,:/usr/lib/dhcpcd:/bin/false
   messagebus:x:101:101::/nonexistent:/usr/sbin/nologin
   syslog:x:102:102::/nonexistent:/usr/sbin/nologin
   systemd-resolve:x:991:991:systemd Resolver:/:/usr/sbin/nologin
   uuidd:x:103:103::/run/uuidd:/usr/sbin/nologin
   usbmux:x:104:46:usbmux daemon,,,:/var/lib/usbmux:/usr/sbin/nologin
   tss:x:105:105:TPM software stack,,,:/var/lib/tpm:/bin/false
   systemd-oom:x:990:990:systemd Userspace OOM Killer:/:/usr/sbin/nologin
   kernoops:x:106:65534:Kernel Oops Tracking Daemon,,,:/:/usr/sbin/nologin
   whoopsie:x:107:109::/nonexistent:/bin/false
   dnsmasq:x:999:65534:dnsmasq:/var/lib/misc:/usr/sbin/nologin
   avahi:x:108:111:Avahi mDNS daemon,,,:/run/avahi-daemon:/usr/sbin/nologin
   tcpdump:x:109:112::/nonexistent:/usr/sbin/nologin
   sssd:x:110:113:SSSD system user,,,:/var/lib/sss:/usr/sbin/nologin
   speech-dispatcher:x:111:29:Speech Dispatcher,,,:/run/speech-dispatcher:/bin/false
   cups-pk-helper:x:112:114:user for cups-pk-helper service,,,:/nonexistent:/usr/sbin/nologin
   fwupd-refresh:x:989:989:Firmware update daemon:/var/lib/fwupd:/usr/sbin/nologin
   saned:x:113:116::/var/lib/saned:/usr/sbin/nologin
   geoclue:x:114:117::/var/lib/geoclue:/usr/sbin/nologin
   cups-browsed:x:115:114::/nonexistent:/usr/sbin/nologin
   hplip:x:116:7:HPLIP system user,,,:/run/hplip:/bin/false
   gnome-remote-desktop:x:988:988:GNOME Remote Desktop:/var/lib/gnome-remote-desktop:/usr/sbin/nologin
   polkitd:x:987:987:User for polkitd:/:/usr/sbin/nologin
   rtkit:x:117:119:RealtimeKit,,,:/proc:/usr/sbin/nologin
   colord:x:118:120:colord colour management daemon,,,:/var/lib/colord:/usr/sbin/nologin
   gnome-initial-setup:x:119:65534::/run/gnome-initial-setup/:/bin/false
   gdm:x:120:121:Gnome Display Manager:/var/lib/gdm3:/bin/false
   nm-openvpn:x:121:122:NetworkManager OpenVPN,,,:/var/lib/openvpn/chroot:/usr/sbin/nologin
   praditadf:x:1000:1000:praditadf:/home/praditadf:/bin/bash
   praditadf@praditadf-VirtualBox:/etc$ cd -
   /
   praditadf@praditadf-VirtualBox:/$ pwd
   /
   ```

2. Lanjutkan penelusuran pohon pada sistem file menggunakan cd, ls, pwd dan cat. Telusuri direktory /bin, /usr/bin, /sbin, /tmp dan /boot.

   ```
   praditadf@praditadf-VirtualBox:~$ cd /bin
   praditadf@praditadf-VirtualBox:/bin$ pwd
   /bin
   praditadf@praditadf-VirtualBox:/bin$ ls -al | head -10
   total 199852
   drwxr-xr-x  2 root root       65536 Mar  4 12:58 .
   drwxr-xr-x 12 root root        4096 Feb 10 07:19 ..
   -rwxr-xr-x  1 root root       55744 Jun 22  2025 [
   -rwxr-xr-x  1 root root       14640 Mar 31  2024 411toppm
   -rwxr-xr-x  1 root root       18744 Aug 15  2025 aa-enabled
   -rwxr-xr-x  1 root root       18744 Aug 15  2025 aa-exec
   -rwxr-xr-x  1 root root       18736 Aug 15  2025 aa-features-abi
   -rwxr-xr-x  1 root root       22912 Apr  7  2024 aconnect
   -rwxr-xr-x  1 root root        1622 Feb  7 00:52 acpidbg
   praditadf@praditadf-VirtualBox:/bin$ cat aconnect
   @@@@���   Q�Q�@@@���J�Z�Z���K�[�8880hhhDDS�td8880P�tdXEXEXEttQ�tdR�td�J�Z�Zpp/lib64/ld-linux-x86-64.so.2 GNU���GNU�[��q
   ```

   ```
   praditadf@praditadf-VirtualBox:~$ cd /usr/bin
   praditadf@praditadf-VirtualBox:/usr/bin$ pwd
   /usr/bin
   praditadf@praditadf-VirtualBox:/usr/bin$ ls -l | head -5
   total 199784
   -rwxr-xr-x 1 root root       55744 Jun 22  2025 [
   -rwxr-xr-x 1 root root       14640 Mar 31  2024 411toppm
   -rwxr-xr-x 1 root root       18744 Aug 15  2025 aa-enabled
   -rwxr-xr-x 1 root root       18744 Aug 15  2025 aa-exec
   ```

   ```
   praditadf@praditadf-VirtualBox:/usr/bin$ cd /sbin
   praditadf@praditadf-VirtualBox:/sbin$ pwd
   /sbin
   praditadf@praditadf-VirtualBox:/sbin$ ls -l | head -10
   total 38768
   -rwxr-xr-x 1 root root     39680 Aug 15  2025 aa-load
   -rwxr-xr-x 1 root root      3225 Aug 15  2025 aa-remove-unknown
   -rwxr-xr-x 1 root root     40000 Aug 15  2025 aa-status
   -rwxr-xr-x 1 root root       137 Apr 12  2024 aa-teardown
   -rwxr-xr-x 1 root root     14904 Apr  8  2024 accessdb
   -rwxr-xr-x 1 root root      3075 Jan  6 05:01 addgnupghome
   lrwxrwxrwx 1 root root         7 Jul  6  2023 addgroup -> adduser
   -rwxr-xr-x 1 root root      1053 Mar 31  2024 add-shell
   -rwxr-xr-x 1 root root     55191 Jul  6  2023 adduser
   praditadf@praditadf-VirtualBox:/sbin$ cat adduser
   #! /usr/bin/perl

   # Copyright (C) 2000-2004 Roland Bauerschmidt <rb@debian.org>
   #               2005-2023 Marc Haber <mh+debian-packages@zugschlus.de>
   #               2022 Benjamin Drung <benjamin.drung@canonical.com>
   #               2023 Guillem Jover <guillem@debian.org>
   #               2021-2022 Jason Franklin <jason@oneway.dev>
   #               2022 Matt Barry <matt@hazelmollusk.org>
   #               2016-2017 Afif Elghraoui <afif@debian.org>
   #               2016 Dr. Helge Kreutzmann <debian@helgefjell.de>
   #               2005-2009 Joerg Hoh <joerg@joerghoh.de>
   #               2006-2011 Stephen Gran <sgran@debian.org>
   ```

   ```
   praditadf@praditadf-VirtualBox:/sbin$ cd /tmp
   praditadf@praditadf-VirtualBox:/tmp$ pwd
   /tmp
   praditadf@praditadf-VirtualBox:/tmp$ ls -l | head -5
   total 100
   -rw-rw-r-- 1 praditadf praditadf 32965 Mar 10 20:23 exthost-e6487f.cpuprofile
   drwx------ 2 praditadf praditadf  4096 Mar 10 19:42 mcp-AloueR
   drwx------ 2 praditadf praditadf  4096 Mar 10 19:31 mcp-lqv6i4
   drwx------ 2 praditadf praditadf  4096 Mar 10 19:40 mcp-VSCpi0
   praditadf@praditadf-VirtualBox:/tmp$ cat mcp-VSCpi0 | head -5
   cat: mcp-VSCpi0: Is a directory
   praditadf@praditadf-VirtualBox:/tmp$ 
   ```

   ```
   
   praditadf@praditadf-VirtualBox:/tmp$ cd /boot
   praditadf@praditadf-VirtualBox:/boot$ pwd
   /boot
   praditadf@praditadf-VirtualBox:/boot$ ls -l | head -5
   total 103284
   -rw-r--r-- 1 root root   302820 Jan 15 20:44 config-6.17.0-14-generic
   drwxr-xr-x 5 root root     4096 Feb 14 18:30 grub
   lrwxrwxrwx 1 root root       28 Feb 14 18:27 initrd.img -> initrd.img-6.17.0-14-generic
   -rw-r--r-- 1 root root 77655313 Mar  4 11:21 initrd.img-6.17.0-14-generic
   ```

3. Telusuri direktory /dev. Identifikasi perangkat yang tersedia. Identifikasi tty (termninal) Anda (ketik who am i); siapa pemilih tty Anda (gunakan ls –l).

```
   praditadf@praditadf-VirtualBox:~$ cd /dev
   praditadf@praditadf-VirtualBox:/dev$ pwd
   /dev
   praditadf@praditadf-VirtualBox:/dev$ ls -l | head -15
   total 0
   crw-r--r--   1 root      root     10, 235 Mar 10 17:58 autofs
   drwxr-xr-x   2 root      root         420 Mar 10 17:59 block
   drwxr-xr-x   2 root      root          80 Mar 10 17:58 bsg
   crw-------   1 root      root     10, 234 Mar 10 17:58 btrfs-control
   drwxr-xr-x   3 root      root          60 Mar 10 17:58 bus
   lrwxrwxrwx   1 root      root           3 Mar 10 17:58 cdrom -> sr0
   drwxr-xr-x   2 root      root        3720 Mar 10 17:58 char
   crw-------   1 root      root      5,   1 Mar 10 17:58 console
   lrwxrwxrwx   1 root      root          11 Mar 10 17:58 core -> /proc/kcore
   drwxr-xr-x   4 root      root          80 Mar 10 17:58 cpu
   crw-------   1 root      root     10, 260 Mar 10 17:58 cpu_dma_latency
   crw-------   1 root      root     10, 203 Mar 10 17:58 cuse
   drwxr-xr-x  10 root      root         200 Mar 10 17:58 disk
   drwxr-xr-x   2 root      root          60 Mar 10 17:58 dma_heap
   praditadf@praditadf-VirtualBox:/dev$ who am i
   praditadf@praditadf-VirtualBox:/dev$ ls -l /dev/pts/0
   crw--w---- 1 praditadf tty 136, 0 Mar 10 20:42 /dev/pts/0
```

1. Telusuri derectory /proc. Tampilkan isi file interrupts, devices, cpuinfo, meminfo dan uptime menggunakan perintah cat. Dapatkah Anda melihat mengapa directory /proc disebut pseudo -filesystem yang memungkinkan akses ke struktur data kernel ?

   Direkktory /proc disebut pseudo -filesystem

   ```
   praditadf@praditadf-VirtualBox:~$ cd /proc
   praditadf@praditadf-VirtualBox:/proc$ cat interrupts
            CPU0       CPU1       
   0:        178          0  IO-APIC   2-edge      timer
   1:          0      17347  IO-APIC   1-edge      i8042
   8:          0          0  IO-APIC   8-edge      rtc0
   9:          0          0  IO-APIC   9-fasteoi   acpi
   12:          0      33210  IO-APIC  12-edge      i8042
   14:      10489          0  IO-APIC  14-edge      ata_piix
   15:          0          0  IO-APIC  15-edge      ata_piix
   18:          0          9  IO-APIC  18-fasteoi   vmwgfx
   19:      34534          0  IO-APIC  19-fasteoi   ehci_hcd:usb2, enp0s3
   20:     110462          0  IO-APIC  20-fasteoi   vboxguest
   21:          0      75970  IO-APIC  21-fasteoi   ahci[0000:00:0d.0], snd_intel8x0
   22:         27          0  IO-APIC  22-fasteoi   ohci_hcd:usb1
   NMI:          0          0   Non-maskable interrupts
   LOC:    3926466    1405470   Local timer interrupts
   SPU:          0          0   Spurious interrupts
   PMI:          0          0   Performance monitoring interrupts
   IWI:         65         68   IRQ work interrupts
   RTR:          0          0   APIC ICR read retries
   RES:      50091      60940   Rescheduling interrupts
   CAL:    1220382    1404987   Function call interrupts
   TLB:     170971     237976   TLB shootdowns
   TRM:          0          0   Thermal event interrupts
   THR:          0          0   Threshold APIC interrupts
   DFR:          0          0   Deferred Error APIC interrupts
   MCE:          0          0   Machine check exceptions
   MCP:         32         32   Machine check polls
   ERR:          0
   MIS:        329
   PIN:          0          0   Posted-interrupt notification event
   NPI:          0          0   Nested posted-interrupt event
   PIW:          0          0   Posted-interrupt wakeup event
   praditadf@praditadf-VirtualBox:/proc$ cat devices
   Character devices:
   1 mem
   4 /dev/vc/0
   4 tty
   4 ttyS
   5 /dev/tty
   5 /dev/console
   5 /dev/ptmx
   5 ttyprintk
   6 lp
   7 vcs
   10 misc
   13 input
   21 sg
   29 fb
   89 i2c
   99 ppdev
   108 ppp
   116 alsa
   128 ptm
   136 pts
   180 usb
   189 usb_device
   202 cpu/msr
   204 ttyMAX
   226 drm
   240 hidraw
   241 ttyDBC
   242 bsg
   243 watchdog
   244 remoteproc
   245 ptp
   246 pps
   247 rtc
   248 dma_heap
   249 dax
   250 dimmctl
   251 ndctl
   252 tpm
   253 pwm
   254 gpiochip
   261 accel

   Block devices:
   7 loop
   8 sd
   9 md
   11 sr
   65 sd
   66 sd
   67 sd
   68 sd
   69 sd
   70 sd
   71 sd
   128 sd
   129 sd
   130 sd
   131 sd
   132 sd
   133 sd
   134 sd
   135 sd
   252 device-mapper
   253 virtblk
   254 mdp
   259 blkext
   praditadf@praditadf-VirtualBox:/proc$ cat cpuinfo
   processor : 0
   vendor_id : GenuineIntel
   cpu family : 6
   model  : 186
   model name : 13th Gen Intel(R) Core(TM) i5-13420H
   stepping : 2
   microcode : 0xffffffff
   cpu MHz  : 2611.198
   cache size : 12288 KB
   physical id : 0
   siblings : 2
   core id  : 0
   cpu cores : 2
   apicid  : 0
   initial apicid : 0
   fpu  : yes
   fpu_exception : yes
   cpuid level : 22
   wp  : yes
   flags  : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ibrs_enhanced fsgsbase bmi1 avx2 bmi2 invpcid rdseed adx clflushopt sha_ni arat md_clear flush_l1d arch_capabilities
   bugs  : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi spectre_v2_user its
   bogomips : 5222.39
   clflush size : 64
   cache_alignment : 64
   address sizes : 39 bits physical, 48 bits virtual
   power management:

   processor : 1
   vendor_id : GenuineIntel
   cpu family : 6
   model  : 186
   model name : 13th Gen Intel(R) Core(TM) i5-13420H
   stepping : 2
   microcode : 0xffffffff
   cpu MHz  : 2611.198
   cache size : 12288 KB
   physical id : 0
   siblings : 2
   core id  : 1
   cpu cores : 2
   apicid  : 1
   initial apicid : 1
   fpu  : yes
   fpu_exception : yes
   cpuid level : 22
   wp  : yes
   flags  : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ibrs_enhanced fsgsbase bmi1 avx2 bmi2 invpcid rdseed adx clflushopt sha_ni arat md_clear flush_l1d arch_capabilities
   bugs  : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi spectre_v2_user its
   bogomips : 5222.39
   clflush size : 64
   cache_alignment : 64
   address sizes : 39 bits physical, 48 bits virtual
   power management:

   praditadf@praditadf-VirtualBox:/proc$ cat meminfo
   MemTotal:        4008744 kB
   MemFree:          474712 kB
   MemAvailable:    1594864 kB
   Buffers:           13680 kB
   Cached:          1360092 kB
   SwapCached:        68496 kB
   Active:          1417684 kB
   Inactive:        1722296 kB
   Active(anon):    1067480 kB
   Inactive(anon):   777040 kB
   Active(file):     350204 kB
   Inactive(file):   945256 kB
   Unevictable:          32 kB
   Mlocked:              32 kB
   SwapTotal:       2097148 kB
   SwapFree:        1462724 kB
   Zswap:                 0 kB
   Zswapped:              0 kB
   Dirty:                 8 kB
   Writeback:             0 kB
   AnonPages:       1741588 kB
   Mapped:           622940 kB
   Shmem:            221476 kB
   KReclaimable:      54752 kB
   Slab:             190664 kB
   SReclaimable:      54752 kB
   SUnreclaim:       135912 kB
   KernelStack:       14688 kB
   PageTables:        39316 kB
   SecPageTables:         0 kB
   NFS_Unstable:          0 kB
   Bounce:                0 kB
   WritebackTmp:          0 kB
   CommitLimit:     4101520 kB
   Committed_AS:   12293880 kB
   VmallocTotal:   34359738367 kB
   VmallocUsed:       34036 kB
   VmallocChunk:          0 kB
   Percpu:             1512 kB
   HardwareCorrupted:     0 kB
   AnonHugePages:         0 kB
   ShmemHugePages:        0 kB
   ShmemPmdMapped:        0 kB
   FileHugePages:      2048 kB
   FilePmdMapped:         0 kB
   CmaTotal:              0 kB
   CmaFree:               0 kB
   Unaccepted:            0 kB
   Balloon:               0 kB
   HugePages_Total:       0
   HugePages_Free:        0
   HugePages_Rsvd:        0
   HugePages_Surp:        0
   Hugepagesize:       2048 kB
   Hugetlb:               0 kB
   DirectMap4k:      122816 kB
   DirectMap2M:     4071424 kB
   praditadf@praditadf-VirtualBox:/proc$ cat uptime
   10620.09 16706.71
   ```

2. Ubahlah direktory home ke user lain secara langsung menggunakan cd ~username.

   ```
   praditadf@praditadf-VirtualBox:~$ cd  ~praditadf
   praditadf@praditadf-VirtualBox:~$ 
   ```

3. Ubah kembali ke direktory home Anda.

   ```
   praditadf@praditadf-VirtualBox:~$ cd /home
   praditadf@praditadf-VirtualBox:/home$ 
   ```

4. Buat subdirektory work dan play.

   ```
   praditadf@praditadf-VirtualBox:~$ mkdir work play
   drwxrwxr-x 2 praditadf praditadf   4096 Mar 10 21:14 work
   drwxrwxr-x 2 praditadf praditadf   4096 Mar 10 21:14 play
   ```

5. Hapus subdirektory work.

   ```
   praditadf@praditadf-VirtualBox:~$ rmdir work
   ```

6. Copy file /etc/passwd ke direktory home Anda.

    ```
    praditadf@praditadf-VirtualBox:~$ cp /etc/passwd ~
    raditadf@praditadf-VirtualBox:~$ ls -l passwd
    -rw-r--r-- 1 praditadf praditadf 2873 Mar 10 21:11 passwd

   ```

10. Pindahkan ke subirectory play.

   ```

   praditadf@praditadf-VirtualBox:~$ mv ~/passwd ~/play

   ```

11. Ubahlah ke subdirektory play dan buat symbolic link dengan nama terminal yang menunjuk ke perangkat tty. Apa yang terjadi jika melakukan hard link ke perangkat tty ?

```

   praditadf@praditadf-VirtualBox:~$ cd ~/play
   praditadf@praditadf-VirtualBox:~/play$ ln -s /dev/pts/0 terminal

```

12. Buatlah file bernama hello.txt yang berisi kata ”hello word”. Dapatkah Anda  gunakan ”cp” menggunakan ”terminal” sebagai file asal untuk menghasilkan efek yang sama ?

```

praditadf@praditadf-VirtualBox:~/play$ echo "hello world" > hello.txt

```

13. Copy hello.txt ke terminal. Apa yang terjadi ?

Sistem akan mencetak hello world

```

praditadf@praditadf-VirtualBox:~/play$ cp hello.txt terminal
hello world

```

14. Masih direktory home, copy keseluruhan direktory play ke direktory bernama work menggunakan symbolic link.

```

praditadf@praditadf-VirtualBox:~/play$ cd ~
praditadf@praditadf-VirtualBox:~$ ln -s play work

```

15. Hapus direktory work dan isinya dengan satu perintah

```

praditadf@praditadf-VirtualBox:~$ rm -rf work

```

## LAPORAN RESMI

1. Analisa hasil percobaan yang Anda lakukan.
   a. Analisa setiap hasil tampilannya.
   b. Pada Percobaan 1 point 3 buatlah pohon dari struktur file dan direktori
   
   .
   ├── A
   │   ├── D
   │   │   └── A
   │   └── 
   ├── B
   │   └── F
   ├── C

   c. Bila terdapat pesan error, jelaskan penyebabnya.
2. Kerjakan latihan diatas dan analisa hasil tampilannya.
3. Berikan kesimpulan dari praktikum ini.


