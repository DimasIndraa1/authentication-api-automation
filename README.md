# 🚀 API Automation Testing - Authentication
[![API Test](https://github.com/DimasIndraa1/authentication-api-automation/actions/workflows/api-test.yml/badge.svg)](https://github.com/DimasIndraa1/authentication-api-automation/actions)
[![View Report](https://img.shields.io/badge/View-Live_Report-brightgreen?style=flat-sq&logo=github)](https://dimasindraa1.github.io/authentication-api-automation/)

Project ini merupakan framework **Automation API Testing** yang mengintegrasikan **Postman + Newman** ke dalam alur **CI/CD GitHub Actions**. Hasil pengujian secara otomatis dipublikasikan melalui GitHub Pages.

---

## 📊 Live Test Report

Hasil eksekusi testing terbaru dapat diakses secara interaktif melalui tautan di bawah ini:

> 🔗 **[Lihat HTML Extra Report](https://dimasindraa1.github.io/authentication-api-automation/)**

---

## 🛠️ Tech Stack & Tools

| Tool | Kegunaan |
| :--- | :--- |
| **Postman** | API Development & Collection runner |
| **Newman** | CLI runner untuk menjalankan Postman collection |
| **Newman HTML Extra** | Reporter visual untuk hasil test yang mendalam |
| **GitHub Actions** | Automation pipeline (CI/CD) |
| **GitHub Pages** | Hosting laporan testing statis |

---

## 🧪 Scope Testing

Pengujian difokuskan pada modul autentikasi untuk memastikan keamanan dan validitas data:
* ✅ **Login API:** Validasi skenario positif & negatif (credentials salah/kosong).
* ✅ **Token Validation:** Memastikan akses token digenerate dengan benar.
* ✅ **Response Schema:** Verifikasi struktur JSON response sesuai kontrak API.
* ✅ **Status Code:** Memastikan respon HTTP (200, 400, 401, dll) sesuai ekspektasi.

---

## 🚀 Cara Menjalankan di Local

### 1. Prasyarat
Pastikan Anda sudah menginstal **Node.js**, lalu pasang library pendukung secara global:
```bash
npm install -g newman newman-reporter-htmlextra
```

### 2. Eksekusi Test
Jalankan perintah berikut untuk mengeksekusi collection dan menghasilkan report HTML:
```bash
newman run api-automation/collections/auth/login.postman_collection.json \
-e api-automation/environments/dev.postman_environment.json \
-r cli,htmlextra \
--reporter-htmlextra-export newman/index.html
```
