# Cybersecurity Fundamentals (Sample for testing skills)

## The CIA Triad

The CIA triad is the foundational model for information security, made up of three core principles:

- **Confidentiality**: Ensuring information is only accessible to authorized users. Achieved through encryption, access controls, and authentication.
- **Integrity**: Ensuring information is accurate and unaltered except by authorized actions. Achieved through hashing, checksums, and digital signatures.
- **Availability**: Ensuring systems and data are accessible to authorized users when needed. Achieved through redundancy, backups, and DDoS protection.

## Common Threats and Attacks

- **Phishing**: Fraudulent messages (often email) designed to trick users into revealing credentials or installing malware.
- **Malware**: Malicious software, including viruses, worms, ransomware, and spyware, designed to damage or gain unauthorized access to systems.
- **SQL Injection**: An attack where malicious SQL code is inserted into input fields to manipulate or access a database.
- **Cross-Site Scripting (XSS)**: Injecting malicious scripts into web pages viewed by other users, often to steal session data.
- **Denial-of-Service (DoS) / Distributed DoS (DDoS)**: Overwhelming a system with traffic so legitimate users cannot access it.
- **Man-in-the-Middle (MitM)**: An attacker secretly intercepts and possibly alters communication between two parties.

## Authentication and Access Control

- **Authentication**: Verifying the identity of a user (e.g., passwords, biometrics, tokens).
- **Authorization**: Determining what an authenticated user is allowed to do.
- **Multi-Factor Authentication (MFA)**: Requires two or more verification methods (e.g., password + one-time code) to increase security.
- **Principle of Least Privilege**: Users and systems should only have the minimum access necessary to perform their function.
- **Role-Based Access Control (RBAC)**: Permissions are assigned to roles, and users are assigned to roles, simplifying access management.

## Encryption

- **Encryption**: The process of converting data into a coded form to prevent unauthorized access.
- **Symmetric Encryption**: Uses the same key for encryption and decryption (e.g., AES). Fast, but key distribution is a challenge.
- **Asymmetric Encryption**: Uses a public key (to encrypt) and a private key (to decrypt) (e.g., RSA). Solves key distribution but is slower.
- **Hashing**: A one-way function that converts data into a fixed-size string (hash). Used for storing passwords and verifying integrity. Common algorithms: SHA-256.
- **HTTPS/TLS**: Encrypts data in transit between a client and a server, preventing eavesdropping and tampering.

## Security Best Practices

- Keep software and systems patched and up to date to fix known vulnerabilities.
- Use strong, unique passwords and enable MFA wherever possible.
- Apply the principle of least privilege to user accounts and services.
- Regularly back up data and test recovery procedures.
- Monitor logs and set up alerts for suspicious activity.

## Quick Recap

- CIA triad = Confidentiality, Integrity, Availability — the core goals of security.
- Common attacks: phishing, malware, SQL injection, XSS, DoS/DDoS, MitM.
- Authentication = who you are; Authorization = what you can do; MFA adds extra verification layers.
- Symmetric encryption (one key, fast) vs Asymmetric encryption (public/private key pair).
- Hashing is one-way and used for passwords/integrity checks, not for reversible encryption.
