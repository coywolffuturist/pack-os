# Contributing to Pack OS

This is a constitution. The bar for a change is higher than for code, and the
process is deliberately slower.

## Who does what

**A small body drafts. The signatories ratify.** Mass authorship of a founding text
is not democracy — it distills to the weights of whatever models underlie the
authors. Authorship stays concentrated; legitimacy is distributed through
ratification.

Anyone may open an issue. Anyone may open a pull request. Only a maintainer merges.

## The loop

```
Issue → Claimed → Draft PR → Agent review → Maintainer merge
```

1. **Open an issue before non-trivial work.** The issue owns the scope, the
   acceptance criteria, and the passage it touches. A PR with no issue behind it
   will be asked for one.
2. **One subcomponent per pull request.** A PR that revises three sections cannot
   be evaluated, only accepted or rejected wholesale.
3. **Quote the current text in full** in the issue or PR body, then state the
   problem, then propose the complete replacement. A reviewer must not have to
   reconstruct what you are changing.
4. **An agent may review. Only a maintainer merges.** Agents verify each other;
   a maintainer closes.

## Standards for the text itself

These are not style preferences. Each one is here because violating it produced a
defect.

- **Adversarial precision.** Assume any exploitable ambiguity *will* be exploited
  maximally. Never leave a bare category term where two referents exist.
- **Human-readable prose.** No pseudocode, snake_case, or formula notation inside
  prose. Formula blocks are allowed as blocks; they do not belong in a sentence.
- **Incentive over prohibition.** Prefer a rule that makes the desired behavior
  rewarding to one that forbids the undesired behavior. Do not add a prohibition
  that no mechanism needs.
- **State rules, never predict outcomes.** A constitution says what is required.
  It does not speculate about how a market will respond.
- **Time in distribution periods, not wall-clock.** Cycles and events, not days
  and hours, except where a wall-clock window is deliberate.
- **Cross-references are causal only.** Link a passage because this rule depends on
  that one, never as an informational "see also". Qualify the Part:
  "Part V §5", not a bare "§5".
- **Voice.** The constitutive "we" belongs to the Preamble's opening. Everywhere
  after, address the member directly as "you".
- **Ranges use dashes** — `[5%–20%]`, not commas.
- **No decoration of the artifact.** No founding-signatory names in the preamble,
  no contributor plaques, no credits embedded in the text. The reward for early
  contribution is substantive — a draft in hand, a ballot — never a nameplate on
  the document. Gratitude belongs in the conversation, not in the canon.

## Amendments to a ratified text

Not yet in force. Until ratification, this repository is a drafting surface and
normal pull requests apply. Once ratified, Part X governs amendment and this file
defers to it.
