# 🌐 Personal Website Infrastructure

This repo contains all the infrastructure code that powers my personal website **thanaphatj.me**.
Everything here is built using **AWS CloudFormation** and follows a simple goal:

👉 *Make a fast, secure, and cheap static website*
👉 *Run entirely on AWS with almost zero maintenance*

---

## 🚀 What This Stack Includes

This setup uses a classic (but modern + secure) AWS architecture:

* **Amazon S3** – stores the static website files (HTML, CSS, JS)
* **CloudFront** – global CDN that serves the website fast everywhere
* **OAC (Origin Access Control)** – ensures only CloudFront can read from S3
* **ACM Certificate (us-east-1)** – handles HTTPS for my domain
* **Route 53** – DNS routing for `thanaphatj.me` and `www.thanaphatj.me`

No servers, no backend, no manual deployments. Just fully serverless and easy.

---

## 🏗️ Architecture Diagram

Here’s the overall structure of the infrastructure:

![Architecture Diagram](assets/personal-web-application.drawio.svg)

## 📦 What’s Inside the CloudFormation Template

* Creates or connects to an **existing S3 bucket**
* Deploys a **CloudFront distribution** with:

  * HTTPS using ACM cert
  * Caching + compression enabled
* Adds **Route 53 A records** for:

  * thanaphatj.me
  * [www.thanaphatj.me](http://www.thanaphatj.me)
* Sets up an S3 bucket policy that only allows CloudFront (via OAC) to access content

Basically everything needed for a secure static site.

---

## 💰 Cost

The whole setup is very cheap:

* CloudFront: usually < $1–2 / month unless huge traffic
* Route 53 hosted zone: $0.50 / month

Perfect for a personal website.
