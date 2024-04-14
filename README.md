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

### A. Persiapan

1. Setup terlebih dahulu mail server pada konfigurasi zone sehingga dapat di resolve ```mail.kelompok2.local```

    > ![alt text](image-1.png)
    > forward

    >![alt text](image-2.png)
    > inverse

2. nslookup

    > ![alt text](image-3.png)


### B. Setup NTP ( Network Time Protocol )

1. Installasi Paket dengan command ``sudo apt install systemd-timesyncd``

2. Ubah TimeZone ke Asia/Jakarta

3. Buat RTC menjadi sama dengan UTC

4. Aktifkan NTP supaya waktu Sinkron

    > ![alt text](<Screenshot 2024-04-14 024813.png>)

5. Ubah config file ``timesync.d``, buat pool ke terdekat supaya delay jadi pendek.

    > ![alt text](image-4.png)

    > List NTP Indonesia https://www.ntppool.org/zone/id

6. Restart Service yang berjalan dan cek statusnya

    > ![alt text](<Screenshot 2024-04-14 025009.png>)

7. Cek Tanggal

    > ![alt text](<Screenshot 2024-04-14 025028.png>)

### C. Install Web Server ( APACHE2 + PHP-FM )

#### +  Install Apache2
1. Install paket dengan command berikut ``sudo apt -y install apache2``

    > ![alt text](<Screenshot 2024-04-14 025102.png>)


2. Ubah ServerToken Menjadi Prod gunakan Text Editor seperti Nano

    > ![alt text](<Screenshot 2024-04-14 030245.png>)
    > sudo nano /etc/apache2/conf-enabled/security.conf

3. Tambahkan Directory yang dapat diakses

    > ![alt text](<Screenshot 2024-04-14 030341.png>)
    > sudo nano /etc/apache2/mods-enabled/dir.conf

4. Tambahkan ServerName

    > ![alt text](<Screenshot 2024-04-14 030838.png>)
    > sudo nano /etc/apache2/apache2.conf

5. Webmaster email

    > ![alt text](<Screenshot 2024-04-14 031039.png>)
    > sudo nano /etc/apache2/sites-enabled/000-default.conf

6. Reload service apache2

    > ![alt text](<Screenshot 2024-04-14 031100.png>)

7. Cek apakah webserver berjalan pada browser kita

    > ![alt text](<Screenshot 2024-04-14 032124.png>)

#### + Install PHP 8.2

1. Install dengan perintah berikut

    > ![alt text](<Screenshot 2024-04-14 032433.png>)
    > sudo apt -y install php8.2 php8.2-mbstring php-pear

2. Cek apakah sudah terinstall

    > ![alt text](<Screenshot 2024-04-14 032735.png>)

3. Buat sebuah file php untuk memeriksa apakah PHP Berjalan/Fungsi

    > ![alt text](<Screenshot 2024-04-14 032957.png>)

4. Jalankan

    > ![alt text](<Screenshot 2024-04-14 033008.png>)


#### + Install PHP FM

1. Install dengan perintah berikut

    > ![alt text](<Screenshot 2024-04-14 033132.png>)

2. Lakukan Konfigurasi pada file apache untuk PHP-FM

    > ![alt text](<Screenshot 2024-04-14 033350.png>)
    > sudo nano /etc/apache2/sites-available/default-ssl.conf

3. setenvif pada ae2enmod proxy_fcgi
4. load config

    > ![alt text](<Screenshot 2024-04-14 033509.png>)

5. Jalankan ulang Servicenya 

    > ![alt text](<Screenshot 2024-04-14 033534.png>)

6. Test kedalam webserver, buat file info.php

    > ![alt text](<Screenshot 2024-04-14 033722.png>)
    > sudo echo '<?php phpinfo(); ?>' > /var/www/html/info.php

7. cek pada web

    > ![alt text](<Screenshot (1669).png>)
    > berhasil


### D. Install Database server ( Mariadb-Server )

1. Install paket dengan perintah berikut

    > ![alt text](<Screenshot 2024-04-14 033801.png>)
    > sudo apt -y install mariadb-server

2. Pastikan atau ubah charset ke utf8mb4, lalu restart service mariadb

    > ![alt text](<Screenshot 2024-04-14 034101.png>)
    > sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf

3. Lakukan installasi dengan perintah ``sudo mysql_secure_installation``

    > ![alt text](<Screenshot 2024-04-14 034235.png>)

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

    > ![alt text](<Screenshot 2024-04-14 034429.png>)

5. Cek akses user root

    > ![alt text](<Screenshot 2024-04-14 034505.png>)

6. Cek daftar user pada database user

    > ![alt text](<Screenshot 2024-04-14 034530.png>)

7. Lihat semua database

    > ![alt text](<Screenshot 2024-04-14 034555.png>)

8. Berarti mysql sudah terinstall, coba buat sebuah dummy database dan table untuk menjalankan beberapa query crud

    > ![alt text](<Screenshot 2024-04-14 034806.png>)

9. Berhasil dan Database mariadb sudah terinstall.



#### E. Install POSTFIX mailserver (SMTP Server)

1. Install dengan perintah ``sudo nano apt -y install postfix sasl2-bin``
2. Pilih yang No Configuration ( kita config manual )
    > ![alt text](<Screenshot (1650).png>)

3. Copy file config /usr/share/postfix/main.cf.dist ke /etc/postfix/main.cf

    > ![alt text](<Screenshot 2024-04-14 035106.png>)

4. Ubah beberapa Konfigurasi pada file postfix main.cf

    > ![alt text](<Screenshot (1651).png>)
    > ![alt text](<Screenshot (1652).png>)
    > ![alt text](<Screenshot (1653).png>)
    > ![alt text](<Screenshot (1654).png>)
    > ![alt text](<Screenshot (1655).png>)
    > ![alt text](<Screenshot (1656).png>)
    > ![alt text](<Screenshot (1657).png>)
    > ![alt text](<Screenshot (1658).png>)
    > ![alt text](<Screenshot (1659).png>)
    > ![alt text](<Screenshot (1660).png>)
    > ![alt text](<Screenshot (1661).png>)

5. Tambahkan config anti spam
    > ![alt text](<Screenshot (1662).png>)


### F. Install DOVECOT (IMAP POP3)

1. Gunakan Perintah berikut untuk installasi `sudo  apt -y install dovecot-core dovecot-pop3d dovecot-imapd`

    > ![alt text](<Screenshot 2024-04-14 040547.png>)


2. Ubah listen IP
    > ![alt text](<Screenshot (1664).png>)

3. Setting file auth   

    > ![alt text](<Screenshot (1663).png>)

4. Konfigurasi file mail

    > ![alt text](<Screenshot (1665).png>)

5. Terakhir tambahkan mode 0666, dan user,group postfix pada file master

    > ![alt text](<Screenshot (1666).png>)

6. Restart service, dan cek di netstat

    > ![alt text](<Screenshot (1668).png>)


Setelah beberapa paket terinstall seperti imap, pop3 kita akan coba melakukan test connection ke postfix

1. dengan perintah `telnet mail.kelompok2.local`

    > ![alt text](<Screenshot 2024-04-14 195925.png>)

2. Coba test kirim ke user reza

    > ![alt text](image-5.png)

### G. DEBIAN EVOLUTION

1. Buat User Terlebih dahulu disini kita buat user default kita di saya yaitu
``user``

    > Identitiy
    > ![alt text](image-6.png)

    > Recieve
    > ![alt text](image-7.png)

    > Sending ( Port 25 )
    > ![alt text](image-8.png)

2. user telah dibuat sekarang buat user lagi (dummy) untuk saya, ``reza`` dengan langkah yang sama.

3. Mengirim pesan

    > ![alt text](image-9.png)

4. cek Inbox user `reza`

    > ![alt text](image-11.png)

    terdapat email dari user dan budi yang kita lakukan di telnet tadi!.
    berhasil!.


### H. ROUNDCUBE