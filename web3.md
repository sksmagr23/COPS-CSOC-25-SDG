# <img src="https://avatars.githubusercontent.com/u/38392463?s=200&v=4" height=40></img> COPS SDG Summer of Code 2025 - Web3 Week 1

---

# Foundations

### Blockchain Essentials

**Resources:**  
- [Video Lectures](http://youtube.com/watch?v=lUTv9NHkuR4&list=PLlzIv5W0T83BPJqonIRMf-lV7K7E06qyY&index=1)
- [Satoshi Nakamoto Whitepaper](https://bitcoin.org/bitcoin.pdf)

---

# Bitcoin Mechanics

### Transaction Lifecycle

**Resources:**  
- [But How Does Bitcoin Actually Work?](https://www.youtube.com/watch?v=bBC-nXj3Ng4&t=219s)
- [Grokking Bitcoin](https://rosenbaum.se/book/grokking-bitcoin.html)

---

# 🎯 Week 1 Assignment: Cryptographic Proof Simulator

## 📌 Problem Statement  
Create a Python script that **demonstrates** Bitcoin's cryptographic principles by:

1. Generating SHA-256 hashes for transaction data  
2. Simulating digital signature creation/verification  
3. Mapping concepts to real Bitcoin transactions  

**Required Workflow:**  
[Transaction Data] → [SHA-256 Hash] → [Signature Simulation] → [Verification]

## ✅ Deliverables  
1. `crypto_demo.py` with:  
```python
import hashlib

# 1. Hash Generator
def create_tx_hash(tx_data):
    return ...

# 2. Signature Simulator
def sign_transaction(private_key, tx_hash):
    # Simulate signing using XOR (educational purpose only)
    return ...

# 3. Verification Check
def verify_signature(public_key, signature, tx_hash):
    # Simplified verification logic
    return ...
  ```
2. `README.md` explaining:
  - How SHA-256 protects transaction integrity
  - Real-world signature process vs your simulation

## 🌟 Evaluation Criteria  
- Working SHA-256 implementation
- Clear understanding of signing/verification concepts
- Accurate references to provided resources
- Identification of real transaction components 

---

# Cryptography
- [Transaction Decoder Tool](https://live.blockcypher.com/btc/decodetx/)
- [Play with Cryptography](https://andersbrownworth.com/blockchain/hash).

*"Bitcoin is the internet of money." - Andreas Antonopoulos*
