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

## 📂 Repository Structure

```text
repo-root/
├── https-site/
│   ├── docker-compose.yml   # For Nginx + SSL site
│   └── finexo-html/         # Website static files (e.g. index.html)
├── ssh-jail/
│   ├── docker-compose.yml   # For OpenSSH jail
│   └── shared/              # Shared folder for jail users
├── pf.conf                  # macOS firewall config example
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

