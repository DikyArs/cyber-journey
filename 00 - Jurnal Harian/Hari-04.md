# Hari 04 — [03-04-2026]

## Yang dipelajari
- ip addres
- subnetting
- ip publik & ip private


## Hasil Praktik in terminal

output:

```
┌──(kaii@debian)-[~]
└─$ ip addr show
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
    inet 192.168.1.12/24 brd 192.168.1.255 scope global dynamic noprefixroute wlp1s0
       valid_lft 86365sec preferred_lft 86365sec
    inet6 fe80::f203:8cff:fedb:bbd1/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```

```
┌──(kaii@debian)-[~]
└─$ curl ifconfig.me
157.15.0.191
```

```
┌──(kaii@debian)-[~]
└─$ sudo nmap -sn 192.168.1.11/24
Starting Nmap 7.95 ( https://nmap.org ) at 2026-04-11 08:24 WIB
Nmap scan report for 192.168.1.1 (192.168.1.1)
Host is up (0.0026s latency).
MAC Address: B0:B1:94:37:7A:2E (zte)
Nmap scan report for 192.168.1.3 (192.168.1.3)
Host is up (0.11s latency).
MAC Address: 06:DB:64:54:9F:7C (Unknown)
Nmap scan report for 192.168.1.5 (192.168.1.5)
Host is up (0.13s latency).
MAC Address: 82:DB:24:AA:8D:CB (Unknown)
Nmap scan report for 192.168.1.7 (192.168.1.7)
Host is up (0.11s latency).
MAC Address: 0C:A8:A7:C7:00:1C (Samsung Electronics)
Nmap scan report for 192.168.1.17 (192.168.1.17)
Host is up (0.091s latency).
MAC Address: 00:08:22:14:B5:8A (InPro Comm)
Nmap scan report for 192.168.1.12 (192.168.1.12)
Host is up.
Nmap done: 256 IP addresses (6 hosts up) scanned in 7.33 seconds

```

- IP laptop saya: 192.168.1.11
- Gateway saya: 192.168.1.1
- IP public saya:  157.15.0.189
- Device yang ketemu di nmap: 2 (192.168.1.1 adalah ip dari router)


## Hasil Quiz

1. IP 192.168.1.50/24 — berapa range host yang valid?
2. Bedanya IP public dan IP private itu apa?
3. Kalau subnet mask /24, berapa jumlah host maksimal?
4. IP laptop kamu berapa? Masuk kelas apa?
5. Apa fungsi gateway?

jawab :

1. 192.168.1.1 - 192.168.1.254
2. **ip publik** adalah ip yang bisa diakses melalui internet, inilah yang terlihat saat kita berselancar di internet. misal membuka google.com ip inilah yang akan terlihat saat berkomunikasi dengan server google.
   **ip private** adalah ip yang berlaku di jaringan lokal saja tidak dapat diakses dari internet hanya bisa untuk komunikasi dalam Wi-Fi/jaringan lokal yang sama.


| Aspek  | IP Publik                                            | IP Private                                                      |
| ------ | ---------------------------------------------------- | --------------------------------------------------------------- |
| Akses  | Bisa diakses dari internet di seluruh dunia          | Hanya bisa diakses di dalam jaringan lokal (LAN)                |
| Unik   | Harus unik secara global                             | Cukup unik di dalam jaringan lokal saja                         |
| Biaya  | Harus disewa dari penyedia layanan internet (ISP)    | Gratis, bisa dipakai siapa saja                                 |
| Contoh | 8.8.8.8 (DNS Google), 1.1.1.1 (Cloudflare)           | 192.168.x.x, 10.x.x.x, 172.16.x.x - 172.31.x.x                  |
| Fungsi | Agar perangkat bisa ditemukan dan mengakses internet | Untuk keperluan internal seperti di rumah, kantor, atau sekolah |

3. host maksimal pada /24 adalah 254 host(256 - 2)
   karena rentang host di prefix ini adalah 1 - 254, -2 karena 0 untuk network id dan 255 untuk broadcast
4. ip laptop saya adalah 192.168.1.11 masuk di kelas C (Private IP)

| Kelas   | Oktet Pertama | Contoh      | Keterangan                                         |
| ------- | ------------- | ----------- | -------------------------------------------------- |
| Kelas A | 1 - 126       | 10.0.0.1    | Untuk jaringan sangat besar                        |
| Kelas B | 128 - 191     | 172.16.0.1  | Untuk jaringan menengah                            |
| Kelas c | 192 - 223     | 192.168.1.1 | Untuk jaringan kecil (paling umum di rumah/kantor) |
5. Gateway adalah pintu keluar masuknya data dari satu jaringan ke jaringan lain.

   **Fungsi utamanya:**

6. Menghubungkan jaringan lokal ke internet.
   saat laptop Anda (192.168.1.11) ingin membuka Google, data akan dikirim dulu ke gateway (biasanya router), lalu router meneruskannya ke internet.
    
7. Menghubungkan antar jaringan yang berbeda.
   misalnya jaringan kantor dengan jaringan pabrik yang berbeda subnet.
    
8. Menerjemahkan alamat (NAT).
   gateway mengubah IP private (seperti 192.168.1.11) menjadi IP public saat keluar ke internet, dan sebaliknya.

   Pada jaringan rumahan, gateway biasanya adalah **router** dengan IP seperti `192.168.1.1`.


## Yang masih bingung


## Target Besok
- DNS & DHCP
