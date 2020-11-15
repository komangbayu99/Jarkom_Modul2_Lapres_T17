# Shift 1 JARKOM 2020  -T17
Penyelesaian Soal Shift 1 Komunikasi Data, dan Jaringan Data 2020\
Kelompok T17
  * Milenia Ulwan Zafira (05311840000020)
  * Bayu Trianayasa      (05311840000038)

## Topologi
```
# Switch
uml_switch -unix switch1 > /dev/null < /dev/null &
uml_switch -unix switch2 > /dev/null < /dev/null &

# Router
xterm -T SURABAYA -e linux ubd0=SURABAYA,jarkom umid=SURABAYA eth0=tuntap,,,'ip_tuntap_tiap_kelompok' eth1=daemon,,,switch2 eth2=daemon,,,switch1 mem=96M &

# Server
xterm -T MALANG -e linux ubd0=MALANG,jarkom umid=MALANG eth0=daemon,,,switch2 mem=128M &
xterm -T MOJOKERTO -e linux ubd0=MOJOKERTO,jarkom umid=MOJOKERTO eth0=daemon,,,switch2 mem=128M &
xterm -T PROBOLINGGO -e linux ubd0=PROBOLINGGO,jarkom umid=PROBOLINGGO eth0=daemon,,,switch2 mem=128M &

# Klien
xterm -T SIDOARJO -e linux ubd0=SIDOARJO,jarkom umid=SIDOARJO eth0=daemon,,,switch1 mem=96M &
xterm -T GRESIK -e linux ubd0=GRESIK,jarkom umid=GRESIK eth0=daemon,,,switch1 mem=96M &
```
## Interfaces UML (Setting IP)
* [Surabaya](#Surabaya)
* [Malang](#Malang)
* [Mojokerto](#Mojokerto)
* [Probolinggo](#Probolinggo)
* [Sidoarjo](#Sidoarjo)
* [Gresik](#Gresik)



## Table of Contents
* [Soal 1](#soal-1)
* [Soal 2](#soal-2)
* [Soal 3](#soal-3)
* [Soal 4](#soal-4)
* [Soal 5](#soal-5)
* [Soal 6](#soal-6)
* [Soal 7](#soal-7)

---

## Surabaya
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.70.58
netmask 255.255.255.252
gateway 10.151.70.57

auto eth1
iface eth1 inet static
address 10.151.71.113
netmask 255.255.255.248

auto eth2
iface eth2 inet static
address 192.168.0.1
netmask 255.255.255.0
````
## Malang
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.71.114
netmask 255.255.255.248
gateway 10.151.71.113
```
## Mojokerto 
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.71.115
netmask 255.255.255.248
gateway 10.151.71.113
```
## Probolinggo
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.151.71.116
netmask 255.255.255.248
gateway 10.151.71.113
```
## Sidoarjo
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1
```
## Gresik
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
```
---

## Soal 1

- update pada **MALANG** dengan cara menuliskan kata ``apt-get update``

- Instal bind9 dengan ``apt-get install bind9 -y``

- Beri perintah ``nano /etc/bind/named.conf.local``

- Isikan configurasi domain semerut17.pw sesuai dengan syntax sbagai berikut : 

`` zone "semerut17.pw" {
	   type master;
	   file "etc/bind/jarkom/semerut17.pw";
}; ``


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777162105257197568/1605346401630.jpg)


- Copy file **db.local** pada path **/etc/bind** ke dalam folder jarkom yang baru saja dibuat : 

- Edit file semerut17.pw seperti gambar dibawah


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777162139378778152/1605346489650.jpg)


- Kemudian restart bind9 dengan perintah ``service bind9 restart``

- Pada client GRESIK arahkan nameserver menuju IP MALANG dengan mengedit file resolve.conf dengan perintah ``nano /etc/resolv.conf``

- Untuk mencoba koneksi DNS, lakukan ping domain semerut17.pw dengan melakukan perintah berikut pada client GRESIK ``ping semerut17.pw``


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777217975274962964/Gresik1.jpg)


## Soal 2 

- Step awal kita harus membuka file pada server malang dengan cara ``nano /etc/bind/jarkom/semerut17.pw`` jika sudah kita harus tambahkan konfigurasi seperti dibawah ini(pada CNAME).


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777162139378778152/1605346489650.jpg)


- Lalu Restart bind9 dengan perintah ``service bind9 restart``

- Setelah itu cek di client GRESIK ping www.semerut17.pw


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777292301805682688/Gresik2.jpg)


## Soal 3

- Pertama-tama kita harus edit file semeru.pw pada MALANG nano /etc/bind/jarkom/semerut17.pw


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777162139378778152/1605346489650.jpg)


- Lalu edit ``nano /etc/bind/named.conf.local``

- Kemudian restart bind9 dengan perintah ``service bind9 restart``

- Kemudian pada client GRESIK lakukan Ujicoba ``ping penanjakan.semerut17.pw``


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777293821574774824/Gresik3.jpg)



## Soal 4

- Langkah awal kita akan mengedit file  ``nano /etc/bind/named.conf.local`` pada MALANG

``zone "71.151.10.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/71.151.10.in-addr.arpa";
};``

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777162105257197568/1605346401630.jpg)


- Selanjutnya adalah copy ``db.local`` ke dalam file ``71.151.10.in-addr.arpa`` pada folder jarkom dengan perintah ``cp /etc/bind/db.local /etc/bind/jarkom/71.151.10.in-addr.arpa``

- ``71.151.10`` merupakan 3 byte pertama IP MALANG yang di-reverse urutannya

- Kemudian edit file dengan ``nano /etc/bind/jarkom/71.151.10.in-addr.arpa``


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777162322711150603/1605346515750.jpg)


- Kemudian restart bind9 dengan perintah ``service bind9 restart``

- Untuk mengecek konfigurasi dapat melakukan perintah ``host -t PTR 10.151.71.116`` pada client GRESIK

![picture](https://cdn.discordapp.com/attachments/691272793706201100/777536209189863434/no_4_ujicoba.jpg)

## Soal 5

- Pada MALANG edit ``nano /etc/bind/named.conf.local``

``zone "semerut17.pw" {
    type master;
    notify yes;
    also-notify { 10.151.71.116; }; // IP MOJOKERTO
    allow-transfer { 10.151.71.116; }; // MOJOKERTO
    file "/etc/bind/jarkom/semerut17.pw";
}; `` 


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777162105257197568/1605346401630.jpg)


- Kemudian restart bind9 dengan perintah ``service bind9 restart``

- Buka MOJOKERTO dan update package lists dengan menjalankan command ``apt-get update``

- Kemudian install aplikasi bind9 pada MOJOKERTO ``apt-get install bind9 -y``

- Edit file pada MOJOKERTO agar menjadi DNS Slave ``nano /etc/bind/named.conf.local``


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777298754012708866/Mojokerto2.jpg)


- Langkah Selanjutnya adalah kita restart bind9 pada MOJOKERTO dengan perintah ``service bind9 restart``

- Pada sever MALANG kita akan mematikan service bind9 ``service bind9 stop``

- Pada client GRESIK atur nameserver mengarah ke IP MALANG dan MOJOKERTO ``nano /etc/resolv.conf`` 

- Langkah terakhir adalah kita akan melakukan  ``ping semerut17.pw`` pada client GRESIK


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777300430026833920/Gresik1.jpg) 


## Soal 6

**MALANG**

- Edit file ``nano /etc/bind/jarkom/semerut17.pw``

- Tambahkan konfigurasi


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777162139378778152/1605346489650.jpg)


- Step selanjutnya adalah Mengedit nano ``/etc/bind/named.conf.options``

- Setelah sudah, edit nano ``/etc/bind/named.conf.local``

``zone "semerut17.pw" {
    type master;
    notify yes;
    also-notify { 10.151.71.116; }; // IP MOJOKERTO
    allow-transfer { 10.151.71.116; }; // MOJOKERTO
    file "/etc/bind/jarkom/semerut17.pw";
};``

- Jika semua sudah terlakukan, Maka kita akan restart bind9 dengan perintah ``service bind9 restart``

**MOJOKERTO**

- Lakukan Comment ``//dnssec-validation auto;``

- Jika sudah, Tambahkanlah  ``allow-query{any;};``

- Setelah itu kita harus edit file nano dengan cara ``/etc/bind/named.conf.local``

``zone "semerut17.pw" {
    type slave;
    masters { 10.151.71.114; }; // IP MALANG
    file "/var/lib/bind/gunung.semerut17.pw";
};``


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777298754012708866/Mojokerto2.jpg)


- Step selanjutnya adalah kita harus membuat direktori delegasi ``mkdir /etc/bind/delegasi``

- Copy ``db.local`` ke dalam ``gunung.semeru.t17.pw`` dengan cara sebagai berikut ``cp /etc/bind/db.local /etc/bind/delegasi/gunung.semerut17.pw``

- Edit ``nano /etc/bind/delegasi/gunung.semerut17.pw`` menjadi seperti gambar di bawah ini 


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777304707826843668/Mojokerto1.jpg) 


- Setelah itu restart bind9 dengan perintah ``service bind9 restart``

- Setelah itu Lakukan uji coba dengan cara ``ping gunung.semerut17.pw``


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777305958413238342/gresik4.jpg)


## Soal 7

- Pada MOJOKERTO edit ``nano /etc/bind/delegasi/gunung.semerut14.pw dan tambahkan naik IN A 10.151.77.164``


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777304707826843668/Mojokerto1.jpg) 


- Langkah selanjutnya restart bind9 dengan perintah sebagai berikut ``service bind9 restart``

- Setelah itu jika sudah, lakukan uji coba dengan cara ``ping naik.gunung.semerut17.pw``


![picture](https://cdn.discordapp.com/attachments/777146787336290354/777307383683743754/gresik5.jpg)


