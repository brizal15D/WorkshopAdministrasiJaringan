# Projek Konfigurasi DNS
3121600021 Muhammad Faishal Nabhan   
3121600008 Mochammad Rizal
3121600007 Muhammad Rizal	


## **I** Reset Konfigurasi Router - 7
1. Install winbox pada komputer yang digunakan
2. Akses System -> pilih Reset Configuration -> centang No Default Configuration -> klik Reset Configuration
3. Tunggu hingga Router tereset

## **II** Config IP Local & Public

Pilih menu IP -> Addresses -> klik tombol "**+**" -> **ETHER 1**

**ETHER 1**

 - Address = 10.252.108.17
 - Network = 10.252.108.0
 - Interface = ETHER 1

**ETHER 2**
-   Address = 192.168.7.1/24
-   Network = 192.168.7.1/24
-   Interface = ETHER 2

![IP Lokal & public](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%203/assets/IP%20lokal%20%26%20public.png)

## **III** Config Default Route

Akses fitur di sidebar pada menu New Terminal

Configurasi Default Route

    ip route add dst-address=0.0.0.0/0 gateway=10.252.108.1
    ip ro pr
![Config default route](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%203/assets/Screenshot%202023-03-10%20151932%20(2).png)
## **IV**. Configurasi DNS

Akses fitur di sidebar pada menu IP -> DNS -> masukkan IP Server=202.9.85.3

![Configurasi DNS](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%203/assets/dns.png)

## **V** Config Internet Client

Berikut adalah configurasi Internet Client
![DHCP](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%203/assets/dhcp%20server.png)

## **VI** Menambah IP Routes

Ketikkan pada New Terminal Winbox

    ip ro add gateway 10.252.108.12 dst 192.168.2.0/24
    ip ro add gateway 10.252.108.13 dst 192.168.3.0/24
    ip ro add gateway 10.252.108.14 dst 192.168.4.0/24
    ip ro add gateway 10.252.108.15 dst 192.168.5.0/24
    ip ro add gateway 10.252.108.16 dst 192.168.6.0/24
    ip ro add gateway 10.252.108.17 dst 192.168.7.0/24
    ip ro add gateway 10.252.108.19 dst 192.168.9.0/24
![Router list](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%203/assets/Config%20default%20route%20%26%20routing%20table.png)

## **VII** Tes ping antar client
![Ping](https://raw.githubusercontent.com/rizal15D/WorkshopAdministrasiJaringan/main/Minggu%203/assets/pingg.png)
## **VIII** Dokumentasi

[Dokumentasi](https://drive.google.com/file/d/1NXB4yPU9dC1U83fsOYPHV4S4TIG1pC6E/view?usp=share_link)


