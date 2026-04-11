# Hari 03 — [29-03-2026]


## Yang dipelajari 

- TCP/IP Model vs OSI
- Perbedaan TCP dan UDP
- TCP 3-Way Handshake
- Tools: ss, traceroute


## Kendala hari ini


## QUIZ
1. Bedanya TCP dan UDP itu apa?
2. TCP/IP punya berapa layer? Sebutkan.
3. Apa itu 3-way handshake?
4. Kalau kamu streaming YouTube, pakai TCP atau UDP? Kenapa?
5. traceroute itu ngapain?

Jawab : 

1. TCP itu Connection-oriented(Harus Handshake) data terjamin sampai dan utuh tapi lebih lambat karena memang harus memastikan sampai dulu, contohnya akses web & kirim email. Sedangkan UDP itu Connectionless (Langsung kirim tanpa handshake) tidak terjamin dan data bisa hilang/acak tapi lebih cepat karena langsung kirim tanpa konfirmasi.contohnya Streaming & Game online
2. 4 layer
   Application Layer --> Tempat aplikasi berjalan(HTTP/S,FTP,SMTP,DNS)
   Transport Layer --> Mengatur dan menentukan koneksi (TCP,UDP)
   Internet Layer --> Pengalamatan IP dan Routing (IP, ICMP) 
   Network Access Layer --> hardware fisiknya (Ethernet, Wi-Fi)
3. merupakan Proses pembukaan koneksi TCP dalam 3 langkah :
   1.SYN, Klien minta koneksi ke server
   2.SYN-ACK, Server menyetujui dan membalas
   3.ACK, klien konfirmasi lalu koneksi siap
4. Menggunakan Quic yaitu yang berbasis UDP dengan fitur TCP 
   karena video harus utuh(TCP) dan menyesuaikan kualitas video dengan kecepatan internet
5. Melacak **jalur yang dilalui paket data** dari komputer ke server tujuan. untuk :
   - Menampilkan daftar router perantara (hop)
   - Mengukur waktu tempuh disetiap hop
   - Digunakan untuk mendiognisis di titik mana koneksi bermasalah




## Target besok

IP Address & Subnetting


