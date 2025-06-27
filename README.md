# 🛡️ LynCrypt

> ⚡ High-performance, key-locked encryption for ultra-secure communication — built on a novel cipher architecture.

---

## 🚀 Overview

<p align="center">
  <img src="https://img.shields.io/badge/version-1.0.0-blue?style=flat-square" alt="Version" />
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="License" />
  <img src="https://img.shields.io/badge/build-passing-brightgreen?style=flat-square" alt="Build" />
  <img src="https://img.shields.io/badge/python-3.8%2B-yellow?style=flat-square" alt="Python" />
  <img src="https://img.shields.io/badge/security-military%20grade-red?style=flat-square" alt="Security" />
</p>

**LynCrypt** is a high-speed, fully reversible symmetric encryption algorithm designed from scratch. Unlike traditional ciphers (AES, RSA, etc.), LynCrypt introduces a fresh approach based on per-block key-derived keystreams and nonlinear permutation.

* 🔒 **Symmetric stream+permute encryption**
* 🔁 **100% reversible** only with the correct key
* ⚡ **Extremely fast** and lightweight
* 🚫 **Not based on any existing algorithm**
* 🧬 **Hash-bound decryption integrity**

---

## 🧠 How It Works

### 🔑 Key Concept

LynCrypt relies on a **master key** (chosen by the user) to encrypt and decrypt data. No key = no access.

```plaintext
Plaintext + Key  →  Secure Encrypted Message + Hash
Encrypted Message + Key  →  ✅ Original Message (if hash matches)
```

### 📦 Internals

Each encryption call uses:

| Element       | Description                                    |
| ------------- | ---------------------------------------------- |
| `Key`         | User-provided password or token                |
| `Nonce`       | Random 12-byte value (fresh each time)         |
| `Session Key` | Derived using HMAC(Key + Nonce)                |
| `Permute`     | Nonlinear byte scrambling (block-based)        |
| `Keystream`   | SHA256(Key + Nonce + Block Index) → XOR        |
| `Auth Tag`    | HMAC(Key, Nonce + Ciphertext) for tamper check |

### 🔄 Encryption Flow

1. Input plaintext is chunked into 64-byte blocks
2. Each block is XORed with a derived keystream
3. The block is scrambled using a swap-based permute
4. At the end, an HMAC tag is generated for integrity

### 🔓 Decryption Flow

1. HMAC tag is verified (to reject tampered data)
2. Each encrypted block is descrambled twice (reverse permute)
3. Keystream XOR is applied again → plaintext restored

---

## 💡 Why LynCrypt?

| Feature                 | Benefit                                              |
| ----------------------- | ---------------------------------------------------- |
| 🔥 Unique Design        | Completely novel — not AES, RSA, or XOR-only based   |
| ⚙️ Fast & Lightweight   | Designed for real-time API & embedded usage          |
| 🔐 Fully Reversible     | Accurate decryption only with correct key and hash   |
| 🚫 Unbreakable Patterns | Keystream + permute removes repeated patterns        |
| ✅ Tamper Detection      | Encrypted payload has a built-in HMAC authentication |

---

## 🧪 Usage

### 🔐 Encrypt

```bash
python lyncrypt.py
🔁 Mode: e
🔑 Enter Key: mySecret123
✉️  Enter Text: Hello from LynCrypt
```

**Output:**

* Encrypted string (base64)
* Auth Tag (base64)
* Nonce (base64)

### 🔓 Decrypt

```bash
python lyncrypt.py
🔁 Mode: d
🔑 Enter Key: mySecret123
📦 Encrypted String: (paste here)
🧾 Auth Tag: (paste here)
🔢 Nonce: (paste here)
```

**Output:** Original message ✅

---

## 📦 Integration

✅ Suitable for:

* API encryption
* Form data protection
* Secure message passing
* RPA/IoT devices
* Python backends

---

## 📈 Roadmap

| Version | Features                                              |
| ------- | ----------------------------------------------------- |
| ✅ v1.0  | Core CLI tool with full encryption/decryption         |
| ⏳ v1.1  | Library packaging, import support, command-line flags |
| 🔜 v2.0 | GUI/Web version + browser encryption SDK              |
| 🔒 v3.0 | Advanced: multi-pass, layered keys, forward secrecy   |

---

## 🧾 License

This project is licensed under the **MIT License**. Feel free to use, modify, and share — with credit to the original author 🙏

---

## 🌟 Support & Contribution

We welcome community support!

* ⭐ Star the repo to show love
* 🐛 Open issues for bugs or feature requests
* 🛠️ Pull requests are welcome!

---

**LynCrypt** — *Built different. Secured forever.* 🔐
