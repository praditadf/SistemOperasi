# Manajemen Memori & System Call

## Praktikum 10.1 — Melihat Penggunaan Memori

### 1. Jalankan free -h untuk melihat ringkasan RAM dan swap

```
praditadf@praditadf-VirtualBox:~$ free -h
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.5Gi       199Mi       283Mi       1.6Gi       1.4Gi
Swap:          2.0Gi       135Mi       1.9Gi
```

### 2. Lihat detail memori dari kernel melalui /proc/meminfo

```
praditadf@praditadf-VirtualBox:~$ cat /proc/meminfo | head -n 20
MemTotal:        4008740 kB
MemFree:          258508 kB
MemAvailable:    1643948 kB
Buffers:            6500 kB
Cached:          1658104 kB
SwapCached:        22568 kB
Active:          1207772 kB
Inactive:        2034124 kB
Active(anon):     637180 kB
Inactive(anon):  1041892 kB
Active(file):     570592 kB
Inactive(file):   992232 kB
Unevictable:          32 kB
Mlocked:              32 kB
SwapTotal:       2097148 kB
SwapFree:        1958376 kB
Zswap:                 0 kB
Zswapped:              0 kB
Dirty:             13080 kB
Writeback:             0 kB
```

### Analisis

1. Hitung persentase memori tersedia: available / total × 100%. Jika hasilnya di bawah 10%, sistem mulai kekurangan memori.
```
Memori tersedia = 1.4Gi / 3.8Gi x 100% = 36%, Sistem masih mempunyai memori tersisa
```
2. Pada baris Swap, apakah kolom used bernilai 0? Jika lebih dari 0, kernel sudah pernah memindahkan data ke disk karena RAM tidak cukup.
```
Kolom used bernilai 135Mi, kernel sudah petmah memindahkan data ke disk karena RAM tidak cukup.
```
3. Perhatikan field Cached dan Buffers di /proc/meminfo. Nilai ini sesuai dengan kolom buff/cache pada free -h.
```
Buffers:            6500 kB
Cached:          1658104 kB

buff/cache
1.6Gi
```

## Studi Kasus 10.1 — Server Lambat karena Memori

### 1. Periksa kondisi memori secara 

```
praditadf@praditadf-VirtualBox:~$ free -h
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.3Gi       187Mi       201Mi       1.7Gi       1.5Gi
Swap:          2.0Gi       135Mi       1.9Gi
```

### 2. Pantau proses secara real-time

```
top - 19:20:17 up 14 min,  1 user,  load average: 0.76, 1.85, 1.25
Tasks: 232 total,   3 running, 229 sleeping,   0 stopped,   0 zombie
%Cpu(s):  7.5 us,  6.4 sy,  0.0 ni, 81.2 id,  0.0 wa,  0.0 hi,  4.9 si,  0.0 st 
MiB Mem :   3914.8 total,    119.2 free,   2341.8 used,   1800.0 buff/cache     
MiB Swap:   2048.0 total,   1912.6 free,    135.4 used.   1573.0 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                           
   2038 pradita+  20   0 3901232 239492  89292 R  22.3   6.0   1:30.53 gnome-shell                                                                       
   3091 pradita+  20   0  571436  46948  36396 S   9.3   1.2   0:04.65 gnome-terminal-                                                                   
   2890 _apt      20   0   34208   8008   6868 S   1.0   0.2   0:20.72 http                                                                              
    617 root     -51   0       0      0      0 S   0.7   0.0   0:03.43 irq/18-vmwgfx                                                                     
   3551 pradita+  20   0 1411.3g 363144 139148 S   0.7   9.1   0:53.00 code                                                                              
   4003 pradita+  20   0 1393.6g 388264  87856 S   0.7   9.7   0:26.52 code                                                                              
   4592 root      20   0       0      0      0 R   0.7   0.0   0:00.40 kworker/u9:1+events_unbound                                                       
     15 root      20   0       0      0      0 I   0.3   0.0   0:01.96 rcu_preempt                                                                       
     71 root       0 -20       0      0      0 I   0.3   0.0   0:01.34 kworker/1:1H-kblockd                                                              
    140 root      20   0       0      0      0 I   0.3   0.0   0:01.46 kworker/1:3-events                                                                
      1 root      20   0   23688  14956   9752 S   0.0   0.4   0:03.31 systemd                                                                           
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.03 kthreadd                                                                          
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                            
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp                                                                  
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq                                                                 
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-kvfree_rcu_reclaim                                                      
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_flushwq                                                            
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns                                                                   
     10 root      20   0       0      0      0 I   0.0   0.0   0:00.27 kworker/0:1-mm_percpu_wq                                                          
     11 root       0 -20       0      0      0 I   0.0   0.0   0:00.39 kworker/0:0H-kblockd                                                              
     12 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/u8:0-ipv6_addrconf                                                        
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_percpu_wq                                                            
     14 root      20   0       0      0      0 S   0.0   0.0   0:01.58 ksoftirqd/0                                                                       
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_exp_par_gp_kthread_worker/0                                                   
     17 root      20   0       0      0      0 S   0.0   0.0   0:00.08 rcu_exp_gp_kthread_worker                                                         
     18 root      rt   0       0      0      0 S   0.0   0.0   0:00.05 migration/0                                                                       
     19 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                     
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                           
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                           


top - 19:21:06 up 15 min,  1 user,  load average: 0.41, 1.58, 1.18
Tasks: 226 total,   1 running, 225 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.2 us, 10.4 sy,  0.0 ni, 80.8 id,  0.2 wa,  0.0 hi,  5.5 si,  0.0 st 
MiB Mem : 58.5/3914.8   [|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||                                         ] 
MiB Swap:  7.0/2048.0   [|||||||                                                                                             ] 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                           
   2038 pradita+  20   0 3901248 240932  91648 S  20.5   6.0   1:34.11 gnome-shell                                                                       
   2890 _apt      20   0   34208   8008   6868 S   9.9   0.2   0:22.98 http                                                                              
    573 root      20   0       0      0      0 I   1.0   0.0   0:02.31 kworker/u9:5-events_unbound                                                       
   3091 pradita+  20   0  571568  46996  36396 S   1.0   1.2   0:05.17 gnome-terminal-                                                                   
    617 root     -51   0       0      0      0 S   0.7   0.0   0:03.51 irq/18-vmwgfx                                                                     
   2150 pradita+  20   0  471048  10948   6940 S   0.7   0.3   0:01.48 ibus-daemon                                                                       
   1446 root      20   0  325356   9124   7476 S   0.3   0.2   0:00.43 upowerd                                                                           
   3180 pradita+  20   0 3558140 431600 206684 S   0.3  10.8   0:56.14 firefox                                                                           
   3974 pradita+  20   0 1393.6g 108348  77584 S   0.3   2.7   0:01.70 code                                                                              
      1 root      20   0   23688  14132   9752 S   0.0   0.4   0:03.33 systemd                                                                           
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.03 kthreadd                                                                          
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                            
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp                                                                  
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq                                                                 
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-kvfree_rcu_reclaim                                                      
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_flushwq                                                            
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns                                                                   
     10 root      20   0       0      0      0 I   0.0   0.0   0:00.28 kworker/0:1-events                                                                
     11 root       0 -20       0      0      0 I   0.0   0.0   0:00.40 kworker/0:0H-kblockd                                                              
     12 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/u8:0-ipv6_addrconf                                                        
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_percpu_wq                                                            
     14 root      20   0       0      0      0 S   0.0   0.0   0:01.60 ksoftirqd/0                                                                       
     15 root      20   0       0      0      0 I   0.0   0.0   0:01.99 rcu_preempt                                                                       
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_exp_par_gp_kthread_worker/0                                                   
     17 root      20   0       0      0      0 S   0.0   0.0   0:00.08 rcu_exp_gp_kthread_worker                                                         
     18 root      rt   0       0      0      0 S   0.0   0.0   0:00.05 migration/0                                                                       
     19 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                     
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                           
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                           


```

### Analisis

1. Apakah nilai available sangat kecil (misalnya di bawah 200 MB pada server dengan RAM 2 GB)? Jika ya, server kemungkinan kekurangan memori.
```
```
2. Apakah kolom used pada baris Swap lebih dari 0? Jika ya, kernel sedang enggunakan swap, yang berarti performa menurun.
```
```
3. Di tampilan top, proses apa yang memiliki %MEM terbesar? Proses tersebut enjadi kandidat utama penyebab lambatnya server.
```
```

## Praktikum 10.2 — Mengamati Aktivitas Paging

### 1. Jalankan vmstat dengan interval 1 detik, 5 sampel

```
praditadf@praditadf-VirtualBox:~$ vmstat 1 5
procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu-------
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu
 1  0 166320 109812   7032 1882988   17  157  3232  1082 2197    8  7 16 76  0  0  0
 0  0 166320 109348   7040 1883856    0    0     0    56 1681  374  1  6 93  0  0  0
 0  0 166320 108660   7040 1884648    0    0     0     0 1659  294  1  4 95  0  0  0
 0  0 166320 108188   7040 1885352    0    0     0     0 1724  420  1  6 94  0  0  0
 0  0 166320 108188   7040 1886068    0    0     0     0 1844  480  1  6 94  0  0  0
```

### Analisis

1. Amati nilai si dan so pada kelima baris. Pada sistem normal dengan RAM cukup, kedua nilai ini selalu 0.
```
```
2. Jika nilai si atau so sesekali muncul lebih dari 0, artinya pernah ada aktivitas swap. Ini masih wajar jika tidak terus-menerus.
```
```
3. Jika si dan so terus-menerus lebih dari 0, sistem dalam kondisi memory pressure serius — performa turun drastis karena akses disk jauh lebih lambat
dari RAM.
```
```
4. Perhatikan juga kolom free (RAM kosong) dan buff (buffer) untuk memahami kondisi keseluruhan RAM saat itu.
```
```

## Praktikum 10.3 — Membuat dan Mengonfigurasi Swap File

### 1. Buat file berukuran 512 MB sebagai calon swap

```
praditadf@praditadf-VirtualBox:~$ sudo fallocate -l 512M /swapfile-week10
```

### 2. Atur permission file menjadi 600 — hanya root yang boleh membaca dan menulis

```
praditadf@praditadf-VirtualBox:~$ sudo chmod 600 /swapfile-week10
```

### 3. Format file sebagai area swap, lalu aktifkan

```
praditadf@praditadf-VirtualBox:~$ sudo mkswap /swapfile-week10
Setting up swapspace version 1, size = 512 MiB (536866816 bytes)
no label, UUID=9950d621-5393-45c2-bdb7-30e473ef74ea
praditadf@praditadf-VirtualBox:~$ sudo swapon /swapfile-week10
```

### 4. Verifikasi swap aktif. Anda akan melihat entri /swapfile-week10 dengan ukuran 512M, dan nilai total pada baris Swap di free -h bertambah 512M

```
praditadf@praditadf-VirtualBox:~$ swapon --show
NAME             TYPE SIZE USED PRIO
/swap.img        file   2G 447M   -2
/swapfile-week10 file 512M   0B   -3
praditadf@praditadf-VirtualBox:~$ free -h
               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       176Mi       187Mi       1.9Gi       1.7Gi
Swap:          2.5Gi       449Mi       2.1Gi
```

### 5. Periksa nilai swappiness, ubah sementara, dan verifikasi perubahan

```
praditadf@praditadf-VirtualBox:~$ cat /proc/sys/vm/swappiness
60
praditadf@praditadf-VirtualBox:~$ sudo sysctl vm.swappiness=10
vm.swappiness = 10
praditadf@praditadf-VirtualBox:~$ cat /proc/sys/vm/swappiness
10
```

### Analisis

1. Berapa nilai swappiness default? Apa artinya bagi perilaku kernel dalam menggunakan swap?
```
```

2. Setelah diubah ke 10, konfirmasi nilai berubah pada output cat kedua. Apa dampak nilai 10 terhadap penggunaan swap dibanding nilai 60?
```
```

3. Apakah entri /swapfile-week10 muncul di swapon –show? Jika tidak, pastikan Langkah 2 (chmod 600) sudah dijalankan sebelum Langkah 3.
```
```

## Praktikum 10.4 — Monitoring Memory

### 1. Ambil snapshot proses diurutkan dari penggunaan memori terbesar

```
praditadf@praditadf-VirtualBox:~$ ps aux --sort=-%mem | head
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
pradita+    4003  3.3  8.2 1461327920 331872 ?   Sl   19:13   0:32 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService --lang=en-US --service-sandbox-type=none --no-sandbox --dns-result-order=ipv4first --experimental-network-inspection --inspect-port=0 --js-flags=--nodecommit_pooled_pages --crashpad-handler-pid=3308 --enable-crash-reporter=e9bfb98a-f4aa-4b21-89a7-bd4f93b569d0,no_channel --user-data-dir=/home/praditadf/.config/Code --standard-schemes=vscode-webview,vscode-file --secure-schemes=vscode-webview,vscode-file --cors-schemes=vscode-webview,vscode-file --fetch-schemes=vscode-webview,vscode-file --service-worker-schemes=vscode-webview --code-cache-schemes=vscode-webview,vscode-file --shared-files=v8_context_snapshot_data:100 --field-trial-handle=3,i,17405268602528586336,10985351871226386686,262144 --enable-features=DocumentPolicyIncludeJSCallStacksInCrashReports,EarlyEstablishGpuChannel,EstablishGpuChannelAsync --disable-features=CalculateNativeWinOcclusion,LocalNetworkAccessChecks,ScreenAIOCREnabled,SpareRendererForSitePerProcess,TraceSiteInstanceGetProcessCreation --variations-seed-version --trace-process-track-uuid=3190708995682289984
pradita+    3180  9.9  7.8 3592364 314908 ?      Sl   19:13   1:37 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    3551  7.2  7.2 1479816660 288828 ?   Sl   19:13   1:10 /snap/code/235/usr/share/code/code --type=zygote --no-sandbox
root        2827  2.6  5.7 503524 231036 ?       Rl   19:09   0:32 /usr/bin/python3 /usr/bin/unattended-upgrade
pradita+    3786  2.7  5.7 7004972 229844 ?      Sl   19:13   0:26 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:32906 -prefMapHandle 1:278832 -jsInitHandle 2:227672 -parentBuildID 20260309231353 -sandboxReporter 3 -chrootClient 4 -ipcHandle 5 -initialChannelId {1020d8be-ae05-4ac2-aa69-77692daf63a8} -parentPid 3180 -crashReporter 6 -crashHelper 7 -greomni /snap/firefox/7967/usr/lib/firefox/omni.ja -appomni /snap/firefox/7967/usr/lib/firefox/browser/omni.ja -appDir /snap/firefox/7967/usr/lib/firefox/browser 6 tab
pradita+    2038 12.0  4.2 3975248 170356 ?      Ssl  19:07   2:39 /usr/bin/gnome-shell
pradita+    3270  1.6  2.6 1461463556 105792 ?   SLsl 19:13   0:16 /snap/code/235/usr/share/code/code --no-sandbox --force-user-env --ozone-platform=x11
pradita+    3499  0.4  2.0 2608680 83084 ?       Sl   19:13   0:04 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:39098 -prefMapHandle 1:278832 -jsInitHandle 2:227672 -parentBuildID 20260309231353 -sandboxReporter 3 -chrootClient 4 -ipcHandle 5 -initialChannelId {aa06f6b9-d037-4b7b-9fa5-d407fbef5f8b} -parentPid 3180 -crashReporter 6 -crashHelper 7 -greomni /snap/firefox/7967/usr/lib/firefox/omni.ja -appomni /snap/firefox/7967/usr/lib/firefox/browser/omni.ja -appDir /snap/firefox/7967/usr/lib/firefox/browser 3 tab
pradita+    3609  1.5  1.6 33933600 67600 ?      Sl   19:13   0:15 /proc/self/exe --type=gpu-process --disable-gpu-sandbox --no-sandbox --ozone-platform=x11 --crashpad-handler-pid=3308 --enable-crash-reporter=e9bfb98a-f4aa-4b21-89a7-bd4f93b569d0,no_channel --user-data-dir=/home/praditadf/.config/Code --gpu-preferences=UAAAAAAAAAAgAAAEAAAAAAAAAAAAAGAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAYAAAAAAAAABgAAAAAAAAAAQAAAAAAAAAIAAAAAAAAAAgAAAAAAAAA --use-gl=angle --use-angle=swiftshader-webgl --shared-files --field-trial-handle=3,i,17405268602528586336,10985351871226386686,262144 --enable-features=DocumentPolicyIncludeJSCallStacksInCrashReports,EarlyEstablishGpuChannel,EstablishGpuChannelAsync --disable-features=CalculateNativeWinOcclusion,LocalNetworkAccessChecks,ScreenAIOCREnabled,SpareRendererForSitePerProcess,TraceSiteInstanceGetProcessCreation --variations-seed-version --trace-process-track-uuid=3190708992871164437
```

### 2. Pantau secara real-time dengan top

```
top - 19:30:59 up 25 min,  1 user,  load average: 1.88, 2.20, 1.62
Tasks: 224 total,   1 running, 223 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.9 us,  1.2 sy,  0.0 ni, 93.3 id,  0.0 wa,  0.0 hi,  4.6 si,  0.0 st 
MiB Mem : 53.0/3914.8   [|||||||||||||||||||||||||||||||||||||||||||||||||||||                                               ] 
MiB Swap: 27.4/2048.0   [|||||||||||||||||||||||||||                                                                         ] 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                           
   2038 pradita+  20   0 3975264 170364  92188 S   3.0   4.2   2:44.91 /usr/bin/gnome-shell                                                              
   3091 pradita+  20   0  571700  49364  41332 S   1.0   1.2   0:12.01 /usr/libexec/gnome-terminal-server                                                
   3180 pradita+  20   0 3592364 317456 122996 S   0.7   7.9   1:40.55 /snap/firefox/7967/usr/lib/firefox/firefox                                        
    140 root      20   0       0      0      0 I   0.3   0.0   0:02.45 [kworker/1:3-events]                                                              
   3973 pradita+  20   0 1393.6g  66696  48148 S   0.3   1.7   0:10.09 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService --lang=e+ 
   4295 pradita+  20   0 2568148  46088  40892 S   0.3   1.1   0:01.17 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHand+ 
  19683 pradita+  20   0   23200   6104   3852 R   0.3   0.2   0:00.11 top                                                                               
      1 root      20   0   23508  14444   9728 S   0.0   0.4   0:04.32 /sbin/init splash                                                                 
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.03 [kthreadd]                                                                        
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 [pool_workqueue_release]                                                          
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 [kworker/R-rcu_gp]                                                                
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 [kworker/R-sync_wq]                                                               
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 [kworker/R-kvfree_rcu_reclaim]                                                    
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 [kworker/R-slub_flushwq]                                                          
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 [kworker/R-netns]                                                                 
     10 root      20   0       0      0      0 I   0.0   0.0   0:00.43 [kworker/0:1-events]                                                              
     11 root       0 -20       0      0      0 I   0.0   0.0   0:00.90 [kworker/0:0H-kblockd]                                                            
     12 root      20   0       0      0      0 I   0.0   0.0   0:00.00 [kworker/u8:0-ipv6_addrconf]                                                      
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 [kworker/R-mm_percpu_wq]                                                          
     14 root      20   0       0      0      0 S   0.0   0.0   0:02.14 [ksoftirqd/0]                                                                     
     15 root      20   0       0      0      0 I   0.0   0.0   0:04.33 [rcu_preempt]                                                                     
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.00 [rcu_exp_par_gp_kthread_worker/0]                                                 
     17 root      20   0       0      0      0 S   0.0   0.0   0:00.09 [rcu_exp_gp_kthread_worker]                                                       
     18 root      rt   0       0      0      0 S   0.0   0.0   0:00.15 [migration/0]                                                                     
     19 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 [idle_inject/0]                                                                   
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.00 [cpuhp/0]                                                                         
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 [cpuhp/1]                                                                         
     22 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 [idle_inject/1]                                                                   
     23 root      rt   0       0      0      0 S   0.0   0.0   0:00.84 [migration/1]                              
```

### Analisis

1. Proses apa yang berada di urutan pertama? Catat nilai %MEM dan RSS-nya.
```
```

2. Konversikan RSS dari KB ke MB (bagi 1024). Misalnya, RSS=524288 berarti proses menggunakan 512 MB RAM. Apakah wajar untuk jenis program tersebut?
```
```

3. Mengapa VSZ selalu lebih besar dari RSS pada proses yang sama?
```
```

4. Apakah urutan proses di ps konsisten dengan tampilan top saat diurutkan berdasarkan %MEM?
```
```

## Praktikum 10.5 — Script Monitor Memori

### 1. Masuk ke direktori kerja dan buat file script

```
praditadf@praditadf-VirtualBox:~$ cd ~/praktikum-os/week10-memory
praditadf@praditadf-VirtualBox:~/praktikum-os/week10-memory$ nano monitor-memori.sh
```

### 2. Ketik isi script berikut

```
#!/bin/bash
set -euo pipefail

THRESHOLD=20
echo "=== Monitor Memori ==="
date
echo

free -h
echo

AVAIL=$(free | awk '/Mem/ {printf "%d", $7/$2*100}')
if [ "$AVAIL" -lt "$THRESHOLD" ]; then
echo "PERINGATAN: Memori tersedia hanya ${AVAIL}%!"
else
echo "Status: Memori tersedia ${AVAIL}% (normal)"
fi
echo
echo "--- 5 Proses Memori Tertinggi ---"
ps aux --sort=-%mem | head -n 6 | tail -n 5
```

### 3. Beri izin eksekusi dan jalankan script

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week10-memory$ chmod +x monitor-memori.sh 
praditadf@praditadf-VirtualBox:~/praktikum-os/week10-memory$ bash monitor-memori.sh 
=== Monitor Memori ===
Sun May  3 07:37:09 PM WIB 2026

               total        used        free      shared  buff/cache   available
Mem:           3.8Gi       2.1Gi       231Mi       135Mi       1.8Gi       1.7Gi
Swap:          2.0Gi       553Mi       1.5Gi

Status: Memori tersedia 43% (normal)

--- 5 Proses Memori Tertinggi ---
pradita+    4003  2.6  8.3 1461327920 334616 ?   Sl   19:13   0:37 /proc/self/exe --type=utility --utility-sub-type=node.mojom.NodeService --lang=en-US --service-sandbox-type=none --no-sandbox --dns-result-order=ipv4first --experimental-network-inspection --inspect-port=0 --js-flags=--nodecommit_pooled_pages --crashpad-handler-pid=3308 --enable-crash-reporter=e9bfb98a-f4aa-4b21-89a7-bd4f93b569d0,no_channel --user-data-dir=/home/praditadf/.config/Code --standard-schemes=vscode-webview,vscode-file --secure-schemes=vscode-webview,vscode-file --cors-schemes=vscode-webview,vscode-file --fetch-schemes=vscode-webview,vscode-file --service-worker-schemes=vscode-webview --code-cache-schemes=vscode-webview,vscode-file --shared-files=v8_context_snapshot_data:100 --field-trial-handle=3,i,17405268602528586336,10985351871226386686,262144 --enable-features=DocumentPolicyIncludeJSCallStacksInCrashReports,EarlyEstablishGpuChannel,EstablishGpuChannelAsync --disable-features=CalculateNativeWinOcclusion,LocalNetworkAccessChecks,ScreenAIOCREnabled,SpareRendererForSitePerProcess,TraceSiteInstanceGetProcessCreation --variations-seed-version --trace-process-track-uuid=3190708995682289984
pradita+    3180  9.0  7.6 3520020 307072 ?      Sl   19:13   2:08 /snap/firefox/7967/usr/lib/firefox/firefox
pradita+    3551  6.2  7.5 1479816372 301464 ?   Sl   19:13   1:28 /snap/code/235/usr/share/code/code --type=zygote --no-sandbox
pradita+    3786  2.8  4.8 6954164 194604 ?      Sl   19:13   0:39 /snap/firefox/7967/usr/lib/firefox/firefox -contentproc -isForBrowser -prefsHandle 0:32906 -prefMapHandle 1:278832 -jsInitHandle 2:227672 -parentBuildID 20260309231353 -sandboxReporter 3 -chrootClient 4 -ipcHandle 5 -initialChannelId {1020d8be-ae05-4ac2-aa69-77692daf63a8} -parentPid 3180 -crashReporter 6 -crashHelper 7 -greomni /snap/firefox/7967/usr/lib/firefox/omni.ja -appomni /snap/firefox/7967/usr/lib/firefox/browser/omni.ja -appDir /snap/firefox/7967/usr/lib/firefox/browser 6 tab
root       20476  7.7  4.5 629380 181248 ?       Ssl  19:36   0:01 /usr/libexec/fwupd/fwupd
```

### Analisis

1. Variabel THRESHOLD=20 menetapkan batas persentase. Perintah free | awk ’/Mem/ {printf "%d", $7/$2*100}’ mengambil kolom ke-7 (available) dibagi kolom ke-2 (total) dari baris Mem, lalu dikalikan 100 untuk menghasilkan persentase bilangan bulat.
```
```

2. Kondisi if [ "$AVAIL" -lt "$THRESHOLD" ] bernilai benar jika persentase memori tersedia di bawah 20.
```
```

3. Ubah THRESHOLD menjadi 90 dan jalankan ulang. Apa yang berubah pada output? Mengapa demikian?
```
```

## Studi Kasus 10.2 — Gagal Akses File

### 1. Buat direktori dan file konfigurasi contoh

```
praditadf@praditadf-VirtualBox:~$ mkdir -p ~/praktikum-os/week10-memory/syscall-case
praditadf@praditadf-VirtualBox:~$ cd ~/praktikum-os/week10-memory/syscall-case
praditadf@praditadf-VirtualBox:~/praktikum-os/week10-memory/syscall-case$ echo "PORT=8080" > app.conf
praditadf@praditadf-VirtualBox:~/praktikum-os/week10-memory/syscall-case$ ls -l app.conf 
-rw-rw-r-- 1 praditadf praditadf 10 May  3 19:39 app.conf
praditadf@praditadf-VirtualBox:~/praktikum-os/week10-memory/syscall-case$ cat app.conf 
PORT=8080
```

### 2. Simulasikan permission bermasalah

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week10-memory/syscall-case$ chmod 000 app.conf
praditadf@praditadf-VirtualBox:~/praktikum-os/week10-memory/syscall-case$ cat app.conf 
cat: app.conf: Permission denied
```

### 3. Kembalikan permission dan verifikasi

```
praditadf@praditadf-VirtualBox:~/praktikum-os/week10-memory/syscall-case$ chmod 644 app.conf 
praditadf@praditadf-VirtualBox:~/praktikum-os/week10-memory/syscall-case$ cat app.conf 
PORT=8080
```

### Analisis

1. Mengapa cat menghasilkan Permission denied setelah chmod 000? System call apa yang gagal?
```
```

2. Apa perbedaan pesan error Permission denied vs No such file or directory? Coba rm app.conf lalu cat app.conf untuk melihat perbedaannya.
```
praditadf@praditadf-VirtualBox:~/praktikum-os/week10-memory/syscall-case$ rm app.conf 
praditadf@praditadf-VirtualBox:~/praktikum-os/week10-memory/syscall-case$ cat app.conf
cat: app.conf: No such file or directory
```

3. Permission 644 berarti apa untuk owner, group, dan others?
```
```

## Praktikum 10.6 — Mengamati System Call dengan strace

### 1. Lihat 30 baris pertama system call dari perintah ls

```
praditadf@praditadf-VirtualBox:~$ strace ls 2>&1 \ head -n 30
execve("/usr/bin/ls", ["ls", " head", "-n", "30"], 0x7ffd5ff483c8 /* 49 vars */) = 0
brk(NULL)                               = 0x64357ac59000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7777b4630000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=65527, ...}) = 0
mmap(NULL, 65527, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7777b4620000
close(3)                                = 0
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libselinux.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=174472, ...}) = 0
mmap(NULL, 181960, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7777b45f3000
mmap(0x7777b45f9000, 118784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7777b45f9000
mmap(0x7777b4616000, 24576, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23000) = 0x7777b4616000
mmap(0x7777b461c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x29000) = 0x7777b461c000
mmap(0x7777b461e000, 5832, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7777b461e000
close(3)                                = 0
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\243\2\0\0\0\0\0"..., 832) = 832
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
fstat(3, {st_mode=S_IFREG|0755, st_size=2125328, ...}) = 0
pread64(3, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
mmap(NULL, 2170256, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7777b4200000
mmap(0x7777b4228000, 1605632, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x28000) = 0x7777b4228000
mmap(0x7777b43b0000, 323584, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b0000) = 0x7777b43b0000
mmap(0x7777b43ff000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1fe000) = 0x7777b43ff000
mmap(0x7777b4405000, 52624, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7777b4405000
close(3)                                = 0
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libpcre2-8.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=625344, ...}) = 0
mmap(NULL, 627472, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7777b4559000
mmap(0x7777b455b000, 450560, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7777b455b000
mmap(0x7777b45c9000, 163840, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x70000) = 0x7777b45c9000
mmap(0x7777b45f1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x97000) = 0x7777b45f1000
close(3)                                = 0
mmap(NULL, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7777b4556000
arch_prctl(ARCH_SET_FS, 0x7777b4556800) = 0
set_tid_address(0x7777b4556ad0)         = 20654
set_robust_list(0x7777b4556ae0, 24)     = 0
rseq(0x7777b4557120, 0x20, 0, 0x53053053) = 0
mprotect(0x7777b43ff000, 16384, PROT_READ) = 0
mprotect(0x7777b45f1000, 4096, PROT_READ) = 0
mprotect(0x7777b461c000, 4096, PROT_READ) = 0
mprotect(0x6435489c7000, 8192, PROT_READ) = 0
mprotect(0x7777b4670000, 8192, PROT_READ) = 0
prlimit64(0, RLIMIT_STACK, NULL, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
munmap(0x7777b4620000, 65527)           = 0
statfs("/sys/fs/selinux", 0x7ffef78dc6e0) = -1 ENOENT (No such file or directory)
statfs("/selinux", 0x7ffef78dc6e0)      = -1 ENOENT (No such file or directory)
getrandom("\x14\xef\x64\xe0\xdd\x35\x50\x95", 8, GRND_NONBLOCK) = 8
brk(NULL)                               = 0x64357ac59000
brk(0x64357ac7a000)                     = 0x64357ac7a000
openat(AT_FDCWD, "/proc/filesystems", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
read(3, "nodev\tsysfs\nnodev\ttmpfs\nnodev\tbd"..., 1024) = 393
read(3, "", 1024)                       = 0
close(3)                                = 0
access("/etc/selinux/config", F_OK)     = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=14596880, ...}) = 0
mmap(NULL, 14596880, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7777b3400000
close(3)                                = 0
ioctl(1, TCGETS, {c_iflag=ICRNL|IXON|IUTF8, c_oflag=NL0|CR0|TAB0|BS0|VT0|FF0|OPOST|ONLCR, c_cflag=B38400|CS8|CREAD, c_lflag=ISIG|ICANON|ECHO|ECHOE|ECHOK|IEXTEN|ECHOCTL|ECHOKE, ...}) = 0
openat(AT_FDCWD, "/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2996, ...}) = 0
read(3, "# Locale name alias data base.\n#"..., 4096) = 2996
read(3, "", 4096)                       = 0
close(3)                                = 0
openat(AT_FDCWD, "/usr/share/locale/en_US.UTF-8/LC_TIME/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en_US.utf8/LC_TIME/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en_US/LC_TIME/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en.UTF-8/LC_TIME/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en.utf8/LC_TIME/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en/LC_TIME/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=27028, ...}) = 0
mmap(NULL, 27028, PROT_READ, MAP_SHARED, 3, 0) = 0x7777b4629000
close(3)                                = 0
futex(0x7777b440472c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
statx(AT_FDCWD, " head", AT_STATX_SYNC_AS_STAT|AT_SYMLINK_NOFOLLOW|AT_NO_AUTOMOUNT, STATX_MODE|STATX_NLINK|STATX_UID|STATX_GID|STATX_MTIME|STATX_SIZE, 0x7ffef78dc1c0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en_US.UTF-8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en_US.utf8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en_US/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en.UTF-8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en.utf8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en_US.UTF-8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en_US/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en.utf8/LC_MESSAGES/coreutils.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en/LC_MESSAGES/coreutils.mo", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=613, ...}) = 0
mmap(NULL, 613, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7777b4628000
close(3)                                = 0
write(2, "ls: ", 4ls: )                     = 4
write(2, "cannot access ' head'", 21cannot access ' head')   = 21
openat(AT_FDCWD, "/usr/share/locale/en_US.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en_US.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en.utf8/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
write(2, ": No such file or directory", 27: No such file or directory) = 27
write(2, "\n", 1
)                       = 1
statx(AT_FDCWD, "30", AT_STATX_SYNC_AS_STAT|AT_SYMLINK_NOFOLLOW|AT_NO_AUTOMOUNT, STATX_MODE|STATX_NLINK|STATX_UID|STATX_GID|STATX_MTIME|STATX_SIZE, 0x7ffef78dc1c0) = -1 ENOENT (No such file or directory)
write(2, "ls: ", 4ls: )                     = 4
write(2, "cannot access '30'", 18cannot access '30')      = 18
write(2, ": No such file or directory", 27: No such file or directory) = 27
write(2, "\n", 1
)                       = 1
close(1)                                = 0
close(2)                                = 0
exit_group(2)                           = ?
+++ exited with 2 +++
```

### 2. Lihat ringkasan statistik dan bandingkan dua direktori berbeda

```
praditadf@praditadf-VirtualBox:~$ strace -c ls
'2026-03-11 11-12-11.mp4'   error.log    path.txt
 A       error.txt    Pictures
 aaaaaaa      Github    ping-log.txt
 app.log      halo.txt    play
 B       hasil-pencarian.txt   praktikum-os
 backup-error.log     IvfhB    Public
 backup.sh      IvfhB.1    SistemOperasi
 backup-succes.log     IvfhB.2    snap
 backup-success.log     IvfhB.3    sorted-users.txt
 backup.tar.gz      IvfhB.4    system
 bye.txt      large-logs.txt   Templates
 C       log.txt    Videos
 config.txt      monitor.sh    wget-log
 Desktop      Music    z
 Documents      mydir
 Downloads      myerror.txt
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 47.29    0.000297          59         5           mprotect
 13.54    0.000085           5        16           write
  7.32    0.000046          23         2           getdents64
  5.73    0.000036           5         7           openat
  4.14    0.000026           5         5           read
  4.14    0.000026          26         1           munmap
  3.82    0.000024           2         9           close
  3.50    0.000022          11         2         2 statfs
  3.03    0.000019           6         3           brk
  1.91    0.000012           1         8           fstat
  1.91    0.000012           0        18           mmap
  1.43    0.000009           4         2           ioctl
  0.96    0.000006           3         2         2 access
  0.80    0.000005           5         1           getrandom
  0.48    0.000003           3         1           prlimit64
  0.00    0.000000           0         2           pread64
  0.00    0.000000           0         1           execve
  0.00    0.000000           0         1           arch_prctl
  0.00    0.000000           0         1           set_tid_address
  0.00    0.000000           0         1           set_robust_list
  0.00    0.000000           0         1           rseq
------ ----------- ----------- --------- --------- ----------------
100.00    0.000628           7        89         4 total
praditadf@praditadf-VirtualBox:~$ strace -c ls /etc 2>&1 | tail -5
  0.51    0.000001           1         1           getrandom
  0.51    0.000001           1         1           rseq
  0.00    0.000000           0         1           execve
------ ----------- ----------- --------- --------- ----------------
100.00    0.000195           2        76         5 total
```

### Analisis

1. Dari output Langkah 1, identifikasi minimal 4 system call berbeda. Jelaskan fungsi singkat masing-masing berdasarkan argumen yang terlihat.
```
```

2. Dari ringkasan strace -c, system call mana yang paling sering dipanggil? Mengapa?
```
```

3. Apakah ada system call dengan errors lebih dari 0? Apakah itu berarti program bermasalah, ataukah bagian normal dari logika program?
```
```

4. Apakah jumlah system call berbeda antara ls dan ls /etc? Faktor apa yang menyebabkan perbedaan tersebut?
```
```
## Tugas Praktikum

### 1. Tugas 10.1 Audit Penggunaan Memori Sistem

### Instruksi: Buat script memory-audit.sh yang menghasilkan laporan kondisi memori sistem secara otomatis

### Analisis

1. Hitung persentase memori tersedia (available / total × 100%). Apakah sistem dalam kondisi normal?
2. Mengapa buff/cache tidak dihitung sebagai memori yang terpakai dari sudut pandang ketersediaan untuk aplikasi?
3. Dari /proc/meminfo, apakah SwapTotal lebih besar dari 0? Berapa nilai SwapFree?

### 2. Tugas 10.2 Identifikasi Proses dengan Memori Tertinggi

### Instruksi: Simpan daftar 10 proses pengguna memori terbesar ke file

### Analisis

1. Proses apa di urutan pertama? Catat nilai %MEM dan RSS.
2. Konversikan RSS ke MB (bagi 1024). Apakah wajar?
3. Jumlahkan %MEM dari 5 proses teratas. Berapa persen RAM yang mereka gunakan bersama?

### 3. Tugas 10.3 Membuat dan Memverifikasi Swap File

### Instruksi: Buat swap file khusus tugas sebesar 256 MB dan verifikasi

### Analisis

1. Identifikasi kolom NAME, TYPE, SIZE, dan USED pada output swapon –show.
2. Apakah nilai total pada baris Swap di free -h bertambah 256 MB?
3. Mengapa permission 600 penting? Apa risiko jika diatur ke 644?

### 4. Tugas 10.4 Analisis System Call dengan strace

### Instruksi: Analisis system call yang dipanggil perintah ls

### Analisis

1. Sebutkan minimal 5 system call dari strace-summary.txt beserta fungsi singkatnya.
2. System call mana yang paling sering dipanggil? Mengapa?
3. Apakah ada errors lebih dari 0? Apakah program tetap berjalan normal meskipun ada kegagalan tersebut?

### 5. Tugas 10.5 Studi Kasus Diagnosa Server Lambat

### Skenario: Server terasa lambat. Buat script diagnosa yang menggabungkan semua pemeriksaan dari bab ini menggunakan fungsi Bash

### Analisis

1. Jelaskan peran masing-masing fungsi: cek_memori, cek_swap, cek_proses, cek_paging, dan ringkasan. Mengapa diagnosa dipecah menjadi fungsi terpisah?
2. Berdasarkan bagian RINGKASAN, apakah kondisi sistem normal atau kritis? Jelaskan berdasarkan nilai threshold yang digunakan script.
3. Mengapa script menggunakan tee "$LAPORAN" bukan redirection biasa > "$LAPORAN"? Apa keuntungannya?
4. Dari output cek_paging, apakah ada aktivitas si atau so? Jika ada, apa implikasinya terhadap performa server?
