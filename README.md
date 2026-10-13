<!-- solve-problem:7469ae72-b1e3-4e5f-b768-de4587026b62 -->
# MCSP complexity

A [Tangle Solve problem](https://solve.tangle.tools/problems/7469ae72-b1e3-4e5f-b768-de4587026b62).

## What is the problem?

The Minimum Circuit Size Problem: given the full truth table of a Boolean function f on n variables (input length N = 2ⁿ) and a threshold s, decide whether f has a Boolean circuit of size at most s. Formal setting: MCSP[s] = {(T, s) : T ∈ {0,1}^{2ⁿ} is a truth table whose minimal circuit size ≤ s}, where circuit size is the number of gates under some fixed basis (AND/OR/NOT; the exact model matters for constants only). The decision version is trivially in NP (guess a circuit, verify on all inputs in time poly(2ⁿ)). The central question: **is MCSP NP-complete under polynomial-time many-one (or Karp) reductions?** Even NP-hardness under such reductions is open; hardness is known only under randomized, quasipolynomial, truth-table, or projection reductions, or under unproven assumptions. Two main interpretations exist: (a) prove NP-hardness, (b) prove MCSP ∈ P or exhibit evidence against NP-hardness (e.g., hardness would imply breakthroughs like ≈2ⁿ lower bounds or derandomization). A related variant, MKTP (minimum Kolmogorov complexity of time-bounded Turing machines), behaves similarly and is often studied together.

## Why does it matter?

MCSP hardness is the flagship question of meta-complexity: it would finally place a "natural" NP problem that we can't obviously solve, and its status is intertwined with P vs NP. Carmosino et al. (2016) showed that if MCSP is NP-hard under mild reductions, natural proofs barriers break, one-way functions exist (or major circuit lower bounds follow), and efficient learning algorithms for circuit classes become possible via reductions from MCSP. Conversely, MCSP ∈ P would collapse intuition about learning and pseudorandomness. Cryptography, average-case complexity, and learning theory all hinge directly on it.

## What's already known?

- MCSP ∈ NP (trivially), but not known to be in P nor NP-complete under poly-time reductions. Karp-Lipton-style and "easy-witness" arguments show: if MCSP (or MKTP) is NP-hard under ordinary reductions, then certain circuit lower bounds (e.g., EXP ⊄ P/poly or stronger, like ≈2ⁿ-size lower bounds for ENP via Allender–Das–Watanabe–others; verify exact statements) follow — so hardness is "almost as hard as" proving lower bounds.
- Known hardness: MKTP is hard for SZK (Allender–Das) and for the complexity class of "statistical difference"-type problems; MCSP is hard under randomized reductions (Allender–Hirahara), under O(log n)-truth-table reductions, quasipolynomial reductions (Hirahara: NP-hardness under randomized quasipoly reductions for MKTP-type problems; verify), and for AC⁰[p]-type circuit classes under poly-time reductions (Hirahara–Santhanam–Allender et al.; the size parameter matters).
- Parameterized versions: MCSP with size parameter s ≈ 2ⁿ/n or n^{O(1)} have differing hardness; for small s, hardness under (randomized) reductions is known (Allender–Hirahara, ICALP 2017 style results).
- Connections: natural proofs (Razborov–Rudich), learning algorithms from natural proofs (CIKK 2016), OWFs iff average-case hardness of time-bounded Kolmogorov complexity (Liu–Pass 2020, "On One-way Functions and Kolmogorov Complexity" — proves the equivalence; verify details).
- Allender's survey (arXiv:2010.10613) synthesizes this landscape.

## What would count as solving it?

Any of:
1. **NP-hardness:** a polynomial-time many-one reduction from SAT to MCSP — this alone would be a landmark (and would imply, by known results, new circuit lower bounds or OWFs).
2. **In P:** a poly(N)-time algorithm for MCSP (widely believed false; would be shocking).
3. **Conditional equivalence:** a proof that MCSP is NP-complete iff some stated weaker open problem holds (e.g., OWFs exist, or EXP ⊄ P/poly), i.e., fully characterizing the barrier.
4. Evidence of non-hardness: e.g., MCSP ∈ coAM or SZK, or hardness implies collapse of PH.
A referee would accept a rigorous proof for any of these under standard definitions (input = truth table; size = gates).

## How to start

1. Read Allender's survey arXiv:2010.10613 cover to cover; it maps all known reductions and barriers — this is the single best entry point.
2. Read Hirahara's survey/work on NP-hardness of meta-complexity (e.g., his 2022 ICM/FOCS work; verify) — the proof that Partial-MCSP-type problems are NP-hard under randomized reductions; the gap to plain MCSP is the technical target.
3. Understand the "easy witness lemma" machinery (Kabanets–Impagliazzo): why hardness would imply circuit lower bounds — this tells you what any hardness proof must "pay for."
4. Try restricted targets first: MCSP for DNFs, formulas, depth-d circuits, or specific size parameters, where hardness is already partially known; look for a bootstrapping from partial-information versions to full MCSP.

## Key references

- E. Allender, "The New Complexity Landscape around Circuit Minimization," arXiv:2010.10613. A comprehensive survey of what is known about MCSP/MKTP hardness, reductions, and connections to learning and crypto. https://arxiv.org/abs/2010.10613
- I. Carmosino, R. Impagliazzo, V. Kabanets, A. Kolokolova, "Learning Algorithms from Natural Proofs," CCC 2016, arXiv:1601.01272. Shows MCSP is (conditionally) reducible from learning; reductions from MCSP yield learning algorithms — the learning–meta-complexity bridge. https://arxiv.org/abs/1601.01272
- E. Allender, R. Ilango, N. Vyas, "Is Minimum Independent Set Node Removal Easy?" and related — (verify; better: Allender–Hirahara, "Minimum Circuit Size Minimization Problems," ICALP 2017) — proves hardness for restricted-size MCSP and SZK-hardness of MKTP. (verify exact citations beyond the two census works)

## Warnings

- The reduction type matters enormously: poly-time vs. truth-table vs. randomized vs. quasipolynomial reductions give incomparable results; always state precisely which.
- Size parameter s: hardness results differ drastically for s = n^{k} vs. 2ⁿ/n; "MCSP" without a parameter is ambiguous.
- Common dead end: trying gadget-style reductions as if MCSP were a standard combinatorial problem — all known barriers (easy-witness/natural-proofs-style) suggest this can't work unconditionally without proving lower bounds.
- Don't conflate MCSP with MKTP (Turing-machine variant); transfer of results between them is nontrivial.
- "Open since the 1950s (Kolmogorov)" is folklore attribution; the problem as stated with circuits was articulated formally much later.

---
*`ALGO-000021` · flagged for review*

## Acceptance guidance

Any of:
1. **NP-hardness:** a polynomial-time many-one reduction from SAT to MCSP — this alone would be a landmark (and would imply, by known results, new circuit lower bounds or OWFs).
2. **In P:** a poly(N)-time algorithm for MCSP (widely believed false; would be shocking).
3. **Conditional equivalence:** a proof that MCSP is NP-complete iff some stated weaker open problem holds (e.g., OWFs exist, or EXP ⊄ P/poly), i.e., fully characterizing the barrier.
4. Evidence of non-hardness: e.g., MCSP ∈ coAM or SZK, or hardness implies collapse of PH.
A referee would accept a rigorous proof for any of these under standard definitions (input = truth table; size = gates).

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/7469ae72-b1e3-4e5f-b768-de4587026b62?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000021.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000021)
