# Jarkom_Modul4_Lapres_B05

- Vania Meilani Taqiyyah 05111840000045
- Elvira Catrine Natalie 05111840000016

## Pembagian Subnet
Untuk server **MOJOKERTO** dan **MALANG**, tidak diikutkan dalam subnet pembagian IP, karena menggunakan **NID DMZ: 10.151.83.48/29**, di mana akan dipecah masing-masing mendapatkan **NID 10.151.83.48/30** dan **10.151.83.52/30**.

<img src="https://user-images.githubusercontent.com/61219556/102013471-f9261f00-3d82-11eb-8a92-4152410854c0.png" width="500" height="auto">

## A. VLSM (Variable Length Subnet Masking) - CPT
<img src="https://user-images.githubusercontent.com/61219556/102014896-ee6f8800-3d8a-11eb-8543-5d927ec8fe55.PNG" width="500" height="auto">
- Subnet besar yang dibentuk memiliki **NID 192.168.0.0** dengan netmask **/19**. Pembagian IP berdasarkan NID dan netmask dihitung menggunakan pohon pada gambar di bawah:
<img src="https://user-images.githubusercontent.com/61219556/102015576-0f39dc80-3d8f-11eb-80be-d5b2d43a11e8.jpg" width="500" height="auto">
- Kemudian NID dibagikan pada setiap subnet pada topologi sesuai dengan tabel diatas.
- Untuk melakukan subneting pada cpt, bisa diliat di **Modul 4 : SUBNETING & ROUTING**.
- Untuk melakukan routing pada cpt dapat dilakukan pada menu `Config > Routing > Static` pada device Router. Lalu, diberikan static route pada semua router yang ada dengan route sebagai berikut :
**SURABAYA**
```
192.168.8.0/22 via 192.168.0.2
192.168.0.4/30 via 192.168.0.2
192.168.0.4/30 via 192.168.0.2
192.168.24.0/21 via 192.168.0.2
192.168.2.0/23 via 192.168.0.10
192.168.0.16/28 via 192.168.0.10
192.168.12.0/22 via 192.168.0.10
192.168.0.12/30 via 192.168.0.10
192.168.1.0/24 via 192.168.0.10
192.168.16.0/22 via 192.168.0.10
10.151.83.52/30 via 192.168.0.10
```
**BATU**
```
0.0.0.0/0 via 192.168.0.9
192.168.0.16/28 via 192.168.2.2
192.168.1.0/24 via 192.168.0.14
192.168.16.0/24 via 192.168.0.14
10.151.83.52/30 via 192.168.0.14
```
**PASURUAN**
```
0.0.0.0/0 via 192.168.0.1
192.168.0.128/25 via 192.168.0.6
192.168.24.0/21 via 192.168.0.6
```
**KEDIRI**
```
0.0.0.0/0 via 192.168.0.13
192.168.16.0/22 via 192.168.1.2
```
**PROBOLINGGO**
```
0.0.0.0/0 via 192.168.0.5
```
**MADIUN**
```
0.0.0.0/0 via 192.168.2.1
```
BLITAR
```
0.0.0.0/0 via 192.168.1.1
```

## CIDR (Classless Inter Domain Routing) - UML
Metode ini dikerjakan dengan cara menggabungkan subnet-subnet paling bawah dalam topologi, hingga subnet paling atas (mendekati cloud), berikut adalah penggabunganya : 
<img src="https://user-images.githubusercontent.com/61219556/102016191-49f14400-3d92-11eb-9ee4-af25f148b97e.jpg" width="500" height="auto">
<img src="https://user-images.githubusercontent.com/61219556/102016282-ac4a4480-3d92-11eb-9f9e-7ae1032546a2.jpg" width="500" height="auto">
<img src="https://user-images.githubusercontent.com/61219556/102016284-af453500-3d92-11eb-92c8-3d9434944225.jpg" width="500" height="auto">
<img src="https://user-images.githubusercontent.com/61219556/102016207-61303180-3d92-11eb-9777-fa37294a46b8.jpg" width="500" height="auto">
<img src="https://user-images.githubusercontent.com/61219556/102016219-67261280-3d92-11eb-91d8-3758be15f3aa.jpg" width="500" height="auto">
<img src="https://user-images.githubusercontent.com/61219556/102016225-6beac680-3d92-11eb-9e67-baa6ab365d21.jpg" width="500" height="auto">
<img src="https://user-images.githubusercontent.com/61219556/102016229-6ee5b700-3d92-11eb-8ee9-607b182c5e3a.jpg" width="500" height="auto">
- Sehingga di dapatkan pohon pembagian IP berdasarkan penggabungan subnet yang telah dilakukan:
<img src="https://user-images.githubusercontent.com/61219556/102016385-3beff300-3d93-11eb-8e16-7c2cd65ba80b.png" width="500" height="auto">
- Kemudian NID dibagikan pada setiap subnet pada topologi seperti berikut : 
<img src="https://user-images.githubusercontent.com/61219556/102016443-a30da780-3d93-11eb-97d0-d9c06a1b1f9e.jpg" width="500" height="auto"> 
- Membuat file `topologi.sh` pada putty dengan konfigurasi seperti berikut : 
```
Switch
uml_switch -unix switch1 > /dev/null < /dev/null &
uml_switch -unix switch2 > /dev/null < /dev/null &
uml_switch -unix switch3 > /dev/null < /dev/null &
uml_switch -unix switch4 > /dev/null < /dev/null &
uml_switch -unix switch5 > /dev/null < /dev/null &
uml_switch -unix switch13 > /dev/null < /dev/null &
uml_switch -unix switch15 > /dev/null < /dev/null &
uml_switch -unix switch16 > /dev/null < /dev/null &
uml_switch -unix switch17 > /dev/null < /dev/null &
uml_switch -unix switch18 > /dev/null < /dev/null &
uml_switch -unix switch19 > /dev/null < /dev/null &
uml_switch -unix switch20 > /dev/null < /dev/null &
uml_switch -unix switch21 > /dev/null < /dev/null &
uml_switch -unix switch22 > /dev/null < /dev/null &
uml_switch -unix switch25 > /dev/null < /dev/null &

Router
xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,10.151.74.25 eth1=daemon,,,switch1 eth2=daemon,,,switch2 eth3=daemon,,,switch4 eth4=daemon,,,switch13 mem=64M &
xterm -T PASURUAN -e linux ubd0=PASURUAN,jarkom umid=PASURUAN eth0=daemon,,,switch2 eth1=daemon,,,switch3 eth2=daemon,,,switch19 mem=64M &
xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch3 eth1=daemon,,,switch15 eth2=daemon,,,switch16 mem=64M &
xterm -T BATU -e linux ubd0=BATU,jarkom umid=BATU eth0=daemon,,,switch4 eth1=daemon,,,switch5 eth2=daemon,,,switch21 eth3=daemon,,,switch22 mem=64M &
xterm -T MADIUN -e linux ubd0=MADIUN,jarkom umid=MADIUN eth0=daemon,,,switch22 eth1=daemon,,,switch25 mem=64M &
xterm -T KEDIRI -e linux ubd0=KEDIRI,jarkom umid=KEDIRI eth0=daemon,,,switch5 eth1=daemon,,,switch17 eth2=daemon,,,switch18 mem=64M &
xterm -T BLITAR -e linux ubd0=BLITAR,jarkom umid=BLITAR eth0=daemon,,,switch17 eth1=daemon,,,switch20 mem=64M &

Server
xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch18 mem=64M &
xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO eth0=daemon,,,switch13 mem=64M &

Klien
xterm -T SAMPANG -e linux ubd0=SAMPANG,jarkom umid=SAMPANG eth0=daemon,,,switch1 mem=64M &
xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch19 mem=64M &
xterm -T BANYUWANGI -e linux ubd0=BANYUWANGI,jarkom umid=BANYUWANGI eth0=daemon,,,switch16 mem=64M &
xterm -T JEMBER -e linux ubd0=JEMBER,jarkom umid=JEMBER eth0=daemon,,,switch16 mem=64M &
xterm -T BONDOWOSO -e linux ubd0=BONDOWOSO,jarkom umid=BONDOWOSO eth0=daemon,,,switch15 mem=64M &
xterm -T BOJONEGORO -e linux ubd0=BOJONEGORO,jarkom umid=BOJONEGORO eth0=daemon,,,switch25 mem=64M &
xterm -T JOMBANG -e linux ubd0=JOMBANG,jarkom umid=JOMBANG eth0=daemon,,,switch22 mem=64M &
xterm -T NGANJUK -e linux ubd0=NGANJUK,jarkom umid=NGANJUK eth0=daemon,,,switch21 mem=64M &
xterm -T TULUNGAGUNG -e linux ubd0=TULUNGAGUNG,jarkom umid=TULUNGAGUNG eth0=daemon,,,switch20 mem=64M &
xterm -T LUMAJANG -e linux ubd0=LUMAJANG,jarkom umid=LUMAJANG eth0=daemon,,,switch17 mem=64M &
```
- Pada UML yang berperan sebagai router, melakukan uncomment pada perintah `net.ipv4.ip_forward=1` agar dapat meneruskan route yaitu dengan cara mengetikkan `nano /etc/sysctl.conf`. Lalu, ketik `sysctl -p.` untuk mengaktifkan perubahan baru. Kemudian, atur interface pada setiap UML dengan menjalankan perintah `nano /etc/network/interfaces` kemudian melakukan `restart networking restart`.

- Berikut setting file `/etc/network/interfaces` untuk setiap UML:
**SURABAYA (Router)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.74.26
netmask 255.255.255.252
gateway 10.151.74.25

auto eth1
iface eth1 inet static
address 192.168.64.1
netmask 255.255.252.0

auto eth2
iface eth2 inet static
address 192.168.192.1
netmask 255.255.255.252

auto eth3
iface eth3 inet static
address 192.168.32.1
netmask 255.255.255.252

auto eth4
iface eth4 inet static
address 10.151.83.49
netmask 255.255.255.252
```
**PASURUAN (Router)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.192.2
netmask 255.255.255.252
gateway 192.168.192.1

auto eth1
iface eth1 inet static
address 192.168.144.1
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.168.160.1
netmask 255.255.252.0
```
**MOJOKERTO (Server)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.83.50
netmask 255.255.255.252
gateway 10.151.83.49
```
**SAMPANG (Client)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.64.2
netmask 255.255.252.0
gateway 192.168.64.1
```
**PROBOLINGGO (Router)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.144.2
netmask 255.255.255.252
gateway 192.168.144.1

auto eth1
iface eth1 inet static
address 192.168.136.1
netmask 255.255.255.128

auto eth2
iface eth2 inet static
address 192.168.128.1
netmask 255.255.248.0
```
**SIDOARJO (Client)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.160.2
netmask 255.255.252.0
gateway 192.168.160.1
```
**BANYUWANGI (Client)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.128.3
netmask 255.255.248.0
gateway 192.168.128.1
```
**JEMBER (Client)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.128.2
netmask 255.255.248.0
gateway 192.168.128.1
```
**BONDOWOSO (Client)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.136.2
netmask 255.255.255.128
gateway 192.168.136.1
```
**BATU (Rouoter)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.32.2
netmask 255.255.255.252
gateway 192.168.32.1

auto eth1
iface eth1 inet static
address 192.168.8.1
netmask 255.255.255.252

auto eth2
iface eth2 inet static
address 192.168.20.1
netmask 255.255.252.0

auto eth3
iface eth3 inet static
address 192.168.16.1
netmask 255.255.254.0
```
**KEDIRI (Router)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.8.2
netmask 255.255.255.252
gateway 192.168.8.1

auto eth1
iface eth1 inet static
address 192.168.4.1
netmask 255.255.255.0

auto eth2
iface eth2 inet static
address 10.151.83.53
netmask 255.255.255.252
```
#### JOMBANG (Client)
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.16.3
netmask 255.255.254.0
gateway 192.168.16.1
```
**MADIUN (Router)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.16.2
netmask 255.255.254.0
gateway 192.168.16.1

auto eth1
iface eth1 inet static
address 192.168.18.1
netmask 255.255.255.240
```
**BOJONEGORO (Client)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.18.2
netmask 255.255.255.240
gateway 192.168.18.1
```
**NGANJUK (Client)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.20.2
netmask 255.255.252.0
gateway 192.168.20.1
```
**MALANG (Server)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.83.54
netmask 255.255.255.252
gateway 10.151.83.53
```
**BLITAR (Router)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.4.2
netmask 255.255.255.0
gateway 192.168.4.1

auto eth1
iface eth1 inet static
address 192.168.0.1
netmask 255.255.252.0
```
**LUMAJANG (Client)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.4.3
netmask 255.255.255.0
gateway 192.168.4.1
```
**TULUNGAGUNG (Client)**
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.252.0
gateway 192.168.0.1
```
- Agar UML dapat mengakses internet, pada **SURABAYA** diketikkan perintah `iptables –t nat –A POSTROUTING –o eth0 –j MASQUERADE –s 192.168.0.0/16`.

[ PENGERJAAN UNTUK UML HANYA SAMPAI SINI, UNTUK ROUTING UP ]


