# Langkah-3 Pointing Domain dan Konfigurasi Reverse Proxy

## 1. Pointing Domain

**_Petunjuk: Berikut adalah [tutorial](https://youtu.be/beeAdVNNPZg) cara membeli dan mengkonfigurasi domain ke IP Public di VPS Biznet Gio Neo Lite_**

## 2. Arahkan ke Direktori /etc/nginx/conf.d

```bash
cd /etc/nginx/conf.d
```

## 3. Buat File Konfigurasi

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

## 4. Verifikasi Konfigurasi

```bash
sudo nginx -t
```

## 5. Restart Nginx

```bash
sudo systemctl restart nginx
```
