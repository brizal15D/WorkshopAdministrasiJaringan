# Web Mail
## 1. Installasi Mariadb dan Roundcube
1. jalankan perintah berikut untuk menginstall mariadb dan roundcube
```
sudo apt install mariadb-server roundcube
```
klik yes:

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2013/assets/157.png)

Masukkan password, wajib dan minimal 4 karakter

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2013/assets/158.png)

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2013/assets/159.png)

2. edit file config.inc.php
```
sudo nano /etc/roundcube/config.inc.php
```
3. Isikan default host dengan nama domain mail server.
```
// For example %n = mail.domain.tld, %t = domain.tld
$config['default_host'] = 'mail.kampus-07.takehome.com';
```
4. Ganti smtp server dengan nama domain mail server.
```
// For example %n = mail.domain.tld, %t = domain.tld
$config['smtp_server'] = 'mail.kampus-05.takehome.com';
```
5. Ganti smtp port dari 587 ke 25.
```
// SMTP port. Use 25 for cleartext, 465 for Implicit TLS, or 587 for STARTTLS (default)
$config['smtp_port'] = 25;
```
6. Kosongkan value dari smtp user.
```
// will use the current username for login
$config['smtp_user'] = '';
```
7. Kosongkan value dari smtp password.
```
// will use the current user's password for login
$config['smtp_pass'] = '';
```
8. Configure ulang roundcube (langkah ini bisa dilewati).
```
sudo dpkg-reconfigure roundcube-core
```
9. Kosongkan karena kita tidak menggunakan tls.

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2013/assets/160.png)

10. Pilih bahasa untuk roundcube.

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2013/assets/161.png)

11. Pilih no jika tidak ingin reinstall database yang telah dibuat.

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2013/assets/162.png)

12. Check pada pilihan apache dan uncheck lighttpd.

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2013/assets/163.png)

13. Pilih yes untuk merestart web server.

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2013/assets/164.png)

14. Edit apache config untuk memasukkan konfigurasi tambahan dari roundcube ke apache config.
```
sudo nano /etc/apache2/apache2.conf
```
Tambahkan pada baris paling bawah.
```
Include /etc/roundcube/apache.conf
```
15. Selanjutnya, masuk ke directory website apache dan tambahkan file baru untuk mail server.
```
cd /etc/apache2/sites-available
sudo touch mail.conf
sudo nano mail.conf
```
isikan file itu dengan command dibawah ini
```
<VirtualHost *:80>
    ServerName mail.kampus-07.takehome.com
    DocumentRoot /usr/share/roundcube
</VirtualHost>
```
dan save
16. Disable apache default config dan enable kan mail config.
```
a2dissite 000-default.conf
a2ensite mail.conf
```
17. Restart apache service.
```
systemctl restart apache2
```

## 2. Testing
Setelah membuka web browser di sisi klien, navigasikan ke domain mail server yang sesuai. Kemudian, tampilan antarmuka Roundcube akan muncul. Anda dapat melihat dan mengakses kotak surat elektronik melalui antarmuka ini.

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2013/assets/165.png)

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2013/assets/166.png)

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2013/assets/167.png)
