# Litecoin-doc
Documentation for Litecoin

## Transactions

Transactions let users spend lites. Each transaction is constructed out of several parts which enable both simple direct payments and complex transactions. This section will describe each part and demonstrate how to use them together to build complete transactions.

To keep things simple, this section pretends coinbase transactions do not exist. Coinbase transactions can only be created by Litecoin miners and they’re an exception to many of the rules listed below. Instead of pointing out the coinbase exception to each rule, we invite you to read about coinbase transactions in the block chain section of this guide.

<p align="center">
    <img src="img/en-tx-overview.svg"><br>
    <i></i>
</p>

The figure above shows the main parts of a Litecoin transaction. Each transaction has at least one input and one output. Each input spends the lites paid to a previous output. Each output then waits as an Unspent Transaction Output (UTXO) until a later input spends it. When your Litecoin wallet tells you that you have a 10,000 lites balance, it really means that you have 10,000 lites waiting in one or more UTXOs.

Each transaction is prefixed by a four-byte transaction version number which tells Litecoin peers and miners which set of rules to use to validate it. This lets developers create new rules for future transactions without invalidating previous transactions.

<p align="center">
    <img src="img/en-tx-overview-spending.svg"><br>
    <i></i>
</p>

An output has an implied index number based on its location in the transaction—the index of the first output is zero. The output also has an amount in lites which it pays to a conditional pubkey script. Anyone who can satisfy the conditions of that pubkey script can spend up to the amount of lites paid to it.

An input uses a transaction identifier (txid) and an output index number (often called “vout” for output vector) to identify a particular output to be spent. It also has a signature script which allows it to provide data parameters that satisfy the conditionals in the pubkey script. (The sequence number and locktime are related and will be covered together in a later subsection.)

The figures below help illustrate how these features are used by showing the workflow Alice uses to send Bob a transaction and which Bob later uses to spend that transaction. Both Alice and Bob will use the most common form of the standard Pay-To-Public-Key-Hash (P2PKH) transaction type. P2PKH lets Alice spend lites to a typical Litecoin address, and then lets Bob further spend those lites using a simple cryptographic key pair.

<p align="center">
    <img src="img/en-creating-p2pkh-output.svg"><br>
    <i></i>
</p>

Bob must first generate a private/public key pair before Alice can create the first transaction. Litecoin uses the Elliptic Curve Digital Signature Algorithm (ECDSA) with the secp256k1 curve; secp256k1 private keys are 256 bits of random data. A copy of that data is deterministically transformed into an secp256k1 public key. Because the transformation can be reliably repeated later, the public key does not need to be stored.

The public key (pubkey) is then cryptographically hashed. This pubkey hash can also be reliably repeated later, so it also does not need to be stored. The hash shortens and obfuscates the public key, making manual transcription easier and providing security against unanticipated problems which might allow reconstruction of private keys from public key data at some later point.

Bob provides the pubkey hash to Alice. Pubkey hashes are almost always sent encoded as Litecoin addresses, which are base58-encoded strings containing an address version number, the hash, and an error-detection checksum to catch typos. The address can be transmitted through any medium, including one-way mediums which prevent the spender from communicating with the receiver, and it can be further encoded into another format, such as a QR code containing a bitcoin: URI.

Once Alice has the address and decodes it back into a standard hash, she can create the first transaction. She creates a standard P2PKH transaction output containing instructions which allow anyone to spend that output if they can prove they control the private key corresponding to Bob’s hashed public key. These instructions are called the pubkey script or scriptPubKey.

Alice broadcasts the transaction and it is added to the block chain. The network categorizes it as an Unspent Transaction Output (UTXO), and Bob’s wallet software displays it as a spendable balance.

When, some time later, Bob decides to spend the UTXO, he must create an input which references the transaction Alice created by its hash, called a Transaction Identifier (txid), and the specific output she used by its index number (output index). He must then create a signature script—a collection of data parameters which satisfy the conditions Alice placed in the previous output’s pubkey script. Signature scripts are also called scriptSigs.

Pubkey scripts and signature scripts combine secp256k1 pubkeys and signatures with conditional logic, creating a programmable authorization mechanism.

<p align="center">
    <img src="img/en-unlocking-p2pkh-output.svg"><br>
    <i></i>
</p>

For a P2PKH-style output, Bob’s signature script will contain the following two pieces of data:

    His full (unhashed) public key, so the pubkey script can check that it hashes to the same value as the pubkey hash provided by Alice.

    An secp256k1 signature made by using the ECDSA cryptographic formula to combine certain transaction data (described below) with Bob’s private key. This lets the pubkey script verify that Bob owns the private key which created the public key.

Bob’s secp256k1 signature doesn’t just prove Bob controls his private key; it also makes the non-signature-script parts of his transaction tamper-proof so Bob can safely broadcast them over the peer-to-peer network.

<p align="center">
    <img src="img/en-signing-output-to-spend.svg"><br>
    <i></i>
</p>

As illustrated in the figure above, the data Bob signs includes the txid and output index of the previous transaction, the previous output’s pubkey script, the pubkey script Bob creates which will let the next recipient spend this transaction’s output, and the amount of lites to spend to the next recipient. In essence, the entire transaction is signed except for any signature scripts, which hold the full public keys and secp256k1 signatures.

After putting his signature and public key in the signature script, Bob broadcasts the transaction to Litecoin miners through the peer-to-peer network. Each peer and miner independently validates the transaction before broadcasting it further or attempting to include it in a new block of transactions.
