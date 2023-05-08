# Install Web Server di Linux
### Daftar Isi

- [Cara 1](#Cara-1)
    -  [Install nginx, MariaFB, php](#Install-nginx-MariaFB-php)
    -  [Install utility untuk install composer](#Install-utility-untuk-install-composer)
    -  [Download composer.phar](#Download-composerphar)
    -  [Cek version](#Cek-version)
- [Cara 2](#Cara-2)
    -  Install web server, php, database
        -  Install MariaDB-server
        -  Membuat user baru
        -  Upload projeck ke webserver
    - Install konfigurasi FTP Server
        - Install ProFTPD
        - Backup
        - Membuat user baru
        - uji coba FTP
        
 ## Install nginx, MariaFB, php
lakukan instalasi dengan perintah dibawah ini:
```console
sudo apt install nginx php mariadb-server
```
![Image description](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%208/Assets/Screenshot%20(20).png)

## Install utility untuk install composer
Sebelum install composer perlu diinstall utility terlebih dahulu
```console
sudo apt install php-cli php-mbstring git unzip
```
![Image description](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%208/Assets/Screenshot%20(21).png)
        
## Download composer.phar
jalankan perintah berikut untuk lakukan instalasi composer:
```console
curl -sS https://getcomposer.org/installer | php
```
serta lakukan pemindahan file agar dapat menjadi bagian dari linux:
```console
sudo mv composer.phar /usr/local/bin/composer
```
![Image description](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%208/Assets/Screenshot%20(22).png)

## Cek version
cek version ini juga bisa untuk mengetahui apakah composer terinstall di perangkat:
```console
composer --version
```
![Image description](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%208/Assets/Screenshot%20(23).png)

