
| TCP/IP Layer      | Setara OSI Layer | Protokol            |
| ----------------- | ---------------- | ------------------- |
| Application Layer | Layer 5,6,7      | HTTP, DNS, FTP, SSH |
| Transport Layer   | Layer 4          | TCP, UDP            |
| Internet Layer    | Layer 3          | IP, ICMP            |
| Network Layer     | Layer 2,1        | Ethernet, Wi-Fi     |
- **TCP** = pengiriman yang dijamin sampai, ada konfirmasi (browsing, email, transfer file) 
- **UDP** = pengiriman cepat tanpa konfirmasi (streaming video, gaming online, video call)


**Praktik Terminal**

 **traceroute google.com**

output : 
traceroute to google.com (142.251.12.100), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1.572 ms  1.511 ms  2.078 ms
 2  10.1.32.1 (10.1.32.1)  5.970 ms  5.953 ms  5.871 ms
 3  * 172.22.85.1 (172.22.85.1)  5.808 ms  5.724 ms
 4  10.13.135.1 (10.13.135.1)  16.559 ms  15.751 ms  15.714 ms
 5  10.135.13.25 (10.135.13.25)  18.824 ms  19.439 ms  19.568 ms
 6  10.135.13.130 (10.135.13.130)  18.467 ms  15.408 ms  16.139 ms
 7  10.10.244.33 (10.10.244.33)  14.717 ms  15.693 ms  15.430 ms
 8  * * *
 9  142.250.160.196 (142.250.160.196)  26.806 ms  27.061 ms  28.704 ms
10  * * *
11  142.251.54.254 (142.251.54.254)  28.384 ms 72.14.232.100 (72.14.232.100)  27.402 ms 142.251.241.0 (142.251.241.0)  26.512 ms
12  172.253.66.204 (172.253.66.204)  27.479 ms 142.251.192.8 (142.251.192.8)  29.693 ms 72.14.233.134 (72.14.233.134)  26.456 ms
13  216.239.57.50 (216.239.57.50)  27.228 ms 142.251.230.227 (142.251.230.227)  26.916 ms 142.251.230.137 (142.251.230.137)  29.777 ms
14  142.251.231.186 (142.251.231.186)  28.670 ms 192.178.46.238 (192.178.46.238)  26.509 ms 216.239.41.221 (216.239.41.221)  28.201 ms
15  142.251.52.147 (142.251.52.147)  26.235 ms 142.251.52.227 (142.251.52.227)  27.168 ms 142.251.52.193 (142.251.52.193)  28.829 ms
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * se-in-f100.1e100.net (142.251.12.100)  26.819 ms  27.007 ms


artinya :
 - **Hop 1**: 192.168.1.1 Ini merupakan router atau modem WiFi lokal. Waktu respons sangat cepat (sekitar 1.5–2 ms), yang merupakan hal normal.
- **Hop 2 hingga 7**: IP-IP private seperti 10.1.32.1, 172.22.85.1, 10.13.135.1, dan sejenisnya. IP-IP ini termasuk peralatan internal ISP. Penggunaan IP private di bagian ini sangat umum dan normal, menandakan bahwa paket masih berada di dalam jaringan ISP sebelum keluar ke internet umum.
- **Hop 8, 10, dan 16 hingga 24**: Banyak tanda *** (asterisk). Tanda ini berarti router tersebut tidak memberikan respons terhadap permintaan traceroute. Hal ini biasa terjadi karena router dikonfigurasi untuk tidak merespons ICMP demi alasan keamanan, atau firewall memblokir. Keadaan ini tidak menandakan adanya masalah, paket tetap dapat melewati router tersebut.
- **Hop 9, 11 hingga 15**: Mulai muncul IP milik Google (142.250.x.x, 142.251.x.x, 72.14.x.x, 216.239.x.x, dll.). Bagian ini menunjukkan bahwa paket telah memasuki jaringan backbone Google.
- **Hop 25**: se-in-f100.1e100.net (142.251.12.100) Ini adalah server Google yang berhasil dicapai. Domain 1e100.net merupakan domain khusus milik Google.

kesimpulan : Koneksi menuju Google berjalan normal dan berhasil mencapai tujuan di hop ke-25. Latency secara keseluruhan berada di kisaran 26–29 ms pada hop akhir, yang termasuk baik untuk koneksi dari Indonesia ke server Google.

Banyak tanda *** di tengah jalur merupakan hal yang sangat biasa terjadi pada traceroute modern, terutama pada ISP besar dan jaringan Google.

IP private di awal hanya menunjukkan perjalanan paket di dalam jaringan ISP.

Traceroute ini tidak menunjukkan adanya masalah besar di jalur koneksi. Jika terdapat keluhan lambat atau putus-putus, penyebabnya kemungkinan berada di bagian lain, seperti WiFi, bandwidth ISP, atau perangkat itu sendiri.