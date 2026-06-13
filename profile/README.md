# 🌊 NativeFlow - Decentralized Recurring Payments Protocol

![NativeFlow Badge](https://img.shields.io/badge/Built%20on-Stellar%20Soroban-4B7BF5?style=flat-square)
![Status Badge](https://img.shields.io/badge/Status-Production%20Ready-green?style=flat-square)

NativeFlow is a **completely decentralized, non-custodial recurring payments and subscription protocol** built on the Stellar blockchain using Soroban smart contracts. It enables merchants to accept automated, permission-based recurring payments without intermediaries—all while respecting user privacy and maintaining self-sovereignty.

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

## 🎯 Core Features

| Feature | Layer | Status |
|---------|-------|--------|
| **Non-Custodial** | All | ✅ Deployed |
| **Permission-Based** | Contracts | ✅ Deployed |
| **Automated Execution** | Keeper | ✅ Deployed |
| **Dashboard UI** | Web | ✅ Deployed |
| **State TTL Management** | Contracts | 📋 Planned |
| **Multi-Asset Support** | Contracts | 📋 Planned |
| **Dynamic Gas Optimization** | Keeper | 📋 Planned |
| **Caching Layer** | Keeper | 📋 Planned |
| **Hardware Wallet Support** | Web | 📋 Planned |
| **Embeddable Payment Buttons** | Web | 📋 Planned |

---

## 📦 Repository Structure

Each component is a **fully independent, decoupled repository**:

### 1. **[`nativeflow-contracts`](https://github.com/NativeFlow-org/nativeflow-contracts)** 🔐
The on-chain smart contract engine.

**Key Responsibilities:**
- Store and manage subscription data in persistent memory
- Validate subscription intervals and constraints
- Execute token transfers via Soroban Token Standard (CPI)
- Enforce authorization rules and permissions
- Manage state expiration (TTL)

**Tech Stack:** Rust + Soroban SDK, WASM

**Tests & Validation:** `cargo test`

---

### 2. **[`nativeflow-keeper`](https://github.com/NativeFlow-org/nativeflow-keeper)** 🚀
The off-chain automation daemon.

**Key Responsibilities:**
- Continuously scan ledger state via Soroban RPC
- Detect subscriptions whose intervals have matured
- Trigger execution transactions automatically
- Collect processing bounties
- Monitor network congestion and adapt strategies

**Tech Stack:** Rust / Node.js (TBD), async runtime

**Tests & Validation:** Unit tests + integration tests against testnet

---

### 3. **[`nativeflow-web`](https://github.com/NativeFlow-org/nativeflow-web)** 💻
The front-end merchant dashboard and integration SDK.

**Key Responsibilities:**
- Freighter Wallet integration (signing, approvals)
- Multi-step token approval flows
- Merchant dashboard for subscription lifecycle management
- Web SDK for third-party integrations
- Web3 utilities and contract interaction

**Tech Stack:** React, TypeScript, Freighter SDK, TailwindCSS

**Tests & Validation:** `npm run build && npm test`

---

## 🚀 Current Live Deployments

| Component | Network | Status |
|-----------|---------|--------|
| Smart Contract | Stellar Testnet | ✅ [Deployed](#) |
| Dashboard | Vercel/Netlify | ✅ [Live](#) |
| Keeper Daemon | Server/Cloud | ✅ Running |

**Smart Contract ID:** `[PASTE_YOUR_DEPLOYED_CONTRACT_ID_HERE]`  
**Live Dashboard URL:** `[PASTE_YOUR_WEB_DEPLOYMENT_URL_IF_APPLICABLE]`  
**Testnet Network:** `https://soroban-testnet.stellar.org`

---

## 🗺️ Contributor Roadmap

### Phase 1: Foundation ✅
- [x] Smart contract implementation
- [x] Keeper daemon MVP
- [x] Web dashboard & SDK
- [x] Testnet deployment

### Phase 2: Optimization & Scalability 🔄
- [ ] **State TTL Extensions** (`nativeflow-contracts`)  
  Implement automated storage rent bumps using Soroban's state expiration ledger thresholds to prevent subscription data from becoming archived.

- [ ] **Multi-Asset Support** (`nativeflow-contracts`)  
  Expand validation logic to handle complex custom Stellar asset structures beyond standard Testnet USDC.

- [ ] **Gas-Fee Price Optimization** (`nativeflow-keeper`)  
  Add dynamic fee bidding logic to ensure execution transactions succeed during periods of high Stellar network congestion.

- [ ] **Memory Cache Layer** (`nativeflow-keeper`)  
  Implement a local database/caching layer (e.g., Redis or SQLite) so the daemon doesn't have to scan the entire RPC history on every loop.

### Phase 3: User Experience & Expansion 📱
- [ ] **Hardware Wallet Integrations** (`nativeflow-web`)  
  Expand the client-side SDK layer to support Ledger and Trezor hardware wallets via Stellar's ecosystem protocols.

- [ ] **Embeddable Payment Buttons** (`nativeflow-web`)  
  Build a lightweight, copy-pasteable React/HTML checkout button snippet for merchants to integrate into external websites.

- [ ] **Advanced Analytics** (`nativeflow-web`)  
  Dashboard metrics for subscription success rates, failure analysis, and revenue tracking.

---

## 🤝 How to Contribute

### Prerequisites
- **Rust & Cargo** (for contracts & keeper)
- **Node.js & npm** (for web)
- **Git** & GitHub account
- **Stellar CLI** & Soroban tools

### Getting Started

1. **Choose an Issue**
   - Browse the [open issues](../../issues) or roadmap items above
   - Comment on the issue to claim it

2. **Fork & Branch**
   ```bash
   git clone https://github.com/YOUR_USERNAME/nativeflow-[component].git
   cd nativeflow-[component]
   git checkout -b feat/your-feature-name
   ```

3. **Develop & Test**
   ```bash
   # For Contracts (Rust)
   cargo test
   cargo build --target wasm32-unknown-unknown
   
   # For Keeper (Rust/Node.js)
   cargo test  # or npm test
   
   # For Web
   npm install
   npm run build
   npm test
   ```

4. **Commit & Push**
   ```bash
   git add .
   git commit -m "feat: add your feature description"
   git push origin feat/your-feature-name
   ```

5. **Submit a Pull Request**
   - Create PR against the main branch
   - Use our [PR template](#) for consistency
   - Ensure CI/CD checks pass
   - Request review from maintainers

### Code Style & Standards
- **Rust:** Follow `rustfmt` & `clippy` standards
- **TypeScript/JavaScript:** Follow ESLint & Prettier config
- **Commits:** Conventional Commits format (`feat:`, `fix:`, `docs:`, etc.)
- **Tests:** Aim for >80% coverage on new code

---

## 📚 Documentation

- **[Architecture Deep-Dive](./architecture.md)** – Detailed system design
- **[Smart Contract API](https://github.com/NativeFlow-org/nativeflow-contracts/blob/main/docs/API.md)**
- **[Keeper Configuration Guide](https://github.com/NativeFlow-org/nativeflow-keeper/blob/main/README.md)**
- **[Web SDK Integration Guide](https://github.com/NativeFlow-org/nativeflow-web/blob/main/SDK.md)**

---

## 🛠️ Development & Deployment

### Local Development
```bash
# Start the keeper daemon locally
./nativeflow-keeper --testnet

# Run the web dashboard
npm start

# Deploy to staging
npm run deploy:staging
```

### Testnet Deployment
All three components are currently deployed on **Stellar Testnet**. Contracts are registered and active. Keeper daemon is running continuously.

### Mainnet Readiness
The protocol is **production-ready** and can be deployed to Stellar Mainnet upon community consensus.

---

## 📊 Statistics

- **Smart Contract Size:** ~X KB (WASM)
- **Keeper RPC Calls/Minute:** ~X (configurable)
- **Avg Execution Latency:** ~X seconds
- **Network Gas Costs:** ~X stroops per transaction
- **Uptime SLA:** 99.9% (target)

---

## ❓ FAQ

**Q: Is NativeFlow custodial?**  
A: No. Users retain full custody of their private keys. The protocol is completely non-custodial.

**Q: What blockchains does it support?**  
A: Currently Stellar (via Soroban). Other blockchain integrations can be built by the community.

**Q: Can merchants set custom intervals?**  
A: Yes. Subscriptions support flexible time intervals (daily, weekly, monthly, custom seconds).

**Q: What assets can be used for payments?**  
A: Any Stellar asset (native XLM, issued assets, wrapped bridged assets). Multi-asset constraints are part of Phase 2.

**Q: How much does it cost to use?**  
A: Only Stellar network fees (stroops). No platform fees or middlemen.

**Q: How do I deploy the keeper daemon?**  
A: See the [Keeper Deployment Guide](https://github.com/NativeFlow-org/nativeflow-keeper/blob/main/DEPLOY.md).

---

## 🐛 Reporting Issues

Found a bug or have a feature request?
- **Security Issues:** Email security@nativeflow.org (do not open public issues)
- **Bugs & Features:** [Open an issue](../../issues) with detailed description

---

## 📄 License

All NativeFlow repositories are licensed under the **Apache 2.0 License**. See individual repos for full license text.

---

## 🌐 Community & Links

- **Discord:** [Join our community](#)
- **Twitter:** [@NativeFlowOrg](#)
- **GitHub:** [github.com/NativeFlow-org](#)
- **Stellar Docs:** https://developers.stellar.org/
- **Soroban Docs:** https://soroban.stellar.org/

---

## 🙌 Special Thanks

Thanks to the **Stellar Foundation** for Soroban and continued support of the ecosystem. Big thanks to all contributors making this protocol stronger!

---

<div align="center">

**Built with ❤️ for the Stellar ecosystem**

[Star us on GitHub](../../) • [Follow us on Twitter](#) • [Join Discord](#)

</div>