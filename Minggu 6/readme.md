# Konfigurasi DNS Server pada Linux

Dosen pengampu : Dr. Ferry Astika Saputra. S.T, M.Sc.

Kelompok 7
Anggota : 
- 3121600007 Muhammad Rizal
- 3121600008 Mochammad Rizal
- 3121600021 Muhammad Faishal Nabhan

## Jenis - jenis DNS Record
DNS Record adalah entitas yang ada dalam sistem DNS yang menyimpan informasi tentang domain dan layanan yang terkait dengan domain tersebut. Berikut adalah beberapa jenis DNS Record yang umum dijumpai:
1. A Record: Menyimpan alamat IP terkait dengan nama domain. Digunakan untuk menghubungkan nama domain ke alamat IP yang sesuai.
2. CNAME Record: Menyimpan alias untuk nama domain. Digunakan untuk membuat entri yang mengarahkan domain ke domain lain atau subdomain.
3. MX Record: Menyimpan informasi tentang server mail exchange untuk nama domain. Digunakan untuk mengarahkan pengiriman email ke server email yang benar untuk domain tersebut.
4. TXT Record: Menyimpan teks arbitrer yang terkait dengan nama domain. Digunakan untuk menyimpan informasi tambahan seperti verifikasi DNS, SPF (Sender Policy Framework), dan lainnya.
5. NS Record: Menyimpan informasi tentang server nama (name server) yang bertanggung jawab untuk zona domain. Digunakan untuk mengarahkan permintaan DNS ke server yang benar.
6. AAAA Record: Menyimpan alamat IPv6 terkait dengan nama domain. Mirip dengan A Record, tetapi untuk IPv6.
7. SRV Record: Menyimpan informasi tentang layanan yang tersedia dalam domain. Digunakan untuk mengarahkan permintaan ke server yang menyediakan layanan spesifik, seperti VoIP atau layanan pesan instan.
8. PTR Record: Menyimpan rekaman kebalikan untuk resolusi DNS. Digunakan untuk menghubungkan alamat IP ke nama domain yang sesuai.
9. SOA Record: Menyimpan informasi tentang server otoritatif (authoritative server) untuk zona domain. Digunakan untuk mengelola informasi dan konfigurasi yang terkait dengan zona.
10. SPF Record: Menyimpan kebijakan pengirim (sender policy) untuk domain. Digunakan untuk memverifikasi pengiriman email dan mencegah email spoofing.

## Langkah - langkah
1. melakukan update dan upgrade pada linux agar mendapatkan daftar paket terbaru
```
sudo apt-get update
sudo apt-get upgrade
```
2. menginstal package bind9 dan bind9utils
```
sudo apt-get install bind9 bind9utils
```
3. configurasi named.conf

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%206/assets/namedconf.png)

4. configurasi dns server (named.conf.local)

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%206/assets/namedconflocal.png)

5. configurasi  forward

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%206/assets/forward.png)

6. configurasi reverse

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%206/assets/reverse.png)

7. configurasi resolve

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%206/assets/resolvconf.png)

8. configurasi resolve

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%206/assets/namedconfoptions.png)
![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%206/assets/namedconfoptions2.png)

9. testing

![](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%206/assets/testing.png)
