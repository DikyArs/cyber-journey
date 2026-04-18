# Hari 02 — [25-03-2026]

## Yang dipelajari hari ini

**OSI MODEL 7 Layer**
- **(7)Application layer**, Lapisan paling atas yang menyediakan interface bagi aplikasi untuk mengakses layanan jaringan.Lapisan ini _bukan_ a plikasi itu sendiri (bukan Chrome atau Outlook), tetapi protokol yang dipanggil oleh aplikasi tersebut.
- (6)Presentation Layer, sebagai penerjamah. translasi data(angka/huruf ke biner), kompresi, enkripsi/dekripsi.
- **(5)Sesion Layer**, Lapisan yang mengelola sesi komunikasi antara dua perangkat(memulai (establish), memelihara (maintain), dan mengakhiri (terminate) koneksi).Saat Anda download file besar (misal 5GB) dan koneksi putus di 60%, fitur resume yang membuat download lanjut dari 60% tanpa ulang dari 0% adalah fungsi session layer. 
- **(4)Transport Layer**, Melakukan segmentasi (memecah data menjadi potongan-potongan kecil), flow control (mengatur kecepatan kirim agar penerima tidak kewalahan), error control (deteksi dan retransmisi data yang hilang), dan port addressing (membedakan aplikasi mana yang menerima data). Unit data di lapisan ini disebut **segmen**.
- **(3)Network Layer**, pengalamatan logis dan routing. Menentukan jalur terbaik (path determination) agar data sampai ke tujuan yang mungkin berada di jaringan yang berbeda. Menggunakan alamat IP (Internet Protocol) untuk mengidentifikasi perangkat sumber dan tujuan. Unit data di lapisan ini disebut **packet**.
- **(2)Data Link**, Lapisan yang menyediakan transfer data yang andal antara dua node yang terhubung secara fisik dalam satu jaringan lokal (LAN).Bertanggung jawab atas physical addressing menggunakan **MAC Address**, deteksi kesalahan (error detection) dengan CRC, dan mengatur akses ke media transmisi. Unit data di lapisan ini disebut **frame**. Terbagi menjadi dua sub-lapisan: **MAC** (Media Access Control) dan **LLC** (Logical Link Control). **MAC Address** (alamat fisik yang melekat di perangkat keras). **Switch** adalah perangkat yang membaca alamat lokal ini dan mengirim data ke perangkat yang tepat dalam satu jaringan.
- **(1)Physical Layer**, Di dunia jaringan, ini adalah kabel, sinyal radio, dan konektor yang secara fisik membawa data.


## Praktik terminal

perintah yang dicoba : ip link show, ip addr show, ss -tulpn, ping
yang menarik : ss -tulpn, karena bisa lihat port yang terbuka secara langsung


## Yang belum jelas

memahami pada setiap bagian output terminal dari praktik di atas


## Target besok

TCP/IP Model & bedanya sama OSI

