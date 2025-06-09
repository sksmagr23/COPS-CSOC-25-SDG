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

---

# <img src="https://avatars.githubusercontent.com/u/38392463?s=200&v=4" height=40></img> COPS SDG Summer of Code 2025 - Web3 Week 3

---

## 🚀 Web3 Development
> Transition from browser-based tools to professional-grade development frameworks used by blockchain engineers

### 🔗 **Ethers.js Mastery**
The backbone of Ethereum interaction in JavaScript applications

**Core Concepts:**
- Providers (JsonRpcProvider, Web3Provider)
- Signers (Wallet, JsonRpcSigner)
- Contract abstraction
- BigNumber operations
- Event filtering

**Resources:**
- 📹 [Master Ethers.js Step-by-Step](https://www.youtube.com/watch?v=yk7nVp5HTCk&t=673s)
- 📚 [Official Documentation](https://docs.ethers.org/v5/)

---

### ⚒️ **Hardhat Deep Dive**
The professional Ethereum development environment

**Key Features:**
- Advanced testing framework
- Solidity debugging
- Plugin ecosystem
- TypeScript support

**Resources:**
- 📹 [Hardhat Complete Playlist](https://www.youtube.com/playlist?list=PLgPmWS2dQHW9mucRpDVe16j9Qn74ZXqcD) -> Outdated But Learn To Use It From Here.
- 📚 [Official Documentation](https://hardhat.org/docs)
- 🧪 [Hardhat Testing Guide](https://hardhat.org/hardhat-runner/docs/guides/test-contracts)

---

### 🌐 **Full-Stack DApp Development**
Connecting smart contracts to modern web interfaces

**Resource Collection:**
- 📹 [Learn To Build DApp](https://www.youtube.com/watch?v=3681ZYbDSSk)
- 📚 [Learn By Watching Tutorial](https://www.youtube.com/watch?v=8rhueOcTu8k&list=PLS5SEs8ZftgVV6ah1fo2IvlHk1kTCy6un&index=1)
- 🧭 [DApp Architecture Patterns](https://ethereum.org/en/developers/docs/dapps/)
- 🔐 [Wallet Integration Best Practices](https://docs.metamask.io/guide/create-dapp.html)

---

## 🧪 Week 3 Assignment: Create A DApp.

Create ANY decentralized application of your choice that:

- Connects to Ethereum blockchain

- Uses at least one smart contract

- Has a functional frontend

- Solves a real problem or provides entertainment
---

## 📝 Submission Guidelines

1. **Code Repository**

2. **ReadMe Updated**

3. **Video Demo (3-5 minutes)**
---

## Happy Learning

---
# ⚒️ Week 4: From Local IDE to Testnet (with a Taste of ZK)

Welcome to **Week 4** of **COPS SDG Summer of Code 2025 – Web3**!  
This week we’ll move your Solidity work out of the browser and into your **local IDE** using **Hardhat**, deploy to a public testnet, hook up a simple frontend, and get your first glimpse of **Zero‑Knowledge**.

---

## 📖 Overview

- **Local Dev Workflow**  
  - Install and configure Hardhat in VS Code (or your IDE)  
  - Write, compile, test, and debug contracts locally  

- **Testnet Deployment**  
  - Configure Holesky networks in your project  
  - Deploy your contracts with a script  
  - Verify on Etherscan  

- **Frontend Integration**  
  - Connect Ethers.js + MetaMask to your deployed contract  
  - Read state and send transactions from a minimal UI  

- **Zero‑Knowledge Intro**  
  - Understand why ZK proofs matter for privacy & scalability  
  - Try a toy ZK circuit or verifier in your project  

---

## 🛠 Part 1: Local Hardhat Setup

1. **Initialize a Hardhat project** in your IDE  
2. **Explore** the sample contract and script that Hardhat creates  
3. **Compile**, **run a local node**, and **deploy** to your own localhost network  
4. **Debug** using console logs and the Hardhat console

---

## 🌐 Part 2: Deploying to a Public Testnet

1. **Obtain test ETH** from Holesky
2. **Add network settings** (RPC URL, private key) to your Hardhat config  
3. **Run your deployment script** to publish contracts to Goerli/Mumbai  
4. **Verify** your contract on a block explorer and review its transactions

---

## 🌐 Part 3: Frontend Connection

1. **Scaffold a minimal UI** (HTML + JS or React)  
2. **Instantiate Ethers.js** with MetaMask as provider  
3. **Read data** (e.g. total supply, a stored message) from your contract  
4. **Send a transaction** (e.g. mint a token, cast a vote) via the UI  

---

## 🧠 Part 4: Bonus Zero‑Knowledge Exploration

- **Why ZK?** Privacy in voting, private identity, rollups  
- **Concepts to know**: circuit → proof → on‑chain verifier  
- **Try a toy demo**: generate a simple “I know a secret” proof and deploy its verifier alongside your main contract  
- **Tool suggestions**: Circom + SnarkJS, Noir, zk‑kit

---

## 🎨 Easy Project Themes

Pick one of these, deploy it, and connect it in a tiny frontend:

- **Token Faucet** – let any address claim a few tokens once  
- **Mini Voting DApp** – users create proposals & cast votes on‑chain  
- **On‑chain Notepad** – store short messages in the contract  
- **Tip Jar** – send ETH or tokens as tips to a designated address  

---

## 📚 Key Resources

- **Hardhat Guide** → hardhat.org/getting‑started  
- **Deploying to Networks** → hardhat.org/hardhat‑runner/docs/guides/deploying  
- **Ethers.js Docs** → docs.ethers.org  
- **Holesky Faucet** → [Holesky](https://cloud.google.com/application/web3/faucet/ethereum/holesky)  
- **Intro to ZK** → zkhack.dev / docs.circom.io  

---

## ✅ Submission Checklist

- **Short project description** in your README  
- **Deployed contract address** on Holesky 
- **GitHub repo** containing:  
  - `contracts/` (your Solidity files)  
  - `scripts/` (deployment script)  
  - `frontend/` (minimal UI)  
- **2–4 min demo video** showing:  
  - Local compile & test  
  - Deployment to testnet  
  - UI interaction  
  - (Optional) ZK demo  

---

🔥 You’re now bridging local development, testnet deployment, frontend integration, and next‑gen ZK concepts. Let’s ship your first real‑world Web3 project! 🚀  

