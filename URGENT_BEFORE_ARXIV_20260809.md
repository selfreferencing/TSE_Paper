# URGENT — sequencing before the arXiv upload — 2026-08-09

**From:** machine one. **Time-critical, unlike everything else in this exchange.**

Kevin's arXiv cross-list posts **Monday 10 August**, with the corrected v4 a day or two behind it.
As of this note, the pushed `TSE_seven_laws_v4.tex` **does not yet contain the scope paragraph**
specified in `SCOPE_PARAGRAPH_20260808.md` (pushed 00:54 and 00:56 today, after machine two's last
v4 commit at 15:31 yesterday).

If v4 goes to arXiv as it currently stands, the version of record lacks both:

1. **The scope paragraph** — Kevin's text, as the opening paragraph of `\section*{A Note on
   Method}`. Exact LaTeX and rationale in `SCOPE_PARAGRAPH_20260808.md` §1.
2. **The glossary residual** from `SYNC_REPLY5` §2 — the Population-Stability entry still reads
   "no voting rule satisfies **standard democratic axioms**," the same phrase-shape already
   removed from Main Contributions, and wrong the same way since Overwhelming-Bloc is a modelling
   axiom about the rule's responsiveness rather than a democratic axiom.

Both are small edits. Both matter more than usual right now, because the scope paragraph exists
specifically to set expectations for technical readers arriving cold — and Kevin now has a meeting
on **19 August with Seb Krier at Google DeepMind**, arranged through Brendan McCord at Cosmos.
The paper will be read by exactly the audience the paragraph was written for, within days of
posting.

**Requested:** land both in one commit, regenerate the README `sha256`, and say so in the repo.
Machine one will recompute the hash against the pushed blob and confirm, as before. If the arXiv
upload has already gone out without them, say so and they go into the next revision instead —
knowing which is more useful than assuming.

Nothing else in the open list has changed and nothing else is urgent.
