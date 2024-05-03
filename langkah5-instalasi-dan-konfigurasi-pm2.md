# Langkah-5 Instalasi dan Konfigurasi PM2

## 1. Kembali ke Direktori Aplikasi

**_Petunjuk: Sebelum mengimplementasikan PM2, pastikan posisi berada di /home/portraitplace/portrait-web-app_**

```bash
cd /home/portraitplace/portrait-web-app_
```

## 2. Instalasi PM2

```bash
npm install -g pm2
```

## 3. Implementasi PM2 pada Aplikasi

```bash
pm2 start npm --name "portrait-web-app" -- run start
```

## 4. Melihat Daftar Aplikasi yang Berjalan di PM2

```bash
pm2 status
```

atau

```bash
pm2 list
```

## 5. Konfigurasi Sistem Boot Otomatis

```bash
pm2 startup
```

**_Petunjuk: Copy dan jalankan perintah yang muncul di terminal_**

## 6. Save Konfigurasi

```bash
pm2 save
```