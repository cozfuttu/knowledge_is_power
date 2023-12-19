Elliptic Curve Cryptography (ECC) is a [[Public Key (Asymmetric) Cryptography|public key encryption]] technique based on the algebraic structure of elliptic curves over finite fields. The idea behind ECC is that it provides the same level of cryptographic strength with smaller keys compared to non-ECC cryptographic systems like RSA. This means that less computational power and memory is required, making ECC particularly useful for constrained environments like mobile devices.

Here's a high-level description of how ECC works:

1. **Choose an Elliptic Curve and a Point on the Curve:** The foundation of ECC is an elliptic curve, which is defined by a mathematical equation with a specific shape. One point on this curve is chosen as a "base point."
    
2. **Define the Private and Public Keys:** Each person (or participant in the communication) chooses a private key, which is just a number, and calculates their public key. The public key is the result of the base point added to itself the number of times specified by the private key (this operation of repeated addition is also called "scalar multiplication" in the context of ECC). This operation is easy to do, but hard to reverse, which is the basis of ECC's security: given the public key, it's computationally impractical to re-derive the private key.
    
3. **Communicate Using these Keys:** Once these keys are established, they can be used to encrypt and decrypt information. When someone wants to send an encrypted message, they use the recipient's public key to encrypt the message. When the recipient gets the encrypted message, they use their own private key to decrypt it. Since only the recipient knows their private key, only they can decrypt the message.
    
4. **Key Exchange:** In addition to providing a basis for encryption/decryption of messages, ECC can also be used to securely agree on a shared secret between two parties in a public setting. This is done using a method similar to the Diffie-Hellman key exchange, but using ECC operations instead.
    

ECC is widely regarded as secure, provided that good implementation practices are followed. Its efficiency and scalability make it a popular choice for many modern cryptographic systems.