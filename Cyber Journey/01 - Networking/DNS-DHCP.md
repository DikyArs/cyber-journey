
# DNS (Domain Name System) — Panduan Ringkas

## Apa itu DNS?

DNS adalah sistem yang bertugas **menerjemahkan nama domain** (yang mudah diingat manusia) menjadi **alamat IP** (yang dipahami komputer).

### Analogi sederhana:
DNS seperti **buku telepon internet**. Anda cari nama "Google", DNS memberi nomor teleponnya (alamat IP).

### Proses singkat:
Ketik `google.com` → DNS cari alamat IP → browser terhubung ke IP tersebut → website muncul.

## Urutan Cara DNS Bekerja 

Ketika Anda mengetik `google.com` di browser, permintaan melewati tahapan ini:

Browser  
↓ (cek cache sendiri)  
Cache lokal (komputer/HP)  
↓ (kalau tidak ada)  
DNS Resolver (biasanya dari ISP atau layanan seperti 8.8.8.8)  
↓ (resolver tidak tahu, lanjut tanya)  
Root Server (menunjuk ke server TLD)  
↓ (diberi tahu server untuk .com)  
TLD Server (menunjuk ke authoritative server untuk [google.com](https://google.com))  
↓ (diberi tahu server resmi Google)  
Authoritative Server (memberi jawaban final: IP dari [google.com](https://google.com))  
↓  
Resolver mengembalikan IP ke browser  
↓  
Browser konek ke IP tersebut


> **Catatan:** Proses ini terjadi dalam hitungan milidetik dan biasanya sudah di-cache agar lebih cepat.

## Record DNS yang Wajib Kamu Tahu

| Record | Fungsi | Contoh |
|--------|--------|--------|
| **A** | Menerjemahkan domain ke **IPv4** | `google.com` → `142.250.185.46` |
| **AAAA** | Menerjemahkan domain ke **IPv6** | `google.com` → `2607:f8b0:4004::200e` |
| **MX** | Menentukan server penerima **email** untuk domain | `gmail.com` → `gmail-smtp-in.l.google.com` |
| **CNAME** | Membuat **alias** dari satu domain ke domain lain | `www.google.com` → `google.com` |
| **NS** | Menunjukkan **nameserver** yang berwenang untuk domain | Siapa yang "memegang" dan mengelola catatan DNS domain tersebut |

### Catatan Tambahan:
- **A** dan **AAAA** adalah catatan paling dasar — tanpa salah satunya, website tidak bisa diakses.
- **MX** wajib ada jika domain ingin menerima email.
- **CNAME** berguna untuk membuat subdomain seperti `www` mengarah ke domain utama.
- **NS** adalah "papan nama" yang menunjukkan di mana catatan lengkap suatu domain disimpan.

---

## Istilah Penting yang Sering Muncul

| Istilah | Arti Singkat |
|---------|---------------|
| **DNS Resolver** | Petugas yang mencari alamat IP untuk Anda (bisa dari ISP atau Google/Cloudflare) |
| **Root Server** | Server puncak yang tahu alamat semua server TLD (seperti `.com`, `.id`, `.org`) |
| **TLD Server** | Server untuk ekstensi domain tertentu (contoh: semua domain `.id` dikelola di sini) |
| **Authoritative Server** | Server resmi milik pemilik domain — sumber kebenaran terakhir |
| **Cache** | Memori sementara yang menyimpan hasil pencarian DNS agar cepat di lain waktu |

---

## Tips Cepat Hafal Record DNS

- **A** → **A**ngka (IPv4 pake angka-angka)
- **AAAA** → **A**ngka juga tapi lebih **A** **(A)** (IPv6 lebih panjang)
- **MX** → **M**ail e**X**change (email)
- **CNAME** → **C**anonical (alias) — seperti nama panggilan
- **NS** → **N**ame **S**erver — siapa bos yang megang domain

## Cara Cek Sendiri 

Di terminal/CMD:
Cek A record
```
nslookup google.com
```

Cek MX record
```
nslookup -type=MX gmail.com
```

Cek NS record
```
nslookup -type=NS google.com
```

Di Linux/Mac, lebih detail pakai dig
```
dig google.com A
dig google.com MX
dig google.com NS

```


# DHCP (Dynamic Host Configuration Protocol)

## Apa itu DHCP?

DHCP kepanjangan dari Dynamic Host Configuration Protocol.

Tugas DHCP: memberikan konfigurasi jaringan secara otomatis ke perangkat yang konek ke jaringan.

Tanpa DHCP, kita harus setting IP manual satu per satu ke setiap perangkat (laptop, HP, printer, dll).

---

## Kenapa DHCP dibutuhkan?

Kalau tanpa DHCP:
- Setiap perangkat harus punya IP unik dalam satu jaringan
- Kalau setting manual, rawan terjadi **duplikat IP** (tabrakan)
- Ribet kalau banyak perangkat (kantor, kafe, kampus)
- Kalau pindah jaringan (dari kantor ke rumah), harus ganti setting manual lagi

Dengan DHCP:
- Otomatis, praktis, tanpa konflik IP
- Setiap perangkat mendapat IP yang berbeda
- Bisa meminjamkan IP sementara, lalu dikembalikan saat tidak dipakai

---

## Cara Kerja DHCP (Proses DORA)

Proses DHCP disebut **DORA**. DORA itu singkatan dari:

- **D** = Discover
- **O** = Offer
- **R** = Request
- **A** = ACK

| Langkah | Nama     | Yang terjadi                                                                                 |
| ------- | -------- | -------------------------------------------------------------------------------------------- |
| 1       | DISCOVER | Laptop menyiarkan ke seluruh jaringan: "Ada DHCP server tidak?"                              |
| 2       | OFFER    | Server DHCP menjawab: "Ada! Saya tawarkan IP 192.168.1.10 untukmu"                           |
| 3       | REQUEST  | Laptop menjawab: "OK, saya setuju. Saya minta IP itu"                                        |
| 4       | ACK      | Server mengonfirmasi: "Baik, IP 192.168.1.10 sekarang resmi menjadi milikmu untuk sementara" |
Setelah langkah 4 (ACK), laptop sudah punya:

- Alamat IP
    
- Subnet mask
    
- Gateway (router)
    
- DNS server
    

Laptop sekarang bisa internetan.

## Contoh Kasus Nyata

**Kamu nyalakan laptop di rumah, lalu konek ke WiFi rumah.**

1. Laptop nyari server DHCP. Di rumah, yang bertindak sebagai server DHCP adalah **router WiFi**.
    
2. Router lihat IP 192.168.1.50 masih kosong, lalu tawarkan ke laptop.
    
3. Laptop setuju ambil IP 192.168.1.50.
    
4. Router catat: "IP 192.168.1.50 sedang dipakai laptop A, masa sewanya sampai jam 10 malam."
    
5. Laptop bisa internet dengan alamat IP itu.
    

**Kalau laptop mati sebelum jam 10 malam** → IP 192.168.1.50 kembali ke pool (kembali ke kumpulan IP yang tersedia), bisa dipakai perangkat lain.

--------------------------------------------------------------

## Praktik Terminal

### DNS Server saya

```
┌──(kaii@debian)-[~]
└─$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1

```
### nslookup google.com

```
┌──(kaii@debian)-[~]
└─$ nslookup google.com
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	google.com
Address: 172.253.118.138
Name:	google.com
Address: 172.253.118.100
Name:	google.com
Address: 172.253.118.102
Name:	google.com
Address: 172.253.118.139
Name:	google.com
Address: 172.253.118.113
Name:	google.com
Address: 172.253.118.101
Name:	google.com
Address: 2404:6800:4003:c01::8b
Name:	google.com
Address: 2404:6800:4003:c01::71
Name:	google.com
Address: 2404:6800:4003:c01::66
Name:	google.com
Address: 2404:6800:4003:c01::8a

```
### dig google.com

```
┌──(kaii@debian)-[~]
└─$ dig google.com

; <<>> DiG 9.20.21-1~deb13u1-Debian <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 42150
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		13	IN	A	142.251.12.100
google.com.		13	IN	A	142.251.12.138
google.com.		13	IN	A	142.251.12.139
google.com.		13	IN	A	142.251.12.113
google.com.		13	IN	A	142.251.12.101
google.com.		13	IN	A	142.251.12.102

;; Query time: 944 msec
;; SERVER: 192.168.1.1#53(192.168.1.1) (UDP)
;; WHEN: Sat Apr 11 06:07:00 WIB 2026
;; MSG SIZE  rcvd: 135

```
### Perbandingan DNS

```
┌──(kaii@debian)-[~]
└─$ dig @8.8.8.8 google.com | grep "Query time"
;; Query time: 28 msec
┌──(kaii@debian)-[~]
└─$ dig @1.1.1.1 google.com | grep "Query time"
;; Query time: 16 msec

```
lebih cepat 8.8.8.8(google DNS) dibandingkan dengan 1.1.1.1(Cloudflare) pada penggunaan di laptop saya






