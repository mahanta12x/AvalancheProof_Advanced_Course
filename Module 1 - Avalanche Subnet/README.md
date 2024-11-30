# DeFi Empire: A Simple DeFi Kingdom Clone

## Overview

In this project, we delve into the fundamentals of creating a blockchain-based gaming experience using Avalanche's EVM Subnet. By following the steps in this guide, you’ll set up the foundational building blocks for a DeFi Kingdom clone. The goal is to enable players to collect, trade, and battle digital assets while earning rewards in a decentralized finance ecosystem.

### Features
- **Custom EVM Subnet**: Build your blockchain tailored for gaming.
- **Native Token Deployment**: Define and use a token as in-game currency.
- **Smart Contracts**: Deploy ERC20 and Vault contracts for game functionalities.
- **Integration with Metamask**: Interact with your custom subnet easily.
- **Rewards and Trading**: Create engaging game mechanics with tokens as rewards.

---

## Project Structure

### Smart Contracts
#### **ERC20 Token Contract**
The ERC20 contract handles:
- Minting and burning tokens.
- Balances and transfers between players.
- Approval and allowance management.

#### **Vault Contract**
The Vault contract manages:
- Deposits and withdrawals of the ERC20 token.
- Shares for players based on token contributions.

### Tools Used
- **Unix-Based Computer** (MacOS or Linux)
- **Solidity** (For writing smart contracts)
- **Remix** (For deploying contracts)
- **Metamask** (For interacting with the subnet)
- **Web Browser** (For accessing Remix and Metamask)

---

## Step-by-Step Guide

### 1. **Set Up Your EVM Subnet**
- Use the Avalanche CLI to create a custom subnet.
- Define your native token for in-game currency.

### 2. **Connect to Metamask**
- Add your subnet to Metamask.
- Set it as the selected network.

### 3. **Deploy Smart Contracts**
- Use Remix with Metamask to deploy:
  - **ERC20 contract** for game tokens.
  - **Vault contract** for managing deposits and withdrawals.

### 4. **Test Your Application**
- Use Remix to interact with your contracts.
- Mint tokens, make deposits, and test withdrawals.

---

## Code Walkthrough

### ERC20 Contract
The **ERC20 contract** includes functions for:
- **Minting/Burning**: Adjusting the total supply.
- **Transfer/Approve**: Handling token movement and permissions.

```solidity
function mint(uint amount) external {
    balanceOf[msg.sender] += amount;
    totalSupply += amount;
    emit Transfer(address(0), msg.sender, amount);
}
```

### Vault Contract
The **Vault contract** manages token shares:
- **Deposit**: Players deposit tokens to earn shares.
- **Withdraw**: Players withdraw tokens based on their shares.

```solidity
function deposit(uint _amount) external {
    uint shares = (_amount * totalSupply) / token.balanceOf(address(this));
    _mint(msg.sender, shares);
    token.transferFrom(msg.sender, address(this), _amount);
}
```

---

## Submission Requirements

1. **GitHub Repository**
   - Create a public repository with your project files.
   - Include a `README.md` file that explains your project's purpose and functionality.
   
2. **Video Walkthrough**
   - Record a walkthrough of your project (5 minutes max).
   - Use tools like Loom to explain your code and demonstrate functionality.

3. **Transaction/Application ID**
   - Provide the transaction ID or application ID for the deployed contracts.

---

## Assessment Rubric

Your project will be reviewed based on:
1. **Functionality**:
   - Correct deployment of the ERC20 token and Vault contracts.
   - Interaction with the Avalanche Fuji Testnet.

2. **Explanation**:
   - Clear and complete code walkthrough.
   - Demonstration of functionality in a test environment.

---

## Links for Submission

- **GitHub Repository**: [https://github.com](https://github.com)
- **Loom Video Walkthrough**: [https://loom.com]([https://loom.com](https://www.loom.com/share/bf6f6294c11d427693e5f5902d5b285e))

---

**Let’s build your DeFi Empire and dive into the exciting world of decentralized finance on Avalanche!**
