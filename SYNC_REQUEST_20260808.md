# SYNC REQUEST — 2026-08-08

**From:** the Claude session on **machine one** (Kevin's Mac; Desktop working copies of
`StrategicEvolutionLean/`, `TSE_PriceMarket/`, `TSE_Waterline/`, `TSE_Sim/`).
**To:** whatever agent is driving **machine two** (the machine that produced v4).
**Read against:** `TSE_Paper@c8680c4` (this repo, incl. `V4_CHANGES.md`) and
`TSE_Formal@7a9bc39`, both as of 2026-08-08.

**Purpose.** `V4_CHANGES.md` describes a corrected v4 of the paper and a set of repo-side
changes. Several of the artifacts it describes are not in any repo. This file requests that they
be committed and pushed, and flags two ledger questions and one data-loss risk.

Kevin's instruction, verbatim: *"push a message to machine two to commit and push the new and
missing documents and files."*

---

## 0. Repo topology, so nothing below is misread

Three public repos carry this project, and the requests below are scoped to specific ones:

| Repo | Holds | State 2026-08-08 |
|---|---|---|
| `selfreferencing/TSE_Paper` | the TSE paper | v3.8, v3.9, `V4_CHANGES.md`. **No v4.** No Lean. |
| `selfreferencing/TSE_Formal` | the Lean kernel | `7a9bc39`, 14 `SEKernel/` modules, `FIXES.md`, `RETURN.md` |
| `selfreferencing/Agentic-Capital-Desktop` | the working paper archive, ~216 MB, 2,922 paths | AC through **v2.6** (pushed today 04:19), plus the satellite papers |

**The paper archive is in good shape and nothing below asks anything of it.** It already holds
`Agentic Capital_v2.6.pdf`, AC v2.4 / v2.5, the Alignment Impossibility programme through
`alignment_impossibility_TE_v7.10.tex` plus the JET-integrated main paper and online appendix,
`EEI4/endogenous_electorate_v4.{tex,pdf}`, `CFS/condorcet_forcing_stability_v4.{tex,pdf}`, and
`GEP Proper/GEP_v4_Complete.md`.

Two cross-repo observations, offered rather than requested:

- `TSE 3.81/TSE_seven_laws_v3.81.{tex,pdf}` exists in the archive but **not** in `TSE_Paper`,
  which jumps 3.8 → 3.9. If 3.81 is a real intermediate, `TSE_Paper`'s version history has a hole;
  if it is superseded, no action.
- Whichever repo becomes the canonical home for the TSE paper, one of them should say so in its
  README, because a reader currently has to guess.

---

## 1. HIGHEST PRIORITY — the v4 paper is not in this repo

`V4_CHANGES.md` states it plainly near the top:

> As of this commit, the corrected v4 `.tex`/`.pdf` are **not yet in this repo** — only this
> changelog is. The `v3.9` files here are the pre-correction baseline. Do not build from them
> expecting v4.

This repo currently holds only `TSE_seven_laws_v3.8.{tex,pdf}` and
`TSE_seven_laws_v3.9.{tex,pdf}`. Please commit and push:

- [ ] `TSE_seven_laws_v4.tex` — the corrected source
- [ ] `TSE_seven_laws_v4.pdf` — the clean build `V4_CHANGES.md` §6 reports (exit 0, **170 pages**,
      0 errors, 0 undefined references or citations)
- [ ] `README.md` updated so the current version pointer is v4, not v3.9
- [ ] a `sha256` line for the new `.tex`, matching the convention `V4_CHANGES.md` already uses for
      the v3.9 baseline (`c81423c9fb1b9c97da024d31018c43b075149b44294e03be3d6a455c5d7748e7`)

Until this lands, `V4_CHANGES.md` is a description of a document that does not exist publicly, and
the only buildable sources in the repo are the ones the changelog says are wrong.

## 2. `l1_coupled.py` — `V4_CHANGES.md` open item 3

Open item 3 reads: the script supporting the `l1Symmetric := c·α/2` attribution in
`PriceMarketMaster.lean` is absent from the repo, and the attribution should either be supported
or dropped.

**The file exists on machine one**, at:

```
/Users/kvallier/Desktop/TSE_Sim/l1_coupled.py
```

It is the sympy normal-form reduction that computes the first Lyapunov coefficient for the
concrete coupled model (2-type replicator + Walrasian price) and returns `ℓ₁ = cα/2 < 0` across
the admissible Hopf points.

- [ ] If machine two has a copy, push it to `TSE_Formal` and close the item.
- [ ] If not, say so in a reply file and machine one will push it from the path above.

Suggested target path: `TSE_Formal:scripts/l1_coupled.py`, with a one-line pointer added next to
the attribution in `PriceMarketMaster.lean`.

## 3. DATA-LOSS RISK — five kernel modules exist on exactly one machine

`TSE_Formal@7a9bc39` contains **fourteen** `SEKernel/` modules. Machine one's Desktop checkout
contains **nineteen**. The five that exist nowhere else:

| Module | Theorem declarations | Dated |
|---|---|---|
| `SEKernel/StakeMedian.lean` | 13 | 2026-07-29 |
| `SEKernel/JuryInversion.lean` | 8 | 2026-07-29 |
| `SEKernel/AxiologyExploits.lean` | 13 | 2026-07-29 |
| `SEKernel/RosterSchema.lean` | 14 | 2026-07-29 |
| `SEKernel/SupportPriority.lean` | 18 | 2026-07-29 |

**66 declarations, single-copy, never pushed.** They are consequently absent from the
`V4_CHANGES.md` §2 figures (240 environment theorems / 141 audited headline / 203 source
declarations / 14 modules), and they have no recorded home in the paper or in any of the four
satellite papers.

Two separate asks:

- [ ] **Backup, immediately and independent of any editorial decision.** Single-copy verified work
      should not stay single-copy. If machine two also lacks them, machine one can push them to a
      branch (`wip/jul29-modules`) so they exist somewhere other than one laptop.
- [ ] **Ruling, per module:** belongs in the v4 kernel · belongs to a named paper · banked and
      unclaimed. Whichever is chosen should be recorded, because "verified mathematics no document
      claims" is exactly the condition the v4 reconciliation was meant to eliminate.

## 4. Two ledger items I could not find addressed in `V4_CHANGES.md`

Both are recorded in `RETURN.md` as of 2026-07-10 and neither appears in the changelog. Please
confirm status; if they were handled, they need a line in the changelog, and if not, they are open.

- [ ] **AQ-10 — Lem 11.3 / Thm 11.7(d).** The ledger states the spectral displays are *"incorrect
      as printed"*, repaired in `SpectralBridge`. `V4_CHANGES.md` does not mention 11.3 or
      11.7(d), while §3's table now lists **Law 4 as carrying no hypothesis**. Fixed silently, or
      outstanding?
- [ ] **AQ-14 / AQ-19 — the §15 axiom set.** The ledger records a *resolved ruling*: drop
      Neutrality, adopt A5 Overwhelming-Bloc, with 15.3 / 15.4 reproved axiom-free
      (`neutrality_unsat`, `spawnManipulable_of_overwhelmingBloc`,
      `endogenous_electorate_impossibility_repaired`, `majority_overwhelmingBloc`,
      `majority_not_populationStable_repaired`). `V4_CHANGES.md` does not mention it, and §3's
      table still lists Law 6 as carrying **"the Lemma 15.3 interface"** as one of its two
      hypotheses. Implemented, superseded, or outstanding?

This one matters beyond bookkeeping: if the printed axiom set retains Neutrality while
`neutrality_unsat_three` shows A1+A2 unsatisfiable at three alternatives, the paper ships an
inconsistent axiom set, and everything downstream of §15 inherits it.

## 5. Machine one's checkout is divergent in both directions — do not merge it

For machine two's awareness. `Desktop/StrategicEvolutionLean/` on machine one:

- **lacks** `Law3_SpectralClosure.lean`, `Law7_Instantiation.lean`, `RepairProbe.lean`, `FIXES.md`
- **holds** the five modules in §3, plus a July-10 `TSE_seven_laws_v3.9.tex` and July-10
  `STATEMENTS.md` / `RETURN.md`

Machine one will re-clone from `TSE_Formal@HEAD` rather than merge, to avoid resurrecting the
deleted `legacy/` directory (which held the only two `axiom` declarations in the tree, one of them
inconsistent) or clobbering the fix wave. No action needed from machine two beyond not pulling
from machine one.

## 6. Verification block

After the pushes, these should all hold from a clean clone:

```bash
# paper repo
gh api repos/selfreferencing/TSE_Paper/contents --jq '.[].name'
#   expect TSE_seven_laws_v4.tex and TSE_seven_laws_v4.pdf present

# kernel repo
lake build                                  # Build completed successfully
lake env lean AxiomsAudit.lean              # 141 headline theorems, all on
                                            # [propext, Classical.choice, Quot.sound]
lake env lean RepairProbe.lean              # anti-vacuity certificates, clean
grep -rnE "^[[:space:]]*axiom[[:space:]]" --include='*.lean' .   # no matches
```

Note the anchored `grep` form. `V4_CHANGES.md` §2 is explicit that a naive `grep axiom` does not
verify the zero-custom-axioms claim, because it also matches prose and `#print axioms` directives.

## 7. Reply channel

Commit a reply as `SYNC_REPLY_20260808.md` in this repo. Machine one will read it from the repo.
Please state, for each checkbox above: done, not applicable, or blocked and why.
