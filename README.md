# Ansible Capstone Project – Apache, Nginx, and Java Roles

## 📌 Project Overview
This project is part of my **DevOps Capstone using Ansible**, where I automated the configuration and deployment of web and application servers using **Ansible roles**.  
It demonstrates **infrastructure automation, environment grouping, and role-based provisioning** across multiple EC2 instances on AWS.

---

## 🚀 Objectives
- Set up a **5-node Ansible cluster** (1 control node + 4 managed nodes).  
- Divide servers into two groups:  
  - **Apache Group (App Servers)** → Install Apache + Java.  
  - **Nginx Group (Web Servers)** → Install Nginx.  
- Use **Ansible roles** for modular automation:
  - `apache-role` → Installs Apache, deploys custom HTML.  
  - `nginx-role` → Installs Nginx, deploys custom HTML.  
  - `java-role` → Installs Java on Apache group.  
- Deploy **custom web pages** for each group.  
- Ensure all services are **enabled and running**.  
- Demonstrate **real-world DevOps practices** with infrastructure-as-code.

---

## 🏗️ Infrastructure Setup
- **Control Node**: Ubuntu 24.04 LTS (Ansible installed)  
- **Managed Nodes (AWS EC2 Ubuntu 24.04 LTS)**:
  - Slave1 → Apache + Java
  - Slave3 → Apache + Java
  - Slave2 → Nginx
  - Slave4 → Nginx  

- **Inventory File**:
```ini
[apache]
172.31.90.22
172.31.92.165

[nginx]
172.31.93.2
172.31.81.84

[all:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=/home/ubuntu/ansible-key.pem
⚙️ Roles & Playbooks
Apache Role (roles/apache-role)

Installs Apache

Deploys custom index.html

Starts and enables Apache

Prints a success message

Nginx Role (roles/nginx-role)

Installs Nginx

Deploys custom index.html

Starts and enables Nginx

Prints a success message

Java Role (roles/java-role)

Installs Java (default-jdk)

Prints a success message

Capstone Playbook (capstone-playbook.yml)
---
- name: Configure Apache group
  hosts: apache
  become: yes
  roles:
    - apache-role
    - java-role

- name: Configure Nginx group
  hosts: nginx
  become: yes
  roles:
    - nginx-role

✅ Verification
Apache Group

Apache running:

systemctl status apache2


Java installed:

java -version


Custom page deployed:

curl http://<apache-public-ip>

Nginx Group

Nginx running:

systemctl status nginx


Custom page deployed:

curl http://<nginx-public-ip>

📊 Outcome

Automated provisioning of a 4-node cluster with Ansible.

Successfully installed and configured Apache, Nginx, and Java using roles.

Deployed custom static web pages to both server groups.

Demonstrated real-world Infrastructure as Code (IaC) practices.

🔑 Key Learnings

Grouping servers in Ansible inventory for environment-based provisioning.

Writing modular, reusable roles.

Deploying static content and application runtimes via automation.

Using Ansible as a configuration management tool in a cloud environment.

👨‍💻 Author

Vishnu S
DevOps Engineer | WordPress & Cloud Enthusiast
LinkedIn
 | GitHub
