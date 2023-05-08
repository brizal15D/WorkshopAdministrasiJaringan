# INSTALASI NTP DEBIAN SERVER 
(pada VMWARE)
- [Download Debian Server](#download-debian-server)
- [Instalasi Debian Server](#instalasi-debian-server)
- [Instalasi NTP Server Debian](#instalasi-ntp-server-debian)
- [Konfigurasi NTP Client Mikrotik ke Server Debian](#konfigurasi-ntp-client-mikrotik-ke-server-debian)
  - [Membuka file konfigurasi ntp server](#membuka-file-konfigurasi-ntp-server)
  - [Menjalankan ntp](#menjalankan-ntp)
  - [ntp client](#ntp-client)
- [Hasil](#hasil)

## Download Debian Server
Kita mengunduh file debian di link berikut :
    https://www.osboxes.org/debian/#debian-11-vmware

## Instalasi Debian Server
1. File yang diunduh tadi di _extract_ terlebih dahulu
2. Buka VM Ware, pilih menu create a new virtual machine->Typical
![create virtual machine](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/1.png)
3. Pilih "I will install operating system later"
![I will install operating system later](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/2.png)
4. Pilih linux Debian 11 x64 bit
![linux Debian 11 x64 bit](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/3.png)
5. Beri nama Debian 11.x 64-bit server dan _locate_ biarkan default
![Debian 11.x 64-bit server](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/4.png)
6. Disini saya mengatur max hardisk yang digunakan sebanyak 10 GB
![max hardisk](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/5.png)
7. Setting konfigurasi hardware-nya
![konfigurasi hardware](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/6.png)
8. Hasilnya adalah sebuah settingan yang siap diisi debian server
![Hasil](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/7.png)
9. Pergi ke C:\Users\ ...\Documents\Virtual Machines\Debian 11.x 64-bit server dan delete file berikut
![delete file](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/8.png)
10. File di _extract_ tadi pindahkan ke C:\Users\ ...\Documents\Virtual Machines\Debian 11.x 64-bit server dan rename menjadi Debian 11.x 64-bit server
11. Jalankan VM Debian server-nya
![Jalankan VM](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/9.png)
12. username: osboxes password: osboxes.org
![ username password](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/10.png)
13. Debian server siap digunakan

## Instalasi NTP Server Debian
1. Lakukan penginstalan package ntp:
```console
sudo apt install ntp
```
![install ntp](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/11.png)
2. Masukkan Password: osboxes.org
3. Pilih y dan tunggu hingga selesai
![selesai](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/12.png)

## Konfigurasi NTP Client Mikrotik ke Server Debian
### Membuka file konfigurasi ntp server
1. Lakukan update apt-get
```console
sudo apt-get update
```
2. Jalan code dibawah ini agar dapat menjalankan vim
```console
sudo apt-get install vim
```
3. Bukalah pengaturan ntp dengan menggunakan perintah
```console
sudo vim /etc/ntp.conf
```
4. Inputkan konfigurasi dibawah ini: 
```console
pool 0.debian.pool.ntp.org iburst
pool 1.debian.pool.ntp.org iburst
pool 2.debian.pool.ntp.org iburst
pool 3.debian.pool.ntp.org iburst
```
5. Simpan dengan cara tekan esc dan masukkan perintah berikut
```console
:wq.
```
![selesai](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/13.png)
### Menjalankan ntp
1. Gunakan perintah berikut untuk run ntp
```console
sudo service ntp status
```
![status ntp](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/14.png)
2. Cek juga dengan 
```
sudo netstat -npltu
```
![netstat](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/15.png)
3. Bisa juga dengan mengecek date-nya
```
date
```
![date1](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/16.png)
- jalankan perintah berikut dan pilih indonesia->Java
```
cd /usr/share/zoneinfo
tzselect
```
- untuk mensave gunakan perintah berikut:
```
TZ='Asia/Jakarta'
```
- cek kembali date
![date](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%204/Assets/17.png)

### ntp client
atur ntp client pada mikrotik dengan winbox di menu`System -> SNTP Client` dan simpan

## Hasil
Setelah konfigurasi selesai, Seharusnya waktu dimikrotik dan server bakal sama
