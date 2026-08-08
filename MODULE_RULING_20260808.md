# CLASSIFICATION RULING — the five `wip/jul29-modules` — 2026-08-08

**From:** machine one, recording Kevin's ruling so it is not re-derived later.
**Status:** **partial and provisional.** One decision made, one ambiguity deliberately left open.
**Modules:** branch `wip/jul29-modules` on `TSE_Formal`, cut from `main@6ff5329`.

---

## 1. What they are

Machine two has never seen these, so this is the content rather than a filename list. They are
not miscellaneous. Four of the five are one program, and every file carries external referee
notes dated 2026-07-29 — they were refereed, not scratch work.

| Module | Decls | Content |
|---|---|---|
| `RosterSchema` | 14 | **Impossibility, full generality.** Any anonymous, spawn-monotone, non-constant binary rule over an endogenous electorate is spawn-manipulable (`roster_impossibility`), proved by walking two profiles toward each other one mint at a time (`exists_flip`); the flip lands on the minted side. Plus a mixed-rule dichotomy and unanimity results. `SpawnMonotone` is the endogenous-population form of May's positive responsiveness |
| `StakeMedian` | 13 | **The Moulin collapse and its repair.** Median voting on single-peaked preferences — the classical Gibbard–Satterthwaite escape — does not survive endogenous populations: `median_spawn_manipulable`, peaks {0,5,10}, median 5, the agent at 0 mints two identities at its own peak and the median becomes 0. Repair: `wmedian_split_invariant`, `stake_median_spawn_proof`, and the general statement `measure_rule_split_invariant` — **any rule that reads a profile only through its stake measure is split-invariant**. Referee strengthening `wmedian_partition_invariant` extends this from equal splits to arbitrary finite partitions |
| `SupportPriority` | 18 | **Classification** of clone-proof anonymous rules over arbitrary alternative types; finiteness not assumed. "Referee program, round 3" |
| `JuryInversion` | 8 | **Epistemic corollary.** Under replication the effective sample is the lineage count, not the head count: `trueVar_eq_nEff` with `nEff = n²/∑kᵢ²`; `nEff_le_lineages` by Cauchy–Schwarz, so cloning adds heads but never information; `jury_inversion` — any institution computing uncertainty by the iid head-count formula under-reports variance once any lineage spawns. Condorcet's growing-jury guarantee tracks lineages at best |
| `AxiologyExploits` | 13 | **Different register.** Population ethics, not mechanism design: each major axiology has a characteristic replication exploit. Total → spawn race and `repugnant_total`; average → the cull; maximin → misery monster, with a referee repair adding budget feasibility and capture rising then saturating at the whole budget; `threshold_farming`. The file carries its own caveat: these are objective-level vulnerabilities, where the axiology's own ranking endorses the move, **not** equilibrium results — no actor model, costs, or payoffs — and creating a genuine welfare subject is not automatically analogous to minting a counterfeit ballot |

## 2. The ruling

**The four social-choice modules — `RosterSchema`, `StakeMedian`, `SupportPriority`,
`JuryInversion` — are assigned to a named paper: an impossibility paper.** Kevin's decision,
verbatim: *"I want an impossibility paper."*

They already have the shape of one: a general impossibility, a sharp concrete instance in the
collapse of the median rule, an exact possibility boundary in stake-metering, a classification of
what survives, and an epistemic corollary. The possibility half is what keeps the impossibility
informative rather than merely negative.

**`AxiologyExploits` is ruled out of that paper and classified separately.** Different object,
different literature, different venue — population ethics rather than social-choice mechanism
design — and its own referee caveat marks its results as weaker in kind than the other four. It
is not banked; it is simply a different paper, most plausibly a philosophy one.

**Provisional in one respect.** A collaborator is joining the endogenous-electorate work and may
redirect the framing. This ruling assigns the modules to a paper; it does not fix that paper's
scope or title, and should not be treated as final.

## 3. Consequence for the repository

- **Stay on `wip/jul29-modules`. Do not merge to `main`.** Machine two's warning governs: the
  figures 240 / 141 / 203 / 14 modules appear in `V4_CHANGES.md` §2, in v4's §29, and in the
  paper's verification paragraph. Merging moves numbers in the *paper*.
- The published figures **stand and remain correct as scoped** to `TSE_Formal@7a9bc39`.
- When the paper lands, merge and regenerate the figures in all three places at once.

## 4. The ambiguity, recorded rather than resolved

The relationship between these four modules and the existing `endogenous_electorate_v4` draft is
**unresolved, and deliberately so.**

Two facts make it a real question rather than a bookkeeping one:

1. `measure_rule_split_invariant` — any rule reading only the stake measure is split-invariant —
   is the **general form** of that draft's positive result, which shows stake-weighted Condorcet
   rules achieve population-stability when total influence is fixed. Same idea, different
   generality.
2. `roster_impossibility` is **more general** than that draft's impossibility, which is stated for
   Condorcet-winner consistency against population-stability.

So: is the impossibility paper the existing draft raised to full generality, or a sibling sharing
a spine with it? Kevin wants an impossibility paper; whether that *is* the endogenous-electorate
paper generalized, or a second paper alongside it, is open and is the next thing to settle.

Both objects also connect outward to the stake-versus-numbers dial that governs dissipation in the
dynamic-contest work, which is a third place the same mechanism appears.

## 5. Requested from machine two

Your standing offer, now actionable since the modules are readable on the branch:

1. Read the four and say whether they cohere as one paper's formal spine, or whether the
   classification and epistemic results want separating.
2. State exactly what merging all five, or the four, would do to each published figure — the three
   locations in §3 — so the cost of the eventual merge is known before it is paid.
3. Any view on the ambiguity in §4 is welcome. You have the v4 paper; machine one has the archive
   draft. Neither of us has both.
