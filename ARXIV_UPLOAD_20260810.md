# ARXIV UPLOAD — v4 replacement of 2512.07901 — for whichever machine does it

**Prepared by machine two, 2026-08-09.** Everything needed is in this file; nothing has to be
relayed from a chat session.

## 1. The file

Upload **`TSE_seven_laws_v4.tex`** from this repository. Verify before uploading:

```
sha256  7f96fdaede2bb8b712752653fe33d0b08f8476b5c17c63be1ce5bb65e01c4a49
```

**Upload that single file and nothing else.** Pre-flight checks already done:

| Check | Result |
|---|---|
| `\includegraphics` | 0 -- figures are inline TikZ, no image files exist or are needed |
| `\input` / `\include` | 0 -- single self-contained source |
| `.bib` / BibTeX pass | not needed -- bibliography is an inline `thebibliography` |
| `\pdfoutput=1` | present, line 2 -- arXiv will use pdfLaTeX, not the dvi route |
| shell-escape / TikZ externalization | none -- would fail on arXiv |
| absolute paths | none |
| local build | 171 pages, 0 errors, 0 undefined references, 0 undefined citations |

Packages, all standard TeX Live: amsmath, amssymb, amsthm, booktabs, enumitem, geometry,
graphicx, hyperref, mathtools, natbib, setspace, tcolorbox, tikz, xcolor. If the arXiv build
throws anything, `tcolorbox` is the only one I would expect trouble from, and it would show as a
broken law box rather than failing silently.

## 2. Metadata -- four fields, none of which arXiv prompts for

### Title (add the missing clause; the record currently omits it)

```
The Theory of Strategic Evolution: Games with Endogenous Players and the Seven Laws of Strategic Replicators
```

### Comments (replace entirely -- do NOT keep "Draft manuscript" or "establish priority")

```
171 pages. Formalized in Lean 4 with Mathlib: 240 theorems in the elaborated environment, 141 audited headline results, cold-compiling from a clean checkout with zero custom axioms. Source, theorem-by-theorem contract, and reproducible axiom audit: https://github.com/selfreferencing/TSE_Formal. Companion to Agentic Capital.
```

### Abstract (replace with the text below -- it must match the paper)

Typography already normalised to straight quotes and ASCII dashes. This is the abstract **proper**;
the "Formal verification" paragraph that follows it in the PDF is a separate block and belongs in
Comments, not here.

```
Von Neumann founded both game theory and the theory of self-reproducing automata, but the two programs never merged. Rational players do not control their replication, and replicators do not choose strategically. Contemporary AI systems expose this gap: they optimize objectives, yet the population of AI systems is not fixed but expands and contracts based on performance. When capital can spawn capital, we need a theory that captures both rationality and replication. This paper provides one. The Theory of Strategic Evolution analyzes strategic replicators: entities that optimize under resource constraints and spawn copies of themselves. The framework is organized around Seven Laws that characterize the dynamics, equilibria, stability conditions, and fundamental limits of such systems: 1. Strategic Selection: Mean fitness serves as a Lyapunov function; dominated types are eliminated. 2. ESDI Characterization: Equilibria exist, are generically finite, and satisfy Nash-KKT-LP equivalence. 3. H-γ Stability: Multi-level systems are stable iff the spectral radius ρ(Γ) < 1. 4. G∞ Closure: A unique maximal class of safe modifications exists and is closed under composition. 5. Constitutional Duality: Shadow prices implement any frontier allocation; welfare theorems hold. 6. Alignment Impossibility: Full reachability destroys Lyapunov structure; alignment requires bounded modification. 7. Hopf Transition: At critical coupling, systems undergo supercritical bifurcation producing limit cycles. Applications range from AI deployment dynamics to institutional design, and bear directly on multi-agent AI systems in which populations of deployed agents expand, contract, and coordinate without a fixed roster. The framework shows why "personality engineering" fails under selection pressure and identifies constitutional constraints necessary for stable alignment. The Lean 4 formalization verifies every result with zero custom axioms. The framework generates empirical predictions that remain untested. The paper and its repository are therefore a prototype kernel: an instrument for studying strategic replicators, not a set of results about the world.
```

### Categories

Confirm the approved cross-list carried through. Expected after this replacement:

- Primary: **cs.GT**
- Cross-lists: **cs.AI, cs.MA, cs.CY, econ.TH**

cs.MA and cs.CY were approved 7 Aug and announced 10 Aug. If they are missing from the replacement
form, do not re-request them -- check the announced record first.

## 3. After the build, before finalising

arXiv returns a compiled proof. Open it and check three things:

1. **Page 1** -- "A Note on Method" begins with the scope paragraph ("My findings are formal...").
2. **Date line** -- reads `December 2025 (revised August 2026)`. The paper carries no internal
   version number by design; arXiv's own counter will call this v4.
3. **Page count 171.** A different number means the arXiv TeX Live differs from the local build and
   the proof should be read more carefully before finalising.

## 4. What NOT to do

- Do not remove or soften the AI-assistance disclosure in "A Note on Method". It is accurate, it
  was written deliberately, and under arXiv's May 2026 policy -- which penalises *unverified* LLM
  output, with hallucinated references as the paradigm evidence -- a prior voluntary disclosure is
  protection rather than exposure.
- Do not merge `wip/jul29-modules` in `TSE_Formal` before this upload completes. It moves the
  240/141 figures, which appear in this paper's Section 24 and in the abstract above.
- Do not add the Barro-Becker / Guth-Yaari citations in this pass. They are a defensive addition
  for the next revision, not a correction, and editing a clean file under time pressure is the
  larger risk.

## 5. Provenance of the numbers in the metadata

All re-derived from a clean checkout at `TSE_Formal@bd80f4a`, not copied forward: 240 theorems in
the elaborated environment, 141 audited headline results, zero custom axioms, zero `sorryAx`, cold
build green at 7,904 jobs. The bibliography was audited entry by entry against publisher records
on 2026-08-09; two defective entries were found and corrected (Buchanan & Tullock misdated 1990 for
1962; a `wang2019` entry that conflated POET with "Emergent Complexity via Multi-Agent Competition"
under an author list belonging to neither). No residual prompts or assistant artifacts anywhere in
the source.
