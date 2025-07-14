
# 🧪 Foundry Cross-Chain Rebase Token (CCIP)

This project is a part of the **Cyfrin Foundry Advanced Course** focused on cross-chain development using **Chainlink CCIP**. It implements a **cross-chain rebase token** architecture using Foundry.

---

## ✨ About

A decentralized protocol where users can deposit ETH and receive **rebase tokens** that accrue yield over time. The twist? You can **bridge these tokens** to other chains via Chainlink CCIP and retain your interest rate.

---

## 🧰 Getting Started

### Requirements

- [Git](https://git-scm.com/)
- [Foundry](https://book.getfoundry.sh/getting-started/installation)

Check if installed:
```bash
git --version
forge --version
````

---

## ⚡ Quickstart

```bash
git clone https://github.com/your-repo/ccip-rebase-token
cd ccip-rebase-token
make build
```

---

## 🚀 Usage

### Start Local Node

```bash
make anvil
```

### Deploy Locally

```bash
make deploy
```

### Deploy on Sepolia

```bash
make deploy ARGS="--network sepolia"
```

### Run Tests

```bash
make test
```

### Run Coverage Report

```bash
make coverage
```

---

## 🧪 Testing Strategy

This repo focuses on:

* ✅ Unit tests
* ✅ Fuzzing tests
* 🔜 Forked & staging tests (optional)

All test files are in `test/`:

* `RebaseToken.t.sol` - Token & vault logic
* `CrossChain.t.sol` - CCIP bridging logic

---

## 🌐 Deployment on Testnet

### 1. Setup `.env` file:

```dotenv
SEPOLIA_RPC_URL=your_sepolia_rpc_url
PRIVATE_KEY=your_private_key
ETHERSCAN_API_KEY=your_etherscan_key (optional)
```

> ⚠️ Never use a real key with funds. Use test accounts only.

### 2. Get Testnet ETH

Go to [faucets.chain.link](https://faucets.chain.link/sepolia) and request Sepolia ETH.

### 3. Deploy

```bash
make deploy ARGS="--network sepolia"
```

---

## 🛠 Cast Interactions

Instead of writing extra scripts, use `cast`:

```bash
cast send <vault-address> "deposit()" --value 0.1ether --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY
```

```bash
cast send <vault-address> "redeem(uint256)" 10000000000000000 --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY
```

---

## ⛽ Gas Estimation

```bash
make snapshot
```

Check `.gas-snapshot` for output.

---

## 🎨 Formatting

```bash
make format
```

---

## 📌 Design Decisions

* 💰 Interest rate **decreases** with protocol usage
* ⛓️ Users can bridge tokens via Chainlink CCIP
* 🪙 Interest **sticks** with the user when bridging
* ⚠️ No yield earned **during bridge transit**
* 🔁 Only deposit & withdrawal on L1 is allowed

---

## 🧠 Assumptions

* Vault contract holds all ETH
* Rebase tokens track user's stake
* Early/L2 users are rewarded with higher rates

---

## 🙌 Special Thanks

This project is a part of the **CyfrinUpdraft Course**.

Built using:

* Chainlink CCIP 🟡
* OpenZeppelin Contracts 🛡️
* Forge Std 🧪