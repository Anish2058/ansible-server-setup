# Ansible LAMP & Docker Automation Project

This project automates the setup of a **LAMP stack (Linux, Apache, MySQL, PHP)** and **Docker** on a remote Ubuntu VM using **Ansible**. The automation is done entirely through Infrastructure as Code (IaC), allowing repeatable and consistent server provisioning.

## Project Structure

ansible-server-setup/
├── ansible.cfg # Ansible configuration file
├── inventory.ini # Inventory with remote host details
├── playbooks/
│ ├── lamp.yml # Playbook to install Apache, MySQL, PHP
│ └── docker.yml # Playbook to install Docker
├── roles/
│ ├── lamp/
│ │ └── tasks/main.yml # Tasks for LAMP installation
│ └── docker/
│ └── tasks/main.yml # Tasks for Docker installation
└── README.md # Project documentation


---

## Features

Automates LAMP stack setup:  
- Apache2  
- MySQL  
- PHP & common modules

Installs and enables Docker engine

Modular role-based Ansible structure

SSH key-based connection (no password login)

Ubuntu 24.04 compatible (host and VM)

---

## Tools & Technologies

- [Ansible](https://www.ansible.com/)
- Ubuntu (host + guest)
- Docker
- Apache, MySQL, PHP
- YAML, SSH
- VirtualBox or any VM platform

---

## Getting Started

###  Generate SSH Key and Copy to VM
```bash
ssh-keygen
ssh-copy-id -p 2222 anton@127.0.0.1

# Run LAMP playbook
ansible-playbook -i inventory.ini playbooks/lamp.yml --ask-become-pass

# Run Docker playbook
ansible-playbook -i inventory.ini playbooks/docker.yml --ask-become-pass

# Inside VM (ssh anton@127.0.0.1 -p 2222)
systemctl status apache2
docker --version
