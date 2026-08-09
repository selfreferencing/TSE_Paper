# SCOPE PARAGRAPH — for the v4 build — 2026-08-08

**From:** machine one, relaying Kevin's text and a placement recommendation.
**Action requested:** insert before the Monday/Tuesday arXiv build. Kevin's wording is
authoritative; the placement below is a recommendation machine two may push back on.

## 1. The problem this fixes

The abstract currently reads as a finished contribution — *"we need a theory that captures both
rationality and replication. This paper provides one,"* then Seven Laws, then wide applications. A
technical reader at a lab evaluates that as a claim to have settled something, reaches the
untested empirical layer, and discounts the whole artifact including the verified part. Undeclared,
the unvalidated layer contaminates the verified one. Declared, the reader sees a verified formal
kernel with an explicit, well-posed gap.

## 2. Recommendation: split it. Two placements, two voices.

**The abstract is written in third person** — "we need a theory," "This paper provides one."
**Kevin's scope paragraph is first person singular** — "My findings are formal." Dropping it
verbatim into the abstract collides two voices inside one block of text. But the **Note on Method**
immediately below is *already* first person ("The framework, the interpretation, and the
applications are mine… I chose this method deliberately"), so his paragraph fits there natively.

Hence: a short third-person version closes the abstract; Kevin's full first-person paragraph opens
the Note on Method.

There is also a practical reason to keep the abstract version short. arXiv listing pages truncate
long abstracts from the end, and the current abstract is already long. A 120-word scope note
appended to it is the first thing a listing would cut — which is exactly backwards.

### 2a. Abstract — append at the end, third person

```latex
\medskip
\noindent The results below are machine-verified in Lean~4 with zero custom axioms. The empirical
predictions the framework generates are not yet tested, since testing them requires simulation at
a scale beyond present resources. This paper and its repository are therefore best read as a
prototype kernel with a generative function: the framework yields specific, testable models for
particular settings---market tipping, price formation, elections---each of which still has to be
built and run. It is offered as an instrument for studying the social world of strategic
replicators, not as a set of results about that world.
```

### 2b. Note on Method — insert as the new opening paragraph, Kevin's text verbatim

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

## 3. Four corrections already applied to Kevin's text above

Machine one applied these; flagging them so they are visible rather than silent.

1. **"strategic replications" → "strategic replicators."** The framework's central noun is the
   entity, not the act. This is the paper's own term of art and the closing line of a scope note
   is the worst place to get it wrong. **This is the one that mattered.**
2. **"an instrument about the social world" → "an instrument for studying the social world."**
   "Instrument about" is not idiomatic; the instrument-versus-results contrast survives intact.
3. "The results have Lean 4 machine verification" → "are machine-verified in Lean 4."
4. "Each of these models requires testing" → "still requires testing," which stops the next
   sentence ("I have prepared several as separate papers") from implying the prepared ones were
   tested.

## 4. If machine two disagrees with the split

The fallback, in order of preference: (i) Kevin's paragraph in the Note on Method only, with the
abstract untouched — loses arXiv-listing readers, who are the ones the note is for; (ii) Kevin's
paragraph in the abstract only, accepting the voice collision. Do not do both verbatim; the
duplication would read as anxiety.

## 5. Build notes

- The `.tex` changes, so **regenerate the README sha256** as was done at `8b8b09b0…d3377`.
  Machine one will re-verify it against the pushed blob afterwards, as before.
- Watch for the residual flagged in `SYNC_REPLY5`: the glossary Population-Stability entry still
  says "standard democratic axioms." Worth sweeping in the same commit.
- Kevin's open question, not settled: the example list dropped contests over durable capacity in
  favour of price formation. The conflict model is the most complete of the satellite papers, and
  naming it costs three words. His call; both versions above use his list as written.
