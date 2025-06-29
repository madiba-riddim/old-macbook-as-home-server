# 🖥️ Old MacBook Pro as Home Server / Workstation

A collection of scripts and configuration files for transforming an old MacBook Pro (or any unused Mac) into a secure home server and collaborative workstation.

## 🚀 Features

* **HTTPS Personal Website**
  Securely host your own static website using Dockerized Nginx and automated SSL certificates (Let’s Encrypt).

* **OpenSSH Server (Jail Environment)**
  Provide isolated SSH/SFTP access to team members or yourself, without exposing the rest of your Mac’s filesystem.

* **macOS Firewall Example (`pf.conf`)**
  Example `pf.conf` to control allowed ports and restrict access by IP for extra security.

* **Ready-to-Use Example Files**
  Includes an example `index.html` and sample folder structure for fast deployment.

## 📖 Full Step-by-Step Tutorial Series

For detailed guides, follow the Medium series:

- **Part 1: Secure SSH & VNC Setup**  
  [舊 Mac 筆電改造！家用伺服器／工作站架設全攻略 Part 1：安全部署、SSH 遠端連線與螢幕共享實作](https://medium.com/@madiba-riddim/%E8%88%8A-mac-%E7%AD%86%E9%9B%BB%E6%94%B9%E9%80%A0-%E5%AE%B6%E7%94%A8%E4%BC%BA%E6%9C%8D%E5%99%A8-%E5%B7%A5%E4%BD%9C%E7%AB%99%E6%9E%B6%E8%A8%AD%E5%85%A8%E6%94%BB%E7%95%A5-part-1-%E5%AE%89%E5%85%A8%E9%83%A8%E7%BD%B2-ssh-%E9%81%A0%E7%AB%AF%E9%80%A3%E7%B7%9A%E8%88%87%E8%9E%A2%E5%B9%95%E5%85%B1%E4%BA%AB%E5%AF%A6%E4%BD%9C-30743ddcf522)

- **Part 2: Website Hosting & Shared Workspace**  
  [舊 Mac 筆電改造！家用Server／工作站架設全攻略 Part 2：架設個人網站、設置共享專案空間](https://medium.com/@madiba-riddim/%E8%88%8A-mac-%E7%AD%86%E9%9B%BB%E6%94%B9%E9%80%A0-%E5%AE%B6%E7%94%A8server-%E5%B7%A5%E4%BD%9C%E7%AB%99%E6%9E%B6%E8%A8%AD%E5%85%A8%E6%94%BB%E7%95%A5-part-2-%E6%9E%B6%E8%A8%AD%E5%80%8B%E4%BA%BA%E7%B6%B2%E7%AB%99-%E8%A8%AD%E7%BD%AE%E5%85%B1%E4%BA%AB%E5%B0%88%E6%A1%88%E7%A9%BA%E9%96%93-8e9fc42f7337)

- **Part 3: Firewall (pf) Settings**  
  [舊 Mac 筆電改造！家用Server／工作站架設全攻略 Part 3：設置防火牆免於外部惡意攻擊](https://medium.com/@madiba-riddim/%E8%88%8A-mac-%E7%AD%86%E9%9B%BB%E6%94%B9%E9%80%A0-%E5%AE%B6%E7%94%A8server-%E5%B7%A5%E4%BD%9C%E7%AB%99%E6%9E%B6%E8%A8%AD%E5%85%A8%E6%94%BB%E7%95%A5-part-3-%E8%A8%AD%E7%BD%AE%E9%98%B2%E7%81%AB%E7%89%86%E5%85%8D%E6%96%BC%E5%A4%96%E9%83%A8%E6%83%A1%E6%84%8F%E6%94%BB%E6%93%8A-b88a38fdbb7b)

## 📂 Repository Structure

```text
repo-root/
├── https-site/
│   ├── docker-compose.yml   # For Nginx + SSL site
│   └── finexo-html/         # Website static files (e.g. index.html)
├── ssh-jail/
│   ├── docker-compose.yml   # For OpenSSH jail
│   └── shared/              # Shared folder for jail users
├── firewall/
│   └── pf.conf              # macOS firewall config example
└── README.md
```

## ⚡ Quick Start

### 1. HTTPS Website with Docker

1. Install [Docker Desktop for Mac](https://docs.docker.com/desktop/install/mac/).
2. Clone this repository and navigate to `https-site`.
3. Edit `docker-compose.yml`:

   * Set `VIRTUAL_HOST`, `LETSENCRYPT_HOST` to your domain or DDNS.
   * Set `LETSENCRYPT_EMAIL` to your email.
4. Place your website files (e.g. `index.html`) in `finexo-html/`.
5. Run:

   ```bash
   docker compose up -d
   ```
6. Set up port forwarding (ports 80, 443) on your router to your Mac’s local IP.

### 2. OpenSSH Jail for Team Sharing

1. Navigate to `ssh-jail`.
2. Edit `docker-compose.yml`:

   * Set desired `USER_NAME` and `USER_PASSWORD`.
3. Run:

   ```bash
   docker compose up -d
   ```
4. Set up port forwarding (e.g., 2200) on your router to your Mac.

### 3. macOS Firewall

* Example `pf.conf` is provided for advanced users who want to restrict network access at the OS level.
  **Note:** Always back up your current firewall config before applying changes.

## 🔒 Security Tips

* Use SSH keys for admin accounts, disable password login where possible.
* Change all default passwords before exposing services.
* Restrict allowed IP addresses with `pf.conf` or at the router.
* Regularly update Docker images and Mac system software.

## 📝 License

MIT License.

## 🙌 Credits

* Inspired by open-source projects and guides from the Docker, Nginx, and OpenSSH communities.

## 💬 Feedback / Questions

If you have issues or suggestions, feel free to open an issue or start a discussion!

