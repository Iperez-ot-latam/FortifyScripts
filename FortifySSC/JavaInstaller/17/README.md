# ☕ Java OpenJDK 17 Installation Script

This Bash script automates the installation of **Java OpenJDK 17** on Linux systems using **DNF**, ensuring the environment is properly configured with `JAVA_HOME` and the latest Java binaries.

---

## ✨ Features

* Checks if Java 17 is already installed.
* Automatically installs **OpenJDK 17** and **OpenJDK 17 Development Kit**.
* Updates the system packages before installation.
* Sets up the `JAVA_HOME` environment variable system-wide.
* Adds `JAVA_HOME` to `/etc/environment` for persistent configuration.
* Prompts for a reboot after successful installation.

---

## 🧩 Requirements

* Linux distribution with **DNF package manager**.
* Root or sudo privileges.
* Internet connectivity for downloading packages.

---

## 🚀 Usage Overview

1. **Clone or copy** the script to your system:

   ```bash
   git clone https://github.com/your-repo/FortifyScripts.git
   cd FortifyScripts/JavaInstallation
   ```

2. **Make the script executable:**

   ```bash
   chmod +x java_17_installer.sh
   ```

3. **Run the script as root or with sudo:**

   ```bash
   ./java_17_installer.sh
   ```

4. **Follow on-screen prompts:**

   * If Java 17 is already installed, it will exit safely.
   * Otherwise, it will:

     * Update your system packages
     * Install Java 17
     * Set `JAVA_HOME`
     * Optionally reboot your system

---

## 🗂️ Directory Structure

```
JavaInstallation/
|   ├── 17/                             # Directory for Java version to install
|   └── java_openjdk17_install.sh       # Main installation script
└────────────────────────────────
```

---

## 📝 Notes

* If you modify `/etc/environment` manually, ensure no duplicate `JAVA_HOME` entries exist.
* The script dynamically determines your Java installation path and applies it automatically.
* To verify installation after reboot:

  ```bash
  echo $JAVA_HOME
  java -version
  ```

---


## 🧾 License

This project is part of the **Fortify SSC Scripts Utilities** suite.
Use according to your organization’s internal deployment and licensing guidelines.
