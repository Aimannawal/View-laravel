## Cara Deploy Web Kamu di Ubuntu Server
Halo kali ini saya akan membuat panduan cara deploy web di Ubuntu Server

**Step 1**
--
1 . Pastikan anda memiliki Ubuntu Server 

2 . Jika di server anda belum terinstall Apache2 atau Nginx, maka install terlebih dahulu menggunakan command:
```
sudo apt install apache2
```
3 . Clone repository web anda yang ingin di deploy di Ubuntu Server

4 . Lalu copy dan paste folder yang telah di clone dan hapus file index.html menggunakan command:
```
cp nama_folder /var/www/html
sudo rm index.html
```
5 . Lalu masuk ke dir sites-available menggunakan command:
```
cd /etc/apache2/sites-available
```
6 . Setelah itu edit file bernama 000-default.conf menggunakan command:
```
sudo nano 000-default.conf
```
7 . Lalu ubah line berikut 
```
ServerName afif.lokal
        ServerAlias afif.lokal
        DocumentRoot /var/www/html/TestingDeploy/
        <Directory /var/www/html/TestingDeploy>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride All
            Require all granted
        </Directory>
```
NB: Anda bisa sesuaikan sesuai dengan nama folder dan file yang ingin anda deploy dibagian setelah /html/

8 . Lalu save dan exit menggunakan ctrl x; y; key enter

9 . Setelah itu gunakan command berikut secara ter-urut
```
sudo a2enmod rewrite
sudo systemctl restart apache2
```
10 . Lalu cek status apache2 menggunakan command:
```
systemctl status apache2
```
11 . Lalu buka di browser kalian mdengan mengetikan ip 127.0.0.1

## Web anda berhasil terdeploy ##
