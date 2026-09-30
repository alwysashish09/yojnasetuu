# Yojana Setu

**AI-powered, blockchain-backed citizen services platform — helping Madhya Pradesh citizens find, apply for, and track government welfare schemes.**

Built for a Madhya Pradesh state-level hackathon. ("Yojana Setu" is a placeholder name — rename freely.)

## What This Is

Yojana Setu helps citizens discover the government schemes they're actually eligible for, apply without resubmitting the same documents over and over, interact entirely in Hindi by voice, and track their application and fund disbursement on a transparent, tamper-proof ledger.

## The Problem

- Citizens rarely know which of the thousands of schemes they qualify for.
- The same documents get resubmitted and re-verified for every application.
- Fake identities and duplicate claims drain welfare budgets.
- Once submitted, applications vanish into a black box — no status visibility.
- Text-heavy portals exclude citizens who are more comfortable speaking than filling out a form.
- There's no traceable, tamper-proof record of fund flow, so delays or leakage go unnoticed.

## Key Features

1. **AI Scheme Recommendation Engine** — matches a citizen's profile against eligibility rules and returns a ranked list of schemes with plain-language explanations.
2. **DigiLocker One-Time Verification** — documents are fetched and signature-verified once, never re-uploaded.
3. **Blockchain-Backed Fund Transparency** — every application stage is logged immutably on Polygon; real money still moves through PFMS/DBT, the blockchain is the audit layer.
4. **Fraud & Duplicate-Identity Prevention** — Aadhaar e-KYC, on-chain identity-hash deduplication, and AI anomaly detection on suspicious bank-account patterns.
5. **Hindi Voice Assistant** — speak a request in Hindi, get it understood and answered back in Hindi, via Bhashini/AI4Bharat.
6. **Real-Time Status Tracking & Grievance Escalation** — citizens see live application status; stuck applications auto-escalate to a human officer.

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React (Vite) |
| Backend | Node.js + Express |
| Database | PostgreSQL (via Prisma) |
| Blockchain | Solidity smart contracts on Polygon Amoy testnet (via Hardhat) |
| Voice | Bhashini or AI4Bharat (Hindi ASR/TTS) |
| Identity | Aadhaar e-KYC (mocked for hackathon), DigiLocker (mocked or sandbox) |

> Note: Amoy is the current Polygon PoS testnet — the older Mumbai testnet was deprecated in 2024.

## Project Structure

```
yojana-setu/
├── frontend/          # React app — citizen + officer UI, voice widget
├── backend/           # Node.js + Express API, Prisma models
├── contracts/         # Solidity smart contracts (Hardhat, Polygon Amoy)
├── data/              # Curated MP scheme dataset (from data.gov.in)
├── docs/              # PRD, build-phase prompts, this README
└── README.md
```

## How It Works

A citizen's profile is matched against scheme eligibility rules, verified identity documents are reused instead of re-collected, and every stage of their application — submitted, verified, approved, disbursed — is written to a smart contract on Polygon so the trail is public and unchangeable. The actual payment still runs through India's existing PFMS/DBT bank rails; the blockchain hash and the bank's transaction reference are linked together, so the blockchain proves the process wasn't tampered with without needing to move currency on-chain.

## Getting Started

This section fills in as the build progresses — see the build plan below, starting with Phase 1.

**Prerequisites**
- Node.js 18+
- PostgreSQL
- A MetaMask wallet funded with Polygon Amoy testnet POL (free from the official Polygon faucet)
- API access: Bhashini or AI4Bharat; DigiLocker sandbox (if using real integration instead of the mock)

**Environment variables** (`backend/.env`)
```
DATABASE_URL=
POLYGON_AMOY_RPC_URL=
WALLET_PRIVATE_KEY=
BHASHINI_API_KEY=
DIGILOCKER_CLIENT_ID=
```

**Run locally** *(update once Phase 1 scaffolding is complete)*
```
cd backend && npm install && npm run dev
cd frontend && npm install && npm run dev
```

## Build Plan

The full build is broken into 24 phases, from project scaffolding through demo rehearsal — see `Yojana_Setu_Build_Prompts_24_Phases.md` for copy-paste-ready prompts for each phase:

1–5: Data & recommendation engine · 6–10: Citizen onboarding, KYC, documents, applications · 11–17: Blockchain, fraud detection, officer dashboard, disbursement · 18–19: Status tracking & grievances · 20–22: Hindi voice assistant · 23–24: Integration, polish, demo readiness.

## Hackathon Demo Notes

**Built for real:** the Polygon Amoy smart contract and live transactions, the AI recommendation engine on real MP scheme data, and the Hindi voice demo.
**Mocked for time:** DigiLocker (realistic dummy-document flow) and the PFMS/bank transfer (simulated, but still linked to a real on-chain hash). Judges evaluate whether the concept and flow hold together, not production-grade integrations.

## Data & API Sources

- [data.gov.in](https://data.gov.in) — MP government scheme datasets
- DigiLocker — identity and document verification
- Bhashini / AI4Bharat — Hindi speech-to-text and text-to-speech
- Polygon Amoy — public testnet for the transparency ledger

## Roadmap (Post-Hackathon)

- IVR/USSD access for citizens without smartphones
- Expand beyond Hindi to other regional languages
- Full production DigiLocker and Bhashini partner integration
- Evaluate Hyperledger Fabric for real government deployment
- Extend beyond MP to central government schemes

## Team

_Add your team members here._

## Documents in This Repo

| File | Purpose |
|---|---|
| `README.md` | This file — plan and overview |
| `Yojana_Setu_PRD.md` | Full product requirements document |
| `Yojana_Setu_Build_Prompts_24_Phases.md` | Copy-paste prompts for building with Google Antigravity |
