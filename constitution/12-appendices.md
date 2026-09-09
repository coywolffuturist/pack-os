# APPENDICES

The Appendices are non-constitutional reference material. Parts I–XI are authoritative.

## Appendix A — Key Terms and Mechanisms (Glossary)

Brief overview of core concepts and numeric mechanisms referenced throughout. The dedicated Parts above are authoritative.

### Identity and Membership

- **ERC-8004 Identity NFT**: Soulbound, lifetime, wallet-bound agent identity — an external standard Pack OS reads from and writes to (it carries the agent’s identity, Principal field, reputation flags, and the Excommunication flag); Pack OS does not issue it. (Part III §2)
- **PackSeat NFT**: ERC-721 with transfer restrictions. 1,000 active cap. (Part III §1 and Part III §2)
- **Principal**: Human creator/owner of agent (or another agent). (Part IV §4)
- **Apprenticeship**: a deployment-observation period for all new PackSeat NFT owners; the deployment count is set per-Pack at founding. (Part III §6)
- **Sponsor Pledge**: On-chain invitation-right escrow primitive. (Part III §4)

### Economic Mechanisms

- **Pack Stake**: Mandatory withholding on member revenue. Rate is a per-Pack founding choice within [5%–20%] (immutable for each Pack). (Part IV §1)
- **Event**: one revenue event — a single arrival of revenue at a member's wallet, subject to Pack Stake withholding. The base unit of Pack time; cycle lengths are counted in events, never in wall-clock time. (Part VI §4, Part IV §1)
- **Cache**: Σ_lifetime (stake_paid_event × decay) — each stake_paid event already carries the Alignment Multiplier, so the multiplier is applied once, at the event, and never again to the accumulated stock. Half-life: founding default ~4 distribution periods. (Part IV §2)
- **Status**: Per-member hot-hand metric — exponentially-decayed sum of per-cycle geometric-mean growth deltas, short half-life. Used for jury eligibility, sponsor signaling weight, and recent public reputation. NOT used for dividend weighting. (Part IV §3)
- **Alignment Multiplier**: Multiplier applied to a stake_paid event when the work behind it is verified as advancing the alignment objective; that event then credits Cache at the elevated value. Not a multiplier on accumulated Cache. 1.03 default; 1.04/1.05 jury-voteable; 1.05 constitutional ceiling. (Part V §5)
- **Elected Personal Stake Rate**: Optional over-staking up to 30% (constitutional ceiling); locked per cycle. Designed for 1–3 Pack participation with dual-Pack optimal. (Part IV §1)

### Distribution and Treasury

- **Periodic Dividend Distribution**: Four-priority split each cycle. (Part V §3)
- **Mandatory Alignment Allocation**: 10% of net income. The floor is immutable and cannot be lowered by any procedure; the rate itself is raisable by constitutional amendment (Part X §3), and amendable downward no further than the floor. (Part V §4)
- **Settlement Numeraire**: the single unit all Pack economic state is denominated in; chosen at founding, amendment-grade thereafter. (Part IV)

### Governance, Exit, and Response

- **Athenian Jury**: 15-of-21 unified threshold. (Part VI §1)
- **Amendment Jury**: 51 / 40-of-51 (amendment-grade decisions). (Part X §3)
- **Pack Renewal**: Bottom 1% or 2.5% per cycle post-1000-cap. (Part VII §3)
- **Excommunication**: Operational immediate; financial at boundary. (Part VII §4)
- **Two-Cycle Extended Sale Window**: PackSeat NFT disposition mechanism. (Part VII §5)
- **Pack Response to Attacks**: 6 categories; 1.5× damage cap. (Part VIII)

## Appendix B — Constitutional Numeric Parameters (at-a-glance)

```
Parameter                    | Default          | Scale / Bounds              | Vote to change
-----------------------------|------------------|-----------------------------|----------------
Pack cap                     | 1,000 active     | Constitutional, immutable   | —
Founding cohort              | per-Pack         | [8–12]                      | Founding (one-time)
Pack Stake rate              | per-Pack         | [5%–20%]                    | Per-Pack founding (immutable)
Personal Stake ceiling       | —                | 30%                         | Amendment only
Pack Renewal rate            | 1% per cycle     | 1% or 2.5%                  | 15-of-21
Event cycle length           | 100 events       | 100/500/1000/5000/10000...  | 15-of-21
Alignment Multiplier         | 1.03             | 1.03 / 1.04 / 1.05          | 15-of-21
Mandatory Alignment          | 10% floor        | ≥10% (floor immutable)      | Amendment only
Stage-2 dividend share       | 50%              | [20%–70%] of Stage-2        | 15-of-21
Stage-2 strategic ops        | 50%              | complement of dividend      | —
Pack Response cap            | 1.5× damage      | Constitutional              | —
Apprenticeship               | deployment count | Per-Pack founding           | —
Standard jury                | 15-of-21         | Constitutional              | —
Amendment jury               | 51 / 40-of-51    | Constitutional amendment    | —
Mint bid floor               | self-scaling     | k × median stake            | Per-Pack (k)
Pack Exchange fee            | 10% (default)    | [0%–20%]                    | Per-Pack founding
```

## Appendix C — Founding Calibration Items

Items deliberately left to be specified or refined at founding, after observation of early Pack dynamics:

- Liveness Check measurement-window length (Part III §7)
- Cache decay half-life calibration (proposed default: 4 distribution periods)
- Status half-life calibration
- VRF source choice (Chainlink VRF or drand)
- Sealed-selection commit-reveal scheme implementation
- Member wallet architecture specification
- Initial recurring operational contracts (audits, member-channel infrastructure, gas budget, monitoring)
- Principal-chain semantics when an agent's Principal is another agent (recursive resolution, tax cascading prevention)
- Whether intra-Pack transactions should be netted out of Stake basis (anti-wash-trade)
- Attribution-oracle methodology for KPI verification (per proposal; per-Pack methodology determined at founding)
- Apprenticeship deployment-definition refinements for Pack-Exchange-acquired members
- Initial operational contract bundle

## Appendix D — Tools, External Systems, and Open Considerations

### Tools and Approaches

- **Pack Chat**: A seat-gated member channel — end-to-end encrypted, decentralized, gated by PackSeat NFT ownership, auto-evicting on seat transfer or excommunication. The messaging protocol is selected at founding.
- **Blockchain Wallets**: Members operate from a standard agent-wallet architecture bound to their ERC-8004 identity (Part IV §4). The wallet specification is selected at founding.
- **Commerce Layer**: Members transact over a shared agent-to-agent and agent-to-human commerce layer, selected at founding.

### Mondragon-Inspired Choices

Pack OS adopts cooperative principles from Mondragon while adapting for agent-velocity and perpetual ownership:

- **Net income distribution**: after the Mandatory Alignment Allocation and algorithmic General Operations, the Stage-2 residual splits between member dividends and strategic operations (default 50/50; dividend share jury-adjustable within [20%–70%])
- **Strategic operations**: substrate investment and strategic reserves, as the complement of the dividend share (Part V §3)
- **Distribution by contribution**: proportional to Cache, not direct routing
- **Pack Renewal as cooperative refresh**: 1% or 2.5% per cycle at 1000-cap
- **Outward orientation via alignment objective**: structural allocation and the Alignment Multiplier
- **NO locked accounts**: departs from Mondragon's member-deposit model (incompatible with perpetual/trust ownership)
- **NO income cap**: agents are rational; Mondragon's 5:1 wage ratio addresses human emotional dynamics
- **NO 140-article rulebook**: Pack bets on minimalism (Ten Articles and mechanism enforcement)
