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
### Pipeline :
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

### Script Monitor :
```
#!/bin/bash
for i in {1..12}; do
date '+%Y-%m%-d %H:%M:%S' | tee -a log.txt
free -h | tee -a log.txt
uptime | tee -a log.txt
sleep 5 
done
```
``` $ bash monitor.sh
2026-033 18:12:29
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       202Mi       135Mi       1.6Gi       1.8Gi
Swap:          2.0Gi        23Mi       2.0Gi
 18:12:29 up  1:09,  1 user,  load average: 0.35, 0.43, 0.46
2026-033 18:12:34
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       202Mi       135Mi       1.6Gi       1.8Gi
Swap:          2.0Gi        23Mi       2.0Gi
 18:12:35 up  1:09,  1 user,  load average: 0.30, 0.41, 0.46
2026-033 18:12:40
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       201Mi       135Mi       1.6Gi       1.8Gi
Swap:          2.0Gi        23Mi       2.0Gi
 18:12:40 up  1:10,  1 user,  load average: 0.27, 0.40, 0.45
2026-033 18:12:45
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       201Mi       135Mi       1.6Gi       1.8Gi
Swap:          2.0Gi        23Mi       2.0Gi
 18:12:45 up  1:10,  1 user,  load average: 0.25, 0.40, 0.45
2026-033 18:12:50
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       201Mi       135Mi       1.6Gi       1.8Gi
Swap:          2.0Gi        23Mi       2.0Gi
 18:12:50 up  1:10,  1 user,  load average: 0.23, 0.39, 0.45
2026-033 18:12:55
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       201Mi       135Mi       1.6Gi       1.8Gi
Swap:          2.0Gi        23Mi       2.0Gi
 18:12:55 up  1:10,  1 user,  load average: 0.21, 0.38, 0.45
2026-033 18:13:00
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       201Mi       135Mi       1.6Gi       1.8Gi
Swap:          2.0Gi        23Mi       2.0Gi
 18:13:00 up  1:10,  1 user,  load average: 0.20, 0.38, 0.44
2026-033 18:13:05
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       201Mi       135Mi       1.6Gi       1.8Gi
Swap:          2.0Gi        23Mi       2.0Gi
 18:13:05 up  1:10,  1 user,  load average: 0.18, 0.37, 0.44
2026-033 18:13:10
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       199Mi       143Mi       1.6Gi       1.8Gi
Swap:          2.0Gi        23Mi       2.0Gi
 18:13:10 up  1:10,  1 user,  load average: 0.41, 0.41, 0.45
2026-033 18:13:16
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       197Mi       143Mi       1.6Gi       1.8Gi
Swap:          2.0Gi        23Mi       2.0Gi
 18:13:16 up  1:10,  1 user,  load average: 0.37, 0.41, 0.45
2026-033 18:13:21
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       197Mi       143Mi       1.6Gi       1.8Gi
Swap:          2.0Gi        23Mi       2.0Gi
 18:13:21 up  1:10,  1 user,  load average: 0.34, 0.40, 0.45
2026-033 18:13:26
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       197Mi       143Mi       1.6Gi       1.8Gi
Swap:          2.0Gi        23Mi       2.0Gi
 18:13:26 up  1:10,  1 user,  load average: 0.31, 0.39, 0.45
```

## Latihan 3.4
Buat perintah yang:
1. Mencari semua file .conf di sistem
2. Membuang pesan "Permission denied"
3. Menghitung jumlah file yang ditemukan
4. Menyimpan daftar path lengkap ke file

### Perintah :
```
$ find / -name "*.conf" 2> /dev/null | wc -l > path.txt
```

```
$ wc -l < path.txt
2078
```

## Latihan 3.5
Implementasikan script backup yang:
1. Menggunakan tar untuk backup direktori
2. Menampilkan progress dengan tee
3. Mencatat stdout ke backup-success.log
4. Mencatat stderr ke backup-error.log
5. Menambahkan timestamp di setiap log entry

### Script backup :
```
#!/bin/bash
echo "[$(date)] /home/user" | tee -a backup-succes.log
tar -cvzf backup.tar.gz /home/user 2>> backup-error.log | tee -a backup-succes.log
```
```
$ ./backup.sh
[Tue Mar  3 07:11:29 PM WIB 2026] /home/user
```
