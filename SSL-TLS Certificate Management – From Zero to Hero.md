# SSL/TLS Certificate Management – From Zero to Hero

## 🌟 Course Objective:

By the end of this course, learners will:
- Understand SSL/TLS basics and public key infrastructure (PKI)
- Generate, sign, install, and verify certificates
- Manage SSL/TLS in real systems (Nginx, Apache, Postfix, RabbitMQ, etc.)
- Work with self-signed and CA-signed certificates
- Automate renewals using Let's Encrypt

---

## 📚 Course Modules

### 🔹 Module 1: Introduction to SSL/TLS
- What is encryption, SSL, and TLS?
- Difference between SSL and TLS
- Symmetric vs Asymmetric encryption
- TLS handshake explained (step by step)
- Common protocols using TLS (HTTPS, SMTPS, AMQPS, etc.)

### 🔹 Module 2: Understanding Certificates & PKI
- What is a certificate?
- Anatomy of a certificate (PEM, DER, CRT, etc.)
- Public vs Private key
- Certificate Signing Request (CSR)
- Root CA vs Intermediate CA
- PKI architecture

### 🔹 Module 3: Generating Keys and Certificates (Hands-On)
- Generate private key (`openssl genrsa`, `openssl ecparam`)
- Generate CSR (`openssl req`)
- Create self-signed certificate
- View certificate contents (`openssl x509 -in ...`)
- Validate key matches cert

### 🔹 Module 4: Working with Certificate Authorities
- Submit CSR to public CA (e.g., Sectigo, DigiCert)
- Work with free CAs (ZeroSSL, Let's Encrypt)
- Install intermediate CA bundles
- Understand CA chains and trust stores

### 🔹 Module 5: Installing & Configuring SSL/TLS
- Configure TLS in:
  - ✅ Nginx
  - ✅ Apache
  - ✅ HAProxy
  - ✅ Postfix / Dovecot
  - ✅ RabbitMQ
  - ✅ Python / Node.js applications
- Validate setup using:
  - `curl -v https://...`
  - `openssl s_client`
  - SSL Labs scanner

### 🔹 Module 6: Managing Expiration, Renewal, Revocation
- Check certificate expiry (`openssl x509 -enddate`)
- Use `cron` for monitoring expiration
- Automate with Let's Encrypt (Certbot)
- Renewing commercial certs
- Revoking a certificate (CRL, OCSP)

### 🔹 Module 7: Advanced Topics
- Wildcard vs SAN certificates
- TLS versions & cipher suites (enable/disable)
- TLS hardening (Perfect Forward Secrecy, HSTS)
- Troubleshooting TLS handshake failures
- Certificate pinning (mobile apps, APIs)

### 🔹 Module 8: Real World Projects (Lab)
- Deploy HTTPS on a static website (Nginx + Certbot)
- Enable TLS on RabbitMQ (`amqps://`)
- Enable SMTPS in Postfix
- Enforce TLS 1.3-only with strong ciphers
- Simulate man-in-the-middle attack (for learning)

---

## 🛠 Tools Used
- `openssl`, `cfssl`, `mkcert`
- `certbot` (Let's Encrypt)
- `curl`, `s_client`, `nmap`
- Web servers, message brokers, email servers

---

## 🧪 Bonus
- Quiz after each module
- Final exam: Set up full TLS-enabled stack
- Certificate management checklist (for DevOps/SRE work)

---

## 🧠 Who Should Take This?
- Freshers in DevOps, SRE, Backend roles
- Sysadmins managing production infrastructure
- Developers securing their APIs
