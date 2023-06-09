# Mail Server

## 1 Install postfox
sebelumnya pastikan apache2 telah terinstall, barulah lakukan instalasi postfix
```
sudo apt install postfix
```

## 2 Konfigurasi
ubah lah konfigurasi menjadi seperti dibawah ini 
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# See http://www.postfix.org/COMPATIBILITY_README.html -- default to 2 on
# fresh installs.
compatibility_level = 2

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_security_level=may

smtp_tls_CApath=/etc/ssl/certs
smtp_tls_security_level=may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = kelompok7
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = kelompok7, kampus-07.takehome.com, debian, localhost.localdomain, localhost, mail.kampus-07.takehome.com
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 0.0.0.0/0
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
```

## 3 Install dan Konfigurasi Dovecot
jalankan command berikut untuk instalasi
```
sudo apt install dovecot-imapd dovecot-pop3d
```

selanjutnya konfigurasi dovecot
```
sudo nano /etc/dovecot/dovecot.conf
```

uncomment code berikut
```
# from
#listen = *, ::

# to
listen = *
```

konfigurasi juga file `/etc/dovecot/conf.d/10-auth.conf`
```
sudo nano /etc/dovecot/conf.d/10-auth.conf
```
uncomment dan ganti yes menjadi no
```
# connection is considered secure and plaintext authentication is allowed.
# See also ssl=required setting.
disable_plaintext_auth = no
```

konfigurasi juga file `/etc/dovecot/conf.d/10-mail.conf`
```
sudo nano /etc/dovecot/conf.d/10-mail.conf
```

Uncomment code yang:
```
mail_location = maildir:~/Maildir
```
dan comment code yang:
```
mail_location = mbox:~/mail:INBOX=/var/mail/%u
```

lakukan restart dovecot
```
sudo systemctl restart dovecot
```

## 4 Menambahkan email
untuk membuat email jalankan command berikut:
```
sudo adduser b
```
lakukan restart postfix dan dovecot
```
sudo systemctl restart postfix dovecot
```

## 5 testing menggunakan telnet
Install telnet
```
sudo apt install telnet
```
setelah install, coba jalankan code berikut untuk mengirimkan email
```
telnet mail.kampus-07.takehome.com 25
```
Contoh mengirim email
![send email](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2012/assets/SENT%20MAIL.png)

contoh penerima email
![receive email](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%2012/assets/receive%20mail.png)
