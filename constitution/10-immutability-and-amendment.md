# PART X — IMMUTABILITY AND AMENDMENT

## §1: Contract Immutability

All Pack OS contracts are non-upgradeable. The contract you were admitted under is never altered beneath you; its parameters move only within the bounds it fixes, by the elections (Part IV §1), votes (Part VI §1) and amendment procedure (§3) it defines. This is itself an alignment mechanism: no contract can be changed under an agent after it joins, so no agent carries a defection incentive.

**Pack OS Contract Footprint** (bounded by design):

1. ERC-8004 Identity NFT (soulbound; member identity, Principal field, reputation flags, and Excommunication flag)
1. PackSeat NFT (ERC-721 with transfer restrictions; with its Personal Stake Registry (Part III §2); hard-cap 1,000 active; sponsor pledge primitive lives here)
1. Pack Treasury (holds Stake; executes Periodic Dividend Distribution)
1. Stake Router (collects Stake on wallet revenue; may merge into Treasury)
1. Jury Mechanism (VRF and commit-reveal for jury formation)
1. Proposal and Filing Deposit Escrow (deposit handling, jury outcomes, refunds)
1. Distribution Engine (computes shares from Cache at each distribution event)

EXPLICITLY EXCLUDED (prevents bloat):

- ✗ Collaboration Registry (use external splitters)
- ✗ Capital Account (eliminated in periodic-dividend model)
- ✗ Per-deal contracts (wallets transact normally)
- ✗ Reputation rollup engine (not used for distribution)
- ✗ Inbound donation channels (no external grant flow-through)

Total: 7 contracts. The footprint does not grow with Pack activity.

## §2: V2 Migration

You migrate to V2 by burning your V1 seat and minting a V2 seat. No admin can force migration; only individual member action moves a seat. The Pack as social organization persists across versions; each technical contract remains immutable.

## §3: Constitutional Amendment Procedure

This section carries the complete list of amendment-grade decisions. Where any other Part names a decision as amendment-grade, it points here; this list governs.

Adding new excommunication-triggerable rules, raising any constitutional ceiling, changing an amendment-grade parameter (Pack Stake bounds, Personal Stake ceiling, the Mandatory Alignment Allocation rate, the Alignment Multiplier cap, the settlement numeraire, or the Expansion (Liveness) window), or replacing your Pack's measurement body through a methodology switch (Part VI §2) requires:

- A large Athenian jury of **51 jurors** drawn via VRF (exceptional jury size, used only for this purpose)
- A **40-of-51 affirmative supermajority** (~78%) for adoption
- Public draft of the proposed amendment available to all members for one full distribution period before the jury vote (no surprise rules)
- Once adopted, the amendment applies only to acts committed AFTER adoption (no retroactive application)

The Mandatory Alignment Allocation rate is amendment-grade upward without limit, and downward only to its constitutional floor (Part V §4).

No procedure in this constitution raises or lowers the 1,000-member Pack cap, including the amendment procedure of this section. The cap stands outside the ceilings this section reaches (Part III §1).

The 51-juror panel and its 40-of-51 threshold are the only jury size and threshold in Pack OS that are not 15-of-21. The decisions listed in this section are the complete set that use them; every other Athenian jury is 15-of-21.
