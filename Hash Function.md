A hash function is a function that is used to map data of arbitrary size to fixed-size values. The values returned by a hash function are called hash values, hash codes, digests, or simply hashes.

Hash functions have many uses in computing. They are commonly used in hash tables, a fundamental data structure in computer science, to quickly locate a data record given its search key. Hash functions are also used in [[Cryptography]] for purposes such as data integrity verification and password storage.

Here are some important properties of a hash function:

1. **Deterministic**: For a given input, the output (hash) will always be the same.
    
2. **Fixed Size**: Regardless of the size of the input data, the output hash length stays the same.
    
3. **Fast to Compute the Hash Value**: For any given input, it should be computationally easy to calculate the hash.
    
4. **Uniform Distribution (Avalanche Effect)**: Hash functions should provide a uniform distribution across the hash values, i.e., a small change to input data should produce such a drastic change in output that the new hash value appears uncorrelated with the old hash value.
    
5. **Pre-image Resistant**: Given a hash output, it should be computationally infeasible to determine the original input. This means that even if you have a hash value, you can't work out what the original data was.
	
6. **Second Pre-image Resistance**: Given an input and its hash, it should be computationally infeasible to find a different input with the same hash. In other words, it should be very difficult to find two different pieces of data that produce the same hash.
	
7. **Collision Resistance**: It should be computationally infeasible to find any two distinct inputs that hash to the same output. A collision happens when two different pieces of data produce the same hash.

Some examples of commonly used hash functions include the MD5, SHA-1, and SHA-256 algorithms. Please note that not all hash functions are suitable for all purposes; for instance, MD5 and SHA-1 are considered to be broken for cryptographic uses due to vulnerability to collision attacks.