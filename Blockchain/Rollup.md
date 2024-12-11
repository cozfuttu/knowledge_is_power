A **rollup** in [[blockchain]] refers to a **layer 2 scaling solution** designed to increase the throughput and efficiency of a blockchain by processing transactions off-chain while still maintaining security through the underlying main chain (layer 1). Rollups enable faster and cheaper transactions without sacrificing the security and decentralization of the base layer blockchain.

### Key Features of Rollups

1. **Off-Chain Processing**:
    
    - Transactions are executed off-chain in the rollup, and the results (or summaries) are posted on-chain.
2. **Security Inheritance**:
    
    - Rollups inherit the security of the underlying layer 1 blockchain by posting transaction data or proofs on-chain.
3. **Batching Transactions**:
    
    - Transactions are aggregated (rolled up) into batches to reduce the amount of data that needs to be stored and verified on the main chain.
4. **Lower Costs**:
    
    - By moving execution off-chain, rollups significantly reduce [[gas|gas fees]] for users.
5. **Scalability**:
    
    - Rollups can handle a much higher volume of transactions compared to the main chain.

---

### Types of Rollups

1. **Optimistic Rollups**:
    
    - Assume transactions are valid by default.
    - Fraud proofs are used to detect and challenge invalid transactions.
    - Example: **Optimism**, **Arbitrum**.
2. **Zero-Knowledge Rollups (ZK-Rollups)**:
    
    - Use cryptographic proofs (e.g., zk-SNARKs) to verify the correctness of transactions.
    - More efficient and faster finality but require advanced cryptographic techniques.
    - Example: **zkSync**, **StarkNet**.

---

### How Rollups Work

1. **Transaction Execution**:
    
    - Transactions are processed off-chain in the rollup environment.
2. **Data Commitment**:
    
    - Compressed transaction data or proofs are submitted to the main chain.
3. **Validation**:
    
    - The main chain either assumes validity (Optimistic Rollups) or verifies validity proofs (ZK-Rollups).
4. **Dispute Resolution**:
    
    - For Optimistic Rollups, a challenge period exists where invalid transactions can be flagged.

---

### Benefits of Rollups

- **High Throughput**: Can process thousands of transactions per second.
- **Cost-Effective**: Lower gas fees compared to the main chain.
- **Security**: Transactions rely on the base layer's robustness.
- **Flexibility**: Supports smart contracts and complex dApps.