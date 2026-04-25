# Hari 13 — [25-04-2026]

## Room yang diselesaikan
- [x] What is Networking?
- [x] Intro to LAN

## Topologi jaringan
1. **Star (Bintang)**  
    Semua perangkat (komputer, printer, dll.) terhubung ke satu pusat, biasanya _switch_ atau _hub_. Keunggulannya: jika satu kabel rusak, hanya perangkat di ujung kabel itu yang bermasalah. Kekurangannya: jika pusatnya mati, seluruh jaringan mati.
    
2. **Bus**  
    Semua perangkat terhubung ke satu kabel utama (disebut backbone). Ujung kabel diberi _terminator_ untuk mencegah sinyal memantul. Keunggulan: sederhana dan hemat kabel. Kekurangan: jika kabel utama putus, seluruh jaringan lumpuh; sulit mendeteksi masalah.
    
3. **Ring (Cincin)**  
    Setiap perangkat terhubung ke dua perangkat lainnya membentuk lingkaran. Data berputar searah satu arah. Keunggulan: tidak perlu pusat, kinerja stabil saat padat. Kekurangan: jika satu perangkat atau kabel putus, seluruh jaringan terganggu (kecuali memakai ring ganda).

## ARP Protocol

ARP adalah protokol dalam jaringan komputer yang digunakan untuk mencari tahu alamat MAC  dari sebuah perangkat berdasarkan alamat IP yang diketahui. ARP diperlukan karena perangkat seperti switch dan kartu jaringan bekerja dengan alamat MAC, sedangkan kita (dan router) menggunakan alamat IP untuk berkomunikasi di jaringan lokal (LAN).

**Cara Kerja ARP:**

1. Komputer A ingin mengirim data ke Komputer B.
    
2. Mengecek tabel ARP (cache ARP).  
    
3. Mengirim permintaan ARP (ARP Request) secara broadcast.
    
4. Semua perangkat menerima, hanya yang IP-nya cocok yang membalas.  
    
5. Komputer A menyimpan hasilnya di cache ARP.
    
6. Data siap dikirim.


## Quiz

1. Bedanya Switch dan Router itu apa?

Switch bekerja di Layer 2 (Data Link). Fungsinya menghubungkan perangkat dalam satu jaringan lokal (LAN) berdasarkan alamat MAC. Switch tidak bisa menghubungkan jaringan yang berbeda.

Router bekerja di Layer 3 (Network). Fungsinya menghubungkan jaringan yang berbeda (misal LAN ke WAN atau ke internet) berdasarkan alamat IP. Router juga bisa melakukan NAT, routing, dan firewall.

2. Apa itu ARP dan kenapa dibutuhkan?

ARP (Address Resolution Protocol) adalah protokol untuk memetakan alamat IP ke alamat MAC dalam satu jaringan lokal.

Dibutuhkan karena perangkat di layer 2 (switch, NIC) hanya mengenali MAC address, sedangkan aplikasi dan protokol (seperti TCP/IP) menggunakan IP address. Tanpa ARP, perangkat tidak tahu MAC tujuan untuk mengirim frame.

3. Topologi mana yang paling umum dipakai di jaringan modern?

Topologi Star, karena mudah dikelola jika ada kabel putus maka hanya 1 perangkat saja yang terdampak.

4. Bedanya LAN dan WAN?

 LAN (Local Area Network): mencakup area terbatas (rumah, kantor, sekolah), kepemilikan sendiri, kecepatan tinggi (GbE), biaya rendah.

WAN (Wide Area Network): mencakup area geografis luas (kota, negara, benua), biasanya disewa dari ISP, kecepatan lebih rendah, latency lebih tinggi, biaya besar. Contoh: Internet.

5. Apa yang disimpan di ARP cache?

menyimpan tabel pasangan (IP address <--> MAC address) dari perangkat lain dalam satu subnet yang baru saja berkomunikasi.