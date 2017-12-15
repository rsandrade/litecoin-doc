# Litecoin Developer Guide
_Find detailed information about the Litecoin protocol and related specifications_

> **Disclaimer:** This documentation has not been extensively reviewed by Bitcoin experts and so likely contains numerous errors. Please use the Issue and Edit links on the bottom left menu to help us improve.

The **Litecoin Developer Guide** aims to provide the information you need to understand Litecoin and start building Litecoin-based applications, but it is not a specification. To make the best use of this documentation, you may want to install the current version of [Litecoin Core](https://www.litecoin.org), either from source or from a pre-compiled executable.

Questions about Litecoin development are best asked in one of the Litecoin development communities. Errors or suggestions related to documentation can be submitted as an issue `or posted to the litecoin-documentation mailing list`.

In the following documentation, some strings have been shortened or wrapped: “[…]” indicates extra data was removed, and lines ending in a single backslash “\” are continued below. If you hover your mouse over a paragraph, cross-reference links will be shown in blue. If you hover over a cross-reference link, a brief definition of the term will be displayed in a tooltip.

- **Blockchain**
  - Block Chain Overview
  - Proof Of Work
  - Block Height And Forking
  - Transaction Data
  - Consensus Rule Changes
    - Detecting Forks
- **[Transactions](Transactions.md)** (not reviewed)
  - [P2PKH Script Validation](P2PKH-script-validation.md) (not reviewed)
  - P2SH Scripts
  - Standard Transactions
    - Non-Standard Transactions
  - Signature Hash Types
  - Locktime And Sequence Number
  - Transaction Fees And Change
  - Avoiding Key Reuse
  - Transaction Malleability
- **Contracts**
  - Escrow And Arbitration
  - Micropayment Channel
  - CoinJoin
- **Wallets**
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
- **Payment Processing**
  - Pricing Orders
  - Requesting Payments
    - Plain Text
    - bitcoin: URI
    - QR Codes
    - Payment Protocol
  - Verifying Payment
  - Issuing Refunds
  - Disbursing Income (Limiting Forex Risk)
    - Merge Avoidance
    - Last In, First Out (LIFO)
    - First In, First Out (FIFO)
  - Rebilling Recurring Payments
- **Operating Modes**
  - Full Node
  - Simplified Payment Verification (SPV)
    - Potential SPV Weaknesses
    - Bloom Filters
    - Application Of Bloom Filters
  - Future Proposals
- **P2P Network**
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
- **Mining**
  - Solo Mining
  - Pool Mining
  - Block Prototypes
    - getwork RPC
    - getblocktemplate RPC
    - Stratum
