# 🔒 Tomcat9SSLConfig (Fortify SSC Tomcat 9.x SSL Configuration Script)

This script automates the process of **configuring Secure Sockets Layer (SSL)** for an **Apache Tomcat 9.x** instance running the **Fortify Software Security Center (SSC)** web application on a Linux system.
It creates and applies self-signed SSL certificates, updates Tomcat configuration files, modifies Fortify SSC settings, and ensures the service runs securely over HTTPS.

---

## ⚙️ Features

* 🔑 Automatically generates private key and certificate files.
* 🧩 Creates PKCS#12 (`.p12`) keystore for Tomcat integration.
* 🛡️ Adds certificate to the system's trusted CA store.
* 🔗 Inserts SSL Connector configuration in `server.xml`.
* 🧱 Updates Fortify SSC `app.properties` with the new HTTPS URL.
* ⚙️ Enables SOAP API support in SSC.
* 🔁 Restarts Tomcat service after SSL configuration.

---

## 🧾 Requirements

* 🐧 Linux-based OS (RHEL, CentOS, Ubuntu, etc.).
* 🔧 `openssl`, `awk`, `sed`, and `systemctl` installed.
* 🌍 Proper permissions to manage the Tomcat service and modify system CA.
* 📄 `.env` file configured with the following variables:

The values are at the discretion of each user.

```makefile
CERTIFICATES_DIR=                                 # Directory where the certificate files for Fortify SSC are stored
APP_PROPERTIES_FILE=                              # Directory where the app.properties file from Fortify SSC is stored
SCRIPT_DIR=                                       # Directory where this script is stored
FORTIFY_SSC_KEY_FILE=                             # Private key file for Fortify SSC SSL
FORTIFY_SSC_CERTIFICATE_FILE=                     # Certificate file for Fortify SSC SSL
FORTIFY_SSC_PEM_FILE=                             # PEM file for Fortify SSC SSL
FORTIFY_SSC_P12_FILE=                             # P12 file for Fortify SSC SSL
FORTIFY_SSC_CERTIFICATE_DAYS_VALID=               # Fortify SSC SSL Certificate validity (in days)
FORTIFY_SSC_CERTIFICATE_KEY_SIZE=                 # Fortify SSC SSL Key size (e.g., 2048)
FORTIFY_SSC_CERTIFICATE_PASSWORD=                 # Fortify SSC SSL Certificate password
FORTIFY_SSC_HOST_NAME=                            # Hostname of the machine where Fortify SSC is deployed
FORTIFY_SSC_IP_ADDRESS=                           # IP Address of the machine where Fortify SSC is deployed
FORTIFY_SSC_CERTIFICATE_COUNTRY=                  # Country code for SSL Certificate
FORTIFY_SSC_CERTIFICATE_STATE=                    # State or province for SSL Certificate
FORTIFY_SSC_CERTIFICATE_LOCALITY=                 # City or locality for SSL Certificate
FORTIFY_SSC_CERTIFICATE_ORGANIZATION=             # Organization name for SSL Certificate
FORTIFY_SSC_CERTIFICATE_ORGANIZATION_UNIT=        # Organizational Unit for SSL Certificate
FORTIFY_SSC_CERTIFICATE_COMMON_NAME=              # Common Name for SSL Certificate (usually the hostname)
FORTIFY_SSC_CERTIFICATE_EMAIL=                    # Contact email for SSL Certificate
FORTIFY_SSC_CERTIFICATE_SAN_VALUE=                # Subject Alternative Name (SAN) value (DNS and IP)
FORTIFY_SSC_CERTIFICATE_SUBJECT=                  # Subject string for SSL Certificate
FORTIFY_SSC_TOMCAT_DIR=                           # Directory where Fortify SSC Tomcat is installed
FORTIFY_SSC_TOMCAT_SERVER_FILE=                   # Path to Tomcat server.xml file
APP_ALIAS=                                        # Fortify SSC webapp alias (e.g., ssc)
HTTP_PORT=                                        # Fortify SSC HTTP Port (default: 8080)
HTTPS_PORT=                                       # Fortify SSC HTTPS Port (default: 8443)
FORTIFY_SSC_OLD_HOST_URL=                         # Fortify SSC HTTP URL
FORTIFY_SSC_NEW_HOST_URL=                         # Fortify SSC HTTPS URL
```

---

## 🗂️ Directory Structure

```
Tomcat9SSLConfig/
|     ├── tomcat9_ssl_config.sh      # Script that applies the SSL configuration on Apache Tomcat 9 for Fortify SSC.
|     └── .env                       # Environment variables file used by the Apache Tomcat 9 SSL configuration script. 
└──────────────────────────────
```

---

## 🧰 Usage

1. **Ensure environment variables are defined** in a `.env` file.
2. Make the script executable:

   ```bash
   chmod +x tomcat9_ssl_config.sh
   ```
3. Run the script:

   ```bash
   ./tomcat9_ssl_config.sh
   ```

---

## 🧱 Components Used

* 🐚 **Bash** – Automation script.
* 🧰 **OpenSSL** – Certificate and key generation.
* 🐱 **Apache Tomcat 9.x** – Application server.
* 🛡️ **Fortify Software Security Center (SSC)** – Secure code analysis web app.

---

## 📝 Notes

* The script **detects if SSL is already configured** and exits gracefully if found.
* A `.bak` backup of `server.xml` and `app.properties` is automatically created.
* Make sure Tomcat service name matches `fortify_ssc_tomcat` in your systemd unit.

---

## 🧾 License

This project is part of the **Fortify SSC Scripts Utilities** suite.
Use according to your organization’s internal deployment and licensing guidelines.
