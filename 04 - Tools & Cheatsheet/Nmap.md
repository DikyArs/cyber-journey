**Nmap** (kependekan dari _Network Mapper_) adalah alat yang berguna untuk memetakan jaringan komputer. Fungsinya antara lain:

- Melakukan pemindaian jaringan untuk mengetahui perangkat mana saja yang sedang aktif.
    
- Mengecek port-port mana yang terbuka di suatu perangkat.
    
- Mendeteksi sistem operasi dan layanan (service) yang berjalan di balik port tersebut.


### Port dan service nya yang harus dihafal

| Port  | Service | Keterangan            |
| ----- | ------- | --------------------- |
| 22    | SSH     | Remote Terminal       |
| 80    | HTTP    | Web tidak terenkripsi |
| 443   | HTTPS   | Web Terenkripsi       |
| 53    | DNS     | Domain resolution     |
| 67/68 | DHCP    | Pemberian IP otomatis |
| 21    | FTP     | Transfer File         |
| 25    | SMTP    | Kirim Email           |

### Contoh output nmap dan artinya

```
PORT     STATE    SERVICE   VERSION
22/tcp   open     ssh       OpenSSH 8.4
80/tcp   closed   http
443/tcp  filtered https
```

| Kolom          | Artinya                                      |
| -------------- | -------------------------------------------- |
| Port           | Nomer Port & Protokol                        |
| STATE open     | Port terbuka, ada service yang listen        |
| STATE closed   | Port tertutup, tidak ada service             |
| STATE filtered | Ada firewall yang memblokir                  |
| SERVICE        | Nama service yang biasanya jalan di port itu |
| VERSION        | Versi software (kalau pakai -sV)             |


## Hasil Praktik

### Scan jaringan lokal
Command: sudo nmap -sn 192.168.x.x/24
Device yang ditemukan: 3 device dan satu lagi adalah ip router saya
### Scan localhost
Port yang terbuka di laptop saya:
- Port 22 : service ssh
- Port 53 : service domain
- Port 631 : service ipp
- port 8081 : service blackice-icecap
### Scan -A localhost
OS yang terdeteksi: Linux (dengan kernel versi 2.6.32 atau 5.0–6.2)

Service yang berjalan:
- `ssh` (port 22)
    
- `domain` (DNS) (port 53)
    
- `ipp` (Internet Printing Protocol) (port 631)
    
- `blackice-icecap` (port 8081)


## Quiz Hari 8

1. Apa perbedaan nmap -sn dan nmap biasa?
nmap -sn untuk mendeteksi device yang hidup/ terhubung saat ini sedangkan nmap biasa hanya mendeteksi port apa saja yang sedang terbuka.

2. Apa artinya port state "filtered"?
artinya port terfilter ataupun terblokir oleh firewall

3. Flag apa yang dipakai untuk deteksi versi service?
menggunakan -sV untuk mendeteksi service yang dipakai tiap port.

4. Kenapa nmap butuh sudo?
nmap butuh sudo untuk menjalankan fitur advanced seperti deteksi os -O karena membutuhkan kemampuan membuat dan mengirim paket jaringan mentah.

5. Port berapa yang dipakai SSH? HTTP? HTTPS?
SSH(22), HTTP (80), HTTPS (443)