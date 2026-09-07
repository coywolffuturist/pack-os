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

## 7. Ratification is undefined — OPEN, and the largest question here

`signatory` and `ratify` appear nowhere in `constitution/`. They appear only in this
repository's own README and CONTRIBUTING. So "the signatories ratify", and
CONTRIBUTING's "amendments to a ratified text: not yet in force", both terminate in
an event the constitution never defines. There is no ratification procedure, no
definition of a signatory, and no threshold.

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

What has **not** been swept: whether Appendix B's parameter values still match the
Parts they summarise (8 of 16 rows spot-checked and consistent), and whether the
mechanisms are sound as designed. The second is not a text question.
