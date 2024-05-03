# Langkah-1 Instalasi NVM, NodeJS, dan Nginx

## 1. Persiapkan Dependencies

```bash
sudo apt update
sudo apt install curl build-essential
```

## 2. Download Script Instalasi NVM

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

## 3. Reload Terminal

```bash
source ~/.bashrc
```

## 4. Verifikasi Instalasi NVM

```bash
nvm --version
```

## 5. Instalasi Node.js

Node.js versi terbaru

```bash
nvm install node
```

Node.js versi tertentu, contoh versi 16.1.0

```bash
nvm install 16.1.0
```

## 6. Melihat List Versi Node.js yang tersedia

```bash
nvm list
```

## 7. Memilih Versi Node.js

**_Petunjuk: Misalkan ingin memilih node.js versi 16.1.0_**

```bash
nvm use 16.1.0
```

## 8. Verifikasi Instalasi Node.js

```bash
node --version
```

## 9. Instalasi Nginx

```bash
sudo apt install nginx
```

## 10. Verifikasi Instalasi Nginx

```bash
sudo service nginx status
```

**_Petunjuk: Lakukan testing, buka browser lalu akses melalui IP Public. Jika berhasil maka muncul "Welcome to Nginx!"_**