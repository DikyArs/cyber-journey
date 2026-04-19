### Firewall sebagai Pengatur Lalu Lintas JaringaN

Tugas utama Firewall adalah memeriksa setiap paket data yang masuk maupun keluar, kemudian memutuskan apakah paket tersebut diizinkan atau ditolak berdasarkan aturan yang telah ditetapkan.

Firewall bekerja dalam dua arah lalu lintas:

1. **Inbound (Lalu Lintas Masuk)**  
   Yakni data yang datang dari internet menuju perangkat Anda. Contohnya saat Anda mengakses sebuah situs web, server akan mengirimkan konten balasan. Firewall akan memeriksa apakah data tersebut merupakan respons yang sah terhadap permintaan Anda, atau justru upaya akses mencurigakan yang tidak diundang.

2. **Outbound (Lalu Lintas Keluar)**  
   Yaitu data yang dikirim dari perangkat Anda ke internet. Contohnya ketika Anda mengetik alamat web lalu menekan Enter. Firewall juga mengawasi arus keluar ini untuk mencegah aplikasi jahat yang secara diam-diam mengirimkan data pribadi Anda ke pihak tidak bertanggung jawab.


**UFW: Antarmuka Sederhana untuk Firewall di Linux**

Pada sistem operasi Linux (khususnya distribusi seperti Ubuntu atau Debian), komponen firewall bawaan yang sebenarnya bernama **iptables**. Iptables sangat kuat dan fleksibel, namun konfigurasinya tergolong rumit karena memerlukan perintah panjang serta pemahaman teknis yang mendalam.

**UFW** (*Uncomplicated Firewall*) hadir sebagai lapisan antarmuka yang menyederhanakan pengelolaan iptables. Sesuai namanya, UFW dirancang agar tidak rumit. Dengan UFW, Anda cukup menggunakan perintah singkat seperti `ufw allow 80` (mengizinkan lalu lintas web) atau `ufw enable` (menyalakan firewall), tanpa harus menulis aturan iptables secara manual di belakang layar. Meskipun lebih sederhana, UFW tetap menjalankan fungsi firewall yang sama: mengatur dan mengamankan lalu lintas jaringan.

**Kesimpulan:** Firewall adalah sistem keamanan yang mengatur lalu lintas masuk dan keluar. UFW adalah alat bantu yang memudahkan pengguna Linux untuk mengelola firewall tersebut tanpa perlu mempelajari kerumitan iptables secara langsung.


## Cheatsheet UFW

sudo ufw status verbose         # cek status detail
sudo ufw enable / disable       # aktif / nonaktif
sudo ufw allow [port/service]   # izinkan
sudo ufw deny [port/service]    # blokir
sudo ufw delete [nomor]         # hapus rule
sudo ufw reset                  # reset semua
sudo ufw logging on             # aktifkan log

## Hasil Praktik
GAGAL dikarenakan Secara default, UFW tidak memfilter lalu lintas pada antarmuka loopback (`lo`).  
Antarmuka `lo` (localhost/127.0.0.1) dianggap sebagai jalur "trusted" yang tidak disentuh oleh aturan UFW, demi menjaga stabilitas layanan internal sistem.


### Status UFW sebelum dikonfigurasi
...

### Rules yang saya buat
- Allow: sudo ufw  allow 22
- Deny: sudo ufw deny 22

### Simulasi SSH block & allow
Hasil saat di-deny: tetap masih bisa masuk(berhasil)
Hasil saat di-allow: masuk dan berhasil

### Yang menarik hari ini
yang menarik saat praktek percobaan ternyata tidak dapat memutus ssh localhost yang dikarenakan UFW tidak dapat memfilter lalu lintas pada antarmuka loopback(dianggep trusted).