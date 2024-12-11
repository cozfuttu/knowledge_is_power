The **EVM (Ethereum Virtual Machine)** is the **runtime environment** for executing smart contracts on the Ethereum [[blockchain]]. It serves as a decentralized, sandboxed virtual machine that runs Ethereum's [[bytecode]], enabling developers to deploy and execute smart contracts in a secure and consistent way across all Ethereum nodes.

### Key Features of the EVM

1. **Turing-Complete**:
    
    - The EVM can execute programs of arbitrary complexity, given sufficient computational resources ([[gas]]).
2. **Deterministic**:
    
    - EVM computations yield the same output for the same input on every node, ensuring [[consensus]] across the network.
3. **Platform-Agnostic**:
    
    - It abstracts the underlying hardware, making Ethereum compatible across various platforms and devices.
4. **Secure and Isolated**:
    
    - The EVM operates in isolation, ensuring that malicious contracts cannot access the underlying system or interfere with other contracts.

---

### How the EVM Works

1. **Compilation**:
    
    - Smart contracts are written in high-level programming languages like [[Solidity]] or Vyper and then compiled into **EVM bytecode**.
2. **Execution**:
    
    - When a transaction invokes a smart contract, the EVM executes the bytecode using its stack-based architecture.
3. **Gas**:
    
    - Every operation in the EVM requires a specific amount of **gas**, which is paid for in Ether (ETH). This mechanism prevents infinite loops and ensures fair resource usage.
4. **State**:
    
    - The EVM maintains the global **state** of the Ethereum blockchain, which includes account balances, contract storage, and the state of deployed smart contracts.

---

### Components of the EVM

1. **Accounts**:
    
    - **Externally Owned Accounts (EOAs)**: Controlled by private keys (e.g., wallets).
    - **Contract Accounts**: Controlled by deployed smart contract code.
2. **Storage and Memory**:
    
    - **Storage**: Persistent, costly to use, and specific to each smart contract.
    - **Memory**: Temporary and used only during the execution of a transaction.
3. **Stack**:
    
    - A last-in-first-out (LIFO) structure used for operations like arithmetic and logic.
4. **Opcodes**:
    
    - Low-level instructions (e.g., `ADD`, `MUL`, `SSTORE`) that the EVM executes.
5. **Gas System**:
    
    - Gas is consumed for computation and storage; exceeding the gas limit halts execution.

---

### EVM-Compatible Blockchains

Many blockchains use or are compatible with the EVM, enabling cross-chain compatibility and deployment of Ethereum-based dApps:

- **Binance Smart Chain (BSC)**
- **[[Polygon]]**
- **Avalanche**
- **Fantom**
- **[[Optimism]]**
- **[[Arbitrum]]**

---

### Why is the EVM Important?

The EVM is a cornerstone of Ethereum's programmability and flexibility, enabling:

- **Smart Contracts**: Automating agreements and decentralized logic.
- **dApps**: Decentralized applications in DeFi, NFTs, gaming, etc.
- **Interoperability**: Developers can deploy the same code across EVM-compatible chains.

The EVM's widespread adoption has positioned Ethereum and its ecosystem as leaders in blockchain innovation.