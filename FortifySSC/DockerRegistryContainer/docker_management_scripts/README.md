# 🐳 DockerRegistryContainer (Private Docker Registry)

This directory contains the configuration files, certificates, and management scripts used to deploy and maintain the **private Docker Registry** that stores Fortify-related docker container images.

## 📁 Directory Structure

```
DockerRegistryContainer/
├── auth/                         # Authentication files (htpasswd --> authentication file used by the Docker Registry (nginx) for basic HTTP authentication).
├── certificates/                 # SSL/TLS self-signed certificates for secure HTTPS access to the Docker Registtry (BackEnd and FrontEnd).
├── docker_management_scripts/    # Shell scripts to build and destroy the Docker Registry containers (BackEnd and FrontEnd).
└── registry_ui_https_config/     # Configuration file for the Docker Registry UI over HTTPS.
```

---

## ⚙️ Purpose

The **Private Docker Registry Container** provides a self-hosted, secured Docker Registry used to:

* Stores Fortify SSC, ScanCentral, and related Docker images privately.
* Authenticates users via the `auth/` configuration (Basic one).
* Serves the registry and its UI over HTTPS using the `certificates/` and `registry_ui_https_config/` directories.
* Automate the Docker Registry containers/images management (build and destroy) using the scripts in `docker_management_scripts/` directory.

---

## 🚀 Usage Overview

1. **Generate or update certificates**

   * Already done by the `nacho_docker_registry_builder.sh` script that places the `.crt`, `.key` and `.pem` files in the `certificates/` directory for each environment of the Docker Private Registry. 

2. **Configure authentication**

   * The `nacho_docker_registry_builder.sh` script creates a `.htpasswd` file and places it on the `auth/` directory to have a basic authentication login on the Docker Private Registry.

3. **Creates the Docker Registry BackEnd and Docker Registry FrontEnd docker containers**

   * When running the script:

     ```bash
     ./nacho_docker_registry_builder.sh.sh
     ```
   * It creates both Docker Containers with the previous settings + a network and assigns an IP for each Docker Container *

4. **Access the Registry UI (Docker Registry UI)**

   * Open: `https://<server_ip>` (configured)
   * Log in with your configured credentials with basic authentication (twice if you don't log in in the Docker Registry Back End before).

5. **Access the Registry BackEnd (Docker Registry)**

   * Open: `https://<server_ip>:5000/v2/_catalog` (or configured port)
   * Log in with your configured credentials with basic authentication.

---

## 🧰 Requirements

* Docker Engine installed and running.
* Valid SSL certificates.
* Proper authentication and nginx config file.
* Proper permissions on the directories.

---

## 🧹 Maintenance Tips

* Renew SSL certificates before expiration.
* Rotate the basic authentication credentials periodically.
* Destroy and rebuild the Docker Containers with the updated docker registry image.
* Keep `docker_management_scripts/` synchronized with the automated GitHub repository.
