# 1. Environment Setup

## Instalasi NVM dan Node.js

1. Persiapkan Dependencies

```bash
sudo apt update
sudo apt install curl build-essential
```

2. Download Script Instalasi NVM

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

3. Reload Terminal

```bash
source ~/.bashrc
```

4. Verifikasi Instalasi NVM

```bash
nvm --version
```

5. Instalasi Node.js

Node.js Versi Terbaru

```bash
nvm install node
```

Node.js Versi Tertentu, Contoh Versi 16

```bash
nvm install 16
```

6. Melihat List Versi Node.js yang tersedia

```bash
nvm list
```

7. Memilih Versi Node.js

**_Petunjuk: Misalkan ingin memilih node.js versi 16.1.0_**

```bash
nvm use 16.1.0
```

8. Verifikasi Instalasi Node.js

```bash
node --version
```

## Instalasi Nginx

1. Instalasi Nginx

```bash
sudo apt install nginx
```

2. Verifikasi Instalasi Nginx

```bash
sudo service nginx status
```

**_Petunjuk: Lakukan testing, buka browser lalu akses melalui IP Public. Jika berhasil maka muncul "Welcome to Nginx!"_**

## Clone dan Build Aplikasi

1. Clone Aplikasi

```bash
git clone https://github.com/PortraitDeveloper/portrait-web-app.git
```

2. Instalasi Dependencies

```bash
cd portrait-web-app
npm install
```

3. Build Aplikasi

```bash
npm run build
```

4. Jalankan Aplikasi

```bash
npm start
```

**_Petunjuk: Lakukan testing, buka browser lalu akses melalui IP Public._**

```bash
IP_PUBLIC:3000
```

**_Petunjuk: Setelah itu kembali ke terminal kemudian stop aplikasi dengan cara CTRL+C_**

## Pointing Domain dan Konfigurasi Reverse Proxy

1. Pointing Domain
   **_Petunjuk: Berikut adalah [tutorial](https://youtu.be/beeAdVNNPZg) cara membeli dan mengkonfigurasi domain ke IP Public di VPS Biznet Gio Neo Lite _**

2. Arahkan ke Direktori /etc/nginx/conf.d

```bash
cd /etc/nginx/conf.d
```

3. Buat File Konfigurasi

```bash
sudo nano next.js.conf
```

**Instruksi:**

- Copy dan paste konfigurasi reverse proxy dibawah ini

```bash
server {
	listen 80;

	#server_name ...domain;
	server_name theportraitplace.my.id nextjs.theportraitplace.my.id;

	location / {
		proxy_pass http://localhost:3000;
	}
}
```

- Tekan CTRL + x
- Kemudian muncul pesan seperti ini -> (If prompted with "Save modified buffer?"), tekan Y, lalu tekan Enter untuk menyimpan

4. Verifikasi Konfigurasi

```bash
sudo nginx -t
```

5. Restart Nginx

```bash
sudo systemctl restart nginx
```

## Instalasi HTTPS dan Certbot

**_Catatan: Berikut adalah langkah-langkah instalasi di Ubuntu dan menggunakan Nginx_**

1. Instalasi Snap

```bash
sudo snap install core
sudo snap refresh core
```

2. Copot Instalasi Certbot Bawaan OS

```bash
sudo apt-get remove certbot
```

3. Instalasi Certbot

```bash
sudo snap install --classic certbot
```

4. Inisiasi Perintah-perintah Certbot

```bash
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

5. Proses Instalasi dan Pembaruan Sertifikat SSL Gratis

```bash
sudo certbot --nginx
```

**Instruksi:**

- Masukan email: theportraitplacedeveloper@gmail.com
- Pilih (Y)es: ketik karakter 'y'
- Ketik karakter '1'

6. Verifikasi konfigurasi SSL

```bash
cat /etc/nginx/conf.d/nextjs.conf
```

7. Test Pembaruan Otomatis

```bash
sudo certbot renew --dry-run
```

## Instalasi dan Konfigurasi PM2

1. Kembali ke Direktori Aplikasi
   **_Petunjuk: Sebelum mengimplementasikan PM2, pastikan posisi berada di /home/portraitplace/portrait-web-app_**

```bash
cd /home/portraitplace/portrait-web-app_
```

2. Instalasi PM2

```bash
npm install -g pm2
```

3. Implementasi PM2 pada Aplikasi

```bash
pm2 start npm --name "portrait-web-app" -- run start
```

4. Melihat Daftar Aplikasi yang Berjalan di PM2

```bash
pm2 status
```

atau

```bash
pm2 list
```

5. Konfigurasi Sistem Boot Otomatis

```bash
pm2 startup
```

**_Petunjuk: Copy dan jalankan perintah yang muncul di terminal_**

6. Save Konfigurasi

```bash
pm2 save
```

# Referensi

[Repositori NVM](https://github.com/nvm-sh/nvm?tab=readme-ov-file)

[Official Web PM2](https://pm2.keymetrics.io/)

[Official Web Certbot](https://certbot.eff.org/instructions?ws=nginx&os=ubuntufocal&tab=standard)

[Tutorial Deploy Aplikasi NextJS ke VPS Neo Lite](https://youtu.be/CnS0hTcY-5k?si=5LYt02ILX-1fR4gS)

[Deploy Website NextJS dan Pointing Domain ke VPS - Biznet Gio Neo Lite](https://youtu.be/beeAdVNNPZg?si=-BYZ9vA_1yPjgSgY)

[Cara Install HTTPS di VPS Pakai Let's Encrypt dan Certbot - VPS Biznet Gio Neo Lite](https://youtu.be/Q0jlf7d_j6I?si=JYxD4Slv-7GZZf3j)
