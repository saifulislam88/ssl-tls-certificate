1. SSL/TLS - How to SSL/TLS Works
2. Certificate classcification
	- Self-Signed Certificate
	- CA-signed/Purchased/Commercial/Paid SSL Certificate?
		  - GeoTrust
		  - RapidSSL
		  - Digicert
		  - Comodo
		  - GlobalSign, etc.
	- Free SSL
		 - Let's Encrypt
  	 - ZeroSSL
     - Cloudflare
3. SSL Redirection
4. Wildcard Cert
5. How to generate self-sign certificates and configure it
6. How to purchase Paid certificate and configure it.
7. How to install free ssl certificate
8. example_com.csr | tallykhata_com.key | STAR_example_com.crt(ca-bundle) | SectigoRSADomainValidationSecureServerCA.crt/DigiCertCA.crt | AAACertificateServices.crt | TrustedRoot.crt/USERTrustRSAAAACA.crt/USERTrustRSACertificationAuthorityCARoot.crt
9. How to generate .pem, .crt certs
10. Digicert Cert / Sectigo/ Comodo Cert
11. Example installation ssl - web server, mail server, application - git-server, python, nodejs
12. public key infrastructure (PKI)
13. Generate, sign, install, and verify certificates
14. Manage SSL/TLS in real systems (Nginx, Apache, Postfix, RabbitMQ, etc.)
15. Work with self-signed and CA-signed certificates
16. Automate renewals using Let's Encrypt

convert .CER to .CRT for Apache SSL certificates
# openssl x509 -inform DER -in certificate.cer -out certificate.crt



Make crt file for example.com.crt


Private Key | your private key(example_com.key)
==================================================
-----BEGIN RSA PRIVATE KEY-----
(Your Private Key: your_domain_name.key)
-----END RSA PRIVATE KEY-----



CA_bundle(.Cer file) | STAR_example_com.crt
==============================================
-----BEGIN CERTIFICATE-----
(Your Primary SSL certificate: your_domain_name.crt)
-----END CERTIFICATE-----



Digicert Cert / Sectigo/ Comodo Cert | SectigoRSADomainValidationSecureServerCA.crt
===================================================================================
-----BEGIN CERTIFICATE-----
(Your Intermediate certificate: DigiCertCA.crt/SectigoRSADomainValidationSecureServerCA.crt)
-----END CERTIFICATE-----




Intermediate Certificate(USERTrustRSAAAACA.crt | 
========================================
-----BEGIN CERTIFICATE-----
(Your Root certificate: TrustedRoot.crt) | USERTrustRSAAAACA.crt |  USERTrustRSACertificationAuthorityCARoot.crt
-----END CERTIFICATE-----




https://www.ssldragon.com/blog/check-certificate-openssl-linux/
OpenSSL to View the Status of a Website’s Certificate
$ openssl s_client -connect github.com:443








Creating a .pem with the Private Key and Entire Trust Chain


-----BEGIN RSA PRIVATE KEY-----
(Your Private Key: your_domain_name.key)
-----END RSA PRIVATE KEY-----
-----BEGIN CERTIFICATE-----
(Your Primary SSL certificate: STAR_domain_name.crt) [EX: STAR_example_com.crt]
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
(Your Intermediate certificate: SectigoRSADomainValidationSecureServerCA.crt)
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
(Your Root certificate: USERTrustRSACertificationAuthorityCARoot.crt)
-----END CERTIFICATE-----
