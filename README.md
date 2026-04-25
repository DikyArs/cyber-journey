# Cyber Journey 

Dokumentasi perjalanan belajar saya di bidang Cybersecurity & Networking.

## Progress
- [x] Hari 1 -- Setup environment
- [x] Hari 2 -- OSI Model
- [x] Hari 3 -- TCP/IP Model
- [x] Hari 4 -- IP Addres & Subnetting
- [x] Hari 5 -- DNS & DHCP
- [x] Hari 6 -- Review Minggu 1 & cheatsheet
- [x] Hari 7 -- Rest
- [x] Hari 8 -- Nmap & network scanning
- [x] Hari 9 -- tcpdump & packet capture
- [x] Hari 10 -- Wireshark & packet analysis
- [x] Hari 11 — Firewall & UFW
- [x] Hari 12 — TryHackMe Pre-Security path


## Tools yang Sudah Dipelajari

| Tools        | Kegunaan                             | Contoh command                |
| ------------ | ------------------------------------ | ----------------------------- |
| `ip addr`    | Lihat IP & network interface         | `ip addr show`                |
| `ip link`    | Lihat MAC address & status interface | `ip link show`                |
| `ip route`   | Lihat gateway & routing table        | `ip route show`               |
| `ping`       | Cek konektivitas ke host             | `ping -c 4 google.com`        |
| `traceroute` | Lihat jalur packet ke tujuan         | `traceroute google.com`       |
| `ss`         | Lihat port & koneksi aktif           | `ss -tulpn`                   |
| `nslookup`   | Query DNS sederhana                  | `nslookup google.com`         |
| `dig`        | Query DNS detail & record type       | `dig google.com MX`           |
| `curl`       | HTTP request dari terminal           | `curl ifconfig.me`            |
| `cat`        | Baca isi file konfigurasi            | `cat /etc/resolv.conf`        |
| `nmap`       | Scan jaringan & port                 | sudo nmap -A localhost        |
| `tcpdump`    | Capture & analisis packet jaringan   | sudo tcpdump -i wlan0 -n      |
| `wireshark`  | Analisis packet secara visual        | Filter : 'dns', 'http', 'tcp' |
| `ufw`        | Manage firewall rules                | sudo ufw allow 22             |

## Topik yang Sudah Dipelajari

- OSI Model 7 layer -- fungsi & protokol tiap layer
- TCP/IP Model & perbedaannya dengan OSI
- TCP 3-way handshake (SYN → SYN-ACK → ACK)
- Perbedaan TCP dan UDP
- IP Address -- kelas A, B, C, public vs private
- Subnet mask & CIDR notation
- DNS -- cara kerja, record types (A, AAAA, MX, CNAME, NS)
- DHCP -- proses DORA
- Nmap -- Scan Jaringan lokal & router
- tcpdump -- Menangkap lalu lintas data
- Wireshark -- Menangkap lalu lintas data(packet) berbasis GUI
- Firewall -- UFW dan Block & allow ssh

## TryHackMe Progress

**Path:** Pre-Security  
**Status:** 🔄 In Progress

| Room                        | Status |
| --------------------------- | ------ |
| Intro to Offensive Security | ✅      |
| Intro to Defensive Security | ✅      |
| What is Networking?         | ✅      |
| Intro to LAN                | ✅      |
