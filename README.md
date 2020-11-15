# Jarkom Modul 2 Lapres C11
- Aaron Astonvilla Rompis (0511184000131)
- Nikodemus Siahaan (05111840000151)

### 1.	Membuat semeruc11.pw pada UML Malang
-	nano /etc/bind/named.conf.local
-	mkdir /etc/bind/jarkom
-	cp /etc/bind/db.local /etc/bind/jarkom/semeruc11.pw
-	nano /etc/bind/jarkom/semeruc11.pw
-	service bind9 restart

screenshot:

![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_145.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_146.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_147.png)

### 2.	Membuat alias CNAME pada semeruc11.pw pada UML Malang
-	nano /etc/bind/jarkom/semeruc11.pw
-	service bind9 restart

screenshot:

![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_148.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_150.png)

### 3.	Membuat subdomain www.penanjakan yang mengarah ke IP PROBOLINGGO
-	nano /etc/bind/jarkom/semeruc11.pw
-	service bind9 restart

screenshot:

![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_151.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_152.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_153.png)


### 4.	Membuat Reverse domain untuk domain utama
-	nano /etc/bind/named.conf.local
-	cp /etc/bind/db.local /etc/bind/jarkom/71.151.10.in-addr.arpa
-	nano /etc/bind/jarkom/71.151.10.in-addr.arpa
-	service bind9 restart

screenshot:

![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_154.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_155.png)

### 5.	Membuat Slave pada UML MOJOKERTO
-	nano /etc/bind/named.conf.local pada MALANG
-	service bind9 restart pada MALANG
-	nano /etc/bind/named.conf.local pada MOJOKERTO
-	service bind9 restart pada MOJOKERTO

screenshot:

![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_156.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_157.png)



### 6.	Membuat Delegasi yang pada MOJOKERTO yang mengarah ke PROBOLINGGO
-	nano /etc/bind/jarkom/semeruc11.pw pada MALANG
-	nano /etc/bind/named.conf.options
-	allow-query{ any; };
-	nano /etc/bind/named.conf.local
-	service bind9 restart
-	nano /etc/bind/named.conf.options pada MOJOKERTO
-	allow-query{any;};
-	nano /etc/bind/named.conf.local
-	mkdir /etc/bind/delegasi
-	cp /etc/bind/db.local /etc/bind/delegasi/gunung.semeruc11.pw
-	nano /etc/bind/delegasi/gunung.semeruc11.pw
-	service bind9 restart

screenshot:

![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_158.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_159.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_160.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_161.png)



### 7.	Membuat subdomain naik.gunung.semeruc11.pw yang mengarah ke PROBOLINGGO
-	nano /etc/bind/delegasi/gunung.semeruc11.pw
-	service bind9 restart

screenshot:

![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_162.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_163.png)


### 8.	Mengatur webserver semeruc11.pw
-	wget 10.151.36.202/semeru.pw.zip pada /var/www/ di PROBOLINGGO
-	extract pada folder semeruc11.pw
-	copy 000default menjadi semeruc11.pw.conf
-	tambahkan ServerName dan ServerAlias
-	ubah DocumentRoot menjadi /var/www/semeruc11.pw
-	a2ensite semeruc11.pw.conf
-	apache restart

screenshot:
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/no%208.jpg)

### 9.	Awalnya web dapat diakses menggunakan alamat http://semeruyyy.pw/index.php/home. Karena dirasa alamat urlnya kurang bagus, maka (9) diaktifkan mod rewrite agar urlnya menjadi http://semeruyyy.pw/home.
-	Nano /var/www/semeruc11.pw/.htaccsess
-	A2enmod rewrite
-	Apache restart
-	Edit semeruc11.pw.conf pada PROBOLINGGO
-	Apache restart

### 10.	Web http://penanjakan.semeruyyy.pw akan digunakan untuk menyimpan assets file yang memiliki DocumentRoot pada /var/www/penanjakan.semeruyyy.pw
-	Edit penanjakan.semeruc11.pw.conf pada PROBOLINGGO


### 11.	Pada folder /public dibolehkan directory listing namun untuk folder yang berada di dalamnya tidak dibolehkan.
-	Edit penanjakan.semeruc11.pw.conf pada PROBOLINGGO
-	Tambahkan +Indexes pada public
-	Tambahkan -Indexes pada seluruh folder yang ada di public
-	Apache restart


### 12.	Untuk mengatasi HTTP Error code 404, disediakan file 404.html pada folder /errors untuk mengganti error default 404 dari Apache.
-	Tambahkan error document pada penanjakan.semeruc11.pw.conf
-	Apache restart



### 13.	Untuk mengakses file assets javascript awalnya harus menggunakan url http://penanjakan.semeruyyy.pw/public/javascripts. Karena terlalu panjang maka dibuatkan konfigurasi virtual host agar ketika mengakses file assets menjadi http://penanjakan.semeruyyy.pw/js.
-	Tambahkan Alias "/js" "/var/www/penanjakan.semeruc11.pw/public/javascripts" pada penanjakan.semeruc11.pw.conf
-	+Indexes pada folder javascripts


### 14.	Untuk web http://gunung.semeruyyy.pw belum dapat dikonfigurasi pada web server karena menunggu pengerjaan website selesai. (14) sedangkan web http://naik.gunung.semeruyyy.pw sudah bisa diakses hanya dengan menggunakan port 8888. DocumentRoot web berada pada /var/www/naik.gunung.semeruyyy.pw.
-	Membuat naik.gunung.semeruc11.pw.conf pada PROBOLINGGO
-	Ubah port menjadi 8888
-	Tambahkan listen 8888 pada file ports pada folder apache2

### 15.	Dikarenakan web http://naik.gunung.semeruyyy.pw bersifat private (15) Bibah meminta kamu membuat web http://naik.gunung.semeruyyy.pw agar diberi autentikasi password dengan username “semeru” dan password “kuynaikgunung” supaya aman dan tidak sembarang orang bisa mengaksesnya.
-	htpasswd -c /etc/apache2/.htpasswd semeru
-	masukkan password kuynaikgunung
-	edit naik.gunung.semeruc11.pw.conf
-	apache restart


### 16.	Karena dirasa kurang profesional, maka setiap Bibah mengunjungi IP PROBOLINGGO akan dialihkan secara otomatis ke http://semeruyyy.pw.
- Tambahi Redirect Permanent ke semeru

### 17.	Karena pengunjung pada /var/www/penanjakan.semeruyyy.pw/public/images sangat banyak maka semua request gambar yang memiliki substring “semeru” akan diarahkan menuju semeru.jpg.
