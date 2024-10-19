
# Signature Verification Contract with Diamond Standard (EIP-2535)

This project implements a signature verification system that allows whitelisted addresses to claim ERC20 tokens by signing a message. The contract is developed using the **Diamond Standard (EIP-2535)**, enabling modular contract architecture. This implementation also supports **Foundry** for smart contract testing and **Hardhat** for deployment and testing scripts.

## Features

1. **Signature Verification**: Verify that an address is part of the whitelist and that a valid signature is provided before claiming ERC20 tokens.
2. **Modular Contract Architecture**: Use of the **Diamond Standard** for flexible, upgradeable contract management.
3. **Whitelist Management**: The contract owner can add addresses to the whitelist.
4. **ERC20 Token Claiming**: Whitelisted users can claim a specified amount of ERC20 tokens after signature verification.

## Installation

1. **Clone the repository**

```bash
git clone 
cd foundry-diamond-signature-verification
```

2. **Install Dependencies**

Install dependencies for Hardhat and the Diamond Standard.


5. **Compile Contracts using Foundry**

```bash
forge build
```

---

## Contract Overview

The smart contract leverages **EIP-2535 Diamond Standard** to split the logic into different facets, making it modular and upgradeable. 

- **Diamond.sol**: The diamond contract itself.
- **DiamondCutFacet.sol**: Manages the upgrading of facets.
- **DiamondLoupeFacet.sol**: Used for inspecting the diamond (getting facet addresses).
- **OwnershipFacet.sol**: Manages ownership of the contract.
- **SignatureVerificationFacet.sol**: Implements the signature verification and token claim logic.

---

## How to Use

### 1. **Set up Environment Variables**

Set up `.env` with the necessary details for deployment, such as private key and RPC URL for the Ethereum network.

```bash
cp .env.example .env
```

### 2. **Compile Contracts**
Using Foundry:

```bash
forge build
```


### 3. **Deploy Contracts**

Using Foundry's script:

```bash
forge script script/DeployDiamond.s.sol --broadcast
```

### 4. **Running Tests**


Using Foundry:

```bash
forge test
```
---

## Diamond Standard Explanation

The **Diamond Standard (EIP-2535)** is an Ethereum standard for creating modular, upgradeable smart contracts. It allows splitting logic into multiple facets, each with its own functionality, while using a single contract address for interaction.

**Key Benefits:**
- **Modularity**: Separate facets can be deployed and upgraded independently.
- **Upgradeability**: New functionality can be added without modifying the core diamond contract.

**Diamond Components:**
- **Diamond.sol**: Core contract that forwards calls to specific facets.
- **DiamondCutFacet.sol**: Manages adding, removing, and replacing facets.
- **DiamondLoupeFacet.sol**: Provides tools to query the current facets of the diamond.

---

## License

This project is licensed under the MIT License.

---
