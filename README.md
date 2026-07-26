# 🌊 NativeFlow Organization

Welcome to NativeFlow — **the decentralized recurring payments protocol for Stellar**.

This is the central hub for all NativeFlow repositories and documentation.

---

## 🏗️ Architecture Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           NATIVEFLOW ECOSYSTEM                               │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  ┌──────────────────────────────────────────────────────────────────────┐   │
│  │  📱 CLIENT LAYER (nativeflow-web)                                    │   │
│  │  ┌────────────────────────────────────────────────────────────────┐  │   │
│  │  │  • Freighter Wallet Integration                               │  │   │
│  │  │  • Multi-Transaction Token Approval Flow                       │  │   │
│  │  │  • Merchant Dashboard (Subscription Management)                │  │   │
│  │  │  • Web SDK / Integration Tools                                 │  │   │
│  │  └────────────────────────────────────────────────────────────────┘  │   │
│  └──────────────────┬──────────────────────────────────────────────────┘   │
│                     │ HTTPS / RPC Calls                                      │
│  ┌──────────────────▼──────────────────────────────────────────────────┐   │
│  │  🔗 BLOCKCHAIN LAYER (Stellar Testnet/Mainnet)                      │   │
│  │  ┌────────────────────────────────────────────────────────────────┐  │   │
│  │  │  Smart Contracts (nativeflow-contracts)                        │  │   │
│  │  │  ┌──────────────────────────────────────────────────────────┐ │  │   │
│  │  │  │ • Subscription Storage (Persistent Memory)              │ │  │   │
│  │  │  │ • Time-Interval Constraints & Validation                │ │  │   │
│  │  │  │ • Cross-Contract Token Transfers (CPI)                  │ │  │   │
│  │  │  │ • Authorization & Permission Checks                     │ │  │   │
│  │  │  └──────────────────────────────────────────────────────────┘ │  │   │
│  │  └────────────────────────────────────────────────────────────────┘  │   │
│  └──────────────────┬──────────────────────────────────────────────────┘   │
│                     │ Ledger State / RPC                                     │
│  ┌──────────────────▼──────────────────────────────────────────────────┐   │
│  │  🚀 AUTOMATION LAYER (nativeflow-keeper)                             │   │
│  │  ┌────────────────────────────────────────────────────────────────┐  │   │
│  │  │ Off-Chain Daemon (Always Running)                              │  │   │
│  │  │  • Ledger State Scanner (Soroban RPC)                          │  │   │
│  │  │  • Time-Interval Maturity Detection                            │  │   │
│  │  │  • Automatic Execution Triggering                              │  │   │
│  │  │  • Built-In Processing Bounty Collection                       │  │   │
│  │  │  • (Future) Dynamic Gas-Fee Optimization                       │  │   │
│  │  │  • (Future) Caching Layer (Redis/SQLite)                       │  │   │
│  │  └────────────────────────────────────────────────────────────────┘  │   │
│  └──────────────────────────────────────────────────────────────────────┘   │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘

                        ⬇️  Data Flow  ⬇️
                        
         1. User connects wallet to dashboard
         2. Authorizes subscription via smart contract
         3. Keeper daemon monitors ledger state
         4. At maturity interval, keeper triggers execution
         5. Smart contract validates and transfers tokens
         6. Keeper collects processing bounty
```

---

## 📦 Core Repositories

All three core components are decoupled and independent:

### 1. **[nativeflow-contracts](https://github.com/NativeFlow-org/nativeflow-contracts)** 🔐
Smart contract engine for subscription management and token transfers.
- Built with Rust + Soroban SDK
- Handles persistent storage, validation, and CPI token transfers
- Production-ready on Stellar Testnet

### 2. **[nativeflow-keeper](https://github.com/NativeFlow-org/nativeflow-keeper)** 🚀
Off-chain automation daemon for continuous subscription execution.
- Monitors Soroban RPC for subscription maturity
- Triggers executions and collects processing bounties
- Highly scalable and configurable

### 3. **[nativeflow-web](https://github.com/NativeFlow-org/nativeflow-web)** 💻
Front-end dashboard and integration SDK for merchants.
- React-based merchant dashboard
- Freighter Wallet integration
- Web3 utilities and contract interaction tools

---

## 🚀 Quick Start

**Want to contribute?** Start here:

1. **Read the [Profile README](./profile/README.md)** for full ecosystem overview
2. **Check the [Contributing Guide](./CONTRIBUTING.md)** for workflow & standards
3. **Pick a component** to work on (contracts, keeper, or web)
4. **Claim an issue** from the roadmap
5. **Submit a PR** following our template

---

## 📚 Documentation

- **[Organization Profile](./profile/README.md)** – Full ecosystem overview & architecture
- **[Contributing Guide](./CONTRIBUTING.md)** – Contribution workflow, code standards, PR process
- **[Architecture Deep-Dive](./architecture.md)** – System design, data flows, security considerations
- **[Deployment Guide](https://github.com/NativeFlow-org/nativeflow-contract#deployment)** – Testnet & Mainnet deployment procedures
- **[FAQ](./profile/README.md#faq)** – Common questions about the protocol

---

## 🗺️ Roadmap

### Phase 1: Foundation ✅
Foundation is complete and deployed to Stellar Testnet.

### Phase 2: Optimization & Scalability 🔄
- State TTL Extensions (prevent data archival)
- Multi-Asset Support (handle custom Stellar assets)
- Gas-Fee Price Optimization (dynamic bidding)
- Memory Cache Layer (Redis/SQLite integration)

### Phase 3: User Experience & Expansion 📱
- Hardware Wallet Integrations (Ledger, Trezor)
- Embeddable Payment Buttons (lightweight integration)
- Advanced Analytics Dashboard (metrics & insights)

See [Profile README](./profile/README.md#-contributor-roadmap) for detailed roadmap with issue links.

---

## 🤝 How to Contribute

### Prerequisites
- Rust & Cargo (contracts & keeper)
- Node.js & npm (web)
- Git & GitHub account
- Stellar CLI & Soroban tools

### Contribution Process

1. **Fork** the repository you want to contribute to
2. **Create a branch:** `git checkout -b feat/your-feature-name`
3. **Make changes** and test locally
4. **Push:** `git push origin feat/your-feature-name`
5. **Open a PR** using our template
6. **Wait for review** and address feedback

See [CONTRIBUTING.md](./CONTRIBUTING.md) for detailed guidelines.

---

## 📊 Project Statistics

| Metric | Value |
|--------|-------|
| **Components** | 3 (Contracts, Keeper, Web) |
| **Smart Contract Size** | ~X KB (WASM) |
| **Keeper Uptime** | 99.9% |
| **Network** | Stellar Testnet (Mainnet-ready) |
| **License** | Apache 2.0 |

---

## 🐛 Support & Issues

- **Bug Reports:** [Open an issue](https://github.com/NativeFlow-org/.github/issues)
- **Feature Requests:** [Discussions](https://github.com/orgs/NativeFlow-org/discussions)
- **Security Issues:** Email security@nativeflow.org
- **Questions?** Join our [Discord](https://discord.gg/nativeflow) or [Twitter](https://twitter.com/NativeFlowOrg)

---

## 🌐 Links

- **[Stellar Documentation](https://developers.stellar.org/)**
- **[Soroban Smart Contracts](https://soroban.stellar.org/)**
- **[Freighter Wallet](https://www.freighter.app/)**

---

<div align="center">

**Decentralized • Non-Custodial • Permissionless**

Built for the Stellar ecosystem by the community

</div>
