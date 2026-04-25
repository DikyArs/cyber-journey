
**ARP = Address Resolution Protocol**

```
Laptop A mau kirim data ke IP 192.168.1.5
tapi butuh tau MAC address-nya dulu

Laptop A broadcast: "Siapa yang punya IP 192.168.1.5?"
     ↓
Semua device di jaringan dengar
     ↓
Laptop B (192.168.1.5) jawab: "Saya! MAC saya xx:xx:xx:xx"
     ↓
Laptop A simpan di ARP cache
     ↓
Data dikirim ke MAC address yang benar
```


## Ouput ARP & artinya


```
┌──(kaii@debian)-[~]
└─$ sudo arp -a
? (192.168.1.1) at b0:b1:94:37:7a:2e [ether] on wlp1s0
┌──(kaii@debian)-[~]
└─$ ip neigh show
192.168.1.1 dev wlp1s0 lladdr b0:b1:94:37:7a:2e REACHABLE 
```


- `arp -a` dan `ip neigh show` sama-sama menampilkan ARP cache (tabel mapping IP → MAC)
- `192.168.1.1` adalah alamat IP dari router/gateway.
- `b0:b1:94:37:7a:2e` adalah alamat MAC perangkat tersebut.
- `wlp1s0` adalah antarmuka Wi-Fi laptop saya yang terhubung ke jaringan.
- `REACHABLE` artinya entri ini masih valid dan baru saja dipakai komunikasi – sistem yakin alamat MAC itu masih benar karena sudah ada konfirmasi dalam beberapa detik/menit terakhir.
    

**Kesimpulan:** Perangkat tahu bagaimana cara mengirim frame ke router (192.168.1.1) dengan MAC tujuan tersebut, dan hubungannya sehat.