 

### **Materi Dasar Subnetting
#### 1. Konsep Dasar**

- **IP Address**: Alamat perangkat di jaringan, terdiri dari 4 angka (0-255) yang dipisah titik (contoh: `192.168.1.11`).
    
- **Subnet Mask**: Pembatas yang memisahkan bagian **network** (alamat komplek) dan **host** (nomor rumah). Contoh: `255.255.255.0`.
    
- **Subnetting**: Memecah satu jaringan besar menjadi beberapa jaringan kecil (subnet) agar lebih efisien dan teratur.
    

#### **2. Komponen Penting dalam Satu Subnet**

- **Network ID**: Alamat pertama dalam subnet. Berfungsi sebagai identitas jaringan. **Tidak bisa** dipakai oleh host.
    
- **Host Range**: Rentang alamat yang **bisa dipakai** oleh perangkat (komputer, printer, dll).
    
- **Broadcast**: Alamat terakhir dalam subnet. Digunakan untuk mengirim pesan ke semua host. **Tidak bisa** dipakai oleh host.
    

**Rumus Sederhana:**

Jumlah Host yang Bisa Dipakai = Total IP dalam Subnet - 2

(Karena 1 alamat untuk Network ID dan 1 untuk Broadcast).

#### **3. Cara Penulisan Singkat (Prefix/CIDR)**

Daripada menulis subnet mask panjang, kita bisa menggunakan notasi garis miring (`/`). Ini adalah **cara singkat** yang wajib dihafal.

|Prefix|Subnet Mask|Total IP|Host yang Bisa Dipakai|
|---|---|---|---|
|**/24**|`255.255.255.0`|256|254|
|**/25**|`255.255.255.128`|128|126|
|**/26**|`255.255.255.192`|64|62|
|**/27**|`255.255.255.224`|32|30|
|**/28**|`255.255.255.240`|16|14|
|**/29**|`255.255.255.248`|8|6|
|**/30**|`255.255.255.252`|4|2|

**Pola**: Semakin besar angka prefix, semakin sedikit jumlah host (total IP-nya berkurang setengah setiap kenaikan 1 prefix dari `/24`).

#### **4. Menentukan Subnet (Metode Block Size)**

Block size adalah "lompatan" antar network ID. Rumusnya: **Block Size = 256 - Angka Terakhir Subnet Mask**.

Dari tabel di atas, block size-nya adalah:

- `/24` → Block 256
    
- `/25` → Block 128
    
- `/26` → Block 64
    
- `/27` → Block 32
    
- `/28` → Block 16
    
- `/29` → Block 8
    
- `/30` → Block 4
    

#### **5. Cara Praktis Menentukan Network ID dan Broadcast**

Misal: `192.168.1.0/26` (block size = 64)

1. **Network ID pertama** adalah alamat awal: `192.168.1.0`.
    
2. **Broadcast pertama** adalah `Network ID + Block Size - 1` = `0 + 64 - 1` = `63` → `192.168.1.63`.
    
3. **Network ID kedua** adalah `Broadcast pertama + 1` = `63 + 1` = `64` → `192.168.1.64`.
    
4. Dan seterusnya.
    

**Hasil Subnet untuk /26:**

- Subnet 1: `192.168.1.0` (Net) | `1 - 62` (Host) | `192.168.1.63` (Broadcast)
    
- Subnet 2: `192.168.1.64` (Net) | `65 - 126` (Host) | `192.168.1.127` (Broadcast)
    
- Subnet 3: `192.168.1.128` (Net) | `129 - 190` (Host) | `192.168.1.191` (Broadcast)
    
- Subnet 4: `192.168.1.192` (Net) | `193 - 254` (Host) | `192.168.1.255` (Broadcast)
    

#### **6. Cara Menentukan Letak Suatu IP**

Misal: `192.168.1.100/26` (block size = 64)

1. Cari kelipatan block size yang paling dekat **di bawah** angka oktet terakhir IP (100). Kelipatan 64: 0, 64, **128**.
    
2. Karena 100 berada di antara 64 dan 128, maka **Network ID-nya adalah `192.168.1.64`**.
    
3. Maka IP `192.168.1.100` berada di subnet `192.168.1.64/26` (dengan range host `65-126`).




**`curl ifconfig.me`** menampilkan **IP publik** perangkat Anda, yaitu alamat milik router yang terhubung ke ISP. IP ini sama untuk semua perangkat yang terhubung ke WiFi/router yang sama, berfungsi sebagai identitas di internet, dan dapat diakses dari seluruh dunia.

**`ip addr show`** menampilkan **IP privat** perangkat Anda, yaitu alamat unik yang diberikan oleh router kepada perangkat Anda secara individual. IP ini hanya berlaku di jaringan lokal (LAN) rumah/kantor, tidak bisa diakses dari internet, dan berfungsi untuk komunikasi internal antar perangkat se-WiFi seperti transfer file, casting ke TV, print ke printer, atau main game LAN.