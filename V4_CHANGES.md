# V4_CHANGES.md — what changed between v3.9 and v4

**Date:** 2026-08-08
**Paper:** *The Theory of Strategic Evolution* (arXiv:2512.07901)
**Baseline:** `TSE_seven_laws_v3.9.tex` in this repo,
sha256 `c81423c9fb1b9c97da024d31018c43b075149b44294e03be3d6a455c5d7748e7`
**Companion repo state this version describes:**
[`selfreferencing/TSE_Formal`](https://github.com/selfreferencing/TSE_Formal) @ `7a9bc39`

This file exists so that a machine picking the project up mid-stream can tell,
without re-deriving anything, what v4 changed and why. It is a record, not a
task list.

> **Note on artifacts.** As of this commit, the corrected v4 `.tex`/`.pdf` are
> **not yet in this repo** — only this changelog is. The `v3.9` files here are
> the pre-correction baseline. Do not build from them expecting v4.

---

## 1. The one substantive correction: Law 7

Everything else in v4 is documentation hygiene. This is the only change to a
mathematical claim, and it changed in three ways.

**The printed bifurcation locus was refuted.** The barycentre linearisation of
the canonical replicator–mutator has trace `−κ/3 − 2μ`, which is strictly
negative for every `κ ≥ 0, μ > 0`. The curve v3 printed lies in the
positive-bias region, so no Hopf bifurcation occurs there. Machine-checked
(`rm_no_hopf`). This refutation is independent of everything below and stands
on its own.

**The first Lyapunov coefficient was recomputed, not rescaled.** v3 stated
`ℓ₁(μ) = −(√3/8)(1−3μ)/(1−μ)²`, transcribed from an earlier draft. Computing it
from the vector field's third-order jet (Guckenheimer–Holmes 3.4.11) gives

    ℓ₁(μ) = −6μ,    on the genuine locus  κ_c(μ) = −6μ,  μ ∈ (0, 1/3)

The two disagree most sharply at `μ = 0`, and that is how the error surfaced:
symmetric rock–paper–scissors conserves `x₀x₁x₂` and has neutrally stable
centre orbits, so `ℓ₁` **must** vanish there. The derived value does; the
printed one does not. Confirmed three independent ways — against a test system
whose coefficient is exact by construction, against an independent symbolic
re-derivation of the Poincaré displacement coefficient, and against direct
numerical integration (agreement to 1.8 × 10⁻⁵).

**The γ = 1 identification was withdrawn.** v3 read the transition at the
`γ = 1` boundary. There is no formal support for this:

- γ occurs in the Law 7 sources only in prose; the Law 7 modules do not import
  Law 3.
- The two parameters are different kinds of object — γ is a per-level vector
  over an *N*-level stack, κ is a bias parameter in a single three-type
  population. No map between them is established anywhere.
- `swirlRatio`, the only formal object offered as a bridge, is a function of κ
  alone and cannot identify `μ = 0` even in principle.
- Where it can be checked, the stability boundary is `κ = −6μ`, which equals 0
  only at `μ = 0` — and there `ℓ₁ = 0`, a degenerate centre, not a Hopf point.

v4 therefore states Law 7 at **critical coupling** with the explicit locus, and
adds a Remark recording the γ correspondence as an **open conjecture about the
framework, not a result within it**. The Law 7 statement in the abstract, the
§1.4 box, and §12 now contain no γ. Legitimate H-γ references elsewhere (Laws
1, 3, 4, 6) are unchanged and remain correct.

**Consequence for §12.4.** The amplitude theorem was rederived, not patched —
the locus itself changed, so the old coefficient is not rescalable. It now
reads `r* = (1/6)·√((κ_c − κ)/μ)` and, critically, **names its frame**: `r*` is
measured in the rotation frame after conjugation, whose singular values are
0.8165 and 1.4142, so the physical orbit in simplex coordinates is an ellipse.
An unqualified `r(κ;μ)` is not well-defined.

---

## 2. Verified figures — use these, not the old ones

All re-derived from a fresh clone at `TSE_Formal@7a9bc39`, not copied forward.

| Quantity | Value |
|---|---|
| Theorems in the elaborated environment | **240** |
| Audited headline theorems | **141** (140 standard-base + 1 axiom-free) |
| Source declarations | **203** (190 `theorem` + 13 `lemma`) |
| Custom axioms / `sorryAx` / nonstandard deps | **0 / 0 / 0** |
| Cold build | **exit 0, 7,904 jobs** |
| Lines of Lean | 5,435 across 14 modules |

**"73 theorems" was never a theorem count.** It was the length of the
`AxiomsAudit.lean` list at commit `1bd2b39` (2026-07-10) — a commit that
already contained 95 theorems. It understated the work by roughly half and
cannot be reproduced against any version of the repo. It appeared in three
places in v3 (abstract, footnote 2, §29 opening) and is gone from all of them.

**Scope matters on the axiom-free claim.** "One theorem requires no axioms at
all" is true *of the audited headline list*. The environment sweep finds six.
Both are accurate at their own scope; v4 says "one of the audited headline
results" so the scope is explicit.

**Zero custom axioms is now directly checkable.** The naive `grep axiom` does
not verify it — that hits prose and `#print axioms` directives. The anchored
check, documented in §29 and in the repo README:

```bash
grep -rnE "^[[:space:]]*axiom[[:space:]]" --include='*.lean' .   # no matches
```

---

## 3. What is carried as a hypothesis

Zero custom axioms means nothing is assumed *inside Lean*. It does not mean
every law is unconditional. v4 adds a per-law paragraph to §29 mirroring the
repo's `RETURN.md`.

**No total is quoted, deliberately.** Law 6 carries two distinct inputs, so any
single count is ambiguous — four, five, or seven depending on how you count. An
earlier draft of the correction notes said "four"; that was wrong and is not
used.

| Law | Carried as a hypothesis |
|---|---|
| 1 | hull-domination interface (`frontier_support`) |
| 2 | LP strong duality (zero-gap dual witness) for LP ⟹ KKT; Brouwer for general state-dependent existence |
| 3 | **none** — AQ-9 closed |
| 4 | **none** |
| 5 | cross-state H-γ bound (`poa_bound`). Separately: only the *implementation half* of the Second Welfare Theorem is formalized; the separating-hyperplane converse is **absent**, not hypothesised |
| 6 | **two** — the Perron–Frobenius eigen-witness in `lyapunov_destruction`, and the Lemma 15.3 interface |
| 7 | the classical planar Hopf theorem; every other side condition discharged |

**Do not claim Law 3's spectral closure discharges Law 6's Perron–Frobenius
step.** It proves the certificate ⟺ ρ(Γ) < 1 equivalence for the small-gain
matrix; it does not supply a nonnegative eigenvector with λ ≥ 1, which is a
different statement. An earlier draft of the correction notes asserted this and
was wrong.

---

## 4. Law 3 strengthened

AQ-9 is closed. The M-matrix certificate is now proven equivalent to
`ρ(Γ) < 1` **in both directions**, with zero custom axioms and no appeal to
Perron–Frobenius: a diagonal similarity for one direction, and Gelfand's
formula plus a finite Neumann sum `v = Σ_{k<N} (Γᵀ)^k 𝟙` for the converse
(`Law3_SpectralClosure.lean`). Law 3 therefore stands exactly as printed
throughout the paper — the spectral phrasing is a theorem, not an aspiration.
Nothing in the paper needed weakening to certificate form.

---

## 5. Documentation changes

- **Footnote 1 deleted.** It described a formalization that no longer exists,
  understated the verification, and cited `github.com/kevinvallier/TSE_Formal`,
  which 404s. Every repo reference now reads `selfreferencing`.
- **21 stale `Formalization:` notes swept** to current module names
  (3 Frontier / 2 Sparsity / 4 SmallGain / 4 GInfinityExtension /
  2 G12ConstitutionalSelection / 2 AlignmentImpossibilityProofs /
  3 PerronFrobenius / 1 HopfBifurcation). Every old module name is retired;
  `grep "proven modulo"` returns 0.
- **Footnote 2 shrunk** to a provenance note now that the sweep makes it
  unnecessary.
- **Structure:** each law now has exactly one section heading. An empty
  duplicate "The G∞ Closure Theorem" was deleted; three content sections that
  shadowed a law heading were demoted to subsections with their children
  cascaded. All labels preserved, so every cross-reference resolves.
- **New:** an unnumbered *A Note on Method* after the abstract; plain-language
  glosses under all seven laws; a four-movements paragraph closing §1.4;
  Main Contributions entries 3 and 4 corrected to Part II / Part IV.
- **§29:** Law 3 and Law 7 table rows updated; the certificate paragraph now
  states the equivalence rather than framing the certificate as a weakening;
  "three issues" → "four", with the Law 7 relocation added as the fourth and
  the γ = 1 sentence deleted.
- **Arithmetic fix.** Appendix I.3 read "If both were 0.9: ρ = 0.81"; it is
  0.9, since √(0.9 × 0.9) = 0.9. The same appendix gets this right 45 lines
  earlier, so the document contradicted itself. This was a real error, not a
  `pdftotext` artifact.
- **arXiv categories** updated to `cs.GT (Primary); cs.AI, cs.MA, cs.CY,
  econ.TH` — the cs.MA/cs.CY cross-lists were accepted 7 Aug.
- **Date line** → `December 2025 (revised August 2026)`.

### Repo-side changes at `TSE_Formal@7a9bc39`

- `legacy/` **deleted.** It held the only two `axiom` declarations in the
  checkout; one (`eventually_not_hurwitz`) omitted the hypothesis its own
  docstring named and was **inconsistent** — `False` was derivable from it. One
  of the two files also failed to compile. Both were imported by nothing and on
  no build path, so deletion strictly dominated repair.
- `RETURN.md` reconciled: per-law hypothesis enumeration, the AQ-20 "true Hopf
  at γ = 1" claim withdrawn, and the stale bullet calling the certificate ⟺ ρ
  equivalence "the one recorded spectral interface" corrected.
- New modules: `Law3_SpectralClosure.lean`, `Law7_Instantiation.lean`,
  `RepairProbe.lean`.

---

## 6. Build state

Clean compile from scratch: **exit 0, 170 pages, 0 errors, 0 undefined
references or citations.** (v3.9 was 169; net +1.)

---

## 7. Still open — recorded so they are not lost

1. **Part III has no Main Contributions entry** — four entries cover five
   parts.
2. **`admissible_unique` / `admissible_foldr` generality.** These hold for
   *any* two predicates. If the paper presents them as specific to the
   admissible modification class, that overstates what was proven. Unresolved;
   the most likely of the three to draw a referee's attention, since it is a
   claim about what was proven rather than a gap.
3. **`l1_coupled.py` attribution** for `l1Symmetric := c·α/2` in
   `PriceMarketMaster.lean` — the script is still absent from the repo. Either
   add it or drop the attribution.
4. **arXiv title metadata** — the record omits "the Seven Laws of" relative to
   the PDF title page. Author is matching the metadata to the source.
5. **Tier 1 (Law 7 ↔ γ).** Determining whether γ can be defined for this model
   class so that `γ = 1` characterises the Hopf locus. Evidence so far is
   negative: the two natural readings of "γ = 1" ("no guaranteed mean-fitness
   increase" ⇒ κ = 0 independent of μ; "linearised stability boundary" ⇒
   κ = −6μ) coincide only at μ = 0, the degenerate point, and the swirl-ratio
   route is ruled out. A negative result here is publishable and would settle
   the Remark in §12.2.
