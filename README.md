# MetaPay402: Crypto Payments for Meta Services and AI Agents

> Empower Meta services, APIs, and AI agents to process autonomous, on-chain payments using the HTTP 402 Payment Required standard powered by the Solana blockchain.
> 
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.3+-blue.svg)](https://www.typescriptlang.org/)
[![Node.js 18+](https://img.shields.io/badge/node-18+-green.svg)](https://nodejs.org/)

## About MetaPay402

MetaPay402 is a Meta-native framework built on the X402 protocol. It enables APIs, Meta services, and AI agents to complete autonomous crypto transactions using the HTTP 402 Payment Required standard, powered by Solana for secure and near-instant micropayments.

### Core capabilities 

- Seamless Integration Add MetaPay402 to any API or service with minimal setup 
- AI Optimized Designed for autonomous agents and Meta’s AI ecosystems
- Instant Settlement Transactions finalize in roughly 200 milliseconds on Solana
- Crypto Micropayments Enable payments as small as $0.001 per request
- No Credentials Needed Operates without API keys, subscriptions, or manual billing
- Blockchain Flexible Built on Solana with support planned for additional networks
- Framework Ready Compatible with FastAPI, Express, LangChain, LangGraph, and Meta APIs

## Supported Languages and SDKs

OpenLibx402 is available in both **Python** and **TypeScript/Node.js**, with full feature parity:

- 🐍 **Python**: FastAPI, LangChain, LangGraph
- 📦 **TypeScript**: Express.js, LangChain.js, LangGraph.js

Both implementations use **pnpm/uv monorepo** setup for easy development.

## Getting Started

### (Python with FastAPI)

```typescript
import express from "express";
import { paywall, initMetaPay, MetaPayConfig } from "@metapay402/express";

const app = express();

initMetaPay(new MetaPayConfig({
  walletAddress: "YOUR_WALLET_ADDRESS",
  tokenMint: "USDC_MINT_ADDRESS"
}));

app.get("/meta-ads",
  paywall({ price: "0.10" }),
  (req, res) => res.json({ data: "Ad insights and premium metrics" })
);
```

app.listen(3000, () => console.log("MetaPay402 Express server running on port 3000"));

### (TypeScript with Express.js)

```python
from fastapi import FastAPI
from metapay402_fastapi import paywall

app = FastAPI()

@app.get("/meta-insights")
@paywall(
    price="0.10",
    wallet="YOUR_WALLET_ADDRESS",
    token="USDC_MINT_ADDRESS"
)
async def get_meta_insights():
    return {"data": "Access granted to Meta insights"}

```

### Client (Python - Auto-Payment)

```python
from openlibx402_client import X402AutoClient
from solders.keypair import Keypair

client = X402AutoClient(wallet_keypair=keypair)

# Automatically handles 402 and pays
response = await client.fetch("https://api.example.com/premium-data")
data = response.json()
```

### Client (TypeScript - Auto-Payment)

```typescript
import { X402AutoClient } from '@openlibx402/client';
import { Keypair } from '@solana/web3.js';

const client = new X402AutoClient(keypair);

// Automatically handles 402 and pays
const response = await client.get('https://api.example.com/premium-data');
const data = response.data;
```
Project Layout

```
metapay402/
├── packages/
│   ├── python/                        # Python SDK (uv monorepo)
│   │   ├── metapay402-core/              # Core payment logic and blockchain layer
│   │   ├── metapay402-fastapi/           # FastAPI middleware for pay-per-access endpoints
│   │   ├── metapay402-client/            # Python client with built-in auto-payment
│   │   ├── metapay402-langchain/         # LangChain integration for AI agents
│   │   └── metapay402-langgraph/         # LangGraph workflow integration
│   │
│   └── typescript/                    # TypeScript SDK (pnpm monorepo)
│       ├── metapay402-core/              # Core payment engine (TypeScript)
│       ├── metapay402-express/           # Express.js middleware for API monetization
│       ├── metapay402-client/            # TypeScript client handling 402 and payments
│       ├── metapay402-langchain/         # LangChain.js integration
│       └── metapay402-langgraph/         # LangGraph.js integration
│
├── examples/
│   ├── fastapi-server/                # Example FastAPI server using MetaPay402
│   ├── express-server/                # Example Express.js server with payment endpoints
│   ├── langchain-agent/               # Demonstration of agent-based payments
│   └── langgraph-workflow/            # Example Meta AI workflow using LangGraph
│
├── pnpm-workspace.yaml                # TypeScript workspace configuration
├── pyproject.toml                     # Python workspace configuration
├── package.json                       # Root TypeScript package manifest
├── Makefile                           # Build and test automation
└── docs/
    ├── SETUP.md                       # Setup instructions
    └── metapay402-technical-spec.md   # Technical architecture and design overview
```

## Types

### FastAPI Server

```cd examples/fastapi-server
pip install -r requirements.txt
python app.py
```

## How MetaPay402 performs

```
### How MetaPay402 Works

╭──────────────────────────────╮
│        1. Client Request     │
│   Meta app or AI agent       │
│   requests a paid endpoint.  │
╰──────────────┬───────────────╯
               │
               ▼
╭──────────────────────────────╮
│    2. 402 Payment Trigger    │
│   The Meta API responds with │
│   a 402 Payment Required and │
│   payment instructions.      │
╰──────────────┬───────────────╯
               │
               ▼
╭──────────────────────────────╮
│     3. On-chain Payment      │
│   The client signs and sends │
│   the payment on Solana.     │
╰──────────────┬───────────────╯
               │
               ▼
╭──────────────────────────────╮
│    4. Verification Step      │
│   The API confirms payment   │
│   and validates transaction. │
╰──────────────┬───────────────╯
               │
               ▼
╭──────────────────────────────╮
│       5. Data Access         │
│   The endpoint unlocks and   │
│   returns the requested data │
│   in real time.              │
╰──────────────────────────────╯

Each payment loop completes in under 200ms, creating a **trustless, automatic billing cycle** for APIs, ads, and Meta services powered by **Solana micropayments**.

```
## Where MetaPay402 Fits In

MetaPay402 powers a new kind of economy inside Meta's ecosystem — where AI agents, tools, and APIs exchange value directly on-chain without human intervention.  
This system transforms how digital services operate, replacing credit cards and subscriptions with verified, instant crypto payments.

---

### 💼 Built for Developers
- Convert any endpoint into a revenue stream
- Let APIs self-monetize with per-call billing
- Remove manual invoicing and authentication systems
- Collect verified USDC instantly after each call

### 🤖 Built for Agents
- AI tools can pay for ads, analytics, or compute automatically
- Transactions execute in under 300ms via Solana
- No subscriptions, no stored credentials
- Agents pay only when they consume data or resources

### 🌍 Built for the Meta Ecosystem
- Connects with Meta Ads, Meta APIs, and future Meta services
- Enables blockchain-native automation inside Meta environments
- Works with Solana now, expanding to Base and Ethereum later

---

## System Maturity

**Stage: Active Development**

| Component | Status | Notes |
|------------|--------|-------|
| Core Payment Engine | ✅ Stable | Fully functional Solana transactions |
| SDK (Python / FastAPI) | ✅ Complete | Actively used in Meta developer sandboxes |
| SDK (TypeScript / Express) | ✅ Complete | Mirrors Python implementation |
| Meta AI Agent Toolkit | 🧠 In Progress | Enabling agents to initiate payments autonomously |
| Web Dashboard | 🔧 Planned | Manage services, keys, and invoices |
| Multi-Chain Support | 🧩 Planned | Integrations for Base and Ethereum networks |

