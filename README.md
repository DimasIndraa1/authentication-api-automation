# API Automation Testing - Authentication

[![API Test](https://github.com/DimasIndraa1/authentication-api-automation/actions/workflows/api-test.yml/badge.svg)](https://github.com/DimasIndraa1/authentication-api-automation/actions)
[![View Report](https://img.shields.io/badge/View-Live_Report-brightgreen?style=flat-sq&logo=github)](https://dimasindraa1.github.io/authentication-api-automation/index-positive.html)

Project ini merupakan framework **Automation API Testing** untuk modul autentikasi menggunakan **Postman + Newman** yang terintegrasi dengan **CI/CD GitHub Actions**. Laporan hasil pengujian dipublikasikan ke **GitHub Pages** dalam format HTML Extra dan Allure Report.

---

## Tech Stack & Tools

| Tool | Kegunaan |
| :--- | :--- |
| **Postman** | API Development & Collection runner |
| **Newman** | CLI runner untuk menjalankan Postman collection |
| **Allure** | Reporting framework untuk visualisasi hasil test |
| **Newman HTML Extra** | Reporter visual tambahan untuk hasil test |
| **GitHub Actions** | Automation pipeline (CI/CD) |
| **GitHub Pages** | Hosting laporan testing statis |

---

## Scope Testing

Pengujian difokuskan pada modul autentikasi untuk memastikan keamanan dan validitas data:

- **Login API:** Validasi skenario positif & negatif (wrong password, unknown username, empty body, missing field)
- **Token Validation:** Memastikan akses token digenerate dengan benar (format JWT)
- **Response Schema:** Verifikasi struktur JSON response sesuai kontrak API
- **Status Code:** Memastikan respon HTTP (200, 400, 401) sesuai ekspektasi
- **Security:** Memastikan password/token tidak bocor di response, tidak ada stack trace

---

## Cara Menjalankan di Local

### 1. Prasyarat

Pastikan Anda sudah menginstal **Node.js**, lalu clone repo ini dan masuk ke direktori project.

### 2. Install Dependencies

```bash
npm install
npm install -g newman newman-reporter-htmlextra newman-reporter-allure
```

### 3. Jalankan Test

Via npm scripts (recommended):

```bash
# Positive test saja
npm run test:positive

# Negative test saja (data-driven)
npm run test:negative

# Semua test (positive + negative)
npm run test:all
```

Atau via Newman langsung:

```bash
# Positive test
newman run api-automation/collections/auth/auth.postman_collection.json \
  -e api-automation/environments/dev/dev.postman_environment.json \
  --folder "Positive Flow" \
  -r cli,allure

# Negative test
newman run api-automation/collections/auth/auth.postman_collection.json \
  -e api-automation/environments/dev/dev.postman_environment.json \
  --folder "Negative Flow" \
  -d api-automation/data/scenario.json \
  -r cli,allure
```

### 4. Generate & Lihat Allure Report

```bash
npm run test:report
npm run test:serve
```

Atau langsung:

```bash
allure serve allure-results
```

---

## Struktur Project

```
api-automation-auth/
├── .github/workflows/
│   └── api-test.yml           # GitHub Actions CI/CD pipeline
├── gitlab-ci.yml              # GitLab CI alternative config
├── api-automation/
│   ├── collections/auth/
│   │   └── auth.postman_collection.json   # Main collection (positive & negative)
│   ├── data/
│   │   └── scenario.json      # Data-driven test scenarios
│   └── environments/dev/
│       └── dev.postman_environment.json   # Environment variables
├── .gitignore
├── package.json
└── README.md
```

---

## Live Test Report

- **Newman Report (Positive):** https://dimasindraa1.github.io/authentication-api-automation/index-positive.html
- **Newman Report (Negative):** https://dimasindraa1.github.io/authentication-api-automation/index-negative.html
- **Allure Report:** https://dimasindraa1.github.io/authentication-api-automation/allure-report/
