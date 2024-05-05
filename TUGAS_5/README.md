# DAFTAR TUGAS AKAN SAYA TAMPILKAN PADA BAGIAN INI
| TUGAS | FILE |
| ------| -----|
| [TUGAS 1](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS1.md) |  _[FILE](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS1.md)_ |
| [TUGAS 2](#tugas-2) | _[FILE](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_2/README.md)_ , _[MARP CLICK](TUGAS_2/PPT_SYSADMIN.md)_, _[PDF MARP](TUGAS_2/PPT_SYSADMIN.pdf)_|
| [TUGAS 3](#tugas-3) | _[FILE](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_3/README.md)_|
| [TUGAS 4](#tugas-4) | _[FILE](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/README.md)_|
| [TUGAS 5](#tugas-5) | _[FILE](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/README.md)_|

----


# MAIL SERVER DEBIAN 10, BIND9, POSTFIX, DOVECOT, Client Evolution, RoundCube.

### Daftar Isi
- [A. Persiapan](#a-persiapan)
- [B. Setup NTP Server](#b-setup-ntp--network-time-protocol)
- [C. Install WebServer Apache2](#c-install-web-server--apache2--php-fm)
- [D. Install Database Server MariaDb](#d-install-database-server--mariadb-server)
- [E. Install SMTP Sever Postfix](#e-install-postfix-mailserver-smtp-server)
- [F. Install IMAP POP3 Doveco (telnet)](#f-install-dovecot-imap-pop3)
- [G. Testing Dengan Debian Evolution](#g-debian-evolution)
- [H. RoundCube Email Client](#h-roundcube)
###### Tambahan
- [I. MailServer JARKOM C307 (Network)](#i-percobaan-mailserver-jaringan-jarkom-c307)
###### Tambahan Minggu 10
- [J. Analisis Header Pada Email](#i-analisis-header-email)

### A. Persiapan

1. Setup terlebih dahulu mail server pada konfigurasi zone sehingga dapat di resolve ```mail.kelompok2.local```

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-1.png)
    > forward

    >![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-2.png)
    > inverse

2. nslookup

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-3.png)


### B. Setup NTP ( Network Time Protocol )

1. Installasi Paket dengan command ``sudo apt install systemd-timesyncd``

2. Ubah TimeZone ke Asia/Jakarta

3. Buat RTC menjadi sama dengan UTC

4. Aktifkan NTP supaya waktu Sinkron

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 024813.png>)

5. Ubah config file ``timesync.d``, buat pool ke terdekat supaya delay jadi pendek.

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-4.png)

    > List NTP Indonesia https://www.ntppool.org/zone/id

6. Restart Service yang berjalan dan cek statusnya

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 025009.png>)

7. Cek Tanggal

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 025028.png>)

### C. Install Web Server ( APACHE2 + PHP-FM )

#### +  Install Apache2
1. Install paket dengan command berikut ``sudo apt -y install apache2``

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 025102.png>)


2. Ubah ServerToken Menjadi Prod gunakan Text Editor seperti Nano

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 030245.png>)
    > sudo nano /etc/apache2/conf-enabled/security.conf

3. Tambahkan Directory yang dapat diakses

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 030341.png>)
    > sudo nano /etc/apache2/mods-enabled/dir.conf

4. Tambahkan ServerName

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 030838.png>)
    > sudo nano /etc/apache2/apache2.conf

5. Webmaster email

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 031039.png>)
    > sudo nano /etc/apache2/sites-enabled/000-default.conf

6. Reload service apache2

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 031100.png>)

7. Cek apakah webserver berjalan pada browser kita

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 032124.png>)

#### + Install PHP 8.2

1. Install dengan perintah berikut

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 032433.png>)
    > sudo apt -y install php8.2 php8.2-mbstring php-pear

2. Cek apakah sudah terinstall

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 032735.png>)

3. Buat sebuah file php untuk memeriksa apakah PHP Berjalan/Fungsi

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 032957.png>)

4. Jalankan

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 033008.png>)


#### + Install PHP FM

1. Install dengan perintah berikut

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 033132.png>)

2. Lakukan Konfigurasi pada file apache untuk PHP-FM

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 033350.png>)
    > sudo nano /etc/apache2/sites-available/default-ssl.conf

3. setenvif pada ae2enmod proxy_fcgi
4. load config

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 033509.png>)

5. Jalankan ulang Servicenya 

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 033534.png>)

6. Test kedalam webserver, buat file info.php

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 033722.png>)
    > sudo echo '<?php phpinfo(); ?>' > /var/www/html/info.php

7. cek pada web

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1669).png>)
    > berhasil


### D. Install Database server ( Mariadb-Server )

1. Install paket dengan perintah berikut

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 033801.png>)
    > sudo apt -y install mariadb-server

2. Pastikan atau ubah charset ke utf8mb4, lalu restart service mariadb

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 034101.png>)
    > sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf

3. Lakukan installasi dengan perintah ``sudo mysql_secure_installation``

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 034235.png>)

    Installasi pattern

    
       Enter current password for root (enter for none): Tekan Enter

       Switch to unix_socket authentication [Y/n] n

       Change the root password? [Y/n] n

       Remove anonymous users? [Y/n] y

       Disallow root login remotely? [Y/n] y

       Remove test database and access to it? [Y/n] y

       Reload privilege tables now? [Y/n] y

    Pastikan sama sehingga langkah tetap sama.

4. Masuk kedalam mysql perintah    `mysql`

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 034429.png>)

5. Cek akses user root

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 034505.png>)

6. Cek daftar user pada database user

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 034530.png>)

7. Lihat semua database

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 034555.png>)

8. Berarti mysql sudah terinstall, coba buat sebuah dummy database dan table untuk menjalankan beberapa query crud

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 034806.png>)

9. Berhasil dan Database mariadb sudah terinstall.



#### E. Install POSTFIX mailserver (SMTP Server)

1. Install dengan perintah ``sudo nano apt -y install postfix sasl2-bin``
2. Pilih yang No Configuration ( kita config manual )
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1650).png>)

3. Copy file config /usr/share/postfix/main.cf.dist ke /etc/postfix/main.cf

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 035106.png>)

4. Ubah beberapa Konfigurasi pada file postfix main.cf

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1651).png>)
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1652).png>)
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1653).png>)
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1654).png>)
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1655).png>)
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1656).png>)
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1657).png>)
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1658).png>)
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1659).png>)
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1660).png>)
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1661).png>)

5. Tambahkan config anti spam
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1662).png>)
    > sudo newaliases


### F. Install DOVECOT (IMAP POP3)

1. Gunakan Perintah berikut untuk installasi `sudo  apt -y install dovecot-core dovecot-pop3d dovecot-imapd`

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 040547.png>)


2. Ubah listen IP
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1664).png>)

3. Setting file auth   

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1663).png>)

4. Konfigurasi file mail

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1665).png>)

5. Terakhir tambahkan mode 0666, dan user,group postfix pada file master

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1666).png>)

6. Restart service, dan cek di netstat

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1668).png>)


Setelah beberapa paket terinstall seperti imap, pop3 kita akan coba melakukan test connection ke postfix

1. dengan perintah `telnet mail.kelompok2.local`

    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot 2024-04-14 195925.png>)

2. Coba test kirim ke user reza

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-5.png)

### G. DEBIAN EVOLUTION

1. Buat User Terlebih dahulu disini kita buat user default kita di saya yaitu
``user``

    > Identitiy
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-6.png)

    > Recieve
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-7.png)

    > Sending ( Port 25 )
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-8.png)

2. user telah dibuat sekarang buat user lagi (dummy) untuk saya, ``reza`` dengan langkah yang sama. adduser terlebih dahulu
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/Screenshot (1672).png>)

3. Mengirim pesan

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-9.png)

4. cek Inbox user `reza`

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-11.png)

    terdapat email dari user dan budi yang kita lakukan di telnet tadi!.
    berhasil!.


### H. ROUNDCUBE

1. Sebelum itu kita perlu melakukan Konfigurasi untuk user roundcube, tambahkan pada tabel db user

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-12.png)

2. Berikan full access

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-13.png)
    
    Load
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-14.png)

3. Install Roundcube paket dengan perintah berikut

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-15.png)

4. Pilih Yes
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-16.png)

5. Masukkan password tadi ( 123 )

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-17.png)

6. Lakukan config pada file `/etc/roundcube/config.inc.php`

7. Samakan dengan config berikut
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-19.png)
8. Kemudian konfigurasi file apache pada roundcube, uncomment line 3 dan hapus public_html path

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-20.png)

9. pada apache2 default conf tambahkan Servername untuk mail dan document root menjadi roundcube ``sudo nano /etc/apache2/sites-available/000-default.conf``, Servername mail.kelompok2.local DocumentRoot /var/lib/roundcube/
    
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-21.png)

10. jalankan rekonfigurasi seperti berikut

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-22.png)
    
    Ok

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-24.png)

    en_Us

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-25.png)

    Pilih Install ulang ( YES 
    
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-26.png)

    Pilih TCP IP

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-27.png)

    Pilih localhost

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-28.png)

    Port 3306

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-29.png)

    Pilih native password

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-30.png)

    Database name default

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-31.png)

    Username default

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-32.png)

    Password 123

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-33.png)

    Admin root

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-34.png)

    Pilih webserver apache2

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-35.png)

    Restart dan keep curently installed

11. Roundcube terinstall

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-36.png)

12. Login dengan user debian kita saya user > user, bisa kita lihat config evolution sudah terload pada roundcube saya

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-37.png)

13. Coba mengirim dari user ke Reza

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-38.png)

14. Login sebagai user `reza`

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets/image-39.png)
    Email diterima

### I. PERCOBAAN MAILSERVER JARINGAN JARKOM C307 


1. Pastikan sudah terhubung dengan Ethernet Pada LAB JARKOM

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/g1.png)
2. Lakukan Ping ke 1.1.1.1 pastikan sudah terhubung ke dns 1.1.1.1
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/image.png)

3. Setting Virtual Box Ke Dalam **Network Bridge**

    > settings/machine > Network 
    >
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/image-1.png)

4. Supaya DNS Kita dapat diresolve oleh kelompok lain lakukan Konfigurasi Berikut

    > **Setting interfaces**
    >
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/image-5.png)
    >sudo nano /etc/network/interfaces

    > **Setting named.conf**
    >
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/image-3.png)
    > sudo nano /etc/bind/named.conf.options

    > **Setting resolv.conf**
    >
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/image-4.png)
    > sudo nano /etc/resolv.conf


    Lakukan *sudo restart systemctl networking* Setelahnya

5. Lakukan Ping Detik.com atau IP Kelompok lain disini 192.168.10.10

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/image-2.png)

6. Buat DHCP Server Bridge Pada Aplikasi WINBOX

    >   Connect Ke Server/Router Klik DHCP SETUP, Pilih Bridge Interface
    >
    >   ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/Screenshot 2024-04-22 161942.png>)

    >   Next (Default)
    >
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/Screenshot 2024-04-22 161951.png>)
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/Screenshot 2024-04-22 161958.png>)
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/Screenshot 2024-04-22 162005.png>)
    >  Masukkan dns
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/Screenshot 2024-04-22 162024.png>)
    > Default
    > ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/Screenshot 2024-04-22 162030.png>)

    >   ![alt text](<https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/Screenshot 2024-04-22 161914.png>)

7. Cek Mail Server

    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/image-6.png)
    > nslookup -q=MX kelompok2.local

8. Buka Mail Server Kelompok Kita

    > Lakukan Pengiriman Ke Kelompok Lainnya
    >
    > ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/assets2/image-7.png)


### J. Analisis Header Email


1. Message Header Pada Email dengan attachment IMAGE

    ![alt text](image.png)

    >**Return-Path** adalah alamat email yang digunakan untuk mengirim balik pesan jika terjadi kesalahan pengiriman.

    Dalam kasus ini, alamatnya adalah syahrul@mail.kelompok4.local.

    > **X-Original-To dan Delivered-To** adalah alamat email tujuan asli dan alamat email tujuan akhir. 
    
    Keduanya adalah user@mail.kelompok2.local.


    >**Received** adalah catatan dari setiap server mail yang telah dilewati pesan ini. 
    
    Dalam kasus ini, pesan ini diterima dari mail.kelompok4.local oleh mail.kelompok2.local.

    >**MIME-Version** adalah versi dari MIME yang digunakan dalam pesan ini. 
    
    Dalam kasus ini, versinya adalah 1.0.
    
    >**Date** adalah tanggal dan waktu ketika pesan ini dikirim. 
    
    Dalam kasus ini, pesan ini dikirim pada Senin, 22 April 2024 pukul 18:55:37 WIB.

    >**From** adalah pengirim pesan. 
    
    Dalam kasus ini, pengirimnya adalah syahrul@mail.kelompok4.local.

    >**To** adalah penerima pesan. 
    
    Dalam kasus ini, penerimanya adalah beberapa alamat email.

    >**Subject** Ini adalah subjek atau topik dari pesan. 
    
    Dalam kasus ini, subjeknya adalah “HALO AKU SYAHRUL”.

    >**User-Agent** adalah aplikasi yang digunakan untuk mengirim pesan. 
    
    Dalam kasus ini, aplikasinya adalah Server World Webmail.

    >**Message-ID** adalah ID unik dari pesan ini. 
    
    Dalam kasus ini, ID pesannya adalah **c0ac3e66bdd6cc9289f967a58bce0502@mail.kelompok4.local.**

    >**X-Sender** adalah alamat email pengirim asli. 
    
    Dalam kasus ini, alamatnya adalah syahrul@mail.kelompok4.local.

    >**Content-Type** adalah tipe konten dari pesan ini. 
    
    Dalam kasus ini, tipe kontennya adalah multipart/mixed, yang berarti pesan ini mengandung beberapa bagian dengan tipe konten yang berbeda. “boundary” adalah string yang digunakan untuk memisahkan setiap bagian.

    #### Lalu Apa Itu multipart/mixed ?

    Dalam konteks email, `multipart/mixed` adalah jenis `Content-Type` yang digunakan ketika sebuah pesan email terdiri dari beberapa bagian dengan tipe data yang berbeda. Setiap bagian dalam pesan ini dipisahkan oleh sebuah batas (boundary), yang merupakan string teks.

    Misalnya, jika sebuah email memiliki lampiran, maka `Content-Type`-nya adalah `multipart/mixed`. Dalam kasus ini, teks pesan dan setiap lampiran menjadi bagian terpisah dari konten pesan, masing-masing dengan `Content-Type`-nya sendiri. Jika tidak ada lampiran, `Content-Type` pesan adalah `Text/Plain`, dan tubuh pesan hanya terdiri dari satu bagian.

    Secara umum, `multipart/mixed` digunakan untuk menggabungkan beberapa format data ke dalam satu pesan. Misalnya, sebuah pesan email dapat berisi teks, gambar, dan dokumen lainnya, masing-masing sebagai bagian terpisah dalam pesan yang sama.
