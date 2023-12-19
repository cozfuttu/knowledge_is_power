RSA cryptography, named after its creators Rivest, Shamir, and Adleman, is a  [[Public Key (Asymmetric) Cryptography|public key encryption]] system widely used for secure data transmission. In a public key system, each participant has a pair of keys: a public key which is freely shared with others, and a private key which is kept secret.

Here's a simplified description of RSA:

**Key Generation**

1. **Choose two large prime numbers**, `p` and `q`. The larger these numbers, the more secure the key.
    
2. **Compute `n = p * q`**. `n` is used as the modulus for both the public and private keys.
    
3. **Calculate the Euler's totient function**, `φ(n) = (p-1) * (q-1)`, which is the number of integers less than `n` that are coprime with `n`.
    
4. **Select an integer `e`** such that `1 < e < φ(n)` and `e` and `φ(n)` are coprime. `e` is the public key exponent.
    
5. **Compute `d`** to satisfy the equation `d * e ≡ 1 (mod φ(n))`. In other words, `d` is the multiplicative inverse of `e` modulo `φ(n)`. `d` is the private key exponent.
    

The public key consists of `(n, e)` and the private key is `(n, d)`.

**Encryption and Decryption**

When Alice wants to send a message `M` to Bob:

1. Alice first turns the message `M` into an integer `m` that is smaller than `n`.
    
2. Alice then uses Bob's public key `(n, e)` to compute the ciphertext `c = m^e mod n`.
    
3. Alice sends `c` to Bob.
    

Upon receiving the ciphertext `c`, Bob can recover `m` by using his private key `d`:

`m = c^d mod n`.

The security of RSA relies on the fact that while it's easy to multiply two large prime numbers together, it's computationally difficult to factor a large composite number back into its original primes. Thus, if the private key is kept secret, the RSA protocol allows for secure communication over an insecure network.