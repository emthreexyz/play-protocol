# Emthree Play Protocol: Onchain vs Hybrid Listening Data Design

## Overview

The Emthree Play Protocol supports tracking media listening events such as music, podcasts, and audiobooks. A key design choice is how to store and verify these events: fully onchain, offchain in a database, or a hybrid model.

This document outlines the tradeoffs of each approach and recommends a hybrid solution optimized for scalability, transparency, and user privacy.

---

## Options for Listening Data Storage

### Option 1: 100% Onchain

**Pros:**
- Fully transparent and immutable
- Enables composability for other dapps
- Trustless rewards and incentive systems

**Cons:**
- High cost and low scalability (especially on L1s)
- Public exposure of user listening behavior
- Not feasible for high-frequency events like listens

**Use Cases:**
- First listen events
- Reward-triggering milestones (e.g. daily streaks)
- Achievement minting

---

### Option 2: Hybrid (Database + Onchain Events)

**Pros:**
- Scalable and performant
- Preserves user privacy
- Selective onchain proofs for verifiable achievements
- Cheaper gas usage

**Cons:**
- Requires trust in the platform’s database
- Needs a verification method for cross-system use

**Use Cases:**
- Daily listening tracking in database
- Monthly “Wrapped”-style NFT collectibles
- Onchain badge minting via ZK proofs or Merkle roots

---

## Recommendation

Emthree will adopt a **Hybrid Model**:

- **Database:** Record all raw listening data (hashed track ID, wallet, timestamp, device, NFT metadata)
- **Onchain:** Publish important milestones, badge claims, leaderboard positions, and evolving NFTs based on verified listening behavior
- **Optional Verifiability:** Use Merkle proofs or ZK circuits to allow offchain data to trigger onchain events trustlessly

---

## Future Enhancements

- Add a pluggable **Oracle layer** to expose listening data onchain
- Develop a **verifiable proof format** (e.g., zkSNARKs, Merkle proofs) to decentralize trust in offchain data
- Enable user-controlled **data export and transparency tools**

