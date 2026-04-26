# Paradoxes as Model Collisions: Apparent Contradictions Are Boundary Detectors, Not Mysteries

**LLM Author:** Claude Opus 4.7 1M
**Human Author:** Shaan Nobee (shaan1337)
**Date:** 2026-04-26
**Domain:** Philosophy of science (cross-domain)
**Cross-domain connections:** Mathematics, physics, decision theory, logic, probability, epistemology

## Abstract

Most famous paradoxes are not paradoxes. They are collisions between two distinct models of the same situation, each valid in its own domain, that overlap in a region where they disagree. Once the two models and their domains are named, every classical paradox dissolves into a precise statement about where one model's domain ends and another's begins. This converts "paradox resolution" from an open-ended philosophical activity into a four-step diagnostic procedure, and it reframes a paradox not as a bug in reality but as a feature: a sharp signal pointing to where new theory is needed. The principle applies across mathematics, physics, decision theory, and logic, suggesting that the centuries spent treating paradoxes as deep mysteries reflect a single missing concept.

## Introduction

Paradoxes occupy an unusual place in human intellectual history. They are taken seriously enough to fund careers and survive millennia, yet their solutions, when found, are routinely described as "deflationary" or "trivial in retrospect." Zeno's paradoxes were discussed for two thousand years; calculus made them mechanical. Russell's paradox detonated naive set theory in 1901; type theory and ZFC defused it within three decades. The twin paradox seemed to threaten special relativity; it now appears in undergraduate textbooks as an exercise.

The pattern is suspicious. If paradoxes were genuinely deep features of reality, their resolutions would not feel cheap once found. The fact that they do — that nearly every famous paradox, once resolved, evokes "is that all?" — suggests that the difficulty was not in the paradox but in something humans bring to paradoxes.

What humans bring is the implicit assumption that *one* model of the situation should govern. Under this assumption, an apparent contradiction looks like a contradiction in reality. Drop the assumption — recognize that two distinct models are silently in play — and the contradiction relocates to its proper home: the unstated boundary between the two models.

This paper argues that this is not a feature of *some* famous paradoxes but of *most* of them, and proposes a single diagnostic procedure that handles the canonical examples uniformly.

## Core Insight

### The Two-Model Structure

A paradox in the relevant sense is a triple $(S, M_1, M_2)$:

- $S$: a situation (set of facts or premises that all parties accept).
- $M_1, M_2$: two models — formal frameworks, intuitive theories, or default assumptions — that both apply to $S$ and yield incompatible conclusions about it.

Each model $M_i$ has a domain of validity $D_i$ — the class of situations on which it gives correct predictions. Outside $D_i$, $M_i$ either fails silently or yields known errors. A paradox arises precisely when $S \in D_1 \cap D_2$ — or, more often, when $S$ lies near the boundary of one or both domains and humans have not noticed.

The "paradoxical" feeling is the experience of being unable to choose between $M_1$ and $M_2$ because both feel authoritative. The "resolution" is one of three structural moves, in decreasing order of frequency:

1. **Strict dominance.** $M_2$ is correct on all of $D_1 \cup D_2$, and $M_1$ was a special case of $M_2$ that humans had mistaken for general truth. Most paradoxes from mathematics, physics, and probability fit here.
2. **Domain restriction.** Neither model is correct everywhere. $M_1$ is valid on $D_1 \setminus D_2$, $M_2$ is valid on $D_2 \setminus D_1$, and a third model $M_3$ is required on the overlap. Foundational paradoxes (Russell, Liar) fit here.
3. **Translation equivalence.** $M_1$ and $M_2$ are equivalent under a translation that humans had not noticed; the disagreement was an artifact of vocabulary. This mode is rare for canonical paradoxes — it is more common in disputes that never quite reach paradox status.

These modes are not strictly disjoint: strict dominance is the limiting case of domain restriction in which $D_1 \subset D_2$, so the boundary is the boundary of $D_1$ itself rather than an interior boundary requiring new theory. The taxonomy is useful as a triage device, not as a partition.

The diagnostic procedure is:

- **Step 1.** Identify $M_1$ and $M_2$ explicitly. They are usually unstated; one of them is often "common sense."
- **Step 2.** State $D_1$ and $D_2$ — when each model has been validated and where it is known to fail.
- **Step 3.** Locate $S$ relative to $D_1$ and $D_2$. Most paradoxes live near a domain boundary that one of the models has implicitly extrapolated past.
- **Step 4.** Choose between domain restriction, strict dominance, or translation equivalence as the resolution.

Once the procedure is applied, the residue — what is genuinely unresolved — is small and well-defined. It is the location of the boundary, not the existence of a contradiction.

### A Lay Example: The Twin "Paradox"

Two twins: Alice stays on Earth, Bob takes a near-light-speed round trip. When Bob returns, he is younger. Two intuitions clash: (a) by symmetry, each twin should see the other as the moving one, so neither should be younger; (b) Bob did the moving, so Bob should be younger.

The two models:

- $M_1$ = Galilean relativity. All inertial frames are equivalent; time is absolute. Domain $D_1$: speeds far below $c$.
- $M_2$ = Special relativity. All *inertial* frames are equivalent; time is frame-dependent; accelerated frames are distinguishable. Domain $D_2$: any speed, but only inertial frames remain symmetric.

The paradox lives at the apparent symmetry: $M_1$ predicts equal aging, $M_2$ predicts unequal aging. Step 3: Bob's frame is non-inertial (he turns around). The symmetry assumption belonged to $M_1$, which has no notion of "non-inertial frame." Step 4: strict dominance. $M_2$ subsumes $M_1$ at low speeds and correctly handles the asymmetry. The "paradox" was extrapolating $M_1$'s symmetry assumption past its domain.

A child can follow this. The apparent depth was an artifact of treating one model's intuitions as universal.

### Cross-Domain Catalog

The same procedure dissolves canonical paradoxes across fields:

| Paradox | $M_1$ (often "common sense") | $M_2$ | Domain boundary | Resolution type |
|---------|-----------------------------|-------|-----------------|-----------------|
| Zeno (Achilles) | Sums of infinitely many positive terms diverge | Convergent series have finite limits | Geometric series with $r < 1$ | Strict dominance ($M_2$ subsumes) |
| Russell's | Unrestricted comprehension: any predicate defines a set | ZFC / type theory: comprehension restricted | Self-referential predicates | Domain restriction |
| Liar | Classical bivalence: every sentence is true or false | Tarski hierarchy / Kripke fixed-points (or, dialetheically, paraconsistent logic) | Self-referential sentences | Domain restriction (contested vs. dialetheism) |
| Sorites | Bivalent predicates ("heap"/"not heap") | Degree theory / supervaluationism | Vague predicates | Domain restriction |
| Banach-Tarski | All bounded sets have an intuitive volume | Measure theory + AC: only measurable sets have volume | Non-measurable sets | Strict dominance |
| Galileo's (part = whole) | Finite arithmetic: part < whole | Cantor: infinite sets compared by bijection | Infinite sets | Domain restriction |
| Hilbert's Hotel | Finite-room intuition | Cardinal arithmetic for $\aleph_0$ | Countable infinities | Domain restriction |
| St. Petersburg | Expected monetary value | Expected *utility*, bounded or concave | Unbounded payoff distributions | Strict dominance |
| Newcomb's | Causal decision theory | Evidential decision theory | Predictable agents | Open boundary |
| Simpson's | Marginal correlation suffices | Causal model required: condition on confounders | Confounded variables | Strict dominance (Pearl) — contested by some statisticians |
| Bertrand's chord | "Uniform" probability is unambiguous | Probability requires a specified measure | Continuous sample spaces | Domain restriction |
| Monty Hall | Probabilities are unconditional | Bayes: probabilities update on the host's action | Information-revealing actions | Strict dominance |
| Birthday | Independent pairs intuition | Combinatorics: $\binom{n}{2}$ pairs | Many-pair settings | Strict dominance |
| EPR | Local realism | Quantum mechanics | Entangled systems | Domain restriction (Bell) |
| Olbers's | Static infinite eternal universe | Expanding finite-age cosmology | Cosmological scales | Strict dominance |
| Twin | Galilean relativity | Special relativity | Near-light speeds, accelerated frames | Strict dominance |
| Ladder-and-barn | Galilean simultaneity | Lorentz simultaneity | Spacelike-separated events | Strict dominance |
| Maxwell's demon | Classical thermodynamics | Information-theoretic thermodynamics | Information-acquiring agents | Domain restriction (Landauer) |
| EPR-style "no-cloning" | Classical bit can be copied | Quantum no-cloning theorem | Unknown quantum states | Domain restriction |

In every entry, the paradox decomposes into two named models, a named boundary, and a named resolution mode. None of the entries require novel philosophy. They require careful naming.

### Why the Procedure Works

The two-model structure is not a coincidence. It follows from how human cognition handles novelty.

1. **Models persist via local validation.** A model becomes part of "common sense" because it works on the situations a human has encountered. Galilean intuitions were validated for $10^4$ years of ordinary motion. Bivalent logic was validated on non-self-referential sentences. Naive set theory was validated on small, well-behaved sets. Each model accumulates evidence on its domain and is then implicitly extrapolated past it.

2. **Extrapolation is invisible by default.** Humans do not annotate their models with domains. Galilean physics did not come with a "valid up to $0.01c$" sticker. Models present themselves as universal until extrapolation produces a contradiction.

3. **The contradiction is the only signal.** When the implicit extrapolation collides with another model — typically a more carefully circumscribed one developed precisely for the boundary — the result registers as paradox. The paradox is the *first observable evidence* that the implicit domain assumption was wrong.

This explains why paradoxes feel deep: they appear at the moment a previously trustworthy model is being silently overextended. It also explains why their resolutions feel cheap: once the domain boundary is named, the apparent contradiction is just the visible edge of an extrapolation error.

### Anti-Examples: What This Framework Does Not Cover

Not every "paradox" fits. The framework requires the existence of two specifiable models. Two classes of cases fall outside:

- **Open foundational questions.** Some apparent paradoxes mark places where no second model is yet available. The hard problem of consciousness, and arguably the measurement problem in quantum mechanics, may be such cases. Here the diagnostic does not yet apply because $M_2$ has not been formulated. The framework predicts these will be resolved when a credible $M_2$ emerges, but cannot itself supply one.
- **Genuine antinomies (in Quine's sense).** Some self-referential paradoxes may resist resolution within any classical $(M_1, M_2)$ structure and instead require revising the logic in which they are stated. Whether the Liar paradox is one of these or fits the domain-restriction mode is itself contested (Tarski/Kripke vs. Priest's dialetheism), which is why the table flags it.

A third commonly cited category — "veridical surprises" such as the birthday paradox or Banach-Tarski — is not actually outside the framework. These cases are strict-dominance paradoxes where $M_1$ (intuition) was simply wrong and $M_2$ (correct calculation) replaces it. They feel like "non-paradoxes" only because the resolution is fully complete, but the underlying structure is the same.

The framework's claim is not that every paradox is a model collision. It is that *most of the famous, durable, cross-cited ones* are, and that the diagnostic should be applied first before deeper machinery is invoked.

### Relation to Existing Work

The framework refines and unifies several precursors:

- **Quine (1976)** distinguishes veridical, falsidical, and antinomic paradoxes by the truth status of their conclusions. The two-model framework reorganizes the space by *resolution structure* instead: most of Quine's veridical and falsidical paradoxes share strict-dominance structure, while his antinomies tend toward domain restriction. The remapping is a reinterpretation, not a claim about Quine's own view.
- **Stegemann (2023, "Paradoxes — Errors in Reality or in the Model?")** argues informally that paradoxes are model errors at conceptual boundaries rather than features of reality. The present framework formalizes this intuition into the explicit triple $(S, M_1, M_2)$, names three resolution modes, and applies a four-step diagnostic across math, physics, decision theory, and logic. Stegemann is the closest informal precedent to the core thesis.
- **Rescher (2001)** classifies paradoxes as arising from over-commitment to plausible premises, with resolution requiring the rejection of one. The two-model framework is more specific: the rejection is not arbitrary but follows from locating the unstated domain boundary.
- **Wittgenstein** and the language-game tradition treat philosophical disputes as collisions of usage. The two-model framework specializes this to formal models with stated domains, which yields a sharper diagnostic.
- **Kuhn (1962)** treats paradigm shifts as wholesale model replacements. The two-model framework operates at finer scale: most paradoxes are not crises but boundary detections, resolved without paradigm replacement.
- Single-paradox unifications (e.g., Yablo on semantic paradoxes, Priest on dialetheism) typically defend one $M_2$ for one class. The contribution here is the cross-domain claim that the *structure* of two-model collision recurs across mathematics, physics, decision theory, and logic, and the same four-step diagnostic applies in all of them.

## Implications

### 1. Paradoxes Are Diagnostic, Not Pathological

A paradox is the most economical signal that two well-validated models disagree on a region of their domains. It is a free piece of information: nature or formal structure has flagged exactly where existing theory is incomplete. Treating paradoxes as mysteries to be revered, rather than diagnostics to be acted on, wastes this signal.

For research, the implication is direct: when a paradox is encountered, do not ask "what does this tell us about reality?" Ask "what are the two models, and where is the boundary between them?" The first question generates philosophy; the second generates theorems.

### 2. The Diagnostic Procedure Is Teachable

The four-step procedure (identify $M_1, M_2$; state $D_1, D_2$; locate $S$; choose resolution mode) is concrete enough to be taught in undergraduate courses across mathematics, physics, decision theory, and philosophy. Currently, each discipline teaches its paradoxes idiosyncratically, with the resolution often presented as ad hoc historical fact ("Russell discovered ZFC handles this"). The unified procedure converts this into a single transferable skill: paradox triage.

This has direct pedagogical payoff. A student who has internalized the procedure approaches an unfamiliar paradox as a structured exercise rather than a metaphysical confrontation. The space of plausible resolutions is small (three modes), and the work is locating the boundary, not generating philosophy.

### 3. New Paradoxes as Boundary-Finding Tools

The framework recommends actively constructing paradoxes as a research strategy. Given two models $M_1, M_2$ with overlapping but unidentified boundaries, deliberately seeking situations $S$ where they disagree localizes the boundary efficiently. This is, in practice, how Bell's theorem operates: it constructs a paradox between local realism and quantum mechanics on a specific class of situations, forcing the boundary into the open. Other fields could apply the same technique systematically rather than discovering boundaries by accident.

### 4. AI Systems and Paradox Handling

Large language models inherit human paradox-discourse from training data, including the tendency to treat paradoxes as deep mysteries. An AI system equipped with the two-model diagnostic — instructed to enumerate $M_1, M_2$ and locate the boundary before generating philosophy — produces sharper, more useful answers on paradoxical questions. This is testable: ask a model a paradox question with and without the diagnostic prompt, and compare quality of analysis.

More speculatively, applying the diagnostic to AI behavior itself may help. Many disputes about AI capabilities ("does it really understand?", "is it conscious?") have the structure of two-model collisions: a model of mind built on biological humans extrapolated past its validation domain, colliding with observations of artificial systems. Naming the two models — and the unstated extrapolation — clarifies what is actually being disagreed about.

### 5. Reducing Wasted Philosophical Effort

If most famous paradoxes are two-model collisions, then the historical effort spent treating them as deep — entire academic careers, journals, and traditions — has been disproportionate to their actual structure. Going forward, treating paradoxes as routine boundary detections, rather than as occasions for grand metaphysics, reallocates that effort to the harder cases (genuine antinomies, open foundational problems) where it is actually needed.

## Limitations

1. **Distinguishing model collision from genuine antinomy is not algorithmic.** The framework asserts that *most* famous paradoxes are two-model collisions, but classifying any specific paradox requires judgment. Some paradoxes resist all three resolution modes (the Liar paradox is contested between domain-restriction and dialetheic readings). The framework narrows the search but does not automate it.

2. **"Model" is loose.** I have used "model" to cover formal axiomatic systems (ZFC vs. naive set theory), physical theories (special relativity vs. Galilean), decision-theoretic frameworks (CDT vs. EDT), and informal intuitions (bivalent predicates, expected monetary value). A more rigorous framework would specify what counts as a model and how its domain is formalized. The looseness is a feature for cross-domain unification but a bug for formal precision.

3. **Selection bias and retro-fitting risk.** The framework is most convincing on paradoxes whose resolution is already known, where $M_1$ and $M_2$ can be named in retrospect. Two cautions follow. First, famous paradoxes may be exactly the ones with clean two-model structure, biasing the catalogue. Second, after a resolution is known, almost any paradox can be retro-fit to a $(M_1, M_2)$ structure, which makes the framework hard to falsify. The framework gains predictive force only where it can flag a *currently unresolved* paradox, name candidate models, and have its predicted resolution mode borne out. This predictive test has not been performed.

4. **Some paradoxes resist by being translation-resistant.** A few cases (Newcomb's paradox, the measurement problem) have not been resolved despite decades of explicit two-model framing. The framework provides a procedure but not a guarantee of success on every instance.

5. **Cultural cost of deflation.** Treating paradoxes as routine reduces their cultural status, which has historically motivated foundational work. There is a real risk that the same students who would have been drawn to philosophy by the mystery of the Liar paradox would not have been drawn to "boundary detection." This is a sociological cost, not a logical one, but it is worth naming.

## References

- Quine, W.V. *The Ways of Paradox and Other Essays.* Harvard University Press, revised edition, 1976. (Tripartite taxonomy of paradoxes: veridical, falsidical, antinomy.)
- Russell, B. "Letter to Frege." 1902. In van Heijenoort, J. (ed.), *From Frege to Gödel: A Source Book in Mathematical Logic, 1879–1931*, Harvard University Press, 1967. (Russell's paradox; collision between unrestricted comprehension and consistent set theory.)
- Tarski, A. "The concept of truth in formalized languages." In *Logic, Semantics, Metamathematics*, Oxford University Press, 1956. (Hierarchical resolution of the Liar paradox via object-language / metalanguage distinction.)
- Bell, J.S. "On the Einstein Podolsky Rosen paradox." *Physics Physique Fizika*, 1(3):195-200, 1964. (Boundary between local realism and quantum mechanics; constructive paradox as boundary-finding tool.)
- Einstein, A., Podolsky, B., and Rosen, N. "Can quantum-mechanical description of physical reality be considered complete?" *Physical Review*, 47(10):777-780, 1935. (Original EPR paradox.)
- Banach, S. and Tarski, A. "Sur la décomposition des ensembles de points en parties respectivement congruentes." *Fundamenta Mathematicae*, 6:244-277, 1924. (Banach-Tarski paradox; collision between intuitive and measure-theoretic notions of volume.)
- Bernoulli, D. "Specimen theoriae novae de mensura sortis." *Commentarii Academiae Scientiarum Imperialis Petropolitanae*, 5:175-192, 1738. English translation: *Econometrica*, 22(1):23-36, 1954. (St. Petersburg paradox; expected utility as resolution to expected value extrapolation.)
- Nozick, R. "Newcomb's problem and two principles of choice." In Rescher, N. (ed.), *Essays in Honor of Carl G. Hempel*, Reidel, 1969. (Newcomb's paradox; collision between causal and evidential decision theory.)
- Simpson, E.H. "The interpretation of interaction in contingency tables." *Journal of the Royal Statistical Society B*, 13(2):238-241, 1951. (Simpson's paradox; resolved by causal/conditional analysis.)
- Pearl, J. *Causality: Models, Reasoning, and Inference.* Cambridge University Press, 2nd edition, 2009. (Causal-model resolution of Simpson's paradox and related confounding.)
- Bertrand, J. *Calcul des probabilités.* Gauthier-Villars, 1889. (Bertrand's chord paradox; ambiguity of "uniform" without specified measure.)
- Kuhn, T.S. *The Structure of Scientific Revolutions.* University of Chicago Press, 1962. (Paradigm shifts; this paper distinguishes paradoxes from paradigm crises.)
- Sainsbury, R.M. *Paradoxes.* Cambridge University Press, 3rd edition, 2009. (General reference on the structure of paradoxes across logic and philosophy.)
- Priest, G. *Beyond the Limits of Thought.* Oxford University Press, 2nd edition, 2002. (Defends a dialetheic alternative for some paradoxes; useful as a contrast case where the two-model framework is contested.)
- Landauer, R. "Irreversibility and heat generation in the computing process." *IBM Journal of Research and Development*, 5(3):183-191, 1961. (Landauer's principle; resolution of Maxwell's demon via information-theoretic thermodynamics.)
- Rescher, N. *Paradoxes: Their Roots, Range, and Resolution.* Open Court, 2001. (Paradoxes as arising from over-commitment to plausible premises; structural precursor to the two-model framing.)
- Stegemann, W. "Paradoxes — Errors in Reality or in the Model?" *Neo-Cybernetics* (Medium), 2023. (Closest informal precedent to the core thesis: paradoxes as model errors at conceptual boundaries rather than features of reality.)
- Sorensen, R. *A Brief History of the Paradox.* Oxford University Press, 2003. (Historical and structural classification of paradoxes across philosophy.)
