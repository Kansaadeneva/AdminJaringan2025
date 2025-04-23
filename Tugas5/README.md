Tentu! Aku bantu rapikan, benarkan, dan tambahi kodenya. Ini formatnya cocok untuk dimasukkan ke laporan di GitHub:

---

## Jaringan DNS dan Gateway Virtual Machine (VM)

### Deskripsi Singkat
Dalam konfigurasi ini, **VM 1** bertugas sebagai **gateway** sekaligus **DNS server** yang akan menangani koneksi internet untuk **VM 2** serta mengarahkan nama domain `www.kelompok3.com`. Sementara **VM 2** berperan sebagai **client** jaringan tersebut.

---

##  VM 1 - Gateway & DNS Server

### 1. Install Requirements
Instal paket yang dibutuhkan:

```bash
sudo apt update
sudo apt install bind9 iptables-persistent -y
```

### 2. Konfigurasi IP Forwarding

Aktifkan IP forwarding agar VM 1 bisa meneruskan koneksi internet ke VM 2:

```bash
sudo nano /etc/sysctl.conf
```

Cari dan ubah baris:
```bash
#net.ipv4.ip_forward=1
```
Menjadi:
```bash
net.ipv4.ip_forward=1
```

Lalu aktifkan perubahan:
```bash
sudo sysctl -p
```

### 3. Konfigurasi iptables NAT

Asumsikan interface internet adalah `eth0` dan interface ke VM 2 adalah `eth1`. Ubah sesuai kondisi kalian.

```bash
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
sudo iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
sudo iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT
```

Simpan konfigurasi iptables agar persist setelah reboot:

```bash
sudo netfilter-persistent save
```

### 4. Konfigurasi DNS Server (BIND9)

Edit file konfigurasi domain:

```bash
sudo nano /etc/bind/named.conf.local
```

Tambahkan:

```bash
zone "kelompok3.com" {
    type master;
    file "/etc/bind/db.kelompok3";
};
```

Salin file zona dari template:

```bash
sudo cp /etc/bind/db.local /etc/bind/db.kelompok3
```

Edit file zona:

```bash
sudo nano /etc/bind/db.kelompok3
```

Ubah isinya menjadi seperti berikut:

```
$TTL    604800
@       IN      SOA     kelompok3.com. root.kelompok3.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL

; Name servers
@       IN      NS      kelompok3.com.

; A records
@       IN      A       192.168.100.1    ; IP VM 1
www     IN      A       192.168.100.2    ; IP VM 2 (atau host webnya)
```

Restart BIND9:

```bash
sudo systemctl restart bind9
```

---

##  VM 2 - Client

### 1. Atur IP dan DNS

Edit `/etc/network/interfaces` atau gunakan `nmtui` untuk set IP statis:

```
auto eth0
iface eth0 inet static
    address 192.168.100.2
    netmask 255.255.255.0
    gateway 192.168.100.1
    dns-nameservers 192.168.100.1
```

### 2. Uji Koneksi

Cek koneksi ke internet dan DNS:

```bash
ping google.com
ping www.kelompok3.com
```

