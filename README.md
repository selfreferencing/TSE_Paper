# The Theory of Strategic Evolution

**Games with Endogenous Players and the Seven Laws of Strategic Replicators**

Kevin Vallier  
University of Toledo  
December 2025

[![arXiv](https://img.shields.io/badge/arXiv-2512.07901-b31b1b.svg)](https://arxiv.org/abs/2512.07901)
[![Lean](https://img.shields.io/badge/Lean_4-Formalized-blue.svg)](https://github.com/selfreferencing/TSE_Formal)

---

## Current Version and Formal Verification

**Current source:** [`TSE_seven_laws_v3.9.tex`](TSE_seven_laws_v3.9.tex) (the prior `v3.8` `.tex`/`.pdf` are kept for reference; regenerate the PDF when compiling). Published preprint: [arXiv:2512.07901](https://arxiv.org/abs/2512.07901).

**All seven laws are machine-verified in Lean 4 / Mathlib** — 73 theorems, cold-compiling with zero custom axioms — at [`selfreferencing/TSE_Formal`](https://github.com/selfreferencing/TSE_Formal). Version 3.9 adds a *Formal Verification* section and integrates the corrections the verification surfaced (ESDI existence via Nash's map / Brouwer; corrected G∞ spectral bounds; the endogenous-electorate impossibility rebuilt on an Overwhelming-Bloc axiom; and the Hopf transition placed at the γ = 1 boundary). These appear as clearly-marked footnotes and remarks; the framework's architecture is unchanged.

---

## One-Sentence Summary

When AI systems can copy themselves, alignment becomes a property of the ecosystem rather than individual systems, and stable alignment requires constitutional constraints on self-modification rather than programming the right values.

---

## Abstract

Von Neumann founded both game theory and the theory of self-reproducing automata, but the two programs never merged. Rational players do not control their replication, and replicators do not choose strategically. Contemporary AI systems expose this gap: they optimize objectives, yet the population of AI systems expands and contracts based on performance. When capital can spawn capital, we need a theory that captures both rationality and replication. This paper provides one.

The Theory of Strategic Evolution (TSE) analyzes **strategic replicators**: entities that optimize under resource constraints and spawn copies of themselves. 

---

## The Seven Laws

| Law | Name | Plain Statement |
|-----|------|-----------------|
| 1 | Strategic Selection | Types that waste resources go extinct; mean fitness always increases |
| 2 | ESDI Characterization | Equilibria exist, are sparse, and with m constraints at most m types survive |
| 3 | H-γ Stability | Multi-level systems are stable iff spectral radius ρ(Γ) < 1 |
| 4 | G∞ Closure | Safe modifications form a maximal closed class; going meta doesn't escape selection |
| 5 | Constitutional Duality | Shadow prices implement any frontier allocation; welfare theorems hold |
| 6 | Alignment Impossibility | Unrestricted self-modification escapes any stability basin |
| 7 | Hopf Transition | At γ = 1, stable equilibria become limit cycles |

---

## Core Claims

1. **Replication is the critical variable.** Not superintelligence. When systems can copy themselves, everything changes.

2. **Lineages are the strategic units.** Individual instances are transient. What persists and competes are lineages that decide how many instances to deploy.

3. **Selection eliminates dominated types.** Mean fitness is a Lyapunov function. Inefficient types go extinct.

4. **Equilibria are sparse.** With m binding constraints, at most m types survive. Barbell distributions emerge naturally.

5. **Multi-level stability requires bounded feedback.** The spectral radius condition ρ(Γ) < 1 is necessary and sufficient.

6. **Personality engineering fails.** Alignment through individual system design erodes under population-level selection.

7. **Constitutional design works.** Bounding the modification class enables stable alignment.

8. **Democracy fails under strategic spawning.** No voting rule satisfies standard axioms when voters can replicate.

---

## Key Concepts

### Strategic Replicator
An entity that (1) maintains a utility function, (2) controls a resource budget, (3) can spawn and retire copies, and (4) faces selection pressure favoring higher performance.

### RUPSI Axioms
Five axioms characterizing strategic replicators: Rival resources, Utility-guided portfolios, Performance-mapped fitness, Selection monotone, Innovation rare.

### Games with Endogenous Players (GEP)
Game-theoretic framework where lineages choose portfolios of agent types under shared constraints. The player set is endogenous.

### Return on Compute (ROC)
The generalization of biological fitness: return per unit of computational resource consumed.

### ESDI (Evolutionarily Stable Distribution of Intelligence)
The equilibrium concept for strategic replicators. Nash equilibrium + no invasion + dynamic stability.

### Small-Gain Condition
The stability criterion ρ(Γ) < 1 for multi-level hierarchical systems.

### Modification Class
The set of self-modifications a system can make. Full reachability (M = M_all) implies alignment impossibility.

### Constitutional Design
Bounding the modification class to make alignment stable, rather than trying to program good values (personality engineering).

---

## Why This Matters for AI

The standard approach to AI alignment focuses on individual systems: give them good values, make them corrigible, ensure they do what we want. TSE shows why this is insufficient.

When AI systems can replicate:
- Individual values face selection pressure
- Less constrained systems outcompete more constrained ones
- Alignment erodes even if initial systems are perfectly aligned

The solution is not better personality engineering but constitutional design: constraints on what modifications systems can make, regardless of their values.

---

## Paper Structure

- **Part I: Foundations** — Strategic replicators, RUPSI axioms, Games with Endogenous Players
- **Part II: The Seven Laws** — Full statements and proofs of Laws 1–7
- **Part III: Extensions** — Endogenous utilities, multi-sector dynamics, innovation
- **Part IV: Generalizations** — Heterogeneous fitness, continuous strategies, PDMPs
- **Part V: Synthesis** — Policy implications, future directions
- **Appendices F–L** — Quick reference, concept modules, worked examples, audience framings

---

## Formal Verification

Core theorems have been formally verified in Lean 4 using Mathlib4:
- Laws 2 and 3 are fully machine-checked
- Laws 1, 4, 5, 6, 7 are proven modulo standard axioms for spectral theory, ODE existence, and bifurcation theory

See: [TSE_Formal repository](https://github.com/selfreferencing/TSE_Formal)

---

## Files

| File | Description |
|------|-------------|
| `TSE_seven_laws_v3.8.tex` | Full LaTeX source |
| `TSE_seven_laws_v3.8.pdf` | Compiled PDF (168 pages) |

---

## Citation

```bibtex
@article{vallier2025tse,
  title={The Theory of Strategic Evolution: Games with Endogenous Players and the Seven Laws of Strategic Replicators},
  author={Vallier, Kevin},
  journal={arXiv preprint arXiv:2512.07901},
  year={2025}
}
```

---

## Related Work

- Von Neumann & Morgenstern (1944) — Game theory
- Von Neumann (1966) — Self-reproducing automata
- Arrow (1951) — Impossibility theorem
- Maynard Smith (1982) — Evolutionary game theory
- Buchanan & Tullock (1962) — Constitutional political economy

---

## Keywords

strategic evolution, game theory, self-replication, evolutionary dynamics, AI governance, AI alignment, constitutional political economy, impossibility theorems, Lyapunov stability, replicator dynamics, mechanism design, multi-agent systems, agentic AI

---

## License

MIT License

---

## Contact

Kevin Vallier  
kevinvallier@gmail.com  
University of Toledo
