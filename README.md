# DAFTAR TUGAS AKAN SAYA TAMPILKAN PADA BAGIAN INI
| TUGAS | FILE |
| ------| -----|
| [TUGAS 1](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS1.md) |  _[FILE](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS1.md)_ |
| [TUGAS 2](#tugas-2) | _[FILE](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_2/README.md)_ , _[MARP CLICK](TUGAS_2/PPT_SYSADMIN.md)_, _[PDF MARP](TUGAS_2/PPT_SYSADMIN.pdf)_|
| [TUGAS 3](#tugas-3) | _[FILE](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_3/README.md)_|
| [TUGAS 4](#tugas-4) | _[FILE](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/README.md)_|
| [TUGAS 5](#tugas-5) | _[FILE](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_5/README.md)_|
| [TUGAS 6](#tugas-6) | _[FILE](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/README.md)_|

----

## Daftar Isi
- [A. Web Server and Web Browser Architecture](#a-web-server-and-web-browser-architecture)

- [B. Containerized Web Server Using Docker]() `New `
- [C. Apache2 + Dns Resolver + Docker Uptime Kuma Package]() `New `

# A. Web Server and Web Browser Architecture 


![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/webserver.png)

Ketika pengguna memasukkan alamat web server ke dalam bilah alamat browser Chrome, browser mengirimkan permintaan HTTP ke alamat yang dituju. Permintaan ini mencakup informasi tentang jenis permintaan yang dibuat (seperti GET atau POST) dan alamat yang diminta, serta header permintaan lainnya. Web server yang dituju menerima permintaan ini di port yang sesuai (biasanya port 80 untuk HTTP dan 443 untuk HTTPS) dan memprosesnya. 

Setelah memproses permintaan, server menghasilkan respons HTTP yang berisi informasi yang diminta, seperti halaman web atau data lainnya, bersama dengan kode status HTTP yang sesuai. Browser Chrome menerima respons ini dan memprosesnya, merender halaman web sesuai dengan HTML, CSS, dan JavaScript yang diterima. Konten yang diterima kemudian ditampilkan kepada pengguna.


![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/app.png)


## Apa Bedanya Antara Server Aplikasi dan Server Web?
Server aplikasi dan server web memiliki peran yang serupa namun dengan perbedaan tertentu yang perlu dipahami.

Server aplikasi menggunakan lebih dari sekadar protokol HTTP. Mereka bisa bekerja dengan berbagai jenis program selain halaman web. Selain itu, server aplikasi biasanya menawarkan kemampuan tambahan yang memperluas fungsionalitasnya.

Di sisi lain, server web memiliki fungsi utama yang lebih terbatas. Mereka secara khusus menjalankan permintaan HTTP untuk menampilkan halaman web. Meskipun demikian, server web juga bisa menyediakan fitur tambahan seperti penyimpanan sementara dan permintaan dasar.

Situs web dan aplikasi yang menggunakan server aplikasi sering membutuhkan fitur yang tidak disediakan oleh server web biasa. Misalnya, server aplikasi memungkinkan transaksi, personalisasi, dan layanan pesan, yang menjadi semakin penting untuk berbagai jenis situs web.

Tidak jarang server web menjadi bagian dari server aplikasi. Ini karena server web seringkali merupakan komponen penting dari layanan yang disediakan oleh server aplikasi. Ketika seseorang membicarakan server aplikasi, sering kali juga dimaksudkan sebagai server web.

Saat pengguna mengetikkan URL ke dalam browser, server web menyajikan konten yang sama tidak peduli dari mana pengguna tersebut atau perangkat apa yang digunakannya. Meskipun demikian, halaman web dengan komponen adaptif biasanya didukung oleh teknologi lain selain server web.

Dalam pengelolaan situs web, kombinasi antara server web dan server aplikasi seringkali memberikan hasil yang lebih baik. Server web dapat menangani permintaan dasar dan menyediakan konten statis dengan baik, sedangkan server aplikasi lebih cocok untuk menangani permintaan yang lebih kompleks dan dinamis.

Dengan demikian, meskipun server aplikasi dan server web memiliki perbedaan yang signifikan, keduanya memiliki peran yang penting dalam menjaga situs web berjalan dengan baik dan menyediakan pengalaman pengguna yang baik.

![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/docker.png)

## DOCKER / CONTAINERIZED Masuk Mana?

Docker atau containerisasi adalah teknologi yang memungkinkan pengembang untuk mengemas aplikasi dan semua dependensinya ke dalam unit yang disebut container. Dalam konteks server aplikasi dan web, Docker atau containerisasi sering digunakan untuk menyediakan lingkungan yang terisolasi untuk menjalankan aplikasi.

Dalam hubungannya dengan server aplikasi dan web, Docker atau containerisasi masuk dalam kategori yang berbeda dari server aplikasi dan server web. Server aplikasi dan server web adalah infrastruktur yang digunakan untuk menjalankan dan menyajikan aplikasi dan konten web kepada pengguna akhir. Di sisi lain, Docker atau containerisasi adalah teknologi yang digunakan untuk mengemas, mendistribusikan, dan menjalankan aplikasi dan layanan dalam lingkungan terisolasi yang disebut container.

Jadi, Docker atau containerisasi bisa dianggap sebagai teknologi yang dapat digunakan untuk menyediakan lingkungan runtime untuk menjalankan aplikasi di dalam server aplikasi atau server web. Mereka memungkinkan pengembang untuk mengemas dan mendistribusikan aplikasi dengan lebih mudah, serta memastikan konsistensi dalam lingkungan pengembangan, pengujian, dan produksi. Dengan demikian, Docker atau containerisasi memainkan peran penting dalam infrastruktur modern yang memungkinkan pengembangan dan pengiriman aplikasi yang lebih efisien dan dapat diandalkan.


# B. Containerized Web Server Using Docker

Apa itu docker?, apakah docker sama dengan VMBOX?. Secara fungsi hampir sama tetapi tidak sama, jadi docker menjalankan aplikasi contohnya **MicroService** yang dimana dipecah menjadi kecil kecil kedalam sebuah container!, lalu apa bedanya jika menggunakan vmbox?,

Vmbox biasanya digunakan oleh sebuah aplikasi yang menjunjung tinggi sdlc Agile karena setiap satu vmbox menyimpan satu Server misal Vmbox A sebagai server nginx, lalu VMBOX B sebagai Server Database dst..

Jika menggunakan SDLC DEVOPS Kebanyakan aplikasi telah menjadi MicroService yaitu dipecah menjadi container itu tadi

**Lalu apa saja Container Engine yang ada?**

Ada banyak seperti

Docker, Salad, Ambassador, Red Hat Openshift dll

[Docker](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/docker.com) menjadi salah satunya yang sering digunakan!

Oleh karenanya mari kita coba melakukan Kontainersiasi Virtual Box :D


#### A. Pemasang Docker di Debian vmBox

1. Hapus Docker.io dan dependency bawaan dari *DEBIAN!*, lakukan seperti command berikut!

        for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

2. Lakukan Update/Upgrade Repository dan tambahkan Docker Official GPG Keys

        sudo apt-get update
        sudo apt-get install ca-certificates curl
        sudo install -m 0755 -d /etc/apt/keyrings
        sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
        sudo chmod a+r /etc/apt/keyrings/docker.asc

3. Tambahkan Repository Apt Resources

        echo \
        "deb [arch=$(dpkg --print-architecture) signed-by=/etc apt/keyrings/docker.asc] https://download.docker.com/linux/debian \
        $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
        sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
        sudo apt-get update

4. Install DOCKER OFFICIAL PACKAGE

        sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

5. Docker Sudah Terpasang :D !, Yuk coba jalankan Hello World

        sudo docker run hello-world

    or

        sudo docker pull hello-world && docker run hello-world

    ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/image-1.png)

    Sum

    ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/image.png)    


### Membuat Docker Image

1. Buat File dengan Konfigurasi Berikut Buat file bernama **Dockerfile**

    > Dockerfile

        from nginx:alpine

        COPY index.html /usr/share/nginx/html
        EXPOSE 80

        CMD ["nginx", "-g", "daemon off;"]

    ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/image-2.png)

2. Build Ke dalam Docker **IMAGES**

            sudo docker build -t contoh .

    ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/image-3.png)

    Jalankan Docker dengan Perintah

3. Jalankan **DOCKER IMAGES**

        sudo docker run -d -p 80:80 contoh


4. Berhasil!, akses port 80

    ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/image-4.png)


# C. Apache2 + Dns Resolver + Docker Uptime Kuma Package

Sekarang kita akan coba buka salah satu running server dengan dns yang diresolve oleh named/bind9 kemudian kita gunakan apache2 untuk web servernya :D

1. Git Clone Uptime Kuma dahulu

        git clone https://github.com/louislam/uptime-kuma.git

        cd uptime-kuma

2. lalu Jalankan dengan cara berikut

        sudo docker compose up

    yang dimana akan melakukan eksekusi file compose.yaml

    cek running container

        sudo docker ps -a

    pastikan berjalan

3. kita cek pada port berjalan yaitu **3001**

    `localhost:3001`

    ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/image-5.png)

### Lalu Bagaimana jika menggunakan url `monitoring.kelompok2.local` ?

1. Konfigurasi file **/var/lib/bind/db.kelompok2.local**

    Tambahkan monitoring pada CNAME ns
    dan jangan lupa ubah version file + date

    ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/image-6.png)

    `sudo sytemctl restart named`

2. Untuk melakukan pointing ke domain localhost kita, kita gunakan ReverseProxy pada Apache2 Kita ( a2enmod )

    Install Beberapa Package Berikut dengan menjalankan perintah berikut:

    `sudo a2enmod`

    Masukkan Package berikut
    `proxy proxy_ajp proxy_http rewrite deflate headers proxy_balancer proxy_connect proxy_html`

    ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/ss.png)

3. Setelah itu kita lakukan Konfigurasi pada Apache2 Kita

    > /etc/apache2/sites-enabled/000-default.conf

    ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/image-7.png)

    Tambahkan baris berikut untuk monitoring subdomain

    ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/image-8.png)

    `sudo sytemctl restart apache2`

4. Cek pada web browser kita

    ![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/image-9.png)

    Berhasil :D

    ![hehe](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_6/assets/hehe.gif)