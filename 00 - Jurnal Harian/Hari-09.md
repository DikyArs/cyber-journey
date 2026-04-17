# Hari 09 — [17-04-2026]

## Yang dipelajari
- tcpdump — packet capture di terminal
- Flag: -D, -i, -n, -w, -r
- Cara baca output tcpdump
- Bedanya tcpdump vs nmap

## Yang paling menarik hari ini

yang paling menarik adalah Menjalankan command:
```
   sudo tcpdump -i wlp1s0 -n port 80
```
lalu mengakses website http://example.com


## Quiz

1. Bedanya tcpdump dan nmap itu apa?
tcpdump itu untuk menangkap lalu lintas data sedangkan nmap untuk scan/memetakan/ memindai jaringan.

2. Flag apa yang dipakai untuk simpan capture ke file?
-w lalu di ikuti nama file 

3. Kenapa pakai flag -n di tcpdump?
agar lebih cepat dan jelas karena menampilkan ip addres bukan hostname.

4. Kalau mau capture hanya traffic DNS, command-nya gimana?
mencamtumkan port 53(DNS) :
```
sudo tcpdump -i wlp1s0 -n port 53
```

5. Format file hasil capture tcpdump itu apa ekstensinya?
.pcap

## Yang masih bingung
...

## Target besok
Wireshark — packet capture berbasis GUI