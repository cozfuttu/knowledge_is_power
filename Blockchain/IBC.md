IBC stands for **Inter-Blockchain Communication Protocol**. It's a protocol that facilitates reliable and secure communication between different [[Blockchain]] networks. This technology allows various blockchains to transfer tokens and other data among each other, enabling interoperability between distinct chains that otherwise operate independently.

The IBC protocol is crucial for creating scalable networks of interconnected blockchains, which can transfer value and information seamlessly without the need for intermediaries. This kind of architecture supports a wide variety of applications, including [[DeFi]], cross-chain exchanges, and multi-chain applications. One of the prominent implementations of IBC is within the [[Cosmos Network]], where it serves as a foundational component enabling different blockchain "zones" to interact efficiently within a larger ecosystem.

------------------

## What is IBC?

IBC is a universal interoperability protocol that allows two different blockchains to communicate with one another. IBC guarantees _reliable_, _ordered_, and _authenticated_ communication.

Perhaps one of the most important properties of IBC is trust-minimization. In blockchains, the property of trust-minimization is inherently linked to security. No distributed system is entirely ‘trustless’. Therefore, the question of security boils down to who or what is trusted, and how can that trust be violated i.e., what does it take for the trusted entity to be corrupted?

In this sense, and unlike most bridging solutions, IBC uses no trusted third parties. This means that if you trust two particular chains to use the functions they provide (and by default their consensus mechanisms), then there is no additional trust assumption required while using IBC to interact between said chains.

IBC is also more than just a bridge that facilitates token transfers. It is a **general**-**purpose** message passing protocol. This means that _any form of data_ can be communicated over IBC.

## How does IBC work?

In order to understand how IBC works, it is important to separate the two different layers of IBC — 1) the transport layer and 2) the application layer.

![[Pasted image 20240627204148.png]]

### Transport Layer

Messages communicated over IBC are transported within [data packets](https://computersciencewiki.org/index.php/Data_packet). And the transport layer is responsible for _transporting_, _authenticating_, and _ordering_ these data packets.

The transport layer does not specify anything about what the data in the packets should be or how they should be interpreted by a receiving chain. From the transport layer’s point of view, information within data packets are just random bytes.

The key components of the transport layer are **light clients, relayers, connections, and channels.**

A light client is a lightweight representation of a blockchain. Unlike a [full node](https://github.com/cosmos/cosmos/blob/master/VALIDATORS_FAQ.md#what-is-a-full-node), light clients do not store the entire history of all the messages contained in a blockchain. Neither do they execute transactions. Rather, light clients are designed to connect to a full node, and verify block headers (a summary of the data contained within a block). This allows light clients to be efficient in terms of storage and computation.

Two independent blockchains _A_ and _B_ interacting over IBC have [_light clients_](https://medium.com/tendermint/everything-you-need-to-know-about-the-tendermint-light-client-f80d03856f98) of the counterparty chain. This means that _A_ has a light client on its blockchain which acts as a lightweight representation of _B’s_ blockchain. When _A_ wants to communicate a certain message _‘X’_ with _B_, it sends the header of the block in which that message exists, along with a commitment proof of that message to _B_. The commitment proof is used to verify the presence or absence of a particular message on _A_. Using the block header and proof, _B_ cryptographically verifies that _A_ did indeed perform _X_. **It is this use of light clients in IBC that allow blockchains to exchange messages with one another without the need for a trusted third party.**

But _A_ and _B_ do not directly send these messages/data packets between each other. Instead, when _A_ wishes to send a message to _B_, it commits or stores a [hash](https://www.investopedia.com/terms/h/hash.asp) of a data packet containing the message in its [state machine](https://www.techopedia.com/definition/16447/state-machine). _Relayers_, which are off-chain processes, constantly observe for such messages. When they see that _A_ has committed a message intended for _B_ in its state machine, they simply pick up this message and pass it onto _B_. Note that relayers are permissionless and therefore can be run by anyone.

_Connections_ are responsible for connecting light clients on two different chains. And _channels_ are conduits for transferring packets between modules on these different chains. Therefore, while connections are chain-specific, channels are module-specific. Each channel end has a unique channel ID (and a port ID) that is used to accurately route packets between two modules.

### Application Layer

The application layer is what end-users interact with. It consists of various applications that use the transport layer to build on top. The transport layer does not specify how data packets need to be interpreted. This role is performed by the application layer.

IBC supports a variety of applications such as fungible/non-fungible token transfers, cross-chain oracle feeds, [Interchain Accounts](https://interchain-io.medium.com/welcome-to-the-ibc-gang-lets-talk-f469883e0ffe), Interchain Queries, [Fee middleware](https://interchain-io.medium.com/ibc-relaying-as-a-service-the-in-protocol-incentivization-story-9922c7b953f0) (to incentivise relayers), etc.

For example, the IBC-level application for token transfers — termed [Interchain Standard 20](https://github.com/cosmos/ibc/blob/master/spec/app/ics-020-fungible-token-transfer/README.md) (ICS 20) — specifies how data packets should be structured and how they are to be interpreted by receiving chains. In the case of fungible token transfers, data packets contain information regarding the sender, receiver, amount, and denomination (IBC denom). The denom field traces the path that a particular token has gone through to reach a certain chain. Logic regarding how the packets are to be acted upon are also specified by ICS 20.

A simple analogy that can be helpful in understanding IBC is that of the mail delivery system. When you send a letter to someone, you send it through a postal service that collects the envelope containing the letter from you and deposits it into the recipient’s mailbox. The recipient then opens said envelope and reads your letter. The transport layer of IBC can be thought of as the postal service. The postal service does not tell you what the contents of the letter should be, or how the recipient should interpret your message.

Neither do they know what the contents of the envelope are. It only performs the action of collecting the envelope from point A and sending it to point B. The envelope itself can be thought of as IBC packets that are sent from one chain to another. And on this envelope, you would specify the address of the recipient. This is similar to how IBC packets contain information regarding who sent the packet (specified by the channel ID) and to whom it is intended for (specified by the counterparty channel ID). In the end, it is the receiver (application) that is responsible for opening the envelope (data packet) and interpreting the contents of the letter.
## References
[What is IBC](https://medium.com/the-interchain-foundation/eli5-what-is-ibc-def44d7b5b4c)
