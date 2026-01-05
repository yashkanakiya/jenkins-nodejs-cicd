# This project demonstrates how to set up a CI/CD pipeline for a Node.js application using Jenkins, GitHub, and Docker.

## With this setup, whenever you push code to GitHub, Jenkins will automatically:

✔ Pull the latest code

✔ Build the app

✔ Run tests (if configured)

✔ Deploy the Node.js app inside a container

### 🚀 Live Setup (My Environment)

I configured everything on an Ubuntu VM:

Jenkins Dashboard URL:
👉 http://192.168.56.101:8080

Node.js App Running URL:
👉 http://192.168.56.101:3000/

Trigger Method:
🔁 GitHub Webhooks automatically trigger the CI/CD pipeline when I push changes.

### 🧠 What Is CI/CD?

CI/CD stands for:

- Continuous Integration
  
Automatically building and testing your application when new code is merged or pushed.

- Continuous Deployment/Delivery
  
Automatically deploying the new version of your application after every push.

### Jenkins is an open-source automation server that runs these pipelines. It integrates with source control systems like GitHub to:

Monitor pushes

Execute pipeline stages

Build, test, deploy software automatically


### 📁 Project Structure

.

├── Dockerfile

├── Jenkinsfile

├── app.js

├── package.json

└── README.md


### Key files:

- app.js — Node.js server file

- package.json — Metadata & dependencies

- Jenkinsfile — Defines the CI/CD pipeline

- Dockerfile — Creates a Docker image for the Node.js app

### 📌 Prerequisites

Before running this project, you should have:

✔ Jenkins installed on Ubuntu

✔ Docker installed (optional but recommended for containerized builds)

✔ GitHub repository (this one)

✔ GitHub webhook configured pointing to Jenkins

✔ Node.js and npm installed on the Jenkins server (or via Docker)

### 🛠 Setup Instructions

1️⃣ Clone the Repository

- git clone https://github.com/yashkanakiya/jenkins-nodejs-cicd
- cd jenkins-nodejs-cicd

2️⃣ Jenkins Configuration

Access Jenkins Dashboard
Visit: http://192.168.56.101:8080

Install Plugins

Git Plugin

Docker Pipeline

NodeJS Plugin

Pipeline Plugin

Configure Tools

Go to Manage Jenkins → Global Tool Configuration

Set NodeJS installation (e.g., NodeJS 18)

3️⃣ Create Jenkins Pipeline

New Item → Pipeline

Enter project name (e.g., NodeJS-App)

In Pipeline → Definition:

Choose Pipeline script from SCM

SCM: Git

Repository URL: https://github.com/yashkanakiya/jenkins-nodejs-cicd

Script Path: Jenkinsfile

4️⃣ Configure Webhook (GitHub)

Go to GitHub repository → Settings → Webhooks

Add webhook:

Payload URL: http://192.168.56.101:8080/github-webhook/

Content type: application/json

Events: Just the push event

👉 This ensures Jenkins triggers a build whenever you push code to GitHub. This is the core of continuous integration.
Medium
