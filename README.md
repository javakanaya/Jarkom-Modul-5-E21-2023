# Jarkom-Modul-5-E21-2023

Laporan Resmi Praktikum Jaringan Komputer Modul 5

## Nama Anggota:

- [Yoel Mountanus Sitorus](https://github.com/zemetia) - 5025211078
- [Java Kanaya Prada](https://github.com/javakanaya) - 5025211112

## Topologi

## Pembagian Subnet

## *Network Configuration*
### Aura (Router)
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

# Subnet A4
auto eth1
iface eth1 inet static
address 10.47.0.5
netmask 255.255.255.252

# Subnet A3
auto eth2
iface eth2 inet static
address 10.47.0.1
netmask 255.255.255.252
```
### Heiter (Router)
```
auto lo
iface lo inet loopback

# Subnet A3
auto eth0
iface eth0 inet static
address 10.47.0.2
netmask 255.255.255.252
gateway 10.47.0.1

# Subnet A1
auto eth1
iface eth1 inet static
address 10.47.4.1
netmask 255.255.252.0

# Subnet A2
auto eth2
iface eth2 inet static
address 10.47.8.1
netmask 255.255.248.0
```
### Himmel (Router)
```
# ===Himmel===
auto lo
iface lo inet loopback

# Subnet A6
auto eth0
iface eth0 inet static
address 10.47.0.14
netmask 255.255.255.252
gateway 10.47.0.13

# Subnet A7
auto eth1
iface eth1 inet static
address 10.47.2.1
netmask 255.255.254.0

# Subnet A8
auto eth2
iface eth2 inet static
address 10.47.0.129
netmask 255.255.255.128
```

### Frieren (Router)
```
auto lo
iface lo inet loopback

# Subnet A4
auto eth0
iface eth0 inet static
address 10.47.0.6
netmask 255.255.255.252
gateway 10.47.0.5

# Subnet A6
auto eth1
iface eth1 inet static
address 10.47.0.13
netmask 255.255.255.252

# Subnet A5
auto eth2
iface eth2 inet static
address 10.47.0.9
netmask 255.255.255.252
```

### Fern (Router)
```
auto lo
iface lo inet loopback

# Subnet A8
auto eth0
iface eth0 inet static
address 10.47.0.130
netmask 255.255.255.128
gateway 10.47.0.129

# Subnet A9
auto eth1
iface eth1 inet static
address 10.47.0.17
netmask 255.255.255.252

# Subnet A10
auto eth2
iface eth2 inet static
address 10.47.0.21
netmask 255.255.255.252
```
### Revolte (DHCP Server)
```
# Subnet A10
auto eth0
iface eth0 inet static
address 10.47.0.22
netmask 255.255.255.252
gateway 10.47.0.21
```

### Richter (DNS Server)
```
# Subnet A9
auto eth0
iface eth0 inet static
address 10.47.0.18
netmask 255.255.255.252
gateway 10.47.0.17
```
### Sein (Web Server)
```
# Subnet A1
auto eth0
iface eth0 inet static
address 10.47.4.2
netmask 255.255.252.0
gateway 10.47.4.1
```

### Stark (Web Server)
```
# Subnet A5
auto eth0
iface eth0 inet static
address 10.47.0.10
netmask 255.255.255.252
gateway 10.47.0.9
```

### GrobeForest, LaubHills, SchwerMountain, TurkRegion (Client)
```
auto eth0
iface eth0 inet dhcp
```

## *Routing*
### Aura
```
# KANAN: A3, A2, A1
route add -net 10.47.4.0 netmask 255.255.252.0 gw 10.47.0.2
route add -net 10.47.8.0 netmask 255.255.248.0 gw 10.47.0.2
route add -net 10.47.0.0 netmask 255.255.255.252 gw 10.47.0.2

# BAWAH: A4, A5, A6, A7, A8, A9, A10
route add -net 10.47.0.4 netmask 255.255.255.252 gw 10.47.0.6
route add -net 10.47.0.8 netmask 255.255.255.252 gw 10.47.0.6
route add -net 10.47.0.12 netmask 255.255.255.252 gw 10.47.0.6
route add -net 10.47.2.0 netmask 255.255.254.0 gw 10.47.0.6
route add -net 10.47.0.128 netmask 255.255.255.128 gw 10.47.0.6
route add -net 10.47.0.16 netmask 255.255.255.252 gw 10.47.0.6
route add -net 10.47.0.20 netmask 255.255.255.252 gw 10.47.0.6
```

### Heiter
```
# ATAS: A2
route add -net 10.47.8.0 netmask 255.255.248.0 gw 10.47.8.1

# KANAN: A1
route add -net 10.47.4.0 netmask 255.255.252.0 gw 10.47.4.1
```

### Frieren
```
# KANAN: A5
route add -net 10.47.0.8 netmask 255.255.255.252 gw 10.47.0.9

# KIRI: A6, A7, A8, A9, A10
route add -net 10.47.0.12 netmask 255.255.255.252 gw 10.47.0.14
route add -net 10.47.2.0 netmask 255.255.254.0 gw 10.47.0.14
route add -net 10.47.0.128 netmask 255.255.255.128 gw 10.47.0.14
route add -net 10.47.0.16 netmask 255.255.255.252 gw 10.47.0.14
route add -net 10.47.0.20 netmask 255.255.255.252 gw 10.47.0.14
```

### Himmel
```
# ATAS: A7
route add -net 10.47.2.0 netmask 255.255.254.0 gw 10.47.2.1

# BAWAH: A8, A9, A10
route add -net 10.47.0.128 netmask 255.255.255.128 gw 10.47.0.129
route add -net 10.47.0.16 netmask 255.255.255.252 gw 10.47.0.130
route add -net 10.47.0.20 netmask 255.255.255.252 gw 10.47.0.130
```

### Fern
```
# ATAS: A9
route add -net 10.47.0.16 netmask 255.255.255.252 gw 10.47.0.17

# KIRI: A10
route add -net 10.47.0.20 netmask 255.255.255.252 gw 10.47.0.21
```

### DHCP Server (Revolte)
```sh
echo nameserver 192.168.122.1 > /etc/resolv.conf

apt-get update -y
apt-get install isc-dhcp-server -y

echo "
INTERFACESv4=\"eth0\"
#INTERFACESv6=\"\"
" > /etc/default/isc-dhcp-server

yes | echo "

subnet 10.47.0.20 netmask 255.255.255.252 {} 

subnet 10.47.0.128 netmask 255.255.255.128 {
	range 10.47.0.131 10.47.0.254;
	option routers 10.47.0.129;
	option broadcast-address 10.47.0.255;
	option domain-name-servers 10.47.0.18;
}

subnet 10.47.2.0 netmask 255.255.254.0 {
	range 10.47.2.2 10.47.3.254;
	option routers 10.47.2.1;
	option broadcast-address 10.47.3.255;
	option domain-name-servers 10.47.0.18;
}

subnet 10.47.8.0 netmask 255.255.248.0 {
	range 10.47.8.2 10.47.15.254;
	option routers 10.47.8.1;
	option broadcast-address 10.47.15.255;
	option domain-name-servers 10.47.0.18;
}

subnet 10.47.4.0 netmask 255.255.252.0 {
	range 10.47.4.3 10.47.7.254;
	option routers 10.47.4.1;
	option broadcast-address 10.47.7.255;
	option domain-name-servers 10.47.0.18;
}

" > /etc/dhcp/dhcpd.conf

rm /var/run/dhcpd.pid

service isc-dhcp-server restart
```

### DHCP Relay (Fern, Himmel, Frieren, Heiter)
```sh
echo nameserver 192.168.122.1 > /etc/resolv.conf

apt update -y
apt-get install isc-dhcp-relay -y

echo '
SERVERS="10.47.0.22"
INTERFACES="eth0 eth1 eth2"
OPTIONS=""
' > /etc/default/isc-dhcp-relay

echo '
net.ipv4.ip_forward=1
' > /etc/sysctl.conf

service isc-dhcp-relay restart
```

### DHCP Relay (Aura)
```sh
echo nameserver 192.168.122.1 > /etc/resolv.conf

apt update -y
apt-get install isc-dhcp-relay -y

echo '
SERVERS="10.47.0.22"
INTERFACES="eth1 eth2"
OPTIONS=""
' > /etc/default/isc-dhcp-relay

echo '
net.ipv4.ip_forward=1
' > /etc/sysctl.conf

service isc-dhcp-relay restart
```

### Web Server (Sein)
```sh
echo nameserver 192.168.122.1 > /etc/resolv.conf

apt-get update -y
apt-get install apache2 -y

echo '
This is from SEIN
' > /var/www/html/index.html

echo '
Listen 80 
Listen 443 

<IfModule ssl_module> 
Listen 443 
</IfModule> 
<IfModule mod_gnutls.c> 
Listen 443 
</IfModule>
' > /etc/apache2/ports.conf

service apache2 restart
```

### Web Server (Stark)
```sh
echo nameserver 192.168.122.1 > /etc/resolv.conf

apt-get update -y
apt-get install apache2 -y

echo '
This is from STARK
' > /var/www/html/index.html

echo '
Listen 80 
Listen 443 

<IfModule ssl_module> 
Listen 443 
</IfModule> 
<IfModule mod_gnutls.c> 
Listen 443 
</IfModule>
' > /etc/apache2/ports.conf

service apache2 restart
```

## Soal-Soal:
### Soal 1
> Agar topologi yang kalian buat dapat mengakses keluar, kalian diminta untuk mengkonfigurasi Aura menggunakan iptables, tetapi tidak ingin menggunakan MASQUERADE.
```
IPETH0="$(ip -br a | grep eth0 | awk '{print $NF}' | cut -d'/' -f1)"
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source "$IPETH0" -s 10.47.0.0/20
```
### Soal 2
> Kalian diminta untuk melakukan drop semua TCP dan UDP kecuali port 8080 pada TCP.
```
# Drop semua TCP kecuali pada port 8080
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
iptables -A INPUT -p tcp -j DROP

# Drop semua UDP 
iptables -A INPUT -p udp -j DROP
```
### Soal 3
> Kepala Suku North Area meminta kalian untuk membatasi DHCP dan DNS Server hanya dapat dilakukan ping oleh maksimal 3 device secara bersamaan, selebihnya akan di drop.
```
iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j REJECT
```
### Soal 4
> Lakukan pembatasan sehingga koneksi SSH pada Web Server hanya dapat dilakukan oleh masyarakat yang berada pada GrobeForest.
```
iptables -A INPUT -p tcp --dport 22 -s 10.47.4.0/22 -j ACCEPT

iptables -A INPUT -p tcp --dport 22 -j REJECT
```
### Soal 5
> Selain itu, akses menuju WebServer hanya diperbolehkan saat jam kerja yaitu Senin-Jumat pada pukul 08.00-16.00.
```
iptables -A INPUT -m time --timestart 08:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT
```
### Soal 6
> Lalu, karena ternyata terdapat beberapa waktu di mana network administrator dari WebServer tidak bisa stand by, sehingga perlu ditambahkan rule bahwa akses pada hari Senin - Kamis pada jam 12.00 - 13.00 dilarang (istirahat maksi cuy) dan akses di hari Jumat pada jam 11.00 - 13.00 juga dilarang (maklum, Jumatan rek).
```
iptables -A INPUT -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j REJECT 

iptables -A INPUT -m time --timestart 12:00 --timestop 13:00 --weekdays Mon,Tue,Wed,Thu -j REJECT 
```
### Soal 7
> Karena terdapat 2 WebServer, kalian diminta agar setiap client yang mengakses Sein dengan Port 80 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan dan request dari client yang mengakses Stark dengan port 443 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan.
### Soal 8
> Karena berbeda koalisi politik, maka subnet dengan masyarakat yang berada pada Revolte dilarang keras mengakses WebServer hingga masa pencoblosan pemilu kepala suku 2024 berakhir. Masa pemilu (hingga pemungutan dan penghitungan suara selesai) kepala suku bersamaan dengan masa pemilu Presiden dan Wakil Presiden Indonesia 2024.
```
iptables -A INPUT -p tcp --dport 80 -s 10.47.0.20/30 -m time --datestart 2023-12-11 --datestop 2024-02-15 -j DROP
```
### Soal 9
> Sadar akan adanya potensial saling serang antar kubu politik, maka WebServer harus dapat secara otomatis memblokir  alamat IP yang melakukan scanning port dalam jumlah banyak (maksimal 20 scan port) di dalam selang waktu 10 menit. (clue: test dengan nmap)
### Soal 10
> Karena kepala suku ingin tau paket apa saja yang di-drop, maka di setiap node server dan router ditambahkan logging paket yang di-drop dengan standard syslog level. 

