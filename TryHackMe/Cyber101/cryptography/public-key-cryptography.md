# 🔐 Public Key Cryptography – TryHackMe Notes (Cyber101)

## 📌 Initial Understanding – Why Public Key Cryptography Exists

After learning basic cryptography concepts, I understood that secure communication over the internet is not just about encryption, but about ensuring multiple security properties at the same time.

When we communicate online (SSH, HTTPS, Email, Banking), we must ensure four major things:

1. **Authentication** – Verifying that we are communicating with the correct person/server  
2. **Authenticity** – Confirming the data is coming from the claimed source  
3. **Integrity** – Ensuring the data is not altered during transmission  
4. **Confidentiality** – Preventing eavesdropping or unauthorized access  

I realized that symmetric (private key) cryptography mainly protects **confidentiality**, but public key cryptography plays a huge role in:
- Authentication
- Authenticity
- Integrity

Which makes it extremely important in cybersecurity and SOC operations.

---

## 🔑 Symmetric vs Asymmetric Cryptography (Practical Realization)

### Symmetric Encryption:
- Uses ONE shared key
- Fast and efficient
- But key sharing is a major problem

If the key is intercepted, the entire communication is compromised.

### Asymmetric Encryption (Public Key Cryptography):
- Uses TWO keys:
  - Public Key (for encryption)
  - Private Key (for decryption)
- Much more secure for communication setup
- But slower due to complex mathematics and large key sizes

Example:
- RSA commonly uses 2048-bit or 4096-bit keys

---

## ⚡ Hybrid Encryption (Real World Insight)

One important concept I learned is that:
> Asymmetric encryption is slow, so it is NOT used for full communication.

Instead, in real-world systems:
1. Asymmetric cryptography is used to securely exchange a secret key
2. Then symmetric encryption is used for actual fast communication

This makes the system both:
- Secure
- Efficient

---

## 📦 Lock and Box Analogy (Key Exchange Concept)

A very helpful analogy for understanding public key cryptography:

- Secret Code = Symmetric Key
- Lock = Public Key
- Lock's Key = Private Key

Process:
1. Receiver sends their public key (lock)
2. Sender locks the secret message using that lock
3. Only the receiver (who has the private key) can unlock it

This means:
- The secret key is never directly transmitted
- Attackers cannot decrypt without the private key

---

## 🧮 RSA – Mathematical Foundation of Public Key Cryptography

I learned that modern cryptography heavily relies on mathematics.

RSA security is based on:
- Large prime numbers
- Modular arithmetic
- Difficulty of factorizing very large numbers

In practice:
- RSA uses very large primes (300+ digit numbers)
- Public and private keys are mathematically linked
- But deriving the private key from the public key is computationally infeasible

This is why RSA is still widely used in secure communications.

---

## 🤝 Diffie-Hellman Key Exchange (Key Agreement)

Another major concept I learned was Diffie-Hellman Key Exchange, which allows two parties to agree on a shared secret key over an insecure channel.

### Core Idea:
Both parties create private secrets and use public values to generate a shared key.

Step-by-step understanding:
1. Public values:  
   - Prime number (p)  
   - Generator (g)

2. Each party selects a private integer:
   - Host A → secret (a)
   - Host B → secret (b)

3. They compute public keys:
   - A: g^a mod p
   - B: g^b mod p

4. They exchange public keys

5. Shared secret is computed:
   - A: (g^b mod p)^a mod p
   - B: (g^a mod p)^b mod p

Both end up with the SAME shared key without ever transmitting the secret directly.

This concept is used in secure protocols like TLS and SSH.

---

## 🔐 RSA + Diffie-Hellman in Real Systems

I understood that:
- Diffie-Hellman → Used for key agreement
- RSA → Used for authentication and identity verification

Together they form a secure communication framework used in:
- HTTPS
- SSH
- Secure messaging systems

---

## 🖥️ Practical Task – SSH Key Generation

I generated my own SSH key pair inside my Linux environment using:

```bash
ssh-keygen
```

---
**Key observations:**

Generated public and private key pair (ed25519)
Private key stored securely
Public key can be shared for authentication
Optional passphrase adds extra protection layer

This helped me understand how real systems use key-based authentication instead of passwords.


## 🔑 SSH Signature Algorithms (Awareness)
I also became familiar with different SSH key algorithms:

RSA
DSA
ECDSA
ECDSA-SK

Even though this was more informational, I realized it is important to recognize these in security logs and real environments.

---

## 🧪 Practical Task – GPG Encryption & Decryption
I worked with GPG (GNU Privacy Guard), which is an implementation of OpenPGP.

Key Concepts:

Used for file encryption
Digital signatures
Email security
Data integrity verification

Commands I used:

Importing a key:
```gpg --import pkey.key```
Decrypting an encrypted message:
```gpg --decrypt message.gpg```

This showed me how encrypted files in CTFs can be decrypted using proper keys.

## 📧 PGP and GPG – Email & File Security

I learned that:

PGP (Pretty Good Privacy) is used for encryption and digital signing
GPG is the open-source implementation of OpenPGP

Commonly used to:

Secure emails
Sign messages
Protect confidential files

GPG also protects private keys using passphrases, which adds another security layer.

# 🛠️ Cryptanalysis – Attacking Cryptographic Systems

Another interesting topic was cryptanalysis, which focuses on breaking encryption systems.

Common attack methods:

Brute Force Attack (trying all possible combinations)

Dictionary Attack (using common wordlists)

Tools like:

John the Ripper

gpg2john

can be used to attempt cracking encrypted keys if they are weakly protected.

# 🌐 Digital Signatures and Certificates

I also learned how digital signatures ensure:

Authentication
Integrity
Authenticity of digital messages and documents

Browsers use TLS certificates to:

Verify website identity
Enable HTTPS secure communication
Prevent man-in-the-middle attacks

## 🧠 Final Reflection (My Learning Perspective)

This module significantly expanded my understanding of how secure communication actually works behind the scenes.

Before this, I only thought encryption meant “hiding data”, but now I understand:

Key exchange mechanisms
Role of mathematics in cryptography
Real-world tools like SSH and GPG
How asymmetric and symmetric encryption work together

This was one of the most insightful topics so far because it directly connects to:

Cybersecurity
SOC analysis
Secure network communication
CTF challenges involving encrypted files
