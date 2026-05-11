# API Automation Testing - Authentication

[![API Test](https://github.com/DimasIndraa1/authentication-api-automation/actions/workflows/api-test.yml/badge.svg)](https://github.com/DimasIndraa1/authentication-api-automation/actions)
[![View Report](https://img.shields.io/badge/View-Live_Report-brightgreen?style=flat-sq&logo=github)](https://dimasindraa1.github.io/authentication-api-automation/allure-report/)

This project is an **Automation API Testing** framework for authentication module using **Postman + Newman** integrated with **CI/CD GitHub Actions**. Test reports are published to **GitHub Pages** as Allure Report.

---

## Tech Stack & Tools

| Tool | Purpose |
| :--- | :--- |
| **Postman** | API Development & Collection runner |
| **Newman** | CLI runner for Postman collections |
| **Allure** | Reporting framework for test visualization |
| **GitHub Actions** | Automation pipeline (CI/CD) |
| **GitHub Pages** | Hosting static test reports |

---

## Scope Testing

Testing focuses on the authentication module to ensure security and data validity:

- **Login API:** Positive & negative scenario validation (wrong password, unknown username, empty body, missing field)
- **Token Validation:** Ensures access tokens are generated correctly (JWT format)
- **Response Schema:** Verifies JSON response structure matches API contract
- **Status Code:** Ensures HTTP response codes (200, 400, 401) match expectations
- **Security:** Ensures password/token are not leaked in response, no stack trace exposure

---

## How to Run Locally

### 1. Prerequisites

Make sure you have **Node.js** installed, then clone this repo and navigate to the project directory.

### 2. Install Dependencies

```bash
npm install
npm install -g newman newman-reporter-allure
```

### 3. Run Tests

Via npm scripts (recommended):

```bash
# Positive test only
npm run test:positive

# Negative test only (data-driven)
npm run test:negative

# All tests
npm run test:all
```

Or via Newman directly:

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

### 4. Generate & View Allure Report

```bash
npm run test:report
npm run test:serve
```

Or directly:

```bash
allure serve allure-results
```

---

## Project Structure

```
api-automation-auth/
├── .github/workflows/
│   └── api-test.yml           # GitHub Actions CI/CD pipeline
├── gitlab-ci.yml              # GitLab CI alternative config
├── api-automation/
│   ├── collections/auth/
│   │   └── auth.postman_collection.json   # Main collection (negative tests)
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

- **Allure Report:** https://dimasindraa1.github.io/authentication-api-automation/allure-report/
