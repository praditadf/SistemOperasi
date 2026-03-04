## TUGAS PENDAHULUAN:

Jawablah pertanyaan-pertanyaan di bawah ini :
1. Apa yang dimaksud perintah-perintah direktory : pwd, cd, mkdir, rmdir.
2. Apa yang dimaksud perintah-perintah manipulasi file : cp, mv, dan rm (sertakan format yang digunakan)
3. Jelaskan perbedaan Symbolic link menggunakan hard link (direct) dan soft link (indirect)
4. Tuliskan maksud perintah-perintah : file, find, which, locate dan grep.

## PERCOBAAN:
1. Login sebagai user.
2. Bukalah Console Terminal dan lakukan percobaan-percobaan di bawah ini.
Perhatikan hasilnya.
3. Selesaikan soal-soal latihan

### Percobaan 1 : Direktory
1. Melihat direktori HOME

   $ pwd
   
   $ echo

   $HOME
2. Melihat direktori aktual dan parent direktori
   $ pwd

   $ cd .

   $ pwd

   $ cd ..

   $ pwd

   $ cd
3. Membuat satu direktori, lebih dari satu direktori atau sub direktori
   $ pwd

   $ mkdir A B C A/D A/E B/F A/D/A

   $ ls -l

   $ ls -l A

   $ ls -l A/D
4. Menghap us satu atau lebih direktori hanya dapat dilakukan pada direktori kosong dan hanya dapat dihapus oleh pemiliknya kecuali bila diberikan ijin aksesnya

   $ rmdir B (Terdapat pesan error, mengapa ?)

   $ ls -l B

   $ rmdir B/F B

   $ ls -l B (Terdapat pesan error, me ngapa ?)
5. Navigasi direktori dengan instruksi cd untuk pindah dari satu direktori ke direktori lain.

   $ pwd

   $ ls -l

   $ cd A

   $ pwd

   $ cd ..

   $ pwd

   $ cd /home/<user>/C

   $ pwd

   $ cd /<user/C (Terdapat pesan error, mengapa ?)

   $ pwd
   
### Percobaan 2 : Manipulasi file
1. Perintah cp untuk mengkopi file atau seluruh direktori

   $ cat > contoh

  Membuat sebuah file

  [Ctrl-d]

  $ cp contoh contoh1

  $ ls -l

  $ cp contoh A
  
  $ ls –l A

$ cp contoh contoh1 A/D

$ ls –l A/D

2. Perintah mv untuk memindah file

$ mv contoh contoh2

$ ls -l

$ mv contoh1 contoh2 A/D

$ ls –l A/D

$ mv contoh contoh1 C

$ ls –l C

3. Perintah rm untuk menghapus file

$ rm contoh2

$ ls -l

$ rm –i contoh

$ rm –rf A C

$ ls -l
