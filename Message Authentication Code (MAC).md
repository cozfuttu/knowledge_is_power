A Message Authentication Code (MAC) is a [[Cryptography|cryptographic]] function that provides data integrity and authenticity. It is used to verify that a message has not been altered during transmission and that it was created by a legitimate sender.

![[Message_Authentication_Code_(MAC).png]]

Here's how it works:

1. The sender and receiver agree on a secret key in advance.
2. When the sender wants to send a message, they input the message and the secret key into the MAC function. This produces a MAC value or tag.
3. The sender then sends the message along with the MAC value.
4. Upon receiving the message and the MAC, the receiver inputs the message and their copy of the secret key into the MAC function.
5. If the MAC value that the receiver computes matches the MAC value sent with the message, the receiver can be confident that the message was not altered during transmission and that it came from the legitimate sender.

MACs are commonly used in various security protocols, including IPsec and SSL/TLS. They are an essential tool in the field of information security.