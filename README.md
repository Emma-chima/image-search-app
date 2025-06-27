# Image Search Webserver with Ansible

A hands-on project combining **Ansible automation** and a **client-side image search app** built with Vanilla JavaScript. This was my personal journey to master infrastructure provisioning and web deployment.

---

## 🔍 Project Overview

- 🖥️ **What it does**  
  - Provision AWS infrastructure (VPC, Subnet, Security Group, EC2) using Ansible and cloud-init.
  - Deploy Apache on the EC2 instance and serve a fully self-contained `index.html`.
  - Provide a single-page image search application that queries the Unsplash API, displays results in a responsive grid, and supports paginated loading.

- 🎯 **Why I built this**  
  As part of my goal to deepen my understanding of Ansible and cloud automation, I wanted to:
  1. Learn to **automate AWS infrastructure** with configuration-as-code.
  2. Embed a **simple, interactive front-end** delivered via Apache.
  3. Overcome real-world challenges integrating DevOps and client-side web.

---

## 🛠️ Features

1. **Full AWS provisioning** via Ansible playbook:
   - VPC, Subnet, Internet Gateway, Route Table
   - Security Group allowing HTTP (80), HTTPS (443), SSH (22)
   - EC2 launch with cloud-init for automatic Apache + app installation

2. **Vanilla JS Image Search App**:
   - Search Unsplash photos by keyword
   - Responsive grid of images with hover and click-to-expand
   - “Show more” button for pagination
   - Handles empty queries and errors gracefully

3. **Professional setup**:
   - Secure handling of AWS credentials via Ansible Vault
   - Clean project structure and a ready-to-use `README.md`
   - Potential to deploy web front-end to GitHub Pages

---

## 🧠 Challenges & Solutions

### 1. Shell Script Compatibility

**Problem**: The initial `bootstrap.sh.j2` script was designed for Amazon Linux 2023, but the server used Ubuntu.

**Solution**: Switched to an Ubuntu AMI that ships with cloud-init for reliable execution.

### 2. JavaScript Functionality Issue

**Problem**: After merging multiple JavaScript files, the `.map` function was overwritten, causing the image search to fail.

**Solution**: Refactored the code to use `.forEach` and ensured the markup append logic retained all results.

---

## 📁 File Structure
├── ansible/
│ ├── ansible.cfg
│ ├── bootstrap.sh.j2 # cloud-init script for EC2 bootstrap
│ └── playbook.yml # Ansible provisioning playbook
├── webapp/
│ └── index.html # Vanilla JS image search app
├── .gitignore
└── README.md



- Sensitive files like `vault.yml` are intentionally excluded and encrypted.

---

## 🚀 Quick Start

1. **Clone the repo:**
   ```bash
   git clone https://github.com/Emma-chima/image-search-app.git
   cd image-search-app/ansible
   ```

2. **Provision the EC2 server:**
    ```bash
    ansible-playbook playbook1.yml -K
    ```
    - Runs AWS infra provisioning and deploys the search app

    - Enter your sudo password when prompted

3. **Test the app:**

    - Open the EC2 instance’s public IP or DNS in your browser

    - The Image Search App should load and function out-of-the-box


**💻 Local Front-End (Optional)**
To run the client-side app locally:

Copy webapp/index.html to your local folder.

Open it in your browser—no server or build tools required.

Add your Unsplash API access key in the script.


**⚡ License**
This project is released under the MIT License. Feel free to use, modify, and distribute!


**🤝 About Me**
This repository is part of my learning journey in Ansible, cloud provisioning, and web development. I’m excited to grow and refine these skills, feedback and star ❤️ are always appreciated!