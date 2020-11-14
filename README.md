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
* [Soal 8](#soal-8)
* [Soal 9](#soal-9)
* [Soal 10](#soal-10)
* [Soal 11](#soal-11)
* [Soal 12](#soal-12)
* [Soal 13](#soal-13)
* [Soal 14](#soal-14)
* [Soal 15](#soal-15)
* [Soal 16](#soal-16)
* [Soal 17](#soal-17)
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
- Isikan configurasi domain semerut08.pw sesuai dengan syntax sbagai berikut : 

``zone "semerut08.pw"{
	type master;
	file "/etc/bind/jarkom/semerut08.pw";
};`` 

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777162105257197568/1605346401630.jpg)

-Copykan file **db.local** pada path **/etc/bind** ke dalam folder jarkom yang baru saja dibuat : 
-Edit file semerut17.pw seperti gambar dibawah

![picture](https://cdn.discordapp.com/attachments/777146787336290354/777162139378778152/1605346489650.jpg)

- Kemudian restart bind9 dengan perintah ``service bind9 restart``
- Pada client GRESIK dan SIDOARJO arahkan nameserver menuju IP MALANG dengan mengedit file resolve.conf dengan perintah ``nano /etc/resolv.conf``
- Untuk mencoba koneksi DNS, lakukan ping domain semerut14.pw dengan melakukan perintah berikut pada client GRESIK ``ping semerut14.pw``

- ![picture](https://cdn.discordapp.com/attachments/777146787336290354/777217975274962964/Gresik1.jpg)

## Soal 2

## Soal 3

## Soal 4

## Soal 5

## Soal 6

## Soal 7

## Soal 8

## Soal 9

## Soal 10

## Soal 11

## Soal 12

## Soal 13

## Soal 14

## Soal 15

## Soal 16

## Soal 17
