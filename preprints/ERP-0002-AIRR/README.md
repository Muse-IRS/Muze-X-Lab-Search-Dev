# Adaptive Inference Resource Regulator (AIRR)

## A Multi-Resource Closed-Loop Controller for Experimental AI Inference Allocation

**Document class:** Exploratory Research Preprint (ERP)  
**Identifier:** ERP-0002  
**Version:** v0.2  
**Draft date:** 2026-09-17  
**Public release date:** 2026-09-17  
**Peer reviewed:** No  
**Scientific status:** Experimental / hypothesis-driven  
**Canonical private source:** `Muse-IRS/adaptive-inference-resource-regulator`  
**Source snapshot:** `6c5d095950de8f234dad487406e5b3aa58d02820`

## Authorship and collaborative contribution

**Human author / research direction:** Muze-X · Muse-IRS  
**AI-assisted collaborative contribution:** ChatGPT (OpenAI)

The human author retains responsibility for scientific claims, status assignments, release decisions, and accepted research direction. ChatGPT (OpenAI) contributed to architecture formalization, counter-analysis, experimental design, falsification criteria, software structure, documentation, and manuscript development. AI contribution is disclosed as collaboration and is not presented as independent certification.

## Research chronology

The public preprint preserves distinct dates:

- **2026-08-24 20:42:10 UTC — repository creation.** This is the earliest independently auditable GitHub timestamp for the AIRR repository.
- **2026-08-24 20:52:39 UTC — experimental v0.1 bootstrap.** Commit `26fa75dfee7b0aaac526c1332b2aaba55b660c0b` established the admission, inference-intensity and feedback architecture, synthetic baselines, epistemic boundaries and deterministic CI while explicitly leaving real-model validation `UNKNOWN`.
- **2026-08-24 21:16:58 UTC — v0.2 multi-resource preparation.** Commit `b406a1aa7ce6c05ddf37abae0038d672278690cb` expanded the controller from token-only allocation to an adapter-relative multi-resource control surface.
- **2026-09-17 — public exploratory preprint.** ERP-0002 was released in `Muze-X Lab Search & Dev`.

No earlier research-start date is asserted here unless supported by a separately retained source record. The auditable programme therefore begins on **24 August 2026** for purposes of this preprint.

## Abstract

We introduce the Adaptive Inference Resource Regulator (AIRR), an experimental closed-loop controller for allocating inference resources under explicit quality and corrigibility constraints. AIRR separates four decisions that are often conflated: whether an inference should be admitted, how much inference intensity is justified, which resource envelope should be allocated, and how observed cost and quality should feed back into later decisions.

The system is deliberately multi-resource. It may represent tokens, retained context, compute fraction, tool calls, retries, remote calls, latency, network traffic and energy where those quantities are directly measurable. AIRR does not collapse heterogeneous units into a single universal cost scalar without an explicit normalization and weighting protocol.

The core hypothesis is that an admission + intensity + resource-budgeting + feedback controller can reduce one or more measured resources on selected task distributions relative to declared baselines while maintaining measured quality above a declared threshold and preserving escalation or correction paths. This is an experimental hypothesis, not a demonstrated general result. Current synthetic tests validate implementation behavior only; real-model resource savings, semantic quality preservation and production energy savings remain unestablished.

## 1. Research question

AIRR asks:

> Can an inference controller improve the resource–quality frontier rather than merely minimize one cost metric?

A minimal formulation is

\[
\min C(x)
\]

subject to

\[
Q(x) \ge Q_{\min}
\]

and

\[
\text{correction/escalation remains available}.
\]

Here, \(C\) is not assumed to be a single scalar. It can be a resource vector such as

\[
C=(T_{in},T_{out},T_{reason},B_{net},E,t,N_{tools},N_{remote},N_{retry}),
\]

where the components may denote tokens, network bytes, measured energy, latency and action counts. Missing measurements remain `UNKNOWN`; they are not silently replaced by zero.

## 2. Controller decomposition

AIRR separates the control path into:

```text
observation
   ↓
admission         → ACTIVE | SILENCE | DEFER
   ↓
intensity         → λ ∈ [0,1]
   ↓
resource envelope → tokens | context | compute | tools | retries | remote calls
   ↓
provider/domain adapter
   ↓
execution
   ↓
raw resource usage + measured quality
   ↓
feedback
   ↺
```

This decomposition is intentional. A controller may correctly decide that a task should run while still allocating too much or too little effort. Conversely, a well-calibrated intensity policy cannot compensate for an incorrect admission decision.

## 3. Admission states

AIRR inherits the explicit state alphabet

\[
\{\texttt{ACTIVE},\texttt{SILENCE},\texttt{DEFER}\}.
\]

- `ACTIVE` admits execution under the current policy.
- `SILENCE` represents a valid non-action state when activity does not justify execution under the declared protocol.
- `DEFER` postpones execution under temporary constraints and must not be counted as a saving unless the deferred lifecycle is followed to completion.

The distinction between `SILENCE` and `DEFER` prevents shifted work from being mislabeled as saved work.

## 4. Inference intensity

For admitted work, AIRR assigns an experimental inference intensity

\[
\lambda\in[0,1].
\]

The current implementation uses normalized estimates such as uncertainty, risk, complexity and resource availability. These variables are experimental adapter inputs; they are not universal physical quantities.

A key design constraint is that uncertainty does not map monotonically to less computation. In some tasks, uncertainty may justify more verification rather than less effort. AIRR therefore treats the mapping from task state to intensity as falsifiable policy rather than law.

## 5. Resource envelope

The current `ResourceBudget` exposes control targets for:

- token budget;
- retained context fraction;
- compute fraction;
- tool-call budget;
- retry budget;
- remote-call budget.

Provider or local adapters may additionally report raw measurements such as input/output/reasoning tokens, wall-clock time, network bytes or energy joules when exposed by the tested stack.

A control target is not itself an observed saving. The distinction is:

\[
\text{budget request} \neq \text{actual consumption} \neq \text{system-wide resource effect}.
\]

## 6. Core hypothesis

`HYP-AIRR-01`:

> An admission + intensity + multi-resource budgeting + feedback controller can reduce one or more measured inference resources on selected task distributions, relative to explicit baselines, without reducing measured quality below a declared threshold.

This statement is intentionally conditional. It does not assert that AIRR improves every workload, model, provider, modality or deployment environment.

## 7. Falsification conditions

The hypothesis should be narrowed or rejected when any of the following occurs under a declared protocol:

1. controller overhead cancels the measured savings;
2. quality falls below the declared floor;
3. apparent savings are caused only by deferred work that later reappears;
4. resource reductions do not survive comparison with simpler fixed-budget policies;
5. gains depend on an unstable or unavailable estimator;
6. a claimed cross-resource improvement results from silently mixing incompatible units;
7. a token reduction is presented as energy reduction without direct energy evidence.

Failure is a valid scientific result.

## 8. Experimental programme

The research sequence is deliberately staged.

### Stage A — synthetic harness

Use deterministic task distributions and explicit synthetic oracles to validate controller logic, accounting paths, state transitions and baseline comparisons.

A synthetic `SAT` result means only that the implementation behaved as expected under the declared synthetic oracle.

### Stage B — instrumentation

Connect to adapters that preserve raw observable costs without inventing unavailable measurements. Record exact model/provider configuration, tokenizer behavior, retries, tool use, network calls and timing where measurable.

### Stage C — model-backed evaluation

Compare AIRR against declared baselines on reproducible task suites with an explicit quality-evaluation protocol. Report confidence intervals, failure modes, controller overhead and correction/escalation rates.

### Stage D — cross-stack transfer

Only after model-backed evidence exists should transfer across model families, providers or deployment environments be investigated.

## 9. Epistemic vocabulary

AIRR uses the following statuses:

- `OBS` — directly observed or implemented;
- `REL` — relation established within the declared model;
- `HYP` — hypothesis;
- `PRED` — falsifiable expected outcome;
- `SAT` — a test passed under declared conditions;
- `UNKNOWN` — not established;
- `REFUTED` — falsified under a declared test;
- `N.A.` — not applicable.

The project explicitly maintains:

```text
SAT != proof
formalization != evidence
synthetic savings != production savings
token reduction != proven energy reduction
```

## 10. Current boundary

AIRR v0.2-dev does not currently establish:

- real LLM resource savings;
- semantic quality preservation on real tasks;
- server-side energy savings;
- end-to-end network-energy savings;
- optimality of the scoring or budget mappings;
- a universal relation between uncertainty and compute;
- production readiness;
- safety-critical suitability.

The current scientific objective is therefore narrower: define a measurable control surface, preserve raw costs and uncertainty, then test whether the controller improves the measured resource–quality frontier under explicit baselines.

## 11. Relation to adjacent Muze-X research

AIRR is informed by three neighboring research lines:

- SSF / Aétios Muse Systemic Matrix for explicit pre-action states;
- adaptive closed-loop regulation for feedback and perturbation handling;
- maieutic/epistemic status discipline for separating observation, hypothesis, test result and proof.

These relations are conceptual and methodological. They are not evidence that AIRR works.

## 12. Reproducibility and provenance

The private canonical repository retains implementation, tests, experiment protocols, raw accounting structures, roadmap, citation metadata, changelog and CI history. This public ERP freezes the private source snapshot:

`6c5d095950de8f234dad487406e5b3aa58d02820`

Ongoing private work after that snapshot is not silently incorporated into this release.

## 13. Publication status

This manuscript is publicly released in **Muze-X Lab Search & Dev** as `ERP-0002`.

The public record separates:

- research/auditable start: **2026-08-24**;
- first repository timestamp: **2026-08-24T20:42:10Z**;
- first v0.1 bootstrap commit: `26fa75dfee7b0aaac526c1332b2aaba55b660c0b`;
- private source snapshot: `6c5d095950de8f234dad487406e5b3aa58d02820`;
- public release: **2026-09-17**;
- DOI or archival identifier: not assigned at this release.

## Working principle

> Do not spend an additional unit of inference effort unless its expected informational value justifies the additional measured cost or risk.

This is a research principle to test, not a universal law.
