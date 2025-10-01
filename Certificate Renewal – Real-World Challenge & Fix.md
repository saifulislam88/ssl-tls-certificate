### SSL/TLS Certificate Renewal – Challenge & Fix in Real World
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/076fc674-db09-4da7-9e43-fb8b1427b0c1" />

SSL/TLS certificate management is often more complex than it looks. Beyond just purchasing and deploying, differences in certificate formats, CA bundles, and integration methods can lead to unexpected issues.

Recently, we renewed a wildcard SSL certificate (`*.msi.com`) from Sectigo. This time, the CA provided a new-style bundle with the following files:

- SectigoPublicServerAuthenticationCADVR36.crt
- SectigoPublicServerAuthenticationRootR46_USERTrust.crt
- STAR_msi.com.crt
- USERTrustRSACertificationAuthority.crt

Although I’ve deployed **500+ certificates** in my career across different servers, this one caused serious issues. The web browser tests passed, and the chain looked fine — but **app-to-app communication and microservices integrations failed**.

👉 **The Confusing Part:**  
✅ Browsers showed everything fine.  
❌ But app-to-app communication and microservices started failing. Some services worked, others didn’t.

After two days of troubleshooting, experimenting with different methods, technical approaches (and even AI tools, ChatGPT), we engaged directly with Sectigo. I requested the same chain format used in previous years — and Sectigo reissued using their backend engine, providing:  

- AAACertificateServices.crt
- SectigoRSADomainValidationSecureServerCA.crt
- STAR_msi_com.crt
- USERTrustRSAAAACA.crt

Once re-integrated into **Nginx on Ubuntu 22.04 LTS**, everything worked smoothly. This saved us from a serious business impact.

---

## 💡 Key Takeaways

- SSL/TLS is not always plug & play.  
- Browser validation ≠ application validation. Always test across all use cases.  
- Different CA bundle formats can break microservice integrations.  
- Work with your CA to ensure a compatible chain when issues arise.  

🔐 **Note:**  
`msi.com` means Md. Saiful Islam, it is just a proxy domain name.

---

## ✅ Final Working Integration

**Cert**  
```
STAR_msi_com.crt
```

**CA Bundle**  
```
USERTrustRSAAAACA.crt
SectigoRSADomainValidationSecureServerCA.crt
AAACertificateServices.crt
```

**Key**  
```
Star_msi_com.key
```

**Combined Final Cert**  
```bash
cat STAR_msi_com.crt USERTrustRSAAAACA.crt SectigoRSADomainValidationSecureServerCA.crt AAACertificateServices.crt > final_cert_msicom.crt
```

**Nginx Configuration**  
```nginx
ssl_certificate     /etc/ssl/certs/msi.com/2025/final_cert_msicom.crt;
ssl_certificate_key /etc/ssl/certs/msi.com/2025/Star_msi_com.key;
```
