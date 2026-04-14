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

```
praditadf@praditadf-VirtualBox:~$ cd ~/praktikum-os/week07-bash/sampel
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ touch laporan-harian.log laporan-mingguan.log laporan-bulanan.log
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ ls
backup-01.tar  backup-02.tar  catatan-a.txt  catatan-b.txt  laporan-bulanan.log  laporan-harian.log  laporan-mingguan.log
```

### 2. Uji completion file

```
a) cat lap lalu Tab dua kali menjadi cat laporan-
b) daftar file yang memiliki prefix lap yakni laporan-harian.log laporan-mingguan.log laporan-bulanan.log
c) cat laporan-h lalu tekan Tab menghasilkan cat laporan-harian.log
```

### 3. Jalankan beberapa perintah sederhana

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ pwd
/home/praditadf/praktikum-os/week07-bash/sampel
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ ls -lah
total 8.0K
drwxrwxr-x 2 praditadf praditadf 4.0K Apr  8 12:23 .
drwxrwxr-x 7 praditadf praditadf 4.0K Apr  8 12:46 ..
-rw-rw-r-- 1 praditadf praditadf    0 Apr  8 12:22 backup-01.tar
-rw-rw-r-- 1 praditadf praditadf    0 Apr  8 12:22 backup-02.tar
-rw-rw-r-- 1 praditadf praditadf    0 Apr  8 12:21 catatan-a.txt
-rw-rw-r-- 1 praditadf praditadf    0 Apr  8 12:21 catatan-b.txt
-rw-rw-r-- 1 praditadf praditadf    0 Apr  9 13:30 laporan-bulanan.log
-rw-rw-r-- 1 praditadf praditadf    0 Apr  9 13:30 laporan-harian.log
-rw-rw-r-- 1 praditadf praditadf    0 Apr  9 13:30 laporan-mingguan.log
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ date
Thu Apr  9 01:35:40 PM WIB 2026
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ whoami
praditadf
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ history | tail -n 10
 1804  clear
 1805  cd ~/praktikum-os/week07-bash/sampel
 1806  touch laporan-harian.log laporan-mingguan.log laporan-bulanan.log
 1807  ls
 1808  cat lap
 1809  pwd
 1810  ls -lah
 1811  date
 1812  whoami
 1813  history | tail -n 10
```

## Praktikum 6.10 — Menelusuri Perintah Diagnostik dengan History

### 1. Jalankan beberapa perintah diagnostik

```
praditadf@praditadf-VirtualBox:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           392M  1.6M  390M   1% /run
/dev/sda2        25G   16G  8.1G  66% /
tmpfs           2.0G   25M  1.9G   2% /dev/shm
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           392M  140K  392M   1% /run/user/1000
praditadf@praditadf-VirtualBox:~$ free -h
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.5Gi       131Mi       184Mi       1.5Gi       1.3Gi
Swap:          2.0Gi       489Mi       1.5Gi
praditadf@praditadf-VirtualBox:~$ uptime
 13:37:16 up 46 min,  1 user,  load average: 0.43, 0.96, 0.99
praditadf@praditadf-VirtualBox:~$ ps aux | head
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.2  0.3  23508 14612 ?        Ss   12:50   0:06 /sbin/init splash
root           2  0.0  0.0      0     0 ?        S    12:50   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    12:50   0:00 [pool_workqueue_release]
root           4  0.0  0.0      0     0 ?        I<   12:50   0:00 [kworker/R-rcu_gp]
root           5  0.0  0.0      0     0 ?        I<   12:50   0:00 [kworker/R-sync_wq]
root           6  0.0  0.0      0     0 ?        I<   12:50   0:00 [kworker/R-kvfree_rcu_reclaim]
root           7  0.0  0.0      0     0 ?        I<   12:50   0:00 [kworker/R-slub_flushwq]
root           8  0.0  0.0      0     0 ?        I<   12:50   0:00 [kworker/R-netns]
root          12  0.0  0.0      0     0 ?        I    12:50   0:00 [kworker/u8:0-ipv6_addrconf]
```

### 2. Cari ulang perintah diagnostik dari history

```
praditadf@praditadf-VirtualBox:~$ history | grep -E 'df -h | free -h | uptime | ps aux'
 1118  ps aux
 1119  ps aux -L
 1123  ps aux | wc -1
 1124  ps aux | wc -l
 1125  ps aux wc -
 1126  ps aux | wc -l
 1127  ps aux --sort=pid | head -5
 1132  ps aux
 1133  ps aux | head 2
 1134  ps aux | head -2
 1135  ps aux -l | head -2
 1136  ps aux -L | head -2
 1137  ps aux | head -2
 1138  ps aux | grep sleep
 1172  ps aux | grep sleep
 1176  ps aux | grep sleep
 1179  ps aux | grep sleep
 1184  ps aux | grep sleep
 1186  ps aux | grep sleep
 1191  ps aux | grep -v sleep | grep sleep
 1192  ps aux | grep -v grep | grep sleep
 1194  ps aux | grep -v grep | grep sleep
 1198  ps aux | grep -v grep | grep sleep
 1200  ps aux | grep -v grep | grep sleep
 1202  ps aux | grep sleep
 1204  ps aux | grep sleep
 1206  ps aux | grep sleep
 1209  ps aux | grep sleep
 1211  ps aux | grep sleep
 1213  ps aux | grep sleep
 1215  ps aux | grep sleep
 1248  ps aux --sort=-%cpu | -head 10
 1249  ps aux --sort=-%cpu | head 10
 1250  ps aux --sort=-%cpu | head -10
 1252  ps aux --sort=-%cpu | head -10
 1253  ps aux --sort=-%mem | head -10
 1262  ps aux -sort=%mem
 1263  ps aux--sort=%mem
 1265  ps aux --sort=-%mem | head -10
 1270  ps aux | grep sleep
 1272  ps aux -forest
 1273  ps aux
 1274  ps aux -forest
 1276  ps aux --forest
 1285  ps aux
 1286  ps aux | awk '$8 ~ /^S/'
 1307  ps aux | grep sleep
 1309  ps aux | grep sleep
 1311  ps aux | grep sleep
 1390  df -h /
 1819  ps aux | head
 1820  history | grep -E 'df -h | free -h | uptime | ps aux'
```

### 3. Jalankan ulang salah satu perintah berdasarkan nomor history

```
praditadf@praditadf-VirtualBox:~$ !1390
df -h /
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        25G   16G  8.1G  66% /
```

### 4. Simpan potongan history ke file dokumentasi

```
praditadf@praditadf-VirtualBox:~$ history | tail -n 20 > ~/praktikum-os/week07-bash/diag-history.txt
praditadf@praditadf-VirtualBox:~$ cat ~/praktikum-os/week07-bash/diag-history.txt
 1803  type backup_conf
 1804  clear
 1805  cd ~/praktikum-os/week07-bash/sampel
 1806  touch laporan-harian.log laporan-mingguan.log laporan-bulanan.log
 1807  ls
 1808  cat lap
 1809  pwd
 1810  ls -lah
 1811  date
 1812  whoami
 1813  history | tail -n 10
 1814  cd
 1815  clear
 1816  df -h
 1817  free -h
 1818  uptime
 1819  ps aux | head
 1820  history | grep -E 'df -h | free -h | uptime | ps aux'
 1821  df -h /
 1822  history | tail -n 20 > ~/praktikum-os/week07-bash/diag-history.txt
```

## Praktikum 6.11 — Mencoba Wildcard Dasar

### 1. Masuk ke direktori sampel

```
praditadf@praditadf-VirtualBox:~$ cd ~/praktikum-os//week07-bash//sampel
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ ls
backup-01.tar  backup-02.tar  catatan-a.txt  catatan-b.txt  laporan-bulanan.log  laporan-harian.log  laporan-mingguan.log
```

### 2. Coba beberapa pola wildcard

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ ls *.log
laporan-bulanan.log  laporan-harian.log  laporan-mingguan.log
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ ls catatan-?.txt
catatan-a.txt  catatan-b.txt
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ ls backup-0[12].tar
backup-01.tar  backup-02.tar
```

### 3. Coba beberapa ekspansi lain

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ echo log-{pagi,siang,malam}.txt
log-pagi.txt log-siang.txt log-malam.txt
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ echo ~
/home/praditadf
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ echo ~/praktikum-os/week07-bash
/home/praditadf/praktikum-os/week07-bash
```

## Praktikum 6.12 — Mengarsipkan Banyak Log Sekaligus

### 1. Siapkan file log tambahan

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/sampel$ cd ~/praktikum-os/week07-bash/logs
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/logs$ touch acces-01.log acces-02.log acces-03.log
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/logs$ ls
acces-01.log  acces-02.log  acces-03.log  app-01.log  app-02.log  app-03.log
```

### 2. Preview file yang akan diproses

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/logs$ echo *.log
acces-01.log acces-02.log acces-03.log app-01.log app-02.log app-03.log
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/logs$ echo acces-0?.log
acces-01.log acces-02.log acces-03.log
```

### 3. Pindahkan semua file log ke folder arsip

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/logs$ mkdir -p arsip-log
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/logs$ mv *.log arsip-log/
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/logs$ ls arsip-log
acces-01.log  acces-02.log  acces-03.log  app-01.log  app-02.log  app-03.log
```

### 4. Kompres folder arsip

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/logs$ tar -czf arsip-log-$(date +%F).tar.gz arsip-log
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/logs$ ls -lah
total 16K
drwxrwxr-x 3 praditadf praditadf 4.0K Apr  9 13:48 .
drwxrwxr-x 7 praditadf praditadf 4.0K Apr  9 13:40 ..
drwxrwxr-x 2 praditadf praditadf 4.0K Apr  9 13:47 arsip-log
-rw-rw-r-- 1 praditadf praditadf  217 Apr  9 13:48 arsip-log-2026-04-09.tar.gz
```

## Praktikum 6.13 — Membedakan Single Quote, Double Quote, dan Escape

### 1. Uji single quote dan double quote

```
praditadf@praditadf-VirtualBox:~$ echo '$USER bekerja di $HOME'
$USER bekerja di $HOME
praditadf@praditadf-VirtualBox:~$ echo "$USER bekerja di $HOME"
praditadf bekerja di /home/praditadf
```

### 2. Uji escape karakter spasi

```
praditadf@praditadf-VirtualBox:~$ cd ~/praktikum-os/week07-bash/ruang-nama
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ ls laporan\ server\ april.txt
'laporan server april.txt'
```

### 3. Uji akses file yang sama dengan double quote

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ cat "laporan server april.txt" 
```

## Praktikum 6.14 — Menangani File dengan Nama Sulit Secara Aman

### 1. Pastikan file target tersedia

```
praditadf@praditadf-VirtualBox:~$ cd ~/praktikum-os/week07-bash/ruang-nama
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ ls -lah
total 8.0K
drwxrwxr-x 2 praditadf praditadf 4.0K Apr  8 12:23  .
drwxrwxr-x 7 praditadf praditadf 4.0K Apr  9 13:40  ..
-rw-rw-r-- 1 praditadf praditadf    0 Apr  8 12:23 'backup [mingguan] server.conf'
-rw-rw-r-- 1 praditadf praditadf    0 Apr  8 12:23 'laporan server april.txt'
```

### 2. Salin file dengan nama kompleks ke folder backup

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ cp -- "backup [mingguan] server.conf" \
> "$HOME/praktikum-os/week07-bash/backup/backup-mingguan-server.conf"
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ 
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ cp -- "backup [mingguan] server.conf" \
> "$HOME/praktikum-os/week07-bash/backup/backup-mingguan-server.conf"
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ 
```

### 3. Gunakan variabel untuk memproses path dengan aman

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ file_asli="$HOME/praktikum-os/week07-bash/ruang-nama/backup [mingguan] server.conf"
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ file_salinan="$HOME/praktikum-os/week07-bash/backup/backup-mingguan-server-v2.conf" 
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ cp -- "$file_asli" "$file_salinan"
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ ls -lah "$HOME/praktikum-os/week07-bash/backup"
total 12K
drwxrwxr-x 2 praditadf praditadf 4.0K Apr  9 14:01 .
drwxrwxr-x 7 praditadf praditadf 4.0K Apr  9 13:40 ..
-rw-rw-r-- 1 praditadf praditadf    0 Apr  9 13:57 backup-mingguan-server.conf
-rw-rw-r-- 1 praditadf praditadf    0 Apr  9 14:01 backup-mingguan-server-v2.conf
-rw-rw-r-- 1 praditadf praditadf   10 Apr  9 13:27 sample-app.conf.2026-04-09-132713.bak
```

### 4. Tampilkan daftar file hasil backup

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ for file in "$HOME/praktikum-os/week07-bash/backup/*;
> do
> printf 'Hasil backup: %s\n' "$file'
> done
> ^C
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash/ruang-nama$ 
```

# 1.8 Tugas Praktikum

## Tugas Praktikum 1 — Toolkit Bash Administrator Pribadi

Konteks riil: seorang administrator sering mengulang perintah yang sama setiap hari. Agar pekerjaan lebih efisien dan konsisten, ia perlu memiliki toolkit Bash pribadi yang otomatis aktif setiap login.
Instruksi tugas:

1. Tambahkan konfigurasi pada .bashrc untuk:
   * menambahkan direktori bin pribadi ke PATH,
   * membuat minimal 2 alias yang membantu kerja harian,
   * membuat minimal 1 fungsi shell yang berguna untuk administrasi.
2. Pastikan konfigurasi tersebut aktif kembali saat membuka shell login.
3. Buat satu script sederhana di direktori bin pribadi, misalnya script untuk menampilkan ringkasan sistem.
4. Uji dari direktori yang berbeda untuk memastikan script dapat dipanggil tanpa menuliskan path lengkap.
5. Simpan bukti pengujian ke file toolkit-bash-report.txt.
Minimal luaran:

* isi blok konfigurasi yang ditambahkan ke .bashrc,
* output echo $PATH,
* output type untuk alias, fungsi, dan script,
* file laporan toolkit-bash-report.txt.

```
praditadf@praditadf-VirtualBox:~$ cat ~/praktikum-os/week07-bash/toolkit-bash-report.txt 

1. BLOK KONFIGURASI .bashrc

1. BLOK KONFIGURASI .bashrc
# --- Tugas Praktikum 1- Toolkit Bash Administrator Pribadi ---
export PATH="$HOME/praktikum-os/week07-bash/bin:$PATH"

alias ll='ls -lah --color=auto'
alias hist10='history | tail -n 10'

backup_conf () {
if [ $# -ne 1 ]; then
echo " Usage : backup_conf <file>"
return 1
fi

local src="$1"
local dst="$HOME/praktikum-os/week07-bash/backup"

if [ ! -f "$src" ]; then
echo "File tidak ditemukan: $src"
return 2
fi

mkdir -p "$dst"
cp -- "$src" "$dst/$(basename "$src").$(date +%F-%H%M%S).bak"
echo "Backup selesai di $dst"
}
# --- End Praktikum Bash Administrator ---


2. OUTPUT ECHO PATH:
/home/praditadf/praktikum-os/week07-bash/bin:/home/praditadf/praktikum-os/week07-bash/bin:/home/praditadf/praktikum-os/week07-bash/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin

3. OUTPUT TYPE: ALIAS, FUNGSI, SCRIPT:
ll is aliased to `ls -lah --color=auto'
hist10 is aliased to `history | tail -n 10'
ringkas-sistem is aliased to `free -h  && uptime -p'

4. HASIL EKSEKUSI SCRIPT:
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
ringkas-sistem is aliased to `free -h  && uptime -p'
```

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

* redirection >, 2>, atau &>,
* pipeline,
* tee,
* penggunaan variabel atau command substitution.
Minimal luaran:
* file laporan audit,
* file log error,
* perintah yang digunakan,
* analisis singkat hasil audit.

```
=== LAPORAN AUDIT FILE KONFIGURASI ===
Tanggal Audit: Tue Apr 14 09:20:11 PM WIB 2026
Daftar file .conf di /etc :
/etc/nsswitch.conf
/etc/fonts/snap-override/10-prefer-noto.conf
/etc/fonts/fonts.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-sans-mono.conf
/etc/fonts/conf.avail/57-dejavu-serif.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-sans.conf
/etc/fonts/conf.avail/65-droid-sans-fallback.conf
/etc/fonts/conf.avail/57-dejavu-sans-mono.conf
/etc/fonts/conf.avail/58-dejavu-lgc-sans.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-sans.conf
/etc/fonts/conf.avail/30-droid-noto-mono.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-lgc-serif.conf
/etc/fonts/conf.avail/30-droid-noto.conf
/etc/fonts/conf.avail/58-dejavu-lgc-serif.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-serif.conf
/etc/fonts/conf.avail/20-unhint-small-dejavu-sans-mono.conf
/etc/fonts/conf.avail/57-dejavu-sans.conf
/etc/fonts/conf.avail/58-dejavu-lgc-sans-mono.conf
/etc/pnm2ppa.conf
/etc/avahi/avahi-daemon.conf
/etc/debconf.conf
/etc/gdm3/custom.conf
/etc/ld.so.conf
/etc/initramfs-tools/update-initramfs.conf
/etc/initramfs-tools/initramfs.conf
/etc/xattr.conf
/etc/apparmor/parser.conf
/etc/security/time.conf
/etc/security/capability.conf
/etc/security/namespace.conf
/etc/security/pam_env.conf
/etc/security/pwhistory.conf
/etc/security/faillock.conf
/etc/security/sepermit.conf
/etc/security/limits.conf
/etc/security/group.conf
/etc/security/access.conf
/etc/security/pwquality.conf
/etc/security/limits.d/25-pw-rlimits.conf
/etc/security/limits.d/10-gamemode.conf
/etc/udisks2/udisks2.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-japan1.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-cns1.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-korea1.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-gb1.conf
/etc/ghostscript/cidfmap.d/90gs-cjk-resource-japan2.conf
/etc/ghostscript/fontmap.d/10fonts-urw-base35.conf
/etc/sudo_logsrvd.conf
/etc/libaudit.conf
/etc/hdparm.conf
/etc/xdg/user-dirs.conf
/etc/gtk-2.0/im-multipress.conf
/etc/ucf.conf
/etc/ufw/sysctl.conf
/etc/ufw/ufw.conf
/etc/e2scrub.conf
/etc/depmod.d/ubuntu.conf
/etc/dbus-1/system.d/com.ubuntu.LanguageSelector.conf
/etc/dbus-1/system.d/org.debian.apt.conf
/etc/dbus-1/system.d/com.ubuntu.SoftwareProperties.conf
/etc/dbus-1/system.d/com.hp.hplip.conf
/etc/dbus-1/system.d/com.redhat.PrinterDriversInstaller.conf
/etc/dbus-1/system.d/kerneloops.conf
/etc/dbus-1/system.d/com.redhat.NewPrinterNotification.conf
/etc/dbus-1/system.d/org.opensuse.CupsPkHelper.Mechanism.conf
/etc/dbus-1/system.d/com.ubuntu.WhoopsiePreferences.conf
/etc/fprintd.conf
/etc/logrotate.conf
/etc/selinux/semanage.conf
/etc/ipp-usb/ipp-usb.conf
/etc/sudo.conf
/etc/snmp/snmp.conf
/etc/bluetooth/network.conf
/etc/bluetooth/input.conf
/etc/bluetooth/main.conf
/etc/hp/hplip.conf
/etc/cups/cups-browsed.conf
/etc/cups/cups-files.conf
/etc/cups/subscriptions.conf
/etc/cups/cupsd.conf
/etc/cups/snmp.conf
/etc/gtk-3.0/im-multipress.conf
/etc/apg.conf
/etc/ts.conf
/etc/UPower/UPower.conf
/etc/pam.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/blacklist-loop.conf
/etc/modprobe.d/intel-microcode-blacklist.conf
/etc/modprobe.d/amd64-microcode-blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/alsa-base.conf
/etc/locale.conf
/etc/sensors3.conf
/etc/NetworkManager/NetworkManager.conf
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
/etc/ld.so.conf.d/libc.conf
/etc/ld.so.conf.d/x86_64-linux-gnu.conf
/etc/apport/crashdb.conf
/etc/PackageKit/Vendor.conf
/etc/PackageKit/PackageKit.conf
/etc/kerneloops.conf
/etc/ca-certificates.conf
/etc/usb_modeswitch.conf
/etc/sane.d/ibm.conf
/etc/sane.d/canon_lide70.conf
/etc/sane.d/microtek.conf
/etc/sane.d/mustek_usb.conf
/etc/sane.d/xerox_mfp.conf
/etc/sane.d/tamarack.conf
/etc/sane.d/dll.conf
/etc/sane.d/genesys.conf
/etc/sane.d/hp4200.conf
/etc/sane.d/epson.conf
/etc/sane.d/pie.conf
/etc/sane.d/mustek_pp.conf
/etc/sane.d/dmc.conf
/etc/sane.d/dell1600n_net.conf
/etc/sane.d/kodak.conf
/etc/sane.d/lexmark.conf
/etc/sane.d/teco2.conf
/etc/sane.d/canon_dr.conf
/etc/sane.d/canon_pp.conf
/etc/sane.d/s9036.conf
/etc/sane.d/agfafocus.conf
/etc/sane.d/kvs1025.conf
/etc/sane.d/epsonds.conf
/etc/sane.d/gphoto2.conf
/etc/sane.d/artec.conf
/etc/sane.d/snapscan.conf
/etc/sane.d/matsushita.conf
/etc/sane.d/plustek_pp.conf
/etc/sane.d/ma1509.conf
/etc/sane.d/umax_pp.conf
/etc/sane.d/airscan.conf
/etc/sane.d/dc25.conf
/etc/sane.d/fujitsu.conf
/etc/sane.d/hpsj5s.conf
/etc/sane.d/st400.conf
/etc/sane.d/rts8891.conf
/etc/sane.d/umax.conf
/etc/sane.d/apple.conf
/etc/sane.d/microtek2.conf
/etc/sane.d/canon.conf
/etc/sane.d/coolscan2.conf
/etc/sane.d/teco1.conf
/etc/sane.d/hs2p.conf
/etc/sane.d/pieusb.conf
/etc/sane.d/coolscan3.conf
/etc/sane.d/dc210.conf
/etc/sane.d/stv680.conf
/etc/sane.d/pixma.conf
/etc/sane.d/magicolor.conf
/etc/sane.d/teco3.conf
/etc/sane.d/bh.conf
/etc/sane.d/mustek.conf
/etc/sane.d/epjitsu.conf
/etc/sane.d/saned.conf
/etc/sane.d/plustek.conf
/etc/sane.d/sharp.conf
/etc/sane.d/sm3840.conf
/etc/sane.d/abaton.conf
/etc/sane.d/hp3900.conf
/etc/sane.d/test.conf
/etc/sane.d/hp5400.conf
/etc/sane.d/coolscan.conf
/etc/sane.d/cardscan.conf
/etc/sane.d/avision.conf
/etc/sane.d/gt68xx.conf
/etc/sane.d/canon630u.conf
/etc/sane.d/net.conf
/etc/sane.d/qcam.conf
/etc/sane.d/sceptre.conf
/etc/sane.d/nec.conf
/etc/sane.d/epson2.conf
/etc/sane.d/umax1220u.conf
/etc/sane.d/ricoh.conf
/etc/sane.d/leo.conf
/etc/sane.d/kodakaio.conf
/etc/sane.d/p5.conf
/etc/sane.d/artec_eplus48u.conf
/etc/sane.d/dc240.conf
/etc/sane.d/sp15c.conf
/etc/sane.d/escl.conf
/etc/sane.d/u12.conf
/etc/sane.d/hp.conf
/etc/nftables.conf
/etc/udev/iocost.conf
/etc/udev/udev.conf
/etc/adduser.conf
/etc/geoclue/geoclue.conf
/etc/host.conf
/etc/pulse/client.conf
/etc/deluser.conf
/etc/cracklib/cracklib.conf
/etc/modules-load.d/cups-filters.conf
/etc/modules-load.d/lp.conf
/etc/modules-load.d/loop.conf
/etc/apt/apt.conf.d/20apt-esm-hook.conf
/etc/apt/apt.conf.d/20snapd.conf
/etc/environment.d/90atk-adaptor.conf
/etc/environment.d/90qt-a11y.conf
/etc/dhcpcd.conf
/etc/gai.conf
/etc/ubuntu-advantage/uaclient.conf
/etc/fwupd/fwupd.conf
/etc/fwupd/remotes.d/lvfs-testing.conf
/etc/fwupd/remotes.d/lvfs.conf
/etc/fwupd/remotes.d/vendor-directory.conf
/etc/brltty.conf
/etc/ldap/ldap.conf
/etc/rygel.conf
/etc/speech-dispatcher/speechd.conf
/etc/speech-dispatcher/modules/espeak-ng.conf
/etc/speech-dispatcher/modules/flite.conf
/etc/speech-dispatcher/modules/mary-generic.conf
/etc/speech-dispatcher/modules/llia_phon-generic.conf
/etc/speech-dispatcher/modules/swift-generic.conf
/etc/speech-dispatcher/modules/espeak.conf
/etc/speech-dispatcher/modules/espeak-ng-mbrola-generic.conf
/etc/speech-dispatcher/modules/espeak-ng-mbrola.conf
/etc/speech-dispatcher/modules/espeak-mbrola-generic.conf
/etc/speech-dispatcher/modules/festival.conf
/etc/speech-dispatcher/modules/openjtalk.conf
/etc/speech-dispatcher/modules/mimic3-generic.conf
/etc/speech-dispatcher/modules/cicero.conf
/etc/speech-dispatcher/modules/epos-generic.conf
/etc/speech-dispatcher/modules/dtk-generic.conf
/etc/speech-dispatcher/clients/emacs.conf
/etc/updatedb.conf
/etc/libao.conf
/etc/init/whoopsie.conf
/etc/mke2fs.conf
/etc/systemd/logind.conf
/etc/systemd/timesyncd.conf
/etc/systemd/user.conf
/etc/systemd/resolved.conf
/etc/systemd/sleep.conf
/etc/systemd/journald.conf
/etc/systemd/pstore.conf
/etc/systemd/networkd.conf
/etc/systemd/system.conf
/etc/systemd/oomd.conf
/etc/fuse.conf
/etc/openal/alsoft.conf
/etc/rsyslog.conf
/etc/sysctl.conf
/etc/rsyslog.d/21-cloudinit.conf
/etc/rsyslog.d/50-default.conf
/etc/rsyslog.d/20-ufw.conf
/etc/sysctl.d/10-zeropage.conf
/etc/sysctl.d/10-kernel-hardening.conf
/etc/sysctl.d/10-bufferbloat.conf
/etc/sysctl.d/10-map-count.conf
/etc/sysctl.d/10-network-security.conf
/etc/sysctl.d/10-console-messages.conf
/etc/sysctl.d/10-ptrace.conf
/etc/sysctl.d/10-magic-sysrq.conf
/etc/sysctl.d/10-ipv6-privacy.conf
Total file konfigurasi .conf: 264 file
=== RINGKASAN STDOUT & STDERR ===
stdout dan stderr sangat penting dalam audit sistem
Karena leporan dapat menjadi lebih rapi dan mudah dibaca
tanpa ada pesan 'permission denied'
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ ls -lah audit-konfigurasi-*.txt
-rw-rw-r-- 1 praditadf praditadf 8.2K Apr 14 21:20 audit-konfigurasi-2026-04-14.txt
-rw-rw-r-- 1 praditadf praditadf 8.2K Apr 14 21:19 audit-konfigurasi-.txt
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ head -n 5 audit-error.log
find: ‘/etc/credstore.encrypted’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/etc/cups/ssl’: Permission denied
find: ‘/etc/polkit-1/rules.d’: Permission denied
find: ‘/etc/sssd’: Permission denied
```

* Perintah yang digunakan

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ {
    echo "=== LAPORAN AUDIT FILE KONFIGURASI ===";
    echo "Tanggal Audit: $(date)"; 
    echo "Daftar file .conf di /etc :"; find /etc -type f -name "*.conf" 2> audit-error.log;
    JUMLAH=$(find /etc -type f -name "*.conf" 2>/dev/null | wc -l);
    echo "Total file konfigurasi .conf: $JUMLAH file"; 
    echo "=== RINGKASAN STDOUT & STDERR ===";
    echo "stdout dan stderr sangat penting dalam audit sistem";
    echo "Karena leporan dapat menjadi lebih rapi dan mudah dibaca";
    echo "tanpa ada pesan 'permission denied'"; 
    } | tee "audit-konfigurasi-$(date +%F).txt"
```

## Tugas Praktikum 3 — Mini Health Check Harian Server

Konteks riil: administrator perlu membuat pemeriksaan cepat (health check) untuk mengetahui kondisi dasar server sebelum dan sesudah maintenance.
Instruksi tugas:

1. Buat script Bash bernama daily-healthcheck pada direktori bin pribadi.
2. Script minimal harus menampilkan:

* tanggal dan waktu,
* hostname,
* user aktif,
* shell aktif,
* uptime,
* penggunaan memori,
* penggunaan filesystem root,
* 10 baris terakhir history command yang relevan dengan pengecekan.

1. Simpan hasil ke file log harian, misalnya healthcheck-$(date +%F).log.
2. Tampilkan hasil ke terminal dan ke file secara bersamaan.
3. Jika Anda menggunakan pipeline dengan tee, cek juga status exit command utama.
Syarat konsep yang harus muncul:

* environment variable,
* PATH,
* alias atau fungsi pendukung,
* history,
* tee,
* penanganan error dasar.
Minimal luaran:
* file script yang executable,

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ cat <<'EOF' > ~/praktikum-os/week07-bash/bin/daily-healthcheck
#!/usr/bin/env bash
echo " === MINI HEALTH CHECK HARIAN === "
                                                 
echo "Tanggal & Waktu : $(date)"         
echo "Hostname        : $(hostname)"             
echo "User Aktif      : $(whoami)"
echo "Shell Aktif     : $SHELL"
echo "Uptime          : $(uptime -p)"
                                     
echo "[1] Penggunaan Memori:"        
free -h                                          
                             
echo "[2] Penggunaan Filesystem Root (/):"
df -h /                                          
                                          
echo "[3] 10 Baris History Terakhir:"
tail -n 10 ~/.bash_history                                                  

EOF
```

* contoh isi file log hasil eksekusi,

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week07-bash$ daily-healthcheck | tee ~/praktikum-os/week07-bash/logs/healthcheck-$(date +%F).log
 === MINI HEALTH CHECK HARIAN === 
Tanggal & Waktu : Tue Apr 14 09:37:02 PM WIB 2026
Hostname        : praditadf-VirtualBox
User Aktif      : praditadf
Shell Aktif     : /bin/bash
Uptime          : up 2 hours, 0 minutes
[1] Penggunaan Memori:
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.5Gi       144Mi       177Mi       1.4Gi       1.3Gi
Swap:          2.0Gi       717Mi       1.3Gi
[2] Penggunaan Filesystem Root (/):
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        25G   15G  8.9G  62% /
[3] 10 Baris History Terakhir:
df -h
lscpu
cat /proc/cpuinfo
cat /proc/meminfo
hist10
cek-sistem
ringkas-sistem
nano ./bashrc
cd ~/praktikum-os/week07-bash/
nano ./bashrc
```

* penjelasan singkat fungsi tiap bagian script.

```
$(...)Digunakan untuk menyisipkan hasil perintah seperti date, hostname, whoami, uptime -p secara langsung ke dalam teks.

free -h: Menampilkan informasi penggunaan memori (RAM) dan Swap.

df -h /: Menampilkan kapasitas, penggunaan, tersedia, dan sisa ruang penyimapan pada direktori root.

tail -n 10 ~/.bash_history: Membaca 10 baris terakhir dari riwayat perintah.
```

## Tugas Praktikum 4 — Penanganan File dengan Nama Kompleks dan Arsip Aman

Konteks riil: file hasil backup, ekspor, atau laporan sering memiliki nama yang mengandung spasi atau karakter khusus. Administrator harus tetap dapat memproses file-file tersebut tanpa salah target.
Instruksi tugas:

1. Buat minimal 4 file contoh dengan nama yang bervariasi, termasuk:

* nama file yang mengandung spasi,
* nama file yang mengandung tanda kurung siku atau karakter khusus,
* file dengan pola nama serupa untuk diuji dengan wildcard.

1. Tunjukkan perbedaan hasil jika file diakses tanpa quoting dan dengan quoting yang benar.
2. Lakukan preview wildcard dengan echo sebelum dipakai untuk operasi nyata.
3. Salin file-file tersebut ke direktori backup dengan nama yang aman.
4. Buat arsip tar.gz dari hasil backup.
5. Simpan riwayat perintah yang Anda gunakan ke file riwayat-arsip.txt. Syarat konsep yang harus muncul:

* single quote, double quote, dan escaping,
* wildcard,
* variabel path,
* history,
* operasi file lanjutan yang aman.
Minimal luaran:
* daftar file awal,
* daftar file hasil backup,
* file arsip tar.gz,
* file riwayat-arsip.txt,
* refleksi singkat tentang pentingnya quoting di Bash
