# Cheatsheet — Networking Dasar

## Lihat info jaringan
ip addr show          # lihat IP & interface
ip link show          # lihat MAC address
ip route show         # lihat gateway & routing table

## Cek konektivitas
ping -c 4 google.com          # ping 4x
traceroute google.com         # lihat jalur packet

## Port & koneksi
ss -tulpn             # semua port yang terbuka
ss -t                 # koneksi TCP aktif
ss -u                 # koneksi UDP aktif

## DNS
nslookup google.com           # query DNS biasa
dig google.com                # query DNS detail
dig google.com MX             # cek mail server
dig @8.8.8.8 google.com       # pakai Google DNS
dig @1.1.1.1 google.com       # pakai Cloudflare DNS
cat /etc/resolv.conf          # lihat DNS server aktif

## DHCP
cat /var/lib/dhcp/dhclient.leases   # lihat lease DHCP

## Scan jaringan
sudo nmap -sn 192.168.1.0/24  # scan semua device di jaringan

## Lain-lain
curl ifconfig.me              # lihat IP public