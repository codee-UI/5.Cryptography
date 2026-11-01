# 🔐 Cryptography

A collection of cryptographic algorithms, implementations, and learning resources, built for education and experimentation.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-active-brightgreen.svg)
![PRs Welcome](https://img.shields.io/badge/PRs-welcome-orange.svg)

> ⚠️ **Disclaimer:** The code in this repository is for **educational purposes only**. Do not use it to protect real-world sensitive data. For production systems, use well-audited libraries such as OpenSSL, libsodium, or the `cryptography` package.

---

## 📖 Table of Contents

- [About](#-about)
- [What is Cryptography?](#-what-is-cryptography)
- [Core Goals](#-core-goals-of-cryptography)
- [Types of Cryptography](#-types-of-cryptography)
- [A Brief History](#-a-brief-history)
- [Guiding Principles](#-guiding-principles)
- [Features](#-features)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Usage](#-usage)
- [Algorithms Covered](#-algorithms-covered)
- [Testing](#-testing)
- [Contributing](#-contributing)
- [Resources](#-resources)
- [License](#-license)

---

## 📌 About

This repository explores the core concepts of cryptography, from classical ciphers to modern symmetric, asymmetric, and hashing algorithms. Each implementation is written to be readable and well-documented so it can be used as a learning aid.

## 🧠 What is Cryptography?

Cryptography is the science of securing information so that only the intended people can read or modify it. The word comes from the Greek *kryptos* ("hidden") and *graphein* ("to write"). At its heart, it turns readable data (**plaintext**) into unreadable data (**ciphertext**) using an algorithm (a **cipher**) and a secret (a **key**), and allows the process to be reversed only by someone who holds the right key.

```text
Plaintext ──► [ Encryption + Key ] ──► Ciphertext ──► [ Decryption + Key ] ──► Plaintext
```

You use cryptography every day without noticing: HTTPS in your browser, messaging apps, online banking, password storage, software updates, and digital signatures all depend on it.

## 🎯 Core Goals of Cryptography

| Goal                | Meaning                                                  | Example                          |
|---------------------|----------------------------------------------------------|----------------------------------|
| **Confidentiality** | Only authorized parties can read the data                | Encrypting a message with AES    |
| **Integrity**       | Data has not been altered in transit or storage          | Checking a SHA-256 hash          |
| **Authentication**  | The identity of a sender or system is verified           | Certificates, HMAC               |
| **Non-repudiation** | A sender cannot later deny having sent a message         | Digital signatures               |

## 🧩 Types of Cryptography

1. **Symmetric-key cryptography:** the same key encrypts and decrypts. It is fast and ideal for bulk data, but both sides must share the key securely (e.g., AES).
2. **Asymmetric (public-key) cryptography:** a key pair is used, where the public key encrypts or verifies and the private key decrypts or signs. It solves key distribution but is slower (e.g., RSA, ECC).
3. **Hash functions:** one-way functions that map any input to a fixed-size fingerprint. They are used for integrity checks and password storage (e.g., SHA-256).
4. **Hybrid systems:** real-world protocols like TLS combine asymmetric cryptography (to exchange a key) with symmetric cryptography (to encrypt the data efficiently).

## 🕰️ A Brief History

- **Ancient times:** simple substitution ciphers such as the Caesar cipher were used for military messages.
- **Renaissance:** polyalphabetic ciphers like Vigenère made frequency analysis harder.
- **World War II:** machines such as Enigma automated encryption, and breaking them (Turing, Bletchley Park) helped shape modern computing.
- **1970s:** DES was standardized, and public-key cryptography (Diffie–Hellman, RSA) was introduced.
- **Today:** AES, elliptic curves, and zero-knowledge proofs are widely used, while **post-quantum cryptography** is being developed to resist future quantum computers.

## 🧭 Guiding Principles

Good cryptography is as much about discipline as it is about math. Keep these ideas in mind while exploring this repo:

- **Kerckhoffs's principle:** a system should stay secure even if everything about it, except the key, is public. Security through obscurity is not security.
- **Never roll your own crypto in production:** subtle mistakes (weak randomness, timing leaks, bad padding) can silently break an otherwise sound algorithm.
- **Randomness matters:** predictable keys or IVs defeat strong ciphers. Use a cryptographically secure random number generator.
- **Key management is the hard part:** most real-world breaches come from leaked, reused, or poorly stored keys, not from broken algorithms.
- **Algorithms age:** MD5, SHA-1, and DES were once standard and are now considered broken or weak. Stay current with recommendations from bodies like NIST.
- **Security is a trade-off:** performance, usability, and strength must be balanced, and the right choice depends on your threat model.
- **Use it responsibly:** cryptographic knowledge carries ethical weight. Use it to protect privacy and systems, never to harm others.

## ✨ Features

- Classical ciphers (Caesar, Vigenère, Playfair, etc.)
- Symmetric encryption (AES, DES)
- Asymmetric encryption (RSA, Diffie-Hellman, ECC)
- Hash functions (SHA-256, MD5) and HMAC
- Digital signatures
- Clear examples and unit tests

## 📂 Project Structure

```text
Cryptography/
├── classical/          # Caesar, Vigenère, Playfair, Hill, etc.
├── symmetric/          # AES, DES, block cipher modes
├── asymmetric/         # RSA, Diffie-Hellman, ECC
├── hashing/            # SHA, MD5, HMAC
├── signatures/         # Digital signature schemes
├── utils/              # Helper functions (primes, modular math)
├── tests/              # Unit tests
├── docs/               # Notes and theory
├── requirements.txt
├── LICENSE
└── README.md
```

## 🚀 Getting Started

### Prerequisites

- Python 3.9 or higher
- `pip` package manager

### Installation

```bash
# Clone the repository
git clone https://github.com/<your-username>/Cryptography.git

# Move into the project directory
cd Cryptography

# (Optional) Create a virtual environment
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

## 💻 Usage

### Caesar Cipher

```python
from classical.caesar import encrypt, decrypt

ciphertext = encrypt("HELLO WORLD", shift=3)
print(ciphertext)                 # KHOOR ZRUOG
print(decrypt(ciphertext, 3))     # HELLO WORLD
```

### SHA-256 Hash

```python
from hashing.sha256 import sha256_hash

print(sha256_hash("hello"))
```

### RSA Key Generation

```python
from asymmetric.rsa import generate_keys, encrypt, decrypt

public_key, private_key = generate_keys(bits=1024)
cipher = encrypt("secret message", public_key)
print(decrypt(cipher, private_key))
```

## 🧮 Algorithms Covered

| Category   | Algorithms                          | Status         |
|------------|-------------------------------------|----------------|
| Classical  | Caesar, Vigenère, Playfair, Hill    | ✅ Complete    |
| Symmetric  | AES, DES                            | 🚧 In progress |
| Asymmetric | RSA, Diffie-Hellman, ECC            | 🚧 In progress |
| Hashing    | SHA-256, MD5, HMAC                  | ✅ Complete    |
| Signatures | RSA signatures, ECDSA               | 📝 Planned     |

## 🧪 Testing

```bash
python -m unittest discover tests
# or, if using pytest
pytest tests/
```

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit your changes: `git commit -m "Add your feature"`
4. Push to the branch: `git push origin feature/your-feature`
5. Open a Pull Request

Please make sure your code is documented and includes tests.

## 📚 Resources

- [Cryptography Engineering](https://www.schneier.com/books/cryptography-engineering/), Ferguson, Schneier, Kohno
- [Crypto 101](https://www.crypto101.io/), free introductory book
- [Cryptopals Challenges](https://cryptopals.com/)
- [NIST Cryptographic Standards](https://csrc.nist.gov/projects/cryptographic-standards-and-guidelines)

## 📄 License

Distributed under the MIT License. See [`LICENSE`](LICENSE) for details.

---

⭐ If you find this repository useful, consider giving it a star!
