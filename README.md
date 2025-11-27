# Implementing SSL/TLS on a Node.js Server

## 📌 Overview
This repository contains the source code and documentation for a Cybersecurity Lab focused on secure web communications. The project demonstrates the transition from an insecure HTTP server to a secure HTTPS server using Node.js and OpenSSL.

The primary goal is to understand how SSL/TLS certificates work, how to generate self-signed certificates, and how to configure a server to use them for encryption.

## 🎯 Learning Objectives
- Understand the difference between HTTP and HTTPS protocols.
- Generate Private Keys and Self-Signed Certificates using OpenSSL.
- Implement a Node.js server that handles secure traffic.
- Analyze network behavior and browser trust warnings.

## 📂 Project Structure
- **server.js**: A basic HTTP server listening on port 3000 (Insecure).
- **server_https.js**: An upgraded HTTPS server listening on port 3443 (Secure).
- **certs/**: Directory containing the cryptographic credentials.
  - `server.key`: The private key (kept secret).
  - `server.cert`: The self-signed public certificate.

## ⚙️ Prerequisites
- **Node.js**: Runtime environment for the server.
- **OpenSSL**: Tool for generating keys and certificates.
- **Curl**: Command-line tool for testing connections.

## 🚀 How to Run

### 1. Install Dependencies
Run the following command to install the required Node.js packages (if any are defined):
```bash
npm install
2. Generate Certificates
If the certificates are not present, generate them using OpenSSL:
code
Bash
mkdir certs
openssl req -nodes -new -x509 -keyout certs/server.key -out certs/server.cert -days 365
Note: Ensure the Common Name (CN) is set to localhost.
3. Run the Insecure Server (HTTP)
code
Bash
node server.js
Access at: http://localhost:3000
Observation: Traffic is unencrypted.
4. Run the Secure Server (HTTPS)
code
Bash
node server_https.js
Access at: https://localhost:3443
Observation: Browser will show a "Self-Signed" warning. You must accept the risk to proceed. Traffic is encrypted.
🧪 Testing
Curl Verification
To test the secure server from the terminal and bypass the self-signed certificate check:
code
Bash
curl -k https://localhost:3443
Browser Verification
Navigate to https://localhost:3443.
Accept the security risk (caused by the lack of a Public CA signature).
Click the "Lock" icon to view certificate details (Subject: localhost).
📝 Lab Outcomes
This project successfully demonstrates the implementation of the TLS handshake and data encryption. While self-signed certificates are valid for encryption, they lack third-party trust, which is why browsers flag them as potential security risks.

