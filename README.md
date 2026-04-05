# 🚀 API Automation Testing - Authentication

Project ini merupakan automation API testing menggunakan **Postman + Newman** dengan integrasi **CI/CD GitHub Actions**.

---

## 📊 Live Test Report

👉 Klik untuk melihat hasil automation terbaru:

🔗 https://dimasindraa1.github.io/authentication-api-automation/

---

## 🧪 Scope Testing

- ✅ Login API (Positive & Negative)
- ✅ Token validation
- ✅ Response schema validation
- ✅ Status code verification

---

## ⚙️ Tech Stack

- Postman
- Newman
- Newman HTML Extra Reporter
- GitHub Actions (CI/CD)
- GitHub Pages (Report Hosting)

---

## 🚀 Cara Menjalankan di Local

```bash
npm install -g newman newman-reporter-htmlextra

newman run api-automation/collections/auth/login.postman_collection.json \
-e api-automation/environments/dev.postman_environment.json \
-r cli,htmlextra \
--reporter-htmlextra-export newman/index.html

