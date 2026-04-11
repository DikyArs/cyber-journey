

| Layer |     Nama     | Fungsi Simpel                                                               | Contoh                              |
| :---: | :----------: | :-------------------------------------------------------------------------- | :---------------------------------- |
|   7   | Application  | Tempat user berinteraksi langsung dengan aplikasi jaringan                  | Web browser (HTTP), FTP, SMTP, DNS  |
|   6   | Presentation | Mengatur format data biar bisa dibaca, dan enkripsi/dekripsi                | SSL/TLS, konversi gambar JPEG/MP4   |
|   5   |   Session    | Mengatur mulai, jalan, dan selesainya koneksi antar aplikasi                | Login session, koneksi RDP          |
|   4   |  Transport   | Memastikan data terkirim utuh dan urut, atau kirim cepat tanpa jaminan      | TCP (terjamin), UDP (cepat)         |
|   3   |   Network    | Menentukan jalur/rute antar jaringan berbeda, pakai IP address              | IP, Router, IP Address              |
|   2   |  Data Link   | Menghubungkan antar device dalam satu jaringan yang sama, pakai MAC address | MAC Address, Switch, Ethernet       |
|   1   |   Physical   | Media fisik buat ngirim sinyal data                                         | Kabel UTP, Fiber optic, sinyal WiFi |

- **Layer 7-5** = fokus ke aplikasi dan komunikasi antar program
- **Layer 4** = jembatan antara software dan hardware
- **Layer 3-1** = fokus ke infrastruktur dan pengiriman data fisik



## Praktik Terminal

### ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN mode DEFAULT group default qlen 1000
    link/ether 88:d7:f6:9e:fd:b6 brd ff:ff:ff:ff:ff:ff
    altname enx88d7f69efdb6
3: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DORMANT group default qlen 1000
    link/ether f0:03:8c:db:bb:d1 brd ff:ff:ff:ff:ff:ff
    altname wlxf0038cdbbbd1

artinya :

|                              |                                                                                                                                                                                                                                                                          |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ## **lo (Loopback)**         | - Interface virtual untuk komunikasi localhost (127.0.0.1)<br>- `UP` = aktif<br>- `LOWER_UP` = koneksi fisik OK (karena virtual, selalu UP)<br>    <br>- Dipakai untuk testing dan komunikasi antar proses di komputer sendiri                                           |
| ## **enp2s0 (Ethernet/LAN)** | - Kabel LAN (interface wired)<br>- `NO-CARRIER` = kabel tidak terpasang atau switch mati<br>- `UP` = interface aktif secara software, tapi siap menunggu kabel<br>- `state DOWN` = fisik tidak konek, jadi tidak bisa kirim data<br>- MAC: `88:d7:f6:9e:fd:b6`           |
| ## **wlp1s0 (WiFi)**         | - Kartu wireless yang sedang digunakan<br>- `UP` = aktif<br>- `LOWER_UP` = koneksi fisik OK (terkoneksi ke access point)<br>- `state UP` = siap kirim data<br>- `mode DORMANT` = sedang idle/tidak ada traffic aktif, tapi tetap terhubung<br>- MAC: `f0:03:8c:db:bb:d1` |

### ip addr show

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 88:d7:f6:9e:fd:b6 brd ff:ff:ff:ff:ff:ff
    altname enx88d7f69efdb6
3: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether f0:03:8c:db:bb:d1 brd ff:ff:ff:ff:ff:ff
    altname wlxf0038cdbbbd1
    inet 192.168.1.11/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp1s0
       valid_lft 83121sec preferred_lft 83121sec
    inet6 fe80::f203:8cff:fedb:bbd1/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

ip saya : 192.168.1.11/24
artinya : 192.168.1.11 --> alamat komputer saya di jaringan lokal
         /24 --> Berarti subnet mask `255.255.255.0` → 254 komputer bisa dalam 1 jaringan

### ss -tulpn

Netid State  Recv-Q Send-Q Local Address:Port  Peer Address:PortProcess
udp   UNCONN 0      0            0.0.0.0:47732      0.0.0.0:*          
udp   UNCONN 0      0            0.0.0.0:5353       0.0.0.0:*          
udp   UNCONN 0      0               [::]:5353          [::]:*          
udp   UNCONN 0      0               [::]:49421         [::]:*          
tcp   LISTEN 0      4096       127.0.0.1:631        0.0.0.0:*          
tcp   LISTEN 0      128          0.0.0.0:22         0.0.0.0:*          
tcp   LISTEN 0      4096           [::1]:631           [::]:*          
tcp   LISTEN 0      128             [::]:22            [::]:*  

Port yang terbuka: 22, 631, 5353, 47732, 49421
Artinya: 


### ping -c 4 google.com

PING google.com (142.251.12.100) 56(84) bytes of data.
64 bytes from se-in-f100.1e100.net (142.251.12.100): icmp_seq=1 ttl=102 time=28.3 ms
64 bytes from se-in-f100.1e100.net (142.251.12.100): icmp_seq=3 ttl=102 time=27.8 ms
64 bytes from se-in-f100.1e100.net (142.251.12.100): icmp_seq=4 ttl=102 time=28.6 ms

--- google.com ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3024ms
rtt min/avg/max/mdev = 27.845/28.245/28.632/0.321 ms

Hasilnya : 3 dari 4 paket berhasil, 1 paket hilang (25% packet loss), waktu tempuh ~28 ms.
Artinya : Koneksi internet jalan tapi ada sedang gangguan (bisa karena WiFi kurang stabil, jaringan ramai, atau server google sibuk)