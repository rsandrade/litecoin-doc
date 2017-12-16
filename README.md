# Litecoin Developer Guide
_Find detailed information about the Litecoin protocol and related specifications_

> **Disclaimer:** This documentation has not been extensively reviewed by Litecoin experts and so likely contains numerous errors. Please use the Issues feature or fork and pull at GitHub to help us improve.

The **Litecoin Developer Guide** aims to provide the information you need to understand Litecoin and start building Litecoin-based applications, but it is not a specification. To make the best use of this documentation, you may want to install the current version of [Litecoin Core](https://www.litecoin.org), either from source or from a pre-compiled executable.

Questions about Litecoin development are best asked in one of the Litecoin development communities. Errors or suggestions related to documentation can be submitted as an issue `or posted to the litecoin-documentation mailing list`.

In the following documentation, some strings have been shortened or wrapped: “[…]” indicates extra data was removed, and lines ending in a single backslash “\” are continued below. If you hover your mouse over a paragraph, cross-reference links will be shown in blue. If you hover over a cross-reference link, a brief definition of the term will be displayed in a tooltip.

## [Block Chain](Block-Chain.md)
- [Block Chain Overview](Block-Chain.md#block-chain-overview)
- [Proof Of Work](Block-Chain.md#proof-of-work)
- [Block Height And Forking](Block-Chain.md#block-height-and-forking)
- [Transaction Data](Block-Chain.md#transaction-data)
- [Consensus Rule Changes](Block-Chain.md#consensus-rule-changes)
  - [Detecting Forks](Block-Chain.md#detecting-forks)
    
## [Transactions](Transactions.md)
- [P2PKH Script Validation](Transactions.md#p2pkh-script-validation)
- [P2SH Scripts](Transactions.md#p2sh-scripts)
- [Standard Transactions](Transactions.md#standard-transactions)
  - [Non-Standard Transactions](Transactions.md#non-standard-transactions)
- [Signature Hash Types](Transactions.md#signature-hash-types)
- [Locktime And Sequence Number](Transactions.md#locktime-and-sequence-number)
- [Transaction Fees And Change](Transactions.md#transaction-fees-and-change)
- [Avoiding Key Reuse](Transactions.md#avoiding-key-reuse)
- [Transaction Malleability](Transactions.md#transaction-malleability)

## [Contracts](Contracts.md)
- [Escrow And Arbitration](Contracts.md#escrow-and-arbitration)
- [Micropayment Channel](Contracts.md#micropayment-channel)
- [CoinJoin](Contracts.md#coinjoin)

## [Wallets](Wallets.md)
- Wallet Programs
  - Full-Service Wallets
  - Signing-Only Wallets
    - Offline Wallets
    - Hardware Wallets
  - Distributing-Only Wallets
- Wallet Files
- Private Key Formats
  - Wallet Import Format (WIF)
  - Mini Private Key Format
- Public Key Formats
- Hierarchical Deterministic Key Creation
  - Hardened Keys
  - Storing Root Seeds
- Loose-Key Wallets

## Payment Processing
- Pricing Orders
- Requesting Payments
  - Plain Text
  - litecoin: URI
  - QR Codes
  - Payment Protocol
- Verifying Payment
- Issuing Refunds
- Disbursing Income (Limiting Forex Risk)
  - Merge Avoidance
  - Last In, First Out (LIFO)
  - First In, First Out (FIFO)
- Rebilling Recurring Payments

## Operating Modes
- Full Node
- Simplified Payment Verification (SPV)
  - Potential SPV Weaknesses
  - Bloom Filters
  - Application Of Bloom Filters
- Future Proposals

## P2P Network
- Peer Discovery
- Connecting To Peers
- Initial Block Download
  - Blocks-First
  - Headers-First
- Block Broadcasting
  - Orphan Blocks
- Transaction Broadcasting
  - Memory Pool
- Misbehaving Nodes
- Alerts

## Mining
- Solo Mining
- Pool Mining
- Block Prototypes
  - getwork RPC
  - getblocktemplate RPC
  - Stratum

## Third-party resources
- [BitcoinJS](https://github.com/bitcoinjs/bitcoinjs-lib)
  - bitcoinjs/bitcoinjs-lib#389
  - [Altcoin and bitcoinjs #389](https://github.com/bitcoinjs/bitcoinjs-lib/issues/389)
