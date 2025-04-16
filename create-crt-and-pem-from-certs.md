
- [Creating `.crt` and `.pem `files from domain certificates for a domain](#)


    ### Creating `.crt` and `.pem `files from domain certificates for a domain
    
    #### 🔐 Files Required
    
    You should have the following certificate files:
    
    - **Private Key:** `example_com.key`
    - **Primary Certificate (Issued to your domain):** `STAR_example_com.crt`
    - **Intermediate Certificate:** `SectigoRSADomainValidationSecureServerCA.crt`
    - **Root Certificate:** `USERTrustRSACertificationAuthorityCARoot.crt`
    
    ---
    
    #### 📌 Create `.crt` File (Full Chain without Private Key)
  
    - 🔴 **Using Bash Command (cat) — Recommended**
  
        Use the following command to combine your domain certificate with the intermediate and root certificates:
        
        ```bash
        cat STAR_example_com.crt \
            SectigoRSADomainValidationSecureServerCA.crt \
            USERTrustRSACertificationAuthorityCARoot.crt > example_com.crt
        ```
    - 🔴 **Manual Copying (e.g., with nano, vim, or cp)**

        - You paste the blocks properly (no extra spaces or characters)
        - You respect the correct order and CRT and PEM format


    This `.crt` file is typically used in `Apache` or `Nginx`, along with your private key.
    
    ---
    
    #### 📌 Create `.pem` File (Private Key + Full Chain)
    
    Use this command to create a `.pem` file that includes your private key and the entire certificate chain:
    
    ```bash
    cat example_com.key \
        STAR_example_com.crt \
        SectigoRSADomainValidationSecureServerCA.crt \
        USERTrustRSACertificationAuthorityCARoot.crt > example_com.pem
    ```
    
    This file is ideal for services that require a single bundle containing both the key and certificates like 'HaProxy'
    
    ---
    
    #### 🧪 Verify the Certificate Using OpenSSL

    To check that the certificate chain is correctly formed:
    
    ```bash
    openssl s_client -connect example.com:443
    ```
