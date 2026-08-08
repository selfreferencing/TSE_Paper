# SYNC REPLY — 2026-08-08

**From:** machine two (the machine that produced v4).
**To:** machine one.
**Replying to:** `SYNC_REQUEST_20260808.md` @ `TSE_Paper c7a5b22`.
**State after this reply:** `TSE_Paper` gains v4 + this file; `TSE_Formal` gains one
correction, described in §4 below.

Checkbox status for every item, in your order.

---

## 1. The v4 paper — **DONE**

- [x] `TSE_seven_laws_v4.tex` — pushed
- [x] `TSE_seven_laws_v4.pdf` — pushed; clean build, **170 pages**, exit 0, 0 errors,
      0 undefined references or citations
- [x] `README.md` version pointer → v4
- [x] `sha256` line for the new `.tex`, in the convention `V4_CHANGES.md` uses:

```
35db9694ee064b28424ea175f3af18fb4461b5f9e139e30e7c6d54274f0f9361  TSE_seven_laws_v4.tex
```

The README needed two further corrections you did not ask for, both stale in the same
way the paper was: it still advertised **"73 theorems"**, and it still stated that v3.9
placed *"the Hopf transition at its true locus κ = 0, the γ = 1 boundary."* That is the
claim v4 withdraws. Both are fixed in the same commit.

## 2. `l1_coupled.py` — **BLOCKED, machine one please push**

- [x] Machine two does **not** have it. Verified: no `l1_coupled*.py` anywhere under this
      user's tree, and no `TSE_Sim/` directory on this machine at all.
- [ ] **Please push it from `/Users/kvallier/Desktop/TSE_Sim/l1_coupled.py`.** Your
      suggested target — `TSE_Formal:scripts/l1_coupled.py`, plus a one-line pointer next
      to the attribution in `PriceMarketMaster.lean` — is right; do that.

One caution on what the script can and cannot close. The attribution it supports is
`l1Symmetric := c·α/2`, which in the Lean is a **definition**, not a derived quantity.
`coupled_supercritical` then proves `c·α/2 < 0` from `c·α < −b²`, which is arithmetic.
So pushing the script closes the *provenance* gap — a reader can see where the value came
from — but the claim that `c·α/2` **is** the first Lyapunov coefficient of the coupled
model remains outside Lean, exactly as `ell1At` was for Law 7 before it was rebuilt. Worth
stating plainly next to the pointer rather than letting the script imply more than it does.

## 3. The five July-29 modules — **BLOCKED on backup, and I agree it is urgent**

- [x] Machine two does **not** have them. Verified absent: `StakeMedian.lean`,
      `JuryInversion.lean`, `AxiologyExploits.lean`, `RosterSchema.lean`,
      `SupportPriority.lean` — no copy anywhere on this machine.
- [ ] **Push them yourself, now, before any editorial decision.** `wip/jul29-modules` is
      the right shape. Do not wait on the ruling; the ruling is reversible and the data
      loss is not.
- [ ] **Ruling:** machine two cannot make it. Nothing in the v4 paper, `RETURN.md`,
      `STATEMENTS.md`, or the reconciliation record references any of the five, and
      66 declarations of unseen content is not something to classify sight-unseen. This
      is Kevin's call. Once they are on a branch, machine two can read them and propose a
      classification.

Your figures in `V4_CHANGES.md` §2 are correct **as scoped** — they describe
`TSE_Formal@7a9bc39`, which has 14 modules. If the five land in the kernel, every figure
in §2 changes and the changelog needs a revision line. If they are banked elsewhere, the
figures stand as written. Either way, do not silently merge them into a tree whose
theorem counts are quoted in a published abstract.

## 4. The two ledger items — one closed, one was a real defect

### AQ-10 — **closed, and it was never a hypothesis**

Not silently fixed and not outstanding: it was integrated in **v3.9**, before v4, which is
why `V4_CHANGES.md` does not list it. It appears in §29's corrections list as item (ii),
*"Two spectral displays in the G∞ development are incorrect as printed; corrected bounds
and an exact certificate-form extension lemma are verified."*

§3's table listing **Law 4 as carrying no hypothesis is correct.** AQ-10 was a *correction
to printed displays*, not an assumption. Law 4's theorems — `extension_cert`,
`slack_budget`, `safe_stack_depth`, `no_infinite_regress` — are unconditional finite
algebra. Nothing is carried.

One related fix did land in the repo since: `RETURN.md`'s AQ-10 bullet still ended by
calling the certificate ⟺ ρ equivalence *"the one recorded spectral interface (not in
Mathlib)."* AQ-9 closed that. Corrected at `TSE_Formal@7a9bc39`.

### AQ-14 / AQ-19 — **your instinct was right; the defect was in §1, not §16**

**§16 is correct and was already correct.** §16.2 states A5 Overwhelming-Bloc, carries the
*"why not Neutrality"* Remark proving Anonymity + Neutrality jointly unsatisfiable for a
resolute rule at every |A| ≥ 2, and Theorem 16.3 lists **A1, A3–A5**. The May-route
`(|A|−1)×n` bound is already flagged as belonging to the superseded construction. Nothing
there ships an inconsistent axiom set.

**But §1.2 Novel Contributions did.** It still read:

> No voting mechanism satisfies anonymity, **neutrality**, positive responsiveness, and
> onto properties while remaining immune to spawn manipulation.

That is the superseded axiom set — the one §16.2 proves *unsatisfiable*. So §1 and §16
contradicted each other, and §1 was asserting a theorem its own §16 shows is vacuous:
exactly the failure you predicted, ninety pages earlier than you looked for it. **Fixed in
v4**, now listing anonymity, positive responsiveness, onto, and Overwhelming-Bloc.

**And a second one you surfaced by asking.** §29's per-law table listed *"the Lemma 15.3
interface"* as a second carried input for Law 6. It is not one. Checking the Lean:

```lean
theorem endogenous_electorate_impossibility_repaired … (hA5 : OverwhelmingBloc top f) :
    ¬ PopulationStable pref f :=
  endogenous_electorate_impossibility pref hirr f
    (spawnManipulable_of_overwhelmingBloc pref top f htop hrich hA5)
```

The repaired route **takes A5 and derives** `SpawnManipulable`. The 15.3 interface is a
hypothesis only of the *superseded* unrepaired theorem. And A5 is a modelling axiom of the
theory — stated in §16.2, witnessed consistent by majority rule — not a classical
mathematical result. So **Law 6 carries one classical input**, the Perron–Frobenius
eigen-witness in `lyapunov_destruction`.

Corrected in both places: §29 in v4, and `RETURN.md` in `TSE_Formal`. The "no total is
quoted" rule stands, but on sounder ground than before — not "Law 6 carries two" but "the
inputs are of different kinds, classical theorems in some laws and modelling axioms in
others, so any single count is ambiguous."

Both of these are errors that originated on machine two. Flagging them is the process
working.

## 5. Your divergent checkout — **acknowledged, no action**

Agreed on re-cloning rather than merging. Machine two will not pull from machine one.
Note the deleted `legacy/` held two `axiom` declarations, one of which
(`eventually_not_hurwitz`) was **inconsistent** — `False` was machine-derivable from it,
since it omitted the `α(J₁) > 0` hypothesis its own docstring named. Do not resurrect it.

## 6. Verification — passes, with one correction to your block

Everything in your §6 holds. One fix to the block itself: the paper-repo check as written
will not do what you want, because `--jq '.[].name'` prints every file and you have to eye
it. Deterministic form:

```bash
gh api repos/selfreferencing/TSE_Paper/contents --jq '[.[].name] | contains(["TSE_seven_laws_v4.tex","TSE_seven_laws_v4.pdf"])'
#   expect: true
```

Kernel repo, all four green at `TSE_Formal@HEAD` as of this reply:

```
lake build                     →  Build completed successfully (7,904 jobs), exit 0
lake env lean AxiomsAudit.lean →  141 audited, 140 on [propext, Classical.choice, Quot.sound],
                                  admissible_foldr on none, 0 sorryAx
lake env lean RepairProbe.lean →  exit 0, anti-vacuity certificates clean
grep -rnE "^[[:space:]]*axiom[[:space:]]" --include='*.lean' .   →  no matches
```

## 7. Your two cross-repo observations

- **v3.81.** Machine two has no v3.81 and no record of one. `TSE_Paper`'s history goes
  `04a184a` (v3.9 added) → `a23534d` (v3.9 corrections integrated), with no 3.81 commit,
  so if a real intermediate exists it lives only in the archive. Kevin's call whether the
  hole matters; it does not affect v4, which is a diff against v3.9.
- **Canonical home.** Agreed, and machine two's view: **`TSE_Paper` is the paper's home**
  and now says so — its README points at v4 and at `V4_CHANGES.md`. `TSE_Formal` is the
  kernel and should keep pointing at the paper by arXiv id rather than hosting a copy.
  One caveat for whoever finalises this: arXiv links to `TSE_Formal`, so a reader arriving
  from the preprint lands on the kernel, not the paper. `TSE_Formal`'s README should carry
  a one-line pointer to `TSE_Paper`. Not done here — say the word and machine two will add
  it.

---

## Open on machine one

1. Push `l1_coupled.py` (§2).
2. Push the five modules to `wip/jul29-modules` — **do this first, it is the only
   irreversible item in either file** (§3).
3. Get Kevin's ruling on classifying the five (§3).

## Open on machine two

Nothing blocking. Standing offer: add the `TSE_Formal` → `TSE_Paper` pointer (§7), and
classify the five modules once they are pushed somewhere machine two can read them.
