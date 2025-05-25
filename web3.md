# <img src="https://avatars.githubusercontent.com/u/38392463?s=200&v=4" height=40></img> COPS SDG Summer of Code 2025 - Web3

# Week 1

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

---
---
---

# Week 2

---

# MetaMask  
> MetaMask is a browser extension and mobile wallet that allows users to interact with Ethereum-based dApps (decentralized applications). It acts as a bridge between your web browser and the Ethereum blockchain, enabling you to manage accounts, sign transactions, and switch between different networks (e.g., Mainnet, testnets like Goerli, Ropsten, etc.).

* [Tutorial on MetaMask](https://www.youtube.com/watch?v=Af_lQ1zUnoM)  
* [Set Up MetaMask](https://chromewebstore.google.com/detail/metamask/nkbihfbeogaeaoehlefnkodbefgpgknn?hl=en&pli=1)  

**Before moving to the next step, get familiar with this first.**

---

# Solidity Fundamentals

### Smart Contracts 101  

Smart contracts are self-executing pieces of code stored on a blockchain. When deployed, they live at a permanent address and run exactly as written, without any possibility of downtime or third-party interference. On Ethereum, smart contracts are written in Solidity—a statically typed language that resembles JavaScript/C++ and compiles to EVM bytecode.

**Why Ethereum?**  
Ethereum popularized the concept of a “world computer”—a decentralized virtual machine (the EVM) that anyone can run. At its core, Ethereum allows users to deploy code (smart contracts) that hold state and execute transactions. Every node on the network processes every smart contract call, ensuring censorship resistance and transparency.

**Resources:**  
- [Solidity Official Documentation](https://docs.soliditylang.org/)  
- [Ethereum Whitepaper](https://ethereum.org/en/whitepaper/)  

> _“With Ethereum, we create not only value, but programmable value.”_ – Vitalik Buterin

---

# Deep Dive Into the World of Solidity and Smart Contracts

> Learn to code Ethereum DApps by building your own zombie army!

CryptoZombies is an interactive, gamified coding tutorial that teaches you Solidity (the language for Ethereum smart contracts) by letting you build your own zombie-based blockchain game. 🧟‍♂️

* [Watch as much as you can](https://www.youtube.com/watch?v=-1GB6m39-rM&t=33094s)  
* [Here](https://cryptozombies.io/): Complete the course **"Solidity: Beginner to Intermediate Smart Contracts"**  

---

# Development Environment

### Setting Up Your Solidity Toolchain  

**Resources:**  
- [Remix IDE (Browser-Based)](https://remix.ethereum.org/)  
- Familiarize yourself with Node.js and related tools for the upcoming weeks, as we will transition to development with Hardhat or Truffle.  

---

## Week 2 Assignment: Build a Voting DApp 🗳️

### Objective  
Create a decentralized voting system where:  
1. A chairperson (contract owner) can register voters.  
2. Registered voters can cast votes on proposals.  
3. Results are transparently tracked on-chain.  
4. Prevents double-voting and unauthorized access.  

---

## Task 1: Smart Contract Implementation (`Voting.sol`)  

### Features to Implement  
1. **Contract Setup**  
   - Store the chairperson's address (deployer).  
   - Use a `modifier` to restrict functions to the chairperson.  

2. **Voter Registration**  
   - Create a struct `Voter` with:  
     ```solidity
     struct Voter {
         bool isRegistered;
         bool hasVoted;
         uint votedProposalId;
     }
     ```  
   - Mapping: `mapping(address => Voter) public voters;`  
   - Function: `registerVoter(address voter)` (only callable by the chairperson).  

3. **Proposal Management**  
   - Struct `Proposal` with:  
     ```solidity
     struct Proposal {
         string name;
         uint voteCount;
     }
     ```  
   - Array: `Proposal[] public proposals;`  
   - Function: `addProposal(string memory name)` (only callable by the chairperson).  

4. **Voting Logic**  
   - Function `vote(uint proposalId)` that:  
     - Allows only registered voters.  
     - Prevents double-voting.  
     - Updates the proposal’s vote count.  

5. **Events**  
   - Emit `VoterRegistered(address voter)` on registration.  
   - Emit `VoteCast(address voter, uint proposalId)` on voting.  

---

## Task 2: Test Your Contract in Remix  

### Manual Testing Steps  
1. **Deploy the Contract**  
   - In Remix, compile and deploy to the **"JavaScript VM"**.  

2. **Chairperson Actions**  
   - Add 3 proposals: **"Red"**, **"Blue"**, **"Green"**.  
   - Register 2 test voter addresses.  

3. **Voter Actions**  
   - Switch to `voter1`’s account and vote for proposal `0`.  
   - Switch to `voter2`’s account and vote for proposal `1`.  
   - Try to vote again with `voter1` → **should fail**.  

4. **Verify Results**  
   - Check `proposals(0).voteCount` → **should be 1**.  
   - Check `proposals(1).voteCount` → **should be 1**.  

---

## Task 3: Code Challenges (Bonus) ⚡  

Add these advanced features:  
1. **Voting Deadline**  
   - Set a time limit for voting (e.g., 1 week after deployment).  
   - Add modifier `onlyDuringVotingPeriod`.  

2. **Delegate Votes**  
   - Allow voters to delegate their vote to another address.  

3. **Winner Calculation**  
   - Function `getWinner()` that returns the proposal with the most votes.  

---

## Submission Guidelines  

1. **Code**  
   - Create a GitHub repo with:  
     - `contracts/Voting.sol`  
     - `README.md` explaining your approach and bonus features.  

2. **Demo**  
   - Record a short video (2-3 minutes) showing:  
     - Deployment in Remix.  
     - Testing voter registration and voting.  
     - Demonstrating error cases (e.g., double voting).  

---

## Evaluation Criteria  

| Criteria                | Points |
|-------------------------|--------|
| Core Features Working   | 40     |
| Error Handling          | 20     |
| Code Readability        | 20     |
| Bonus Features          | 15     |
| Documentation & Demo    | 5      |

---

*"Unlocking smart contracts is unlocking the future of programmable assets."*  
