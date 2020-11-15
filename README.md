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
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_151.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_152.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_153.png)


### 4.	Membuat Reverse domain untuk domain utama
-	nano /etc/bind/named.conf.local
-	cp /etc/bind/db.local /etc/bind/jarkom/71.151.10.in-addr.arpa
-	nano /etc/bind/jarkom/71.151.10.in-addr.arpa
-	service bind9 restart

![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_154.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_155.png)

### 5.	Membuat Slave pada UML MOJOKERTO
-	nano /etc/bind/named.conf.local pada MALANG
-	service bind9 restart pada MALANG
-	nano /etc/bind/named.conf.local pada MOJOKERTO
-	service bind9 restart pada MOJOKERTO

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

![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_158.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_159.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_160.png)
![image](https://github.com/nicosiahaan/Jarkom_Modul2_Lapres_C11/blob/main/img/Screenshot_161.png)



### 7.	Membuat subdomain naik.gunung.semeruc11.pw yang mengarah ke PROBOLINGGO
-	nano /etc/bind/delegasi/gunung.semeruc11.pw
-	service bind9 restart

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

