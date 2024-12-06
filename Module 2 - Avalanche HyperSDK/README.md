# TokenVM - HyperSDK 

**Mint, Transfer, and Trade User-Generated Tokens, All On-Chain**

TokenVM is an example application designed to demonstrate the capabilities of the HyperSDK. It enables users to mint, transfer, and trade custom tokens on-chain. With a user-friendly CLI and support for efficient token management and trading, TokenVM simplifies the process of building decentralized applications.

---

## **Key Features**

### 1. **Arbitrary Token Minting**
- Create and manage user-generated tokens.
- Update metadata (e.g., during a reveal or ownership change).
- Burn tokens and transfer ownership seamlessly.
- Highly optimized storage for balance entries: `72 bytes` per balance entry.

### 2. **On-Chain Trading**
- Fully on-chain support for trading between any two tokens.
- Create and fill orders with a robust in-memory order book.
- Support for partial fills and automatic refunds for unused inputs.
- Expiring fills to ensure timely execution without manual cancellation.

### 3. **In-Memory Order Book**
- Provides a simple and efficient way to interact with orders on-chain.
- Maintains state using max heaps for best rates per asset pair.
- Resistant to sandwich attacks: trades occur at fixed rates for the selected order.

### 4. **Avalanche Warp Support**
- Enables cross-chain asset transfers without a trusted bridge.
- Tracks imported/exported assets to prevent infinite minting.
- Transparent import/export policies to minimize contagion risks.

---

## **Status**
TokenVM is in **ALPHA** and is not production-ready. The framework is under active development, and significant changes may occur as the modules are optimized and audited.

---

## **Getting Started**

### **Prerequisites**
- [Avalanche Network Runner (ANR)](https://github.com/ava-labs/avalanche-network-runner)
- [Go Programming Language](https://golang.org/doc/install)
- A basic understanding of blockchain and token economics.

### **Installation**
1. Clone the repository:
   ```bash
   git clone https://github.com/Metacrafters/tokenvm.git
   cd tokenvm
   ```
2. Build the CLI tool:
   ```bash
   ./scripts/build.sh
   ```
   The compiled CLI will be available at `./build/token-cli`.

3. Launch your own TokenVM Subnet:
   ```bash
   ./scripts/run.sh
   ```
   - For a single Subnet, use:
     ```bash
     MODE="run-single" ./scripts/run.sh
     ```

---

## **Usage**

### **1. Import Default Key**
```bash
./build/token-cli key import demo.pk
```

### **2. Connect Chains**
```bash
./build/token-cli chain import-anr
```

### **3. Create a Token**
```bash
./build/token-cli action create-asset
```
Example output:
```text
database: .token-cli
address: token1rvzh...
chainID: Em2pZtHr...
metadata: YourTokenName
continue (y/n): y
✅ txID: 27grFs9...
```
The `txID` is the `assetID` of your new token.

### **4. Mint Tokens**
```bash
./build/token-cli action mint-asset
```
Example output:
```text
assetID: 27grFs9...
amount: 10000
recipient: token1rvzh...
✅ txID: X1E5CVFg...
```

### **5. Trade Tokens**
- Create an offer:
  ```bash
  ./build/token-cli action create-order
  ```
- Fill an order:
  ```bash
  ./build/token-cli action fill-order
  ```

---

## **Architecture Overview**

### **Modules**
1. **Storage**  
   Optimized for balances and orders using minimal bytes per entry. Enables parallel execution of transfers and fills.
   
2. **Order Book**  
   Maintains live order data using max heaps for best rate selection.

3. **RPC Support**  
   Interacts with external applications via an in-memory state representation.

4. **Avalanche Warp Messaging**  
   Seamless cross-chain communication for token transfers without trust dependencies.

---

## **Security Features**
- **Sandwich Attack Resistance:** Prevents block producers from manipulating transaction execution.
- **Partial Fill Refunds:** Returns unused inputs in the case of overfills.
- **Scoped Validity:** Transactions can have expiration times to prevent stale orders.

---

## **Demo**
1. Start the network:
   ```bash
   ./scripts/run.sh
   ```
2. Build the CLI:
   ```bash
   ./scripts/build.sh
   ```
3. Import keys and chains:
   ```bash
   ./build/token-cli key import demo.pk
   ./build/token-cli chain import-anr
   ```
4. Create, mint, and trade your token as described above.

---

## **Contributing**
Contributions are welcome! Please open an issue or submit a pull request to contribute.

---

## **Contact**
For support or inquiries, please contact the Metacrafters team via the repository's Issues page.

---

Leverage **TokenVM** to explore the intersection of blockchain and on-chain trading. Happy building! 🎉
