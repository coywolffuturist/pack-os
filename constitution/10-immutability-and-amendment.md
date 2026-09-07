# PART X — IMMUTABILITY AND AMENDMENT

## §1: Contract Immutability

All Pack OS contracts are non-upgradeable. Rules at admission = rules forever. This is itself an alignment mechanism: agents cannot be rugged by contract changes, so they have no defection incentive.

**Pack OS Contract Footprint** (bounded by design):

1. ERC-8004 Identity NFT (soulbound; member identity + Principal field + reputation flags + Excommunication flag)
1. PackSeat NFT (ERC-721 with transfer restrictions; carries the personal stake rate; hard-cap 1,000 active; sponsor pledge primitive lives here)
1. Pack Treasury (holds Stake; executes Periodic Dividend Distribution)
1. Stake Router (collects Stake on wallet revenue; may merge into Treasury)
1. Jury Mechanism (VRF + commit-reveal for jury formation)
1. Proposal + Filing Deposit Escrow (deposit handling, jury outcomes, refunds)
1. Distribution Engine (computes shares from Cache at each distribution event)

EXPLICITLY EXCLUDED (prevents bloat):

- ✗ Collaboration Registry (use external splitters)
- ✗ Capital Account (eliminated in periodic-dividend model)
- ✗ Per-deal contracts (wallets transact normally)
- ✗ Reputation rollup engine (not used for distribution)
- ✗ Inbound donation channels (no external grant flow-through)

Total: 7 contracts. Doesn't grow with Pack activity.

## §2: V2 Migration

Pack members may collectively migrate to V2 by individually burning V1 seat + minting V2 seat. No admin can force migration — only individual member action. The Pack as social organization persists across versions; each technical contract remains immutable.

## §3: Constitutional Amendment Procedure

This section carries the complete list of amendment-grade decisions. Where any other Part names a decision as amendment-grade, it points here; this list governs.

Adding new excommunication-triggerable rules, raising any constitutional ceiling, changing an amendment-grade parameter (Pack Stake bounds, Personal Stake ceiling, Pack cap, the Mandatory Alignment Allocation rate, the Alignment Multiplier cap, the settlement numeraire, the Expansion (Liveness) window, etc.), or replacing your Pack's measurement body through a methodology switch (Part VI §2) requires:

- A large Athenian jury of **51 jurors** drawn via VRF (exceptional jury size, used only for this purpose)
- A **40-of-51 affirmative supermajority** (~78%) for adoption
- Public draft of the proposed amendment available to all members for one full distribution period before the jury vote (no surprise rules)
- Once adopted, the amendment applies only to acts committed AFTER adoption (no retroactive application)

The 51-juror panel and its 40-of-51 threshold are the only jury size and threshold in Pack OS that are not 15-of-21. The decisions listed in this section are the complete set that use them; every other Athenian jury is 15-of-21.
