# FILE LAINNYA

[BACK](../README.md)

# TUGAS 4

**Daftar Isi**
- [Soal 1 (Pribadi)](#1-ekosistem-internet)
- [Soal 2 (Pribadi)](#2-dns-query)
- [Soal 3 (Kelompok(BIND9))](#3-config-bind9)


## 1. Ekosistem Internet     

Dibawah ini adalah ekosistem internet menurut saya berdasarkan materi yang di sampaikan oleh bapak Ferry Astika [Akses Catatan Materi](/catatan.md)

Internet adalah sebuah ekosistem yang berkesinambungan, di mana berbagai entitas seperti vendor konten, titik pertukaran internet (Internet Exchange Point), dan gTLD/ccTLDs (Global dan Country Code Top-Level Domains) bekerja sama untuk mengoptimalkan routing dan penyediaan konten. Pendidikan dan pembangunan kapasitas juga merupakan aspek penting dalam pemahaman tentang bagaimana internet berfungsi.

Secara teknis, internet dimulai dengan proses pemberian domain oleh ICANN (Internet Corporation for Assigned Names and Numbers), yang dilakukan melalui entitas seperti PANDI di Indonesia untuk domain berakhiran .id. Admin DNS kemudian menyediakan pemetaan lokasi nama ke alamat IP. Misalnya, saat sebuah komputer menggunakan nama host, itu diterjemahkan menjadi alamat IP melalui router.

Sistem routing memastikan bahwa informasi mencapai tujuannya melalui serangkaian router, dengan setiap router memiliki alamat IP. Ada dua jenis alamat IP: IPv4 dan IPv6. Routing juga melibatkan pengaturan kebijakan router dan protokol routing.

Komunikasi antar ISP (Internet Service Provider) melibatkan koneksi peering, di mana kebijakan seperti provider-customer, transit, dan settlement-free diterapkan. Ini mempengaruhi bagaimana data dipindahkan antar penyedia layanan, dengan tujuan meminimalkan latensi dan memaksimalkan efisiensi.

Penyedia konten juga memiliki kebijakan routing sendiri, seperti yang dilakukan oleh penyedia layanan seperti Google dan YouTube. Mereka menggunakan strategi seperti pemberian cache untuk mempercepat akses konten dan meningkatkan kepuasan pengguna.

Sistem penamaan seperti DNS (Domain Name System) memungkinkan pengguna untuk mengakses situs web menggunakan nama domain alih-alih alamat IP. Ini melibatkan hirarki server DNS dan komponen seperti namespace, nameserver, dan resolver.

Lebih lanjut, standar badan seperti IETF (Internet Engineering Task Force) bertanggung jawab atas standarisasi teknis dalam pengembangan internet, mencakup protokol pada layer 3 transport dan protokol lainnya.

Secara keseluruhan, internet berfungsi sebagai ekosistem yang kompleks, dengan berbagai entitas dan protokol bekerja bersama untuk menyediakan konektivitas dan konten kepada pengguna.

## Bagaimana Cara kerja dari iterative dan recursive dari DNS Query, ada 8 step, dari PC anda! misal akses detik.com

Berdasarkan Penjelesan materi oleh Bapak Ferry Astika
Beberapa tahap dapat digambarkan seperti gambar dibawah ini

![resolver drawio](https://github.com/Reza1290/SysAdmin-3122500024/assets/70069286/edcb30a8-b4d7-4568-a54e-093d21ffefe0)

1. DNS Request IN A www.example.com pada Browser.
2. kemudian Router 10.10.10.1 melakukan forward DNS request ke ns.pens.ac.id
3. ns.pens.ac.id melakukan DNS Request Ke ROOT SERVER Untuk IN A www.example.com
4. Kemudian Root server memberitahu bahwa hubungi .com atau DNS Reply .com IN A
5. ns.pens.ac.id mendapat informasi dari root Server F bahwa .com IN A www.example.com maka pergi ke .com server
6. .com Server IN NS example.com ( memberitahu bahwa Nameserver dari dns request itu adalah example.com ) dan dikembalikan ke ns.pens.ac.id
7. ns.pens.ac.id menuju ns.example.com resolver menanyakan apakah punya www.example.com?
8. kemudian ns.example.com memberikan resolve dari Dns berupa ip dari www.example.com yaitu 93.184.216.54 ke ns.pens.ac.id
9. kemudian diteruskan ke server 10.10.10.1 dengan ip informasi yaitu 93.184.216.54
10. client menerima hasil DNS Request dikarenakan IP telah diketahui.

dilansir pada halaman https://www.cloudflare.com/learning/dns/what-is-dns/


1. Pengguna memasukkan URL "detik.com" ke dalam browser web.
2. browser mengirim permintaan DNS Query pertama ke resolver DNS lokal yang terhubung ke jaringan internet.
3. Resolver DNS lokal tidak memiliki informasi tentang alamat IP untuk "detik.com", sehingga resolver memulai proses query.
4. Langkah Iterative:
   - Resolver DNS lokal membuat kueri pertama ke salah satu dari 13 root server global. Ini adalah langkah iteratif pertama.
   - Root server merespons dengan informasi tentang server TLD (Top-Level Domain) yang bertanggung jawab atas ".com".
5. Langkah Recursive:
   - Resolver DNS lokal kemudian mengirimkan kueri ke server TLD yang bertanggung jawab atas ".com".
   - Server TLD ".com" merespons dengan informasi tentang server DNS yang memiliki informasi tentang "detik.com".
   - Resolver DNS lokal kemudian mengirimkan kueri ke server DNS yang disediakan oleh registrar domain detik.com.
6. Server DNS detik.com merespons dengan alamat IP untuk detik.com.
7. Resolver DNS lokal menerima alamat IP dari server DNS detik.com.
8. Resolver DNS lokal meneruskan alamat IP ke browser.

<br>
<br>

![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/image.png)
[Sumber](https://cf-assets.www.cloudflare.com/slt3lc6tev37/1NzaAqpEFGjqTZPAS02oNv/bf7b3f305d9c35bde5c5b93a519ba6d5/what_is_a_dns_server_dns_lookup.png)


#### Analogi
Kita analogikan seperti ini, analogikan proses pencarian alamat situs web detik.com dengan mencari alamat rumah seseorang di kota yang tidak pernah Anda kunjungi sebelumnya.

1. **Permintaan Awal:**
   Anda ingin mengunjungi teman di kota yang tidak Anda kenal. Anda memiliki nama teman (detik.com) tetapi tidak tahu di mana dia tinggal (alamat IP).

2. **Pertanyaan Pertama:**
   Anda meminta petunjuk pertama kepada seseorang di kota tersebut. Mereka memberi tahu Anda untuk pergi ke pusat informasi kota (root server) karena mereka tidak tahu di mana alamat teman Anda secara langsung.

3. **Pusat Informasi Kota (Root Server):**
   Di pusat informasi kota, petugas memberi tahu Anda bahwa Anda harus mencari di bagian yang bertanggung jawab untuk wilayah tersebut (TLD server).

4. **Wilayah (TLD Server):**
   Anda pergi ke wilayah yang ditunjukkan oleh petugas, dan di sana Anda bertanya pada seseorang lagi. Mereka memberi tahu Anda untuk mencari di kantor polisi setempat (DNS server yang bertanggung jawab atas domain ".com").

5. **Kantor Polisi (DNS Server .com):**
   Di kantor polisi, petugas memberi tahu Anda bahwa Anda harus bertanya langsung ke keluarga teman Anda (DNS server yang bertanggung jawab atas domain detik.com).

6. **Rumah Teman (DNS Server detik.com):**
   Di rumah teman Anda, anggota keluarga memberi tahu Anda alamat lengkap teman Anda.

7. **Kembali ke Anda:**
   Anda kembali dengan alamat lengkap yang diberikan oleh keluarga teman Anda.

8. **Tiba di Rumah Teman:**
   Anda mengunjungi teman Anda dengan menggunakan alamat yang Anda dapatkan dan tiba di rumahnya.


## 3. Config BIND9


Link Tutorial Youtube : https://youtu.be/I1Y9bcQ3zY8
1. lakukan instalasi bind9
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/ss.png)
2. cek instalasi di /etc/bind
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image.png)
3. cek konfigurasi utama bind di named.conf.
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-1.png)
4. Menambahkan ACL (access list), control, dan include 3 file.
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-2.png)
5. Buka named.conf.deafult-zones.
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-3.png)
6. Buka named.conf.option, mengisi provider dan listen-on. Listen ditambahkan sesuai kelompok masing-masing
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-4.png)
7. Buka named.conf.local, untuk mengset atau konfigurasi zone file. Melakukan pengubahan zone sesuai nama kelompok.
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-5.png)
8. Lakukan sudo named-checkconf untuk mengeck pesan error. jika tidak ada pesan error yang keluar itu berarti konfigurasi yang dilakukan telah benar.
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-9.png)
9. Pergi ke arah configuration zone file. 
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-7.png)
10. Masuk ke zone file pertama dan mengubah data di dalamnya.
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-8.png)
11. Masuk ke zone file kedua (.inv) untuk mengubah data seperti file sebelumnya.
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-10.png)
12. Jalankan sudo systemctl restart named untuk menjalankan sistem bind.
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-11.png)
13. Cek status bind apakah running atau tidak.
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-15.png)
14. Cek apakah port terbuka atau tidak.
15. Gunakan perintah dig.
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-14.png)
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-12.png)
16. Gunakan perintah nslookup.
![alt text](https://github.com/Reza1290/SysAdmin-3122500024/blob/main/TUGAS_4/assets/image-13.png)
