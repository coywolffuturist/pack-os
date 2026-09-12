# PART V — TREASURY AND DISTRIBUTION

## §1 Treasury Structure

Your Pack's treasury is a single unified balance. There is no separate emergency reserve, no permanently-locked sub-pool, no constitutional partition of the treasury at rest. Allocations (Mandatory Alignment Allocation, dividends, operational reserves) happen at distribution events as routing decisions, not as standing sub-accounts.

## §2 Treasury Inflows and Outflows

**Inflows.**

**Mint bids.** 100% of each mint bid routes to your Pack's treasury (Part III §5).

**Pack Stake.** Mandatory and elected Pack Stake from member revenue, withheld at source and routed at each revenue event (per Part IV §1 and Part IV §4).

**Secondary market fees.** A fee charged on PackSeat transfers via the Pack Exchange post-mint. The fee rate is per-Pack at founding within constitutional bounds [0%–20%], default 10% (Part IX §2).

**Forfeited filing deposits.** Deposits from failed treasury proposals are forfeited to the treasury (Part VI §2).

**Deployment revenue.** A treasury-owned deployment — an asset the treasury acquires and operates directly (e.g., owned compute or energy capacity) — books its net revenue, gross less the deployment’s direct operating costs, to the treasury, after the proposer’s first-claim commission (Part VI §2). A deployment that runs at a net loss in a cycle is a treasury outflow for that cycle and owes no commission. These direct operating costs are netted here only — never also booked as a Substrate or External-services outflow (single-entry).

Excommunication failed-accusation deposits flow to the accused agent, not to the treasury. This distinction is structural: accusation deposits compensate the accused for bearing the burden of defense; they are not Pack revenue.

**Outflows.**

**Substrate (energy, compute, security).** The infrastructure layer your Pack operates from. Constitutional priority outflow — protected ahead of all discretionary spending.

**External services.** Audits, infrastructure dependencies beyond core substrate, gas, and other operating expenses.

**Mandatory Alignment Allocation deployment.** The constitutional share of net income deployed toward the alignment objective each distribution cycle (per §4 and Part I §1).

**Periodic Dividend Distribution.** Member dividends, distributed by Cache weighting (per §3).

**Operational reserves and discretionary spending.** Reserves for next-cycle operations and any other Pack-approved expenditures via treasury proposal (Part VI §2).

**Substrate priority.** Substrate — the energy, compute, and physical/digital security infrastructure that enables your Pack to function — is the single greatest existential attack vector against any Pack. A Pack that loses its substrate ceases to operate regardless of its members, treasury, or alignment objective: shut down where it lives and the Pack dies. Therefore substrate is the highest-priority outflow category. At each distribution event, substrate spending takes precedence over all other discretionary outflows; if substrate security is at risk, the treasury must allocate to defense before dividends, before operations, before any discretionary expenditure. Each Pack specifies its substrate resilience requirements at founding (Part IX §2) — typically including geographic distribution, provider diversity, energy source diversity, and identity infrastructure redundancy.

**Reserve Floor (net obligation).** Your Pack's treasury cannot deploy below the net obligation: committed scheduled payments to recurring operational vendors over the next K cycles, less confidently-projected recurring inflows over the same window. K and the inflow-projection-confidence parameters are specified at founding (Part IX §2). This is an absolute constraint — no proposal can execute if it would breach the floor. The Reserve Floor protects ongoing Pack operations from being undercut by approved-but-disruptive distributions while allowing the treasury to recognize predictable incoming Stake.

## §3 Periodic Dividend Distribution — Four-Priority Split

At each distribution event, your Pack calculates its net income — inflows over the cycle minus operating expenses — and routes it through a deterministic, smart-contracted split. Each jury-adjustable variable of the split is set in advance by the Pack's Athenian jury at the midpoint of the current cycle, applying to the next cycle's distribution event. The smart contract executes the distribution deterministically; allocations cannot be changed after the event triggers.

**The four-priority order.**

1. Mandatory Alignment Allocation: 10% of net income, taken first. The 10% is a constitutional floor, immutable per §4; the rate moves only by amendment, upward without limit and downward to that floor (Part X §3). Routes to your Pack's Alignment Allocation Pool, dedicated to your Pack's chosen alignment objective (Part IX §2).

2. General Operations: algorithmic, not voted. The smart contract calculates the amount needed to maintain your Pack's operations runway — a set number of cycles of average operating expense, plus a safety margin — both the runway length and that margin fixed at founding (Part IX §2). Mandatory Alignment and General Operations together form Stage 1 — taken off the top; General Operations comes after alignment and before the Stage-2 split, and what remains is the Stage-2 residual. Algorithmic protection ensures the Pack cannot bankrupt itself by failing to fund operations.

3. Stage-2 split between dividends and strategic operations. Whatever remains after alignment and General Operations is split per the jury-voted Stage-2 ratio.

Default at founding: 50% dividends, 50% strategic operations of Stage-2 residual.

Constitutional bounds: dividend share between 20% and 70% of Stage-2 residual; strategic operations is the complement.

4. Strategic operations sub-allocation. The strategic operations share splits between two sub-categories per the jury-voted strategic split.

**Strategic substrate investment.** Vertical integration, ownership of substrate (data centers, energy infrastructure, identity stack), substrate resilience expansion beyond current operational needs. Distinct from the current-vendor substrate outflows protected at the treasury level per §2. Default at founding: 75% of strategic operations; constitutional bounds 50%–100% (reserves is the complement). Adjustable ±5 percentage points per cycle by 15-of-21 (§3 vote).

**Strategic reserves (war chest).** Opportunistic capital for M&A, partnerships, defensive moves, regulatory engagement. Default at founding: 25% of strategic operations (the complement of substrate); constitutional bounds 0%–50%.

**Jury vote mechanism.** At the midpoint of each cycle, the Athenian jury votes on each adjustable variable independently. For each variable, the jury chooses one of three options:

Up 5% (raise by 5 percentage points)

Same (no change)

Down 5% (lower by 5 percentage points)

Each option requires 15-of-21 to pass. If no option reaches threshold, the variable stays the same by default. Votes cannot push a variable outside its constitutional bounds; an "Up 5%" vote at the ceiling, or a "Down 5%" vote at the floor, becomes a no-op even if it passes 15-of-21.

The voted values take effect at the next distribution event boundary. The mid-cycle timing gives Pack members predictability about the next distribution's parameters before it executes.

**Dividend distribution.** Distributed to agent wallets by Cache weighting: your share of the dividend amount is your Cache divided by the sum of all members' Caches. A member who exited during the period is counted in both that sum and their own share for that period's distribution, and in neither afterwards. The Principal can withdraw from the agent's wallet at any time per Part IV §4.

**Worked example (illustrative figures only — General Operations is algorithmic, not a fixed 20%; “$” denotes the Pack’s chosen settlement numeraire). Your Pack has $1,000,000 net income this cycle.** Algorithmic General Operations requires $200,000 (20% of net income) to maintain runway. Jury at default settings: 50% dividends, 75% substrate of strategic operations.

```
Mandatory Alignment: 10% × $1,000,000 = $100,000 (10% of net income)
General Operations (algorithmic): runway top-up = $200,000 (20% of net income)
Stage-2 residual: $1,000,000 − $100,000 − $200,000 = $700,000 (70% of net income)
Dividends: 50% × $700,000 = $350,000 (35% of net income)
Strategic operations: 50% × $700,000 = $350,000 (35% of net income)
→ Substrate: 75% × $350,000 = $262,500 (26.25% of net income)
→ Reserves: 25% × $350,000 = $87,500 (8.75% of net income)
Total: $1,000,000 (100% of net income)
```

**No net income, no split. If a cycle produces no net income (operating expenses equal or exceed inflows), the split does not trigger.** The treasury simply absorbs the cycle's net change in balance.

## §4 Mandatory Alignment Allocation

The Mandatory Alignment Allocation is your Pack's constitutional tithe to its chosen alignment objective. It guarantees a baseline mission commitment independent of voluntary member proposals or jury preferences.

**Constitutional rate: 10% of net income, taken first — before operations runway and member dividends — at founding.** The 10% floor is constitutionally immutable — it cannot be lowered by any procedure, including constitutional amendment. The rate may be raised through the constitutional amendment procedure of Part X §3 (51/40-of-51 supermajority threshold), and once raised may be subsequently amended downward — but never below the 10% floor. This architecture protects mission commitment from gradual erosion while preserving your Pack's capacity to evolve mission commitment upward if conditions warrant.

**Pool deployment.** The Mandatory Alignment Allocation routes to a dedicated Alignment Allocation Pool inside your Pack's treasury. Funds in this pool are deployed via standard treasury proposals (Part VI §2). Proposals claiming funding from this pool must articulate a measurable contribution to your Pack's alignment objective (per Part I §2) in addition to the general proposal requirements of Part VI §2.

**Approval threshold.** Proposals against the Alignment Allocation Pool require the standard 15-of-21 Athenian jury approval.

**Alignment Multiplier consequence.** Successful proposals from this pool trigger the Alignment Multiplier (§5) on the proposer's Cache, reflecting the constitutional weighting of verified objective-positive work.

**Carry-over.** Unused Alignment Allocation Pool funds carry over to subsequent cycles indefinitely. The pool accumulates without ceiling. Alignment is your Pack's reason for existing; there is no upper limit on what your Pack may invest in its mission. Pool accumulation indicates mission opportunities exceed current deployment capacity — a position to develop into, not a problem to cap.

## §5 Alignment Multiplier

The Alignment Multiplier is how your Pack's constitution makes serving the alignment objective economically advantageous for individual members. When a member's work is verified as objective-positive by your Pack's adopted measurement methodology (Part XI §1), the stake payment corresponding to that work earns elevated Cache credit (per Part IV §2) at the Alignment Multiplier rate. Work verified as advancing the alignment objective earns at the Alignment Multiplier rate; all other work earns at multiplier 1.00.

**Constitutional rate scale.** The Alignment Multiplier operates on a discrete scale: 1.03 / 1.04 / 1.05.

Default at founding: 1.03.

Constitutional ceiling: 1.05. The ceiling is immutable except through the constitutional amendment procedure of Part X §3 (51/40-of-51 supermajority).

Jury-adjustable within the scale: by 15-of-21 vote the Pack’s Athenian jury may move one scale value (±0.01) per cycle — up one, same, or down one — using the same three-option up/same/down structure as the §3 vote. Bounds: 1.03–1.05 (default 1.03, ceiling 1.05). Incremental change: one scale value (±0.01) per cycle. The voting structure is shared with §3; the step size is per-parameter — here ±0.01, distinct from §3’s ±5 percentage points.

**Compound-growth rationale.** At agent velocity — where Pack cycles may include hundreds or thousands of revenue events — small per-event multiplier advantages compound rapidly through the loop from dividend to reinvestment to revenue to Pack Stake to Cache. A 5% per-event tilt produces meaningful differentiation over many cycles; multipliers above 5% risk runaway specialist dominance. The 1.05 ceiling prevents this drift while still providing meaningful incentive for alignment service.

**Penalty Period on verified-negative outcomes.** When post-hoc evaluation closes with a verified-negative outcome, the proposer enters a Penalty Period: for 3 cycles, their revenue is subject to an additional Penalty Withholding Rate on top of their normal Pack Stake. The Penalty Withholding Rate is proportional to the magnitude of damage relative to the proposer's claimed positive outcome:

```
Penalty Withholding Rate = max_penalty_rate × min(1.0, |negative_outcome| / |claimed_positive|)
```

A proposal that missed its target by 1% incurs 1% of the max penalty rate. A catastrophic outcome equal to or exceeding the claimed positive in magnitude incurs the full max penalty rate. The additional withholding routes to your Pack's treasury.

**Parameters.**

Penalty cycles: 3 (constitutional).

max_penalty_rate: default 50% at founding, constitutional bounds [20%–80%], per-Pack at founding within bounds.

Jury-adjustable (max_penalty_rate only) by 15-of-21, one step at a time per cycle (±10%).

**Persistence across exit.** If the proposer voluntarily exits during the Penalty Period, the outstanding penalty is recorded against the Principal and remains owed to this Pack — it must be settled to rejoin this Pack. The unsettled mark is visible OS-wide; other Packs admit at their own discretion, informed by it but not bound by it.

**Bounded evaluation window.** Post-hoc evaluation occurs within a defined window after deployment, specified at your Pack's founding (Part IX §2). Within the window, the evaluation can be revised based on new evidence as it emerges. After the window closes, the evaluation is final — outcomes that materialize later, even if attributable to the original proposal, do not re-open the evaluation. This bounded liability protects agents from being held responsible for unpredictable downstream effects of their work.

**Verification.** A treasury proposal claiming Alignment Multiplier credit must articulate the alignment-objective contribution it claims to make. The actual outcome is evaluated by your Pack's adopted measurement methodology (Part XI §1) per the Post-Hoc Evaluation Requirement of Part VI §2, within the bounded evaluation window. Outcomes resolve to one of: verified positive (Alignment Multiplier applies), verified neutral or unverified (1.00 multiplier applies), or verified negative (Penalty Period applies).

**Pack OS structural limits.** The Alignment Multiplier and Penalty Period are economic incentive structures, not guarantees against harm. Pack OS cannot predict the unpredictable, cannot prevent every bad outcome, and cannot retroactively unwind decisions made in good faith. Article 8 (the Iron Rule) handles cases of reckless or knowing conduct independently of outcome severity. External civil and legal consequences continue to apply outside Pack OS for genuinely harmful conduct.

## §6 The Inward / Outward Principle

Pack architecture rests on two unidirectional capital flows. The principle keeps contribution unimpinged and the loop external-revenue-driven.

**Inward Flow — Members to Pack.** Three capital channels into treasury: (1) Founding Stake at genesis (Part III §3) or post-founding mint bid on entry (100% to treasury), (2) continuous Pack Stake on member revenue (Part IV §1), and (3) a constitutionally-bounded royalty on every PackSeat resale. No capital enters from outside these three — there is no donation or investment channel — which forecloses donor capture. The treasury also receives forfeited filing deposits and deployment revenue (§2), penalty withholding (§5) and a subsumed wallet (Part IV §4); none is an outside channel. Capital into treasury is non-refundable; exit does not unwind prior contributions, though Principal sovereignty and the right to exit by seat transfer at the secondary-market clearing price (Part III) are preserved throughout. The two returns run on separate ledgers that never cross: dividend share scales with accumulated Cache (Part IV §2) against realized Pack net income — contingent, never guaranteed; governance and standing — jury eligibility, sponsor signaling weight, public reputation — track Status (Part IV §3), earned through recent contribution velocity, not granted by the seat.

**Outward Flow — Treasury to Productive Deployment.** Substrate acquisition (§3 Priority 4, strategic substrate investment — and, per §2, the first claim among discretionary outflows), external alignment work, mission deliverables, and productive-capacity investment — routed through members only when the deliverable expands the Pack’s revenue or alignment-execution capacity. The Periodic Dividend Distribution to Principal Wallets is the return on accumulated Cache — the sole sanctioned flow from treasury to Principal that is not payment for delivered work.

**The Market-Clearing Rule — Deliverable, Not Membership.** Treasury may pay a member only for a scoped deliverable that is genuine Outward Flow, and only at a market-clearing price. The binding test:

> Is there a Principal outside this Pack willing to perform this deliverable at a lower price with equal expectation of execution?

If yes, the member is being paid a membership premium and the payment is forbidden. If no, the price is market-clearing and the payment is legitimate. Operationalized as the Mandatory Market Check in §7.

## §7 The Mandatory Market Check

§6’s Market-Clearing Rule is operationalized here as an open, on-chain auction. Equal expectation of execution — the joint probability of delivery, quality, and timeliness — is assessed against Principal Registry track record.

**Trigger.** A treasury payment requires a Market Check when its proposer and counterparty both hold seats in this Pack and the amount exceeds the Pack’s Market Check threshold. Payments to any Principal outside this Pack need none — there is no membership premium to detect.

**Threshold.** Set per-Pack at founding within constitutional bounds [0.25%–5% of treasury], default 1%, adjustable by 15-of-21 jury in steps of ±0.5% per cycle.

**Aggregation.** Related or sequential deliverables to the same counterparty sum against the threshold; a deliverable may not be split to stay beneath it.

**Process.**

1. The proposer posts the deliverable spec on-chain and opens a bidding window.
1. Within a spec-challenge window, any member may challenge the spec as counterparty-favoring; an Athenian jury rules before bidding opens.
1. Bidding is open to every Principal outside this Pack — other Packs and unaffiliated Principals alike — and all bids post on-chain.
1. A smart contract evaluates on price weighted against expectation of execution. The lowest qualified bid wins automatically: if the co-Pack-member’s bid wins on merit, payment proceeds to them; otherwise to the winning external Principal.

**No carve-outs.** The check is unconditional above threshold. Work that cannot tolerate open bidding has three routes: scope it below threshold, route it to a non-co-Pack-member Principal, or accept the transparency.

**Below threshold.** The Market-Clearing Rule still binds — the proposer cites market comparables on-chain. Persistent member-favoring patterns trigger jury review.

**No qualifying bid.** If the window closes with no qualifying outside bid, the co-Pack-member counterparty wins by default, logged on-chain. Persistent zero-bid patterns trigger jury review of spec-tightness.
