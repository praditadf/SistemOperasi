# Bash Shell dan Shell Basic

## Praktikum 6.1 — Mengenali Bash dan Menyiapkan Workspace

### 1. Lihat shell login dan shell aktif saat ini

```
praditadf@praditadf-VirtualBox:~$ echo "Shell Login : $SHELL"
Shell Login : /bin/bash
praditadf@praditadf-VirtualBox:~$ echo "Shell Aktif : $0"
Shell Aktif : bash
praditadf@praditadf-VirtualBox:~$ bash --version | head -n 1
GNU bash, version 5.2.21(1)-release (x86_64-pc-linux-gnu)
```

### 2. Lihat proses shell yang sedang berjalan

```
praditadf@praditadf-VirtualBox:~$ echo $$
6574
praditadf@praditadf-VirtualBox:~$ ps -p $$ -o pid,ppid,args=
    PID    PPID 
   6574    6561 bash
```

### 3. Buat workspace praktikum

```
praditadf@praditadf-VirtualBox:~$ mkdir -p ~/praktikum-os/week07-bash/{bin,backup,logs,sampel,ruang-nama}
praditadf@praditadf-VirtualBox:~$ cd ~/praktikum-os/week07-bash
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ pwd
/home/praditadf/praktikum-os/week07-bash
```

### 4. Buat beberapa file contoh yang akan dipakai pada praktikum berikutnya

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ touch sample-app.conf
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ touch logs/app-01.log logs/app-02.log logs/app-03.log
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ touch sampel/catatan-a.txt sampel/catatan-b.txt
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ touch sampel/backup-01.tar sampel/backup-02.tar
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ touch sampel/laporan-harian.log sampel/laporan-mingguan.log sampel/laporan-bulanan.log
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ touch "ruang-nama/laporan server april.txt"
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ touch "ruang-nama/backup [mingguan] server.conf"
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ ls -R
.:
backup  bin  logs  ruang-nama  sampel  sample-app.conf

./backup:

./bin:

./logs:
app-01.log  app-02.log  app-03.log

./ruang-nama:
'backup [mingguan] server.conf'  'laporan server april.txt'

./sampel:
backup-01.tar  backup-02.tar  catatan-a.txt  catatan-b.txt  laporan-bulanan.log  laporan-harian.log  laporan-mingguan.log
```

## Praktikum 6.2 — Membuat Ringkasan Sesi Terminal

### 1. Masuk ke workspace praktikum

```
praditadf@praditadf-VirtualBox:~$ cd ~/praktikum-os/week07-bash
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ 
```

### 2. Simpan informasi sesi terminal ke file laporan

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ {
> echo "=== RINGKASAN SESI BASH ==="
> date
> echo "User       : $(whoami)"
> echo "Hostname   : $(hostname)"
> echo "Shell login: $SHELL"
> echo "Shell aktif: $0"
> echo "PID Shell  : $$"
> echo "Direktori  : $(pwd)"
> } | tee session-info.txt
=== RINGKASAN SESI BASH ===
Wed Apr  8 12:30:42 PM WIB 2026
User       : praditadf
Hostname   : praditadf-VirtualBox
Shell login: /bin/bash
Shell aktif: bash
PID Shell  : 6574
Direktori  : /home/praditadf/praktikum-os/week07-bash
```

### 3. Verifikasi isi file laporan

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ cat session-info.txt
=== RINGKASAN SESI BASH ===
Wed Apr  8 12:30:42 PM WIB 2026
User       : praditadf
Hostname   : praditadf-VirtualBox
Shell login: /bin/bash
Shell aktif: bash
PID Shell  : 6574
Direktori  : /home/praditadf/praktikum-os/week07-bash
```

## Praktikum 6.3 — Menambahkan Konfigurasi Aman pada .bashrc

### 1. Lihat file konfigurasi Bash pada home directory

```
praditadf@praditadf-VirtualBox:~$ ls -la ~ | grep -E 'bashrc|bash_profile|profile'
-rw-r--r--  1 praditadf praditadf     3771 Mar 31  2024 .bashrc
-rw-r--r--  1 praditadf praditadf      807 Mar 31  2024 .profile
```

### 2. Buat backup .bashrc

```
cp ~/.bashrc ~/.bashrc.bak-praktikum
```

### 3. Tambahkan blok konfigurasi praktikum

```
praditadf@praditadf-VirtualBox:~$ cat <<'EOF' >> ~/.bashrc
> 
> # --- Praktikum Bash Shell ---
> export PRAKTIKUM_BASH_DIR="$HOME/praktikum-os/week04-bash"
> export EDITOR=nano
> # --- End Praktikum Bash Shell ---
> 
> EOF
```

### 4. Terapkan konfigurasi tanpa logout

```
praditadf@praditadf-VirtualBox:~$ source ~/.bashrc
praditadf@praditadf-VirtualBox:~$ echo "$PRAKTIKUM_BASH_DIR"
/home/praditadf/praktikum-os/week04-bash
praditadf@praditadf-VirtualBox:~$ echo "$EDITOR"
nano
```

## Praktikum 6.4 — Menyiapkan .bash_profile untuk Shell Login

### 1. Backup .bash_profile jika sudah ada

```
[ -f ~/.bash_profile ] && cp ~/.bash_profile ~/.bach_profile.bak-praktikum
```

### 2. Tambahkan konfigurasi login shell

```
praditadf@praditadf-VirtualBox:~$ cat <<'EOF' >> ~/.bash_profile
> 
> # --- Praktikum Bash Login Shell ---
> if [ -f ~/.bashrc ]; then
> . ~/.bashrc
> fi
> 
> echo "Login Bash pada $(date '+%F %T')" >> "$HOME/praktikum-os/week07-bash/login-audit.log"
> # --- End Praktikum Bash Login Shell ---
> 
> EOF
```

### 3. Uji dengan membuka login shell baru

```
praditadf@praditadf-VirtualBox:~$ bash -l
praditadf@praditadf-VirtualBox:~$ tail -n 3 ~/praktikum-os/week07-bash/login-audit.log
Login Bash pada 2026-04-08 12:46:54
praditadf@praditadf-VirtualBox:~$ exit
logout
```

## Praktikum 6.5 — Membedakan Variabel Shell dan Environment Variable

### 1. Buat variabel lokal

```
praditadf@praditadf-VirtualBox:~$ KELAS_OS="Sistem Operasi A"
praditadf@praditadf-VirtualBox:~$ echo "$KELAS_OS"
Sistem Operasi A
```

### 2. Buka subshell dan cek apakah variabel masih ada

```
praditadf@praditadf-VirtualBox:~$ bash
praditadf@praditadf-VirtualBox:~$ echo "KELAS_OS"
KELAS_OS
praditadf@praditadf-VirtualBox:~$ exit
exit
```

### 3. Sekarang ubah menjadi environment variable

```
praditadf@praditadf-VirtualBox:~$ export KELAS_OS="Sistem Operasi A"
praditadf@praditadf-VirtualBox:~$ bash
praditadf@praditadf-VirtualBox:~$ echo "KELAS_OS"
KELAS_OS
praditadf@praditadf-VirtualBox:~$ exit
exit
```

### 4. Lihat isi PATH dan lokasi beberapa perintah

```
praditadf@praditadf-VirtualBox:~$ echo "$PATH"
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
praditadf@praditadf-VirtualBox:~$ which bash
/usr/bin/bash
praditadf@praditadf-VirtualBox:~$ type ls
ls is aliased to `ls --color=auto'
```

## Praktikum 6.6 — Menambahkan Direktori Script Pribadi ke PATH

### 1. Pastikan direktori bin praktikum tersedia

```
mkdir -p ~/praktikum-os/week07-bash/bin
```

### 2. Tambahkan direktori tersebut ke PATH melalui .bashrc

```
praditadf@praditadf-VirtualBox:~$ cat <<'EOF' >> ~/.bashrc
> 
> # --- Praktikum PATH ---
> export PATH="$HOME/praktikum-os/week07-bash/bin:$PATH"
> # --- End Praktikum PATH ---
> 
> EOF
praditadf@praditadf-VirtualBox:~$ source ~/.bashrc
praditadf@praditadf-VirtualBox:~$ echo "$PATH"
/home/praditadf/praktikum-os/week07-bash/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
```

### 3. Buat script ringkasan sistem

```
praditadf@praditadf-VirtualBox:~$ cat <<'EOF' > ~/praktikum-os/week07-bash/bin/ringkas-sistem
> #!/usr/bin/env bash
> echo "Hostname  : $(hostname)"
> echo "User      : $(whoami)"
> echo "Uptime    : $(uptime -p)"
> echo "Disk /    :"
> df -h /
> EOF
praditadf@praditadf-VirtualBox:~$ chmod +x ~/praktikum-os/week07-bash/bin/ringkas-sistem
```

### 4. Jalankan script dari direktori yang berbeda

```
praditadf@praditadf-VirtualBox:~$ cd A
praditadf@praditadf-VirtualBox:~/A$ ringkas-sistem
Hostname  : praditadf-VirtualBox
User      : praditadf
Uptime    : up 2 hours, 11 minutes
Disk /    :
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        25G   16G  8.2G  65% /
```

## Praktikum 6.7 — Membuat Alias Produktivitas Dasar

### 1. Tambahkan alias ke .bashrc

```
praditadf@praditadf-VirtualBox:~$ cat <<'EOF' >> ~/.bashrc
> 
> # --- Praktikum Alias ---
> alias ll='ls -lah --color=auto'
> alias hist10='history | tail -n 10'
> alias cdbashlab='cd $HOME/praktikum-os/week07-bash'
> # --- End Praktikum Alias ---
> 
> EOF
praditadf@praditadf-VirtualBox:~$ source ~/.bashrc
```

### 2. Uji alias

* ll

```
praditadf@praditadf-VirtualBox:~$ ll
total 16M
drwxr-x--- 27 praditadf praditadf 4.0K Apr  8 12:46  .
drwxr-xr-x  3 root      root      4.0K Feb 14 18:29  ..
-rw-rw-r--  1 praditadf praditadf  16M Mar 11 11:12 '2026-03-11 11-12-11.mp4'
drwxrwxr-x  4 praditadf praditadf 4.0K Mar 10 21:36  A
-rw-r--r--  1 praditadf praditadf 1.8K Feb 24 18:16  aaaaaaa
-rw-rw-r--  1 praditadf praditadf 1004 Mar 11 19:58  app.log
drwxrwxr-x  3 praditadf praditadf 4.0K Mar 10 21:36  B
-rw-rw-r--  1 praditadf praditadf 3.2K Mar  4 10:46  backup-error.log
-rwxrwxr-x  1 praditadf praditadf  151 Mar  4 10:45  backup.sh
-rw-rw-r--  1 praditadf praditadf  951 Mar  4 10:46  backup-succes.log
-rw-rw-r--  1 praditadf praditadf    0 Mar  3 18:51  backup-success.log
-rw-rw-r--  1 praditadf praditadf   45 Mar  4 10:46  backup.tar.gz
-rw-------  1 praditadf praditadf  23K Apr  8 12:50  .bash_history
-rw-r--r--  1 praditadf praditadf  220 Mar 31  2024  .bash_logout
-rw-rw-r--  1 praditadf praditadf  214 Apr  8 12:46  .bash_profile
-rw-r--r--  1 praditadf praditadf 4.2K Apr  8 13:04  .bashrc
-rw-r--r--  1 praditadf praditadf 3.7K Apr  8 12:35  .bashrc.bak-praktikum
lrwxrwxrwx  1 praditadf praditadf    1 Mar 10 20:03  bye.txt -> z
```

<details>
<summary><b>Read More</b></summary>
<br>

```
drwxrwxr-x  2 praditadf praditadf 4.0K Mar 10 21:36  C
drwx------ 15 praditadf praditadf 4.0K Apr  7 20:08  .cache
drwxr-xr-x 21 praditadf praditadf 4.0K Apr  7 20:08  .config
-rw-rw-r--  1 praditadf praditadf   44 Feb 24 18:20  config.txt
drwx------  3 praditadf praditadf 4.0K Mar  4 11:48  .copilot
drwxr-xr-x  2 praditadf praditadf 4.0K Feb 14 18:36  Desktop
drwxr-xr-x  2 praditadf praditadf 4.0K Feb 14 18:36  Documents
drwxrwxr-x  3 praditadf praditadf 4.0K Mar  4 11:47  .dotnet
drwxr-xr-x  2 praditadf praditadf 4.0K Mar 11 10:55  Downloads
-rw-rw-r--  1 praditadf praditadf    0 Mar  3 17:16  error.log
-rw-rw-r--  1 praditadf praditadf  63K Mar 11 20:11  error.txt
-rw-rw-r--  1 praditadf praditadf   60 Mar  4 12:24  .gitconfig
drwxrwxr-x  3 praditadf praditadf 4.0K Mar  4 11:55  Github
drwx------  2 praditadf praditadf 4.0K Apr  8 10:52  .gnupg
-rw-rw-r--  3 praditadf praditadf   17 Mar 10 20:02  halo.txt
-rw-rw-r--  1 praditadf praditadf 199K Mar 11 20:11  hasil-pencarian.txt
-rw-rw-r--  1 praditadf praditadf  307 Mar 11 19:32  IvfhB
-rw-rw-r--  1 praditadf praditadf  307 Mar 11 19:40  IvfhB.1
-rw-rw-r--  1 praditadf praditadf  307 Mar 11 19:41  IvfhB.2
-rw-rw-r--  1 praditadf praditadf  307 Mar 11 19:44  IvfhB.3
-rw-rw-r--  1 praditadf praditadf  307 Mar 11 19:56  IvfhB.4
-rw-rw-r--  1 praditadf praditadf  799 Mar  3 17:16  large-logs.txt
-rw-------  1 praditadf praditadf   20 Feb 25 12:29  .lesshst
drwx------  4 praditadf praditadf 4.0K Feb 14 18:36  .local
-rw-rw-r--  1 praditadf praditadf 3.4K Mar  3 18:13  log.txt
-rw-rw-r--  1 praditadf praditadf  139 Mar  4 10:11  monitor.sh
drwxr-xr-x  2 praditadf praditadf 4.0K Feb 14 18:36  Music
drwxrwxr-x  2 praditadf praditadf 4.0K Mar 10 20:02  mydir
-rw-rw-r--  1 praditadf praditadf 1.4K Mar 10 20:06  myerror.txt
-rw-rw-r--  1 praditadf praditadf 109K Mar  3 18:26  path.txt
drwxr-xr-x  2 praditadf praditadf 4.0K Feb 14 18:36  Pictures
-rw-rw-r--  1 praditadf praditadf 9.8K Mar  3 17:41  ping-log.txt
drwx------  3 praditadf praditadf 4.0K Mar  4 11:46  .pki
drwxrwxr-x  2 praditadf praditadf 4.0K Mar 10 21:25  play
drwxrwxr-x  5 praditadf praditadf 4.0K Apr  8 12:17  praktikum-os
-rw-r--r--  1 praditadf praditadf  807 Mar 31  2024  .profile
drwxr-xr-x  2 praditadf praditadf 4.0K Feb 14 18:36  Public
drwx------  8 praditadf praditadf 4.0K Mar 11 11:31  snap
-rw-rw-r--  1 praditadf praditadf  411 Mar 11 20:17  sorted-users.txt
drwx------  2 praditadf praditadf 4.0K Feb 14 18:37  .ssh
-rw-r--r--  1 praditadf praditadf    0 Feb 15 07:12  .sudo_as_admin_successful
-rw-rw-r--  1 praditadf praditadf  112 Mar  3 17:48  system
drwxr-xr-x  2 praditadf praditadf 4.0K Feb 14 18:36  Templates
drwxr-xr-x  2 praditadf praditadf 4.0K Feb 14 18:36  Videos
drwxrwxr-x  4 praditadf praditadf 4.0K Mar  4 11:46  .vscode
-rw-rw-r--  1 praditadf praditadf  303 Mar 11 19:56  .wget-hsts
-rw-rw-r--  1 praditadf praditadf  381 Mar  4 11:09  wget-log
-rw-rw-r--  3 praditadf praditadf   17 Mar 10 20:02  z
```

</details>

* hist10

```
praditadf@praditadf-VirtualBox:~$ hist10
alias ll='ls -lah --color=auto'
alias hist10='history | tail -n 10'
alias cdbashlab='cd $HOME/praktikum-os/week07-bash'
# --- End Praktikum Alias ---

EOF

 1392  source ~/.bashrc
 1393  ll
 1394  hist10
```

* cdbashlab

```
praditadf@praditadf-VirtualBox:~$ cdbashlab
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ 
```

* pwd

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ pwd
/home/praditadf/praktikum-os/week07-bash
```

* type ll

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ type ll
ll is aliased to `ls -lah --color=auto'
```

## Praktikum 6.8 — Membuat Fungsi Backup Konfigurasi

### 1. Siapkan file konfigurasi contoh

```
praditadf@praditadf-VirtualBox:~$ echo "PORT=8080" > ~/praktikum-os/week07-bash/sample-app.conf
praditadf@praditadf-VirtualBox:~$ cat ~/praktikum-os/week07-bash/sample-app.conf
PORT=8080
```

### 2. Tambahkan fungsi ke .bashrc

```
praditadf@praditadf-VirtualBox:~$ cat <<'EOF' >> ~/.bashrc
> 
> # --- Praktikum Fungsi Shell ---
> backup_conf () {
> if [ $# -ne 1 ]; then
> echo " Usage : backup_conf <file>"
> return 1
> fi
> local src="$1"
> local dst="$HOME/praktikum-os/week07-bash/backup"
> if [ ! -f "$src" ]; then
> echo "File tidak ditemukan: $src"
> return 2
> fi
> mkdir -p "$dst"
> cp -- "$src" "$dst/$(basename "$src").$(date +%F-%H%M%S).bak"
> echo "Backup selesai di $dst"
> }
> # --- End Praktikum Fungsi Shell ---
> EOF
praditadf@praditadf-VirtualBox:~$ source ~/.bashrc
```

### 3. Uji fungsi

```
praditadf@praditadf-VirtualBox:~$ backup_conf ~/praktikum-os/week07-bash/sample-app.conf
Backup selesai di /home/praditadf/praktikum-os/week07-bash/backup
praditadf@praditadf-VirtualBox:~$ ls -lah ~/praktikum-os/week07-bash/backup
total 12K
drwxrwxr-x 2 praditadf praditadf 4.0K Apr  9 13:27 .
drwxrwxr-x 7 praditadf praditadf 4.0K Apr  8 12:46 ..
-rw-rw-r-- 1 praditadf praditadf   10 Apr  9 13:27 sample-app.conf.2026-04-09-132713.bak
praditadf@praditadf-VirtualBox:~$ type backup_conf
backup_conf is a function
backup_conf () 
{ 
    if [ $# -ne 1 ]; then
        echo " Usage : backup_conf <file>";
        return 1;
    fi;
    local src="$1";
    local dst="$HOME/praktikum-os/week07-bash/backup";
    if [ ! -f "$src" ]; then
        echo "File tidak ditemukan: $src";
        return 2;
    fi;
    mkdir -p "$dst";
    cp -- "$src" "$dst/$(basename "$src").$(date +%F-%H%M%S).bak";
    echo "Backup selesai di $dst"
}
```

## Praktikum 6.9 — Menggunakan Completion Dasar dan Melihat History

### 1. Pastikan file contoh tersedia

### 2. Uji completion file

### 3. Jalankan beberapa perintah sederhana

## Praktikum 6.10 — Menelusuri Perintah Diagnostik dengan History

### 1. Jalankan beberapa perintah diagnostik

### 2. Cari ulang perintah diagnostik dari history

### 3. Jalankan ulang salah satu perintah berdasarkan nomor history

### 4. Simpan potongan history ke file dokumentasi

## Praktikum 6.11 — Mencoba Wildcard Dasar

### 1. Masuk ke direktori sampel

### 2. Coba beberapa pola wildcard

### 3. Coba beberapa ekspansi lain

## Praktikum 6.12 — Mengarsipkan Banyak Log Sekaligus

### 1. Siapkan file log tambahan

### 2. Preview file yang akan diproses

### 3. Pindahkan semua file log ke folder arsip

### 4. Kompres folder arsip

## Praktikum 6.13 — Membedakan Single Quote, Double Quote, dan Escape

### 1. Uji single quote dan double quote

### 2. Uji escape karakter spasi

### 3. Uji akses file yang sama dengan double quote

## Praktikum 6.14 — Menangani File dengan Nama Sulit Secara Aman

### 1. Pastikan file target tersedia

### 2. Salin file dengan nama kompleks ke folder backup

### 3. Gunakan variabel untuk memproses path dengan aman

### 4. Tampilkan daftar file hasil backup ###

# 1.8 Tugas Praktikum

## Tugas Praktikum 1 — Toolkit Bash Administrator Pribadi

Konteks riil: seorang administrator sering mengulang perintah yang sama setiap hari. Agar pekerjaan lebih efisien dan konsisten, ia perlu memiliki toolkit Bash pribadi yang otomatis aktif setiap login.
Instruksi tugas:

1. Tambahkan konfigurasi pada .bashrc untuk:
• menambahkan direktori bin pribadi ke PATH,
• membuat minimal 2 alias yang membantu kerja harian,
• membuat minimal 1 fungsi shell yang berguna untuk administrasi.
2. Pastikan konfigurasi tersebut aktif kembali saat membuka shell login.
3. Buat satu script sederhana di direktori bin pribadi, misalnya script untuk menampilkan ringkasan sistem.
4. Uji dari direktori yang berbeda untuk memastikan script dapat dipanggil tanpa menuliskan path lengkap.
5. Simpan bukti pengujian ke file toolkit-bash-report.txt.
Minimal luaran:
• isi blok konfigurasi yang ditambahkan ke .bashrc,
• output echo $PATH,
• output type untuk alias, fungsi, dan script,
• file laporan toolkit-bash-report.txt.

## Tugas Praktikum 2 — Audit File Konfigurasi dan Logging Aman

Konteks riil: saat troubleshooting, administrator sering perlu menginventarisasi file konfigurasi dan memisahkan output normal dari pesan error.
Instruksi tugas:

1. Buat file laporan bernama audit-konfigurasi-$(date +%F).txt.
2. Cari file *.conf di dalam /etc dan simpan hasilnya ke file laporan.
3. Catat jumlah total file konfigurasi yang ditemukan.
4. Jika ada pesan error, simpan ke file terpisah, misalnya audit-error.log.
5. Tampilkan isi laporan ke terminal dan sekaligus simpan menggunakan tee.
6. Tambahkan ringkasan singkat 3–5 baris yang menjelaskan mengapa pemisahan stdout dan stderr penting dalam audit sistem.
Syarat konsep yang harus muncul:
• redirection >, 2>, atau &>,
• pipeline,
• tee,
• penggunaan variabel atau command substitution.
Minimal luaran:
• file laporan audit,
• file log error,
• perintah yang digunakan,
• analisis singkat hasil audit.

## Tugas Praktikum 3 — Mini Health Check Harian Server

Konteks riil: administrator perlu membuat pemeriksaan cepat (health check) untuk mengetahui kondisi dasar server sebelum dan sesudah maintenance.
Instruksi tugas:

1. Buat script Bash bernama daily-healthcheck pada direktori bin pribadi.
2. Script minimal harus menampilkan:
• tanggal dan waktu,
• hostname,
• user aktif,
• shell aktif,
• uptime,
• penggunaan memori,
• penggunaan filesystem root,
• 10 baris terakhir history command yang relevan dengan pengecekan.
3. Simpan hasil ke file log harian, misalnya healthcheck-$(date +%F).log.
4. Tampilkan hasil ke terminal dan ke file secara bersamaan.
5. Jika Anda menggunakan pipeline dengan tee, cek juga status exit command utama.
Syarat konsep yang harus muncul:
• environment variable,
• PATH,
• alias atau fungsi pendukung,
• history,
• tee,
• penanganan error dasar.
Minimal luaran:
• file script yang executable,
• contoh isi file log hasil eksekusi,
• penjelasan singkat fungsi tiap bagian script.

## Tugas Praktikum 4 — Penanganan File dengan Nama Kompleks dan Arsip Aman

Konteks riil: file hasil backup, ekspor, atau laporan sering memiliki nama yang mengandung spasi atau karakter khusus. Administrator harus tetap dapat memproses file-file tersebut tanpa salah target.
Instruksi tugas:

1. Buat minimal 4 file contoh dengan nama yang bervariasi, termasuk:
• nama file yang mengandung spasi,
• nama file yang mengandung tanda kurung siku atau karakter khusus,
• file dengan pola nama serupa untuk diuji dengan wildcard.
2. Tunjukkan perbedaan hasil jika file diakses tanpa quoting dan dengan quoting yang benar.
3. Lakukan preview wildcard dengan echo sebelum dipakai untuk operasi nyata.
4. Salin file-file tersebut ke direktori backup dengan nama yang aman.
5. Buat arsip tar.gz dari hasil backup.
6. Simpan riwayat perintah yang Anda gunakan ke file riwayat-arsip.txt. Syarat konsep yang harus muncul:
• single quote, double quote, dan escaping,
• wildcard,
• variabel path,
• history,
• operasi file lanjutan yang aman.
Minimal luaran:
• daftar file awal,
• daftar file hasil backup,
• file arsip tar.gz,
• file riwayat-arsip.txt,
• refleksi singkat tentang pentingnya quoting di Bash
