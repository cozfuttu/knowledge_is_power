**Yao's Millionaires' Problem** is a classic problem in **secure multi-party computation (MPC)**, introduced by Andrew Yao in 1982. It is a foundational problem in cryptography and secure computation.

### **Problem Statement**

Two millionaires, Alice and Bob, want to compare their wealth to determine who is richer, but neither wants to reveal their exact fortune to the other. Mathematically, given their respective fortunes xxx and yyy, they want to securely compute:

Compare(x,y)={1,if x>y0,otherwise\text{Compare}(x, y) = \begin{cases} 1, & \text{if } x > y \\ 0, & \text{otherwise} \end{cases}Compare(x,y)={1,0,​if x>yotherwise​

### **Solution Approach**

Yao proposed the first **secure two-party computation (2PC)** protocol to solve this problem, introducing the concept of **garbled circuits**. The idea is to:

1. **Encrypt the function itself** rather than the inputs.
2. **Use an oblivious transfer mechanism** so that one party (Bob) evaluates the circuit without learning anything about Alice's inputs beyond the final result.

### **Why Is It Important?**

- It laid the foundation for **secure computation** protocols.
- It introduced **garbled circuits**, a technique still widely used in cryptographic protocols.
- It is a fundamental example of how two parties can compute a function without revealing private inputs.

### **Modern Applications**

- **Privacy-preserving auctions** (e.g., bidding comparisons)
- **Secure voting systems**
- **Confidential salary comparisons** in HR
- **Private set intersection** (used in privacy-preserving analytics)