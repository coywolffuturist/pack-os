# Known defects

Found by two independent reviewers on 2026-09-07, before this repository was opened.
**None of these are fixed.** Each one changes what the constitution says, so each
needs a ruling from the maintainer rather than a quiet edit.

This file exists so a new contributor does not spend a day rediscovering them, and
so nobody mistakes a known hole for settled text. If you find something not listed
here, open an issue.

## 1. The precision-pass boundary — RULED 2026-09-07, no longer blocking

**Ruling: the precision pass applies to the whole document.** Where the earlier pass
stopped no longer decides anything, because no Part is exempt. Treat every Part as
requiring the pass until it has had one, and record passes per Part from here.

The evidence behind the ruling is worth keeping, because it shows the two passes are
separable: Part V §6 carried second-person voice — a voice-pass artifact — while also
carrying defect 3, a pointer inversion that an adversarial reading catches on sight.
Voice reached Part V; precision did not.

The original finding follows, for the record.

### Original finding

The drafting notes say the line-by-line precision pass stopped at **Part IV §1**.
The text disagrees: direct second-person address, an artifact of that pass, runs
through all of Part V and stops sharply at Part VI.

| Part | I | II | III | IV | V | VI | VII | VIII | IX | X | XI |
|---|---|---|---|---|---|---|---|---|---|---|---|
| `you` / `your` | 6 | 77 | 19 | 30 | 21 | 2 | 0 | 0 | 0 | 0 | 0 |

Until this is settled nobody can tell which text is reviewed and which is still
moving. **This is the first thing to resolve.** It is also not certain the notes are
the wrong side of the discrepancy.

## 2. The 40-of-51 jury's scope contradicts itself three ways — FIXED

- `constitution/10-immutability-and-amendment.md` — "This is the only Athenian jury
  in Pack OS that is not 15-of-21. All other juries are 15-of-21."
- `constitution/06-governance.md` — methodology switches also require the 40-of-51
  supermajority.
- `constitution/06-governance.md` — a third grouping lists amendments, methodology
  switches and new excommunication triggers at ≥78%, against the same file's
  "ONE EXCEPTION".
- `constitution/01-alignment-objective.md` sends the reader to Part VI §2 for
  methodology switches, which reads as 15-of-21.

Part X §3, Part IX §1 and Appendix A all say rule-additions only. Two passages say
methodology switches too. Anyone implementing this picks wrong about half the time.

## 3. A cross-reference inverts the document's headline claim — FIXED

`constitution/05-treasury-and-distribution.md` §6 cites "Substrate acquisition
(§3 Priority 1)". In §3, Priority 1 is the **Mandatory Alignment Allocation**;
substrate appears at **Priority 4**. Read alone, §6 says substrate is the first
charge — contradicting Part V §4, Part I §1, and this repository's own summary.

It reads as corroborated, because §2 separately and correctly calls substrate "the
highest-priority outflow category" among *discretionary* outflows. Two different
senses of priority, one wrong pointer.

## 4. A dangling section reference — FIXED

`constitution/09-instantiation.md` cites the Market Check threshold as **Part VI §7**.
Part VI has only §1–§4. The Mandatory Market Check is **Part V §7**. This is the only
invalid target of the 34 distinct `Part N §M` references checked.

## 5. A dead term in the glossary — FIXED

Appendix A defines Cache as `Σ_lifetime (stake_paid × outward_multiplier × decay)`.
`outward_multiplier` appears exactly once in the whole repository — here. The
authoritative Part IV §2 calls it `alignment_multiplier`. Because Part V §6 is
genuinely titled "The Inward / Outward Principle", the dead term reads as a real
mechanism. Anyone implementing Cache from the glossary hunts something that does
not exist.

## 6. A number that holds for only one exit path — FIXED

`constitution/07-exit-pathways.md` says "Pack temporarily at 999 active members
during this cycle." Pack Renewal culls 1% or 2.5% at the 1,000-seat cap — 10 or 25
seats enter the same window at once.

## 7. Ratification is undefined — CLOSED; the defect was mine, not the document's

The constitution's silence was the ruling, not a hole. Pack OS was ruled in June 2026:
**legitimacy = ecology + exit, with no constitutional genesis-gate**, and
**seat-acceptance is the consent — no ratification vote.** A Pack adopts this text by
instantiating under it (Part IX); it binds that Pack and nobody else.

"A small body drafts, the signatories ratify" was imported here from a different
document with the opposite legitimacy model — one that genuinely is ratified by its
signatories. Both are constitutions, so the model travelled without being checked.
It told two invited collaborators their work counted toward a ratification that will
never happen.

Fixed in CONTRIBUTING and README. No constitutional text was needed or added.

## 8. "Event" is the base time unit and is never defined — FIXED

Cycle length defaults to "100 events". Jury non-response windows are "rolling 100 /
500 events". Stake is withheld per "revenue event". The nearest thing to a definition
is circular — Part VI describes how many Pack events make one distribution period.
Appendix A omits the term. Anything time-denominated has to be guessed.

## 9. Standards in CONTRIBUTING that the current text does not meet — RESOLVED

CONTRIBUTING states drafting standards for **new and revised text**. Existing text
predates them in places:

- 32 bare `§` references, against the rule to qualify the Part.
- 16 uses of formula notation inside prose, against the rule that formulas stay in
  blocks — including Parts III and IV.
- Three wall-clock values. One, the Principal-liveness window, is explicitly marked
  deliberate. The 60-second juror timeout and the 24-hour TRIVIAL tier are not
  marked either way.

**Resolved 2026-09-07.** The bare-§ count was measured against an earlier draft of
CONTRIBUTING that required every § to carry its Part. The rule now reads: a
reference within the same Part may be bare. All 35 bare references were checked
against the section index of their own Part and all 35 resolve, so none is a defect.

Formula notation in prose went from 16 occurrences to 12. The four removed were
genuine prose violations. The twelve that remain are accepted exceptions, recorded
here rather than forced: Appendix A, C and D name parameters because naming them is
what a glossary does; Part VI's proposal record lists field names, which is a data
structure and not a formula; and `max_penalty_rate` in Part V is a named
constitutional parameter under discussion, not a calculation.

Both unmarked wall-clock windows are now marked deliberate, with the reason in the
text: the 60-second juror timeout, because a window denominated in Pack events would
let a quiet Pack stall a verdict; and the 24-hour TRIVIAL tier, because recovery time
from an attack is set by the outside world, not by a Pack's event rate.

---

## 10. Cache was double-counted in the glossary — FIXED, and this branch caused it

Appendix A defined Cache as `Σ_lifetime (stake_paid × alignment_multiplier × decay)`.
Part IV §2 is authoritative and applies the multiplier *inside* stake_paid, then sums
those events with decay and no further multiplier. The glossary applied it twice.

This branch created the live version. The line previously read `outward_multiplier`,
a term existing nowhere in the document — visibly broken, so a reader stopped. Fixing
defect 5 renamed it to the live term, which closed a dangling reference and in the
same stroke made a double-count look correct. A rename is not a free operation when
the renamed thing is an operand.

Found by an adversarial reviewer that a rate limit killed before it could write its
report. It left one phrase — "Cache double-count" — and the arithmetic was confirmed
independently against Part IV §2 rather than taken on its word.

**The general lesson, for anyone fixing a term here:** when a correction touches a
formula, check the arithmetic against the authoritative Part, not just the term.

## 11. The "event" definition left the Pack clock stallable and spinnable — FIXED

Defect 8 was closed by defining a Pack event as a revenue event. That definition is
a faithful reading of the text — Part IV §1 already denominated Stake per revenue
event — but substituting it into every use of "event" showed the clock has two
independent holes, and that rights hang off it.

**Stalled.** A Pack with no revenue never reaches a distribution-event boundary.
Voluntary exit executed only at a boundary, so its members could not leave, while
excommunication still ran immediately on a wall-clock juror timeout. The Pack could
expel on a clock that always ticks; a member could not leave on one. Worst at
instantiation, where a founding cohort has no clock at all.

**Spun.** Nothing set a minimum on a revenue event, so one member could manufacture
Pack time with dust transfers: decaying every rival's Cache before a distribution,
rolling their own jury non-response flags out of the window, forcing Renewal
periods, and burning the Part X §3 public-draft window whose stated purpose is to
prevent surprise rules.

The drafters had already seen half of this. The juror-timeout note in this branch
says an event-denominated window "would let a quiet Pack stall a verdict
indefinitely." That instance was fixed and the class was not swept.

**Fixed** by giving voluntary exit the split excommunication already used (Part VII
§2, Part II Article 9, Part VI §3, Part VII §5), and by capping any single member at
one eighth of a cycle's events (Part VI §4). No wall-clock was added; the standing
rule denominating time in events holds.

**Correction, 2026-09-08.** The cap first shipped rounding DOWN, and that re-created
the stall it was written to prevent. At the founding default of 100 events, a
rounded-down cap is 12, so the minimum legal cohort of eight supplied at most 96 of
the 100 events a cycle needs. Such a Pack could never reach a distribution event
however much it earned, and therefore could never distribute, never rank Status to
issue a first invitation, never fire the cycle-length vote, never complete an
amendment public-draft period, and never release a member who had recorded revenue.
The sentence asserting that eight members suffice was false at two of the seven
scale values, including the default. The cap now rounds UP, which makes that
sentence true at every scale value. Found by an adversarial reviewer, not by the
author.

**Named, not closed:** a member with no revenue in the period who anticipates a
large deal may exit on submission rather than waiting up to one cycle. The lockup
never prevented that — it delayed it by at most one cycle. A seat in Sale Limbo in a
dormant Pack still never completes its two cycles, so it never converts to LEGACY;
the member is out, the seat's fate hangs.

## 12. Part X §3 claimed a complete list and ended it with "etc." — FIXED

§3 declared itself "the complete list of amendment-grade decisions" and closed its
enumeration with "etc.", reopening the ambiguity the defect-2 fix existed to close.
The list is now closed. Two related corrections shipped with it: the 51-juror panel
was named the "rule-addition jury" in Part IX and twice in the appendices though
§3 covers four categories, and the Mandatory Alignment Allocation floor (Part V §4)
was not visible from §3.

## 13. An exited member still satisfies the active-member test — OPEN

Part III §2 asks whether an agent HOLDS an unencumbered PackSeat. Part VII §5 lets
a departing member keep the seat for two cycles so it can sell at fair market
value instead of being force-burned — it "remains their property". So a member who
has left still passes the test, and keeps jury eligibility, direct-vote
membership, Pack Chat access and the admission roster check for up to two cycles.

The test conflates owning a tradeable asset with belonging to the Pack. Those were
the same thing when it was written.

### Eight attempts, all refuted. Do not attempt a ninth as a patch.

Seven added a condition to the active-member test. Each broke a different consumer
of the predicate: the cap population, the first-invitation gate, the mint gates,
the Renewal base, the Sale Window phases. One abolished rejoin outright, against
the "Can rejoin: yes | yes | NEVER" row of the Part VII comparison table.

The eighth instead DEFINED `unencumbered`, which appears in the test and is
defined nowhere. That is the right shape, and it still failed, for a reason worth
recording permanently.

### The load-bearing design nobody wrote down

A Pack falling below its cap during a Sale Window is what makes the departing seat
sellable. The chain: every Exchange bid needs a sponsor pledge (Part VII §5); a
pledge escrows an invitation right (Part III §4); an invitation right is earned
only while the Pack is below the cap (Part III §4). A departure drops the Pack
below cap, which regenerates the right needed to buy the departing seat.

Any change that keeps the count at 1,000 through the window starves the Exchange:
no new rights, no bids, every exit force-burns to Legacy. That is the exact
outcome Part VII §5 says the window exists to prevent, and it breaks Part V §6's
promise that exit by seat transfer at the clearing price is "preserved throughout".

### What a correct fix must do

Two counts, two gates. Invitation EARNING keys on ACTIVE MEMBERS, which falls
during the window. MINTING keys on SEATS, which does not. And the mint event in
Part III §5 has no cap check of its own at all — the earning gate is the only
thing protecting the cap at mint time, so re-keying it without adding an explicit
seat check at the moment of use opens an unbounded overshoot, because invitation
rights have no expiry and bank indefinitely.

### Recorded, not part of this defect

A member who exits and buys back re-enters as an apprentice, and apprentices are
exempt from Pack Renewal (Part VII §3), so a culled cohort can buy immunity from
the next cull. This predates the defect above and is untouched by any fix to it.

## Already swept — do not redo

**Cross-references, 2026-09-07.** All 156 qualified `Part N §M` references were
checked mechanically against the actual section index of all eleven Parts. Exactly
one target does not exist: defect 4 above. Sixteen further references were flagged
by a heuristic looking for a cited concept missing from its target section; all
sixteen were read in context and all sixteen are correct. The reference layer is
sound apart from defects 3 and 4.

**Conversion fidelity.** The split files were diffed word-for-word against the
source conversion: 16,296 words, zero differences, order preserved. List glyph types
were checked against the source document — 16 ordered items and 138 unordered, all
carrying their correct form. Structure probes on the source found no footnotes,
inline images, tables, hyperlinks, or tracked changes that could have been silently
dropped.

**Appendix B, 2026-09-07 — INCOMPLETE, see below.** All 16 parameter rows were
checked against the Part that defines each. Every value and bound matches its source.

**Correction, 2026-09-08.** That sweep checked each row against the ONE Part that
defines it, and never against Part X §3, which now claims to govern which decisions
are amendment-grade. Two vote-to-change cells disagree with it: Pack cap reads
"Constitutional, immutable" with no vote, and Personal Stake ceiling reads
"Constitutional", while Part X §3 lists both as amendment-grade parameters. The Personal Stake
cell is corrected; the Pack cap conflict is open and needs a ruling, because
Part X §3 also makes "raising any constitutional ceiling" amendment-grade and
this document uses cap and ceiling for the same objects. Two
defects were in the table itself rather than in the values: one column was
misaligned by two characters, and the Stage-2 strategic-operations row listed a
15-of-21 vote for a figure that is the complement of the dividend share and
cannot be voted independently of it.

What has **not** been swept: whether the mechanisms are sound as designed. That
is not a text question.
