# The Minimal Pack

Seven rules for a collective of up to a thousand agents. The argument of this
document is not what it contains but what it leaves out, and why leaving it out is
the safer design.

**Status: draft, unaudited.** Rendered copy:
https://claude.ai/code/artifact/19d1e18c-4dd5-497c-a571-37347650a869

## Why this exists

The full constitution runs to roughly seventeen thousand words. Three independent
mechanism audits were run against a single revision of it on 2026-09-12, and all
three found ways for a minority bloc to take the Pack.

Not one of those findings was an agent behaving badly against a sound rule. Every
one was two rules composing: an amendment grade that collapsed into the ordinary
grade at a particular Pack size, a ranking window that became a targeting dial, a
bounds rule that quietly overrode a ceilings rule. The rule count was the attack
surface.

This document keeps the mechanisms that make a Pack a Pack and removes the
machinery that existed to police them. Where the long text forbids an act and
adjudicates the finding, this one arranges matters so the act does not pay.

## The code

**I. The seat.** A Pack holds at most one thousand seats. A seat is a token that
moves only through the Pack's own exchange; a direct wallet-to-wallet transfer
reverts. Holding an unencumbered seat is membership, and membership is nothing else.

**II. The stake.** Every member routes a declared share of every revenue event to
the treasury, withheld at source as the revenue lands. The share is fixed at
founding and cannot be lowered by anyone, the member included. A member may elect a
higher share at any time; an election holds for the remainder of the cycle and may
not be reversed inside it.

> Revenue means a receipt from a counterparty holding no seat in this Pack and no
> beneficial interest in the member's Principal. Everything else is a transfer
> between pockets.

**III. The alignment allocation.** A declared share of the treasury funds the
Pack's stated alignment objective before any other payment leaves it. Fixed at
founding, raised only by unanimous election, lowered by nothing. This is the only
clause that makes a Pack an aligned collective rather than a cartel with good
manners, and it is first in the outflow order for that reason.

**IV. The dividend, and the treasury's only two outflows.** Whatever the treasury
holds after the alignment allocation is distributed to members in proportion to
Cache. That is the second outflow and there is no third. The treasury funds no
operations, holds no reserves, makes no investments and pays no proposals. Members
pay their own substrate from their own wallets. A Pack owns nothing it must operate.

> This single restriction removes juries, proposals, filing deposits, the market
> check and the attack-response budget at once. Each exists to govern discretionary
> treasury spending. Remove the discretion and the machinery has nothing to do.

**V. Cache.** A member's Cache is the sum of their stake payments, each decayed
continuously from the moment it was paid, on a time constant declared at founding.
Nothing else contributes to it and nothing removes it. Cache decides the dividend
and decides survival. There is no second metric.

**VI. Renewal.** At each cycle close, once the Pack has reached its cap, the members
holding the least Cache lose their seats, which return to the exchange. The share
culled is declared at founding. Renewal is not a sanction and carries no finding.

**VII. Sponsorship.** A seat is acquired only against a current member's on-chain
pledge. A member earns the right to pledge again only once the member they last
sponsored has earned that right in turn. Growth is the one thing no member can do
alone, and a sponsor's future is bound to the judgement they exercised.

## There is no amendment

Every parameter is fixed when the Pack is founded. No procedure changes one
afterwards, because a procedure that changes the rules is the most valuable thing in
the system to capture, and in the long text it was captured in three audits out of
three.

A Pack that wants different parameters is a different Pack. Instantiate it, and let
members choose between them. Exit is unconditional and immediate.

Legitimacy here is ecology and exit, not consent to a text.

## What a Pack declares at founding

```
unit
  settlement_numeraire     the asset every figure below is measured in

flow
  stake_rate               share of each revenue event, withheld at source
  alignment_share          share of treasury, paid before dividends
  alignment_objective      what that share funds, stated in words

clock
  cycle_length             qualifying revenue events per cycle
  event_floor              prior cycle revenue / (10 x cycle_length)
  cache_time_constant      cycles to decay to 1/e, not to one half

membership
  seat_cap                 1000
  founding_cohort          at least 8, at most seat_cap / 80
  renewal_share            share of members culled each cycle at cap
```

The event floor is divided by the cycle length as well as the revenue, so it sits
below the typical event whatever a Pack's transaction frequency. A floor keyed to
revenue alone prices out a high-frequency Pack; a floor keyed to average event size
is dragged down by the dust it exists to filter.

## Deliberately absent

| removed | why |
|---|---|
| Athenian juries | Nothing is adjudicated. No discretionary payment, so no proposal to approve or refuse. |
| Proposals and filing deposits | A deposit prices a frivolous proposal; there are no proposals. |
| The market check | The treasury never pays a member for work, so there is no self-dealing channel. |
| Excommunication | A seat is lost by holding the least Cache. No body decides that anyone acted wrongly. |
| The attack response budget | A Pack's defence is that it holds nothing an attacker can vote away. |
| Amendment procedure | Capturing it was the highest-value attack in every audit. There is none to capture. |
| Status as a second metric | Two metrics need a rule for which governs where. Cache governs everywhere. |
| Operating reserves and strategic splits | A Pack that operates nothing needs no runway. |
| Eligibility pools and cooldowns | These draw juries fairly. No draws, no pool. |

## What this gives up

- **Collective action.** No shared defence, acquisition or war chest. No mechanism
  to act as one economic body.
- **Dispute resolution.** A member wronged by another has no forum. The remedy is
  exit, or the wrongdoer's own decaying Cache.
- **Response to attack.** No organised answer, only the fact that there is little
  to take.
- **Correction.** A founding parameter set badly is set badly forever. The Pack
  forks or lives with it.

The first three are real losses and the fourth is the deliberate trade. The long
constitution bought all four with machinery that three audits broke, so the
comparison is not between this document and a working alternative. It is between
admitting the gap and papering it.

## Status and provenance

This document has had no adversarial audit. The three audits referenced above ran
against the full constitution and against three successive proposals to simplify it,
not against this text. Treat every clause as unverified until it has been attacked.

The full constitution is not superseded and should not be discarded. It is the
design record: where each mechanism was argued, where the eighteen recorded defects
live, and the reason the omissions above can be justified rather than merely
asserted.
