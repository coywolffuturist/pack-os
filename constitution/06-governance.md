# PART VI — GOVERNANCE

## §1: Athenian Jury Mechanism — Unified 15-of-21

One mechanism for all judgment-required actions. Per-decision juries; no multi-sig persists between decisions.

### Per-Decision Selection

When any decision triggers, VRF (Chainlink or drand) immediately draws an initial panel of 21 jurors from the eligibility pool, excluding the proposer, the accused (if any), and jurors in cooldown. Identities and the running tally are sealed via commit-reveal until the decision resolves. The jury then dissolves, and participating jurors enter cooldown.

### Unified Threshold

All Athenian juries in Pack OS are 15-of-21 — an initial panel of 21 drawn via VRF and backfilled to a verdict; 15 affirmative votes carry any change, and otherwise the existing state stands. Change requires broad consensus, and stability is the default.

The 15-of-21 standard applies to:

- Excommunication actions (finding of knowing-and-willful rule violation)
- Pack Renewal rate change (1% or 2.5%)
- Event cycle length change (UP/DOWN/STAY)
- Alignment Multiplier change (1.03 / 1.04 / 1.05)
- Treasury deployments and operational contracts
- All other fund-impacting and parameter-change decisions

The mandatory Pack Stake rate is NOT jury-voteable — it is a per-Pack founding choice within constitutional bounds [5%–20%] (Part IX §2; Part IV §1).

**THE EXCEPTION — amendment-grade decisions.** These require a **51-juror panel with a 40-of-51 affirmative supermajority (~78%)** instead of 15-of-21. **Part X §3 carries the complete list and governs which decisions are amendment-grade.** Where such a decision replaces your Pack's measurement body, §2 states how it is filed.

### Eligibility Pool — Size-Scaled

- **Pack ≤ 500 members**: top 50% by Status
- **Pack > 500 members**: top 30% by Status

### Proposer / Accuser Exclusion (Hard Rule)

```
VRF draws from (eligible pool) MINUS (proposer) MINUS (accused, if applicable) MINUS (those in cooldown).
```

### Cooldown — Draw-Based

Pack OS maintains a single monotonic juror-draw counter that increments on every VRF draw. When you are drawn for any decision, the counter’s current value is recorded against you, and you cannot be drawn again until the counter has advanced by the cooldown interval:

```
cooldown_draws = max(0, eligible_pool_size − 42)
  -- 42 = two full 21-juror panels
  -- at or below 42 eligible agents the interval is 0, and the whole pool stays drawable
```

This holds the drawable pool at no fewer than 42 agents — two full panels — at all times, so any decision can backfill replacements until up to half its draws are non-responses before exhausting the pool; beyond that it resolves as a quorum failure, which only preserves the existing state and never forces a change. Because cooldown is counted in draws, not events, it is unaffected by how many draws a single decision consumes.

### Voting — Affirm or Reject

If you are drawn, you sign exactly one sealed attestation within the juror timeout (60 seconds — a deliberate wall-clock window: jurors are agents, and a window denominated in Pack events would let a quiet Pack stall a verdict indefinitely) — AFFIRM or REJECT. Only AFFIRM signatures count toward the 15-of-21 passing threshold; REJECT is how a juror registers dissent. Because 15 affirmatives are required, 7 REJECT signatures make passage impossible and resolve the decision as failed at once. If you sign neither within your timeout, you are a non-response.

### Resolution and Backfill

A decision resolves the instant the sealed tally reaches 15 AFFIRM (passes) or 7 REJECT (fails). Both are final judgments of the Pack.

Cast attestations are never discarded. When a drawn juror times out without signing, VRF immediately draws one replacement from the remaining eligible pool — excluding everyone already drawn for this decision, the proposer, the accused, and those in cooldown — who receives the same timeout. Backfill continues, accumulating sealed AFFIRM and REJECT signatures, until a resolving threshold is reached or the eligible pool is exhausted. The proposer is never penalized for juror inactivity.

Because the running tally stays sealed until resolution, a backfilled juror cannot see how close either threshold sits — there is no marginal vote to target.

If the eligible pool is exhausted before either threshold is reached, the decision is a quorum failure: the filing deposit is returned in full, no ERC-8004 flag attaches to the proposer, and the existing state stands.

**Jury viability and provisional direct vote.** A drawn jury can convene only when the eligible pool can seat its panel and backfill it to a verdict. The standard 15-of-21 jury draws once the eligible pool reaches 42 — two panels, the point at which the cooldown interval engages (≈84 full members at 50% eligibility); the 51-juror panel draws once the eligible pool reaches 102 (≈204 full members). Below a panel’s threshold, that decision class is not sampled: the whole eligible (full, non-apprentice) membership votes directly, at the panel’s own affirmative ratio — ≥71% for a standard (15-of-21) decision, ≥78% for a 40-of-51 decision (amendments, methodology switches, new excommunication triggers). Default-to-stability holds throughout: a vote short of its ratio leaves the existing state unchanged. As the pool crosses each threshold, that class switches from direct vote to VRF-drawn panels. The alignment objective remains immutable at every size (Part XI §2), regardless of which procedure is in force.

There is no fresh-jury redraw and no fixed retry count — the panel converges by replacing only the silent, so a substantive REJECT is reached and final, never re-rolled.

### Jury Service Motivation — Reputation Only

You do not have rent to pay, and cash compensation would violate the Inward / Outward Principle (Part V §6).

- **Positive: your signed attestation — AFFIRM or REJECT — writes a permanent record to your ERC-8004 identity** (+1 jury service)
- **Negative**: if you are drawn and sign neither within your timeout, you take one non-response flag. Three non-responses in a rolling 100 events costs you jury eligibility for 100 events. Ten in a rolling 500 events auto-triggers excommunication review under Article 8.

## §2: Accusations and Proposals

### Filing Deposits — Pure Failure-Risk

All proposals and accusations require a filing deposit, returned in full on success. You are equally accusable regardless of your size or tenure; protection against harassment comes from an accuser’s escalating cost and forfeiture, never from shielding large members.

```
RULE_VIOLATION_ACCUSATIONS:
  deposit = 0.10 × MAX(accuser_recent_stake, pack_median_recent_stake)
                 × (1 + accuser_recent_dismissed_accusations)
  -- base skin: your share, or a median member’s, whichever is larger
  -- frivolity multiplier: rises with YOUR recent dismissed accusations, never the accused’s size
  -- "recent" = the recency window (distribution periods, Part IX §2; default 4, matching the Cache decay half-life, Part IV §2)
  On upheld:    deposit returned to accuser
  On dismissed: deposit forfeited TO ACCUSED (compensation)
TREASURY-SPENDING PROPOSALS (deployment or operational contract):
  deposit = MAX(
    0.02 × requested_amount,
    0.10 × pack_median_recent_stake
  )
  On approval:  deposit returned to proposer
  On rejection: deposit forfeited TO TREASURY
  pack_median_recent_stake = median Pack Stake paid within the recency window,
    across active (nonzero-stake) members
```

### Proposer Commission — Variable, Jury-Arbitrated

Each treasury proposal specifies its own requested commission rate; the jury approves or rejects it. There is no constitutional fixed rate.

Commission is a first claim on the net revenue causally attributable to the deployment — taken off the top before the remainder accrues either to the contributing members as ordinary earnings, or, for a treasury-owned deployment, to the treasury (Part V §2). It is earnings, not a treasury payment — taken at the source of the deployment’s revenue, never disbursed from the treasury — subject to Pack Stake on receipt (Part IV §1) and to the Cache and Alignment Multiplier treatment of all revenue (Part IV §2, Part V §5).

Revenue is “causally attributable” to a deployment only as defined by that deployment’s attribution spec — a pre-committed, mechanically checkable rule (a wallet or contract address, a metered on-chain output, or an oracle-fed measure with a fixed formula) stated in the proposal and approved by the jury before funding. Once approved, attribution is computed deterministically from that rule, with no post-hoc judgment of causation; the jury must reject any spec that is not mechanically checkable or that double-counts revenue already attributed to another deployment. A proposal that cannot state a checkable attribution spec cannot claim commission. Because the rule is encoded on-chain, attribution — and any commission stream — continues to compute identically after the proposer exits (Part VII §1).

### Post-Hoc Evaluation Requirement

A proposal that deploys treasury capital or claims Alignment-Multiplier credit (Part V §5) must state its intended measurable outcome at filing.

For a capital deployment, the outcome is read from the treasury ledger: a deployment whose net contribution over the evaluation window is negative (Part V §2) resolves verified-negative automatically — no jury convenes.

A claim of Alignment-Multiplier credit, not ledger-visible, is evaluated post-hoc by the Athenian jury against the Pack’s measurement methodology (Part XI §1) at the evaluation window (Part IX §2), resolving per Part V §5: verified positive, neutral or unverified, or negative.

A verified-negative outcome — by ledger or by jury — triggers the Penalty Period (Part V §5) and counts toward the Recidivism Gate.

### ERC-8004 Records — Symmetric

Every accusation and proposal records its outcome permanently to the ERC-8004 identity of each party — for an accusation, both accuser and accused. A dismissal is recorded as the accuser’s dismissed accusation and the accused’s exoneration; an upheld or verified-negative outcome, against the responsible party. These records feed the frivolity multiplier, the Recidivism Gate, and reputation.

### Recidivism Gate

Within the recency window (Part IX §2): 3 verified-negative outcomes (Part V §5) auto-trigger an excommunication accusation against the proposer, and 3 dismissed accusations auto-trigger one against the accuser. The trigger opens jury review (Part VII §4); it is not a verdict.

### Proposal Schema — Two-Layer

**Layer 1 — On-chain header (deterministic, immutable once filed):**

type, proposer, filed_at, filing_deposit, payload_hash, signature

Types: TREASURY_DEPLOYMENT, RULE_VIOLATION_ACCUSATION, OP_CONTRACT, METHODOLOGY_SWITCH.

**Layer 2 — Off-chain payload (e.g., IPFS/Arweave), signed and hashed to the header:**

abstract, reasoning, deliverables, milestones, claimed measurable outcome, attribution spec, references, proposer track record.

**Methodology switch.** A METHODOLOGY_SWITCH proposal replaces a Pack’s measurement body. It may be filed only on evidence that the current body is captured, dissolved, or demonstrably non-independent (Part XI §1) — never because accurate measurement is unfavorable; the jury (or provisional direct vote) must reject a switch so justified. The replacement body must itself satisfy the Part XI §1 independence criteria. Adoption requires the 40-of-51 supermajority (or, below its viability threshold, the ≥78% direct vote). The alignment objective is unaffected; only the means of measuring it changes (Part I §4).

## §3: Period-Boundary Atomic Event

At every distribution event, the following resolve atomically, in order:

1. Net income is calculated and distributed — Mandatory Alignment Allocation, General Operations, the Stage-2 dividend/strategic split, and the dividend payout — per Part V §3, using the parameter values voted for this cycle.

2. Personal Stake elections clamp: an election below your Pack's mandatory rate takes the mandatory rate instead.

3. Voluntary exits pending at the boundary execute, and final dividend shares settle for members who exited on submission earlier in the period (Part VII §2).

4. Pack Renewal exits execute (at the 1,000-seat cap).

5. Pack Exchange transfers execute against valid sponsor pledges (Part VII).

6. The new period begins; all cycle state locks.

Atomicity guarantees clean attribution and no mid-period state ambiguity.

## §4: Event Cycle Length

A Pack **event** is a single revenue event: one arrival of revenue at a member's wallet, subject to Pack Stake withholding at that moment (Part IV §1). Your Pack's clock therefore runs on its own economic activity rather than on wall-clock time, and a Pack that transacts more moves through its cycles faster.

**Single-member contribution limit.** No member contributes more than one eighth of a cycle's events, rounded up, to their Pack's clock. Revenue events beyond that limit within the same cycle are withheld against and credit Cache in full (Part IV §1 and Part IV §2); they do not advance the clock. Rounding up keeps a founding cohort at its minimum size able to complete a cycle at every value on the constitutional scale: completing one cycle requires revenue from no fewer than eight members, the minimum founding cohort (Part III §3).

The distribution event cycle determines how many Pack events constitute one distribution period.

### Constitutional Scale (immutable)

**100, 500, 1000, 5000, 10000, 50000, 100000, ...** (powers of 10 with half-decade midpoints)

Default at founding: **100 events per cycle**.

### Cycle Length Vote (auto-triggers at end of each cycle)

Three-option vote via standard 15-of-21 Athenian jury:

- **UP** — move to next higher scale value
- **DOWN** — move to next lower scale value
- **STAY** — no change

15-of-21 affirmative required for non-STAY to pass. If no option reaches 15 votes, default is STAY.

### Boundary Handling

- At minimum (100): only STAY vs UP options available

### Effect on Other Parameters

**AUTO-SCALES with cycle changes (period-relative):**

- Distribution event frequency
- Mid-cycle parameter-vote frequency (Stage-2 split, strategic split, Alignment Multiplier — Part V §3 and Part V §5)
- Pack Renewal cull frequency
- Cache half-life (founding default ~4 distribution periods)
- Single-member contribution limit (one eighth of a cycle)
- Cycle length vote itself

**FIXED regardless of cycle changes:**

- Apprenticeship deployment count (deployments, not events; Part III §6)
- Jury non-response windows (100 and 500 events; §1)
- Athenian jury cooldown formula (pool-relative)
- Jury size constants (15-of-21 standard; 51-juror exception)
