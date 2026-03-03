# 1.11 Latihan

## Latihan 3.1
Buatlah script yang:
1. Menampilkan daftar 10 file terbesar di direktori /var/log/
2. Menyimpan hasilnya ke file large-logs.txt
3. Menampilkan output juga di terminal menggunakan tee
4. Menangani error dengan redirect ke error.log

``` $ ls -lS /var/log/ | sort -k5 -rh | head -10 2> error.log | tee large-logs.txt ```
```
-rw-r-----  1 syslog            adm             2880653 Mar  3 11:08 syslog.1
-rw-r--r--  1 root              root             996465 Feb 25 10:47 dpkg.log.1
-rw-r-----  1 syslog            adm              848840 Mar  3 11:08 kern.log.1
-rw-r-----  1 syslog            adm              530260 Feb 24 15:16 syslog.2.gz
-rw-r-----  1 syslog            adm              482456 Mar  3 17:16 syslog
-rw-r-----  1 syslog            adm              166178 Feb 24 15:16 kern.log.2.gz
-rw-r-----  1 syslog            adm              149884 Mar  3 17:16 kern.log
-rw-r--r--  1 root              root             118497 Feb 10 07:20 bootstrap.log
-rw-------  1 root              root             105106 Mar  3 11:08 boot.log.1
-rw-------  1 root              root              80750 Feb 19 20:10 boot.log.5
```

## Latihan 3.2
Buat pipeline yang:
1. Membaca /etc/passwd
2. Mengekstrak username (kolom pertama)
3. Mengurutkan alfabetis
4. Menyimpan ke file sorted-users.txt

   Hint: Gunakan cut, sort, dan operator redirect.
### Pipeline
``` $ cut -d: -f1 /etc/passwd | sort > sorted-users.txt ```
```
_apt
avahi
backup
bin
colord
cups-browsed
cups-pk-helper
daemon
dhcpcd
dnsmasq
fwupd-refresh
games
gdm
geoclue
gnome-initial-setup
gnome-remote-desktop
hplip
irc
kernoops
list
lp
mail
man
messagebus
news
nm-openvpn
nobody
polkitd
praditadf
proxy
root
rtkit
saned
speech-dispatcher
sssd
sync
sys
syslog
systemd-network
systemd-oom
systemd-resolve
systemd-timesync
tcpdump
tss
usbmux
uucp
uuidd
whoopsie
www-data
```

## Latihan 3.3
Tulis script monitoring yang:
1. Mencatat penggunaan CPU dan memory setiap 5 detik
2. Menyimpan log dengan timestamp
3. Berjalan selama 1 menit (12 iterasi)
4. Output ditampilkan di terminal DAN disimpan ke file
44 1 Dasar Input/Output (I/O)
1.12 Referensi Tambahan

## Latihan 3.4
Buat perintah yang:
1. Mencari semua file .conf di sistem
2. Membuang pesan "Permission denied"
3. Menghitung jumlah file yang ditemukan
4. Menyimpan daftar path lengkap ke file

## Latihan 3.5
Implementasikan script backup yang:
1. Menggunakan tar untuk backup direktori
2. Menampilkan progress dengan tee
3. Mencatat stdout ke backup-success.log
4. Mencatat stderr ke backup-error.log
5. Menambahkan timestamp di setiap log entry

