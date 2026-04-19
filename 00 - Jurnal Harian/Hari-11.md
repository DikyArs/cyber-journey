# Hari 11 — [19-04-2026]

## Yang dipelajari
- Konsep firewall — inbound & outbound
- UFW — cara setup, allow, deny, delete rule
- SSH server di laptop sendiri
- Simulasi block & allow port

## Hasil simulasi SSH
...

## Quiz

1. Apa fungsi firewall?

Memfilter lalu lintas jaringan berdasarkan aturan tertentu (port, protokol, IP, status koneksi) untuk melindungi sistem dari akses tidak sah dan serangan siber.

2. Bedanya inbound dan outbound traffic?

- **Inbound**: Data dari luar masuk ke sistem. Firewall mengontrol koneksi masuk (misal blokir serangan).
    
- **Outbound**: Data dari sistem keluar ke jaringan luar. Firewall mengontrol akses keluar (misal cegah kebocoran data).

3. Command UFW untuk blokir port 80?

`sudo ufw deny 80/tcp` atau `sudo ufw deny 80`. Diikuti `sudo ufw reload` jika UFW sudah aktif.

4. Kenapa port 22 penting untuk di-allow sebelum enable UFW?

Port 22 adalah port default SSH. Jika UFW diaktifkan tanpa mengizinkan port 22, semua koneksi masuk termasuk SSH akan diblokir, menyebabkan administrator kehilangan akses remote ke server (lockout). Maka harus `sudo ufw allow 22` terlebih dahulu.

5. Apa bedanya UFW dan iptables?

- **iptables**: Low-level, langsung mengelola aturan di kernel Linux (netfilter). Kompleks, membutuhkan sintaks detail.
    
- **UFW**: Frontend sederhana untuk iptables. Perintah seperti `ufw allow` diterjemahkan ke aturan iptables. Lebih mudah dan aman untuk penggunaan umum.


## Yang masih bingung
...

## Target besok
TryHackMe — mulai Pre-Security path