# 🧩 Ansible Deploy Project

This project demonstrates **automated server provisioning and web application deployment** using **Ansible**.  
It sets up and manages web servers (using Nginx) with simple, reusable playbooks.  

---

## 🚀 Project Overview

The goal of this project is to:
- Automate web server setup using Ansible.
- Deploy a simple static web application.
- Showcase Infrastructure-as-Code (IaC) using YAML playbooks.
- Demonstrate multi-host configuration and automation with minimal manual effort.

---

## ⚙️ Tech Stack

| Component | Description |
|------------|-------------|
| **Ansible** | Configuration management and automation tool |
| **Ubuntu (WSL)** | Local testing environment |
| **Nginx** | Web server used for hosting static app |
| **YAML** | Declarative syntax for defining playbooks |

---

## 🧱 Project Structure

```
ansible-deploy-project/
├── ansible.cfg                 # Ansible configuration file
├── inventory/
│   ├── hosts.ini               # Local inventory (ignored from Git)
│   └── hosts.sample.ini        # Example inventory file
├── playbooks/
│   ├── setup.yml               # Installs Nginx and updates packages
│   └── deploy.yml              # Deploys web app to /var/www/html
├── app/
│   └── index.html              # Sample web application
├── roles/                      # Placeholder for reusable roles
├── .gitignore                  # Ignored files (sensitive data)
└── README.md                   # Project documentation
```

---

## 🧾 How to Run the Project

### 1️⃣ Prerequisites

- **Windows 10/11** with **WSL (Ubuntu)** enabled  
- **Ansible** installed inside Ubuntu  
- Basic knowledge of SSH and YAML

Install Ansible:

```bash
sudo apt update
sudo apt install ansible -y
```

---

### 2️⃣ Setup Inventory File

Create or edit `inventory/hosts.ini`:

```ini
[webservers]
server1 ansible_host=<your_server_ip> ansible_user=<your_username>
server2 ansible_host=<your_server_ip> ansible_user=<your_username>
```

*(Keep your private inventory file out of GitHub!)*

---

### 3️⃣ Test Connection

```bash
ansible all -i inventory/hosts.ini -m ping --ask-pass
```

Expected output:
```
server1 | SUCCESS => { "ping": "pong" }
server2 | SUCCESS => { "ping": "pong" }
```

---

### 4️⃣ Run Playbooks

**Setup server:**
```bash
ansible-playbook -i inventory/hosts.ini playbooks/setup.yml --ask-pass --ask-become-pass
```

**Deploy web app:**
```bash
ansible-playbook -i inventory/hosts.ini playbooks/deploy.yml --ask-pass --ask-become-pass
```

---

### 5️⃣ Verify Deployment

Run this command to confirm Nginx is serving your app:
```bash
ansible all -i inventory/hosts.ini -a "curl -I http://localhost" --become
```

Expected output:
```
HTTP/1.1 200 OK
Server: nginx/1.24.0 (Ubuntu)
```

---

## 🧰 Key Learnings

- Automating infrastructure setup with Ansible.
- Using playbooks for consistent deployments.
- Managing multiple servers via inventory groups.
- Understanding SSH-based provisioning.
- Separating sensitive configurations for secure version control.

---
## 🧾 Output Screenshots
<img width="1906" height="949" alt="image" src="https://github.com/user-attachments/assets/2c60ad46-870b-457d-9808-7e2854393a9e" />



## 🧑‍💻 Author

**Sravani Martha**  
Ansible Automation Project 

---

## 🪪 License

This project is open-source under the **MIT License**.  
Feel free to clone, modify, and reuse it for learning or demonstration purposes.
