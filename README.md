# 🚛 LabOdoo as a Service (`LaaS`)

[![Podman Ready](https://img.shields.io/badge/Podman-Engine-892CA0?style=for-the-badge&logo=podman&logoColor=white)](https://podman.io)
[![Docker Compatible](https://img.shields.io/badge/Docker-Compatible-2496ED?style=for-the-badge&logo=docker&logoColor=white)](https://www.docker.com/)
[![Odoo Powered](https://img.shields.io/badge/Odoo-ERP_Orchestration-714B67?style=for-the-badge&logo=odoo&logoColor=white)](https://www.odoo.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

> ⚡ **A modular, containerized microservices stack to orchestrate, control, and deploy custom LabOdoo educational environments seamlessly.**

---

## 📖 Introduction

**LabOdoo as a Service (LaaS)** abstracts the entire technical infrastructure needed to run a **LabOdoo** mobile educational workshop into a lightweight, containerized microservices architecture.

By leveraging `podman-compose`, **LaaS** encapsulates networking, routing, mail handling, database persistence, and Odoo instance management into isolated, reproducible containers. This decoupled setup allows you to spin up portable, multi-tenant interactive learning environments on any Linux host—whether offline in a mobile workshop truck, inside a high school lab, or on a local server—with a single command! 🚀

### 🌟 Key Highlights

* **🧱 Microservice Abstraction:** Every layer (DNS, Mail, Proxy, Database, Orchestrator) is completely decoupled for maximum flexibility and maintenance ease.
* **🔒 Rootless & Secure:** Built natively for `podman` and `podman-compose` to support rootless container execution with minimal privileges.
* **🧠 HiveMind Orchestration:** Automated dynamic lifecycle management to spawn, configure, and reset Odoo instances on the fly for student workshops.
* **🔌 Plug & Play:** Zero-headache network configuration with integrated lightweight local DNS & DHCP services.

---

## 🛠️ Prerequisites & Installation

To run **LabOdoo as a Service**, make sure your host system has **Podman** (or standard Docker) and **Podman-Compose** installed.

### 🐧 Debian / Ubuntu & Derivatives

Install the required packages directly via `apt`:

```bash
sudo apt update && sudo apt install -y podman podman-compose
```

> 💡 *Note: If you prefer Docker over Podman, `docker-compose` can be used out-of-the-box as an drop-in alternative!*

---

## 🏗️ Microservices Breakdown

Here is an overview of the microservices composing the **LaaS** ecosystem:

| Icon | Service | Technology | Role & Description |
| :---: | :--- | :--- | :--- |
| 🌐 | **DNS & DHCP** | `DNSmasq` | Handles local `DHCPv4` IP allocation and lightweight internal `DNS` resolution for workshop clients. |
| 🔀 | **Reverse Proxy** | `NGINX` | High-performance Web Server directing HTTP/HTTPS traffic, routing host headers, and handling SSL termination. |
| 🧠 | **Orchestrator** | `HiveMind` | The central brain powering the primary Odoo server and dynamically managing student instance lifecycles. |
| ✉️ | **Mail Transfer** | `Postfix` | Outbound `SMTP` server enabling simulated corporate emailing workflows and Odoo notifications. |
| 📥 | **Mail Storage** | `Dovecot` | Secure `IMAP/POP3` inbox server managing user mailboxes across virtual companies. |
| 🐘 | **DBMS** | `PostgreSQL` | Relational database engine providing fast, isolated data storage for all Odoo databases. |

---

## 🚀 Quick Start Guide

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/labodoo-as-a-service.git
cd labodoo-as-a-service
```

### 2. Configure Environment Variables
Copy the template configuration file and adapt the parameters for your network set up:
```bash
cp .env.example .env
```

### 3. Launch the Stack 🏁
Start all microservices in detached mode:
```bash
podman-compose up -d
```

### 4. Check Microservice Status
Verify that all services are healthy and active:
```bash
podman-compose ps
```

To view live service logs:
```bash
podman-compose logs -f
```

---

## 🤝 Contributing & Support

Contributions, issue reports, and feature suggestions are always welcome! Feel free to open a Pull Request or create an Issue.

---

<p center> Made with ❤️ for the <b>LabOdoo</b> Educational Community </p>