## 3 Panel Utama Wireshark

1. **Packet List** (Daftar Semua Packet)  
    Panel ini menampilkan seluruh paket yang tertangkap dalam sesi tertentu. Setiap baris mewakili satu paket, lengkap dengan nomor urut, waktu, alamat asal dan tujuan, protokol, serta informasi ringkas. Berguna untuk melihat alur komunikasi secara garis besar.
    
2. **Packet Details** (Isi Paket)  
    Saat satu paket dipilih di panel atas, detail strukturnya akan muncul di sini. Wireshark akan memecah paket menjadi lapisan-lapisan (Frame, Ethernet, IP, TCP/UDP, hingga payload). Kita bisa membuka lipatan tiap lapisan untuk melihat field-field spesifik seperti alamat MAC, TTL, port, flags, sequence number, dll.
    
3. **Packet Bytes** (Data Mentah/Hex)  
    Panel paling bawah menampilkan data paket dalam bentuk _hex dump_ (kiri) dan representasi ASCII (kanan). Ini adalah bentuk paling mentah dari paket yang sesungguhnya dikirim di jaringan. Berguna untuk menganalisis data non-standar, mencari _signature_ malware, atau memeriksa _payload_ mentah.
    



|   Warna    |                                               Artinya                                                |
| :--------: | :--------------------------------------------------------------------------------------------------: |
| Hijau muda |                      TCP traffic -- koneksi berbasis TCP (HTTP, SSH, SMTP, dll)                      |
| Biru muda  |                 UDP / DNS traffic -- paket UDP umumnya, termasuk query/response DNS                  |
|   Hitam    | Error / packet bermasalah misalnya TCP retransmission, dup ACK, checksum error, atau paket malformed |
|    Ungu    |                   ICMP (ping) -- paket ping request/reply atau error ICMP lainnya                    |

## Filter di Wireshark

**Filter berdasarkan protokol:**
dns
http
tcp
udp
icmp

**Filter berdasarkan IP:**
ip.addr == 8.8.8.8
ip.src == 192.168.1.5
ip.dst == 8.8.8.8

**Filter berdasarkan port:**
tcp.port == 80
udp.port == 53

**Filter gabungan:**
ip.addr == 8.8.8.8 && udp.port == 53
tcp && ip.src == 192.168.1.5


## TCP Stream

1. Cari packet HTTP di list (filter: `http`)
2. Klik kanan salah satu packet
3. Pilih **Follow → TCP Stream**
4. Wireshark akan tampilkan seluruh percakapan dalam satu window

```
GET / HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:140.0) Gecko/20100101 Firefox/140.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Upgrade-Insecure-Requests: 1
If-Modified-Since: Sat, 18 Apr 2026 00:49:31 GMT
Priority: u=0, i


HTTP/1.1 304 Not Modified
Date: Sat, 18 Apr 2026 04:44:41 GMT
Connection: keep-alive
Allow: GET, HEAD
Age: 1075
Server: cloudflare
Last-Modified: Sat, 18 Apr 2026 00:49:31 GMT
ETag: "69e2d51b-210"
cf-cache-status: HIT
CF-RAY: 9ee104047c2e98b3-SIN


GET / HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:140.0) Gecko/20100101 Firefox/140.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: keep-alive
Upgrade-Insecure-Requests: 1
If-Modified-Since: Sat, 18 Apr 2026 00:49:31 GMT
Priority: u=0, i


HTTP/1.1 304 Not Modified
Date: Sat, 18 Apr 2026 04:44:47 GMT
Connection: keep-alive
Allow: GET, HEAD
Age: 1081
Server: cloudflare
Last-Modified: Sat, 18 Apr 2026 00:49:31 GMT
ETag: "69e2d51b-210"
cf-cache-status: HIT
CF-RAY: 9ee1042df85d98b3-SIN
```

Percakapan 1: pada paragraf satu adalah client request lalu paragraf ke dua server memberikan respon.

Percakapan 2: pada paragraf ketiga adalah client request lalu paragraf ke empat server memberikan respon.


## Hasil Praktik

### File yang dibuka
Nama file: capture.pcap
Jumlah packet: 123

### Filter yang dicoba
- dns → 24 packet ditemukan
- http → 4 packet ditemukan
- icmp → 0 packet ditemukan

### TCP Stream
Yang saya lihat: Ada komunikasi antara client (GET) lalu server http memberikan respon

### Yang menarik dari capture ini
- bisa melihat percakapan lengkap dalam satu windows melalui tcp stream