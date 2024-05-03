# Langkah-4 Instalasi HTTPS dan Certbot

**_Catatan: Berikut adalah langkah-langkah instalasi di Ubuntu dan menggunakan Nginx_**

## 1. Instalasi Snap

```bash
sudo snap install core
sudo snap refresh core
```

## 2. Copot Instalasi Certbot Bawaan OS

```bash
sudo apt-get remove certbot
```

## 3. Instalasi Certbot

```bash
sudo snap install --classic certbot
```

## 4. Inisiasi Perintah-perintah Certbot

```bash
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

## 5. Proses Instalasi dan Pembaruan Sertifikat SSL Gratis

```bash
sudo certbot --nginx
```

**Instruksi:**

- Masukan email: theportraitplacedeveloper@gmail.com
- Pilih (Y)es: ketik karakter 'y'
- Ketik karakter '1'

## 6. Verifikasi konfigurasi SSL

```bash
cat /etc/nginx/conf.d/nextjs.conf
```

## 7. Test Pembaruan Otomatis

```bash
sudo certbot renew --dry-run
```