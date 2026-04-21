# TryHackMe — Progress Log

## Path: Pre-Security
Link: https://tryhackme.com/path/outline/presecurity


## Room 1 — Intro to Offensive Security

### Poin penting yang dipelajari

- Tujuan utama keamanan offensif adalah berpikir seperti attacker untuk menemukan dan memahami kelemahan sistem sebelum dieksploitasi oleh peretas sungguhan.
- Keamanan offensif berbeda dengan defensif: ofensif menyerang sistem secara legal untuk menguji ketahanan, bukan hanya memantau dan melindungi.
- Salah satu kelemahan umum yang dieksploitasi adalah hidden pages (halaman tersembunyi) yang ditinggalkan dapat diakses publik tanpa otentikasi.
- Alat seperti `dirb` digunakan untuk melakukan directory brute-forcing – mencari direktori atau halaman rahasia pada website.
- Setelah menemukan halaman tersembunyi (misalnya panel admin atau transfer bank), penyerang dapat mengeksploitasi fungsi yang tidak seharusnya bisa diakses (seperti menambah saldo atau mengubah data).
- Serangan ini menunjukkan pentingnya access control dan menghapus atau melindungi halaman pengembangan/admin yang tidak perlu.
- Ethical hacker harus mampu menemukan → mengakses → membuktikan celah keamanan secara terstruktur dan legal.


## Room 2 — Intro to Defensive Security

### Poin penting yang dipelajari

- Tujuan utama Defensive Security adalah mendeteksi dan merespons serangan, bukan menyerang sistem (berbeda dengan keamanan ofensif).
- Seorang SOC analyst harus mampu membedakan aktivitas normal vs mencurigakan dari dashboard monitoring.
- Langkah pertama investigasi: menemukan source IP yang mencurigakan → contoh: `32.122.195.63`
- Setelah IP ditemukan, identifikasi apa yang dicari attacker melalui daftar "URL Discovery Attempts" → contoh: `https://fakebank.com/admin`
- Prioritas utama saat serangan terkonfirmasi adalah containment yaitu menghentikan serangan yang sedang berlangsung.
- Tindakan containment sederhana: blokir IP attacker melalui firewall (pilih BLOCK, lalu Apply).
- Defender harus mampu mendeteksi → mengidentifikasi → menghentikan serangan secara cepat dan terstruktur.
