# 🚗 AutoElite Motors Website

A modern car company website built with HTML & CSS — used for learning **Jenkins CI/CD pipelines**.

## 📁 Project Structure

```
autoelite/
├── index.html      # Main website page
├── style.css       # All styles
├── Jenkinsfile     # Jenkins pipeline definition
├── .gitignore      # Git ignore rules
└── README.md       # This file
```

## 🚀 Jenkins Pipeline Stages

| Stage | Description |
|-------|-------------|
| **Checkout** | Pulls code from GitHub |
| **Validate HTML** | Checks that required files exist |
| **Build** | Build step (static site, no compile needed) |
| **Test** | Verifies HTML content and file structure |
| **Deploy** | Copies files to deployment directory |

## 🛠️ Setup Guide

### Step 1 — Push to GitHub
```bash
git init
git add .
git commit -m "Initial commit: AutoElite Motors website"
git remote add origin https://github.com/YOUR_USERNAME/autoelite-motors.git
git push -u origin main
```

### Step 2 — Connect to Jenkins
1. Open Jenkins → **New Item**
2. Enter name: `autoelite-pipeline`
3. Select **Pipeline** → Click OK
4. Under **Pipeline** section:
   - Definition: `Pipeline script from SCM`
   - SCM: `Git`
   - Repository URL: your GitHub repo URL
   - Branch: `*/main`
   - Script Path: `Jenkinsfile`
5. Click **Save** → Click **Build Now**

### Step 3 — Watch the Pipeline Run
Jenkins will automatically run all 5 stages and show you green/red status for each.


✅ Step 1 — Basic pipeline (you are here)
⬜ Step 2 — Webhooks (auto trigger)
⬜ Step 3 — Jenkins on a cloud server (AWS/Azure)
⬜ Step 4 — Docker + Jenkins
⬜ Step 5 — Deploy to Kubernetes
⬜ Step 6 — Multi-branch pipelines
⬜ Step 7 — Jenkins shared libraries
