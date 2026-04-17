**tcpdump** adalah alat untuk menangkap lalu lintas data (paket) langsung dari baris perintah (terminal). Fungsinya adalah merekam dan menampilkan paket yang melewati suatu antarmuka jaringan. Alat ini biasanya digunakan untuk mencari masalah pada jaringan, menganalisis pola lalu lintas data, atau mendeteksi aktivitas yang tidak biasa seperti serangan atau kebocoran data. Perbedaan utama dengan Wireshark: tcpdump berjalan di terminal tanpa antarmuka grafis, sedangkan Wireshark memiliki tampilan GUI yang lebih interaktif.

## Output tcpdump

Contoh satu baris output tcpdump:

```
12:34:56.789012 IP 192.168.1.5.54321 > 8.8.8.8.53: UDP, length 32
```

| Bagian              | Artinya                   |
| ------------------- | ------------------------- |
| `12:34:56.789012`   | Timestamp packet          |
| `IP`                | Protokol layer 3          |
| `192.168.1.5.54321` | IP sumber : port sumber   |
| `>`                 | Arah packet               |
| `8.8.8.8.53`        | IP tujuan : port tujuan   |
| `UDP`               | Protokol transport        |
| `length 32`         | Ukuran payload dalam byte |


## Hasil Praktik

### Interface yang tersedia di laptop saya
```
┌──(kaii@debian)-[~]
└─$ sudo tcpdump -D
1.wlp1s0 [Up, Running, Wireless, Associated]
2.any (Pseudo-device that captures on all interfaces) [Up, Running]
3.lo [Up, Running, Loopback]
4.enp2s0 [Up, Disconnected]
5.docker0 [Up, Disconnected]
6.bluetooth0 (Bluetooth adapter number 0) [Wireless, Association status unknown]
7.bluetooth-monitor (Bluetooth Linux Monitor) [Wireless]
8.nflog (Linux netfilter log (NFLOG) interface) [none]
9.nfqueue (Linux netfilter queue (NFQUEUE) interface) [none]
10.dbus-system (D-Bus system bus) [none]
11.dbus-session (D-Bus session bus) [none]
```


### Capture DNS traffic
```
┌──(kaii@debian)-[~]
└─$ sudo tcpdump -i wlp1s0 -n port 53
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on wlp1s0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
17:07:51.062186 IP 192.168.1.12.43416 > 192.168.1.1.53: 12941+ PTR? 1.1.168.192.in-addr.arpa. (42)
17:07:51.064604 IP 192.168.1.1.53 > 192.168.1.12.43416: 12941* 1/0/0 PTR 192.168.1.1. (67)
17:07:56.078205 IP 192.168.1.12.55408 > 192.168.1.1.53: 5410+ PTR? 1.1.168.192.in-addr.arpa. (42)
17:07:56.080261 IP 192.168.1.1.53 > 192.168.1.12.55408: 5410* 1/0/0 PTR 192.168.1.1. (67)
17:07:59.418271 IP 192.168.1.12.43449 > 192.168.1.1.53: 14844+ HTTPS? chat.deepseek.com. (35)
17:07:59.418695 IP 192.168.1.12.50206 > 192.168.1.1.53: 10791+ A? chat.deepseek.com. (35)
17:07:59.421003 IP 192.168.1.12.59998 > 192.168.1.1.53: 16623+ A? chat.deepseek.com. (35)
17:07:59.434736 IP 192.168.1.1.53 > 192.168.1.12.43449: 14844 2/0/0 CNAME d3bbv8sr76az5s.cloudfront.net., HTTPS (100)
17:07:59.435245 IP 192.168.1.1.53 > 192.168.1.12.50206: 10791 2/0/0 CNAME d3bbv8sr76az5s.cloudfront.net., A 3.173.21.63 (94)
17:07:59.435376 IP 192.168.1.12.50206 > 192.168.1.1.53: 55359+ AAAA? chat.deepseek.com. (35)
17:07:59.436435 IP 192.168.1.1.53 > 192.168.1.12.59998: 16623 2/0/0 CNAME d3bbv8sr76az5s.cloudfront.net., A 3.173.21.63 (94)
17:07:59.470728 IP 192.168.1.1.53 > 192.168.1.12.50206: 55359 1/0/1 CNAME d3bbv8sr76az5s.cloudfront.net. (94)
17:07:59.475313 IP 192.168.1.12.50207 > 192.168.1.1.53: 42860+ A? d3bbv8sr76az5s.cloudfront.net. (47)
17:07:59.483806 IP 192.168.1.1.53 > 192.168.1.12.50207: 42860 1/0/0 A 3.173.21.63 (63)
17:08:00.630426 IP 192.168.1.12.60399 > 192.168.1.1.53: 32779+ HTTPS? gator.volces.com. (34)
17:08:00.630755 IP 192.168.1.12.50079 > 192.168.1.1.53: 16018+ A? gator.volces.com. (34)
17:08:00.630801 IP 192.168.1.12.50079 > 192.168.1.1.53: 48023+ AAAA? gator.volces.com. (34)
17:08:00.640165 IP 192.168.1.12.53296 > 192.168.1.1.53: 65259+ A? gator.volces.com. (34)
17:08:00.646878 IP 192.168.1.1.53 > 192.168.1.12.60399: 32779 2/0/0 CNAME gator.volces.com.bytedns1.com., CNAME gator.volces.com.230b2a2545cfa773.queniuck.com. (131)
17:08:00.648679 IP 192.168.1.1.53 > 192.168.1.12.50079: 48023 2/0/0 CNAME gator.volces.com.bytedns1.com., CNAME gator.volces.com.230b2a2545cfa773.queniuck.com. (131)
17:08:00.662488 IP 192.168.1.1.53 > 192.168.1.12.50079: 16018 15/0/0 CNAME gator.volces.com.bytedns1.com., CNAME gator.volces.com.230b2a2545cfa773.queniuck.com., A 43.109.37.228, A 163.181.100.195, A 43.109.37.227, A 43.109.37.232, A 43.109.37.234, A 163.181.158.197, A 43.109.30.176, A 43.109.37.229, A 43.109.37.233, A 43.109.42.187, A 43.109.37.230, A 163.181.18.180, A 43.109.37.231 (339)
17:08:00.662563 IP 192.168.1.1.53 > 192.168.1.12.53296: 65259 15/0/0 CNAME gator.volces.com.bytedns1.com., CNAME gator.volces.com.230b2a2545cfa773.queniuck.com., A 43.109.37.228, A 163.181.100.195, A 43.109.37.227, A 43.109.37.232, A 43.109.37.234, A 163.181.158.197, A 43.109.30.176, A 43.109.37.229, A 43.109.37.233, A 43.109.42.187, A 43.109.37.230, A 163.181.18.180, A 43.109.37.231 (339)
^C
22 packets captured
22 packets received by filter
0 packets dropped by kernel
```


**Yang menarik dari output:**

Ada jenis pertanyaan DNS yang jarang terlihat `HTTPS?`
Biasanya DNS hanya menanyakan alamat IP (A) atau alamat IPv6 (AAAA). Tapi di sini ada tipe `HTTPS` (nomor 65) yang merupakan teknologi baru. Fungsinya: memberi tahu browser atau aplikasi apakah situs tersebut mendukung HTTPS dan HTTP/3 langsung dari DNS. Ini menarik karena menunjukkan bahwa aplikasi (mungkin browser atau chat.deepseek) sudah menggunakan fitur DNS modern.
### Capture port 80
Saya akses: http://example.com
Packet yang muncul: 
```
┌──(kaii@debian)-[~]
└─$ sudo tcpdump -i wlp1s0 -n port 80
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on wlp1s0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
17:01:02.519666 IP 192.168.1.12.41756 > 34.107.221.82.80: Flags [.], ack 266699665, win 501, options [nop,nop,TS val 3294331337 ecr 2984913803], length 0
17:01:02.552379 IP 34.107.221.82.80 > 192.168.1.12.41756: Flags [.], ack 1, win 1050, options [nop,nop,TS val 2984924046 ecr 3294218711], length 0
17:01:05.366009 IP 192.168.1.12.41756 > 34.107.221.82.80: Flags [F.], seq 1, ack 1, win 501, options [nop,nop,TS val 3294334183 ecr 2984924046], length 0
17:01:05.392879 IP 34.107.221.82.80 > 192.168.1.12.41756: Flags [F.], seq 1, ack 2, win 1050, options [nop,nop,TS val 2984926895 ecr 3294334183], length 0
17:01:05.393001 IP 192.168.1.12.41756 > 34.107.221.82.80: Flags [.], ack 2, win 501, options [nop,nop,TS val 3294334210 ecr 2984926895], length 0
17:01:10.103771 IP 192.168.1.12.49434 > 104.20.23.154.80: Flags [S], seq 4066582163, win 64240, options [mss 1460,sackOK,TS val 2291184159 ecr 0,nop,wscale 7], length 0
17:01:10.129102 IP 104.20.23.154.80 > 192.168.1.12.49434: Flags [S.], seq 988540888, ack 4066582164, win 65535, options [mss 1400,sackOK,TS val 4143515858 ecr 2291184159,nop,wscale 13], length 0
17:01:10.129206 IP 192.168.1.12.49434 > 104.20.23.154.80: Flags [.], ack 1, win 502, options [nop,nop,TS val 2291184184 ecr 4143515858], length 0
17:01:10.129577 IP 192.168.1.12.49434 > 104.20.23.154.80: Flags [P.], seq 1:382, ack 1, win 502, options [nop,nop,TS val 2291184184 ecr 4143515858], length 381: HTTP: GET / HTTP/1.1
17:01:10.155718 IP 104.20.23.154.80 > 192.168.1.12.49434: Flags [.], ack 382, win 16, options [nop,nop,TS val 4143515885 ecr 2291184184], length 0
17:01:10.163301 IP 104.20.23.154.80 > 192.168.1.12.49434: Flags [P.], seq 1:260, ack 382, win 16, options [nop,nop,TS val 4143515892 ecr 2291184184], length 259: HTTP: HTTP/1.1 304 Not Modified
17:01:10.163488 IP 192.168.1.12.49434 > 104.20.23.154.80: Flags [.], ack 260, win 501, options [nop,nop,TS val 2291184218 ecr 4143515892], length 0
^C
12 packets captured
12 packets received by filter
0 packets dropped by kernel
```


### File capture
Disimpan di: ~/capture.pcap
Jumlah packet: 88 packet selama 15 detik

```
┌──(kaii@debian)-[~]
└─$ timeout 15 sudo tcpdump -i wlp1s0 -n -w ~/capture.pcap
tcpdump: listening on wlp1s0, link-type EN10MB (Ethernet), snapshot length 262144 bytes
88 packets captured
88 packets received by filter
0 packets dropped by kernel
```
