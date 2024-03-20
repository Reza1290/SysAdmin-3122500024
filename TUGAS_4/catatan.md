internet itu berkesinambungan dapat diartikan seperti eksosistem

Vendor = Konten provider. Internet Exchange Point = Optimasi Routing, g/ccTLDs= penamaan

education and capacity building
Tau cara kerjanya internet didasarkan atas kerjasama, 
machine and device


Internet berawal dari ICANN mengassign ICANN kalo di indonesia melewati PANDI, .id => apakah domain alvailable dan sewanya, 
Admin di DNS rovides name location mapping


Misal Komputer pakai hostname => di translate ke IP address lewati router. 

Routingable-> ip address ada 2 -> publik global, private.

Tugas IANA untuk memberikan Jatah IP di masing masing Regional, Regional Registries => APNIC => asia, ARIN => Amerika.

Internet Excgange => POP point of presence intiland dsb

Internet Teknis, Arsitektur
Teknis => Routing, naming sistem

Arsitektural => Standart, Service providers, Internet Register, Kliring Sistem




# IP ADDRESS AND ROUTING SYSTEM
HAL yang tidak dapat dipisahkan

IP address ada 2 tipe => IPV4 dan IPV6

Routing => Router setiap router ada ip address, 
setiap cluster biasanya IP terdapat edge borderrouter => nmerupakan router kooridnasi pada tiap isp,

memiliki kebijakan Router (POLICY) Routing Protocol

AS Number => kumpulan router ISP 

Peering Connection adalah kebijakan yang diimplementasikan ke provider - customer, transit,sttelment free 

misal PENS INDOSAT Urusan LINK/kabel laut mana urusan Transit -> Indosat => Settlement free adalah bandwith gratis

contoh IDREN

Peering terbesar => GOOGLE, StreamPeering

Edge Provider Routing Policy

misal ISP punya pelanggan dia inginkonek ke suatu website maka harus lewat ISP Besar Dulu
Komplek ini HOT potato ROuting 
dicari jitter paling kecil / RTT harus lewat yang besar , tiba tiba ada customer lain ternyata ada anak perusahaan untuk attract traffic baru tidak perlu ke pusat



Transit Provider Routing Policy


Content Provider routing policy
Kalo Lewat anak perusahaan namanya COLD lebih deket.
Youtube = Sebisanya dekat dengan pengguna, sebelum tahun 2002 akses yutub langsung amerika , sekarang ada CDN, google nyebar server 
Kerjasama ISP, untuk hosting CDN hanya membayar Bandwith, keuntungan ISP => User Statisfied 

Pens punya youtube Cache

Naming System
Contoh DNS Domain Name System
misal PENS.AC.ID, tanya dulu IP nya resolve ip


DNS HEIRARCHY TREE

pens.ac.id => www. nama hostname + gabungan domain name = FQDN Fully qualified domain name

cc dan g 
TLD => top level domain com,net,org,arpa,au,jp,id...

paling atas dinamakan root Server
misal www.pens.ac.id. => TLD, Secondary,Third ... dll

subdomain

DNS COMPOneNTS

dns => bind9

Namespace =>\
Nameserver +> make namespace alvailabel

resolver => query

cnoth


Rootserver => .id => co.id, (ac.id =>pens.ac.d (ethol,maildll))

Domain => ASNumber ROuting domain & Domain Name


Tipe NameSERVER

Authoritative servers => primary Master, secodnary slave
Recursive Servers => Untuk diri sendiri untuk menngforward atu terusan zues

contoh menggunakan IAC => salah satu forwarrder meneruskan dns yang ada di atas gambar

(PENS.AC.ID(IAC2.PENS.AC.ID)<-------forward-------->(LAPTOP))

AUTHORITATIVE NAME SERVERS

Authorize yang berhak menyediakan jawaban itu bisa lebih dari satu tetapi 1 yang jawab => primary yang jawab, secondary untuk backup primary

Recursive bakalan nyari keatas dari root server.

Bagaimana Cara kerja dari iterative dan recursive dari DNS Query, ada 8 step kalo gasalah, dari PC anda! misal akses detik.com, oke tanya yang ada .comnya bolak balik

sekarang ada 13 root server dari a sampe m 

map 


anycache mencari yang terdekat -=> tanya ke root server F bakalan lari ke jakarta

semakin banyak root server diindonesia gaperlu bayar bandwith, resolving lebih cepat

Root server deployment Apnic

DNS Zone file


trainin.apnic.net = label, 86400 = TTL, IN = Class, A = Type, 192.168.1.100 = Rdata

MX => mail server

delegate server subdomain to dns glue record


STANDAR BADAN

bertugas melakukan standarasisasi seluruh apa yang dikerjakan secara teknis

IETF bertugas untk layer 3 transport dan layer protocol


3 tipe isp Tier 1 Networks = huricanes
Transit menjual routing ip supaya lebih dekat contoh
equinix telkom solutin punya transit bisa peering IXP
Tier 2 Networks = isp

openixp


registries => pendtaan ip distribusi IP

ICANN => nama, Iana => Adress

Regional => Kawasan Iana dan ican ngasih ke APNIC asia, Africa Afrinic
