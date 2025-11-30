# Frank Cloud Lab – Anime Themed EC2 Portfolio

This is my **first real cloud project**: an anime-styled portfolio website
running on an **AWS EC2 Ubuntu server** with **Nginx**.

The goal of this project was to move beyond tutorials and actually deploy
something the whole internet can visit, while learning the basics of
cloud infrastructure, Linux, and web servers.

---

## 🌐 Live Demo

> Hosted on an EC2 instance (public IP may change):  
> `http://13.60.166.204`

---

## 🏗 Architecture

- **Client:** Any web browser (HTTP)
- **Internet**
- **AWS EC2 (Ubuntu Server)**
  - Nginx web server
  - Custom anime-themed HTML/CSS portfolio
- **Security Group rules:**
  - `22/tcp` – SSH (restricted)
  - `80/tcp` – HTTP (open to the world)

---

## 🛠 Tech Stack

- AWS EC2 (Free Tier)
- Ubuntu Linux
- Nginx
- SSH & key pairs
- Security Groups
- HTML & CSS (anime UI style)
- `nano` + Linux CLI

---

## 🚀 Deployment Steps (Summary)

### 1. Launch EC2 instance
- AMI: **Ubuntu Server 22.04 LTS**  
- Instance type: **t2.micro** (free tier)  
- Created key pair (`.pem`)  
- Security Group rules:
  - SSH (22) — from my IP  
  - HTTP (80) — open to the world (`0.0.0.0/0`)

---

### 2. Connect via SSH + Install & Start Nginx

```bash
# Connect to EC2
chmod 400 frank-key.pem
ssh -i frank-key.pem ubuntu@13.60.166.204

# Install & start Nginx
sudo apt update -y
sudo apt install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx

### 3. Deploy Anime Portfolio Page

```bash
# Open the default web root file
sudo nano /var/www/html/index.html

# Paste your Anime HTML manually
# Save with: CTRL + O, ENTER
# Exit with: CTRL + X

# Reload Nginx after saving the file
sudo systemctl reload nginx

### 4. Test the Website

```bash
# Open your website in the browser
# http://13.60.166.204

# Optional: Verify Nginx is running correctly
sudo systemctl status nginx
