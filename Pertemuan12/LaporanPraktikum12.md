# Manajemen Service

## Praktek 10.1 — Amati Layanan Aktif Saat Boot

### 1. Lihat semua layanan yang sedang berjalan

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl list-units --type=service --state=runing
  UNIT LOAD ACTIVE SUB DESCRIPTION

0 loaded units listed.
```

### 2. Lihat semua unit service yang ada (aktif maupun tidak)

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl list-unit-fil
es --type=service | head -30
UNIT FILE                                    STATE           PRESET
apparmor.service                             enabled         enabled
apport-autoreport.service                    static          -
apport-coredump-hook@.service                static          -
apport-forward@.service                      static          -
apport.service                               enabled         enabled
apt-daily-upgrade.service                    static          -
apt-daily.service                            static          -
apt-news.service                             static          -
autovt@.service                              alias           -
blk-availability.service                     enabled         enabled
bolt.service                                 static          -
cloud-config.service                         enabled         enabled
cloud-final.service                          enabled         enabled
cloud-init-hotplugd.service                  static          -
cloud-init-local.service                     enabled         enabled
cloud-init.service                           enabled         enabled
console-getty.service                        disabled        disabled
console-setup.service                        enabled         enabled
container-getty@.service                     static          -
cron.service                                 enabled         enabled
cryptdisks-early.service                     masked          enabled
cryptdisks.service                           masked          enabled
dbus-org.freedesktop.hostname1.service       alias           -
dbus-org.freedesktop.locale1.service         alias           -
dbus-org.freedesktop.login1.service          alias           -
dbus-org.freedesktop.ModemManager1.service   alias           -
dbus-org.freedesktop.resolve1.service        alias           -
dbus-org.freedesktop.thermald.service        alias           -
dbus-org.freedesktop.timedate1.service       alias           -
```

### 3. Analisis waktu boot dan temukan layanan paling lambat

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemd-analyze
Startup finished in 6.014s (kernel) + 1min 16.451s (userspace) = 1min 22.466s
graphical.target reached after 1min 15.684s in userspace.
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemd-analyze blame | head -15
1min 4.497s vboxadd.service
    12.982s apt-daily-upgrade.service
     4.607s cloud-config.service
     3.247s cloud-init.service
     3.104s pollinate.service
     2.735s cloud-init-local.service
     2.168s fwupd.service
     1.670s dev-sda2.device
     1.608s dpkg-db-backup.service
     1.446s apparmor.service
     1.259s apport.service
      741ms cloud-final.service
      682ms e2scrub_reap.service
      603ms fwupd-refresh.service
      580ms logrotate.service
```

### Tantangan

Identifikasi tiga layanan dengan waktu inisialisasi terlama menggunakan systemd-analyze blame. Gunakan pipeline dari Bab 3 (| sort rh | head-3) untuk mempercepat pencariannya. Untuk setiap layanan, cari tahu fungsinya dengan systemctl cat nama-layanan. Tuliskan nama layanan, waktu inisialisasinya, dan penjelasan singkat fungsinya.

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemd-analyze blame | sort -rh | head -3
      741ms cloud-final.service
      682ms e2scrub_reap.service
      603ms fwupd-refresh.service
```

## Praktek 10.2 — Kelola Layanan SSH

### 1. Periksa status SSH secara menyeluruh

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl status ssh
○ ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; disabled; preset: enabled)
     Active: inactive (dead) since Wed 2026-05-13 05:45:48 UTC; 2min 26s ago
   Duration: 28.587s
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
   Main PID: 19829 (code=exited, status=0/SUCCESS)
      Tasks: 1 (limit: 4600)
     Memory: 1.2M (peak: 2.7M)
        CPU: 144ms
     CGroup: /system.slice/ssh.service
             └─19498 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl is-active ssh
inactive
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl is-enabled ssh
disabled
```

### 2. Lakukan restart dan pantau perubahannya

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo systemctl restart ssh
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; disabled; preset: enabled)
     Active: active (running) since Wed 2026-05-13 05:49:01 UTC; 3s ago
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 20656 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 20657 (sshd)
      Tasks: 2 (limit: 4600)
     Memory: 2.5M (peak: 2.8M)
        CPU: 134ms
     CGroup: /system.slice/ssh.service
             ├─19498 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"
             └─20657 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"
```

### 3. Lihat dependensi SSH

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl list-dependencies ssh
ssh.service
● ├─-.mount
● ├─ssh.socket
● ├─system.slice
● └─sysinit.target
●   ├─apparmor.service
●   ├─blk-availability.service
●   ├─dev-hugepages.mount
●   ├─dev-mqueue.mount
●   ├─finalrd.service
●   ├─keyboard-setup.service
●   ├─kmod-static-nodes.service
●   ├─ldconfig.service
●   ├─lvm2-lvmpolld.socket
●   ├─lvm2-monitor.service
●   ├─multipathd.service
○   ├─open-iscsi.service
●   ├─plymouth-read-write.service
●   ├─plymouth-start.service
●   ├─proc-sys-fs-binfmt_misc.automount
●   ├─setvtrgb.service
●   ├─sys-fs-fuse-connections.mount
●   ├─sys-kernel-config.mount
●   ├─sys-kernel-debug.mount
●   ├─sys-kernel-tracing.mount
○   ├─systemd-ask-password-console.path
●   ├─systemd-binfmt.service
○   ├─systemd-firstboot.service
○   ├─systemd-hwdb-update.service
●   ├─systemd-journal-catalog-update.service
●   ├─systemd-journal-flush.service
●   ├─systemd-journald.service
○   ├─systemd-machine-id-commit.service
●   ├─systemd-modules-load.service
○   ├─systemd-pcrmachine.service
○   ├─systemd-pcrphase-sysinit.service
○   ├─systemd-pcrphase.service
○   ├─systemd-pstore.service
●   ├─systemd-random-seed.service
○   ├─systemd-repart.service
●   ├─systemd-resolved.service
●   ├─systemd-sysctl.service
●   ├─systemd-sysusers.service
●   ├─systemd-timesyncd.service
●   ├─systemd-tmpfiles-setup-dev-early.service
●   ├─systemd-tmpfiles-setup-dev.service
●   ├─systemd-tmpfiles-setup.service
○   ├─systemd-tpm2-setup-early.service
○   ├─systemd-tpm2-setup.service
●   ├─systemd-udev-trigger.service
●   ├─systemd-udevd.service
●   ├─systemd-update-done.service
●   ├─systemd-update-utmp.service
●   ├─cryptsetup.target
●   ├─integritysetup.target
●   ├─local-fs.target
●   │ ├─-.mount
○   │ ├─systemd-fsck-root.service
●   │ └─systemd-remount-fs.service
●   ├─swap.target
●   └─veritysetup.target
```

### 4. Cek semua unit yang gagal di sistem

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl --failed
  UNIT LOAD ACTIVE SUB DESCRIPTION

0 loaded units listed.
```

### Tantangan

Buat skrip Bash (referensi Bab 7) bernama cek-layanan.sh yang memeriksa status daftar layanan dari sebuah berkas teks. Berkas teks daftar-layanan.txt berisi satu nama layanan per baris (isi minimal: ssh, cron, rsyslog). Skrip membaca setiap nama layanan, memeriksa statusnya dengan systemctl is-active, lalu menulis laporan ke berkas laporan-layanan.log dengan format: [TANGGAL] nama-layanan: ACTIVE/INACTIVE. Gunakan date untuk mendapatkan tanggal.

```

```

## Praktek 10.3 — Buat Layanan Sederhana dari Skrip Bash

### 1. Siapkan konten yang akan dilayani

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ cd ~/lab-os/chapter10-services
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ mkdir -p situs-demo
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ nano situs-demo/index.html
<!DOCTYPE html>
<html>
<body>
<h1>Halo dari layanan systemd kustom!</h1>
<p>Layanan ini dibuat pada praktek Bab 10.</p>
</body>
</html>
```

### 2. Buat skrip wrapper untuk server HTTP

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ nano ~/lab-os/chapter10-services/jalankan-server.sh
#!/bin/bash
DIREKTORI="$HOME/lab-os/chapter10-services/situs-demo"
PORT=9090
echo "Memulai server di port $PORT..."
exec python3 -m http.server $PORT --directory "$DIREKTORI"
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ chmod +x ~/lab-os/chapter10-services/jalankan-server.sh
```

### 3. Buat berkas unit systemd untuk layanan ini

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ nano ~/lab-os/chapter10-services/demo-web.service
[Unit]
Description=Demo Web Server Praktek Bab 10
After=network.target

[Service]
Type=simple
User=praditadf
WorkingDirectory=/home/praditadf/lab-os/chapter10-services/situs-demo
ExecStart=/usr/bin/python3 -m http.server 9090
Restart=on-failure
RestartSec=3s

[Install]
WantedBy=multi-user.target
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo cp ~/lab-os/chapter10-services/demo-web.service /etc/systemd/system/demo-web.service
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo systemctl daemon-reload
```

### 4. Jalankan layanan dan verifikasi

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo systemctl start demo-web
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl status demo-web
● demo-web.service - Demo Web Server Praktek Bab 10
     Loaded: loaded (/etc/systemd/system/demo-web.service; disabled; preset: enabled)
     Active: active (running) since Wed 2026-05-13 14:00:04 UTC; 4s ago
   Main PID: 21946 (python3)
      Tasks: 1 (limit: 4600)
     Memory: 9.3M (peak: 9.7M)
        CPU: 295ms
     CGroup: /system.slice/demo-web.service
             └─21946 /usr/bin/python3 -m http.server 9090
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ curl http://localhost:9090
<!DOCTYPE html>
<html>
<body>
<h1>Halo dari layanan systemd kustom!</h1>
<p>Layanan ini dibuat pada praktek Bab 10.</p>
</body>
</html>
```

### 5. Uji fitur restart otomatis

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl status demo-web | grep "Main PID"
   Main PID: 21946 (python3)
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo kill -9 $(systemctl show demo-web --property=MainPID --value)
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sleep 5
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl status demo-web
● demo-web.service - Demo Web Server Praktek Bab 10
     Loaded: loaded (/etc/systemd/system/demo-web.service; disabled; preset: enabled)
     Active: active (running) since Wed 2026-05-13 14:00:33 UTC; 8s ago
   Main PID: 21961 (python3)
      Tasks: 1 (limit: 4600)
     Memory: 9.3M (peak: 9.9M)
        CPU: 230ms
     CGroup: /system.slice/demo-web.service
             └─21961 /usr/bin/python3 -m http.server 9090
```

### 6. Bersihkan layanan uji setelah selesai

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo systemctl disable --now demo-web
Removed "/etc/systemd/system/multi-user.target.wants/demo-web.service".
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo rm /etc/systemd/system/demo-web.service
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo systemctl daemon-reload
```

### Tantangan

Modifikasi berkas unit demo-web.service sebelum menghapusnya: tambahkan RestartSec=10s agar sistemmenunggu 10 detik sebelum mencoba restart, dan tambahkan Environment="PORT=9091" lalu ubah ExecStart agar menggunakan variabel tersebut. Aktifkan layanan dengan enable dan WantedBy=multi-user.target, lalu uji apakah layanan aktif setelah systemctl daemon-reload. Dokumentasikan perbedaan perilaku dibanding versi sebelumnya.

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ nano ~/lab-os/chapter10-services/demo-web.service
[Unit]
Description=Demo Web Server Praktek Bab 10
After=network.target

[Service]
Type=simple
User=praditadf
WorkingDirectory=/home/praditadf/lab-os/chapter10-services/situs-demo
Environment="PORT=9091"
ExecStart=/usr/bin/python3 -m http.server $PORT
Restart=on-failure
RestartSec=10s

[Install]
WantedBy=multi-user.target
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo cp ~/lab-os/chapter10-services/demo-web.service /etc/systemd/system/demo-web.service
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo systemctl daemon-reload
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo systemctl restart demo-web
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl status demo-web
● demo-web.service - Demo Web Server Praktek Bab 10
     Loaded: loaded (/etc/systemd/system/demo-web.service; enabled; preset: enabled)
     Active: active (running) since Wed 2026-05-13 14:06:39 UTC; 4s ago
   Main PID: 22133 (python3)
      Tasks: 1 (limit: 4600)
     Memory: 9.3M (peak: 9.6M)
        CPU: 279ms
     CGroup: /system.slice/demo-web.service
             └─22133 /usr/bin/python3 -m http.server 9091
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ curl http://localhost:9091
<!DOCTYPE html>
<html>
<body>
<h1>Halo dari layanan systemd kustom!</h1>
<p>Layanan ini dibuat pada praktek Bab 10.</p>
</body>
</html>
```

## Praktek 10.4 — Filter dan Analisis Log Layanan

### 1. Lihat log SSH dari satu jam terakhir

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo journalctl -u ssh --since "1 hour ago" --no-pager
May 14 04:23:36 Ubuntu-Server sshd[22354]: Accepted password for praditadf from 10.0.2.2 port 63999 ssh2
May 14 04:23:36 Ubuntu-Server sshd[22354]: pam_unix(sshd:session): session opened for user praditadf(uid=1000) by praditadf(uid=0)
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo journalctl -u cron --since "1 hour ago" --no-pager
May 14 04:25:01 Ubuntu-Server CRON[22499]: pam_unix(cron:session): session opened for user root(uid=0) by root(uid=0)
May 14 04:25:01 Ubuntu-Server CRON[22500]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
May 14 04:25:01 Ubuntu-Server CRON[22499]: pam_unix(cron:session): session closed for user root
```

### 2. Filter log berprioritas error ke atas

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo journalctl -b -p err --no-pager
May 10 07:36:23 localhost.localdomain kernel: vmwgfx 0000:00:02.0: [drm] *ERROR* vmwgfx seems to be running on an unsupported hypervisor.
May 10 07:36:23 localhost.localdomain kernel: vmwgfx 0000:00:02.0: [drm] *ERROR* This configuration is likely broken.
May 10 07:36:23 localhost.localdomain kernel: vmwgfx 0000:00:02.0: [drm] *ERROR* Please switch to a supported graphics device to avoid problems.
May 10 07:36:43 Ubuntu-Server login[959]: PAM unable to dlopen(pam_lastlog.so): /usr/lib/security/pam_lastlog.so: cannot open shared object file: No such file or directory
May 10 07:36:43 Ubuntu-Server login[959]: PAM adding faulty module: pam_lastlog.so
May 10 08:10:09 Ubuntu-Server kernel: EXT4-fs error (device loop0): __ext4_find_entry:1700: inode #2: comm quotaon: checksumming directory block 0
May 10 08:10:15 Ubuntu-Server kernel: EXT4-fs error (device loop0): __ext4_find_entry:1700: inode #2: comm quotaoff: checksumming directory block 0
May 13 13:35:52 Ubuntu-Server (python3)[20983]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:35:55 Ubuntu-Server (python3)[20984]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:35:58 Ubuntu-Server (python3)[20986]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:01 Ubuntu-Server (python3)[20989]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:05 Ubuntu-Server (python3)[20990]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:08 Ubuntu-Server (python3)[20991]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:11 Ubuntu-Server (python3)[20993]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:14 Ubuntu-Server (python3)[20995]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:18 Ubuntu-Server (python3)[20996]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:21 Ubuntu-Server (python3)[20997]: demo-web.service: Failed to determine user credentials: No such process
```

<details>
<summary><b>Read More</b></summary>
<br>

```
May 13 13:36:24 Ubuntu-Server (python3)[21007]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:27 Ubuntu-Server (python3)[21009]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:31 Ubuntu-Server (python3)[21010]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:34 Ubuntu-Server (python3)[21011]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:37 Ubuntu-Server (python3)[21012]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:40 Ubuntu-Server (python3)[21077]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:44 Ubuntu-Server (python3)[21150]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:47 Ubuntu-Server (python3)[21155]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:50 Ubuntu-Server (python3)[21158]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:53 Ubuntu-Server (python3)[21159]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:36:57 Ubuntu-Server (python3)[21160]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:00 Ubuntu-Server (python3)[21161]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:03 Ubuntu-Server (python3)[21162]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:06 Ubuntu-Server (python3)[21163]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:10 Ubuntu-Server (python3)[21164]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:13 Ubuntu-Server (python3)[21210]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:17 Ubuntu-Server (python3)[21215]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:20 Ubuntu-Server (python3)[21218]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:23 Ubuntu-Server (python3)[21219]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:26 Ubuntu-Server (python3)[21220]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:30 Ubuntu-Server (python3)[21221]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:33 Ubuntu-Server (python3)[21223]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:36 Ubuntu-Server (python3)[21224]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:39 Ubuntu-Server (python3)[21225]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:43 Ubuntu-Server (python3)[21228]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:46 Ubuntu-Server (python3)[21229]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:49 Ubuntu-Server (python3)[21230]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:52 Ubuntu-Server (python3)[21231]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:56 Ubuntu-Server (python3)[21232]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:37:59 Ubuntu-Server (python3)[21233]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:02 Ubuntu-Server (python3)[21234]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:06 Ubuntu-Server (python3)[21235]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:09 Ubuntu-Server (python3)[21237]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:12 Ubuntu-Server (python3)[21238]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:16 Ubuntu-Server (python3)[21239]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:19 Ubuntu-Server (python3)[21240]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:22 Ubuntu-Server (python3)[21241]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:25 Ubuntu-Server (python3)[21249]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:29 Ubuntu-Server (python3)[21250]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:32 Ubuntu-Server (python3)[21251]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:35 Ubuntu-Server (python3)[21252]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:38 Ubuntu-Server (python3)[21253]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:42 Ubuntu-Server (python3)[21254]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:45 Ubuntu-Server (python3)[21255]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:48 Ubuntu-Server (python3)[21256]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:51 Ubuntu-Server (python3)[21257]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:55 Ubuntu-Server (python3)[21258]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:38:58 Ubuntu-Server (python3)[21259]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:01 Ubuntu-Server (python3)[21260]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:04 Ubuntu-Server (python3)[21261]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:08 Ubuntu-Server (python3)[21262]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:11 Ubuntu-Server (python3)[21263]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:14 Ubuntu-Server (python3)[21264]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:17 Ubuntu-Server (python3)[21265]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:21 Ubuntu-Server (python3)[21266]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:24 Ubuntu-Server (python3)[21267]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:27 Ubuntu-Server (python3)[21268]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:30 Ubuntu-Server (python3)[21271]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:34 Ubuntu-Server (python3)[21272]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:37 Ubuntu-Server (python3)[21273]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:40 Ubuntu-Server (python3)[21274]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:43 Ubuntu-Server (python3)[21275]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:47 Ubuntu-Server (python3)[21278]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:50 Ubuntu-Server (python3)[21279]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:53 Ubuntu-Server (python3)[21280]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:39:56 Ubuntu-Server (python3)[21281]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:00 Ubuntu-Server (python3)[21286]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:03 Ubuntu-Server (python3)[21289]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:06 Ubuntu-Server (python3)[21290]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:09 Ubuntu-Server (python3)[21291]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:13 Ubuntu-Server (python3)[21292]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:16 Ubuntu-Server (python3)[21293]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:19 Ubuntu-Server (python3)[21294]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:22 Ubuntu-Server (python3)[21296]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:26 Ubuntu-Server (python3)[21297]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:29 Ubuntu-Server (python3)[21298]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:32 Ubuntu-Server (python3)[21299]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:35 Ubuntu-Server (python3)[21302]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:39 Ubuntu-Server (python3)[21303]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:42 Ubuntu-Server (python3)[21304]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:45 Ubuntu-Server (python3)[21305]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:48 Ubuntu-Server (python3)[21306]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:52 Ubuntu-Server (python3)[21307]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:55 Ubuntu-Server (python3)[21308]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:40:58 Ubuntu-Server (python3)[21309]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:41:01 Ubuntu-Server (python3)[21310]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:41:05 Ubuntu-Server (python3)[21311]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:41:08 Ubuntu-Server (python3)[21312]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:41:11 Ubuntu-Server (python3)[21313]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:41:14 Ubuntu-Server (python3)[21314]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:13 Ubuntu-Server (python3)[21493]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:16 Ubuntu-Server (python3)[21494]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:20 Ubuntu-Server (python3)[21495]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:23 Ubuntu-Server (python3)[21496]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:26 Ubuntu-Server (python3)[21499]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:29 Ubuntu-Server (python3)[21500]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:33 Ubuntu-Server (python3)[21501]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:36 Ubuntu-Server (python3)[21502]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:39 Ubuntu-Server (python3)[21504]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:42 Ubuntu-Server (python3)[21505]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:45 Ubuntu-Server (python3)[21506]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:48 Ubuntu-Server (python3)[21509]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:52 Ubuntu-Server (python3)[21510]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:55 Ubuntu-Server (python3)[21516]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:53:58 Ubuntu-Server (python3)[21517]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:01 Ubuntu-Server (python3)[21520]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:05 Ubuntu-Server (python3)[21521]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:08 Ubuntu-Server (python3)[21522]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:11 Ubuntu-Server (python3)[21525]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:14 Ubuntu-Server (python3)[21526]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:18 Ubuntu-Server (python3)[21527]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:21 Ubuntu-Server (python3)[21528]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:24 Ubuntu-Server (python3)[21529]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:27 Ubuntu-Server (python3)[21530]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:31 Ubuntu-Server (python3)[21531]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:34 Ubuntu-Server (python3)[21532]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:37 Ubuntu-Server (python3)[21534]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:41 Ubuntu-Server (python3)[21535]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:44 Ubuntu-Server (python3)[21536]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:47 Ubuntu-Server (python3)[21537]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:51 Ubuntu-Server (python3)[21538]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:54 Ubuntu-Server (python3)[21539]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:54:57 Ubuntu-Server (python3)[21540]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:00 Ubuntu-Server (python3)[21543]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:04 Ubuntu-Server (python3)[21548]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:07 Ubuntu-Server (python3)[21549]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:10 Ubuntu-Server (python3)[21552]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:13 Ubuntu-Server (python3)[21570]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:17 Ubuntu-Server (python3)[21618]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:20 Ubuntu-Server (python3)[21619]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:23 Ubuntu-Server (python3)[21621]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:26 Ubuntu-Server (python3)[21622]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:30 Ubuntu-Server (python3)[21623]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:33 Ubuntu-Server (python3)[21624]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:36 Ubuntu-Server (python3)[21625]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:40 Ubuntu-Server (python3)[21627]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:43 Ubuntu-Server (python3)[21630]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:46 Ubuntu-Server (python3)[21631]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:49 Ubuntu-Server (python3)[21632]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:53 Ubuntu-Server (python3)[21633]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:56 Ubuntu-Server (python3)[21634]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:55:59 Ubuntu-Server (python3)[21635]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:02 Ubuntu-Server (python3)[21636]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:05 Ubuntu-Server (python3)[21638]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:09 Ubuntu-Server (python3)[21642]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:12 Ubuntu-Server (python3)[21643]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:15 Ubuntu-Server (python3)[21644]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:18 Ubuntu-Server (python3)[21645]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:22 Ubuntu-Server (python3)[21646]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:25 Ubuntu-Server (python3)[21647]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:28 Ubuntu-Server (python3)[21648]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:31 Ubuntu-Server (python3)[21649]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:34 Ubuntu-Server (python3)[21654]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:38 Ubuntu-Server (python3)[21700]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:41 Ubuntu-Server (python3)[21701]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:44 Ubuntu-Server (python3)[21702]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:47 Ubuntu-Server (python3)[21707]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:51 Ubuntu-Server (python3)[21708]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:54 Ubuntu-Server (python3)[21709]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:56:57 Ubuntu-Server (python3)[21712]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:00 Ubuntu-Server (python3)[21713]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:04 Ubuntu-Server (python3)[21714]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:07 Ubuntu-Server (python3)[21716]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:10 Ubuntu-Server (python3)[21719]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:13 Ubuntu-Server (python3)[21720]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:17 Ubuntu-Server (python3)[21721]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:20 Ubuntu-Server (python3)[21726]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:23 Ubuntu-Server (python3)[21727]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:26 Ubuntu-Server (python3)[21729]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:30 Ubuntu-Server (python3)[21730]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:33 Ubuntu-Server (python3)[21731]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:36 Ubuntu-Server (python3)[21734]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:39 Ubuntu-Server (python3)[21735]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:42 Ubuntu-Server (python3)[21736]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:45 Ubuntu-Server (python3)[21737]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:48 Ubuntu-Server (python3)[21738]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:52 Ubuntu-Server (python3)[21739]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:55 Ubuntu-Server (python3)[21740]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:57:58 Ubuntu-Server (python3)[21741]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:01 Ubuntu-Server (python3)[21742]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:05 Ubuntu-Server (python3)[21743]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:08 Ubuntu-Server (python3)[21744]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:11 Ubuntu-Server (python3)[21745]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:14 Ubuntu-Server (python3)[21746]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:18 Ubuntu-Server (python3)[21747]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:21 Ubuntu-Server (python3)[21748]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:24 Ubuntu-Server (python3)[21750]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:27 Ubuntu-Server (python3)[21751]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:31 Ubuntu-Server (python3)[21752]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:34 Ubuntu-Server (python3)[21753]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:37 Ubuntu-Server (python3)[21754]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:40 Ubuntu-Server (python3)[21755]: demo-web.service: Failed to determine user credentials: No such process
May 13 13:58:44 Ubuntu-Server (python3)[21756]: demo-web.service: Failed to determine user credentials: No such process
```

</details>

### 3. Ikuti log secara real-time sambil memicu aktivitas

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo journalctl -u ssh -f
May 13 05:49:01 Ubuntu-Server systemd[1]: ssh.service: This usually indicates unclean termination of a previous run, or service implementation deficiencies.
May 13 05:49:01 Ubuntu-Server sshd[20657]: Server listening on 0.0.0.0 port 22.
May 13 05:49:01 Ubuntu-Server sshd[20657]: Server listening on :: port 22.
May 13 05:49:01 Ubuntu-Server systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
May 13 13:22:16 Ubuntu-Server sshd[20764]: Accepted password for praditadf from 10.0.2.2 port 60430 ssh2
May 13 13:22:16 Ubuntu-Server sshd[20764]: pam_unix(sshd:session): session opened for user praditadf(uid=1000) by praditadf(uid=0)
May 13 13:55:13 Ubuntu-Server sshd[21550]: Accepted password for praditadf from 10.0.2.2 port 54539 ssh2
May 13 13:55:13 Ubuntu-Server sshd[21550]: pam_unix(sshd:session): session opened for user praditadf(uid=1000) by praditadf(uid=0)
May 14 04:23:36 Ubuntu-Server sshd[22354]: Accepted password for praditadf from 10.0.2.2 port 63999 ssh2
May 14 04:23:36 Ubuntu-Server sshd[22354]: pam_unix(sshd:session): session opened for user praditadf(uid=1000) by praditadf(uid=0)
May 14 04:35:41 Ubuntu-Server sshd[22591]: Accepted password for praditadf from 10.0.2.2 port 63171 ssh2
May 14 04:35:41 Ubuntu-Server sshd[22591]: pam_unix(sshd:session): session opened for user praditadf(uid=1000) by praditadf(uid=0)
May 14 04:36:02 Ubuntu-Server sshd[22658]: Accepted password for praditadf from ::1 port 43320 ssh2
May 14 04:36:02 Ubuntu-Server sshd[22658]: pam_unix(sshd:session): session opened for user praditadf(uid=1000) by praditadf(uid=0)

praditadf@Ubuntu-Server:~$ ssh localhost
The authenticity of host 'localhost (::1)' can't be established.
ED25519 key fingerprint is SHA256:sy6qwNykC7jGyiJw+qdTGwB3MydkN5Xa+4IDmzZ6g88.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added 'localhost' (ED25519) to the list of known hosts.
praditadf@localhost's password:
Welcome to Ubuntu 24.04.4 LTS (GNU/Linux 6.8.0-111-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

 System information as of Thu May 14 04:35:41 AM UTC 2026

  System load:             0.0
  Usage of /:              11.0% of 29.36GB
  Memory usage:            13%
  Swap usage:              0%
  Processes:               150
  Users logged in:         1
  IPv4 address for enp0s3: 10.0.2.15
  IPv6 address for enp0s3: fd17:625c:f037:2:a00:27ff:febb:9bc3

 * Strictly confined Kubernetes makes edge and IoT secure. Learn how MicroK8s
   just raised the bar for easy, resilient and secure K8s cluster deployment.

   https://ubuntu.com/engage/secure-kubernetes-at-the-edge

Expanded Security Maintenance for Applications is not enabled.

0 updates can be applied immediately.

Enable ESM Apps to receive additional future security updates.
See https://ubuntu.com/esm or run: sudo pro status


Last login: Thu May 14 04:35:43 2026 from 10.0.2.2
```

### 4. Ekstrak log ke berkas untuk analisis

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ cd ~/lab-os/chapter10-services
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo journalctl -u ssh --since today --no-pager > log-ssh-hari-ini.txt
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ wc -l log-ssh-hari-ini.txt
6 log-ssh-hari-ini.txt
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ grep -i "error\|failed" log-ssh-hari-ini.txt | head -20
```

### Tantangan

Ekstrak semua log dengan prioritas error (-p err) dari 24 jam terakhir untuk layanan SSH, simpan ke berkas error-ssh-24jam.txt. Gunakan pipeline dari Bab 3 untuk menghitung total jumlah baris error dengan wc-1, lalu tampilkan 10 pesan error yang paling sering muncul menggunakan sort | uniq -c | sort -rn | head -10. Tuliskan perintah lengkap yang kamu gunakan.

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo journalctl -u ssh -p err --since "24 hours ago" --no-pager > error-ssh-24jam.txt
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ wc -l error-ssh-24jam.txt
1 error-ssh-24jam.txt
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ cat error-ssh-24jam.txt | sort | uniq -c | sort -rn | head -10
      1 -- No entries --
```

## Praktek 10.5 — Konfigurasi SSH Server

### 1. Periksa konfigurasi SSH saat ini

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo grep -n "^Port\|^#Port" /etc/ssh/sshd_config
23:#Port 22
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ ss -tlnp | grep ssh
```

### 2. Buat backup dan ubah port SSH

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup.lab12
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo sed -i 's/^#Port 22/Port 2222/' /etc/ssh/sshd_config
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ grep "^Port" /etc/ssh/sshd_config
Port 2222
```

### 3. Validasi konfigurasi dan restart layanan

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo sshd -t
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ echo "Kode keluar sshd -t: $?"
Kode keluar sshd -t: 0
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo systemctl restart ssh
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabled; preset: enabled)
     Active: active (running) since Thu 2026-05-14 04:58:58 UTC; 3s ago
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 23468 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 23470 (sshd)
      Tasks: 3 (limit: 4600)
     Memory: 5.8M (peak: 9.4M)
        CPU: 115ms
     CGroup: /system.slice/ssh.service
             ├─19498 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"
             ├─20657 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"
             └─23470 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"
```

### 4. Verifikasi port baru dengan ss

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo ss -tlnp | grep ssh
LISTEN 0      128          0.0.0.0:2222      0.0.0.0:*    users:(("sshd",pid=23722,fd=3))
LISTEN 0      4096         0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=20657,fd=3),("sshd",pid=19498,fd=3))
LISTEN 0      128             [::]:2222         [::]:*    users:(("sshd",pid=23722,fd=4))
LISTEN 0      4096            [::]:22           [::]:*    users:(("sshd",pid=20657,fd=4),("sshd",pid=19498,fd=4))
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo ss -tlnp | grep ssh > ~/lab-os/chapter10-services/bukti-port-ssh.txt
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ cat ~/lab-os/chapter10-services/bukti-port-ssh.txt
LISTEN 0      128          0.0.0.0:2222      0.0.0.0:*    users:(("sshd",pid=23722,fd=3))
LISTEN 0      4096         0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=20657,fd=3),("sshd",pid=19498,fd=3))
LISTEN 0      128             [::]:2222         [::]:*    users:(("sshd",pid=23722,fd=4))
LISTEN 0      4096            [::]:22           [::]:*    users:(("sshd",pid=20657,fd=4),("sshd",pid=19498,fd=4))
```

### 5. Kembalikan port SSH ke 22 setelah praktek

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo cp /etc/ssh/sshd_config.backup.lab12 /etc/ssh/sshd_config
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo sshd -t
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo systemctl restart ssh
Job for ssh.service failed because the control process exited with error code.
See "systemctl status ssh.service" and "journalctl -xeu ssh.service" for details.
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo ss -tlnp | grep ssh
LISTEN 0      4096         0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=20657,fd=3),("sshd",pid=19498,fd=3))
LISTEN 0      4096            [::]:22           [::]:*    users:(("sshd",pid=20657,fd=4),("sshd",pid=19498,fd=4))
```

### Tantangan

Ubah konfigurasi SSH untuk menambahkan dua pengaturan keamanan: PermitRootLogin no (larang login root langsung) dan MaxAuthTries 3 (maksimal tiga kali percobaan). Lakukan dengan urutan yang aman: backup, edit, validasi dengan sshd -t, reload. Verifikasi perubahan dengan grep -E "PermitRoot|MaxAuth" /etc/ssh/sshd_config. Kemudian periksa log SSH untuk memastikan tidak ada error setelah perubahan dengan journalctl -u ssh -n 20. Referensi Bab 2 untuk penggunaan ss dan Bab 9 untuk keamanan pengguna.

```
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup.keamanan
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ echo "PermitRootLogin no" | sudo tee -a /etc/ssh/sshd_config
PermitRootLogin no
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ echo "MaxAuthTries 3" | sudo tee -a /etc/ssh/sshd_config
MaxAuthTries 3
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo sshd -t
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabled; preset: enabled)
     Active: active (running) since Thu 2026-05-14 05:30:36 UTC; 5s ago
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 23836 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 23838 (sshd)
      Tasks: 1 (limit: 4600)
     Memory: 1.2M (peak: 1.5M)
        CPU: 140ms
     CGroup: /system.slice/ssh.service
             └─23838 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ grep -E "PermitRoot|MaxAuth" /etc/ssh/sshd_config
#PermitRootLogin prohibit-password
#MaxAuthTries 6
# the setting of "PermitRootLogin prohibit-password".
PermitRootLogin no
MaxAuthTries 3
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo journalctl -u ssh -n 20
May 14 05:27:23 Ubuntu-Server systemd[1]: ssh.service: This usually indicates unclean termination of a previous run, or service implementation deficiencies.
May 14 05:27:23 Ubuntu-Server systemd[1]: ssh.service: Found left-over process 20657 (sshd) in control group while starting unit. Ignoring.
May 14 05:27:23 Ubuntu-Server systemd[1]: ssh.service: This usually indicates unclean termination of a previous run, or service implementation deficiencies.
May 14 05:27:23 Ubuntu-Server systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
May 14 05:27:23 Ubuntu-Server systemd[1]: ssh.service: Found left-over process 19498 (sshd) in control group while starting unit. Ignoring.
May 14 05:27:23 Ubuntu-Server systemd[1]: ssh.service: This usually indicates unclean termination of a previous run, or service implementation deficiencies.
May 14 05:27:23 Ubuntu-Server systemd[1]: ssh.service: Found left-over process 20657 (sshd) in control group while starting unit. Ignoring.
May 14 05:27:23 Ubuntu-Server systemd[1]: ssh.service: This usually indicates unclean termination of a previous run, or service implementation deficiencies.
May 14 05:27:23 Ubuntu-Server sshd[23808]: error: Bind to port 22 on 0.0.0.0 failed: Address already in use.
May 14 05:27:23 Ubuntu-Server sshd[23808]: error: Bind to port 22 on :: failed: Address already in use.
May 14 05:27:23 Ubuntu-Server systemd[1]: ssh.service: Main process exited, code=exited, status=255/EXCEPTION
May 14 05:27:23 Ubuntu-Server sshd[23808]: fatal: Cannot bind any address.
May 14 05:27:23 Ubuntu-Server systemd[1]: ssh.service: Failed with result 'exit-code'.
May 14 05:27:23 Ubuntu-Server systemd[1]: ssh.service: Unit process 19498 (sshd) remains running after unit stopped.
May 14 05:27:23 Ubuntu-Server systemd[1]: ssh.service: Unit process 20657 (sshd) remains running after unit stopped.
May 14 05:27:23 Ubuntu-Server systemd[1]: Failed to start ssh.service - OpenBSD Secure Shell server.
May 14 05:30:36 Ubuntu-Server systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
May 14 05:30:36 Ubuntu-Server sshd[23838]: Server listening on 0.0.0.0 port 22.
May 14 05:30:36 Ubuntu-Server sshd[23838]: Server listening on :: port 22.
May 14 05:30:36 Ubuntu-Server systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo cp /etc/ssh/sshd_config.backup.keamanan /etc/ssh/sshd_config
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo sshd -t
praditadf@Ubuntu-Server:~/lab-os/chapter10-services$ sudo systemctl reload ssh
```

# Latihan

## Latihan 10.1 — Audit Layanan dan Analisis Boot

1. Jalankan systemctl list-units -type=service -state running dan catat semua layanan aktif. Pilih tiga layanan yang kamu kenal, periksa status masing-masing dengan systemctl status, dan jelaskan fungsinya.

```
praditadf@Ubuntu-Server:~$ systemctl list-units --type=service --state=running
  UNIT                        LOAD   ACTIVE SUB     DESCRIPTION
  cron.service                loaded active running Regular background program processing daemon
  dbus.service                loaded active running D-Bus System Message Bus
  fwupd.service               loaded active running Firmware update daemon
  getty@tty1.service          loaded active running Getty on tty1
  ModemManager.service        loaded active running Modem Manager
  multipathd.service          loaded active running Device-Mapper Multipath Device Controller
  packagekit.service          loaded active running PackageKit Daemon
  polkit.service              loaded active running Authorization Manager
  rsyslog.service             loaded active running System Logging Service
  ssh.service                 loaded active running OpenBSD Secure Shell server
  systemd-journald.service    loaded active running Journal Service
  systemd-logind.service      loaded active running User Login Management
  systemd-networkd.service    loaded active running Network Configuration
  systemd-resolved.service    loaded active running Network Name Resolution
  systemd-timesyncd.service   loaded active running Network Time Synchronization
  systemd-udevd.service       loaded active running Rule-based Manager for Device Events and Files
  udisks2.service             loaded active running Disk Manager
  unattended-upgrades.service loaded active running Unattended Upgrades Shutdown
  upower.service              loaded active running Daemon for power management
  user@1000.service           loaded active running User Manager for UID 1000

Legend: LOAD   → Reflects whether the unit definition was properly loaded.
        ACTIVE → The high-level unit activation state, i.e. generalization of SUB.
        SUB    → The low-level unit activation state, values depend on unit type.

20 loaded units listed.

praditadf@Ubuntu-Server:~$ systemctl status ssh.service
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabled; preset: enabled)
     Active: active (running) since Thu 2026-05-14 05:30:36 UTC; 4 days ago
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 23836 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
    Process: 23863 ExecReload=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
    Process: 23865 ExecReload=/bin/kill -HUP $MAINPID (code=exited, status=0/SUCCESS)
   Main PID: 23838 (sshd)
      Tasks: 1 (limit: 4600)
     Memory: 3.0M (peak: 4.2M)
        CPU: 574ms
     CGroup: /system.slice/ssh.service
             └─23838 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"

praditadf@Ubuntu-Server:~$ systemctl status upower.service
● upower.service - Daemon for power management
     Loaded: loaded (/usr/lib/systemd/system/upower.service; disabled; preset: enabled)
     Active: active (running) since Sun 2026-05-10 08:54:20 UTC; 1 week 1 day ago
       Docs: man:upowerd(8)
   Main PID: 18702 (upowerd)
      Tasks: 4 (limit: 4600)
     Memory: 4.0M (peak: 4.6M)
        CPU: 9.951s
     CGroup: /system.slice/upower.service
             └─18702 /usr/libexec/upowerd

praditadf@Ubuntu-Server:~$ systemctl status udisk2.service
Unit udisk2.service could not be found.
praditadf@Ubuntu-Server:~$ systemctl status udisks2.service
● udisks2.service - Disk Manager
     Loaded: loaded (/usr/lib/systemd/system/udisks2.service; enabled; preset: enabled)
     Active: active (running) since Sun 2026-05-10 07:39:56 UTC; 1 week 1 day ago
       Docs: man:udisks(8)
   Main PID: 16607 (udisksd)
      Tasks: 6 (limit: 4600)
     Memory: 2.5M (peak: 3.0M)
        CPU: 2.190s
     CGroup: /system.slice/udisks2.service
             └─16607 /usr/libexec/udisks2/udisksd
```

2. Jalankan systemd-analyze blame dan identifikasi lima layanan dengan waktu inisialisasi terlama. Tampilkan hasilnya menggunakan pipeline: systemd-analyze blame | head -5.

```
praditadf@Ubuntu-Server:~$ systemd-analyze blame | head -5
1min 4.497s vboxadd.service
    28.377s apt-daily.service
     7.436s fwupd-refresh.service
     4.607s cloud-config.service
     3.898s motd-news.service
```

3. Jalankan systemctl -failed dan dokumentasikan hasilnya. Jika ada layanan yang gagal, cari tahu penyebabnya dengan journalctl -u nama-layanan -n 30.

```
praditadf@Ubuntu-Server:~$ systemctl --failed
  UNIT LOAD ACTIVE SUB DESCRIPTION

0 loaded units listed.
```

## Latihan 10.2 — Layanan Kustom dengan Restart Otomatis

1. Buat skrip Bash (referensi Bab 7) bernama monitor-disk. sh yang setiap 30 detik menuliskan penggunaan disk ke berkas log. Gunakan df -h dan date.

```

```

2. Buat berkas unit /etc/systemd/system/monitor-disk. service untuk menjalankan skrip tersebut dengan konfigurasi: Restart=always, RestartSec $=5~s$, dan berjalan sebagai pengguna kamu sendiri.

```

```

3. Aktifkan dan jalankan layanan. Verifikasi dengan systemctl status dan pastikan log masuk ke journal.

```

```

4. Simulasikan crash dengan membunuh proses secara paksa (kill -9), tunggu 10 detik, dan verifikasi bahwa layanan hidup kembali secara otomatis.

```

```

5. Bersihkan: nonaktifkan layanan dan hapus berkas unit setelah selesai.

```

```

## Latihan 10.3 — Investigasi Log dan Keamanan SSH

1. Gunakan journalctl -b-perr untuk menemukan semua error sejak boot terakhir. Simpan hasilnya ke berkas dan hitung jumlah baris dengan wc -1.

```

```

2. Lakukan tiga perubahan keamanan pada /etc/ssh/sshd_config: tambahkan PermitRootLogin no, MaxAuthTries 3, dan LoginGraceTime 30. Ikuti alur aman: backup, edit, validasi sshd -t, reload.

```

```

3. Setelah reload, verifikasi tiga hal: layanan masih berjalan (systemctl status ssh), port masih mendengarkan (ss -tlnp | grep ssh), dan konfigurasi baru terbaca (grep -Е "PermitRoot | MaxAuth | GraceTime" /etc/ssh/sshd_config).

```

```

4. Kembalikan konfigurasi SSH ke kondisi semula menggunakan berkas backup.

```

```
