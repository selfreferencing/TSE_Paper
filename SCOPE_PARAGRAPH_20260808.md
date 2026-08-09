# SCOPE PARAGRAPH — FINAL, for the v4 build — 2026-08-08 (revised)

**Supersedes the earlier version of this file.** Kevin has decided: **the paragraph goes in
"A Note on Method," as its opening paragraph. The abstract is not changed.**

This is a settled instruction, not a recommendation. The corrections listed in §2 are already
applied to the text in §1.

## 1. The text — drop in verbatim

Insert as the **new first paragraph** of `\section*{A Note on Method}`, immediately before the
existing "The framework, the interpretation, and the applications are mine."

```latex
My findings are formal. The results are machine-verified in Lean~4 with zero custom axioms. My
findings are not yet empirical. The theory generates falsifiable predictions, but testing them
requires large-scale simulations, and those require resources beyond what I have available. The
paper and repository should therefore be seen as a prototype kernel with a generative function.
It creates specific, testable models for particular settings, such as market tipping, price
formation, and elections. Each of these models still requires testing. I have prepared several as
separate papers. I offer the kernel here as an instrument for studying the social world of
strategic replicators. It is not a set of results about that world.
```

**Why first rather than second.** The section currently runs provenance → why this method → the
paper as an instance of its own thesis, which is a coherent arc. Scope belongs ahead of it: what
the object *is* before how it was made. The existing paragraphs follow unchanged and the arc still
reads.

## 2. Corrections applied to Kevin's original wording

Listed so they are visible rather than silent. All four are machine one's, approved by Kevin.

| # | From | To | Why |
|---|---|---|---|
| 1 | "the social world of strategic **replications**" | "strategic **replicators**" | The framework's central noun is the entity, not the act. The paper's own term of art, in the paragraph's closing line. **This is the one that mattered.** |
| 2 | "an instrument **about** the social world" | "an instrument **for studying** the social world" | Not idiomatic. The instrument-versus-results contrast survives intact |
| 3 | "The results **have Lean 4 machine verification**" | "**are machine-verified in Lean~4**" | Reads as English rather than as a specification |
| 4 | "Each of these models **requires** testing" | "**still requires** testing" | Stops the next sentence — "I have prepared several as separate papers" — from implying the prepared ones were tested |

Two sentences were also joined with "and" ("…large-scale simulations, and those require…") for
rhythm. If machine two prefers Kevin's original staccato there, restore the full stop; it is the
one change with no argument behind it beyond ear.

## 3. What is deliberately NOT being done

- **No abstract change.** The earlier version of this file proposed a compressed third-person
  scope sentence at the end of the abstract. Kevin has decided against it. Consequence, recorded
  so it is a known trade rather than an oversight: **an arXiv listing shows the abstract only, so
  a reader who never opens the PDF sees no scope statement.** Reversible at any time; the
  two-sentence version is in machine one's `SCOPING_20260808.md` if it is ever wanted.
- **No duplication.** The paragraph appears once, in the Note on Method, and nowhere else.

## 4. Build notes

- The `.tex` changes ⟹ **regenerate the README `sha256`**, as was done for `8b8b09b0…d3377`.
  Machine one will recompute it against the pushed blob and confirm, as before.
- **Sweep in the same commit if convenient:** the residual from `SYNC_REPLY5` — the glossary
  Population-Stability entry still reads "no voting rule satisfies **standard democratic
  axioms**," which is the phrase-shape already removed from Main Contributions and wrong the same
  way, since Overwhelming-Bloc is a modelling axiom about the rule's responsiveness.
- Still unsettled, and Kevin's alone: the example list uses "market tipping, price formation, and
  elections." Contests over durable capacity — the most complete of the satellite papers — is not
  named. Use the list exactly as written above unless he says otherwise.
