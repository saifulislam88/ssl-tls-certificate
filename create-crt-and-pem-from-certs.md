# Creating .crt and .pem Files from Domain Certificates

This guide outlines how to generate `.crt` and `.pem` files using your domain certificate components.

---

## 🔐 Files Required

You should have the following certificate files:

- **Private Key:** `example_com.key`
- **Primary Certificate (Issued to your domain):** `STAR_example_com.crt`
- **Intermediate Certificate:** `SectigoRSADomainValidationSecureServerCA.crt`
- **Root Certificate:** `USERTrustRSACertificationAuthorityCARoot.crt`

---

## 📌 Create `.crt` File (Full Chain without Private Key)

Use the following command to combine your domain certificate with the intermediate and root certificates:

```bash
cat STAR_example_com.crt \
    SectigoRSADomainValidationSecureServerCA.crt \
    USERTrustRSACertificationAuthorityCARoot.crt > example_com_fullchain.crt
```

This `.crt` file is typically used in Apache or Nginx, along with your private key.

---

## 📌 Create `.pem` File (Private Key + Full Chain)

Use this command to create a `.pem` file that includes your private key and the entire certificate chain:

```bash
cat example_com.key \
    STAR_example_com.crt \
    SectigoRSADomainValidationSecureServerCA.crt \
    USERTrustRSACertificationAuthorityCARoot.crt > example_com.pem
```

This file is ideal for services that require a single bundle containing both the key and certificates.

---

## 🧪 Verify the Certificate Using OpenSSL

To check that the certificate chain is correctly formed:

```bash
openssl s_client -connect example.com:443
```

---

## 🔗 Useful Reference

- [SSL Dragon – Check Certificate with OpenSSL](https://www.ssldragon.com/blog/check-certificate-openssl-linux/)
