### Anggota Tim:
1. 3121600007 - Muhammad Rizal
2. 3121600008 - Mochammad Rizal
3. 3121600021 - Muhammad Faishal Nabhan
### Kelas : 2 D4 Informatika A 2021

# Installasi Web server
## 1. Aturlah wifi + setting VMware
- Setting VMware network menjadi Bridge
![setting VMware](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2010/Assets/1.png)
- Setting wifi pada linux (Debian)
![setting wifi](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2010/Assets/2.png)
## 2. Install php
- _Copas_-lah perintah berikut pada terminal linux
```
sudo apt install apache2
```
- Cek versi yang diinstall
```
php -version
```
![php](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2010/Assets/3.png)
## 3. Install utility + composer
- Gunakan perintah berikut untuk install utility
```
sudo apt install php-cli php-mbstring git unzip
```
- Install Composer
```
curl -sS https://getcomposer.org/installer | php
```
- pindahkan file composer agar bisa terbaca
```
sudo mv composer.phar /usr/local/bin/composer
```
- Cek hasilnya
```
composer --version
```
![composer](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2010/Assets/4.png)

## 4. Install Laravel
- Pindah directory
```
cd /var/www/html
```
- Lakukan instalasi laravel
```
composer create-project --prefer-dist laravel/laravel:^7.0 blog
```
*Note* : blog adalah nama folder laravel
- Jalankan perintah berikut
```
sudo chgrp -R www-data /var/www/html/example/
sudo chmod -R 775 /var/www/html/example/storage
```
- Buat configurasi laravel
```
cd /etc/apache2/sites-available
sudo nano laravel_project.conf
```
- Salin code dibawah ini untuk configurasinya:
```
<VirtualHost *:80>
   ServerName www.kampus-07.takehome.com
   ServerAdmin webmaster@kampus-07.takehome.com
   DocumentRoot /var/www/html/blog/public

   <Directory /var/www/html/blog>
       AllowOverride All
   </Directory>
   ErrorLog ${APACHE_LOG_DIR}/error.log
   CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
- Cara cek error
```
cd /var/log/apache2
cat error.log
```
![cek error php](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2010/Assets/5.png)

## Berikut hasilnya
- Laravel sudah berjalan namun masih error, kemungkinan ada diizin akses VM 
![cek error php](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2010/Assets/6.jpeg)
