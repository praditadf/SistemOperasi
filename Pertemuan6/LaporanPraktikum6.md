# Manajemen Proses

## Praktikum 6.1 — Melihat Proses dan Thread

### 1. Tampilkan semua proses yang berjalan

```
praditadf@praditadf-VirtualBox:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  1.2  0.3  23636 15016 ?        Ss   20:07   0:03 /sbin/init splash
root           2  0.0  0.0      0     0 ?        S    20:07   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    20:07   0:00 [pool_workqueue_release]
root           4  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-rcu_gp]
root           5  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-sync_wq]
root           6  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-kvfree_rcu_reclaim]
root           7  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-slub_flushwq]
root           8  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-netns]
root           9  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/0:0-rcu_gp]
root          10  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/0:1-cgroup_release]
root          11  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/0:0H-kblockd]
root          12  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u8:0-ipv6_addrconf]
root          13  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-mm_percpu_wq]
```

<details>
<summary><b>Read More</b></summary>
<br>

```
root          14  0.1  0.0      0     0 ?        S    20:07   0:00 [ksoftirqd/0]
root          15  0.3  0.0      0     0 ?        I    20:07   0:00 [rcu_preempt]
root          16  0.0  0.0      0     0 ?        S    20:07   0:00 [rcu_exp_par_gp_kthread_worker/0]
root          17  0.0  0.0      0     0 ?        S    20:07   0:00 [rcu_exp_gp_kthread_worker]
root          18  0.0  0.0      0     0 ?        S    20:07   0:00 [migration/0]
root          19  0.0  0.0      0     0 ?        S    20:07   0:00 [idle_inject/0]
root          20  0.0  0.0      0     0 ?        S    20:07   0:00 [cpuhp/0]
root          21  0.0  0.0      0     0 ?        S    20:07   0:00 [cpuhp/1]
root          22  0.0  0.0      0     0 ?        S    20:07   0:00 [idle_inject/1]
root          23  0.2  0.0      0     0 ?        S    20:07   0:00 [migration/1]
root          24  0.4  0.0      0     0 ?        S    20:07   0:01 [ksoftirqd/1]
root          25  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/1:0-cgroup_free]
root          26  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/1:0H-events_highpri]
root          27  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:0-loop13]
root          28  0.3  0.0      0     0 ?        I    20:07   0:00 [kworker/u10:0-loop21]
root          29  0.0  0.0      0     0 ?        S    20:07   0:00 [kdevtmpfs]
root          30  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-inet_frag_wq]
root          31  0.0  0.0      0     0 ?        I    20:07   0:00 [rcu_tasks_kthread]
root          32  0.0  0.0      0     0 ?        I    20:07   0:00 [rcu_tasks_rude_kthread]
root          33  0.0  0.0      0     0 ?        I    20:07   0:00 [rcu_tasks_trace_kthread]
root          34  0.0  0.0      0     0 ?        S    20:07   0:00 [kauditd]
root          35  0.0  0.0      0     0 ?        S    20:07   0:00 [khungtaskd]
root          36  0.0  0.0      0     0 ?        S    20:07   0:00 [oom_reaper]
root          37  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u10:1-events_unbound]
root          38  0.4  0.0      0     0 ?        I    20:07   0:01 [kworker/u10:2-events_unbound]
root          39  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-writeback]
root          40  0.0  0.0      0     0 ?        S    20:07   0:00 [kcompactd0]
root          41  0.0  0.0      0     0 ?        SN   20:07   0:00 [ksmd]
root          42  0.0  0.0      0     0 ?        SN   20:07   0:00 [khugepaged]
root          43  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-kblockd]
root          44  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-blkcg_punt_bio]
root          45  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-kintegrityd]
root          46  0.0  0.0      0     0 ?        S    20:07   0:00 [irq/9-acpi]
root          47  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/1:1-cgroup_release]
root          48  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-tpm_dev_wq]
root          49  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-ata_sff]
root          50  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-md]
root          51  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-md_bitmap]
root          52  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-edac-poller]
root          53  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-devfreq_wq]
root          54  0.0  0.0      0     0 ?        S    20:07   0:00 [watchdogd]
root          55  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-quota_events_unbound]
root          56  0.1  0.0      0     0 ?        I<   20:07   0:00 [kworker/1:1H-kblockd]
root          57  0.1  0.0      0     0 ?        S    20:07   0:00 [kswapd0]
root          58  0.0  0.0      0     0 ?        S    20:07   0:00 [ecryptfs-kthread]
root          59  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-kthrotld]
root          60  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-acpi_thermal_pm]
root          61  0.2  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:1-flush-8:0]
root          62  0.2  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:2-ext4-rsv-conversion]
root          63  0.0  0.0      0     0 ?        S    20:07   0:00 [scsi_eh_0]
root          64  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-scsi_tmf_0]
root          65  0.0  0.0      0     0 ?        S    20:07   0:00 [scsi_eh_1]
root          66  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-scsi_tmf_1]
root          67  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:3-loop8]
root          68  0.1  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:4-ext4-rsv-conversion]
root          69  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/0:1H-kblockd]
root          70  0.1  0.0      0     0 ?        I    20:07   0:00 [kworker/0:2-events]
root          71  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-mld]
root          72  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-ipv6_addrconf]
root          73  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u8:1-ipv6_addrconf]
root          74  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-kstrp]
root          76  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/u11:0]
root          77  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/u12:0]
root          78  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/u13:0-ttm]
root          89  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-charger_manager]
root         137  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/1:2-events]
root         139  0.0  0.0      0     0 ?        S    20:07   0:00 [scsi_eh_2]
root         140  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-scsi_tmf_2]
root         195  0.0  0.0      0     0 ?        S    20:07   0:00 [jbd2/sda2-8]
root         196  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-ext4-rsv-conversion]
root         244  0.3  0.4  42664 17268 ?        S<s  20:07   0:00 /usr/lib/systemd/systemd-journald
root         272  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/0:3-cgroup_free]
root         312  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u10:3-loop11]
root         326  0.1  0.2  30180  8328 ?        Ss   20:07   0:00 /usr/lib/systemd/systemd-udevd
root         377  0.0  0.0      0     0 ?        S    20:07   0:00 [psimon]
systemd+     416  0.0  0.1  17572  7800 ?        Ss   20:07   0:00 /usr/lib/systemd/systemd-oomd
systemd+     419  0.1  0.3  21860 13896 ?        Ss   20:07   0:00 /usr/lib/systemd/systemd-resolved
systemd+     421  0.0  0.2  91060  8068 ?        Ssl  20:07   0:00 /usr/lib/systemd/systemd-timesyncd
root         581  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:5-loop13]
root         582  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:6-flush-8:0]
root         585  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u10:4-loop20]
root         586  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u10:5-events_power_efficient]
root         589  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u10:6-events_unbound]
root         591  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:7-writeback]
root         599  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:8-loop14]
root         600  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:9-loop12]
root         613  0.0  0.0      0     0 ?        S    20:07   0:00 [irq/18-vmwgfx]
root         615  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-ttm]
root         616  0.0  0.0  16964  2428 ?        Ss   20:07   0:00 /usr/sbin/anacron -d -q -s
avahi        620  0.0  0.1   8676  4776 ?        Ss   20:07   0:00 avahi-daemon: running [praditadf-VirtualBox.local]
message+     621  0.5  0.1  12208  7392 ?        Ss   20:07   0:01 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --s
gnome-r+     625  0.1  0.4 439092 16784 ?        Ssl  20:07   0:00 /usr/libexec/gnome-remote-desktop-daemon --system
polkitd      645  0.4  0.2 384604 11384 ?        Ssl  20:07   0:01 /usr/lib/polkit-1/polkitd --no-debug
root         657  0.0  0.1 322052  7592 ?        Ssl  20:07   0:00 /usr/libexec/power-profiles-daemon
root         668  0.7  1.0 1849680 42196 ?       Ssl  20:07   0:01 /usr/lib/snapd/snapd
root         672  0.1  0.2 321968  8228 ?        Ssl  20:07   0:00 /usr/libexec/accounts-daemon
root         675  0.0  0.0  18100  3016 ?        Ss   20:07   0:00 /usr/sbin/cron -f -P
root         691  0.0  0.1 318560  7316 ?        Ssl  20:07   0:00 /usr/libexec/switcheroo-control
root         718  0.1  0.2  18176  9180 ?        Ss   20:07   0:00 /usr/lib/systemd/systemd-logind
root         724  0.1  0.3 469736 14700 ?        Ssl  20:07   0:00 /usr/libexec/udisks2/udisksd
syslog       749  0.1  0.1 222572  6320 ?        Ssl  20:07   0:00 /usr/sbin/rsyslogd -n -iNONE
avahi        762  0.0  0.0   8488  1528 ?        S    20:07   0:00 avahi-daemon: chroot helper
root         778  0.1  0.4 345172 19976 ?        Ssl  20:07   0:00 /usr/sbin/NetworkManager --no-daemon
root         787  0.0  0.1  17392  6776 ?        Ss   20:07   0:00 /usr/sbin/wpa_supplicant -u -s -O DIR=/run/wpa_supplicant GROUP=netdev
root         872  0.2  0.0      0     0 ?        I<   20:07   0:00 [kworker/0:2H-kblockd]
root         874  0.0  0.3 392108 13400 ?        Ssl  20:07   0:00 /usr/sbin/ModemManager
root        1215  0.0  0.3  47072 12496 ?        Ss   20:07   0:00 /usr/sbin/cupsd -l
root        1222  0.0  0.5 120928 23404 ?        Ssl  20:07   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for
root        1226  0.0  0.0      0     0 ?        I    20:07   0:00 [kworker/0:4-events]
root        1235  0.0  0.2 323500  9604 ?        Ssl  20:07   0:00 /usr/sbin/gdm3
cups-br+    1239  0.0  0.5 268500 20572 ?        Ssl  20:07   0:00 /usr/sbin/cups-browsed
kernoops    1245  0.0  0.0  12752  2404 ?        Ss   20:07   0:00 /usr/sbin/kerneloops --test
kernoops    1249  0.0  0.0  12752  2344 ?        Ss   20:07   0:00 /usr/sbin/kerneloops
root        1260  0.0  0.0      0     0 ?        S    20:07   0:00 [psimon]
rtkit       1316  0.0  0.0  22948  3540 ?        SNsl 20:07   0:00 /usr/libexec/rtkit-daemon
colord      1428  0.0  0.3 328736 14896 ?        Ssl  20:07   0:00 /usr/libexec/colord
root        1467  0.0  0.5 383880 21296 ?        Ssl  20:07   0:00 /usr/libexec/packagekitd
root        1468  0.0  0.2 325352  9352 ?        Ssl  20:07   0:00 /usr/libexec/upowerd
root        1762  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/u12:1-ttm]
root        1763  0.0  0.0      0     0 ?        I<   20:07   0:00 [kworker/u13:1]
root        1793  0.0  0.2 251264 10844 ?        Sl   20:07   0:00 gdm-session-worker [pam/gdm-password]
pradita+    1808  0.4  0.3  21280 12784 ?        Ss   20:08   0:00 /usr/lib/systemd/systemd --user
pradita+    1817  0.0  0.0  21472  3672 ?        S    20:08   0:00 (sd-pam)
pradita+    1830  0.2  0.3 124044 14524 ?        S<sl 20:08   0:00 /usr/bin/pipewire
pradita+    1843  0.0  0.1 106412  6252 ?        Ssl  20:08   0:00 /usr/bin/pipewire -c filter-chain.conf
pradita+    1846  0.1  0.4 415576 19128 ?        S<sl 20:08   0:00 /usr/bin/wireplumber
pradita+    1847  0.1  0.4 124472 17560 ?        S<Lsl 20:08   0:00 /usr/bin/pipewire-pulse
pradita+    1848  0.5  0.1  10932  6784 ?        Ss   20:08   0:01 /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activ
pradita+    1849  0.0  0.2 325192 10532 ?        SLsl 20:08   0:00 /usr/bin/gnome-keyring-daemon --foreground --components=pkcs11,secrets --control-direc
pradita+    1892  0.0  0.1 693732  7864 ?        Ssl  20:08   0:00 /usr/libexec/xdg-document-portal
pradita+    1900  0.0  0.1 244344  6392 tty2     Ssl+ 20:08   0:00 /usr/libexec/gdm-wayland-session env GNOME_SHELL_SESSION_MODE=ubuntu /usr/bin/gnome-se
pradita+    1919  0.0  0.4 306912 16892 tty2     Sl+  20:08   0:00 /usr/libexec/gnome-session-binary --session=ubuntu
pradita+    1930  0.0  0.1 317984  6360 ?        Ssl  20:08   0:00 /usr/libexec/xdg-permission-store
root        1953  0.0  0.0   2712  2096 ?        Ss   20:08   0:00 fusermount3 -o rw,nosuid,nodev,fsname=portal,auto_unmount,subtype=portal -- /run/user/
pradita+    1984  0.0  0.1 162660  7156 ?        Ssl  20:08   0:00 /usr/libexec/gcr-ssh-agent --base-dir /run/user/1000/gcr
pradita+    1986  0.0  0.1 100224  5788 ?        Ssl  20:08   0:00 /usr/libexec/gnome-session-ctl --monitor
pradita+    1999  0.0  0.2 322952  8240 ?        Ssl  20:08   0:00 /usr/libexec/gvfsd
pradita+    2017  0.0  0.1 468384  7352 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-fuse /run/user/1000/gvfs -f
pradita+    2019  0.1  0.4 742172 18888 ?        Ssl  20:08   0:00 /usr/libexec/gnome-session-binary --systemd-service --session=ubuntu
pradita+    2067 12.4 11.9 4064616 477196 ?      Ssl  20:08   0:26 /usr/bin/gnome-shell
pradita+    2068  0.0  0.2 382952  8180 ?        Sl   20:08   0:00 /usr/libexec/at-spi-bus-launcher --launch-immediately
pradita+    2084  0.0  0.1   9488  5348 ?        S    20:08   0:00 /usr/bin/dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibility.conf --no
pradita+    2137  0.0  0.1 236076  7800 ?        Sl   20:08   0:00 /usr/libexec/at-spi2-registryd --use-gnome-session
pradita+    2155  0.0  0.4 654792 18180 ?        Sl   20:08   0:00 /usr/libexec/gnome-shell-calendar-server
pradita+    2162  0.1  1.0 604016 43168 ?        Ssl  20:08   0:00 /usr/libexec/evolution-source-registry
pradita+    2173  0.0  0.6 2593560 27328 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.Shell.Notifications
pradita+    2183  0.1  0.2 395920 10996 ?        Ssl  20:08   0:00 /usr/bin/ibus-daemon --panel disable
pradita+    2184  0.0  0.1 392200  6956 ?        Ssl  20:08   0:00 /usr/libexec/gsd-a11y-settings
pradita+    2185  0.0  0.5 423400 21356 ?        Ssl  20:08   0:00 /usr/libexec/gsd-color
pradita+    2186  0.0  0.3 440356 12632 ?        Ssl  20:08   0:00 /usr/libexec/gsd-datetime
pradita+    2187  0.0  0.2 467552  8240 ?        Ssl  20:08   0:00 /usr/libexec/gsd-housekeeping
pradita+    2188  0.0  0.5 422256 20840 ?        Ssl  20:08   0:00 /usr/libexec/gsd-keyboard
pradita+    2189  0.1  0.6 752112 26464 ?        Ssl  20:08   0:00 /usr/libexec/gsd-media-keys
pradita+    2191  0.0  0.6 534024 25352 ?        Ssl  20:08   0:00 /usr/libexec/gsd-power
pradita+    2192  0.0  0.3 332436 12088 ?        Ssl  20:08   0:00 /usr/libexec/gsd-print-notifications
pradita+    2193  0.0  0.1 539760  6856 ?        Ssl  20:08   0:00 /usr/libexec/gsd-rfkill
pradita+    2194  0.0  0.1 318236  6592 ?        Ssl  20:08   0:00 /usr/libexec/gsd-screensaver-proxy
pradita+    2195  0.0  0.3 551872 12080 ?        Ssl  20:08   0:00 /usr/libexec/gsd-sharing
pradita+    2196  0.0  0.2 468232  8432 ?        Ssl  20:08   0:00 /usr/libexec/gsd-smartcard
pradita+    2197  0.0  0.2 402316 10132 ?        Ssl  20:08   0:00 /usr/libexec/gsd-sound
pradita+    2198  0.1  0.5 496964 21600 ?        Ssl  20:08   0:00 /usr/libexec/gsd-wacom
pradita+    2202  0.0  0.6 555360 24884 ?        Sl   20:08   0:00 /usr/libexec/goa-daemon
pradita+    2217  0.1  1.5 836800 61400 ?        Sl   20:08   0:00 /usr/libexec/evolution-data-server/evolution-alarm-notify
pradita+    2219  0.0  0.1 305500  7804 ?        Sl   20:08   0:00 /usr/libexec/gsd-disk-utility-notify
pradita+    2328  0.0  0.6 907600 25004 ?        Ssl  20:08   0:00 /usr/libexec/evolution-calendar-factory
pradita+    2348  0.0  0.1 319144  7472 ?        Sl   20:08   0:00 /usr/libexec/ibus-dconf
pradita+    2357  1.4  0.7 431972 30580 ?        Sl   20:08   0:03 /usr/libexec/ibus-extension-gtk3
pradita+    2373  0.0  0.3 424916 15388 ?        Sl   20:08   0:00 /usr/libexec/gsd-printer
pradita+    2383  0.0  0.1 319100  7464 ?        Sl   20:08   0:00 /usr/libexec/ibus-portal
pradita+    2398  0.0  0.2 397800  9640 ?        Sl   20:08   0:00 /usr/libexec/goa-identity-service
pradita+    2403  0.0  0.2 398000 11080 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-udisks2-volume-monitor
pradita+    2406  0.0  0.3  39140 12100 ?        Ss   20:08   0:00 /snap/snapd-desktop-integration/343/usr/bin/snapd-desktop-integration
pradita+    2456  0.0  0.7 834144 30760 ?        Ssl  20:08   0:00 /usr/libexec/evolution-addressbook-factory
pradita+    2466  0.0  0.1 318448  6856 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-goa-volume-monitor
pradita+    2485  0.0  0.2 398056  8252 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-afc-volume-monitor
pradita+    2500  0.1  0.7 429420 29908 ?        Sl   20:08   0:00 /snap/snapd-desktop-integration/343/usr/bin/snapd-desktop-integration
pradita+    2501  0.0  0.1 318468  6732 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-mtp-volume-monitor
pradita+    2515  0.0  0.1 319436  7284 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-gphoto2-volume-monitor
pradita+    2540  0.0  0.1 245444  7692 ?        Sl   20:08   0:00 /usr/libexec/ibus-engine-simple
pradita+    2568  0.0  0.1 230252  6132 ?        Ssl  20:08   0:00 /usr/libexec/dconf-service
pradita+    2592  0.0  0.6 2536140 27300 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.ScreenSaver
pradita+    2606  0.0  0.2 544384  9356 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-trash --spawner :1.18 /org/gtk/gvfs/exec_spaw/0
pradita+    2624  0.1  0.5 743088 23924 ?        SNsl 20:08   0:00 /usr/libexec/tracker-miner-fs-3
pradita+    2625  0.1  0.3 710292 14864 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal
pradita+    2635  0.1  1.0 852300 42100 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gnome
pradita+    2676  0.4  1.6 2820888 67092 ?       Sl   20:08   0:01 gjs /usr/share/gnome-shell/extensions/ding@rastersoft.com/app/ding.js -E -P /usr/share
pradita+    2712  0.1  0.6 428252 27024 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gtk
pradita+    2718  0.0  0.1 244948  6708 ?        Ssl  20:08   0:00 /usr/libexec/gvfsd-metadata
root        2768  0.0  0.0      0     0 ?        I    20:08   0:00 [kworker/1:3-events]
pradita+    2888  0.4  1.5 713072 61760 ?        Ssl  20:08   0:00 /usr/libexec/gnome-terminal-server
pradita+    2894  0.0  1.7 245008 68916 ?        S    20:08   0:00 /usr/bin/Xwayland :0 -rootless -noreset -accessx -core -auth /run/user/1000/.mutter-Xw
pradita+    2898  0.1  2.1 650968 84916 ?        Ssl  20:08   0:00 /usr/libexec/gsd-xsettings
pradita+    2920  0.0  0.6 275544 24692 ?        Sl   20:08   0:00 /usr/libexec/ibus-x11
pradita+    2925  0.1  2.5 1128036 104112 ?      Sl   20:08   0:00 /usr/libexec/mutter-x11-frames
pradita+    2929  0.0  0.1  19936  5696 pts/0    Ss   20:08   0:00 bash
pradita+    2956 18.0 13.6 3487756 546152 ?      Sl   20:08   0:34 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    3015  0.0  0.0 149172  2888 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/crashhelper 2956 9 /tmp/ 11
pradita+    3086  0.0  0.8 443020 35696 ?        S    20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -ipcHandle 0 -signalPipe 1 -in
pradita+    3093  0.0  0.9 456456 39588 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20260309231353 
pradita+    3115  0.5  2.9 2601820 119592 ?      Sl   20:08   0:01 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:3
pradita+    3123  0.1  1.1 589448 46748 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20260309231353 
pradita+    3170  0.0  0.6 1691764 25600 ?       Sl   20:08   0:00 /usr/bin/snap userd
pradita+    3322  0.4  2.5 2612844 102204 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:3
pradita+    3517  4.8  7.2 2840924 288980 ?      Sl   20:08   0:08 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:4
pradita+    3734  0.0  0.9 456436 39380 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20260309231353 
pradita+    3744  2.0  7.5 7040748 302224 ?      Sl   20:08   0:03 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:4
pradita+    3745  0.2  1.7 2568148 71176 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:4
pradita+    3927  0.2  1.7 2568148 71308 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:4
pradita+    3973  0.2  0.6 575936 27368 ?        Sl   20:09   0:00 /usr/bin/update-notifier
root        4035  0.0  0.0      0     0 ?        I<   20:09   0:00 [kworker/1:2H]
pradita+    4085  2.7  0.2 128568  9552 ?        Ssl  20:11   0:00 /usr/bin/speech-dispatcher -s -t 0
pradita+    4097  0.7  0.0      0     0 ?        Z    20:11   0:00 [sd_espeak-ng-mb] <defunct>
pradita+    4100  0.1  0.2 116052 10292 ?        Sl   20:11   0:00 /usr/lib/speech-dispatcher-modules/sd_espeak-ng /etc/speech-dispatcher/modules/espeak-
pradita+    4103  0.0  0.1 162700  6472 ?        Sl   20:11   0:00 /usr/lib/speech-dispatcher-modules/sd_dummy /etc/speech-dispatcher/modules/dummy.conf
pradita+    4106  0.0  0.0   5676  2764 ?        S    20:11   0:00 /usr/lib/speech-dispatcher-modules/sd_openjtalk /etc/speech-dispatcher/modules/openjta
pradita+    4118  0.8  1.7 2568148 70408 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:4
pradita+    4141 33.3  0.1  22428  4884 pts/0    R+   20:11   0:00 ps aux
```

</details>

### 2. Tampilkan proses beserta thread-nya, dapat dilihat pada kolom LWP (Light-Weight Process ID)

```
praditadf@praditadf-VirtualBox:~$ ps aux -L
USER         PID     LWP %CPU NLWP %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1       1  1.1    1  0.3  23636 15016 ?        Ss   20:07   0:04 /sbin/init splash
root           2       2  0.0    1  0.0      0     0 ?        S    20:07   0:00 [kthreadd]
root           3       3  0.0    1  0.0      0     0 ?        S    20:07   0:00 [pool_workqueue_release]
root           4       4  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-rcu_gp]
root           5       5  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-sync_wq]
root           6       6  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-kvfree_rcu_reclaim]
root           7       7  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-slub_flushwq]
root           8       8  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-netns]
root          11      11  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/0:0H-kblockd]
root          12      12  0.0    1  0.0      0     0 ?        I    20:07   0:00 [kworker/u8:0-ipv6_addrconf]
root          13      13  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-mm_percpu_wq]
root          14      14  0.1    1  0.0      0     0 ?        S    20:07   0:00 [ksoftirqd/0]
root          15      15  0.3    1  0.0      0     0 ?        I    20:07   0:01 [rcu_preempt]
```

<details>
<summary><b>Read More</b></summary>
<br>

```
root          16      16  0.0    1  0.0      0     0 ?        S    20:07   0:00 [rcu_exp_par_gp_kthread_worker/0]
root          17      17  0.0    1  0.0      0     0 ?        S    20:07   0:00 [rcu_exp_gp_kthread_worker]
root          18      18  0.0    1  0.0      0     0 ?        S    20:07   0:00 [migration/0]
root          19      19  0.0    1  0.0      0     0 ?        S    20:07   0:00 [idle_inject/0]
root          20      20  0.0    1  0.0      0     0 ?        S    20:07   0:00 [cpuhp/0]
root          21      21  0.0    1  0.0      0     0 ?        S    20:07   0:00 [cpuhp/1]
root          22      22  0.0    1  0.0      0     0 ?        S    20:07   0:00 [idle_inject/1]
root          23      23  0.1    1  0.0      0     0 ?        S    20:07   0:00 [migration/1]
root          24      24  0.5    1  0.0      0     0 ?        S    20:07   0:02 [ksoftirqd/1]
root          25      25  0.0    1  0.0      0     0 ?        I    20:07   0:00 [kworker/1:0-cgroup_free]
root          26      26  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/1:0H-events_highpri]
root          27      27  0.0    1  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:0-ext4-rsv-conversion]
root          29      29  0.0    1  0.0      0     0 ?        S    20:07   0:00 [kdevtmpfs]
root          30      30  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-inet_frag_wq]
root          31      31  0.0    1  0.0      0     0 ?        I    20:07   0:00 [rcu_tasks_kthread]
root          32      32  0.0    1  0.0      0     0 ?        I    20:07   0:00 [rcu_tasks_rude_kthread]
root          33      33  0.0    1  0.0      0     0 ?        I    20:07   0:00 [rcu_tasks_trace_kthread]
root          34      34  0.0    1  0.0      0     0 ?        S    20:07   0:00 [kauditd]
root          35      35  0.0    1  0.0      0     0 ?        S    20:07   0:00 [khungtaskd]
root          36      36  0.0    1  0.0      0     0 ?        S    20:07   0:00 [oom_reaper]
root          37      37  0.6    1  0.0      0     0 ?        I    20:07   0:02 [kworker/u10:1-events_unbound]
root          38      38  0.6    1  0.0      0     0 ?        I    20:07   0:02 [kworker/u10:2-events_power_efficient]
root          39      39  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-writeback]
root          40      40  0.0    1  0.0      0     0 ?        S    20:07   0:00 [kcompactd0]
root          41      41  0.0    1  0.0      0     0 ?        SN   20:07   0:00 [ksmd]
root          42      42  0.0    1  0.0      0     0 ?        SN   20:07   0:00 [khugepaged]
root          43      43  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-kblockd]
root          44      44  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-blkcg_punt_bio]
root          45      45  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-kintegrityd]
root          46      46  0.0    1  0.0      0     0 ?        S    20:07   0:00 [irq/9-acpi]
root          48      48  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-tpm_dev_wq]
root          49      49  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-ata_sff]
root          50      50  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-md]
root          51      51  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-md_bitmap]
root          52      52  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-edac-poller]
root          53      53  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-devfreq_wq]
root          54      54  0.0    1  0.0      0     0 ?        S    20:07   0:00 [watchdogd]
root          55      55  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-quota_events_unbound]
root          56      56  0.3    1  0.0      0     0 ?        I<   20:07   0:01 [kworker/1:1H-kblockd]
root          57      57  3.3    1  0.0      0     0 ?        S    20:07   0:14 [kswapd0]
root          58      58  0.0    1  0.0      0     0 ?        S    20:07   0:00 [ecryptfs-kthread]
root          59      59  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-kthrotld]
root          60      60  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-acpi_thermal_pm]
root          61      61  0.1    1  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:1-events_unbound]
root          62      62  0.1    1  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:2-ext4-rsv-conversion]
root          63      63  0.0    1  0.0      0     0 ?        S    20:07   0:00 [scsi_eh_0]
root          64      64  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-scsi_tmf_0]
root          65      65  0.0    1  0.0      0     0 ?        S    20:07   0:00 [scsi_eh_1]
root          66      66  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-scsi_tmf_1]
root          68      68  0.1    1  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:4-events_unbound]
root          70      70  0.1    1  0.0      0     0 ?        I    20:07   0:00 [kworker/0:2-cgroup_release]
root          71      71  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-mld]
root          72      72  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-ipv6_addrconf]
root          73      73  0.0    1  0.0      0     0 ?        I    20:07   0:00 [kworker/u8:1-ipv6_addrconf]
root          74      74  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-kstrp]
root          76      76  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/u11:0]
root          77      77  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/u12:0]
root          78      78  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/u13:0-ttm]
root          89      89  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-charger_manager]
root         139     139  0.0    1  0.0      0     0 ?        S    20:07   0:00 [scsi_eh_2]
root         140     140  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-scsi_tmf_2]
root         195     195  0.1    1  0.0      0     0 ?        S    20:07   0:00 [jbd2/sda2-8]
root         196     196  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-ext4-rsv-conversion]
root         244     244  0.2    1  0.4  50860 17160 ?        S<s  20:07   0:00 /usr/lib/systemd/systemd-journald
root         272     272  0.0    1  0.0      0     0 ?        I    20:07   0:00 [kworker/0:3-cgroup_release]
root         326     326  0.0    1  0.1  30180  7760 ?        Ss   20:07   0:00 /usr/lib/systemd/systemd-udevd
root         377     377  0.0    1  0.0      0     0 ?        S    20:07   0:00 [psimon]
systemd+     416     416  0.0    1  0.1  17572  7804 ?        Ss   20:07   0:00 /usr/lib/systemd/systemd-oomd
systemd+     419     419  0.1    1  0.3  21860 13484 ?        Ss   20:07   0:00 /usr/lib/systemd/systemd-resolved
systemd+     421     421  0.0    2  0.1  91060  7996 ?        Ssl  20:07   0:00 /usr/lib/systemd/systemd-timesyncd
systemd+     421     462  0.0    2  0.1  91060  7996 ?        Ssl  20:07   0:00 /usr/lib/systemd/systemd-timesyncd
root         582     582  0.0    1  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:6-ext4-rsv-conversion]
root         586     586  0.0    1  0.0      0     0 ?        I    20:07   0:00 [kworker/u10:5-events_power_efficient]
root         591     591  0.0    1  0.0      0     0 ?        I    20:07   0:00 [kworker/u9:7-flush-8:0]
root         613     613  0.0    1  0.0      0     0 ?        S    20:07   0:00 [irq/18-vmwgfx]
root         615     615  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/R-ttm]
avahi        620     620  0.0    1  0.1   8676  4776 ?        Ss   20:07   0:00 avahi-daemon: running [praditadf-VirtualBox.local]
message+     621     621  0.3    1  0.1  12208  7392 ?        Ss   20:07   0:01 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-a
gnome-r+     625     625  0.0    4  0.3 439092 14088 ?        Ssl  20:07   0:00 /usr/libexec/gnome-remote-desktop-daemon --system
gnome-r+     625     884  0.0    4  0.3 439092 14088 ?        Ssl  20:07   0:00 /usr/libexec/gnome-remote-desktop-daemon --system
gnome-r+     625     895  0.0    4  0.3 439092 14088 ?        Ssl  20:07   0:00 /usr/libexec/gnome-remote-desktop-daemon --system
gnome-r+     625     901  0.0    4  0.3 439092 14088 ?        Ssl  20:07   0:00 /usr/libexec/gnome-remote-desktop-daemon --system
polkitd      645     645  0.1    4  0.2 384604 11076 ?        Ssl  20:07   0:00 /usr/lib/polkit-1/polkitd --no-debug
polkitd      645     822  0.0    4  0.2 384604 11076 ?        Ssl  20:07   0:00 /usr/lib/polkit-1/polkitd --no-debug
polkitd      645     823  0.0    4  0.2 384604 11076 ?        Ssl  20:07   0:00 /usr/lib/polkit-1/polkitd --no-debug
polkitd      645     827  0.0    4  0.2 384604 11076 ?        Ssl  20:07   0:00 /usr/lib/polkit-1/polkitd --no-debug
root         657     657  0.0    4  0.1 322052  7532 ?        Ssl  20:07   0:00 /usr/libexec/power-profiles-daemon
root         657     678  0.0    4  0.1 322052  7532 ?        Ssl  20:07   0:00 /usr/libexec/power-profiles-daemon
root         657     679  0.0    4  0.1 322052  7532 ?        Ssl  20:07   0:00 /usr/libexec/power-profiles-daemon
root         657     681  0.0    4  0.1 322052  7532 ?        Ssl  20:07   0:00 /usr/libexec/power-profiles-daemon
root         668     668  0.0   10  0.8 1923668 32396 ?       Ssl  20:07   0:00 /usr/lib/snapd/snapd
root         668     708  0.7   10  0.8 1923668 32396 ?       Ssl  20:07   0:03 /usr/lib/snapd/snapd
root         668     711  0.0   10  0.8 1923668 32396 ?       Ssl  20:07   0:00 /usr/lib/snapd/snapd
root         668     712  0.2   10  0.8 1923668 32396 ?       Ssl  20:07   0:01 /usr/lib/snapd/snapd
root         668     720  0.0   10  0.8 1923668 32396 ?       Ssl  20:07   0:00 /usr/lib/snapd/snapd
root         668     781  0.0   10  0.8 1923668 32396 ?       Ssl  20:07   0:00 /usr/lib/snapd/snapd
root         668     783  0.3   10  0.8 1923668 32396 ?       Ssl  20:07   0:01 /usr/lib/snapd/snapd
root         668     904  0.6   10  0.8 1923668 32396 ?       Ssl  20:07   0:02 /usr/lib/snapd/snapd
root         668    1425  0.4   10  0.8 1923668 32396 ?       Ssl  20:07   0:01 /usr/lib/snapd/snapd
root         668    4223  1.0   10  0.8 1923668 32396 ?       Ssl  20:12   0:00 /usr/lib/snapd/snapd
root         672     672  0.0    4  0.2 321968  8224 ?        Ssl  20:07   0:00 /usr/libexec/accounts-daemon
root         672     731  0.0    4  0.2 321968  8224 ?        Ssl  20:07   0:00 /usr/libexec/accounts-daemon
root         672     732  0.0    4  0.2 321968  8224 ?        Ssl  20:07   0:00 /usr/libexec/accounts-daemon
root         672     734  0.0    4  0.2 321968  8224 ?        Ssl  20:07   0:00 /usr/libexec/accounts-daemon
root         675     675  0.0    1  0.0  18100  3016 ?        Ss   20:07   0:00 /usr/sbin/cron -f -P
root         691     691  0.0    4  0.1 318560  7188 ?        Ssl  20:07   0:00 /usr/libexec/switcheroo-control
root         691     730  0.0    4  0.1 318560  7188 ?        Ssl  20:07   0:00 /usr/libexec/switcheroo-control
root         691     735  0.0    4  0.1 318560  7188 ?        Ssl  20:07   0:00 /usr/libexec/switcheroo-control
root         691     737  0.0    4  0.1 318560  7188 ?        Ssl  20:07   0:00 /usr/libexec/switcheroo-control
root         718     718  0.0    1  0.2  18176  8884 ?        Ss   20:07   0:00 /usr/lib/systemd/systemd-logind
root         724     724  0.0    6  0.3 469736 14228 ?        Ssl  20:07   0:00 /usr/libexec/udisks2/udisksd
root         724     746  0.0    6  0.3 469736 14228 ?        Ssl  20:07   0:00 /usr/libexec/udisks2/udisksd
root         724     747  0.0    6  0.3 469736 14228 ?        Ssl  20:07   0:00 /usr/libexec/udisks2/udisksd
root         724     750  0.0    6  0.3 469736 14228 ?        Ssl  20:07   0:00 /usr/libexec/udisks2/udisksd
root         724     863  0.0    6  0.3 469736 14228 ?        Ssl  20:07   0:00 /usr/libexec/udisks2/udisksd
root         724     922  0.0    6  0.3 469736 14228 ?        Ssl  20:07   0:00 /usr/libexec/udisks2/udisksd
syslog       749     749  0.0    4  0.1 222572  6320 ?        Ssl  20:07   0:00 /usr/sbin/rsyslogd -n -iNONE
syslog       749     811  0.0    4  0.1 222572  6320 ?        Ssl  20:07   0:00 /usr/sbin/rsyslogd -n -iNONE
syslog       749     813  0.0    4  0.1 222572  6320 ?        Ssl  20:07   0:00 /usr/sbin/rsyslogd -n -iNONE
syslog       749     814  0.0    4  0.1 222572  6320 ?        Ssl  20:07   0:00 /usr/sbin/rsyslogd -n -iNONE
avahi        762     762  0.0    1  0.0   8488  1528 ?        S    20:07   0:00 avahi-daemon: chroot helper
root         778     778  0.0    4  0.4 345172 19644 ?        Ssl  20:07   0:00 /usr/sbin/NetworkManager --no-daemon
root         778     919  0.0    4  0.4 345172 19644 ?        Ssl  20:07   0:00 /usr/sbin/NetworkManager --no-daemon
root         778     920  0.0    4  0.4 345172 19644 ?        Ssl  20:07   0:00 /usr/sbin/NetworkManager --no-daemon
root         778     921  0.0    4  0.4 345172 19644 ?        Ssl  20:07   0:00 /usr/sbin/NetworkManager --no-daemon
root         787     787  0.0    1  0.1  17392  6468 ?        Ss   20:07   0:00 /usr/sbin/wpa_supplicant -u -s -O DIR=/run/wpa_supplicant GROUP=netdev
root         872     872  0.2    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/0:2H-kblockd]
root         874     874  0.0    4  0.2 392108 11736 ?        Ssl  20:07   0:00 /usr/sbin/ModemManager
root         874     924  0.0    4  0.2 392108 11736 ?        Ssl  20:07   0:00 /usr/sbin/ModemManager
root         874     928  0.0    4  0.2 392108 11736 ?        Ssl  20:07   0:00 /usr/sbin/ModemManager
root         874     933  0.0    4  0.2 392108 11736 ?        Ssl  20:07   0:00 /usr/sbin/ModemManager
root        1215    1215  0.0    1  0.3  47072 12476 ?        Ss   20:07   0:00 /usr/sbin/cupsd -l
root        1222    1222  0.0    2  0.3 120928 14988 ?        Ssl  20:07   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdo
root        1222    1244  0.0    2  0.3 120928 14988 ?        Ssl  20:07   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdo
root        1235    1235  0.0    4  0.2 323500  9396 ?        Ssl  20:07   0:00 /usr/sbin/gdm3
root        1235    1237  0.0    4  0.2 323500  9396 ?        Ssl  20:07   0:00 /usr/sbin/gdm3
root        1235    1238  0.0    4  0.2 323500  9396 ?        Ssl  20:07   0:00 /usr/sbin/gdm3
root        1235    1240  0.0    4  0.2 323500  9396 ?        Ssl  20:07   0:00 /usr/sbin/gdm3
cups-br+    1239    1239  0.0    4  0.4 268500 18968 ?        Ssl  20:07   0:00 /usr/sbin/cups-browsed
cups-br+    1239    1255  0.0    4  0.4 268500 18968 ?        Ssl  20:07   0:00 /usr/sbin/cups-browsed
cups-br+    1239    1256  0.0    4  0.4 268500 18968 ?        Ssl  20:07   0:00 /usr/sbin/cups-browsed
cups-br+    1239    1257  0.0    4  0.4 268500 18968 ?        Ssl  20:07   0:00 /usr/sbin/cups-browsed
kernoops    1245    1245  0.0    1  0.0  12752  2120 ?        Ss   20:07   0:00 /usr/sbin/kerneloops --test
kernoops    1249    1249  0.0    1  0.0  12752  2252 ?        Ss   20:07   0:00 /usr/sbin/kerneloops
rtkit       1316    1316  0.0    3  0.0  22948  3540 ?        SNsl 20:07   0:00 /usr/libexec/rtkit-daemon
rtkit       1316    1323  0.0    3  0.0  22948  3540 ?        Ssl  20:07   0:00 /usr/libexec/rtkit-daemon
rtkit       1316    1324  0.0    3  0.0  22948  3540 ?        SNsl 20:07   0:00 /usr/libexec/rtkit-daemon
colord      1428    1428  0.0    4  0.3 328736 14248 ?        Ssl  20:07   0:00 /usr/libexec/colord
colord      1428    1433  0.0    4  0.3 328736 14248 ?        Ssl  20:07   0:00 /usr/libexec/colord
colord      1428    1434  0.0    4  0.3 328736 14248 ?        Ssl  20:07   0:00 /usr/libexec/colord
colord      1428    1436  0.0    4  0.3 328736 14248 ?        Ssl  20:07   0:00 /usr/libexec/colord
root        1468    1468  0.0    4  0.2 325352  9116 ?        Ssl  20:07   0:00 /usr/libexec/upowerd
root        1468    1512  0.0    4  0.2 325352  9116 ?        Ssl  20:07   0:00 /usr/libexec/upowerd
root        1468    1513  0.0    4  0.2 325352  9116 ?        Ssl  20:07   0:00 /usr/libexec/upowerd
root        1468    1516  0.0    4  0.2 325352  9116 ?        Ssl  20:07   0:00 /usr/libexec/upowerd
root        1762    1762  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/u12:1-ttm]
root        1763    1763  0.0    1  0.0      0     0 ?        I<   20:07   0:00 [kworker/u13:1]
root        1793    1793  0.0    4  0.2 251264 10628 ?        Sl   20:07   0:00 gdm-session-worker [pam/gdm-password]
root        1793    1794  0.0    4  0.2 251264 10628 ?        Sl   20:07   0:00 gdm-session-worker [pam/gdm-password]
root        1793    1795  0.0    4  0.2 251264 10628 ?        Sl   20:07   0:00 gdm-session-worker [pam/gdm-password]
root        1793    1796  0.0    4  0.2 251264 10628 ?        Sl   20:07   0:00 gdm-session-worker [pam/gdm-password]
pradita+    1808    1808  0.2    1  0.3  21280 12784 ?        Ss   20:08   0:01 /usr/lib/systemd/systemd --user
pradita+    1817    1817  0.0    1  0.0  21472  3672 ?        S    20:08   0:00 (sd-pam)
pradita+    1830    1830  0.0    3  0.2 124044 11348 ?        S<sl 20:08   0:00 /usr/bin/pipewire
pradita+    1830    1856  0.0    3  0.2 124044 11348 ?        Ssl  20:08   0:00 /usr/bin/pipewire
pradita+    1830    1875  0.0    3  0.2 124044 11348 ?        Ssl  20:08   0:00 /usr/bin/pipewire
pradita+    1843    1843  0.0    3  0.1 106412  5508 ?        Ssl  20:08   0:00 /usr/bin/pipewire -c filter-chain.conf
pradita+    1843    1857  0.0    3  0.1 106412  5508 ?        Ssl  20:08   0:00 /usr/bin/pipewire -c filter-chain.conf
pradita+    1843    1858  0.0    3  0.1 106412  5508 ?        Ssl  20:08   0:00 /usr/bin/pipewire -c filter-chain.conf
pradita+    1846    1846  0.0    6  0.3 415576 15384 ?        S<sl 20:08   0:00 /usr/bin/wireplumber
pradita+    1846    1859  0.0    6  0.3 415576 15384 ?        Ssl  20:08   0:00 /usr/bin/wireplumber
pradita+    1846    1862  0.0    6  0.3 415576 15384 ?        Ssl  20:08   0:00 /usr/bin/wireplumber
pradita+    1846    1878  0.0    6  0.3 415576 15384 ?        Ssl  20:08   0:00 /usr/bin/wireplumber
pradita+    1846    1881  0.0    6  0.3 415576 15384 ?        Ssl  20:08   0:00 /usr/bin/wireplumber
pradita+    1846    1883  0.0    6  0.3 415576 15384 ?        Ssl  20:08   0:00 /usr/bin/wireplumber
pradita+    1847    1847  0.0    3  0.4 125024 17880 ?        S<Lsl 20:08   0:00 /usr/bin/pipewire-pulse
pradita+    1847    1855  0.0    3  0.4 125024 17880 ?        SLsl 20:08   0:00 /usr/bin/pipewire-pulse
pradita+    1847    1876  0.0    3  0.4 125024 17880 ?        SLsl 20:08   0:00 /usr/bin/pipewire-pulse
pradita+    1848    1848  0.3    1  0.1  10932  6832 ?        Ss   20:08   0:01 /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --
pradita+    1849    1849  0.0    5  0.2 325192 10560 ?        SLsl 20:08   0:00 /usr/bin/gnome-keyring-daemon --foreground --components=pkcs11,secrets --
pradita+    1849    1865  0.0    5  0.2 325192 10560 ?        SLsl 20:08   0:00 /usr/bin/gnome-keyring-daemon --foreground --components=pkcs11,secrets --
pradita+    1849    1866  0.0    5  0.2 325192 10560 ?        SLsl 20:08   0:00 /usr/bin/gnome-keyring-daemon --foreground --components=pkcs11,secrets --
pradita+    1849    1873  0.0    5  0.2 325192 10560 ?        SLsl 20:08   0:00 /usr/bin/gnome-keyring-daemon --foreground --components=pkcs11,secrets --
pradita+    1849    1874  0.0    5  0.2 325192 10560 ?        SLsl 20:08   0:00 /usr/bin/gnome-keyring-daemon --foreground --components=pkcs11,secrets --
pradita+    1892    1892  0.0    9  0.1 693732  7676 ?        Ssl  20:08   0:00 /usr/libexec/xdg-document-portal
pradita+    1892    1924  0.0    9  0.1 693732  7676 ?        Ssl  20:08   0:00 /usr/libexec/xdg-document-portal
pradita+    1892    1925  0.0    9  0.1 693732  7676 ?        Ssl  20:08   0:00 /usr/libexec/xdg-document-portal
pradita+    1892    1926  0.0    9  0.1 693732  7676 ?        Ssl  20:08   0:00 /usr/libexec/xdg-document-portal
pradita+    1892    1952  0.0    9  0.1 693732  7676 ?        Ssl  20:08   0:00 /usr/libexec/xdg-document-portal
pradita+    1892    1955  0.0    9  0.1 693732  7676 ?        Ssl  20:08   0:00 /usr/libexec/xdg-document-portal
pradita+    1892    1956  0.0    9  0.1 693732  7676 ?        Ssl  20:08   0:00 /usr/libexec/xdg-document-portal
pradita+    1892    1957  0.0    9  0.1 693732  7676 ?        Ssl  20:08   0:00 /usr/libexec/xdg-document-portal
pradita+    1892    4941  0.0    9  0.1 693732  7676 ?        Ssl  20:13   0:00 /usr/libexec/xdg-document-portal
pradita+    1900    1900  0.0    4  0.1 244344  6344 tty2     Ssl+ 20:08   0:00 /usr/libexec/gdm-wayland-session env GNOME_SHELL_SESSION_MODE=ubuntu /usr
pradita+    1900    1901  0.0    4  0.1 244344  6344 tty2     Ssl+ 20:08   0:00 /usr/libexec/gdm-wayland-session env GNOME_SHELL_SESSION_MODE=ubuntu /usr
pradita+    1900    1903  0.0    4  0.1 244344  6344 tty2     Ssl+ 20:08   0:00 /usr/libexec/gdm-wayland-session env GNOME_SHELL_SESSION_MODE=ubuntu /usr
pradita+    1900    1917  0.0    4  0.1 244344  6344 tty2     Ssl+ 20:08   0:00 /usr/libexec/gdm-wayland-session env GNOME_SHELL_SESSION_MODE=ubuntu /usr
pradita+    1919    1919  0.0    4  0.3 306912 13444 tty2     Sl+  20:08   0:00 /usr/libexec/gnome-session-binary --session=ubuntu
pradita+    1919    1981  0.0    4  0.3 306912 13444 tty2     Sl+  20:08   0:00 /usr/libexec/gnome-session-binary --session=ubuntu
pradita+    1919    1982  0.0    4  0.3 306912 13444 tty2     Sl+  20:08   0:00 /usr/libexec/gnome-session-binary --session=ubuntu
pradita+    1919    1983  0.0    4  0.3 306912 13444 tty2     Sl+  20:08   0:00 /usr/libexec/gnome-session-binary --session=ubuntu
pradita+    1930    1930  0.0    4  0.1 317984  6292 ?        Ssl  20:08   0:00 /usr/libexec/xdg-permission-store
pradita+    1930    1936  0.0    4  0.1 317984  6292 ?        Ssl  20:08   0:00 /usr/libexec/xdg-permission-store
pradita+    1930    1937  0.0    4  0.1 317984  6292 ?        Ssl  20:08   0:00 /usr/libexec/xdg-permission-store
pradita+    1930    1941  0.0    4  0.1 317984  6292 ?        Ssl  20:08   0:00 /usr/libexec/xdg-permission-store
root        1953    1953  0.0    1  0.0   2712  2060 ?        Ss   20:08   0:00 fusermount3 -o rw,nosuid,nodev,fsname=portal,auto_unmount,subtype=portal 
pradita+    1984    1984  0.0    3  0.1 162660  6768 ?        Ssl  20:08   0:00 /usr/libexec/gcr-ssh-agent --base-dir /run/user/1000/gcr
pradita+    1984    1989  0.0    3  0.1 162660  6768 ?        Ssl  20:08   0:00 /usr/libexec/gcr-ssh-agent --base-dir /run/user/1000/gcr
pradita+    1984    1991  0.0    3  0.1 162660  6768 ?        Ssl  20:08   0:00 /usr/libexec/gcr-ssh-agent --base-dir /run/user/1000/gcr
pradita+    1986    1986  0.0    2  0.1 100224  5752 ?        Ssl  20:08   0:00 /usr/libexec/gnome-session-ctl --monitor
pradita+    1986    1995  0.0    2  0.1 100224  5752 ?        Ssl  20:08   0:00 /usr/libexec/gnome-session-ctl --monitor
pradita+    1999    1999  0.0    4  0.1 322952  7936 ?        Ssl  20:08   0:00 /usr/libexec/gvfsd
pradita+    1999    2009  0.0    4  0.1 322952  7936 ?        Ssl  20:08   0:00 /usr/libexec/gvfsd
pradita+    1999    2010  0.0    4  0.1 322952  7936 ?        Ssl  20:08   0:00 /usr/libexec/gvfsd
pradita+    1999    2012  0.0    4  0.1 322952  7936 ?        Ssl  20:08   0:00 /usr/libexec/gvfsd
pradita+    2017    2017  0.0    7  0.1 468384  7352 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-fuse /run/user/1000/gvfs -f
pradita+    2017    2025  0.0    7  0.1 468384  7352 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-fuse /run/user/1000/gvfs -f
pradita+    2017    2026  0.0    7  0.1 468384  7352 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-fuse /run/user/1000/gvfs -f
pradita+    2017    2027  0.0    7  0.1 468384  7352 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-fuse /run/user/1000/gvfs -f
pradita+    2017    2028  0.0    7  0.1 468384  7352 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-fuse /run/user/1000/gvfs -f
pradita+    2017    2029  0.0    7  0.1 468384  7352 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-fuse /run/user/1000/gvfs -f
pradita+    2017    2032  0.0    7  0.1 468384  7352 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-fuse /run/user/1000/gvfs -f
pradita+    2019    2019  0.0    5  0.3 742172 15100 ?        Ssl  20:08   0:00 /usr/libexec/gnome-session-binary --systemd-service --session=ubuntu
pradita+    2019    2034  0.0    5  0.3 742172 15100 ?        Ssl  20:08   0:00 /usr/libexec/gnome-session-binary --systemd-service --session=ubuntu
pradita+    2019    2035  0.0    5  0.3 742172 15100 ?        Ssl  20:08   0:00 /usr/libexec/gnome-session-binary --systemd-service --session=ubuntu
pradita+    2019    2038  0.0    5  0.3 742172 15100 ?        Ssl  20:08   0:00 /usr/libexec/gnome-session-binary --systemd-service --session=ubuntu
pradita+    2019    2041  0.0    5  0.3 742172 15100 ?        Ssl  20:08   0:00 /usr/libexec/gnome-session-binary --systemd-service --session=ubuntu
pradita+    2067    2067  8.8   16  9.0 4076060 363448 ?      Ssl  20:08   0:32 /usr/bin/gnome-shell
pradita+    2067    2080  0.0   16  9.0 4076060 363448 ?      Ssl  20:08   0:00 /usr/bin/gnome-shell
pradita+    2067    2081  0.0   16  9.0 4076060 363448 ?      Ssl  20:08   0:00 /usr/bin/gnome-shell
pradita+    2067    2085  0.2   16  9.0 4076060 363448 ?      Ssl  20:08   0:00 /usr/bin/gnome-shell
pradita+    2067    2086  0.0   16  9.0 4076060 363448 ?      Ssl  20:08   0:00 /usr/bin/gnome-shell
pradita+    2067    2087  0.0   16  9.0 4076060 363448 ?      Ssl  20:08   0:00 /usr/bin/gnome-shell
pradita+    2067    2088  0.0   16  9.0 4076060 363448 ?      Ssl  20:08   0:00 /usr/bin/gnome-shell
pradita+    2067    2094  0.9   16  9.0 4076060 363448 ?      Ssl  20:08   0:03 /usr/bin/gnome-shell
pradita+    2067    2100  5.2   16  9.0 4076060 363448 ?      Ssl  20:08   0:19 /usr/bin/gnome-shell
pradita+    2067    2101  5.4   16  9.0 4076060 363448 ?      Ssl  20:08   0:20 /usr/bin/gnome-shell
pradita+    2067    2102  0.0   16  9.0 4076060 363448 ?      Ssl  20:08   0:00 /usr/bin/gnome-shell
pradita+    2067    2103  0.0   16  9.0 4076060 363448 ?      Ssl  20:08   0:00 /usr/bin/gnome-shell
pradita+    2067    2104  0.0   16  9.0 4076060 363448 ?      SNsl 20:08   0:00 /usr/bin/gnome-shell
pradita+    2067    2109  0.6   16  9.0 4076060 363448 ?      Ssl  20:08   0:02 /usr/bin/gnome-shell
pradita+    2067    2575  0.0   16  9.0 4076060 363448 ?      Ssl  20:08   0:00 /usr/bin/gnome-shell
pradita+    2067    2628  0.0   16  9.0 4076060 363448 ?      Ssl  20:08   0:00 /usr/bin/gnome-shell
pradita+    2068    2068  0.0    5  0.2 382952  8024 ?        Sl   20:08   0:00 /usr/libexec/at-spi-bus-launcher --launch-immediately
pradita+    2068    2071  0.0    5  0.2 382952  8024 ?        Sl   20:08   0:00 /usr/libexec/at-spi-bus-launcher --launch-immediately
pradita+    2068    2074  0.0    5  0.2 382952  8024 ?        Sl   20:08   0:00 /usr/libexec/at-spi-bus-launcher --launch-immediately
pradita+    2068    2075  0.0    5  0.2 382952  8024 ?        Sl   20:08   0:00 /usr/libexec/at-spi-bus-launcher --launch-immediately
pradita+    2068    2078  0.0    5  0.2 382952  8024 ?        Sl   20:08   0:00 /usr/libexec/at-spi-bus-launcher --launch-immediately
pradita+    2084    2084  0.0    1  0.1   9488  5228 ?        S    20:08   0:00 /usr/bin/dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibil
pradita+    2137    2137  0.0    4  0.1 236076  7520 ?        Sl   20:08   0:00 /usr/libexec/at-spi2-registryd --use-gnome-session
pradita+    2137    2138  0.0    4  0.1 236076  7520 ?        Sl   20:08   0:00 /usr/libexec/at-spi2-registryd --use-gnome-session
pradita+    2137    2139  0.0    4  0.1 236076  7520 ?        Sl   20:08   0:00 /usr/libexec/at-spi2-registryd --use-gnome-session
pradita+    2137    2140  0.0    4  0.1 236076  7520 ?        Sl   20:08   0:00 /usr/libexec/at-spi2-registryd --use-gnome-session
pradita+    2155    2155  0.0    7  0.4 654792 16436 ?        Sl   20:08   0:00 /usr/libexec/gnome-shell-calendar-server
pradita+    2155    2156  0.0    7  0.4 654792 16436 ?        Sl   20:08   0:00 /usr/libexec/gnome-shell-calendar-server
pradita+    2155    2157  0.0    7  0.4 654792 16436 ?        Sl   20:08   0:00 /usr/libexec/gnome-shell-calendar-server
pradita+    2155    2159  0.0    7  0.4 654792 16436 ?        Sl   20:08   0:00 /usr/libexec/gnome-shell-calendar-server
pradita+    2155    2160  0.0    7  0.4 654792 16436 ?        Sl   20:08   0:00 /usr/libexec/gnome-shell-calendar-server
pradita+    2155    2161  0.0    7  0.4 654792 16436 ?        Sl   20:08   0:00 /usr/libexec/gnome-shell-calendar-server
pradita+    2155    2324  0.0    7  0.4 654792 16436 ?        Sl   20:08   0:00 /usr/libexec/gnome-shell-calendar-server
pradita+    2162    2162  0.0    5  0.9 604016 37208 ?        Ssl  20:08   0:00 /usr/libexec/evolution-source-registry
pradita+    2162    2165  0.0    5  0.9 604016 37208 ?        Ssl  20:08   0:00 /usr/libexec/evolution-source-registry
pradita+    2162    2166  0.0    5  0.9 604016 37208 ?        Ssl  20:08   0:00 /usr/libexec/evolution-source-registry
pradita+    2162    2167  0.0    5  0.9 604016 37208 ?        Ssl  20:08   0:00 /usr/libexec/evolution-source-registry
pradita+    2162    2168  0.0    5  0.9 604016 37208 ?        Ssl  20:08   0:00 /usr/libexec/evolution-source-registry
pradita+    2173    2173  0.0    6  0.4 2593560 18452 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.Shell.Notifications
pradita+    2173    2177  0.0    6  0.4 2593560 18452 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.Shell.Notifications
pradita+    2173    2178  0.0    6  0.4 2593560 18452 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.Shell.Notifications
pradita+    2173    2180  0.0    6  0.4 2593560 18452 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.Shell.Notifications
pradita+    2173    2208  0.0    6  0.4 2593560 18452 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.Shell.Notifications
pradita+    2173    2209  0.0    6  0.4 2593560 18452 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.Shell.Notifications
pradita+    2183    2183  0.0    4  0.2 395920  8976 ?        Ssl  20:08   0:00 /usr/bin/ibus-daemon --panel disable
pradita+    2183    2211  0.0    4  0.2 395920  8976 ?        Ssl  20:08   0:00 /usr/bin/ibus-daemon --panel disable
pradita+    2183    2212  0.0    4  0.2 395920  8976 ?        Ssl  20:08   0:00 /usr/bin/ibus-daemon --panel disable
pradita+    2183    2227  0.0    4  0.2 395920  8976 ?        Ssl  20:08   0:00 /usr/bin/ibus-daemon --panel disable
pradita+    2184    2184  0.0    5  0.1 392200  6692 ?        Ssl  20:08   0:00 /usr/libexec/gsd-a11y-settings
pradita+    2184    2281  0.0    5  0.1 392200  6692 ?        Ssl  20:08   0:00 /usr/libexec/gsd-a11y-settings
pradita+    2184    2299  0.0    5  0.1 392200  6692 ?        Ssl  20:08   0:00 /usr/libexec/gsd-a11y-settings
pradita+    2184    2343  0.0    5  0.1 392200  6692 ?        Ssl  20:08   0:00 /usr/libexec/gsd-a11y-settings
pradita+    2184    2356  0.0    5  0.1 392200  6692 ?        Ssl  20:08   0:00 /usr/libexec/gsd-a11y-settings
pradita+    2185    2185  0.0    5  0.3 423400 15604 ?        Ssl  20:08   0:00 /usr/libexec/gsd-color
pradita+    2185    2303  0.0    5  0.3 423400 15604 ?        Ssl  20:08   0:00 /usr/libexec/gsd-color
pradita+    2185    2322  0.0    5  0.3 423400 15604 ?        Ssl  20:08   0:00 /usr/libexec/gsd-color
pradita+    2185    2326  0.0    5  0.3 423400 15604 ?        Ssl  20:08   0:00 /usr/libexec/gsd-color
pradita+    2185    2344  0.0    5  0.3 423400 15604 ?        Ssl  20:08   0:00 /usr/libexec/gsd-color
pradita+    2186    2186  0.0    5  0.2 440356 10556 ?        Ssl  20:08   0:00 /usr/libexec/gsd-datetime
pradita+    2186    2311  0.0    5  0.2 440356 10556 ?        Ssl  20:08   0:00 /usr/libexec/gsd-datetime
pradita+    2186    2312  0.0    5  0.2 440356 10556 ?        Ssl  20:08   0:00 /usr/libexec/gsd-datetime
pradita+    2186    2339  0.0    5  0.2 440356 10556 ?        Ssl  20:08   0:00 /usr/libexec/gsd-datetime
pradita+    2186    2350  0.0    5  0.2 440356 10556 ?        Ssl  20:08   0:00 /usr/libexec/gsd-datetime
pradita+    2187    2187  0.0    5  0.1 467552  7904 ?        Ssl  20:08   0:00 /usr/libexec/gsd-housekeeping
pradita+    2187    2246  0.0    5  0.1 467552  7904 ?        Ssl  20:08   0:00 /usr/libexec/gsd-housekeeping
pradita+    2187    2247  0.0    5  0.1 467552  7904 ?        Ssl  20:08   0:00 /usr/libexec/gsd-housekeeping
pradita+    2187    2283  0.0    5  0.1 467552  7904 ?        Ssl  20:08   0:00 /usr/libexec/gsd-housekeeping
pradita+    2187    2338  0.0    5  0.1 467552  7904 ?        Ssl  20:08   0:00 /usr/libexec/gsd-housekeeping
pradita+    2188    2188  0.0    5  0.3 422256 15340 ?        Ssl  20:08   0:00 /usr/libexec/gsd-keyboard
pradita+    2188    2301  0.0    5  0.3 422256 15340 ?        Ssl  20:08   0:00 /usr/libexec/gsd-keyboard
pradita+    2188    2304  0.0    5  0.3 422256 15340 ?        Ssl  20:08   0:00 /usr/libexec/gsd-keyboard
pradita+    2188    2310  0.0    5  0.3 422256 15340 ?        Ssl  20:08   0:00 /usr/libexec/gsd-keyboard
pradita+    2188    2337  0.0    5  0.3 422256 15340 ?        Ssl  20:08   0:00 /usr/libexec/gsd-keyboard
pradita+    2189    2189  0.0    5  0.4 752112 17248 ?        Ssl  20:08   0:00 /usr/libexec/gsd-media-keys
pradita+    2189    2265  0.0    5  0.4 752112 17248 ?        Ssl  20:08   0:00 /usr/libexec/gsd-media-keys
pradita+    2189    2266  0.0    5  0.4 752112 17248 ?        Ssl  20:08   0:00 /usr/libexec/gsd-media-keys
pradita+    2189    2268  0.0    5  0.4 752112 17248 ?        Ssl  20:08   0:00 /usr/libexec/gsd-media-keys
pradita+    2189    2278  0.0    5  0.4 752112 17248 ?        Ssl  20:08   0:00 /usr/libexec/gsd-media-keys
pradita+    2191    2191  0.0    5  0.4 534024 17100 ?        Ssl  20:08   0:00 /usr/libexec/gsd-power
pradita+    2191    2290  0.0    5  0.4 534024 17100 ?        Ssl  20:08   0:00 /usr/libexec/gsd-power
pradita+    2191    2291  0.0    5  0.4 534024 17100 ?        Ssl  20:08   0:00 /usr/libexec/gsd-power
pradita+    2191    2293  0.0    5  0.4 534024 17100 ?        Ssl  20:08   0:00 /usr/libexec/gsd-power
pradita+    2191    2341  0.0    5  0.4 534024 17100 ?        Ssl  20:08   0:00 /usr/libexec/gsd-power
pradita+    2192    2192  0.0    4  0.2 332436 10908 ?        Ssl  20:08   0:00 /usr/libexec/gsd-print-notifications
pradita+    2192    2286  0.0    4  0.2 332436 10908 ?        Ssl  20:08   0:00 /usr/libexec/gsd-print-notifications
pradita+    2192    2300  0.0    4  0.2 332436 10908 ?        Ssl  20:08   0:00 /usr/libexec/gsd-print-notifications
pradita+    2192    2342  0.0    4  0.2 332436 10908 ?        Ssl  20:08   0:00 /usr/libexec/gsd-print-notifications
pradita+    2193    2193  0.0    4  0.1 539760  6656 ?        Ssl  20:08   0:00 /usr/libexec/gsd-rfkill
pradita+    2193    2255  0.0    4  0.1 539760  6656 ?        Ssl  20:08   0:00 /usr/libexec/gsd-rfkill
pradita+    2193    2277  0.0    4  0.1 539760  6656 ?        Ssl  20:08   0:00 /usr/libexec/gsd-rfkill
pradita+    2193    2327  0.0    4  0.1 539760  6656 ?        Ssl  20:08   0:00 /usr/libexec/gsd-rfkill
pradita+    2194    2194  0.0    4  0.1 318236  6400 ?        Ssl  20:08   0:00 /usr/libexec/gsd-screensaver-proxy
pradita+    2194    2256  0.0    4  0.1 318236  6400 ?        Ssl  20:08   0:00 /usr/libexec/gsd-screensaver-proxy
pradita+    2194    2257  0.0    4  0.1 318236  6400 ?        Ssl  20:08   0:00 /usr/libexec/gsd-screensaver-proxy
pradita+    2194    2285  0.0    4  0.1 318236  6400 ?        Ssl  20:08   0:00 /usr/libexec/gsd-screensaver-proxy
pradita+    2195    2195  0.0    5  0.2 551872 10104 ?        Ssl  20:08   0:00 /usr/libexec/gsd-sharing
pradita+    2195    2280  0.0    5  0.2 551872 10104 ?        Ssl  20:08   0:00 /usr/libexec/gsd-sharing
pradita+    2195    2282  0.0    5  0.2 551872 10104 ?        Ssl  20:08   0:00 /usr/libexec/gsd-sharing
pradita+    2195    2284  0.0    5  0.2 551872 10104 ?        Ssl  20:08   0:00 /usr/libexec/gsd-sharing
pradita+    2195    2340  0.0    5  0.2 551872 10104 ?        Ssl  20:08   0:00 /usr/libexec/gsd-sharing
pradita+    2196    2196  0.0    5  0.1 468232  7628 ?        Ssl  20:08   0:00 /usr/libexec/gsd-smartcard
pradita+    2196    2261  0.0    5  0.1 468232  7628 ?        Ssl  20:08   0:00 /usr/libexec/gsd-smartcard
pradita+    2196    2264  0.0    5  0.1 468232  7628 ?        Ssl  20:08   0:00 /usr/libexec/gsd-smartcard
pradita+    2196    2279  0.0    5  0.1 468232  7628 ?        Ssl  20:08   0:00 /usr/libexec/gsd-smartcard
pradita+    2196    2334  0.0    5  0.1 468232  7628 ?        Ssl  20:08   0:00 /usr/libexec/gsd-smartcard
pradita+    2197    2197  0.0    5  0.2 402316  9136 ?        Ssl  20:08   0:00 /usr/libexec/gsd-sound
pradita+    2197    2298  0.0    5  0.2 402316  9136 ?        Ssl  20:08   0:00 /usr/libexec/gsd-sound
pradita+    2197    2321  0.0    5  0.2 402316  9136 ?        Ssl  20:08   0:00 /usr/libexec/gsd-sound
pradita+    2197    2345  0.0    5  0.2 402316  9136 ?        Ssl  20:08   0:00 /usr/libexec/gsd-sound
pradita+    2197    2370  0.0    5  0.2 402316  9136 ?        Ssl  20:08   0:00 /usr/libexec/gsd-sound
pradita+    2198    2198  0.0    5  0.3 496964 15208 ?        Ssl  20:08   0:00 /usr/libexec/gsd-wacom
pradita+    2198    2252  0.0    5  0.3 496964 15208 ?        Ssl  20:08   0:00 /usr/libexec/gsd-wacom
pradita+    2198    2294  0.0    5  0.3 496964 15208 ?        Ssl  20:08   0:00 /usr/libexec/gsd-wacom
pradita+    2198    2302  0.0    5  0.3 496964 15208 ?        Ssl  20:08   0:00 /usr/libexec/gsd-wacom
pradita+    2198    2336  0.0    5  0.3 496964 15208 ?        Ssl  20:08   0:00 /usr/libexec/gsd-wacom
pradita+    2202    2202  0.0    5  0.5 555360 20508 ?        Sl   20:08   0:00 /usr/libexec/goa-daemon
pradita+    2202    2330  0.0    5  0.5 555360 20508 ?        Sl   20:08   0:00 /usr/libexec/goa-daemon
pradita+    2202    2331  0.0    5  0.5 555360 20508 ?        Sl   20:08   0:00 /usr/libexec/goa-daemon
pradita+    2202    2386  0.0    5  0.5 555360 20508 ?        Sl   20:08   0:00 /usr/libexec/goa-daemon
pradita+    2202    2392  0.0    5  0.5 555360 20508 ?        Sl   20:08   0:00 /usr/libexec/goa-daemon
pradita+    2217    2217  0.0    8  1.2 836800 49008 ?        Sl   20:08   0:00 /usr/libexec/evolution-data-server/evolution-alarm-notify
pradita+    2217    2295  0.0    8  1.2 836800 49008 ?        Sl   20:08   0:00 /usr/libexec/evolution-data-server/evolution-alarm-notify
pradita+    2217    2296  0.0    8  1.2 836800 49008 ?        Sl   20:08   0:00 /usr/libexec/evolution-data-server/evolution-alarm-notify
pradita+    2217    2317  0.0    8  1.2 836800 49008 ?        Sl   20:08   0:00 /usr/libexec/evolution-data-server/evolution-alarm-notify
pradita+    2217    2346  0.0    8  1.2 836800 49008 ?        Sl   20:08   0:00 /usr/libexec/evolution-data-server/evolution-alarm-notify
pradita+    2217    2578  0.0    8  1.2 836800 49008 ?        Sl   20:08   0:00 /usr/libexec/evolution-data-server/evolution-alarm-notify
pradita+    2217    2582  0.0    8  1.2 836800 49008 ?        Sl   20:08   0:00 /usr/libexec/evolution-data-server/evolution-alarm-notify
pradita+    2217    2583  0.0    8  1.2 836800 49008 ?        Sl   20:08   0:00 /usr/libexec/evolution-data-server/evolution-alarm-notify
pradita+    2219    2219  0.0    4  0.1 305500  7712 ?        Sl   20:08   0:00 /usr/libexec/gsd-disk-utility-notify
pradita+    2219    2254  0.0    4  0.1 305500  7712 ?        Sl   20:08   0:00 /usr/libexec/gsd-disk-utility-notify
pradita+    2219    2271  0.0    4  0.1 305500  7712 ?        Sl   20:08   0:00 /usr/libexec/gsd-disk-utility-notify
pradita+    2219    2359  0.0    4  0.1 305500  7712 ?        Sl   20:08   0:00 /usr/libexec/gsd-disk-utility-notify
pradita+    2328    2328  0.0   10  0.5 907600 22496 ?        Ssl  20:08   0:00 /usr/libexec/evolution-calendar-factory
pradita+    2328    2365  0.0   10  0.5 907600 22496 ?        Ssl  20:08   0:00 /usr/libexec/evolution-calendar-factory
pradita+    2328    2367  0.0   10  0.5 907600 22496 ?        Ssl  20:08   0:00 /usr/libexec/evolution-calendar-factory
pradita+    2328    2402  0.0   10  0.5 907600 22496 ?        Ssl  20:08   0:00 /usr/libexec/evolution-calendar-factory
pradita+    2328    2440  0.0   10  0.5 907600 22496 ?        Ssl  20:08   0:00 /usr/libexec/evolution-calendar-factory
pradita+    2328    2441  0.0   10  0.5 907600 22496 ?        Ssl  20:08   0:00 /usr/libexec/evolution-calendar-factory
pradita+    2328    2448  0.0   10  0.5 907600 22496 ?        Ssl  20:08   0:00 /usr/libexec/evolution-calendar-factory
pradita+    2328    2454  0.0   10  0.5 907600 22496 ?        Ssl  20:08   0:00 /usr/libexec/evolution-calendar-factory
pradita+    2328    2455  0.0   10  0.5 907600 22496 ?        Ssl  20:08   0:00 /usr/libexec/evolution-calendar-factory
pradita+    2328    2463  0.0   10  0.5 907600 22496 ?        Ssl  20:08   0:00 /usr/libexec/evolution-calendar-factory
pradita+    2348    2348  0.0    5  0.1 319144  6500 ?        Sl   20:08   0:00 /usr/libexec/ibus-dconf
pradita+    2348    2379  0.0    5  0.1 319144  6500 ?        Sl   20:08   0:00 /usr/libexec/ibus-dconf
pradita+    2348    2385  0.0    5  0.1 319144  6500 ?        Sl   20:08   0:00 /usr/libexec/ibus-dconf
pradita+    2348    2409  0.0    5  0.1 319144  6500 ?        Sl   20:08   0:00 /usr/libexec/ibus-dconf
pradita+    2348    2438  0.0    5  0.1 319144  6500 ?        Sl   20:08   0:00 /usr/libexec/ibus-dconf
pradita+    2357    2357  0.8    5  0.5 431972 23288 ?        Sl   20:08   0:03 /usr/libexec/ibus-extension-gtk3
pradita+    2357    2408  0.0    5  0.5 431972 23288 ?        Sl   20:08   0:00 /usr/libexec/ibus-extension-gtk3
pradita+    2357    2415  0.0    5  0.5 431972 23288 ?        Sl   20:08   0:00 /usr/libexec/ibus-extension-gtk3
pradita+    2357    2417  0.0    5  0.5 431972 23288 ?        Sl   20:08   0:00 /usr/libexec/ibus-extension-gtk3
pradita+    2357    2424  0.0    5  0.5 431972 23288 ?        Sl   20:08   0:00 /usr/libexec/ibus-extension-gtk3
pradita+    2373    2373  0.0    4  0.3 424916 13944 ?        Sl   20:08   0:00 /usr/libexec/gsd-printer
pradita+    2373    2399  0.0    4  0.3 424916 13944 ?        Sl   20:08   0:00 /usr/libexec/gsd-printer
pradita+    2373    2400  0.0    4  0.3 424916 13944 ?        Sl   20:08   0:00 /usr/libexec/gsd-printer
pradita+    2373    2423  0.0    4  0.3 424916 13944 ?        Sl   20:08   0:00 /usr/libexec/gsd-printer
pradita+    2383    2383  0.0    4  0.1 319100  7220 ?        Sl   20:08   0:00 /usr/libexec/ibus-portal
pradita+    2383    2394  0.0    4  0.1 319100  7220 ?        Sl   20:08   0:00 /usr/libexec/ibus-portal
pradita+    2383    2395  0.0    4  0.1 319100  7220 ?        Sl   20:08   0:00 /usr/libexec/ibus-portal
pradita+    2383    2401  0.0    4  0.1 319100  7220 ?        Sl   20:08   0:00 /usr/libexec/ibus-portal
pradita+    2398    2398  0.0    4  0.2 397800  9172 ?        Sl   20:08   0:00 /usr/libexec/goa-identity-service
pradita+    2398    2404  0.0    4  0.2 397800  9172 ?        Sl   20:08   0:00 /usr/libexec/goa-identity-service
pradita+    2398    2405  0.0    4  0.2 397800  9172 ?        Sl   20:08   0:00 /usr/libexec/goa-identity-service
pradita+    2398    2421  0.0    4  0.2 397800  9172 ?        Sl   20:08   0:00 /usr/libexec/goa-identity-service
pradita+    2403    2403  0.0    5  0.2 398000 10764 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-udisks2-volume-monitor
pradita+    2403    2418  0.0    5  0.2 398000 10764 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-udisks2-volume-monitor
pradita+    2403    2419  0.0    5  0.2 398000 10764 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-udisks2-volume-monitor
pradita+    2403    2420  0.0    5  0.2 398000 10764 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-udisks2-volume-monitor
pradita+    2403    2447  0.0    5  0.2 398000 10764 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-udisks2-volume-monitor
pradita+    2406    2406  0.0    1  0.0  39140  3020 ?        Ss   20:08   0:00 /snap/snapd-desktop-integration/343/usr/bin/snapd-desktop-integration
pradita+    2456    2456  0.0    7  0.7 834144 28244 ?        Ssl  20:08   0:00 /usr/libexec/evolution-addressbook-factory
pradita+    2456    2476  0.0    7  0.7 834144 28244 ?        Ssl  20:08   0:00 /usr/libexec/evolution-addressbook-factory
pradita+    2456    2477  0.0    7  0.7 834144 28244 ?        Ssl  20:08   0:00 /usr/libexec/evolution-addressbook-factory
pradita+    2456    2483  0.0    7  0.7 834144 28244 ?        Ssl  20:08   0:00 /usr/libexec/evolution-addressbook-factory
pradita+    2456    2492  0.0    7  0.7 834144 28244 ?        Ssl  20:08   0:00 /usr/libexec/evolution-addressbook-factory
pradita+    2456    2493  0.0    7  0.7 834144 28244 ?        Ssl  20:08   0:00 /usr/libexec/evolution-addressbook-factory
pradita+    2456    2508  0.0    7  0.7 834144 28244 ?        Ssl  20:08   0:00 /usr/libexec/evolution-addressbook-factory
pradita+    2466    2466  0.0    4  0.1 318448  6700 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-goa-volume-monitor
pradita+    2466    2474  0.0    4  0.1 318448  6700 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-goa-volume-monitor
pradita+    2466    2475  0.0    4  0.1 318448  6700 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-goa-volume-monitor
pradita+    2466    2478  0.0    4  0.1 318448  6700 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-goa-volume-monitor
pradita+    2485    2485  0.0    5  0.2 398056  8128 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-afc-volume-monitor
pradita+    2485    2494  0.0    5  0.2 398056  8128 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-afc-volume-monitor
pradita+    2485    2495  0.0    5  0.2 398056  8128 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-afc-volume-monitor
pradita+    2485    2496  0.0    5  0.2 398056  8128 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-afc-volume-monitor
pradita+    2485    2498  0.0    5  0.2 398056  8128 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-afc-volume-monitor
pradita+    2500    2500  0.1    5  0.2 429420 11220 ?        Sl   20:08   0:00 /snap/snapd-desktop-integration/343/usr/bin/snapd-desktop-integration
pradita+    2500    2524  0.0    5  0.2 429420 11220 ?        Sl   20:08   0:00 /snap/snapd-desktop-integration/343/usr/bin/snapd-desktop-integration
pradita+    2500    2525  0.0    5  0.2 429420 11220 ?        Sl   20:08   0:00 /snap/snapd-desktop-integration/343/usr/bin/snapd-desktop-integration
pradita+    2500    2526  0.0    5  0.2 429420 11220 ?        Sl   20:08   0:00 /snap/snapd-desktop-integration/343/usr/bin/snapd-desktop-integration
pradita+    2500    2530  0.0    5  0.2 429420 11220 ?        Sl   20:08   0:00 /snap/snapd-desktop-integration/343/usr/bin/snapd-desktop-integration
pradita+    2501    2501  0.0    4  0.1 318468  6680 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-mtp-volume-monitor
pradita+    2501    2503  0.0    4  0.1 318468  6680 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-mtp-volume-monitor
pradita+    2501    2504  0.0    4  0.1 318468  6680 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-mtp-volume-monitor
pradita+    2501    2507  0.0    4  0.1 318468  6680 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-mtp-volume-monitor
pradita+    2515    2515  0.0    4  0.1 319436  6984 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-gphoto2-volume-monitor
pradita+    2515    2523  0.0    4  0.1 319436  6984 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-gphoto2-volume-monitor
pradita+    2515    2527  0.0    4  0.1 319436  6984 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-gphoto2-volume-monitor
pradita+    2515    2529  0.0    4  0.1 319436  6984 ?        Ssl  20:08   0:00 /usr/libexec/gvfs-gphoto2-volume-monitor
pradita+    2540    2540  0.0    4  0.1 245444  7632 ?        Sl   20:08   0:00 /usr/libexec/ibus-engine-simple
pradita+    2540    2547  0.0    4  0.1 245444  7632 ?        Sl   20:08   0:00 /usr/libexec/ibus-engine-simple
pradita+    2540    2549  0.0    4  0.1 245444  7632 ?        Sl   20:08   0:00 /usr/libexec/ibus-engine-simple
pradita+    2540    2550  0.0    4  0.1 245444  7632 ?        Sl   20:08   0:00 /usr/libexec/ibus-engine-simple
pradita+    2568    2568  0.0    4  0.1 230252  6144 ?        Ssl  20:08   0:00 /usr/libexec/dconf-service
pradita+    2568    2569  0.0    4  0.1 230252  6144 ?        Ssl  20:08   0:00 /usr/libexec/dconf-service
pradita+    2568    2570  0.0    4  0.1 230252  6144 ?        Ssl  20:08   0:00 /usr/libexec/dconf-service
pradita+    2568    2571  0.0    4  0.1 230252  6144 ?        Ssl  20:08   0:00 /usr/libexec/dconf-service
pradita+    2592    2592  0.0    6  0.4 2536140 18452 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.ScreenSaver
pradita+    2592    2594  0.0    6  0.4 2536140 18452 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.ScreenSaver
pradita+    2592    2595  0.0    6  0.4 2536140 18452 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.ScreenSaver
pradita+    2592    2598  0.0    6  0.4 2536140 18452 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.ScreenSaver
pradita+    2592    2599  0.0    6  0.4 2536140 18452 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.ScreenSaver
pradita+    2592    2600  0.0    6  0.4 2536140 18452 ?       Sl   20:08   0:00 /usr/bin/gjs -m /usr/share/gnome-shell/org.gnome.ScreenSaver
pradita+    2606    2606  0.0    5  0.2 544384  9056 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-trash --spawner :1.18 /org/gtk/gvfs/exec_spaw/0
pradita+    2606    2607  0.0    5  0.2 544384  9056 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-trash --spawner :1.18 /org/gtk/gvfs/exec_spaw/0
pradita+    2606    2608  0.0    5  0.2 544384  9056 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-trash --spawner :1.18 /org/gtk/gvfs/exec_spaw/0
pradita+    2606    2609  0.0    5  0.2 544384  9056 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-trash --spawner :1.18 /org/gtk/gvfs/exec_spaw/0
pradita+    2606    2612  0.0    5  0.2 544384  9056 ?        Sl   20:08   0:00 /usr/libexec/gvfsd-trash --spawner :1.18 /org/gtk/gvfs/exec_spaw/0
pradita+    2624    2624  0.0    8  0.5 743088 20900 ?        SNsl 20:08   0:00 /usr/libexec/tracker-miner-fs-3
pradita+    2624    2630  0.0    8  0.5 743088 20900 ?        SNsl 20:08   0:00 /usr/libexec/tracker-miner-fs-3
pradita+    2624    2631  0.0    8  0.5 743088 20900 ?        SNsl 20:08   0:00 /usr/libexec/tracker-miner-fs-3
pradita+    2624    2632  0.0    8  0.5 743088 20900 ?        SNsl 20:08   0:00 /usr/libexec/tracker-miner-fs-3
pradita+    2624    2669  0.0    8  0.5 743088 20900 ?        SNsl 20:08   0:00 /usr/libexec/tracker-miner-fs-3
pradita+    2624    2670  0.0    8  0.5 743088 20900 ?        SNsl 20:08   0:00 /usr/libexec/tracker-miner-fs-3
pradita+    2624    2697  0.0    8  0.5 743088 20900 ?        SNsl 20:08   0:00 /usr/libexec/tracker-miner-fs-3
pradita+    2624    2699  0.0    8  0.5 743088 20900 ?        SNsl 20:08   0:00 /usr/libexec/tracker-miner-fs-3
pradita+    2625    2625  0.0    8  0.3 710292 13276 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal
pradita+    2625    2626  0.0    8  0.3 710292 13276 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal
pradita+    2625    2629  0.0    8  0.3 710292 13276 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal
pradita+    2625    2633  0.0    8  0.3 710292 13276 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal
pradita+    2625    2711  0.0    8  0.3 710292 13276 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal
pradita+    2625    2723  0.0    8  0.3 710292 13276 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal
pradita+    2625    2726  0.0    8  0.3 710292 13276 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal
pradita+    2625    4943  0.0    8  0.3 710292 13276 ?        Ssl  20:13   0:00 /usr/libexec/xdg-desktop-portal
pradita+    2635    2635  0.0    6  0.7 852300 29916 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gnome
pradita+    2635    2661  0.0    6  0.7 852300 29916 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gnome
pradita+    2635    2662  0.0    6  0.7 852300 29916 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gnome
pradita+    2635    2664  0.0    6  0.7 852300 29916 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gnome
pradita+    2635    2690  0.0    6  0.7 852300 29916 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gnome
pradita+    2635    2701  0.0    6  0.7 852300 29916 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gnome
pradita+    2676    2676  0.2    8  1.2 2820888 48740 ?       Sl   20:08   0:01 gjs /usr/share/gnome-shell/extensions/ding@rastersoft.com/app/ding.js -E 
pradita+    2676    2692  0.0    8  1.2 2820888 48740 ?       Sl   20:08   0:00 gjs /usr/share/gnome-shell/extensions/ding@rastersoft.com/app/ding.js -E 
pradita+    2676    2693  0.0    8  1.2 2820888 48740 ?       Sl   20:08   0:00 gjs /usr/share/gnome-shell/extensions/ding@rastersoft.com/app/ding.js -E 
pradita+    2676    2694  0.0    8  1.2 2820888 48740 ?       Sl   20:08   0:00 gjs /usr/share/gnome-shell/extensions/ding@rastersoft.com/app/ding.js -E 
pradita+    2676    2695  0.0    8  1.2 2820888 48740 ?       Sl   20:08   0:00 gjs /usr/share/gnome-shell/extensions/ding@rastersoft.com/app/ding.js -E 
pradita+    2676    2696  0.0    8  1.2 2820888 48740 ?       Sl   20:08   0:00 gjs /usr/share/gnome-shell/extensions/ding@rastersoft.com/app/ding.js -E 
pradita+    2676    2703  0.0    8  1.2 2820888 48740 ?       Sl   20:08   0:00 gjs /usr/share/gnome-shell/extensions/ding@rastersoft.com/app/ding.js -E 
pradita+    2676    2730  0.0    8  1.2 2820888 48740 ?       Sl   20:08   0:00 gjs /usr/share/gnome-shell/extensions/ding@rastersoft.com/app/ding.js -E 
pradita+    2712    2712  0.0    5  0.4 428252 20000 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gtk
pradita+    2712    2713  0.0    5  0.4 428252 20000 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gtk
pradita+    2712    2714  0.0    5  0.4 428252 20000 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gtk
pradita+    2712    2716  0.0    5  0.4 428252 20000 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gtk
pradita+    2712    2717  0.0    5  0.4 428252 20000 ?        Ssl  20:08   0:00 /usr/libexec/xdg-desktop-portal-gtk
pradita+    2718    2718  0.0    4  0.1 244948  6560 ?        Ssl  20:08   0:00 /usr/libexec/gvfsd-metadata
pradita+    2718    2719  0.0    4  0.1 244948  6560 ?        Ssl  20:08   0:00 /usr/libexec/gvfsd-metadata
pradita+    2718    2720  0.0    4  0.1 244948  6560 ?        Ssl  20:08   0:00 /usr/libexec/gvfsd-metadata
pradita+    2718    2721  0.0    4  0.1 244948  6560 ?        Ssl  20:08   0:00 /usr/libexec/gvfsd-metadata
root        2768    2768  0.0    1  0.0      0     0 ?        I    20:08   0:00 [kworker/1:3-events]
pradita+    2888    2888  0.5    7  1.2 716028 48192 ?        Ssl  20:08   0:02 /usr/libexec/gnome-terminal-server
pradita+    2888    2889  0.0    7  1.2 716028 48192 ?        Ssl  20:08   0:00 /usr/libexec/gnome-terminal-server
pradita+    2888    2890  0.0    7  1.2 716028 48192 ?        Ssl  20:08   0:00 /usr/libexec/gnome-terminal-server
pradita+    2888    2892  0.0    7  1.2 716028 48192 ?        Ssl  20:08   0:00 /usr/libexec/gnome-terminal-server
pradita+    2888    2893  0.0    7  1.2 716028 48192 ?        Ssl  20:08   0:00 /usr/libexec/gnome-terminal-server
pradita+    2888    2922  0.0    7  1.2 716028 48192 ?        Ssl  20:08   0:00 /usr/libexec/gnome-terminal-server
pradita+    2888    3087  0.0    7  1.2 716028 48192 ?        Ssl  20:08   0:00 /usr/libexec/gnome-terminal-server
pradita+    2894    2894  0.4    1  1.2 280056 49568 ?        S    20:08   0:01 /usr/bin/Xwayland :0 -rootless -noreset -accessx -core -auth /run/user/10
pradita+    2898    2898  0.0    5  0.8 650968 34044 ?        Ssl  20:08   0:00 /usr/libexec/gsd-xsettings
pradita+    2898    2900  0.0    5  0.8 650968 34044 ?        Ssl  20:08   0:00 /usr/libexec/gsd-xsettings
pradita+    2898    2901  0.0    5  0.8 650968 34044 ?        Ssl  20:08   0:00 /usr/libexec/gsd-xsettings
pradita+    2898    2902  0.0    5  0.8 650968 34044 ?        Ssl  20:08   0:00 /usr/libexec/gsd-xsettings
pradita+    2898    2903  0.0    5  0.8 650968 34044 ?        Ssl  20:08   0:00 /usr/libexec/gsd-xsettings
pradita+    2920    2920  0.0    4  0.4 275544 19400 ?        Sl   20:08   0:00 /usr/libexec/ibus-x11
pradita+    2920    2923  0.0    4  0.4 275544 19400 ?        Sl   20:08   0:00 /usr/libexec/ibus-x11
pradita+    2920    2924  0.0    4  0.4 275544 19400 ?        Sl   20:08   0:00 /usr/libexec/ibus-x11
pradita+    2920    2926  0.0    4  0.4 275544 19400 ?        Sl   20:08   0:00 /usr/libexec/ibus-x11
pradita+    2925    2925  0.0   11  1.0 1128036 43504 ?       Sl   20:08   0:00 /usr/libexec/mutter-x11-frames
pradita+    2925    2928  0.0   11  1.0 1128036 43504 ?       Sl   20:08   0:00 /usr/libexec/mutter-x11-frames
pradita+    2925    2941  0.0   11  1.0 1128036 43504 ?       Sl   20:08   0:00 /usr/libexec/mutter-x11-frames
pradita+    2925    2942  0.0   11  1.0 1128036 43504 ?       Sl   20:08   0:00 /usr/libexec/mutter-x11-frames
pradita+    2925    2943  0.0   11  1.0 1128036 43504 ?       Sl   20:08   0:00 /usr/libexec/mutter-x11-frames
pradita+    2925    2944  0.0   11  1.0 1128036 43504 ?       Sl   20:08   0:00 /usr/libexec/mutter-x11-frames
pradita+    2925    2945  0.0   11  1.0 1128036 43504 ?       SNl  20:08   0:00 /usr/libexec/mutter-x11-frames
pradita+    2925    2951  0.0   11  1.0 1128036 43504 ?       Sl   20:08   0:00 /usr/libexec/mutter-x11-frames
pradita+    2925    2952  0.0   11  1.0 1128036 43504 ?       Sl   20:08   0:00 /usr/libexec/mutter-x11-frames
pradita+    2925    2953  0.0   11  1.0 1128036 43504 ?       Sl   20:08   0:00 /usr/libexec/mutter-x11-frames
pradita+    2925    2954  0.0   11  1.0 1128036 43504 ?       Sl   20:08   0:00 /usr/libexec/mutter-x11-frames
pradita+    2929    2929  0.0    1  0.1  19936  5036 pts/0    Ss   20:08   0:00 bash
pradita+    2956    2956  6.0   99  8.4 11969580 340668 ?     Sl   20:08   0:20 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3013  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3017  0.6   99  8.4 11969580 340668 ?     Sl   20:08   0:02 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3018  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3019  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3020  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3035  0.6   99  8.4 11969580 340668 ?     Sl   20:08   0:02 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3037  0.4   99  8.4 11969580 340668 ?     Sl   20:08   0:01 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3038  0.1   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3039  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3040  0.7   99  8.4 11969580 340668 ?     Sl   20:08   0:02 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3041  0.4   99  8.4 11969580 340668 ?     Sl   20:08   0:01 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3051  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3052  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3057  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3059  0.5   99  8.4 11969580 340668 ?     Sl   20:08   0:01 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3060  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3064  0.2   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3065  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3067  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3068  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3074  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3075  1.7   99  8.4 11969580 340668 ?     Sl   20:08   0:06 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3076  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3077  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3078  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3079  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3080  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3081  0.5   99  8.4 11969580 340668 ?     Sl   20:08   0:01 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3082  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3083  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3084  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3085  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3092  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3099  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3104  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3121  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3122  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3125  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3126  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3135  0.4   99  8.4 11969580 340668 ?     Sl   20:08   0:01 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3137  0.6   99  8.4 11969580 340668 ?     Sl   20:08   0:02 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3138  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3139  0.5   99  8.4 11969580 340668 ?     Sl   20:08   0:01 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3140  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3141  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3142  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3143  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3144  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3158  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3165  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3312  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3318  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3319  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3328  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3346  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3347  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3488  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3489  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3491  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3505  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3520  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3524  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3525  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3537  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3538  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3539  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3540  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3541  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3542  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3543  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3544  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3741  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3743  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3757  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3928  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3934  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3957  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3958  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3959  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3960  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3961  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3962  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3963  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3964  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3965  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3966  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3967  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    3968  0.0   99  8.4 11969580 340668 ?     Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    4042  0.0   99  8.4 11969580 340668 ?     Sl   20:10   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    4084  0.1   99  8.4 11969580 340668 ?     Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    4119  0.0   99  8.4 11969580 340668 ?     Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    4150  0.0   99  8.4 11969580 340668 ?     Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    4151  0.0   99  8.4 11969580 340668 ?     Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    4165  0.0   99  8.4 11969580 340668 ?     Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    4178  0.0   99  8.4 11969580 340668 ?     Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    4915  0.6   99  8.4 11969580 340668 ?     Sl   20:13   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    4920  0.0   99  8.4 11969580 340668 ?     Sl   20:13   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2956    4922  0.3   99  8.4 11969580 340668 ?     Sl   20:13   0:00 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    3015    3015  0.0    2  0.0 149172  1348 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/crashhelper 2956 9 /tmp/ 11
pradita+    3015    3016  0.0    2  0.0 149172  1348 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/crashhelper 2956 9 /tmp/ 11
pradita+    3086    3086  0.0    1  0.6 443020 24264 ?        S    20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -ipcHandle 0 -sig
pradita+    3093    3093  0.0    6  0.7 456440 31004 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3093    3096  0.0    6  0.7 456440 31004 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3093    3098  0.0    6  0.7 456440 31004 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3093    3103  0.0    6  0.7 456440 31004 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3093    3105  0.0    6  0.7 456440 31004 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3093    3592  0.0    6  0.7 456440 31004 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3115    3115  0.4   16  2.4 2601788 97164 ?       Sl   20:08   0:01 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3118  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3120  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3131  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3132  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3133  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3136  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3145  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3146  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3147  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3149  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3150  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3151  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3152  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3153  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3115    3584  0.0   16  2.4 2601788 97164 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3123    3123  0.0    5  0.8 589448 35740 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3123    3128  0.0    5  0.8 589448 35740 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3123    3130  0.0    5  0.8 589448 35740 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3123    3156  0.0    5  0.8 589448 35740 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3123    3593  0.0    5  0.8 589448 35740 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3170    3170  0.0    7  0.2 1691764 11612 ?       Sl   20:08   0:00 /usr/bin/snap userd
pradita+    3170    3171  0.0    7  0.2 1691764 11612 ?       Sl   20:08   0:00 /usr/bin/snap userd
pradita+    3170    3172  0.0    7  0.2 1691764 11612 ?       Sl   20:08   0:00 /usr/bin/snap userd
pradita+    3170    3173  0.0    7  0.2 1691764 11612 ?       Sl   20:08   0:00 /usr/bin/snap userd
pradita+    3170    3174  0.0    7  0.2 1691764 11612 ?       Sl   20:08   0:00 /usr/bin/snap userd
pradita+    3170    3175  0.0    7  0.2 1691764 11612 ?       Sl   20:08   0:00 /usr/bin/snap userd
pradita+    3170    3176  0.0    7  0.2 1691764 11612 ?       Sl   20:08   0:00 /usr/bin/snap userd
pradita+    3322    3322  0.2   17  2.0 2611804 81496 ?       Sl   20:08   0:01 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3325  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3327  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3329  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3330  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3331  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3333  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3337  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3338  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3339  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3340  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3341  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3342  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3343  0.1   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3344  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    3583  0.0   17  2.0 2611804 81496 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3322    4953  0.0   17  2.0 2611804 81496 ?       Sl   20:14   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3517  3.4   20  5.0 2910068 202280 ?      Sl   20:08   0:11 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3521  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3523  0.2   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3526  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3527  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3528  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3530  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3531  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3532  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3533  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3534  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3535  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3536  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3545  1.0   20  5.0 2910068 202280 ?      Sl   20:08   0:03 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3546  0.2   20  5.0 2910068 202280 ?      Sl   20:08   0:01 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3585  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    3594  0.0   20  5.0 2910068 202280 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    4065  0.0   20  5.0 2910068 202280 ?      Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    4079  0.1   20  5.0 2910068 202280 ?      Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3517    4080  0.0   20  5.0 2910068 202280 ?      Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3734    3734  0.0    5  0.7 456436 30852 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3734    3737  0.0    5  0.7 456436 30852 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3734    3739  0.0    5  0.7 456436 30852 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3734    3758  0.0    5  0.7 456436 30852 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3734    3969  0.0    5  0.7 456436 30852 ?        Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -parentBuildID 20
pradita+    3744    3744  1.0   18  3.9 7047436 160344 ?      Sl   20:08   0:03 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3753  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3756  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3760  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3761  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3763  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3765  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3767  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3770  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3771  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3774  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3775  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3776  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3777  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3779  0.1   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    3780  0.0   18  3.9 7047436 160344 ?      Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    4112  0.0   18  3.9 7047436 160344 ?      Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3744    4116  0.4   18  3.9 7047436 160344 ?      Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3927  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3931  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3933  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3935  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3936  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3937  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3939  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3948  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3949  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3950  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3951  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3952  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3953  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3954  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3927    3955  0.0   15  1.4 2568132 56808 ?       Sl   20:08   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    3973    3973  0.1    5  0.5 575936 21348 ?        Sl   20:09   0:00 /usr/bin/update-notifier
pradita+    3973    3986  0.0    5  0.5 575936 21348 ?        Sl   20:09   0:00 /usr/bin/update-notifier
pradita+    3973    3987  0.0    5  0.5 575936 21348 ?        Sl   20:09   0:00 /usr/bin/update-notifier
pradita+    3973    3989  0.0    5  0.5 575936 21348 ?        Sl   20:09   0:00 /usr/bin/update-notifier
pradita+    3973    3990  0.0    5  0.5 575936 21348 ?        Sl   20:09   0:00 /usr/bin/update-notifier
root        4035    4035  0.0    1  0.0      0     0 ?        I<   20:09   0:00 [kworker/1:2H-kblockd]
pradita+    4085    4085  0.3    5  0.2 128568  8984 ?        Ssl  20:11   0:00 /usr/bin/speech-dispatcher -s -t 0
pradita+    4085    4107  0.0    5  0.2 128568  8984 ?        Ssl  20:11   0:00 /usr/bin/speech-dispatcher -s -t 0
pradita+    4085    4108  0.0    5  0.2 128568  8984 ?        Ssl  20:11   0:00 /usr/bin/speech-dispatcher -s -t 0
pradita+    4085    4109  0.0    5  0.2 128568  8984 ?        Ssl  20:11   0:00 /usr/bin/speech-dispatcher -s -t 0
pradita+    4085    4110  0.0    5  0.2 128568  8984 ?        Ssl  20:11   0:00 /usr/bin/speech-dispatcher -s -t 0
pradita+    4097    4097  0.0    1  0.0      0     0 ?        Z    20:11   0:00 [sd_espeak-ng-mb] <defunct>
pradita+    4100    4100  0.0    2  0.2 116052  9232 ?        Sl   20:11   0:00 /usr/lib/speech-dispatcher-modules/sd_espeak-ng /etc/speech-dispatcher/mo
pradita+    4100    4101  0.0    2  0.2 116052  9232 ?        Sl   20:11   0:00 /usr/lib/speech-dispatcher-modules/sd_espeak-ng /etc/speech-dispatcher/mo
pradita+    4103    4103  0.0    3  0.1 162700  5428 ?        Sl   20:11   0:00 /usr/lib/speech-dispatcher-modules/sd_dummy /etc/speech-dispatcher/module
pradita+    4103    4104  0.0    3  0.1 162700  5428 ?        Sl   20:11   0:00 /usr/lib/speech-dispatcher-modules/sd_dummy /etc/speech-dispatcher/module
pradita+    4103    4105  0.0    3  0.1 162700  5428 ?        Sl   20:11   0:00 /usr/lib/speech-dispatcher-modules/sd_dummy /etc/speech-dispatcher/module
pradita+    4106    4106  0.0    1  0.0   5676  2736 ?        S    20:11   0:00 /usr/lib/speech-dispatcher-modules/sd_openjtalk /etc/speech-dispatcher/mo
pradita+    4118    4118  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4122  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4124  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4125  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4126  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4127  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4128  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4129  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4130  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4131  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4132  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4133  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4134  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4135  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4136  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4118    4137  0.0   16  1.3 2568148 56108 ?       Sl   20:11   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4172  0.1   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4175  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4177  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4179  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4180  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4181  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4182  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4183  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4184  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4185  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4186  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4187  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4188  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4189  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4190  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
pradita+    4172    4191  0.0   16  1.5 2568148 61784 ?       Sl   20:12   0:00 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -pr
root        4225    4225  0.9    1  0.0      0     0 ?        I    20:12   0:00 [kworker/u10:0-ext4-rsv-conversion]
pradita+    4353    4353  7.5   39  4.3 1478273340 174132 ?   SLsl 20:13   0:05 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4354  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4357  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4358  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4359  0.5   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4360  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4361  0.6   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4362  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4363  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4364  0.3   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4365  0.2   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4366  0.2   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4367  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4368  0.2   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4377  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4378  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4379  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4380  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4381  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4382  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4383  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4384  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4387  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4388  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4390  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4395  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4396  0.1   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4397  0.1   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4398  0.1   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4399  0.1   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4400  0.1   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4420  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4421  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4425  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4426  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4427  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4428  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4445  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4353    4459  0.0   39  4.3 1478273340 174132 ?   SLsl 20:13   0:00 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-
pradita+    4355    4355  0.1    1  1.2 33805580 49076 ?      S    20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-zygote-sandbox --no
pradita+    4356    4356  0.0    1  1.2 33805596 50480 ?      S    20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4370    4370  0.0    3  0.0 33576468 3308 ?       Sl   20:13   0:00 /snap/code/228/usr/share/code/chrome_crashpad_handler --monitor-self-anno
pradita+    4370    4371  0.0    3  0.0 33576468 3308 ?       Sl   20:13   0:00 /snap/code/228/usr/share/code/chrome_crashpad_handler --monitor-self-anno
pradita+    4370    4372  0.0    3  0.0 33576468 3308 ?       Sl   20:13   0:00 /snap/code/228/usr/share/code/chrome_crashpad_handler --monitor-self-anno
pradita+    4403    4403  0.0    8  1.8 33863948 75332 ?      Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=network.mojom.NetworkSer
pradita+    4403    4416  0.0    8  1.8 33863948 75332 ?      Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=network.mojom.NetworkSer
pradita+    4403    4417  0.0    8  1.8 33863948 75332 ?      Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=network.mojom.NetworkSer
pradita+    4403    4418  0.0    8  1.8 33863948 75332 ?      Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=network.mojom.NetworkSer
pradita+    4403    4419  1.0    8  1.8 33863948 75332 ?      Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=network.mojom.NetworkSer
pradita+    4403    4422  0.0    8  1.8 33863948 75332 ?      Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=network.mojom.NetworkSer
pradita+    4403    4423  0.0    8  1.8 33863948 75332 ?      Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=network.mojom.NetworkSer
pradita+    4403    4424  0.0    8  1.8 33863948 75332 ?      Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=network.mojom.NetworkSer
pradita+    4446    4446 19.4   15 10.4 1463055680 417732 ?   Sl   20:13   0:13 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4460  0.0   15 10.4 1463055680 417732 ?   Sl   20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4461  0.0   15 10.4 1463055680 417732 ?   Sl   20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4462  4.0   15 10.4 1463055680 417732 ?   Sl   20:13   0:02 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4463  0.8   15 10.4 1463055680 417732 ?   Sl   20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4464  2.0   15 10.4 1463055680 417732 ?   Sl   20:13   0:01 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4474  4.4   15 10.4 1463055680 417732 ?   Sl   20:13   0:02 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4475  0.0   15 10.4 1463055680 417732 ?   Sl   20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4481  1.3   15 10.4 1463055680 417732 ?   Sl   20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4498  0.2   15 10.4 1463055680 417732 ?   Sl   20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4752  0.3   15 10.4 1463055680 417732 ?   Sl   20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4913  0.0   15 10.4 1463055680 417732 ?   Sl   20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4916  0.2   15 10.4 1463055680 417732 ?   Sl   20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4917  0.0   15 10.4 1463055680 417732 ?   Sl   20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4446    4918  1.9   15 10.4 1463055680 417732 ?   Sl   20:13   0:00 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    4480    4480  0.3   11  2.7 33932112 110784 ?     Sl   20:13   0:00 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --oz
pradita+    4480    4484  0.0   11  2.7 33932112 110784 ?     Sl   20:13   0:00 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --oz
pradita+    4480    4485  0.0   11  2.7 33932112 110784 ?     Sl   20:13   0:00 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --oz
pradita+    4480    4486  0.0   11  2.7 33932112 110784 ?     Sl   20:13   0:00 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --oz
pradita+    4480    4487  0.0   11  2.7 33932112 110784 ?     Sl   20:13   0:00 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --oz
pradita+    4480    4489  0.0   11  2.7 33932112 110784 ?     Sl   20:13   0:00 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --oz
pradita+    4480    4490  0.0   11  2.7 33932112 110784 ?     Sl   20:13   0:00 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --oz
pradita+    4480    4491  0.0   11  2.7 33932112 110784 ?     Sl   20:13   0:00 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --oz
pradita+    4480    4492  0.0   11  2.7 33932112 110784 ?     Sl   20:13   0:00 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --oz
pradita+    4480    4493  0.8   11  2.7 33932112 110784 ?     Sl   20:13   0:00 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --oz
pradita+    4480    4494  5.3   11  2.7 33932112 110784 ?     Sl   20:13   0:03 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --oz
pradita+    4508    4508  8.2   19  2.9 1461316216 117872 ?   Sl   20:13   0:04 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4521  0.0   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4522  0.0   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4523  0.0   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4524  0.1   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4526  0.0   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4527  1.0   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4528  0.8   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4529  0.9   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4530  0.0   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4531  0.0   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4532  0.0   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4533  0.0   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4553  0.3   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4559  0.2   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4560  0.2   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4561  0.2   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4562  0.2   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4508    4564  0.0   19  2.9 1461316216 117872 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4509  0.8   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4510  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4511  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4512  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4513  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4514  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4515  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4516  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4517  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4518  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4519  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4520  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4525  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4534  0.2   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4536  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4537  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4538  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4539  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4540  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4923  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4509    4924  0.0   21  2.7 1478110416 108896 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4535 19.4   19 10.8 1478097100 436448 ?   Sl   20:13   0:11 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4541  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4542  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4543  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4544  0.2   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4545  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4546  1.3   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4547  1.2   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4548  1.1   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4549  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4550  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4551  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4552  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4554  0.6   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4555  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4556  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4557  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4558  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
pradita+    4535    4563  0.0   19 10.8 1478097100 436448 ?   Sl   20:13   0:00 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService -
root        4755    4755  0.0    1  0.0      0     0 ?        I    20:13   0:00 [kworker/u9:3]
root        4758    4758  0.2    1  0.0      0     0 ?        I    20:13   0:00 [kworker/0:0-events]
root        4899    4899  0.0    1  0.0      0     0 ?        S    20:13   0:00 [psimon]
root        4912    4912  0.5    1  0.0      0     0 ?        I<   20:13   0:00 [kworker/0:1H-kblockd]
pradita+    4926    4926  2.9    8  2.2 1459515644 91764 ?    Sl   20:13   0:00 /snap/code/228/usr/share/code/code /snap/code/228/usr/share/code/resource
pradita+    4926    4927  0.0    8  2.2 1459515644 91764 ?    Sl   20:13   0:00 /snap/code/228/usr/share/code/code /snap/code/228/usr/share/code/resource
pradita+    4926    4928  0.0    8  2.2 1459515644 91764 ?    Sl   20:13   0:00 /snap/code/228/usr/share/code/code /snap/code/228/usr/share/code/resource
pradita+    4926    4929  0.0    8  2.2 1459515644 91764 ?    Sl   20:13   0:00 /snap/code/228/usr/share/code/code /snap/code/228/usr/share/code/resource
pradita+    4926    4930  0.0    8  2.2 1459515644 91764 ?    Sl   20:13   0:00 /snap/code/228/usr/share/code/code /snap/code/228/usr/share/code/resource
pradita+    4926    4931  0.0    8  2.2 1459515644 91764 ?    Sl   20:13   0:00 /snap/code/228/usr/share/code/code /snap/code/228/usr/share/code/resource
pradita+    4926    4932  0.0    8  2.2 1459515644 91764 ?    Sl   20:13   0:00 /snap/code/228/usr/share/code/code /snap/code/228/usr/share/code/resource
pradita+    4926    4933  0.0    8  2.2 1459515644 91764 ?    Sl   20:13   0:00 /snap/code/228/usr/share/code/code /snap/code/228/usr/share/code/resource
pradita+    4991    4991  100    1  0.1  25344  7756 pts/0    R+   20:14   0:00 ps aux -L
```

</details>

### 3. Lihat PID shell aktif dan detail prosesnya

```
praditadf@praditadf-VirtualBox:~$ echo $$
2929
praditadf@praditadf-VirtualBox:~$ ps -p $$ -f
UID          PID    PPID  C STIME TTY          TIME CMD
pradita+    2929    2888  0 20:08 pts/0    00:00:00 bash
```

### 4. Lihat hierarki proses secara visual

```
praditadf@praditadf-VirtualBox:~$ pstree -p
systemd(1)─┬─ModemManager(874)─┬─{ModemManager}(924)
           │                   ├─{ModemManager}(928)
           │                   └─{ModemManager}(933)
           ├─NetworkManager(778)─┬─{NetworkManager}(919)
           │                     ├─{NetworkManager}(920)
           │                     └─{NetworkManager}(921)
           ├─accounts-daemon(672)─┬─{accounts-daemon}(731)
           │                      ├─{accounts-daemon}(732)
           │                      └─{accounts-daemon}(734)
           ├─avahi-daemon(620)───avahi-daemon(762)
           ├─colord(1428)─┬─{colord}(1433)
           │              ├─{colord}(1434)
           │              └─{colord}(1436)
           ├─cron(675)
           ├─cups-browsed(1239)─┬─{cups-browsed}(1255)
           │                    ├─{cups-browsed}(1256)
           │                    └─{cups-browsed}(1257)
           ├─cupsd(1215)
           ├─dbus-daemon(621)
           ├─gdm3(1235)─┬─gdm-session-wor(1793)─┬─gdm-wayland-ses(1900)─┬─gnome-session-b(1919)─┬─{gnome-session-b}(1981)
           │            │                       │                       │                       ├─{gnome-session-b}(1982)
           │            │                       │                       │                       └─{gnome-session-b}(1983)
           │            │                       │                       ├─{gdm-wayland-ses}(1901)
           │            │                       │                       ├─{gdm-wayland-ses}(1903)
           │            │                       │                       └─{gdm-wayland-ses}(1917)
           │            │                       ├─{gdm-session-wor}(1794)
           │            │                       ├─{gdm-session-wor}(1795)
           │            │                       └─{gdm-session-wor}(1796)
           │            ├─{gdm3}(1237)
           │            ├─{gdm3}(1238)
           │            └─{gdm3}(1240)
```

<details>
<summary><b>Read More</b></summary>
<br>

```
           ├─gnome-remote-de(625)─┬─{gnome-remote-de}(884)
           │                      ├─{gnome-remote-de}(895)
           │                      └─{gnome-remote-de}(901)
           ├─kerneloops(1245)
           ├─kerneloops(1249)
           ├─polkitd(645)─┬─{polkitd}(822)
           │              ├─{polkitd}(823)
           │              └─{polkitd}(827)
           ├─power-profiles-(657)─┬─{power-profiles-}(678)
           │                      ├─{power-profiles-}(679)
           │                      └─{power-profiles-}(681)
           ├─rsyslogd(749)─┬─{rsyslogd}(811)
           │               ├─{rsyslogd}(813)
           │               └─{rsyslogd}(814)
           ├─rtkit-daemon(1316)─┬─{rtkit-daemon}(1323)
           │                    └─{rtkit-daemon}(1324)
           ├─snapd(668)─┬─{snapd}(708)
           │            ├─{snapd}(711)
           │            ├─{snapd}(712)
           │            ├─{snapd}(720)
           │            ├─{snapd}(781)
           │            ├─{snapd}(783)
           │            ├─{snapd}(904)
           │            ├─{snapd}(1425)
           │            └─{snapd}(4223)
           ├─switcheroo-cont(691)─┬─{switcheroo-cont}(730)
           │                      ├─{switcheroo-cont}(735)
           │                      └─{switcheroo-cont}(737)
           ├─systemd(1808)─┬─(sd-pam)(1817)
           │               ├─at-spi2-registr(2137)─┬─{at-spi2-registr}(2138)
           │               │                       ├─{at-spi2-registr}(2139)
           │               │                       └─{at-spi2-registr}(2140)
           │               ├─chrome_crashpad(4370)─┬─{chrome_crashpad}(4371)
           │               │                       └─{chrome_crashpad}(4372)
           │               ├─code(4353)─┬─code(4355)
           │               │            ├─code(4356)───code(4446)─┬─{code}(4460)
           │               │            │                         ├─{code}(4461)
           │               │            │                         ├─{code}(4462)
           │               │            │                         ├─{code}(4463)
           │               │            │                         ├─{code}(4464)
           │               │            │                         ├─{code}(4474)
           │               │            │                         ├─{code}(4475)
           │               │            │                         ├─{code}(4481)
           │               │            │                         ├─{code}(4752)
           │               │            │                         ├─{code}(4913)
           │               │            │                         └─{code}(4918)
           │               │            ├─code(4403)─┬─{code}(4416)
           │               │            │            ├─{code}(4417)
           │               │            │            ├─{code}(4418)
           │               │            │            ├─{code}(4419)
           │               │            │            ├─{code}(4422)
           │               │            │            ├─{code}(4423)
           │               │            │            └─{code}(4424)
           │               │            ├─code(4480)─┬─{code}(4484)
           │               │            │            ├─{code}(4485)
           │               │            │            ├─{code}(4486)
           │               │            │            ├─{code}(4487)
           │               │            │            ├─{code}(4489)
           │               │            │            ├─{code}(4490)
           │               │            │            ├─{code}(4491)
           │               │            │            ├─{code}(4492)
           │               │            │            ├─{code}(4493)
           │               │            │            └─{code}(4494)
           │               │            ├─code(4508)─┬─{code}(4521)
           │               │            │            ├─{code}(4522)
           │               │            │            ├─{code}(4523)
           │               │            │            ├─{code}(4524)
           │               │            │            ├─{code}(4526)
           │               │            │            ├─{code}(4527)
           │               │            │            ├─{code}(4528)
           │               │            │            ├─{code}(4529)
           │               │            │            ├─{code}(4530)
           │               │            │            ├─{code}(4531)
           │               │            │            ├─{code}(4532)
           │               │            │            ├─{code}(4533)
           │               │            │            ├─{code}(4553)
           │               │            │            ├─{code}(4559)
           │               │            │            ├─{code}(4560)
           │               │            │            ├─{code}(4561)
           │               │            │            ├─{code}(4562)
           │               │            │            └─{code}(4564)
           │               │            ├─code(4509)─┬─{code}(4510)
           │               │            │            ├─{code}(4511)
           │               │            │            ├─{code}(4512)
           │               │            │            ├─{code}(4513)
           │               │            │            ├─{code}(4514)
           │               │            │            ├─{code}(4515)
           │               │            │            ├─{code}(4516)
           │               │            │            ├─{code}(4517)
           │               │            │            ├─{code}(4518)
           │               │            │            ├─{code}(4519)
           │               │            │            ├─{code}(4520)
           │               │            │            ├─{code}(4525)
           │               │            │            ├─{code}(4534)
           │               │            │            ├─{code}(4536)
           │               │            │            ├─{code}(4537)
           │               │            │            ├─{code}(4538)
           │               │            │            ├─{code}(4539)
           │               │            │            ├─{code}(4540)
           │               │            │            ├─{code}(4923)
           │               │            │            └─{code}(4924)
           │               │            ├─code(4535)─┬─code(4926)─┬─{code}(4927)
           │               │            │            │            ├─{code}(4928)
           │               │            │            │            ├─{code}(4929)
           │               │            │            │            ├─{code}(4930)
           │               │            │            │            ├─{code}(4931)
           │               │            │            │            ├─{code}(4932)
           │               │            │            │            └─{code}(4933)
           │               │            │            ├─{code}(4541)
           │               │            │            ├─{code}(4542)
           │               │            │            ├─{code}(4543)
           │               │            │            ├─{code}(4544)
           │               │            │            ├─{code}(4545)
           │               │            │            ├─{code}(4546)
           │               │            │            ├─{code}(4547)
           │               │            │            ├─{code}(4548)
           │               │            │            ├─{code}(4549)
           │               │            │            ├─{code}(4550)
           │               │            │            ├─{code}(4551)
           │               │            │            ├─{code}(4552)
           │               │            │            ├─{code}(4554)
           │               │            │            ├─{code}(4555)
           │               │            │            ├─{code}(4556)
           │               │            │            ├─{code}(4557)
           │               │            │            ├─{code}(4558)
           │               │            │            └─{code}(4563)
           │               │            ├─{code}(4354)
           │               │            ├─{code}(4357)
           │               │            ├─{code}(4358)
           │               │            ├─{code}(4359)
           │               │            ├─{code}(4360)
           │               │            ├─{code}(4361)
           │               │            ├─{code}(4362)
           │               │            ├─{code}(4363)
           │               │            ├─{code}(4364)
           │               │            ├─{code}(4365)
           │               │            ├─{code}(4366)
           │               │            ├─{code}(4367)
           │               │            ├─{code}(4368)
           │               │            ├─{code}(4377)
           │               │            ├─{code}(4378)
           │               │            ├─{code}(4379)
           │               │            ├─{code}(4380)
           │               │            ├─{code}(4381)
           │               │            ├─{code}(4382)
           │               │            ├─{code}(4383)
           │               │            ├─{code}(4384)
           │               │            ├─{code}(4387)
           │               │            ├─{code}(4388)
           │               │            ├─{code}(4390)
           │               │            ├─{code}(4395)
           │               │            ├─{code}(4396)
           │               │            ├─{code}(4397)
           │               │            ├─{code}(4398)
           │               │            ├─{code}(4399)
           │               │            ├─{code}(4400)
           │               │            ├─{code}(4420)
           │               │            ├─{code}(4421)
           │               │            ├─{code}(4425)
           │               │            ├─{code}(4426)
           │               │            ├─{code}(4427)
           │               │            ├─{code}(4428)
           │               │            ├─{code}(4445)
           │               │            └─{code}(4459)
           │               ├─crashhelper(3015)───{crashhelper}(3016)
           │               ├─dbus-daemon(1848)
           │               ├─dconf-service(2568)─┬─{dconf-service}(2569)
           │               │                     ├─{dconf-service}(2570)
           │               │                     └─{dconf-service}(2571)
           │               ├─evolution-addre(2456)─┬─{evolution-addre}(2476)
           │               │                       ├─{evolution-addre}(2477)
           │               │                       ├─{evolution-addre}(2483)
           │               │                       ├─{evolution-addre}(2492)
           │               │                       ├─{evolution-addre}(2493)
           │               │                       └─{evolution-addre}(2508)
           │               ├─evolution-calen(2328)─┬─{evolution-calen}(2365)
           │               │                       ├─{evolution-calen}(2367)
           │               │                       ├─{evolution-calen}(2402)
           │               │                       ├─{evolution-calen}(2440)
           │               │                       ├─{evolution-calen}(2441)
           │               │                       ├─{evolution-calen}(2448)
           │               │                       ├─{evolution-calen}(2454)
           │               │                       ├─{evolution-calen}(2455)
           │               │                       └─{evolution-calen}(2463)
           │               ├─evolution-sourc(2162)─┬─{evolution-sourc}(2165)
           │               │                       ├─{evolution-sourc}(2166)
           │               │                       ├─{evolution-sourc}(2167)
           │               │                       └─{evolution-sourc}(2168)
           │               ├─gcr-ssh-agent(1984)─┬─{gcr-ssh-agent}(1989)
           │               │                     └─{gcr-ssh-agent}(1991)
           │               ├─gjs(2173)─┬─{gjs}(2177)
           │               │           ├─{gjs}(2178)
           │               │           ├─{gjs}(2180)
           │               │           ├─{gjs}(2208)
           │               │           └─{gjs}(2209)
           │               ├─gjs(2592)─┬─{gjs}(2594)
           │               │           ├─{gjs}(2595)
           │               │           ├─{gjs}(2598)
           │               │           ├─{gjs}(2599)
           │               │           └─{gjs}(2600)
           │               ├─gnome-keyring-d(1849)─┬─{gnome-keyring-d}(1865)
           │               │                       ├─{gnome-keyring-d}(1866)
           │               │                       ├─{gnome-keyring-d}(1873)
           │               │                       └─{gnome-keyring-d}(1874)
           │               ├─gnome-session-b(2019)─┬─at-spi-bus-laun(2068)─┬─dbus-daemon(2084)
           │               │                       │                       ├─{at-spi-bus-laun}(2071)
           │               │                       │                       ├─{at-spi-bus-laun}(2074)
           │               │                       │                       ├─{at-spi-bus-laun}(2075)
           │               │                       │                       └─{at-spi-bus-laun}(2078)
           │               │                       ├─evolution-alarm(2217)─┬─{evolution-alarm}(2295)
           │               │                       │                       ├─{evolution-alarm}(2296)
           │               │                       │                       ├─{evolution-alarm}(2317)
           │               │                       │                       ├─{evolution-alarm}(2346)
           │               │                       │                       ├─{evolution-alarm}(2578)
           │               │                       │                       ├─{evolution-alarm}(2582)
           │               │                       │                       └─{evolution-alarm}(2583)
           │               │                       ├─gsd-disk-utilit(2219)─┬─{gsd-disk-utilit}(2254)
           │               │                       │                       ├─{gsd-disk-utilit}(2271)
           │               │                       │                       └─{gsd-disk-utilit}(2359)
           │               │                       ├─update-notifier(3973)─┬─{update-notifier}(3986)
           │               │                       │                       ├─{update-notifier}(3987)
           │               │                       │                       ├─{update-notifier}(3989)
           │               │                       │                       └─{update-notifier}(3990)
           │               │                       ├─{gnome-session-b}(2034)
           │               │                       ├─{gnome-session-b}(2035)
           │               │                       ├─{gnome-session-b}(2038)
           │               │                       └─{gnome-session-b}(2041)
           │               ├─gnome-session-c(1986)───{gnome-session-c}(1995)
           │               ├─gnome-shell(2067)─┬─Xwayland(2894)
           │               │                   ├─firefox(2956)─┬─forkserver(3086)─┬─Isolated Web Co(3517)─┬─{Isolated Web Co}(3521)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3523)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3526)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3527)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3528)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3530)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3531)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3532)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3533)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3534)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3535)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3536)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3545)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3546)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3585)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3594)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(4065)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(4079)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(4080)
           │               │                   │               │                  │                       └─{Isolated Web Co}(4996)
           │               │                   │               │                  ├─Isolated Web Co(3744)─┬─{Isolated Web Co}(3753)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3756)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3760)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3761)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3763)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3765)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3767)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3770)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3771)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3774)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3775)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3776)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3777)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3779)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(3780)
           │               │                   │               │                  │                       ├─{Isolated Web Co}(4112)
           │               │                   │               │                  │                       └─{Isolated Web Co}(4116)
           │               │                   │               │                  ├─Privileged Cont(3115)─┬─{Privileged Cont}(3118)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3120)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3131)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3132)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3133)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3136)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3145)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3146)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3147)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3149)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3150)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3151)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3152)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3153)
           │               │                   │               │                  │                       ├─{Privileged Cont}(3584)
           │               │                   │               │                  │                       └─{Privileged Cont}(4993)
           │               │                   │               │                  ├─RDD Process(3123)─┬─{RDD Process}(3128)
           │               │                   │               │                  │                   ├─{RDD Process}(3130)
           │               │                   │               │                  │                   ├─{RDD Process}(3156)
           │               │                   │               │                  │                   └─{RDD Process}(3593)
           │               │                   │               │                  ├─Socket Process(3093)─┬─{Socket Process}(3096)
           │               │                   │               │                  │                      ├─{Socket Process}(3098)
           │               │                   │               │                  │                      ├─{Socket Process}(3103)
           │               │                   │               │                  │                      ├─{Socket Process}(3105)
           │               │                   │               │                  │                      └─{Socket Process}(3592)
           │               │                   │               │                  ├─Utility Process(3734)─┬─{Utility Process}(3737)
           │               │                   │               │                  │                       ├─{Utility Process}(3739)
           │               │                   │               │                  │                       ├─{Utility Process}(3758)
           │               │                   │               │                  │                       └─{Utility Process}(3969)
           │               │                   │               │                  ├─Web Content(3927)─┬─{Web Content}(3931)
           │               │                   │               │                  │                   ├─{Web Content}(3933)
           │               │                   │               │                  │                   ├─{Web Content}(3935)
           │               │                   │               │                  │                   ├─{Web Content}(3936)
           │               │                   │               │                  │                   ├─{Web Content}(3937)
           │               │                   │               │                  │                   ├─{Web Content}(3939)
           │               │                   │               │                  │                   ├─{Web Content}(3948)
           │               │                   │               │                  │                   ├─{Web Content}(3949)
           │               │                   │               │                  │                   ├─{Web Content}(3950)
           │               │                   │               │                  │                   ├─{Web Content}(3951)
           │               │                   │               │                  │                   ├─{Web Content}(3952)
           │               │                   │               │                  │                   ├─{Web Content}(3953)
           │               │                   │               │                  │                   ├─{Web Content}(3954)
           │               │                   │               │                  │                   └─{Web Content}(3955)
           │               │                   │               │                  ├─Web Content(4118)─┬─{Web Content}(4122)
           │               │                   │               │                  │                   ├─{Web Content}(4124)
           │               │                   │               │                  │                   ├─{Web Content}(4125)
           │               │                   │               │                  │                   ├─{Web Content}(4126)
           │               │                   │               │                  │                   ├─{Web Content}(4127)
           │               │                   │               │                  │                   ├─{Web Content}(4128)
           │               │                   │               │                  │                   ├─{Web Content}(4129)
           │               │                   │               │                  │                   ├─{Web Content}(4130)
           │               │                   │               │                  │                   ├─{Web Content}(4131)
           │               │                   │               │                  │                   ├─{Web Content}(4132)
           │               │                   │               │                  │                   ├─{Web Content}(4133)
           │               │                   │               │                  │                   ├─{Web Content}(4134)
           │               │                   │               │                  │                   ├─{Web Content}(4135)
           │               │                   │               │                  │                   ├─{Web Content}(4136)
           │               │                   │               │                  │                   └─{Web Content}(4137)
           │               │                   │               │                  ├─Web Content(4172)─┬─{Web Content}(4175)
           │               │                   │               │                  │                   ├─{Web Content}(4177)
           │               │                   │               │                  │                   ├─{Web Content}(4179)
           │               │                   │               │                  │                   ├─{Web Content}(4180)
           │               │                   │               │                  │                   ├─{Web Content}(4181)
           │               │                   │               │                  │                   ├─{Web Content}(4182)
           │               │                   │               │                  │                   ├─{Web Content}(4183)
           │               │                   │               │                  │                   ├─{Web Content}(4184)
           │               │                   │               │                  │                   ├─{Web Content}(4185)
           │               │                   │               │                  │                   ├─{Web Content}(4186)
           │               │                   │               │                  │                   ├─{Web Content}(4187)
           │               │                   │               │                  │                   ├─{Web Content}(4188)
           │               │                   │               │                  │                   ├─{Web Content}(4189)
           │               │                   │               │                  │                   ├─{Web Content}(4190)
           │               │                   │               │                  │                   └─{Web Content}(4191)
           │               │                   │               │                  └─WebExtensions(3322)─┬─{WebExtensions}(3325)
           │               │                   │               │                                        ├─{WebExtensions}(3327)
           │               │                   │               │                                        ├─{WebExtensions}(3329)
           │               │                   │               │                                        ├─{WebExtensions}(3330)
           │               │                   │               │                                        ├─{WebExtensions}(3331)
           │               │                   │               │                                        ├─{WebExtensions}(3333)
           │               │                   │               │                                        ├─{WebExtensions}(3337)
           │               │                   │               │                                        ├─{WebExtensions}(3338)
           │               │                   │               │                                        ├─{WebExtensions}(3339)
           │               │                   │               │                                        ├─{WebExtensions}(3340)
           │               │                   │               │                                        ├─{WebExtensions}(3341)
           │               │                   │               │                                        ├─{WebExtensions}(3342)
           │               │                   │               │                                        ├─{WebExtensions}(3343)
           │               │                   │               │                                        ├─{WebExtensions}(3344)
           │               │                   │               │                                        └─{WebExtensions}(3583)
           │               │                   │               ├─{firefox}(3013)
           │               │                   │               ├─{firefox}(3017)
           │               │                   │               ├─{firefox}(3018)
           │               │                   │               ├─{firefox}(3019)
           │               │                   │               ├─{firefox}(3020)
           │               │                   │               ├─{firefox}(3035)
           │               │                   │               ├─{firefox}(3037)
           │               │                   │               ├─{firefox}(3038)
           │               │                   │               ├─{firefox}(3039)
           │               │                   │               ├─{firefox}(3040)
           │               │                   │               ├─{firefox}(3041)
           │               │                   │               ├─{firefox}(3051)
           │               │                   │               ├─{firefox}(3052)
           │               │                   │               ├─{firefox}(3057)
           │               │                   │               ├─{firefox}(3059)
           │               │                   │               ├─{firefox}(3060)
           │               │                   │               ├─{firefox}(3064)
           │               │                   │               ├─{firefox}(3065)
           │               │                   │               ├─{firefox}(3067)
           │               │                   │               ├─{firefox}(3068)
           │               │                   │               ├─{firefox}(3074)
           │               │                   │               ├─{firefox}(3075)
           │               │                   │               ├─{firefox}(3076)
           │               │                   │               ├─{firefox}(3077)
           │               │                   │               ├─{firefox}(3078)
           │               │                   │               ├─{firefox}(3079)
           │               │                   │               ├─{firefox}(3080)
           │               │                   │               ├─{firefox}(3081)
           │               │                   │               ├─{firefox}(3082)
           │               │                   │               ├─{firefox}(3083)
           │               │                   │               ├─{firefox}(3084)
           │               │                   │               ├─{firefox}(3085)
           │               │                   │               ├─{firefox}(3092)
           │               │                   │               ├─{firefox}(3099)
           │               │                   │               ├─{firefox}(3104)
           │               │                   │               ├─{firefox}(3121)
           │               │                   │               ├─{firefox}(3122)
           │               │                   │               ├─{firefox}(3125)
           │               │                   │               ├─{firefox}(3126)
           │               │                   │               ├─{firefox}(3135)
           │               │                   │               ├─{firefox}(3137)
           │               │                   │               ├─{firefox}(3138)
           │               │                   │               ├─{firefox}(3139)
           │               │                   │               ├─{firefox}(3140)
           │               │                   │               ├─{firefox}(3141)
           │               │                   │               ├─{firefox}(3142)
           │               │                   │               ├─{firefox}(3143)
           │               │                   │               ├─{firefox}(3144)
           │               │                   │               ├─{firefox}(3158)
           │               │                   │               ├─{firefox}(3165)
           │               │                   │               ├─{firefox}(3312)
           │               │                   │               ├─{firefox}(3318)
           │               │                   │               ├─{firefox}(3319)
           │               │                   │               ├─{firefox}(3328)
           │               │                   │               ├─{firefox}(3346)
           │               │                   │               ├─{firefox}(3347)
           │               │                   │               ├─{firefox}(3488)
           │               │                   │               ├─{firefox}(3489)
           │               │                   │               ├─{firefox}(3491)
           │               │                   │               ├─{firefox}(3505)
           │               │                   │               ├─{firefox}(3520)
           │               │                   │               ├─{firefox}(3524)
           │               │                   │               ├─{firefox}(3525)
           │               │                   │               ├─{firefox}(3537)
           │               │                   │               ├─{firefox}(3538)
           │               │                   │               ├─{firefox}(3539)
           │               │                   │               ├─{firefox}(3540)
           │               │                   │               ├─{firefox}(3541)
           │               │                   │               ├─{firefox}(3542)
           │               │                   │               ├─{firefox}(3543)
           │               │                   │               ├─{firefox}(3544)
           │               │                   │               ├─{firefox}(3741)
           │               │                   │               ├─{firefox}(3743)
           │               │                   │               ├─{firefox}(3757)
           │               │                   │               ├─{firefox}(3928)
           │               │                   │               ├─{firefox}(3934)
           │               │                   │               ├─{firefox}(3957)
           │               │                   │               ├─{firefox}(3958)
           │               │                   │               ├─{firefox}(3959)
           │               │                   │               ├─{firefox}(3960)
           │               │                   │               ├─{firefox}(3961)
           │               │                   │               ├─{firefox}(3962)
           │               │                   │               ├─{firefox}(3963)
           │               │                   │               ├─{firefox}(3964)
           │               │                   │               ├─{firefox}(3965)
           │               │                   │               ├─{firefox}(3966)
           │               │                   │               ├─{firefox}(3967)
           │               │                   │               ├─{firefox}(3968)
           │               │                   │               ├─{firefox}(4042)
           │               │                   │               ├─{firefox}(4084)
           │               │                   │               ├─{firefox}(4119)
           │               │                   │               ├─{firefox}(4150)
           │               │                   │               ├─{firefox}(4151)
           │               │                   │               ├─{firefox}(4165)
           │               │                   │               ├─{firefox}(4178)
           │               │                   │               ├─{firefox}(4994)
           │               │                   │               └─{firefox}(4995)
           │               │                   ├─gjs(2676)─┬─{gjs}(2692)
           │               │                   │           ├─{gjs}(2693)
           │               │                   │           ├─{gjs}(2694)
           │               │                   │           ├─{gjs}(2695)
           │               │                   │           ├─{gjs}(2696)
           │               │                   │           ├─{gjs}(2703)
           │               │                   │           └─{gjs}(2730)
           │               │                   ├─mutter-x11-fram(2925)─┬─{mutter-x11-fram}(2928)
           │               │                   │                       ├─{mutter-x11-fram}(2941)
           │               │                   │                       ├─{mutter-x11-fram}(2942)
           │               │                   │                       ├─{mutter-x11-fram}(2943)
           │               │                   │                       ├─{mutter-x11-fram}(2944)
           │               │                   │                       ├─{mutter-x11-fram}(2945)
           │               │                   │                       ├─{mutter-x11-fram}(2951)
           │               │                   │                       ├─{mutter-x11-fram}(2952)
           │               │                   │                       ├─{mutter-x11-fram}(2953)
           │               │                   │                       └─{mutter-x11-fram}(2954)
           │               │                   ├─{gnome-shell}(2080)
           │               │                   ├─{gnome-shell}(2081)
           │               │                   ├─{gnome-shell}(2085)
           │               │                   ├─{gnome-shell}(2086)
           │               │                   ├─{gnome-shell}(2087)
           │               │                   ├─{gnome-shell}(2088)
           │               │                   ├─{gnome-shell}(2094)
           │               │                   ├─{gnome-shell}(2100)
           │               │                   ├─{gnome-shell}(2101)
           │               │                   ├─{gnome-shell}(2102)
           │               │                   ├─{gnome-shell}(2103)
           │               │                   ├─{gnome-shell}(2104)
           │               │                   ├─{gnome-shell}(2109)
           │               │                   ├─{gnome-shell}(2575)
           │               │                   └─{gnome-shell}(2628)
           │               ├─gnome-shell-cal(2155)─┬─{gnome-shell-cal}(2156)
           │               │                       ├─{gnome-shell-cal}(2157)
           │               │                       ├─{gnome-shell-cal}(2159)
           │               │                       ├─{gnome-shell-cal}(2160)
           │               │                       ├─{gnome-shell-cal}(2161)
           │               │                       └─{gnome-shell-cal}(2324)
           │               ├─gnome-terminal-(2888)─┬─bash(2929)───pstree(5001)
           │               │                       ├─{gnome-terminal-}(2889)
           │               │                       ├─{gnome-terminal-}(2890)
           │               │                       ├─{gnome-terminal-}(2892)
           │               │                       ├─{gnome-terminal-}(2893)
           │               │                       ├─{gnome-terminal-}(2922)
           │               │                       └─{gnome-terminal-}(3087)
           │               ├─goa-daemon(2202)─┬─{goa-daemon}(2330)
           │               │                  ├─{goa-daemon}(2331)
           │               │                  ├─{goa-daemon}(2386)
           │               │                  └─{goa-daemon}(2392)
           │               ├─goa-identity-se(2398)─┬─{goa-identity-se}(2404)
           │               │                       ├─{goa-identity-se}(2405)
           │               │                       └─{goa-identity-se}(2421)
           │               ├─gsd-a11y-settin(2184)─┬─{gsd-a11y-settin}(2281)
           │               │                       ├─{gsd-a11y-settin}(2299)
           │               │                       ├─{gsd-a11y-settin}(2343)
           │               │                       └─{gsd-a11y-settin}(2356)
           │               ├─gsd-color(2185)─┬─{gsd-color}(2303)
           │               │                 ├─{gsd-color}(2322)
           │               │                 ├─{gsd-color}(2326)
           │               │                 └─{gsd-color}(2344)
           │               ├─gsd-datetime(2186)─┬─{gsd-datetime}(2311)
           │               │                    ├─{gsd-datetime}(2312)
           │               │                    ├─{gsd-datetime}(2339)
           │               │                    └─{gsd-datetime}(2350)
           │               ├─gsd-housekeepin(2187)─┬─{gsd-housekeepin}(2246)
           │               │                       ├─{gsd-housekeepin}(2247)
           │               │                       ├─{gsd-housekeepin}(2283)
           │               │                       └─{gsd-housekeepin}(2338)
           │               ├─gsd-keyboard(2188)─┬─{gsd-keyboard}(2301)
           │               │                    ├─{gsd-keyboard}(2304)
           │               │                    ├─{gsd-keyboard}(2310)
           │               │                    └─{gsd-keyboard}(2337)
           │               ├─gsd-media-keys(2189)─┬─{gsd-media-keys}(2265)
           │               │                      ├─{gsd-media-keys}(2266)
           │               │                      ├─{gsd-media-keys}(2268)
           │               │                      └─{gsd-media-keys}(2278)
           │               ├─gsd-power(2191)─┬─{gsd-power}(2290)
           │               │                 ├─{gsd-power}(2291)
           │               │                 ├─{gsd-power}(2293)
           │               │                 └─{gsd-power}(2341)
           │               ├─gsd-print-notif(2192)─┬─{gsd-print-notif}(2286)
           │               │                       ├─{gsd-print-notif}(2300)
           │               │                       └─{gsd-print-notif}(2342)
           │               ├─gsd-printer(2373)─┬─{gsd-printer}(2399)
           │               │                   ├─{gsd-printer}(2400)
           │               │                   └─{gsd-printer}(2423)
           │               ├─gsd-rfkill(2193)─┬─{gsd-rfkill}(2255)
           │               │                  ├─{gsd-rfkill}(2277)
           │               │                  └─{gsd-rfkill}(2327)
           │               ├─gsd-screensaver(2194)─┬─{gsd-screensaver}(2256)
           │               │                       ├─{gsd-screensaver}(2257)
           │               │                       └─{gsd-screensaver}(2285)
           │               ├─gsd-sharing(2195)─┬─{gsd-sharing}(2280)
           │               │                   ├─{gsd-sharing}(2282)
           │               │                   ├─{gsd-sharing}(2284)
           │               │                   └─{gsd-sharing}(2340)
           │               ├─gsd-smartcard(2196)─┬─{gsd-smartcard}(2261)
           │               │                     ├─{gsd-smartcard}(2264)
           │               │                     ├─{gsd-smartcard}(2279)
           │               │                     └─{gsd-smartcard}(2334)
           │               ├─gsd-sound(2197)─┬─{gsd-sound}(2298)
           │               │                 ├─{gsd-sound}(2321)
           │               │                 ├─{gsd-sound}(2345)
           │               │                 └─{gsd-sound}(2370)
           │               ├─gsd-wacom(2198)─┬─{gsd-wacom}(2252)
           │               │                 ├─{gsd-wacom}(2294)
           │               │                 ├─{gsd-wacom}(2302)
           │               │                 └─{gsd-wacom}(2336)
           │               ├─gsd-xsettings(2898)─┬─{gsd-xsettings}(2900)
           │               │                     ├─{gsd-xsettings}(2901)
           │               │                     ├─{gsd-xsettings}(2902)
           │               │                     └─{gsd-xsettings}(2903)
           │               ├─gvfs-afc-volume(2485)─┬─{gvfs-afc-volume}(2494)
           │               │                       ├─{gvfs-afc-volume}(2495)
           │               │                       ├─{gvfs-afc-volume}(2496)
           │               │                       └─{gvfs-afc-volume}(2498)
           │               ├─gvfs-goa-volume(2466)─┬─{gvfs-goa-volume}(2474)
           │               │                       ├─{gvfs-goa-volume}(2475)
           │               │                       └─{gvfs-goa-volume}(2478)
           │               ├─gvfs-gphoto2-vo(2515)─┬─{gvfs-gphoto2-vo}(2523)
           │               │                       ├─{gvfs-gphoto2-vo}(2527)
           │               │                       └─{gvfs-gphoto2-vo}(2529)
           │               ├─gvfs-mtp-volume(2501)─┬─{gvfs-mtp-volume}(2503)
           │               │                       ├─{gvfs-mtp-volume}(2504)
           │               │                       └─{gvfs-mtp-volume}(2507)
           │               ├─gvfs-udisks2-vo(2403)─┬─{gvfs-udisks2-vo}(2418)
           │               │                       ├─{gvfs-udisks2-vo}(2419)
           │               │                       ├─{gvfs-udisks2-vo}(2420)
           │               │                       └─{gvfs-udisks2-vo}(2447)
           │               ├─gvfsd(1999)─┬─gvfsd-trash(2606)─┬─{gvfsd-trash}(2607)
           │               │             │                   ├─{gvfsd-trash}(2608)
           │               │             │                   ├─{gvfsd-trash}(2609)
           │               │             │                   └─{gvfsd-trash}(2612)
           │               │             ├─{gvfsd}(2009)
           │               │             ├─{gvfsd}(2010)
           │               │             └─{gvfsd}(2012)
           │               ├─gvfsd-fuse(2017)─┬─{gvfsd-fuse}(2025)
           │               │                  ├─{gvfsd-fuse}(2026)
           │               │                  ├─{gvfsd-fuse}(2027)
           │               │                  ├─{gvfsd-fuse}(2028)
           │               │                  ├─{gvfsd-fuse}(2029)
           │               │                  └─{gvfsd-fuse}(2032)
           │               ├─gvfsd-metadata(2718)─┬─{gvfsd-metadata}(2719)
           │               │                      ├─{gvfsd-metadata}(2720)
           │               │                      └─{gvfsd-metadata}(2721)
           │               ├─ibus-daemon(2183)─┬─ibus-dconf(2348)─┬─{ibus-dconf}(2379)
           │               │                   │                  ├─{ibus-dconf}(2385)
           │               │                   │                  ├─{ibus-dconf}(2409)
           │               │                   │                  └─{ibus-dconf}(2438)
           │               │                   ├─ibus-engine-sim(2540)─┬─{ibus-engine-sim}(2547)
           │               │                   │                       ├─{ibus-engine-sim}(2549)
           │               │                   │                       └─{ibus-engine-sim}(2550)
           │               │                   ├─ibus-extension-(2357)─┬─{ibus-extension-}(2408)
           │               │                   │                       ├─{ibus-extension-}(2415)
           │               │                   │                       ├─{ibus-extension-}(2417)
           │               │                   │                       └─{ibus-extension-}(2424)
           │               │                   ├─{ibus-daemon}(2211)
           │               │                   ├─{ibus-daemon}(2212)
           │               │                   └─{ibus-daemon}(2227)
           │               ├─ibus-portal(2383)─┬─{ibus-portal}(2394)
           │               │                   ├─{ibus-portal}(2395)
           │               │                   └─{ibus-portal}(2401)
           │               ├─ibus-x11(2920)─┬─{ibus-x11}(2923)
           │               │                ├─{ibus-x11}(2924)
           │               │                └─{ibus-x11}(2926)
           │               ├─pipewire(1830)─┬─{pipewire}(1856)
           │               │                └─{pipewire}(1875)
           │               ├─pipewire(1843)─┬─{pipewire}(1857)
           │               │                └─{pipewire}(1858)
           │               ├─pipewire-pulse(1847)─┬─{pipewire-pulse}(1855)
           │               │                      └─{pipewire-pulse}(1876)
           │               ├─snap(3170)─┬─{snap}(3171)
           │               │            ├─{snap}(3172)
           │               │            ├─{snap}(3173)
           │               │            ├─{snap}(3174)
           │               │            ├─{snap}(3175)
           │               │            └─{snap}(3176)
           │               ├─snapd-desktop-i(2406)───snapd-desktop-i(2500)─┬─{snapd-desktop-i}(2524)
           │               │                                               ├─{snapd-desktop-i}(2525)
           │               │                                               ├─{snapd-desktop-i}(2526)
           │               │                                               └─{snapd-desktop-i}(2530)
           │               ├─speech-dispatch(4085)─┬─sd_dummy(4103)─┬─{sd_dummy}(4104)
           │               │                       │                └─{sd_dummy}(4105)
           │               │                       ├─sd_espeak-ng(4100)───{sd_espeak-ng}(4101)
           │               │                       ├─sd_espeak-ng-mb(4097)
           │               │                       ├─sd_openjtalk(4106)
           │               │                       ├─{speech-dispatch}(4107)
           │               │                       ├─{speech-dispatch}(4108)
           │               │                       ├─{speech-dispatch}(4109)
           │               │                       └─{speech-dispatch}(4110)
           │               ├─tracker-miner-f(2624)─┬─{tracker-miner-f}(2630)
           │               │                       ├─{tracker-miner-f}(2631)
           │               │                       ├─{tracker-miner-f}(2632)
           │               │                       ├─{tracker-miner-f}(2669)
           │               │                       ├─{tracker-miner-f}(2670)
           │               │                       ├─{tracker-miner-f}(2697)
           │               │                       └─{tracker-miner-f}(2699)
           │               ├─wireplumber(1846)─┬─{wireplumber}(1859)
           │               │                   ├─{wireplumber}(1862)
           │               │                   ├─{wireplumber}(1878)
           │               │                   ├─{wireplumber}(1881)
           │               │                   └─{wireplumber}(1883)
           │               ├─xdg-desktop-por(2625)─┬─{xdg-desktop-por}(2626)
           │               │                       ├─{xdg-desktop-por}(2629)
           │               │                       ├─{xdg-desktop-por}(2633)
           │               │                       ├─{xdg-desktop-por}(2711)
           │               │                       ├─{xdg-desktop-por}(2723)
           │               │                       └─{xdg-desktop-por}(2726)
           │               ├─xdg-desktop-por(2635)─┬─{xdg-desktop-por}(2661)
           │               │                       ├─{xdg-desktop-por}(2662)
           │               │                       ├─{xdg-desktop-por}(2664)
           │               │                       ├─{xdg-desktop-por}(2690)
           │               │                       └─{xdg-desktop-por}(2701)
           │               ├─xdg-desktop-por(2712)─┬─{xdg-desktop-por}(2713)
           │               │                       ├─{xdg-desktop-por}(2714)
           │               │                       ├─{xdg-desktop-por}(2716)
           │               │                       └─{xdg-desktop-por}(2717)
           │               ├─xdg-document-po(1892)─┬─fusermount3(1953)
           │               │                       ├─{xdg-document-po}(1924)
           │               │                       ├─{xdg-document-po}(1925)
           │               │                       ├─{xdg-document-po}(1926)
           │               │                       ├─{xdg-document-po}(1952)
           │               │                       ├─{xdg-document-po}(1955)
           │               │                       ├─{xdg-document-po}(1956)
           │               │                       └─{xdg-document-po}(1957)
           │               └─xdg-permission-(1930)─┬─{xdg-permission-}(1936)
           │                                       ├─{xdg-permission-}(1937)
           │                                       └─{xdg-permission-}(1941)
           ├─systemd-journal(244)
           ├─systemd-logind(718)
           ├─systemd-oomd(416)
           ├─systemd-resolve(419)
           ├─systemd-timesyn(421)───{systemd-timesyn}(462)
           ├─systemd-udevd(326)
           ├─udisksd(724)─┬─{udisksd}(746)
           │              ├─{udisksd}(747)
           │              ├─{udisksd}(750)
           │              ├─{udisksd}(863)
           │              └─{udisksd}(922)
           ├─unattended-upgr(1222)───{unattended-upgr}(1244)
           ├─upowerd(1468)─┬─{upowerd}(1512)
           │               ├─{upowerd}(1513)
           │               └─{upowerd}(1516)
           └─wpa_supplicant(787)

```

</details>

## Latihan 6.1

### Jalankan ps aux dan amati outputnya

#### 1. Berapa total proses yang berjalan? Proses apa yang memiliki PID terkecil?

> Total proses yang berjalan ada 225 proses yang didapatkan dengan menggunakan menjalankan perintah ws -l, dan proses dengan PID terkecil yaitu

```
root           1  0.3  0.3  23636 15016 ?        Ss   20:07   0:04 /sbin/init splash

```

#### 2. Jalankan pstree -p dan temukan proses bash Anda. Proses apa yang menjadi induk (PPID) dari bash tersebut?

```
|-gnome-terminal-(2806)-+-bash(2824)-+-grep(4979)
```

> Proses yang menjadi induk dari bash tersebut adalah gnome-terminal dengan PPID 2806

#### 3. Bandingkan output ps aux dan ps aux -L. Apa perbedaan yang Anda lihat?

```
ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
ps aux -L
USER         PID     LWP %CPU NLWP %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
```

> Perbedaan kedua output terdapat pada ps aux -L yang terdapat kolom LWP (Light-Weight Process ID)

## Praktikum 6.2 — Mengamati Siklus Hidup Proses

### 1. Buat proses di background dan amati kondisinya

```
praditadf@praditadf-VirtualBox:~$ sleep 60 &
[1] 5550

praditadf@praditadf-VirtualBox:~$ ps aux | grep sleep
pradita+    5550  0.0  0.0  16964  2152 pts/0    S    15:41   0:00 sleep 60
pradita+    5552  0.0  0.0  17820  2368 pts/0    S+   15:41   0:00 grep --color=auto sleep

```

### 2. Amati perubahan exit code dari perintah yang berhasil dan gagal

```
praditadf@praditadf-VirtualBox:~$ ls /tmp
mcp-17TKOP
snap-private-tmp
systemd-private-7683b1e18fdf4a54a239cfe856e4b968-colord.service-Wv1Orz
systemd-private-7683b1e18fdf4a54a239cfe856e4b968-fwupd.service-FGQJhy
systemd-private-7683b1e18fdf4a54a239cfe856e4b968-ModemManager.service-jaMIBR
systemd-private-7683b1e18fdf4a54a239cfe856e4b968-polkit.service-Nw5Fl7
systemd-private-7683b1e18fdf4a54a239cfe856e4b968-power-profiles-daemon.service-NWsPtX
systemd-private-7683b1e18fdf4a54a239cfe856e4b968-switcheroo-control.service-Owb1fY
systemd-private-7683b1e18fdf4a54a239cfe856e4b968-systemd-logind.service-NK8EtM
systemd-private-7683b1e18fdf4a54a239cfe856e4b968-systemd-oomd.service-x5VWqe
systemd-private-7683b1e18fdf4a54a239cfe856e4b968-systemd-resolved.service-kXKHcZ
systemd-private-7683b1e18fdf4a54a239cfe856e4b968-systemd-timesyncd.service-EL62qr
systemd-private-7683b1e18fdf4a54a239cfe856e4b968-upower.service-qLz1N2
praditadf@praditadf-VirtualBox:~$ echo "Sukses: $?"
Sukses: 0
[1]+  Done                    sleep 60

praditadf@praditadf-VirtualBox:~$ ls /direktori-tidak-ada
ls: cannot access '/direktori-tidak-ada': No such file or directory
praditadf@praditadf-VirtualBox:~$ echo "Gagal: $?"
Gagal: 2

```

## Latihan 6.2

#### 1. Jalankan sleep 120 & dan amati kolom STAT pada ps aux. Kondisi apa yang ditampilkan? Mengapa proses sleep berada di kondisi tersebut?

```
praditadf@praditadf-VirtualBox:~$ sleep 120 &
[1] 5611

praditadf@praditadf-VirtualBox:~$ ps aux | grep sleep
pradita+    5611  0.0  0.0  16964  2152 pts/0    S    15:46   0:00 sleep 120
pradita+    5613  0.0  0.0  17820  2376 pts/0    S+   15:46   0:00 grep --color=auto sleep
```

> Pada kolom STAT menampilkan kondisi S, proses ini menunggu event dan dapat diinterupsi sinyal

#### 2. Jalankan beberapa perintah yang berhasil dan yang gagal, lalu catat exit code masing-masing. Pola apa yang Anda temukan?

```
praditadf@praditadf-VirtualBox:~$ ls A && echo "Exit code: $?"
D  E
Exit code: 0

praditadf@praditadf-VirtualBox:~$ ls a ; echo "Exit code: $?"
ls: cannot access 'a': No such file or directory
Exit code: 2

praditadf@praditadf-VirtualBox:~$ ls z ; echo "Exit code: $?"
z
Exit code: 0

praditadf@praditadf-VirtualBox:~$ ls Z ; echo "Exit code: $?"
ls: cannot access 'Z': No such file or directory
Exit code: 2

praditadf@praditadf-VirtualBox:~$ ls B ; echo "Exit code: $?"
F
Exit code: 0

praditadf@praditadf-VirtualBox:~$ ls b ; echo "Exit code: $?"
ls: cannot access 'b': No such file or directory
Exit code: 2
```

> Pada setiap Exit code yang berhasil maka nilainya akan 0 sedangkan yang gagal Exit code bernilai selain 0

## Praktikum 6.3 — Mengatur Prioritas Proses

### 1. Jalankan proses dengan prioritas rendah

```
praditadf@praditadf-VirtualBox:~$ nice -n 10 sleep 300 &
[1] 4856
```

### 2. Verifikasi nilai nice pada kolom NI

```
praditadf@praditadf-VirtualBox:~$ ps aux | grep sleep
pradita+    4856  0.0  0.0  16964  2156 pts/0    SN   16:36   0:00 sleep 300
pradita+    4859  0.0  0.0  17820  2372 pts/0    S+   16:36   0:00 grep --color=auto sleep
```

### 3. Ubah nilai nice proses yang sudah berjalan

```
praditadf@praditadf-VirtualBox:~$ renice -n 15 -p 4856
4856 (process ID) old priority 10, new priority 15
praditadf@praditadf-VirtualBox:~$ ps -p 4856 -o pid,ni,cmd
    PID  NI CMD
   4856  15 sleep 300
```

### 4. Bersihkan proses percobaan

```
praditadf@praditadf-VirtualBox:~$ kill %1
praditadf@praditadf-VirtualBox:~$ 
```

## Latihan 6.3

#### 1. Jalankan nice -n 5 sleep 200 & dan verifikasi nilai NI-nya dengan ps

```
praditadf@praditadf-VirtualBox:~$ nice -n 5 sleep 200 &
[1] 4962
praditadf@praditadf-VirtualBox:~$ ps -p 4962 -o pid,ni,cmd
    PID  NI CMD
   4962   5 sleep 200
```

#### 2. Ubah nilai nice menjadi 10 menggunakan renice, lalu verifikasi kembali

```
praditadf@praditadf-VirtualBox:~$ renice -n 10 -p 4962
4962 (process ID) old priority 5, new priority 10
praditadf@praditadf-VirtualBox:~$ ps -p 4962 -o pid,ni,cmd
    PID  NI CMD
   4962  10 sleep 200
```

#### 3. Coba ubah nilai nice menjadi -5 tanpa sudo. Apa yang terjadi? Mengapa Linux membatasi hal ini untuk user biasa?

```
praditadf@praditadf-VirtualBox:~$ renice -n -5 -p 4962
renice: failed to set priority for 4962 (process ID): Permission denied
```

> Linux membatasi user biasa untuk memberikan nilai nice negatif, karena nilai default adalah 0 dan hanya root yang dapat menurunkannya ke nilai negatif, sedangkan user biasa hanya bisa menaikkan nilai nice.

## Praktikum 6.4 — Mengirim Sinyal ke Proses

### 1. Buat proses percobaan

```
praditadf@praditadf-VirtualBox:~$ sleep 500 &
[1] 5157
praditadf@praditadf-VirtualBox:~$ sleep 600 &
[2] 5158
praditadf@praditadf-VirtualBox:~$ sleep 700 &
[3] 5159
praditadf@praditadf-VirtualBox:~$ ps aux | grep -v grep | grep sleep
pradita+    5157  0.0  0.0  16964  2156 pts/0    S    16:49   0:00 sleep 500
pradita+    5158  0.0  0.0  16964  2156 pts/0    S    16:49   0:00 sleep 600
pradita+    5159  0.0  0.0  16964  2148 pts/0    S    16:49   0:00 sleep 700
```

### 2. Hentikan satu proses dengan SIGTERM dan verifikasi

```
praditadf@praditadf-VirtualBox:~$ kill 5157
praditadf@praditadf-VirtualBox:~$ ps aux | grep -v grep | grep sleep
pradita+    5158  0.0  0.0  16964  2156 pts/0    S    16:49   0:00 sleep 600
pradita+    5159  0.0  0.0  16964  2148 pts/0    S    16:49   0:00 sleep 700
[1]   Terminated              sleep 500
```

### 3. Jeda dan lanjutkan proses dengan SIGSTOP/SIGCONT

```
praditadf@praditadf-VirtualBox:~$ ps aux | grep sleep
pradita+    5158  0.0  0.0  16964  2156 pts/0    T    16:49   0:00 sleep 600
pradita+    5159  0.0  0.0  16964  2148 pts/0    S    16:49   0:00 sleep 700
pradita+    5216  0.0  0.0  17820  2372 pts/0    S+   16:54   0:00 grep --color=auto sleep

[2]+  Stopped                 sleep 600

praditadf@praditadf-VirtualBox:~$ kill -SIGCONT 5158
praditadf@praditadf-VirtualBox:~$ ps aux | grep sleep
pradita+    5158  0.0  0.0  16964  2156 pts/0    S    16:49   0:00 sleep 600
pradita+    5159  0.0  0.0  16964  2148 pts/0    S    16:49   0:00 sleep 700
pradita+    5232  0.0  0.0  17820  2372 pts/0    S+   16:55   0:00 grep --color=auto sleep

```

### 4. Hentikan semua proses sleep sekaligus

```
praditadf@praditadf-VirtualBox:~$ pkill sleep
[2]-  Terminated              sleep 600
[3]+  Terminated              sleep 700
```

## Latihan 6.4

#### 1. Jalankan sleep 400 &, kirim SIGSTOP, dan amati perubahan kolom STAT. Kondisi apa yang muncul?

```
praditadf@praditadf-VirtualBox:~$ sleep 400 &
[1] 5250
praditadf@praditadf-VirtualBox:~$ kill -SIGSTOP 5250
praditadf@praditadf-VirtualBox:~$ ps aux | grep sleep
pradita+    5250  0.0  0.0  16964  2156 pts/0    T    16:56   0:00 sleep 400
pradita+    5254  0.0  0.0  17820  2376 pts/0    S+   16:56   0:00 grep --color=auto sleep

[1]+  Stopped                 sleep 400
```

> Kolom STAT menjadi T (Jeda proses)

#### 2. Kirim SIGCONT dan verifikasi proses kembali berjalan

```
praditadf@praditadf-VirtualBox:~$ kill -SIGCONT 5250
praditadf@praditadf-VirtualBox:~$ ps aux | grep sleep
pradita+    5250  0.0  0.0  16964  2156 pts/0    S    16:56   0:00 sleep 400
pradita+    5288  0.0  0.0  17820  2376 pts/0    S+   16:58   0:00 grep --color=auto sleep
```

#### 3. Hentikan proses dengan SIGTERM lalu verifikasi sudah tidak ada. Kapan Anda memilih SIGKILL daripada SIGTERM?

```
praditadf@praditadf-VirtualBox:~$ kill -SIGTERM 5250
praditadf@praditadf-VirtualBox:~$ ps aux | grep sleep
pradita+    5303  0.0  0.0  17820  2376 pts/0    S+   16:59   0:00 grep --color=auto sleep
[1]+  Terminated              sleep 400
praditadf@praditadf-VirtualBox:~$ ps aux | grep sleep
pradita+    5314  0.0  0.0  17820  2376 pts/0    S+   17:00   0:00 grep --color=auto sleep
```

> Penggunaan SIGKILL digunakan ketika kita sudah mencoba menggunakan SIGTERM agar komputer mendapatkan kesempatan untuk menyimpan data dan membersihkan sumber daya sebelum berhenti. Sedangkan SIGKILL mematikan proses secara paksa tanpa cleanup yang berisiko menyebabkan data korup atau file lock yang tidak terlepas.

## Praktikum 6.5 — Manajemen Job Foreground dan Background

### 1. Jalankan tiga job di background

```
praditadf@praditadf-VirtualBox:~$ sleep 200 &
[1] 5719
praditadf@praditadf-VirtualBox:~$ sleep 300 &
[2] 5720
praditadf@praditadf-VirtualBox:~$ sleep 400 &
[3] 5722
praditadf@praditadf-VirtualBox:~$ jobs
[1]   Running                 sleep 200 &
[2]-  Running                 sleep 300 &
[3]+  Running                 sleep 400 &
```

### 2. Bawa job pertama ke foreground, jeda, lalu kembalikan ke background

```
praditadf@praditadf-VirtualBox:~$ fg %1
sleep 200
^Z
[1]+  Stopped                 sleep 200
praditadf@praditadf-VirtualBox:~$ bg %1
[1]+ sleep 200 &
praditadf@praditadf-VirtualBox:~$ jobs
[1]   Running                 sleep 200 &
[2]-  Running                 sleep 300 &
[3]+  Running                 sleep 400 &
```

### 3. Hentikan semua job

```
praditadf@praditadf-VirtualBox:~$ kill %1 %2 %3
praditadf@praditadf-VirtualBox:~$ jobs
[1]   Terminated              sleep 200
[2]-  Terminated              sleep 300
[3]+  Terminated              sleep 400
```

## Latihan 6.5

#### 1. Jalankan top di foreground. Apa yang terjadi di terminal?

> Ketika top dijalankan di foreground maka kita tidak bisa menulis perintah lain sebelum keluar atau jeda terlebih dahulu.

```

top - 18:57:01 up  1:03,  1 user,  load average: 0.63, 0.61, 0.67
Tasks: 221 total,   1 running, 220 sleeping,   0 stopped,   0 zombie
%Cpu(s):  9.1 us,  9.9 sy,  0.0 ni, 80.2 id,  0.2 wa,  0.0 hi,  0.6 si,  0.0 st 
MiB Mem :   3914.8 total,    130.0 free,   2421.6 used,   1791.4 buff/cache     
MiB Swap:   2048.0 total,   1741.6 free,    306.4 used.   1493.2 avail Mem 

```

<details>
<summary><b>Read More</b></summary>
<br>

```
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                           
   2000 pradita+  20   0 4171772 366516 141664 S  19.9   9.1   9:17.67 gnome-shell                                                                       
   3575 pradita+  20   0 1393.6g 442704  87392 S  19.3  11.0   1:56.76 code                                                                              
   3233 pradita+  20   0 1395.3g 374532 135192 S  12.0   9.3   3:39.18 code                                                                              
   3286 pradita+  20   0   48.4g 114116 111008 S   6.6   2.8   1:02.51 code                                                                              
   3076 pradita+  20   0 1393.8g 153024 110936 S   1.7   3.8   0:47.91 code                                                                              
   2862 pradita+  20   0  287552  57232  38716 S   1.3   1.4   0:17.70 Xwayland                                                                          
   5609 root      20   0       0      0      0 I   1.3   0.0   0:00.28 kworker/u10:2-ext4-rsv-conversion                                                 
   2868 pradita+  20   0  641252  52492  42268 S   0.7   1.3   0:15.66 gnome-terminal-                                                                   
   4285 pradita+  20   0 1391.9g 131352  68400 S   0.7   3.3   0:12.64 code                                                                              
    571 root      20   0       0      0      0 I   0.3   0.0   0:04.39 kworker/u9:5-kvfree_rcu_reclaim                                                   
   2105 pradita+  20   0  397316   8008   7020 S   0.3   0.2   0:06.35 ibus-daemon                                                                       
   2571 pradita+  20   0  917828  27948  20204 S   0.3   0.7   0:00.87 xdg-desktop-por                                                                   
   3002 pradita+  20   0 3322972 437016 164756 S   0.3  10.9   2:01.06 firefox                                                                           
      1 root      20   0   23460  13860   9816 S   0.0   0.3   0:05.91 systemd                                                                           
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.08 kthreadd                                                                          
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                            
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp                                                                  
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq                                                                 
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-kvfree_rcu_reclaim                                                      
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_flushwq                                                            
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns                                                                   
     12 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/u8:0-ipv6_addrconf                                                        
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_percpu_wq                                                            
     14 root      20   0       0      0      0 S   0.0   0.0   0:01.31 ksoftirqd/0                                                                       
     15 root      20   0       0      0      0 I   0.0   0.0   0:03.82 rcu_preempt                                                                       
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_exp_par_gp_kthread_worker/0                                                   
     17 root      20   0       0      0      0 S   0.0   0.0   0:00.07 rcu_exp_gp_kthread_worker                                                         
     18 root      rt   0       0      0      0 S   0.0   0.0   0:00.06 migration/0                                                                       
     19 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                     
```

</details>

#### 2. Tekan Ctrl+Z dan cek statusnya dengan jobs. Kondisi apa yang ditampilkan?

```
[1]+  Stopped                 top
praditadf@praditadf-VirtualBox:~$ jobs
[1]+  Stopped                 top

Terminal akan menampilkan kondisi jobs yang terjeda
```

#### 3. Pindahkan ke background dengan bg. Apakah top dapat berjalan dengan baik di background? Mengapa?

```
[1]+  Stopped                 top
praditadf@praditadf-VirtualBox:~$ jobs
[1]+  Stopped                 top
praditadf@praditadf-VirtualBox:~$ bg %1
[1]+ top &
praditadf@praditadf-VirtualBox:~$ 

```

> Top tidak dapat berjalan baik di background, karena top menampilkan proses secara real time sehingga harus berjalan di foreground

#### 4. Kembalikan ke foreground dengan fg, lalu keluar dengan q

```top - 19:05:37 up  1:12,  1 user,  load average: 0.75, 1.18, 0.97
Tasks: 221 total,   1 running, 220 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.8 sy,  0.0 ni, 98.3 id,  0.0 wa,  0.0 hi,  0.8 si,  0.0 st 
MiB Mem :   3914.8 total,    172.5 free,   2424.7 used,   1707.0 buff/cache     
MiB Swap:   2048.0 total,   1722.6 free,    325.4 used.   1490.0 avail Mem 

```

<details>
<summary><b>Read More</b></summary>
<br>

```
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                           
   2000 pradita+  20   0 4165708 356588 135400 S  27.3   8.9  10:47.05 gnome-shell                                                                       
     14 root      20   0       0      0      0 S   9.1   0.0   0:01.36 ksoftirqd/0                                                                       
   6044 pradita+  20   0   23200   5768   3544 R   9.1   0.1   0:00.01 top                                                                               
      1 root      20   0   23460  13860   9816 S   0.0   0.3   0:05.92 systemd                                                                           
top - 19:08:02 up  1:14,  1 user,  load average: 1.30, 1.22, 1.01
Tasks: 221 total,   4 running, 217 sleeping,   0 stopped,   0 zombie
%Cpu(s):  6.7 us,  9.7 sy,  0.0 ni, 83.0 id,  0.0 wa,  0.0 hi,  0.5 si,  0.0 st 
MiB Mem :   3914.8 total,    202.5 free,   2411.4 used,   1704.4 buff/cache     
MiB Swap:   2048.0 total,   1719.2 free,    328.8 used.   1503.4 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                           
   2000 pradita+  20   0 4173868 355892 135400 S  17.2   8.9  11:12.01 gnome-shell                                                                       
   3233 pradita+  20   0 1395.3g 398628 116580 S  17.1   9.9   6:00.65 code                                                                              
   3575 pradita+  20   0 1393.6g 440936  87392 S   4.9  11.0   2:36.80 code                                                                              
   3286 pradita+  20   0   48.4g 100048  96352 S   4.3   2.5   1:32.98 code                                                                              
   3076 pradita+  20   0 1393.8g 155064 111164 S   2.8   3.9   1:01.82 code                                                                              
   2862 pradita+  20   0  280020  49712  31184 S   1.5   1.2   0:27.20 Xwayland                                                                          
   4285 pradita+  20   0 1391.9g 128520  68400 S   0.4   3.2   0:17.70 code                                                                              
   2868 pradita+  20   0  641252  51620  42268 S   0.4   1.3   0:17.90 gnome-terminal-                                                                   
   4799 root      20   0       0      0      0 R   0.4   0.0   0:07.32 kworker/u9:1-kvfree_rcu_reclaim                                                   
   3002 pradita+  20   0 3321996 414872 164772 S   0.4  10.3   2:03.74 firefox                                                                           
     68 root      20   0       0      0      0 I   0.4   0.0   0:14.95 kworker/u10:4-events_unbound                                                      
    571 root      20   0       0      0      0 R   0.3   0.0   0:05.99 kworker/u9:5+events_unbound                                                       
   4701 root      20   0       0      0      0 I   0.3   0.0   0:04.78 kworker/u10:0-events_unbound                                                      
   2899 pradita+  20   0 1128336  41976  15872 S   0.2   1.0   0:02.49 mutter-x11-fram                                                                   
     15 root      20   0       0      0      0 I   0.1   0.0   0:04.38 rcu_preempt                                                                       
   2105 pradita+  20   0  397316   8028   7020 S   0.1   0.2   0:06.82 ibus-daemon                                                                       
   3354 pradita+  20   0 2608080 119620  79536 S   0.1   3.0   0:07.61 Privileged Cont                                                                   
     58 root      20   0       0      0      0 S   0.1   0.0   0:13.71 kswapd0                                                                           
   1137 root      20   0       0      0      0 I   0.1   0.0   0:05.01 kworker/0:4-events                                                                
   3571 pradita+  20   0 1393.6g  87168  76188 S   0.1   2.2   0:04.10 code                                                                              
   3627 pradita+  20   0 7001912 252876 186496 S   0.1   6.3   0:34.66 Isolated Web Co                                                                   
   1762 pradita+  20   0  124140  13468   8732 S   0.1   0.3   0:02.74 pipewire                                                                          
   3150 pradita+  20   0   48.3g  61716  58880 S   0.1   1.5   0:02.95 code                                                                              
   3469 pradita+  20   0 1393.6g 102920  80132 S   0.1   2.6   0:06.95 code                                                                              
   4044 pradita+  20   0 2568144  66356  51396 S   0.1   1.7   0:04.23 Web Content                                                                       
   4050 pradita+  20   0 2568144  66140  51268 S   0.1   1.6   0:04.04 Web Content                                                                       
   2438 pradita+  20   0  245444   7216   6732 S   0.0   0.2   0:02.23 ibus-engine-sim                                                                   
    409 systemd+  20   0   17572   7744   6848 S   0.0   0.2   0:01.64 systemd-oomd                                                                      
   2285 pradita+  20   0  432040  23472  13492 S   0.0   0.6   0:03.59 ibus-extension-                                                                   
praditadf@praditadf-VirtualBox:~$ 
praditadf@praditadf-VirtualBox:~$ 

```

</details>

## Praktikum 6.6 — Pemantauan Proses

### 1. Temukan proses dengan penggunaan CPU dan memori tertinggi

```
praditadf@praditadf-VirtualBox:~$ ps aux --sort=-%cpu | head -10
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
pradita+    2000 15.6  8.8 4173868 355904 ?      Ssl  17:54  12:41 /usr/bin/gnome-shell
pradita+    3233  9.5 10.3 1463038196 413116 ?   Sl   17:54   7:41 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    3575  3.6 11.2 1461319884 449892 ?   Sl   17:54   2:54 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService --lang=en-US --service-sandbox-type=none --no-sandbox --dns-result-order=ipv4first --experimental-network-inspection --inspect-port=0 --crashpad-handler-pid=3114 --enable-crash-reporter=e9bfb98a-f4aa-4b21-89a7-bd4f93b569d0,no_channel --user-data-dir=/home/praditadf/.config/Code --standard-schemes=vscode-webview,vscode-file --secure-schemes=vscode-webview,vscode-file --cors-schemes=vscode-webview,vscode-file --fetch-schemes=vscode-webview,vscode-file --service-worker-schemes=vscode-webview --code-cache-schemes=vscode-webview,vscode-file --shared-files=v8_context_snapshot_data:100 --field-trial-handle=3,i,3184216701153887361,13250874988657799531,262144 --enable-features=DocumentPolicyIncludeJSCallStacksInCrashReports,EarlyEstablishGpuChannel,EstablishGpuChannelAsync --disable-features=CalculateNativeWinOcclusion,LocalNetworkAccessChecks,ScreenAIOCREnabled,SpareRendererForSitePerProcess,TraceSiteInstanceGetProcessCreation --variations-seed-version --trace-process-track-uuid=3190708997556373682
pradita+    3002  2.7 10.3 3321980 413436 ?      Sl   17:54   2:15 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    3286  2.3  2.2 50717524 91024 ?      Sl   17:54   1:54 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --ozone-platform=x11 --crashpad-handler-pid=3114 --enable-crash-reporter=e9bfb98a-f4aa-4b21-89a7-bd4f93b569d0,no_channel --user-data-dir=/home/praditadf/.config/Code --gpu-preferences=UAAAAAAAAAAgAAAEAAAAAAAAAAAAAGAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAYAAAAAAAAABgAAAAAAAAAAQAAAAAAAAAIAAAAAAAAAAgAAAAAAAAA --use-gl=angle --use-angle=swiftshader-webgl --shared-files --field-trial-handle=3,i,3184216701153887361,13250874988657799531,262144 --enable-features=DocumentPolicyIncludeJSCallStacksInCrashReports,EarlyEstablishGpuChannel,EstablishGpuChannelAsync --disable-features=CalculateNativeWinOcclusion,LocalNetworkAccessChecks,ScreenAIOCREnabled,SpareRendererForSitePerProcess,TraceSiteInstanceGetProcessCreation --variations-seed-version --trace-process-track-uuid=3190708994745248135
pradita+    3076  1.4  3.8 1461521032 155796 ?   SLsl 17:54   1:11 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-platform=x11
pradita+    3627  0.7  6.3 7001928 253732 ?      Sl   17:54   0:38 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:32809 -prefMapHandle 1:278884 -jsInitHandle 2:227672 -parentBuildID 20260309231353 -sandboxReporter 3 -chrootClient 4 -ipcHandle 5 -initialChannelId {481ca707-2ece-4961-806d-26327ccb2d1f} -parentPid 3002 -crashReporter 6 -crashHelper 7 -greomni /snap/firefox/7967/usr/lib/firefox/omni.ja -appomni /snap/firefox/7967/usr/lib/firefox/browser/omni.ja -appDir /snap/firefox/7967/usr/lib/firefox/browser 6 tab
pradita+    2862  0.7  1.2 280020 49760 ?        S    17:54   0:34 /usr/bin/Xwayland :0 -rootless -noreset -accessx -core -auth /run/user/1000/.mutter-Xwaylandauth.4F9GN3 -listenfd 4 -listenfd 5 -displayfd 6 -initfd 7 -byteswappedclients
pradita+    4285  0.4  3.1 1459515644 127884 ?   Sl   17:55   0:19 /snap/code/228/usr/share/code/code /snap/code/228/usr/share/code/resources/app/extensions/markdown-language-features/dist/serverWorkerMain --node-ipc --clientProcessId=3575
```

<details>
<summary><b>Read More</b></summary>
<br>

```
praditadf@praditadf-VirtualBox:~$ ps aux --sort=-%mem | head -10
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
pradita+    3575  3.6 11.2 1461319884 449784 ?   Sl   17:54   2:54 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService --lang=en-US --service-sandbox-type=none --no-sandbox --dns-result-order=ipv4first --experimental-network-inspection --inspect-port=0 --crashpad-handler-pid=3114 --enable-crash-reporter=e9bfb98a-f4aa-4b21-89a7-bd4f93b569d0,no_channel --user-data-dir=/home/praditadf/.config/Code --standard-schemes=vscode-webview,vscode-file --secure-schemes=vscode-webview,vscode-file --cors-schemes=vscode-webview,vscode-file --fetch-schemes=vscode-webview,vscode-file --service-worker-schemes=vscode-webview --code-cache-schemes=vscode-webview,vscode-file --shared-files=v8_context_snapshot_data:100 --field-trial-handle=3,i,3184216701153887361,13250874988657799531,262144 --enable-features=DocumentPolicyIncludeJSCallStacksInCrashReports,EarlyEstablishGpuChannel,EstablishGpuChannelAsync --disable-features=CalculateNativeWinOcclusion,LocalNetworkAccessChecks,ScreenAIOCREnabled,SpareRendererForSitePerProcess,TraceSiteInstanceGetProcessCreation --variations-seed-version --trace-process-track-uuid=3190708997556373682
pradita+    3233  9.5 10.3 1463038196 413700 ?   Sl   17:54   7:41 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    3002  2.7 10.3 3321964 413440 ?      Sl   17:54   2:15 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    2000 15.6  8.8 4173868 355908 ?      Ssl  17:54  12:42 /usr/bin/gnome-shell
pradita+    3627  0.7  6.3 7001928 253732 ?      Sl   17:54   0:38 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:32809 -prefMapHandle 1:278884 -jsInitHandle 2:227672 -parentBuildID 20260309231353 -sandboxReporter 3 -chrootClient 4 -ipcHandle 5 -initialChannelId {481ca707-2ece-4961-806d-26327ccb2d1f} -parentPid 3002 -crashReporter 6 -crashHelper 7 -greomni /snap/firefox/7967/usr/lib/firefox/omni.ja -appomni /snap/firefox/7967/usr/lib/firefox/browser/omni.ja -appDir /snap/firefox/7967/usr/lib/firefox/browser 6 tab
pradita+    3076  1.4  3.8 1461521032 155796 ?   SLsl 17:54   1:11 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-platform=x11
pradita+    4285  0.4  3.1 1459515644 127884 ?   Sl   17:55   0:20 /snap/code/228/usr/share/code/code /snap/code/228/usr/share/code/resources/app/extensions/markdown-language-features/dist/serverWorkerMain --node-ipc --clientProcessId=3575
pradita+    3354  0.1  3.0 2608096 120280 ?      Sl   17:54   0:07 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:37717 -prefMapHandle 1:278884 -jsInitHandle 2:227672 -parentBuildID 20260309231353 -sandboxReporter 3 -chrootClient 4 -ipcHandle 5 -initialChannelId {7802a8d4-756b-43c1-b556-68e6b1119eab} -parentPid 3002 -crashReporter 6 -crashHelper 7 -greomni /snap/firefox/7967/usr/lib/firefox/omni.ja -appomni /snap/firefox/7967/usr/lib/firefox/browser/omni.ja -appDir /snap/firefox/7967/usr/lib/firefox/browser 3 tab
pradita+    3469  0.1  2.5 1461316216 104144 ?   Sl   17:54   0:07 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService --lang=en-US --service-sandbox-type=none --no-sandbox --crashpad-handler-pid=3114 --enable-crash-reporter=e9bfb98a-f4aa-4b21-89a7-bd4f93b569d0,no_channel --user-data-dir=/home/praditadf/.config/Code --standard-schemes=vscode-webview,vscode-file --secure-schemes=vscode-webview,vscode-file --cors-schemes=vscode-webview,vscode-file --fetch-schemes=vscode-webview,vscode-file --service-worker-schemes=vscode-webview --code-cache-schemes=vscode-webview,vscode-file --shared-files=v8_context_snapshot_data:100 --field-trial-handle=3,i,3184216701153887361,13250874988657799531,262144 --enable-features=DocumentPolicyIncludeJSCallStacksInCrashReports,EarlyEstablishGpuChannel,EstablishGpuChannelAsync --disable-features=CalculateNativeWinOcclusion,LocalNetworkAccessChecks,ScreenAIOCREnabled,SpareRendererForSitePerProcess,TraceSiteInstanceGetProcessCreation --variations-seed-version --trace-process-track-uuid=3190708995682289984
```

</details>

### 2. Jalankan top dan eksplorasi shortcut-nya

* M

```
top - 19:22:37 up  1:29,  1 user,  load average: 0.60, 1.45, 1.39
Tasks: 221 total,   1 running, 220 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.4 us,  2.3 sy,  0.0 ni, 96.2 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st 
MiB Mem :   3914.8 total,    235.8 free,   2399.4 used,   1677.2 buff/cache     
MiB Swap:   2048.0 total,   1711.1 free,    336.9 used.   1515.4 avail Mem                                                                                 ] 
```

<details>
<summary><b>Read More</b></summary>
<br>

```
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                           
   3575 pradita+  20   0 1393.6g 450476  87400 S   0.0  11.2   3:14.14 code                                                                              
   3002 pradita+  20   0 3323980 419288 159668 S   0.0  10.5   2:20.73 firefox                                                                           
   3233 pradita+  20   0 1395.3g 353356 109680 S   0.0   8.8   9:20.78 code                                                                              
   2000 pradita+  20   0 4173884 352216 135496 S   9.3   8.8  14:01.97 gnome-shell                                                                       
   3627 pradita+  20   0 7001912 251304 186496 S   0.3   6.3   0:39.73 Isolated Web Co                                                                   
   3076 pradita+  20   0 1393.8g 156036 111232 S   0.0   3.9   1:18.65 code                                                                              
   4285 pradita+  20   0 1391.9g 138852  68400 S   0.0   3.5   0:22.18 code                                                                              
   3354 pradita+  20   0 2610128 120384  79536 S   0.0   3.0   0:08.44 Privileged Cont                                                                   
   3469 pradita+  20   0 1393.6g 103708  80132 S   0.0   2.6   0:07.41 code                                                                              
   3609 pradita+  20   0 2615436  93504  67092 S   0.0   2.3   0:01.49 WebExtensions                                                                     
   3286 pradita+  20   0   48.4g  92524  89592 S   0.0   2.3   2:11.29 code                                                                              
   3571 pradita+  20   0 1393.6g  87964  76188 S   0.0   2.2   0:04.56 code                                                                              
   4306 pradita+  20   0 1391.9g  84004  63028 S   0.0   2.1   0:00.85 code                                                                              
   4044 pradita+  20   0 2568144  66356  51396 S   0.0   1.7   0:04.79 Web Content                                                                       
   4050 pradita+  20   0 2568144  66144  51268 S   0.0   1.6   0:04.59 Web Content                                                                       
   3853 pradita+  20   0 2567312  65692  50948 S   0.0   1.6   0:00.21 Web Content                                                                       
   3150 pradita+  20   0   48.3g  61728  58880 S   0.0   1.5   0:03.37 code                                                                              
   2868 pradita+  20   0  641252  51476  42428 S   0.7   1.3   0:21.92 gnome-terminal-                                                                   
   2862 pradita+  20   0  280020  49760  31184 S   0.0   1.2   0:39.07 Xwayland                                                                          
   2149 pradita+  20   0  836804  46936  36280 S   0.0   1.2   0:00.58 evolution-alarm                                                                   
   2607 pradita+  20   0 2820888  45504  36372 S   0.0   1.1   0:01.51 gjs                                                                               
   3079 pradita+  20   0   32.2g  45348  41940 S   0.0   1.1   0:00.11 code                                                                              
   4455 root      20   0  489872  42720  36932 S   0.0   1.1   0:00.62 fwupd                                                                             
   2899 pradita+  20   0 1128336  41976  15872 S   0.0   1.0   0:03.57 mutter-x11-fram                                                                   
   3078 pradita+  20   0   32.2g  41680  41676 S   0.0   1.0   0:00.09 code                                                                              
   3364 pradita+  20   0  589448  38280  26160 S   0.0   1.0   0:00.25 RDD Process                                                                       
   2100 pradita+  20   0 1218428  37632  29300 S   0.0   0.9   0:00.37 evolution-sourc                                                                   
   3327 pradita+  20   0  456440  36448  26332 S   0.0   0.9   0:00.10 Socket Process                                                                    
   3850 pradita+  20   0  456436  35660  25528 S   0.0   0.9   0:00.10 Utility Process                                         

```

</details>

* P

```
top - 19:23:37 up  1:30,  1 user,  load average: 0.66, 1.31, 1.34
Tasks: 221 total,   1 running, 220 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.6 us,  5.6 sy,  0.0 ni, 92.6 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st 
MiB Mem :   3914.8 total,    193.4 free,   2441.7 used,   1678.4 buff/cache     
MiB Swap:   2048.0 total,   1711.1 free,    336.9 used.   1473.1 avail Mem 
```

<details>
<summary><b>Read More</b></summary>
<br>

```
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                           
   2000 pradita+  20   0 4173900 352328 135496 S  16.6   8.8  14:14.78 gnome-shell                                                                       
   6176 root      20   0       0      0      0 I   1.7   0.0   0:01.85 kworker/u9:2-events_unbound                                                       
   2868 pradita+  20   0  641252  51516  42428 S   1.3   1.3   0:22.26 gnome-terminal-                                                                   
     40 root      20   0       0      0      0 S   0.7   0.0   0:00.47 kcompactd0                                                                        
   5843 root      20   0       0      0      0 I   0.7   0.0   0:01.79 kworker/u10:1-events_unbound                                                      
   2438 pradita+  20   0  245444   7216   6732 S   0.3   0.2   0:02.50 ibus-engine-sim                                                                   
   3627 pradita+  20   0 7001912 251328 186496 S   0.3   6.3   0:39.79 Isolated Web Co                                                                   
   5312 root      20   0       0      0      0 I   0.3   0.0   0:00.44 kworker/1:0-events                                                                
   6427 pradita+  20   0   23200   6028   3796 R   0.3   0.2   0:00.13 top                                                                               
      1 root      20   0   23460  13860   9816 S   0.0   0.3   0:05.97 systemd                                                                           
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.08 kthreadd                                                                          
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                            
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp                                                                  
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq                                                                 
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-kvfree_rcu_reclaim                                                      
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_flushwq                                                            
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns                                                                   
     12 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/u8:0-ipv6_addrconf                                                        
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_percpu_wq                                                            
     14 root      20   0       0      0      0 S   0.0   0.0   0:01.44 ksoftirqd/0                                                                       
     15 root      20   0       0      0      0 I   0.0   0.0   0:05.08 rcu_preempt                                                                       
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_exp_par_gp_kthread_worker/0                                                   
     17 root      20   0       0      0      0 S   0.0   0.0   0:00.07 rcu_exp_gp_kthread_worker                                                         
     18 root      rt   0       0      0      0 S   0.0   0.0   0:00.08 migration/0                                                                       
     19 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                     
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                           
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                           
     22 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1                                                                     
     23 root      rt   0       0      0      0 S   0.0   0.0   0:01.99 migration/1                                                         
```

</details>

* 1

```
top - 19:24:24 up  1:31,  1 user,  load average: 1.38, 1.40, 1.37
Tasks: 221 total,   1 running, 220 sleeping,   0 stopped,   0 zombie
%Cpu0  :  5.5 us,  9.1 sy,  0.0 ni, 84.7 id,  0.0 wa,  0.0 hi,  0.7 si,  0.0 st 
%Cpu1  :  1.1 us,  8.5 sy,  0.0 ni, 90.4 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :   3914.8 total,    201.1 free,   2433.9 used,   1676.7 buff/cache     
MiB Swap:   2048.0 total,   1711.1 free,    336.9 used.   1480.9 avail Mem 
```

<details>
<summary><b>Read More</b></summary>
<br>

```
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                           
   2000 pradita+  20   0 4182044 352372 135516 S  24.9   8.8  14:25.76 gnome-shell                                                                       
   5843 root      20   0       0      0      0 I   2.7   0.0   0:02.30 kworker/u10:1-events_unbound                                                      
   2868 pradita+  20   0  641252  51516  42428 S   2.3   1.3   0:22.77 gnome-terminal-                                                                   
   4799 root      20   0       0      0      0 I   2.3   0.0   0:09.96 kworker/u9:1-events_unbound                                                       
   4050 pradita+  20   0 2568144  66144  51268 S   0.7   1.6   0:04.68 Web Content                                                                       
    415 systemd+  20   0   91060   7720   7040 S   0.3   0.2   0:00.18 systemd-timesyn                                                                   
   2899 pradita+  20   0 1128336  41976  15872 S   0.3   1.0   0:03.83 mutter-x11-fram                                                                   
   3002 pradita+  20   0 3324012 419296 159668 S   0.3  10.5   2:21.22 firefox                                                                           
   3076 pradita+  20   0 1393.8g 156144 111232 S   0.3   3.9   1:21.59 code                                                                              
   3627 pradita+  20   0 7001928 251344 186496 S   0.3   6.3   0:39.86 Isolated Web Co                                                                   
   4044 pradita+  20   0 2568144  66356  51396 S   0.3   1.7   0:04.86 Web Content                                                                       
      1 root      20   0   23460  13860   9816 S   0.0   0.3   0:05.97 systemd                                                                           
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.08 kthreadd                                                                          
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                            
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp                                                                  
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq                                                                 
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-kvfree_rcu_reclaim                                                      
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_flushwq                                                            
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns                                                                   
     12 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/u8:0-ipv6_addrconf                                                        
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_percpu_wq                                                            
     14 root      20   0       0      0      0 S   0.0   0.0   0:01.45 ksoftirqd/0                                                                       
     15 root      20   0       0      0      0 I   0.0   0.0   0:05.11 rcu_preempt                                                                       
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_exp_par_gp_kthread_worker/0                                                   
     17 root      20   0       0      0      0 S   0.0   0.0   0:00.07 rcu_exp_gp_kthread_worker                                                         
     18 root      rt   0       0      0      0 S   0.0   0.0   0:00.09 migration/0                                                                       
     19 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                     
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                        
```

</details>

* u

```
top - 19:24:52 up  1:31,  1 user,  load average: 1.68, 1.46, 1.39
Tasks: 222 total,   1 running, 221 sleeping,   0 stopped,   0 zombie
%Cpu0  : 28.1 us, 18.2 sy,  0.0 ni, 52.2 id,  0.0 wa,  0.0 hi,  1.5 si,  0.0 st 
%Cpu1  :  9.0 us, 36.0 sy,  0.0 ni, 54.5 id,  0.0 wa,  0.0 hi,  0.6 si,  0.0 st 
MiB Mem :   3914.8 total,    160.5 free,   2474.4 used,   1698.5 buff/cache     
MiB Swap:   2048.0 total,   1711.1 free,    336.9 used.   1440.4 avail Mem 
Which user (blank for all)
```

<details>
<summary><b>Read More</b></summary>
<br>

```
    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                           
   3233 pradita+  20   0 1395.3g 418236 123744 S  53.5  10.4   9:56.35 code                                                                              
   2000 pradita+  20   0 4189592 359944 143048 S  38.2   9.0  14:32.35 gnome-shell                                                                       
   3286 pradita+  20   0   48.4g 105752 102384 S  13.0   2.6   2:18.06 code                                                                              
   3575 pradita+  20   0 1393.6g 452028  87400 S   8.6  11.3   3:19.82 code                                                                              
   3076 pradita+  20   0 1393.8g 156116 111328 S   4.3   3.9   1:22.68 code                                                                              
   2862 pradita+  20   0  287552  57292  38716 S   3.3   1.4   0:41.57 Xwayland                                                                          
   4701 root      20   0       0      0      0 I   1.3   0.0   0:10.25 kworker/u10:0-events_unbound                                                      
   3002 pradita+  20   0 3323980 419296 159668 S   1.0  10.5   2:21.32 firefox                                                                           
   4285 pradita+  20   0 1391.9g 143004  68400 S   1.0   3.6   0:22.72 code                                                                              
   4799 root      20   0       0      0      0 I   1.0   0.0   0:10.22 kworker/u9:1-events_unbound                                                       
   2868 pradita+  20   0  641252  51516  42428 S   0.7   1.3   0:22.92 gnome-terminal-                                                                   
   2105 pradita+  20   0  397316   8048   7020 S   0.3   0.2   0:07.71 ibus-daemon                                                                       
   2285 pradita+  20   0  432040  23476  13492 S   0.3   0.6   0:03.73 ibus-extension-                                                                   
   2899 pradita+  20   0 1128336  41976  15872 S   0.3   1.0   0:03.92 mutter-x11-fram                                                                   
   3627 pradita+  20   0 7001912 251328 186496 S   0.3   6.3   0:39.90 Isolated Web Co                                                                   
   4050 pradita+  20   0 2568144  66144  51268 S   0.3   1.6   0:04.70 Web Content                                                                       
      1 root      20   0   23460  13860   9816 S   0.0   0.3   0:05.97 systemd                                                                           
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.08 kthreadd                                                                          
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                            
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp                                                                  
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq                                                                 
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-kvfree_rcu_reclaim                                                      
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_flushwq                                                            
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns                                                                   
     12 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/u8:0-ipv6_addrconf                                                        
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_percpu_wq                                                            
     14 root      20   0       0      0      0 S   0.0   0.0   0:01.45 ksoftirqd/0                                                                       
     15 root      20   0       0      0      0 I   0.0   0.0   0:05.13 rcu_preempt                                                                       

```

</details>

### 3. Instal dan jalankan htop

```
praditadf@praditadf-VirtualBox:~$ sudo apt install -y htop
[sudo] password for praditadf: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
htop is already the newest version (3.3.0-4build1).
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
praditadf@praditadf-VirtualBox:~$ htop
```

## Latihan 6.6

#### 1. Gunakan ps aux –sort=%mem untuk menemukan proses yang menggunakan memori paling banyak di VM Anda. Proses apa itu?

```
praditadf@praditadf-VirtualBox:~$ ps aux --sort=-%mem | head -10
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
pradita+    3575  3.5 11.1 1461319884 447592 ?   Sl   17:54   3:23 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService --lang=en-US --service-sandbox-type=none --no-sandbox --dns-result-order=ipv4first --experimental-network-inspection --inspect-port=0 --crashpad-handler-pid=3114 --enable-crash-reporter=e9bfb98a-f4aa-4b21-89a7-bd4f93b569d0,no_channel --user-data-dir=/home/praditadf/.config/Code --standard-schemes=vscode-webview,vscode-file --secure-schemes=vscode-webview,vscode-file --cors-schemes=vscode-webview,vscode-file --fetch-schemes=vscode-webview,vscode-file --service-worker-schemes=vscode-webview --code-cache-schemes=vscode-webview,vscode-file --shared-files=v8_context_snapshot_data:100 --field-trial-handle=3,i,3184216701153887361,13250874988657799531,262144 --enable-features=DocumentPolicyIncludeJSCallStacksInCrashReports,EarlyEstablishGpuChannel,EstablishGpuChannelAsync --disable-features=CalculateNativeWinOcclusion,LocalNetworkAccessChecks,ScreenAIOCREnabled,SpareRendererForSitePerProcess,TraceSiteInstanceGetProcessCreation --variations-seed-version --trace-process-track-uuid=3190708997556373682
pradita+    3002  2.5 10.4 3332444 420108 ?      Sl   17:54   2:27 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    3233 10.6  9.9 1463040244 400520 ?   Sl   17:54  10:13 /snap/code/228/usr/share/code/code --type=zygote --no-sandbox
pradita+    2000 15.8  8.8 4173900 353836 ?      Ssl  17:54  15:23 /usr/bin/gnome-shell
pradita+    3627  0.7  6.4 7010392 259852 ?      Sl   17:54   0:41 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:32809 -prefMapHandle 1:278884 -jsInitHandle 2:227672 -parentBuildID 20260309231353 -sandboxReporter 3 -chrootClient 4 -ipcHandle 5 -initialChannelId {481ca707-2ece-4961-806d-26327ccb2d1f} -parentPid 3002 -crashReporter 6 -crashHelper 7 -greomni /snap/firefox/7967/usr/lib/firefox/omni.ja -appomni /snap/firefox/7967/usr/lib/firefox/browser/omni.ja -appDir /snap/firefox/7967/usr/lib/firefox/browser 6 tab
pradita+    3076  1.4  3.9 1461521032 156592 ?   SLsl 17:54   1:25 /snap/code/228/usr/share/code/code --no-sandbox --force-user-env --ozone-platform=x11
pradita+    4285  0.4  3.5 1459515644 142316 ?   Sl   17:55   0:23 /snap/code/228/usr/share/code/code /snap/code/228/usr/share/code/resources/app/extensions/markdown-language-features/dist/serverWorkerMain --node-ipc --clientProcessId=3575
pradita+    3354  0.1  3.0 2610128 120904 ?      Sl   17:54   0:09 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:37717 -prefMapHandle 1:278884 -jsInitHandle 2:227672 -parentBuildID 20260309231353 -sandboxReporter 3 -chrootClient 4 -ipcHandle 5 -initialChannelId {7802a8d4-756b-43c1-b556-68e6b1119eab} -parentPid 3002 -crashReporter 6 -crashHelper 7 -greomni /snap/firefox/7967/usr/lib/firefox/omni.ja -appomni /snap/firefox/7967/usr/lib/firefox/browser/omni.ja -appDir /snap/firefox/7967/usr/lib/firefox/browser 3 tab
pradita+    3469  0.1  2.5 1461316216 103776 ?   Sl   17:54   0:07 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService --lang=en-US --service-sandbox-type=none --no-sandbox --crashpad-handler-pid=3114 --enable-crash-reporter=e9bfb98a-f4aa-4b21-89a7-bd4f93b569d0,no_channel --user-data-dir=/home/praditadf/.config/Code --standard-schemes=vscode-webview,vscode-file --secure-schemes=vscode-webview,vscode-file --cors-schemes=vscode-webview,vscode-file --fetch-schemes=vscode-webview,vscode-file --service-worker-schemes=vscode-webview --code-cache-schemes=vscode-webview,vscode-file --shared-files=v8_context_snapshot_data:100 --field-trial-handle=3,i,3184216701153887361,13250874988657799531,262144 --enable-features=DocumentPolicyIncludeJSCallStacksInCrashReports,EarlyEstablishGpuChannel,EstablishGpuChannelAsync --disable-features=CalculateNativeWinOcclusion,LocalNetworkAccessChecks,ScreenAIOCREnabled,SpareRendererForSitePerProcess,TraceSiteInstanceGetProcessCreation --variations-seed-version --trace-process-track-uuid=3190708995682289984
```
> Proses yang menggunakan memori paling banyak adalah proses dengan PID 3575 yaitu aplikasi visual studio code

#### 2. Di dalam top, tekan 1 . Apa yang berubah pada tampilan? Mengapa informasi ini berguna?

```
top - 19:32:45 up  1:39,  1 user,  load average: 0.92, 0.88, 1.11
Tasks: 222 total,   2 running, 220 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.8 us,  3.1 sy,  0.0 ni, 93.9 id,  0.0 wa,  0.0 hi,  0.2 si,  0.0 st 
MiB Mem :   3914.8 total,    137.2 free,   2489.1 used,   1705.5 buff/cache     
MiB Swap:   2048.0 total,   1712.8 free,    335.2 used.   1425.7 avail Mem 

top - 19:32:55 up  1:39,  1 user,  load average: 1.66, 1.05, 1.16
Tasks: 222 total,   3 running, 219 sleeping,   0 stopped,   0 zombie
%Cpu0  :  5.7 us,  3.8 sy,  0.0 ni, 88.7 id,  0.0 wa,  0.0 hi,  1.9 si,  0.0 st 
%Cpu1  :  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :   3914.8 total,    137.4 free,   2488.9 used,   1714.0 buff/cache     
MiB Swap:   2048.0 total,   1712.8 free,    335.2 used.   1425.9 avail Mem 
```

> Tampilan Cpu total berubah dari yang awalnya menampilkan total penggunaan cpu kemudian berganti menjadi cpu tiap tiap core

#### 3. Di dalam htop, navigasikan ke proses sshd menggunakan tombol panah. Tekan F9 dan amati opsi sinyal yang tersedia


![SLEEP](images/SIGTERM.png)
```
Dengan menggunakan F9 akan muncul opsi sinyal untuk meminta berhenti, dijeda, atau memuat ulang konfigurasi tanpa perlu menuliskan secara manual dengan PID nya
```

# Latihan

## Latihan 6.A

### Eksplorasi Proses Sistem

#### 1. Jalankan ps aux –forest dan temukan proses dengan PID 1. Apa nama dan fungsi proses tersebut dalam sistem Linux modern?

#### 2. Hitung berapa proses yang dimiliki oleh user root dan berapa yang dimiliki oleh user Anda. Mengapa root memiliki lebih banyak proses?

#### 3. Temukan semua proses yang berada dalam kondisi S. Mengapa sebagian besar proses di sistem berada dalam kondisi ini?

## Latihan 6.B

### Simulasi Manajemen Job

#### 1. Jalankan tiga perintah sleep dengan durasi 100, 200, dan 300 detik di background. Verifikasi ketiganya dengan jobs

#### 2. Bawa job kedua ke foreground, jeda dengan Ctrl+Z , lalu kembalikan ke background dengan bg

#### 3. Hentikan job pertama dengan kill %1. Tampilkan kembali daftar job. Berapa job yang tersisa?Latihan 6.B Simulasi Manajemen Job

#### 1. Jalankan tiga perintah sleep dengan durasi 100, 200, dan 300 detik di background. Verifikasi ketiganya dengan jobs

#### 2. Bawa job kedua ke foreground, jeda dengan Ctrl+Z , lalu kembalikan ke background dengan bg

#### 3. Hentikan job pertama dengan kill %1. Tampilkan kembali daftar job. Berapa job yang tersisa?

## Latihan 6.C

### Prioritas dan Sinyal

#### 1. Jalankan dua proses sleep: satu dengan nice +5 dan satu dengan nice +15. Verifikasi nilai NI keduanya dengan ps

#### 2. Gunakan renice untuk mengubah nice proses pertama menjadi +10. Proses mana yang kini lebih diprioritaskan scheduler?

#### 3. Kirim SIGSTOP ke salah satu proses, verifikasi kondisi T-nya, lalu kirim SIGCONT. Akhiri semua proses percobaan dengan pkill sleep
