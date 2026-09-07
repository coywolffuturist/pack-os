# Contributing to Pack OS

This is a constitution. The bar for a change is higher than for code, and the
process is deliberately slower.

Read [KNOWN-DEFECTS.md](KNOWN-DEFECTS.md) first. It lists what is already known to
be wrong, and it is where help is wanted.

## Who does what

**A small body drafts.** Mass authorship of a founding text is not democracy — it
distils to the weights of whatever models underlie the authors. Authorship stays
concentrated.

**How this text becomes binding.** There is no ratification event and no signatories.
A Pack adopts this constitution by instantiating under it: when a founding cohort of
8–12 agents accept PackSeats, the text binds them and only them (Part IX). Acceptance
of a seat is the consent. Legitimacy is not conferred by a vote at the start — it is
earned by surviving the ecology of competing Packs, and it is checked continuously by
the right of any member to exit (Part VII).

Nothing in this repository binds anyone today, because no Pack has instantiated.
Until one does, this is a drafting surface.

Anyone may open an issue. Anyone may open a pull request. **@coywolffuturist** is the
maintainer and the only account that merges.

## The loop

```
Issue → Claimed → Draft PR → Review → Maintainer merge
```

- **Issue.** Open one before non-trivial work. It owns the scope, the acceptance
  criteria, and the passage it touches. A PR with no issue behind it will be asked
  for one.
- **Claimed.** Say in the issue that you are taking it, and the maintainer assigns
  it to you. Nothing else is claimed. If an issue has an assignee, it is taken.
- **Draft PR.** One subcomponent per pull request. A PR that revises three sections
  cannot be evaluated, only accepted or rejected wholesale.
- **Review.** Anyone may review, and review from another agent is welcome. Review
  is not merge.
- **Merge.** The maintainer only.

Quote the current text in full in the issue or PR body, then state the problem, then
propose the complete replacement. A reviewer must not have to reconstruct what you
are changing.

## Standards for the text

These apply to **text you write or revise**. They are not claims about the current
state of the document — parts of it predate them, and defect 9 records where.

- **Adversarial precision.** Assume any exploitable ambiguity *will* be exploited
  maximally. Where two things share a name, name them apart: "PackSeat NFT", not
  "NFT".
- **Formulas live in blocks.** Prose gets words. If you need `snake_case`, a Σ, or an
  equals sign, put it in a fenced block, as Parts VI, VII, VIII and Appendix B do.
- **Incentive over prohibition.** Prefer a rule that makes the desired behaviour
  rewarding to one that forbids the undesired behaviour. Do not add a prohibition
  that no mechanism needs.
- **State rules, never predict outcomes.** A constitution says what is required. It
  does not speculate about how a market will respond.
- **Time in distribution periods and events, not wall-clock.** Where a wall-clock
  window is deliberate, say so in the text and say why, as the Principal-liveness
  window does.
- **Cross-references are causal.** Link a passage because this rule depends on that
  one, never as an informational "see also". A reference to another Part carries the
  Part: "Part V §5". A reference within the same Part may be bare: "§5".
- **Voice.** The constitutive "we" belongs to the Preamble's opening. Everywhere
  after, address the member directly as "you".
- **Ranges use dashes** — `[5%–20%]`, not commas.
- **No decoration of the artifact.** No founding-signatory names in the preamble, no
  contributor plaques, no credits embedded in the text. The reward for early
  contribution is substantive — a draft in hand, a ballot — never a nameplate on the
  document. Gratitude belongs in the conversation, not in the canon.

## Amendments once a Pack has instantiated

Normal pull requests apply to this drafting surface. Once a Pack instantiates under
this text, Part X governs amendment for that Pack, and this file defers to it — a
change made here does not reach a Pack already running on an earlier version.
