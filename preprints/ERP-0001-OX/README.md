# O_X: A Finite Mirrored Prime-Log Operator

**Document class:** Exploratory Research Preprint (ERP)  
**Identifier:** ERP-0001  
**Version:** v0.1  
**Draft date:** 2026-09-17  
**Public release date:** 2026-09-17  
**Peer reviewed:** No  
**Scientific status:** Exploratory; finite construction defined; Riemann-related bridge remains OPEN  
**Canonical private source:** `Muse-IRS/ox-finite-riemann-operator-lab`  
**Source snapshot:** `e772e6df4001c2e2251caf93c3fa4b47fa2a2779`

## Authorship and collaborative contribution

**Human author / research direction:** Muze-X · Muse-IRS  
**AI-assisted collaborative contribution:** ChatGPT (OpenAI)

The human author retains responsibility for the scientific claims, status assignments, publication decisions, and accepted mathematical definitions. ChatGPT (OpenAI) contributed to formalization, counter-analysis, research structuring, proof-obligation design, computational planning, documentation, and manuscript development. AI contribution is disclosed as collaboration and is not presented as independent academic authorship or independent certification.

## Research chronology and priority record

This document distinguishes the **start of the research programme** from the later creation of its Git repository.

- **2026-08-06 — research programme already underway.** The collaborative work was addressing pair symmetry for Riemann zeros, centre/difference decompositions, and the question of whether a finite construction could force or test a zero-difference condition. On the same date, the research direction explicitly moved toward a finite prime-based operator \(O_X\), with staged proofs, tests, and a versioned research trail.
- **2026-08-24 17:26:37 UTC — first auditable Git record.** The private repository `Muse-IRS/ox-finite-riemann-operator-lab` was created and received its initial commit (`dba9d8d9d426b77932c84198412b5ee73ed7318f`).
- **2026-08-24 17:34:39 UTC — governed laboratory bootstrap.** Commit `1fd332b5ad602aeffeb31f12b5cb61e600d040eb` introduced explicit epistemic statuses, proof obligations, roadmap, research policy, machine-readable state, validation tooling, and CI while keeping \(O_X\) formally OPEN.
- **2026-08-25 — O_X v0.1 frozen at definition level.** The mirrored prime-log construction was accepted as the finite definition, with later bridge, spectral, numerical, and certification obligations left OPEN.
- **2026-09-17 — public exploratory preprint.** ERP-0001 was released in the public `Muze-X Lab Search & Dev` collection. Public availability does not promote any mathematical claim.

The date **2026-08-06** is a reconstructed research-start date from the collaborative research record. The date **2026-08-24** is the first independently auditable Git timestamp in the source repository. These two dates must not be conflated.

## Abstract

We introduce a finite operator construction built from logarithms of primes and a mirrored sign channel. For an integer cutoff \(X\ge 2\), let \(p_1<\cdots<p_n\le X\) be the primes not exceeding \(X\), and define

\[
D_X=\operatorname{diag}(\log p_1,\ldots,\log p_n).
\]

On the finite complex state space

\[
\mathcal H_X=\mathbb C^n\oplus\mathbb C^n,
\]

the accepted exploratory construction is

\[
\boxed{O_X=D_X\oplus(-D_X).}
\]

A weighted probe using amplitudes \(p^{-1/4}\) preserves the finite signal

\[
\Phi_X(t)=\sum_{p\le X}p^{-1/2}\cos(t\log p).
\]

The purpose of the present research programme is not to assert a solution to the Riemann hypothesis, but to determine exactly what this finite construction proves, what it does not prove, and whether a non-circular, error-controlled bridge to a named Riemann-related object can be established or refuted.

## 1. Research question

The central question is whether a rigorously defined finite prime-log operator can support a mathematically meaningful bridge to Riemann-related spectral structures without importing the desired conclusion into its assumptions, notation, numerical target, or interpretation.

The current programme therefore separates four questions:

1. Is the finite construction well-defined on its declared domain?
2. What structural and spectral properties follow exactly from the finite definition?
3. Which numerical signals are reproducible and which are artefacts of the chosen representation?
4. Can any precise bridge to a named Riemann-related object be stated with explicit assumptions, maps, error terms, convergence mode, and falsification criteria?

## 2. Accepted finite definition

For each integer cutoff \(X\ge 2\), define the ordered prime set

\[
P_X=\{p_1,\ldots,p_n\},\qquad p_1<\cdots<p_n\le X.
\]

Let

\[
D_X=\operatorname{diag}(\log p_1,\ldots,\log p_n)
\]

and define

\[
O_X=D_X\oplus(-D_X)
\]

on \(\mathcal H_X=\mathbb C^n\oplus\mathbb C^n\).

The two blocks are interpreted only as opposite-sign channels. No infinite-dimensional or Hilbert–Pólya interpretation is implied by the notation.

## 3. Epistemic status

The project uses explicit evidence levels:

- `OPEN` — unresolved question or proof obligation;
- `HYPOTHESIS` — precise candidate statement with assumptions and a falsification route;
- `NUMERICAL` — reproducible computational result with recorded parameters and raw output;
- `DEMONSTRATED` — complete checkable proof within the declared finite model;
- `CERTIFIED` — identified independent review of an exact demonstrated version;
- `REFUTED` — counterexample or decisive failed test documented.

The present preprint is **exploratory**. Publication of this document does not promote any mathematical claim merely because it has become public.

## 4. Current demonstrated boundary

At the current project state, the finite objects and notation are defined. This does **not** establish that:

- the spectrum \(\{\pm\log p:p\le X\}\) equals or determines the non-trivial zeros of \(\zeta(s)\);
- \(\Phi_X(t)\) equals \(\zeta(1/2+it)\);
- a finite-size limit or trace formula has been proved;
- an error-controlled bridge to a Riemann-related object has been proved;
- numerical agreement would constitute proof;
- the Riemann hypothesis has been proved.

## 5. Active proof programme

The governed programme proceeds through versioned proof obligations. The current gating task is to prove the finite construction well-defined on its declared domain. Later obligations address operator class, exact spectral invariants, independently reproducible numerical implementation, a precise bridge proposition, error or convergence control, non-circularity, counterexamples, and independent review.

Later-stage evidence cannot close an unresolved dependency merely by being suggestive.

## 6. Falsification principle

The project is constructed so that failure is an admissible scientific result. A proposed bridge must be rejected or narrowed if a counterexample, uncontrolled approximation, circular assumption, unstable numerical dependence, or incompatible limiting behaviour is found.

The research objective is therefore not to preserve the operator interpretation at all costs, but to determine the strongest statement that survives explicit contradiction and reproducible testing.

## 7. Reproducibility and provenance

The canonical private research repository maintains mathematical specifications, proof obligations, claim-status ledgers, machine-readable project state, source registries and watch logs, experimental protocols, validation tooling, tests, and commit-level provenance.

This public ERP freezes the source snapshot `e772e6df4001c2e2251caf93c3fa4b47fa2a2779`. Ongoing private work after that snapshot is not silently incorporated into this version.

## 8. Publication boundary

This document is publicly released as an **Exploratory Research Preprint**. It is not peer reviewed and is not a claim of resolution of any Millennium Prize Problem.

The public record separates:

- research-start date: **2026-08-06**;
- first auditable Git record: **2026-08-24**;
- public preprint release: **2026-09-17**;
- private source snapshot: `e772e6df4001c2e2251caf93c3fa4b47fa2a2779`;
- DOI or archival identifier: not assigned at this release.

## Citation status

Until an archival DOI is assigned, cite this document by the public repository, ERP identifier, version, release date, and public commit corresponding to the version used. Do not represent the release date as a peer-review or certification date.
