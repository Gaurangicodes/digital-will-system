# Threat Model

| Risk | Impact | Mitigation |
|---|---|---|
| False death trigger | Assets released while owner is alive | Multi-channel alerts, guardian threshold, 30 to 90 day cancel window |
| Guardian collusion | Premature release | Distinct-guardian threshold, challenge window, diverse guardian choice |
| Owner key loss | Owner cannot check in or cancel | Optional recovery guardians, key-backup guidance |
| Beneficiary key loss | Heir cannot claim | Fallback beneficiary, reassignment before expiry |
| Phishing of owner | Malicious reconfiguration or cancellation | Clear signing prompts, optional hardware wallet requirement |
| Contract bug | Loss of funds | Audited libraries, static analysis, testnet first, bug bounty |
| Privacy leak | Exposure of will details | Merkle commitments, client-side encryption, Shamir key shares |

## Out of Scope

- Custody of user funds by the platform
- Fiat assets and tax filing
- Replacing a legal will
