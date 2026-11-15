# Requirements Summary

This is a condensed version of the full Software Requirements Specification (IEEE 830 style).

## Users

| User | Role |
|---|---|
| Owner | Creates and manages the will, holds the assets |
| Beneficiary | Receives assets after execution |
| Guardian | Confirms death or incapacity |
| Legal executor (optional) | Read-only view of the execution log |

## Functional Requirements

**Wallet and vault**
- FR-1: Connect an Ethereum wallet and authenticate by signed message
- FR-2: Deploy or link a Safe vault with the inheritance module

**Will management**
- FR-3: List assets (native, ERC-20, ERC-721, ERC-1155) in the vault
- FR-4: Assign beneficiaries by address with share or asset allocation
- FR-5: Configure check-in period, grace period, challenge window, guardian threshold
- FR-6: Store only a Merkle root of allocations on-chain
- FR-7: Edit or revoke the will before execution, each change owner-signed
- FR-8: Owner signs the final configuration to activate

**Heartbeat and alerts**
- FR-9: Single-signature check-in
- FR-10: Alerts on at least two channels before state advances
- FR-11: Check-in period configurable, down to one minute for demos

**Guardians, time-lock and claim**
- FR-12 to FR-14: Manage guardians; attestations only in Verification state; threshold enforced
- FR-15 to FR-17: Enforced challenge window, owner cancellation, events for every transition
- FR-18 to FR-20: Merkle-proof claims, no double claims, fallback beneficiary

**Legacy vault and executor**
- FR-21 to FR-24: Encrypted instructions released via guardian key shares; optional executor view; exportable event record

## Non-Functional Requirements

- **Security:** no custody of user funds; audited libraries; static analysis; external audit before mainnet
- **Privacy:** no identities or asset lists in plain text on-chain; client-side AES-256 encryption
- **Reliability:** core logic fully on-chain; frontend deployable as static content
- **Performance:** check-in confirms in under 30 seconds on testnet
- **Usability:** setup in under 10 minutes; WCAG 2.1 AA where feasible
- **Compatibility:** ERC-20, ERC-721, ERC-1155 and native ETH

## Acceptance Criteria

1. Owner can create, assign and sign a will on Sepolia
2. A missed check-in moves the will to Warning and sends alerts
3. Guardian threshold confirmation starts the time-lock
4. Owner check-in or cancellation during the window returns the will to Active
5. After the window, a valid Merkle proof releases the correct assets; invalid proofs and repeat claims fail
6. No beneficiary identity or asset detail is readable from on-chain data
