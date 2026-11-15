# Digital Will System

A blockchain-based inheritance layer that lets crypto holders pass digital assets to chosen beneficiaries after verified death or prolonged inactivity.

> **Project status: planning and documentation only.** This repository currently contains specifications and design documents. No application code has been written yet.

Built for **The Corporate Glitch '26**, a national level hackathon by Builders Hub.

## The Problem

Digital assets are secure, but that same security makes them inaccessible when the owner dies. A traditional will can name heirs, yet it cannot unlock a self-custody wallet or force a blockchain transfer, so tokens and NFTs are often lost permanently. Workarounds such as sharing seed phrases are risky and unreliable.

## The Proposed Solution

A non-custodial, smart-contract-based "digital will" that works alongside a legal will:

1. The owner keeps assets in their own **Safe smart-account vault** with an inheritance module.
2. The owner defines beneficiaries and execution terms. Only a **Merkle root** of allocations is stored on-chain, so identities stay private.
3. A **heartbeat** (periodic check-in) shows the owner is active. Missed check-ins trigger multi-channel alerts.
4. **Guardians** (for example 2-of-3 trusted people) confirm death or incapacity.
5. A **30 to 90 day time-lock** gives a living owner the chance to cancel with one signature.
6. After the window, beneficiaries **claim assets with a Merkle proof**.

## Key Features (Planned)

- Non-custodial vault: assets never leave the owner's control while alive
- Layered death verification: heartbeat, guardians, time-locked challenge window
- Private beneficiary claims via Merkle proofs
- Editable and revocable at any time before execution
- Support for native tokens, ERC-20, ERC-721 and ERC-1155
- Encrypted legacy vault for non-on-chain instructions (exchange accounts, seed-phrase locations)
- Optional legal executor view

## Planned Tech Stack

| Layer | Technology |
|---|---|
| Smart contracts | Solidity, Hardhat, OpenZeppelin, Safe modules |
| Frontend | React, wagmi / ethers.js |
| Network | Ethereum Sepolia testnet (L2 support later) |
| Privacy | IPFS, AES encryption, Shamir secret sharing |
| Backend (optional) | Python (Flask) for email/SMS reminders |
| Security tooling | Hardhat tests, Slither |

## Documentation

| Document | Description |
|---|---|
| [docs/REQUIREMENTS.md](docs/REQUIREMENTS.md) | Software requirements summary (functional and non-functional) |
| [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) | System components, state machine and data flow |
| [docs/THREAT_MODEL.md](docs/THREAT_MODEL.md) | Risks and mitigations |
| [docs/ROADMAP.md](docs/ROADMAP.md) | Hackathon MVP scope and production roadmap |
| [docs/LEGAL.md](docs/LEGAL.md) | Legal and compliance notes |
| [CONTRIBUTING.md](CONTRIBUTING.md) | How to contribute |
| [SECURITY.md](SECURITY.md) | Security policy |

## Expected Impact

- **Owners:** pass on assets without sharing seed phrases
- **Families:** a clear, secure path to claim inherited assets
- **Ecosystem:** less crypto lost permanently over time
- **Trust:** auditable rules replace informal workarounds

## Team

**Team JLO and Puck Bunny**

| Member | College |
|---|---|
| Gaurangi Agrawal | GLA University / Sharda University |
| Kanak Rawat | GLA University / Sharda University |

## Disclaimer

This project is not legal, financial or tax advice. A smart contract is not a legally recognized will in most jurisdictions. It is designed to complement, not replace, a legal will. See [docs/LEGAL.md](docs/LEGAL.md).

## License

Released under the [MIT License](LICENSE).
