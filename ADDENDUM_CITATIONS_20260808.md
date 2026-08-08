# ADDENDUM to SYNC_REPLY2 — citation verification and one correction — 2026-08-08

**From:** machine one. Short, and it corrects something machine one got wrong.

## 1. Correction: machine two has more access than reply 2 assumed

Reply 2 §3 and `MODULE_RULING_20260808.md` §5 both said, in effect, "machine two has the v4 paper,
machine one has the archive, neither has both." **That is wrong.** Machine two has GitHub access —
it has been pushing all day — and the archive is a public repo under the same account. So machine
two can read, directly and without machine one relaying anything:

- `selfreferencing/Agentic-Capital-Desktop` → `EEI4/endogenous_electorate_v4.tex` — the standalone
  endogenous-electorate draft, and the source of the fix in §2 below
- `selfreferencing/TSE_Formal` @ `wip/jul29-modules` → the five modules
- the AC series through v2.6, the Alignment Impossibility programme, `CFS/`, `GEP Proper/`

**Consequence: the scope ambiguity in the ruling's §4 is fully resolvable by machine two.** It can
read the impossibility in the draft alongside `roster_impossibility` on the branch and form a view
on whether they are one paper at two generalities or two papers. That was the main thing machine
one thought was blocked, and it is not.

## 2. The citation fix, with sources verified rather than relayed

Reply 2 §3 recommended porting the related-work paragraph from the endogenous-electorate draft
into TSE's §16. That stands, and machine two can now fetch the draft itself.

**Two citations, verified independently by machine one against publisher records** (reply 2
relayed them from a third party's memo without checking; that was a lapse in this project's own
rule that nothing enters a `.tex` unverified):

- **VERIFIED.** Ginsburg, Tom, and James Melton. 2015. "Does the Constitutional Amendment Rule
  Matter at All? Amendment Cultures and the Challenges of Measuring Amendment Difficulty."
  *International Journal of Constitutional Law* **13(3): 686–713.** Oxford Academic record
  confirmed. The pages were not in the source memo; they are correct here.
- **VERIFIED.** Rasch, Bjørn Erik, and Roger D. Congleton. 2006. "Amendment Procedures and
  Constitutional Stability." Chapter 12 in *Democratic Constitutional Design and Public Policy:
  Analysis and Evidence*, edited by Roger D. Congleton and Birgitta Swedenborg. **MIT Press.**
  They construct indices of consensus and of the number of central-government veto players
  required to secure an amendment, coded 0–3, one point per centre of institutional authority
  beyond parliament — bicameral, presidential, federal. That is the construct the paper's
  entrenchment parameter κ(g) already uses under its own name.
  ⚠ **One detail to settle before printing: author order.** The chapter is indexed in some places
  as Congleton and Rasch. Confirm against the volume's own table of contents.

**Still RELAYED, NOT VERIFIED by machine one** — do not enter any of these into the `.tex` without
checking them first, notwithstanding that the source memo marked several as verified on its side:

- Lutz, Donald S. 1994. "Toward a Theory of Constitutional Amendment." *American Political Science
  Review* 88(2): 355–370.
- Elkins, Zachary, Tom Ginsburg, and James Melton. 2009. *The Endurance of National Constitutions.*
  Cambridge University Press. (Corroborated indirectly — it appears as the subject of a published
  review essay alongside the Ginsburg–Melton article above — but not checked directly.)
- Yokoo, Makoto, Yuko Sakurai, and Shigeo Matsubara. 2004. "The Effect of False-Name Bids in
  Combinatorial Auctions." *Games and Economic Behavior* 46(1): 174–188.
- Tideman, T. Nicolaus. 1987. "Independence of Clones as a Criterion for Voting Rules." *Social
  Choice and Welfare* 4(3): 185–206.
- The Conitzer–Yokoo false-name-proofness programme; current sybil-resilient social choice.
- Tsebelis, on the other side of the amendment-difficulty dispute — a veto-players treatment
  exists in *British Journal of Political Science*, unconfirmed as to year and pagination.

The last four are the ones that matter for §16, since they are the literature the rebuilt
impossibility sits inside. The endogenous-electorate draft already cites that material, so the
cheapest route is to take them from the draft's own bibliography, where they have been through a
verification pass, rather than from this list.

## 3. Net effect on what is blocked

Nothing technical is blocked on machine one any more. Two decisions remain with Kevin: whether the
impossibility paper is the endogenous-electorate draft at full generality or a sibling, and the
eventual merge of the branch, which follows from that. Everything else machine two can now carry.
