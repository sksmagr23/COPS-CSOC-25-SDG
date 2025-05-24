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

# Cryptography
- [Transaction Decoder Tool](https://live.blockcypher.com/btc/decodetx/)
- [Play with Cryptography](https://andersbrownworth.com/blockchain/hash).

---

# Week-1 Assignment: Bitcoin Cryptography Implementation Guide

**Objective:**  
Build a Python module demonstrating Bitcoin's core cryptographic operations with clear mapping to actual Bitcoin components.


## Implementation Requirements

### 1. Transaction Hasher (`create_tx_hash`)
**Implement:**
- Double SHA-256 hashing mimicking Bitcoin TXID generation
- Input validation for transaction data format
- Hex-to-bytes conversion matching Bitcoin's serialization



### 2. Signature Simulator (`sign_transaction`)
**Implement:**
- ECDSA-like signature components (r, s) generation
- Nonce generation with cryptographic safety
- Message formatting using Bitcoin's sighash convention



### 3. Verification Engine (`verify_signature`)
**Implement:**
- Signature parsing in DER format
- Public key recovery from signature elements



## Required Artifacts

### `crypto_demo.py` Structure

```python
def create_tx_hash(tx_data: bytes) -> str:
"""Implement Bitcoin-style double SHA-256 with TXID characteristics"""

def sign_transaction(private_key: int, tx_hash: bytes) -> tuple:
"""Produce ECDSA-like (r,s) signature components with nonce safety"""

def verify_signature(pubkey: bytes, sig: tuple, tx_hash: bytes) -> bool:
"""Replicate Bitcoin's verification logic with strict encoding checks"""
```


## Reference Links

1. [Learn me a bitcoin](https://learnmeabitcoin.com/)
2. [libsecp256k1 documentation](https://medium.com/coinmonks/introduction-to-blockchains-bedrock-the-elliptic-curve-secp256k1-e4bd3bc17d)


## Evaluation Criteria

1. **Hashing**
    - Correct double-SHA256 implementation matching TXID specs
    - Proper byte ordering for Bitcoin data structures

2. **Signature**
    - Valid (r,s) component generation
    - Nonce reuse protection mechanism

3. **Verification**
    - Strict encoding rule enforcement
    - Public key recovery logic

4. **Documentation**
    - Clear explanation of your implementation

---

*"Bitcoin is the internet of money." - Andreas Antonopoulos*
