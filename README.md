# Jarkom-Modul-5-E21-2023

Laporan Resmi Praktikum Jaringan Komputer Modul 5

## Nama Anggota:

- [Yoel Mountanus Sitorus](https://github.com/zemetia) - 5025211078
- [Java Kanaya Prada](https://github.com/javakanaya) - 5025211112

## Topologi
<img width="627" alt="Jarkom Modul 5 Topologi" src="https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/87474722/5a6e69c7-523c-4452-a91b-e831b22cad6c">

## Pembagian Subnet
<img width="753" alt="Pembagian Subnetting " src="https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/87474722/e9642608-3cf0-4a60-91ff-798c967779c4">

<img width="1474" alt="Table Sbnet" src="https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/87474722/cdfeb637-7f74-4c16-824c-a79f1ed32f63">

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
**Penjelasan**:

```IPETH0="$(ip -br a | grep eth0 | awk '{print $NF}' | cut -d'/' -f1)"``` 
Mengambil alamat IP dari antarmuka eth0 dan menyimpannya dalam variabel IPETH0. 
- ```ip -br a```: menampilkan informasi antarmuka secara ringkas, 
- ```grep eth0```: mencari baris yang berkaitan dengan eth0, 
- ```awk '{print $NF}'```: mengambil kolom terakhir (yaitu alamat IP dan prefix length), dan 
- ```cut -d'/' -f1```: untuk memisahkan alamat IP dan prefix length dan mengambil alamat IP itu sendiri.

```iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source "$IPETH0" -s 10.47.0.0/20```
Perintah iptables untuk mengkonfigurasi tabel NAT.

- ```-t nat```: Menentukan tabel NAT yang akan diatur (NAT table).
- ```-A POSTROUTING```: Menambahkan aturan pada rantai POSTROUTING, yang berarti aturan ini akan diterapkan setelah proses routing.
- ```-o eth0```: Menentukan antarmuka keluar yang digunakan (eth0).
- ```-j SNAT```: Menentukan target SNAT (Source NAT), yang akan mengubah alamat sumber paket.
- ```--to-source "$IPETH0"```: Menentukan alamat IP yang akan digunakan sebagai alamat sumber yang baru. Alamat ini diambil dari variabel IPETH0 yang telah diambil pada langkah pertama.
- ```-s 10.47.0.0/20```: Menentukan alamat sumber yang akan di-NAT, dalam hal ini, semua paket yang berasal dari subnet 10.47.0.0/20.

**Hasil**: \
![WhatsApp Image 2023-12-18 at 21 25 10_d4414fd6](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/27f9cd0c-70d3-443a-82f1-57fe50b06844)
![WhatsApp Image 2023-12-18 at 21 25 49_f80d4b6b](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/904de119-c0e8-48cb-bc29-ebb1369012c8)


### Soal 2
> Kalian diminta untuk melakukan drop semua TCP dan UDP kecuali port 8080 pada TCP.
```
# Drop semua TCP kecuali pada port 8080
iptables -A INPUT -p tcp --dport 8080 -j ACCEPT
iptables -A INPUT -p tcp -j DROP

# Drop semua UDP 
iptables -A INPUT -p udp -j DROP
```
**Penjelasan**:

```iptables -A INPUT -p tcp --dport 8080 -j ACCEPT```
```iptables -A INPUT -p tcp -j DROP```
Perintah tersebut digunakan untuk memblokir semua koneksi TCP kecuali pada port 8080:
- ```-A INPUT```: Menambahkan aturan pada rantai INPUT, yang menangani paket yang masuk ke sistem.
- ```-p tcp```: Menentukan protokol TCP.
- ```--dport 8080```: Menentukan port tujuan 8080 untuk menerima koneksi.
- ```-j ACCEPT```: Menerima koneksi pada port 8080.
- ```-j DROP```: Menolak semua koneksi TCP.

```- iptables -A INPUT -p udp -j DROP```
Perintah tersebut digunakan untuk menolak semua koneksi UDP:
- ```-A INPUT```: Menambahkan aturan pada rantai INPUT.
- ```-p udp```: Menentukan protokol UDP.
- ```-j DROP```: Menolak semua koneksi UDP.

**Hasil**: \
![WhatsApp Image 2023-12-20 at 20 56 26_abe09446](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/92eb482f-9095-43c0-adb7-d8133f91b7d7)
![WhatsApp Image 2023-12-20 at 20 56 40_cc846373](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/8a8f1f4a-d588-4979-89ad-d70276589c8d)
![WhatsApp Image 2023-12-20 at 20 57 06_7f80f35e](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/9285a9b5-c972-4917-99bc-53a818722aad)
![WhatsApp Image 2023-12-20 at 20 57 17_5c426d53](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/3e0a94ab-5644-4c1d-b640-fa936ab47d1f)


### Soal 3
> Kepala Suku North Area meminta kalian untuk membatasi DHCP dan DNS Server hanya dapat dilakukan ping oleh maksimal 3 device secara bersamaan, selebihnya akan di drop.
```
iptables -A INPUT -p icmp -m connlimit --connlimit-above 3 --connlimit-mask 0 -j REJECT
```
**Penjelasan**:

- ```-A INPUT```: Menambahkan aturan pada rantai INPUT.
- ```-p icmp```: Menentukan protokol ICMP untuk ping.
- ```-m connlimit```: Menggunakan modul connlimit untuk membatasi koneksi.
- ```--connlimit-above 3```: Menentukan batas maksimal 3 koneksi.
- ```--connlimit-mask 0```: Menyatakan bahwa pembatasan berlaku untuk semua alamat IP.
- ```-j REJECT```: Menolak koneksi jika melebihi batas yang ditentukan.

**Hasil**: \
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/5e6dbd0e-98c2-4630-ac21-7d7333c3d857)
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/a9befce6-19c8-4dbb-8a1c-3b7231fef9bb)
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/b275fbfc-510f-44c7-a5b0-7d99a31b6e9a)

Ketika client ke 4 mencoba ping DHCP Server

![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/d2ecda7e-6e91-41f4-b2d1-e7a1917ac2dd)

### Soal 4
> Lakukan pembatasan sehingga koneksi SSH pada Web Server hanya dapat dilakukan oleh masyarakat yang berada pada GrobeForest.
```
iptables -A INPUT -p tcp --dport 22 -s 10.47.4.0/22 -j ACCEPT

iptables -A INPUT -p tcp --dport 22 -j REJECT
```
**Penjelasan**:

```iptables -A INPUT -p tcp --dport 22 -s 10.47.4.0/22 -j ACCEPT```
Perintah tersebut digunakan untuk menerima koneksi SSH dari GrobeForest

```iptables -A INPUT -p tcp --dport 22 -j REJECT```
Perintah tersebut digunakan untuk menolak koneksi SSH dari sumber lainnya

- ```-A INPUT```: Menambahkan aturan pada rantai INPUT.
- ```-p tcp```: Menentukan protokol TCP untuk koneksi SSH.
- ```--dport 22```: Menentukan port tujuan 22 untuk koneksi SSH.
- ```-s 10.47.4.0/22```: Menentukan bahwa hanya sumber dari jaringan GrobeForest yang diizinkan.
- ```-j ACCEPT```: Menerima koneksi SSH dari GrobeForest.
- ```-j REJECT```: Menolak koneksi SSH selain dari GrobeForest.


**Hasil**: \
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/72fc31ff-0583-4b23-a923-2fef956f9c4c)
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/acd32b3a-5287-489a-a0e2-e9495afed61d)

### Soal 5
> Selain itu, akses menuju WebServer hanya diperbolehkan saat jam kerja yaitu Senin-Jumat pada pukul 08.00-16.00.
```
iptables -A INPUT -m time --timestart 08:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT

iptables -A INPUT -j REJECT
```
**Penjelasan**:

```iptables -A INPUT -m time --timestart 08:00 --timestop 16:00 --weekdays Mon,Tue,Wed,Thu,Fri -j ACCEPT```
Perintah tersebut digunakan untuk menerima akses ke Web Server pada jam kerja

```iptables -A INPUT -j REJECT```
Perintah tersebut digunakan untuk menolak akses ke Web Server di luar jam kerja

- ```-A INPUT```: Menambahkan aturan pada rantai INPUT.
- ```-m time```: Menggunakan modul time untuk mengatur waktu.
- ```--timestart 08:00```: Menentukan waktu mulai pada pukul 08.00.
- ```--timestop 16:00```: Menentukan waktu berakhir pada pukul 16.00.
- ```--weekdays Mon,Tue,Wed,Thu,Fri```: Menentukan hari kerja dari Senin hingga Jumat.
- ```-j ACCEPT```: Menerima akses pada jam kerja yang telah ditentukan.
- ```-j REJECT```: Menolak akses.

**Hasil**: \
Dengan waktu yang tidak sesuai \
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/4d070928-f2f1-42a7-82e0-91cdbca62b53)
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/f8288705-dd25-4f87-8dc4-cde7f8b5182e) \
Dengan Waktu yang sesuai \
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/14e32f47-a114-4c78-b422-fe29c19040b3)
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/0049860f-c808-4611-aed8-0ca96f8ee14c)


### Soal 6
> Lalu, karena ternyata terdapat beberapa waktu di mana network administrator dari WebServer tidak bisa stand by, sehingga perlu ditambahkan rule bahwa akses pada hari Senin - Kamis pada jam 12.00 - 13.00 dilarang (istirahat maksi cuy) dan akses di hari Jumat pada jam 11.00 - 13.00 juga dilarang (maklum, Jumatan rek).
```
iptables -A INPUT -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j REJECT 

iptables -A INPUT -m time --timestart 12:00 --timestop 13:00 --weekdays Mon,Tue,Wed,Thu -j REJECT 
```
**Penjelasan**:

```iptables -A INPUT -m time --timestart 11:00 --timestop 13:00 --weekdays Fri -j REJECT ```
Perintah tersebut digunakan untuk menolak akses pada hari Jumat pada jam 11.00-13.00

```iptables -A INPUT -m time --timestart 12:00 --timestop 13:00 --weekdays Mon,Tue,Wed,Thu -j REJECT ```
Perintah tersebut digunakan untuk menolak akses pada hari Senin-Kamis pada jam 12.00-13.00

- ```-A INPUT```: Menambahkan aturan pada rantai INPUT.
- ```-m time```: Menggunakan modul time untuk mengatur waktu.
- ```--timestart 11:00```: Menentukan waktu mulai pada pukul 11.00.
- ```--timestop 13:00```: Menentukan waktu berakhir pada pukul 13:00.
- ```--weekdays Fri```: Menentukan hari Jumat.
- ```--weekdays Mon,Tue,Wed,Thu ```: Menentukan hari Senin-Kamis.
- ```-j REJECT```: Menolak akses pada waktu yang ditentukan.

**Hasil**: \
pada hari biasa

![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/092d29b9-a240-44ff-adfa-ee8e35b01001) 

pada hari jumat 

![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/ff0f2960-7a6e-4ebc-b522-d75ea618ef2a)


### Soal 7
> Karena terdapat 2 WebServer, kalian diminta agar setiap client yang mengakses Sein dengan Port 80 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan dan request dari client yang mengakses Stark dengan port 443 akan didistribusikan secara bergantian pada Sein dan Stark secara berurutan.
```
iptables -A PREROUTING -t nat -p tcp --dport 80 -d 10.47.4.2 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.47.4.2

iptables -A PREROUTING -t nat -p tcp --dport 80 -d 10.47.4.2 -j DNAT --to-destination 10.47.0.10

iptables -A PREROUTING -t nat -p tcp --dport 443 -d 10.47.0.10 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.47.0.10

iptables -A PREROUTING -t nat  -p tcp --dport 443 -d 10.47.0.10 -j DNAT --to-destination 10.47.4.2
```
**Penjelasan**:

Perintah ```iptables``` tersebut dijalankan pada node Heiter (Router), yang merupakan router yang berada diantara node Webserver Sein dan Stark. 
```iptables -A PREROUTING -t nat -p tcp --dport 80 -d 10.47.4.2 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.47.4.2```

```iptables -A PREROUTING -t nat -p tcp --dport 80 -d 10.47.4.2 -j DNAT --to-destination 10.47.0.10```
Perintah tersebut digunakan untuk distribusi koneksi HTTP (Port 80) pada Sein dan Stark secara bergantian


```iptables -A PREROUTING -t nat -p tcp --dport 443 -d 10.47.0.10 -m statistic --mode nth --every 2 --packet 0 -j DNAT --to-destination 10.47.0.10```

```iptables -A PREROUTING -t nat -p tcp --dport 443 -d 10.47.0.10 -j DNAT --to-destination 10.47.4.2```
Perintah tersebut digunakan untuk distribusi koneksi HTTPS (Port 443) pada Sein dan Stark secara bergantian

- ```-A PREROUTING```: Menambahkan aturan pada rantai PREROUTING dalam tabel nat.
- ```-t nat```: Menentukan tabel nat.
- ```-p tcp```: Menentukan protokol TCP.
- ```--dport 80```: Menentukan port tujuan 80 (HTTP).
- ```--dport 443```: Menentukan port tujuan 4430 (HTTPS).
- ```-d 10.47.4.2```: Menentukan destinasi IP 10.47.4.2.
- ```-m statistic --mode nth --every 2 --packet 0```: Menggunakan modul statistic untuk mendistribusikan koneksi secara bergantian setiap dua paket.
- ```-j DNAT --to-destination```: Mengubah alamat tujuan koneksi (DNAT).
- ```10.47.4.2``` dan ```10.47.0.10```: Alamat IP destinasi Sein dan Stark.

**Hasil**: \
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/341fdf84-80d7-4b5b-b00e-3f073a76d94c)
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/cc77ca79-3fd4-45f8-86c9-6c575d9c7909)

### Soal 8
> Karena berbeda koalisi politik, maka subnet dengan masyarakat yang berada pada Revolte dilarang keras mengakses WebServer hingga masa pencoblosan pemilu kepala suku 2024 berakhir. Masa pemilu (hingga pemungutan dan penghitungan suara selesai) kepala suku bersamaan dengan masa pemilu Presiden dan Wakil Presiden Indonesia 2024.
```
iptables -A INPUT -p tcp --dport 80 -s 10.47.0.20/30 -m time --datestart 2023-12-11 --datestop 2024-02-15 -j DROP
```
**Penjelasan**:

- ```-A INPUT```: Menambahkan aturan pada rantai INPUT.
- ```-p tcp```: Menentukan protokol TCP.
- ```--dport 80```: Menentukan port tujuan 80 (HTTP).
- ```-s 10.47.0.20/30```: Subnet Revolte yang akan diblokir.
- ```-m time --datestart 2023-12-11 --datestop 2024-02-15```: Menggunakan modul time untuk menentukan rentang waktu pemilu kepala suku 2024, dimulai dari 11 Desember 2023 hingga 15 Februari 2024.
- ```-j DROP```: Menolak akses HTTP selama rentang waktu pemilu kepala suku 2024.

**Hasil**: \
Pada Revolte (Fri Dec 22 08:03:45 UTC 2023) \
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/4f48b5cb-c7c3-40a5-b2b2-16e1d1202da5) \
Pada TurkRegion (Fri Dec 22 08:03:45 UTC 2023) \
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/ddbd0e2e-acf7-4486-8eff-702e1bee05b4) \
============================================== \
Pada Revolte (Wed Feb 14 09:00:00 UTC 2024) \
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/e527f48a-988d-4827-94a7-67e062b5261d) \
Pada TurkRegion (Wed Feb 14 09:00:00 UTC 2024) \
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/04116877-d186-415e-a9c5-c7632b199cbe) \
============================================== \
Pada Revolte (Wed Feb 16 09:00:00 UTC 2024) \
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/4726f3a7-3c38-46aa-b4ee-842edd7e93e5) \

### Soal 9
> Sadar akan adanya potensial saling serang antar kubu politik, maka WebServer harus dapat secara otomatis memblokir alamat IP yang melakukan scanning port dalam jumlah banyak (maksimal 20 scan port) di dalam selang waktu 10 menit. (clue: test dengan nmap)
```
iptables -N scan_port

iptables -A INPUT -m recent --name scan_port --update --seconds 600 --hitcount 20 -j REJECT
iptables -A FORWARD -m recent --name scan_port --update --seconds 600 --hitcount 20 -j REJECT

iptables -A INPUT -m recent --name scan_port --set -j ACCEPT
iptables -A FORWARD -m recent --name scan_port --set -j ACCEPT
```
**Penjelasan**:

Membuat rantai scan_port: ```iptables -N scan_port```

Menolak akses dari alamat IP yang melakukan scanning port (INPUT): ```iptables -A INPUT -m recent --name scan_port --update --seconds 600 --hitcount 20 -j REJECT```

Menolak akses dari alamat IP yang melakukan scanning port (FORWARD): ```iptables -A FORWARD -m recent --name scan_port --update --seconds 600 --hitcount 20 -j REJECT```

Menyetel alamat IP yang melakukan scanning port (INPUT): ```iptables -A INPUT -m recent --name scan_port --set -j ACCEPT```

Menyetel alamat IP yang melakukan scanning port (FORWARD): ```iptables -A FORWARD -m recent --name scan_port --set -j ACCEPT```

- ```iptables -N scan_port```: Membuat rantai baru dengan nama scan_port.
- ```-A INPUT -m recent --name scan_port --update --seconds 600 --hitcount 20 -j REJECT```: Menolak akses dari alamat IP yang melakukan scanning port pada rantai INPUT, dengan aturan hitcount maksimal 20 dalam selang waktu 10 menit.
- ```-A FORWARD -m recent --name scan_port --update --seconds 600 --hitcount 20 -j REJECT```: Menolak akses dari alamat IP yang melakukan scanning port pada rantai FORWARD, dengan aturan hitcount maksimal 20 dalam selang waktu 10 menit.
- ```-A INPUT -m recent --name scan_port --set -j ACCEPT```: Menyetel alamat IP yang melakukan scanning port pada rantai INPUT agar diizinkan.
- ```-A FORWARD -m recent --name scan_port --set -j ACCEPT```: Menyetel alamat IP yang melakukan scanning port pada rantai FORWARD agar diizinkan.

**Hasil**: \
![image](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/33d274a0-3b8c-4dc5-ab45-649ada8366f8)

### Soal 10
> Karena kepala suku ingin tau paket apa saja yang di-drop, maka di setiap node server dan router ditambahkan logging paket yang di-drop dengan standard syslog level. 
**Penjelasan**: \
Untuk menyelesaikan soal nomor 10 dapat digunakan syntax berikut:

```bash
iptables -A INPUT  -j LOG --log-level debug --log-prefix 'Dropped Packet' -m limit --limit 1/second --limit-burst 10
```

`iptables -A INPUT  -j LOG --log-level debug --log-prefix 'Dropped Packet' -m limit --limit 1/second --limit-burst 10`
Berikut adalah penjelasan dari bagian pada syntax tersebut:

`-A INPUT`: Menambahkan aturan ke chain INPUT.

`-j LOG`: Menunjukkan bahwa aksi yang akan diambil adalah log. Ketika paket mencocokkan aturan ini dan ditolak, informasi tentang paket tersebut akan dicatat dalam log sistem.

`--log-level debug`: Menentukan level log yang akan digunakan. Dalam hal ini, level log adalah "debug", yang berarti log akan mencatat informasi lebih rinci.

`--log-prefix 'Dropped Packet'`: Menetapkan prefix atau awalan untuk setiap entri log. Dalam hal ini, pesan log akan dimulai dengan teks "Dropped Packet".

`-m limit --limit 1/second --limit-burst 10`: Menggunakan modul "limit" untuk mengatur batasan pada jumlah log yang akan dicatat.

`--limit 1/second`: Menetapkan batasan sebanyak satu log per detik.

`--limit-burst 10`: Menetapkan batasan burst, yaitu jumlah log yang dapat dilakukan dalam satu waktu sebelum batasan per detik diambil kembali.

Pada list iptables tersebut terdapat rules untuk membuat log sehingga dapat dilihat paket yang telah didrop.
**Hasil**: \
![Screenshot 2023-12-20 212111](https://github.com/javakanaya/Jarkom-Modul-5-E21-2023/assets/27951856/c36eb307-151b-4173-8343-c7d9932bebf6)

