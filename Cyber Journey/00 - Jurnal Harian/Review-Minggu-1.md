
# Review Minggu 1 

## OSI Model
1. Sebutkan 7 layer dari bawah ke atas.
Physical, Data Link, Network, Transport, Session, Presentation, Application

2. Layer berapa TCP dan UDP bekerja?
Transport Layer

3. Layer berapa IP Address bekerja?
Network Layer

## TCP/IP
1. Apa bedanya TCP dan UDP?
TCP, pengiriman dijamin sampai.
UDP, pengiriman cepat tanpa konfirmasi.

2. Jelaskan 3-way handshake dengan kata-katamu sendiri
merupakan proses pembukaan koneksi TCP yaitu SYN --> SYN-ACK --> ACK. klien meminta koneksi ke server(ACK) lalu server menyetujui(SYN-ACK) dan klien mengonfirmasi(ACK).

3. Kapan UDP lebih cocok dari TCP?
cocok ketika tidak membutuhkan data utuh yang harus sampai atau yang tidak terlalu berdampak terhadap kehilangan beberapa paket data. seperti penggunaan streaming dan juga game online.


## IP & Subnetting
1. IP 192.168.1.0/24 — berapa jumlah host?
ada 254 host total dalam rentang 192.168.1.1 - 192.168.1.255.

2. Bedanya IP public dan IP private?
ip publik untuk berkomunikasi ke luar melalui jaringan internet sedangkan ip private hanya dapat untuk penggunaan dalam satu jaringan lokal yang sama.

3. IP laptopmu berapa? Kelas apa?
ip laptop saya saat menggunakan wifi rumah adalah 192.168.1.11/24 dan masuk ke kelas C.

## DNS & DHCP
1. Apa fungsi DNS?
sebagai penerjamah domain. yang awalnya dalam bentuk alamat ip diterjemahkan menjadi nama domain yang mudah dihafalkan sehingga tidak perlu menghafalkan angka ip yang rumit setiap mau berselancar di internet. 

2. Sebutkan 3 jenis DNS record
A (IPv4), AAAA (IPv6), CNAME(alias/penunjuk domain ke subdomain)

3. Kepanjangan DORA?
Discover, Offer, Request, Ack.

4. DNS mana yang lebih cepat di koneksimu — Google atau Cloudflare?
lebih cepat GoogleDNS (8.8.8.8) dengan kecepatan 28ms daripada Cloudflare (1.1.1.1) hanya 16ms.
