

# Automated Nexus Repository Manager with Ansible & Docker

This project automates the deployment and configuration of **Sonatype Nexus Repository Manager** on a Linux environment (Worker Node) using **Ansible**. It also sets up a **Private Docker Registry** to store and manage custom container images locally.

## 🚀 Project Overview

The goal of this project is to build a professional DevOps infrastructure that allows:

* **Automation:** Installing Java and Nexus without manual intervention.
* **Persistence:** Running Nexus as a dedicated system service (`systemd`).
* **Security:** Running the application under a non-root user and managing firewall rules.
* **Private Registry:** Hosting a local Docker registry on port `5000` to speed up image transfers within a Local Area Network (LAN).

## 🛠 Tech Stack

* **Ansible:** For Infrastructure as Code (IaC) and automation.
* **Docker:** For containerization and image management.
* **Nexus Repository Manager:** For hosting Docker images and build artifacts.
* **Linux (CentOS/RHEL/Ubuntu):** As the host operating system.

## 📁 Key Components

* **Nexus Setup:** Automated download, extraction, and user permission handling.
* **Systemd Integration:** Custom service file with `Restart=on-abort` and `LimitNOFILE=65536` for high availability.
* **Firewall Configuration:** Automatically opening ports `8081` (UI) and `5000` (Docker).
* **Docker Integration:** Configuration of `daemon.json` to allow insecure local registries.

## 📖 How to Use

1. **Clone the repo:** `git clone <your-repo-url>`
2. **Update Inventory:** Add your Worker Node IP to the `hosts` file.
3. **Run the Playbook:** ```bash
ansible-playbook -i hosts nexus-setup.yml
4. **Access Nexus:** Open `http://<worker-ip>:8081` in your browser.
5. **Push your first image:**
```bash
docker tag my-image:latest <worker-ip>:5000/my-image:latest
docker push <worker-ip>:5000/my-image:latest

```




