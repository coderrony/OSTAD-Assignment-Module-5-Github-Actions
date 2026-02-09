# 🚀 CI/CD Pipeline with GitHub Actions & Self-Hosted Runner--&

This repository contains the submission for **Module 5 Assignment**, focused on implementing a full CI/CD pipeline. The pipeline automates testing, artifact management, and deployment of a Node.js application to a self-hosted environment (AWS EC2).

## 📌 Project Overview
The primary objective of this project is to demonstrate how to utilize **GitHub Actions** to create a professional deployment workflow.

### 🌟 Key Features:
- **Automated Testing:** Runs application checks on every push.
- **Artifact Management:** Captures and stores test reports for later review.
- **Continuous Deployment:** Automatically deploys the latest code to an AWS EC2 instance.
- **Process Management:** Uses **PM2** to ensure the application remains online 24/7.

---

## 🛠️ Tech Stack
- **Backend:** Node.js, Express
- **CI/CD:** GitHub Actions
- **Hosting:** AWS EC2 (Ubuntu)
- **Process Manager:** PM2
- **Runner:** Self-hosted GitHub Runner

---

## 🏗️ Workflow Structure
The workflow is defined in `.github/workflows/deploy.yml` and consists of two primary jobs:

### 1. Test Job
- **Environment:** Self-hosted Ubuntu Server.
- **Actions:** - Installs Node.js and dependencies.
  - Runs `npm run check` to verify code integrity.
  - Captures output into `test-results.txt`.
  - **Artifact:** Uploads the test report to GitHub.

### 2. Deploy Job
- **Dependency:** Only runs if the Test Job succeeds.
- **Actions:**
  - Downloads the `test-results-artifact`.
  - Displays test results in the workflow log.
  - Pulls the latest code to the deployment directory.
  - Installs production dependencies.
  - Restarts the application using **PM2**.

---

## 🚀 How to Access
Once the pipeline execution is finished, the application is accessible at:
- **URL:** `http://13.201.64.47:3000`

---

## 📂 Repository Structure
```text
├── .github/workflows/
│   └── deploy.yml          # CI/CD Pipeline Definition
├── src/
│   ├── server.js           # Express Server Logic
│   └── public/             # Static Assets
├── test/                   # Application Tests
├── package.json            # Dependencies & Scripts
└── README.md               # Project Documentation
