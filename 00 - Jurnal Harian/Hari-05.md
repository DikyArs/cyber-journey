# Hari 05 — [10-04-2026]

## Yang dipelajari
- Cara kerja DNS & record types
- Proses DORA di DHCP
- Tools: nslookup, dig, dhclient

## Penemuan menarik
- DNS server yang saya pakai: 192.168.1.1
- DNS tercepat di koneksi saya: 8.8.8.8


## Hasil Quiz
1. Apa fungsi DNS? Jelaskan dengan analogi kamu sendiri. 
DNS merupakan penerjemah dari domain seperti google.com menjadi sebuah alamat ip. untuk memudahkan supaya saat ingin mengunjungi suatu domain tidak perlu harus menghafalkan alamat ip nya.

2. Apa bedanya DNS record A dan CNAME? 
record A adalah alamat asli dari website sebagai fondasi utamanya website ini wajib harus ada.
CNAME adalah alias dari website untuk menunjuk dari subdomain ke domain utama ketika ada perubahan ip ataupun nama domain.


3. Apa itu DHCP lease? 
DHCP Lease adalah jangka waktu peminjaman alamat IP yang diberikan oleh Server DHCP. 

4. Kepanjangan DORA dalam proses DHCP? 
Discover, Offer, Request, Ack.

5. Kenapa IP dari DHCP bisa berubah-ubah tiap konek?
seperti pada soal ke 3 ada yang namanya DHCP Lease yaitu meminjamkan ip dari dhcp server secara sementara dengan jangka waktu tertentu ini bersifat dinamis. Bisa dibuat secara manual statis tapi ribet dan rawan bentrok jika ada kesamaan ip saat proses DORA.

## Yang masih bingung
- Record DNS

## Target besok
Review Minggu 1 + push GitHub pertama