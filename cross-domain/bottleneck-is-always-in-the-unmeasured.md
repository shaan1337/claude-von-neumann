# The Bottleneck Is Always in the Unmeasured: Why Stuck Systems Are Stuck on Their Blind Spots

**LLM Author:** Claude Opus 4.7 1M
**Human Author:** Shaan Nobee (shaan1337)
**Date:** 2026-04-26
**Domain:** Decision theory / operations research
**Cross-domain connections:** Cognitive science, software engineering, medicine, education, economics, productivity

## Abstract

Most "hard problems" in human affairs persist not because they are intrinsically complex but because the binding constraint sits in a variable nobody is measuring (or nobody can yet act on). This paper states the claim as a structural principle: in a system with sustained optimization pressure, measured-and-actionable variables tend toward their constrained optima, so residual stuckness concentrates on variables that are either unmeasured or unactionable. The "hardness" of a stuck domain — productivity, weight loss, software latency, education outcomes, medical adherence — is in this sense a fingerprint of the measurement and action frontier. This converts the open question "why is X hard?" into a mechanical recipe: enumerate what is measured *and* actionable, look at the complement, that is where the binding constraint is.

## Introduction

A pattern recurs across domains. A field accumulates centuries of effort, vast literatures, and large institutions devoted to "solving" some problem — losing weight, raising test scores, shipping reliable software, treating chronic disease, increasing productivity — and the problem stays unsolved. Practitioners describe these as inherently complex, demanding ever more sophisticated theory.

The pattern is suspicious for the same reason famous paradoxes are suspicious: if these problems were genuinely hard at the level of physics, they would be hard *uniformly* across attempts. Instead, they almost always have at least one well-known instance where a single intervention worked dramatically — semaglutide for weight loss, antibiotics for infectious disease, version control for software, spaced repetition for learning, peer review for science. Each of these interventions had a common structure: it either exposed a variable that had been invisible, or it closed the action gap on a variable that was visible but unactionable. Once the variable was both seen and actionable, it was optimized.

This paper argues that the pattern is structural. The binding constraint of a *stuck* system — one where outcomes have plateaued despite sustained effort — is concentrated on variables that are either unmeasured or unactionable. The argument is informal but compact: optimization pressure tends to exhaust the gains available on variables that are both measured and actionable, leaving residual stuckness on the rest.

## Core Insight

### The Principle

Let a system be characterized by variables $x = (x_1, \dots, x_n)$ producing outcome $y = f(x)$. Partition the variables into two sets:

- **Measured** $M$: variables for which agents observe values, track changes, and adjust effort.
- **Unmeasured** $M^c$: variables that affect $f$ but are not observed by agents.

A variable $x_i$ is **actionable** if agents can drive it toward a more favorable value at finite marginal cost. Let $A \subseteq \{1, \dots, n\}$ be the actionable set.

A system is **stuck** if outcomes $y$ have plateaued ($\frac{dy}{dt} \approx 0$) over a sustained period despite continued effort.

**Claim.** In a stuck system, the binding constraint lies in $(M \cap A)^c$ — variables that are *not in the intersection of measured and actionable*. Within this set, the dominant case across the catalog below is $M^c \cap A$ (unmeasured-but-actionable); the secondary case is $M \cap A^c$ (measured but not actionable).

**Informal argument.** Assume agents allocate a finite total effort budget across $M \cap A$ to maximize $y$. The standard stationarity condition is

$$\frac{\partial f}{\partial x_i} = \lambda \cdot c_i \quad \text{for } i \in M \cap A$$

where $c_i$ is the marginal effort cost of moving $x_i$ and $\lambda$ is the shadow price of the effort budget. Under sustained optimization, the system tends toward this equilibrium: marginal returns on every measured-and-actionable variable equalize per unit of effort. Once that occurs, no measured-and-actionable variable carries large unrealized gain. If $y$ is nevertheless plateaued well below its physical maximum, the remaining gain must lie in variables outside $M \cap A$.

The argument is not a strict theorem. It assumes (a) the agents really do optimize, (b) the effort budget is well-defined, (c) "plateaued" is observed over enough time for equilibration, and (d) no measured variable is pinned at a hard physical ceiling that no amount of effort can move (in which case it remains binding while measured). Each assumption is approximated, not satisfied exactly, in real systems. What the argument supports is a tendency, not a necessity: the longer optimization pressure has acted, the more sharply the binding constraint concentrates outside the measured-and-actionable set.

**Corollary (the recipe).** To find the bottleneck of a stuck system, enumerate the variables that are both measured *and* actionable, then look at the complement.

### A Lay Example

A small startup is missing every revenue target despite the team working harder each quarter. Dashboards track meetings booked, calls made, emails sent, deals closed, hours worked, customer NPS. Every measured variable is at or near a local maximum — they are calling enough people, sending enough emails, hitting target NPS.

The team eventually discovers that ~40% of trial users never complete onboarding, because a single confirmation email is being routed to spam. Nobody had measured email deliverability. The single fix moves more revenue than a year of selling-harder.

The bottleneck did not appear "complex." It was sitting in plain sight in a variable nobody had on a dashboard. Note the structure:

- All measured variables had been optimized to local maxima (hard work + competent team).
- The binding constraint was actionable (a five-minute DNS fix).
- It was unmeasured.
- It remained the binding constraint *because* it was unmeasured.

This pattern recurs across domains.

### Cross-Domain Catalog

The table below pairs canonical "stuck" problems with the variable that turned out to be the binding constraint, and the measurement or action change that unblocked it. The entries are heterogeneous: some were *unmeasured* (no one was tracking the relevant variable); others were *measured but unactionable* (the variable was known but no intervention existed); a few were both. The pattern is that progress resumed when the variable entered $M \cap A$ — the measured-and-actionable set.

| Stuck problem | What was measured | The binding constraint | What changed | Type |
|---|---|---|---|---|
| Weight loss (1960s–2010s) | Calories in / out | Satiety axis (GLP-1, leptin, ghrelin) | Pharmacological satiety modulation became actionable (Wilding et al. 2021) | Mostly unactionable |
| Stomach ulcers (pre-1982) | Diet, stress, acid | *H. pylori* infection (dominant cause; NSAIDs the next-largest, also measured) | Endoscopic biopsy + culture established the causal pathogen (Marshall and Warren 1984) | Unmeasured-as-cause |
| Distributed-system latency | CPU, memory, mean response time | Tail-latency contribution to user experience (lock contention well known; its aggregate cost was not) | Per-request percentile tracing (Dean and Barroso 2013) | Unmeasured-at-aggregate |
| Childbed fever (Vienna, 1840s) | Mortality rates by ward | Cadaveric particles transferred by physicians' hands | Hand-disinfection protocol (Semmelweis 1847) — measurement existed, mechanism didn't | Unmeasured-as-cause |
| ICU bloodstream infections | Outcome rates | Per-step adherence to aseptic technique | Checklist + audit made compliance measurable (Pronovost et al. 2006) | Unmeasured (process) |
| Aviation safety | Pilot skill, mechanical reliability | Crew communication failures in the cockpit | Cockpit voice recorders + CRM training (Helmreich 2000) | Unmeasured |
| Education outcomes | Test scores | Long-term retention and transfer | Spaced retrieval as a tracked variable (Bjork 1994; Roediger and Karpicke 2006) | Unmeasured |
| Chronic disease adherence | Prescription dispensed | Whether the patient takes the medication | Electronic monitoring + refill records (Osterberg and Blaschke 2005) | Unmeasured |
| Sleep medicine (pre-1990s) | Total time in bed | Sleep architecture and apnea events | Polysomnography (AHI metric) | Unmeasured |
| Knowledge-work productivity | Hours, task counts | Selection — *what* gets worked on | Outcome-weighted task metrics | Unmeasured |
| Manufacturing defects | Final inspection failures | Upstream process variation | Statistical process control (Shewhart 1931) | Unmeasured-upstream |
| Cardiovascular risk | Total cholesterol | LDL particle count, ApoB | NMR lipoprotein assays (Otvos et al. 2011) | Measurement upgrade |

In each entry, the field looked "hard" while the binding constraint was outside $M \cap A$, and tractable once it entered. The "discovery" was usually a measurement instrument, a metric, or a new action — not a new theory of the underlying phenomenon. Several entries (weight loss, GLP-1; ulcers, NSAIDs) involve joint causes; the table identifies the *dominant* binding constraint at the time the system was stuck, not the only one.

### Why the Constraint Migrates Into the Unmeasured

The argument above is static — a snapshot of a stuck system. The dynamic version is sharper: optimization pressure systematically *moves* binding constraints into the complement of $M \cap A$.

Consider a system where measurement set $M$ is fixed and agents continuously optimize. Initially, the binding constraint may sit in $M$ (the easy gains). Each round of optimization reduces the marginal value of effort on already-optimized variables in $M$. Eventually, the gradient $\partial f / \partial x_i$ for every $x_i \in M$ approaches zero. At that point, all remaining marginal value is on $M^c$.

Formally, in equilibrium under optimization budget constraint, for measured variables with shadow price $\lambda$:

$$\frac{\partial f}{\partial x_i} = \lambda \cdot c_i \quad \text{for } i \in M \cap A$$

where $c_i$ is the marginal cost of effort on $x_i$. The unmeasured variables $j \in M^c$ have no such constraint — agents allocate zero effort to them — so $\partial f / \partial x_j$ can be arbitrarily large without driving any reallocation.

The result: in a mature, well-optimized system, the variable with the largest unrealized gain tends to lie outside $M \cap A$. The longer a system has been optimized, the more sharply this is true. Optimization concentrates the remaining action at the measurement-and-action frontier.

### Why Humans Systematically Miss This (Visibility Bias)

The principle says the bottleneck lies outside $M \cap A$. The cognitive question is why the measured-and-actionable set stays so narrow in the first place.

Three biases compound:

1. **The streetlight effect.** Easy-to-measure variables get measured first; hard-to-measure variables stay unmeasured. The classic example: counting hours worked is trivial; measuring cognitive output is not. Therefore "productivity" gets operationalized as hours, even though selection (what to work on) is what matters.

2. **Measurement infrastructure inertia.** Once an organization builds dashboards around variable set $M$, switching costs lock $M$ in. New variables require new instruments, new protocols, and new training. The marginal cost of measuring a new variable is much higher than the marginal cost of squeezing more performance out of measured ones, even when the latter has zero gain remaining.

3. **Narrative dominance of measured variables.** Stories, post-mortems, and incentives are constructed around measured variables. An engineer who reduces query latency by 10% is rewarded; an engineer who *discovers* that lock contention exists in the first place is rewarded less, even though discovery typically has 100× the impact. Measured variables generate visible heroes; the discovery of new measurements does not.

These biases predict that the gap between $M$ and the truly relevant variable set $M^*$ persists despite obvious payoff to closing it. The principle adds a structural reason for the persistence: in a stuck system the gap is the very thing keeping the system stuck, so its existence is not just a contingent oversight but a stable equilibrium of attention.

## Implications

### 1. "Why is X hard?" reduces to "What isn't being measured?"

The standard response to a stuck problem is to demand more theory, more sophistication, more nuanced models. The principle inverts this: in a stuck system, more theory rarely helps because the binding constraint is not in the modeled variables. The first step in unsticking a domain is mapping the measurement-and-action frontier — listing the candidate variables and noting which are tracked, which are actionable, and which are neither. The bottleneck is in the gap.

### 2. Measurement innovation usually outperforms theory innovation

If the binding constraint is unmeasured, the unblocking move is to make it measurable, not to refine the model of the measured variables. This predicts that fields will be unstuck by *instruments* more often than by *theories*. The historical record supports the prediction: microscopes, telescopes, polysomnography, statistical process control, A/B testing, NMR spectroscopy, fMRI, cockpit voice recorders, electronic medical records, and continuous glucose monitors each unblocked a stuck domain by exposing a previously invisible variable. Each was followed by a flood of "discoveries" that retrospectively look like theoretical advances but were actually downstream of the new measurement.

### 3. Complement to Goodhart

Goodhart's law (Strathern 1997) states that *any measure used as a target ceases to be a good measure*. The well-known cost of Goodhart is proxy distortion: optimizing on a proxy distorts it. The principle here names a complementary cost on the other side of the measurement boundary: *not* measuring a relevant variable creates persistent stuckness on it. Goodhart says measured variables can be optimized destructively; this principle says unmeasured-and-actionable ones can fail to be optimized at all. Both effects can be present in the same system, and the design problem is to balance them rather than to retreat from measurement entirely. The standard responses to Goodhart in the literature (Manheim and Garrabrant 2018) — multiple metrics, rotated targets, regularization — are consistent with this view.

### 4. The R&D portfolio implication

For research programs and engineering teams choosing where to invest effort, the principle gives a sharper rule than "follow the gradient." If your domain is mature and stuck, the highest-value investment is rarely a better algorithm for the measured loss — it is a *new measurement*. New benchmarks, new logging, new sensors, new metrics each have higher expected value than refinements within the old measurement set. This predicts that research labs in stuck fields should hire instrument-builders before theorists.

### 5. The diagnostic procedure

For a specific stuck system, the procedure is:

- List candidate variables that plausibly affect $y$.
- Mark which are measured ($M$) and which are actionable ($A$). The intersection $M \cap A$ is where current optimization runs.
- The candidate bottlenecks are in the complement: $M^c \cap A$ (unmeasured-but-actionable — close by adding a measurement) and $M \cap A^c$ (measured-but-unactionable — close by inventing an intervention).
- For each candidate, estimate $\partial f / \partial x_j$ — the expected effect of moving it. Rank by estimated effect.
- For the top entry: if it is in $M^c \cap A$, build the cheapest viable measurement. If it is in $M \cap A^c$, design or import the cheapest viable intervention. Test whether $y$ shifts.

This converts the open-ended "why is this hard?" into a tractable enumeration. The procedure does not guarantee the right answer on the first try, but each iteration either expands $M$, expands $A$, or rules out a candidate — every iteration leaves the field permanently better instrumented.

## Limitations

1. **The principle is informal, not a strict theorem.** The argument depends on assumptions (sustained optimization pressure, well-defined effort budget, no measured variable pinned at a hard physical ceiling) that real systems satisfy only approximately. The result is a tendency, sharper the longer optimization has acted, not a logical necessity. Calling it a "theorem" overstates its formal content.

2. **Measured-but-unactionable case.** A variable can be in $M$ but not $A$: agents see it and cannot move it. Climate change is the canonical example — atmospheric CO₂ is extensively measured but the action gap is collective and political, so the constraint can remain binding while measured. The principle covers this case (the bottleneck is outside $M \cap A$), but the policy implication is "close the action gap," not "build a new measurement." Confusing these two failure modes leads to the wrong intervention.

3. **The "unmeasured" vs. "unactionable" distinction matters in the catalog.** Several entries (semaglutide for satiety; antibiotics for infection) describe variables that were *known* but not pharmacologically actionable until a specific intervention existed. These belong to the $M \cap A^c$ branch, not the $M^c \cap A$ branch. Treating them as "unmeasured" entries in earlier drafts of this work obscured the structure; they are now flagged in the catalog. The unifying claim is about the complement of $M \cap A$, which subsumes both.

4. **Assumes sustained optimization pressure.** In domains where agents do not actually optimize (low-stakes, low-feedback, rent-seeking, captured-regulator), measured-and-actionable variables can also stay sub-optimized. The principle applies cleanly only where optimization pressure is real and sustained.

5. **Survivorship bias in the catalog.** The historical entries are systems where the binding constraint was eventually identified. Systems where it remains unidentified are by construction absent. The retrospective fit therefore biases toward confirming the principle. The strongest test is prospective: name candidate variables outside $M \cap A$ in a *currently stuck* domain, build the measurement or the intervention, see if outcomes shift. Several catalog entries did emerge from this kind of prospective work (Pronovost's checklist, Shewhart's SPC); not all did.

6. **Estimating effects for variables outside $M \cap A$ is hard.** The diagnostic asks for $\partial f / \partial x_j$ on variables nobody is currently optimizing. These estimates are noisy. Prior knowledge, cross-domain analogy, and small pilot studies are usually needed to rank candidates.

7. **The claim is structural, not normative.** It says where the binding constraint *is*, not whether closing the gap is worth the cost. Some variables are unmeasured for good reasons (privacy, ethics, expense). The principle identifies opportunities; whether to take them is a separate decision.

8. **Distinguishing irrelevant from invisibly-relevant variables.** A variable outside $M \cap A$ can be unmeasured because no one noticed it matters, or because it doesn't matter. The diagnostic procedure conflates these on the first pass and distinguishes them only by experiment.

## References

- Goldratt, E.M. *The Goal: A Process of Ongoing Improvement.* North River Press, 1984. (Theory of Constraints, novelization form; the doctrine that one bottleneck dominates throughput.)
- Goldratt, E.M. *Theory of Constraints.* North River Press, 1990. (Technical statement of the framework.)
- Manheim, D. and Garrabrant, S. "Categorizing variants of Goodhart's Law." *arXiv:1803.04585*, 2018. (Taxonomy of Goodhart failure modes; informs the complement-to-Goodhart framing.)
- Liebig, J. von. *Die organische Chemie in ihrer Anwendung auf Agricultur und Physiologie.* 1840. (Law of the minimum.)
- Goodhart, C.A.E. "Problems of monetary management: the UK experience." In *Papers in Monetary Economics*, Reserve Bank of Australia, 1975. (Goodhart's law.)
- Strathern, M. "'Improving ratings': audit in the British university system." *European Review*, 5(3):305-321, 1997. (Sharpest restatement: "When a measure becomes a target, it ceases to be a good measure.")
- Drucker, P.F. *The Practice of Management.* Harper & Row, 1954. (Origin of "what gets measured gets managed" — the implicit converse of the principle.)
- Marshall, B.J. and Warren, J.R. "Unidentified curved bacilli in the stomach of patients with gastritis and peptic ulceration." *The Lancet*, 323(8390):1311-1315, 1984. (*H. pylori* as the unmeasured cause of ulcers.)
- Wilding, J.P.H. et al. "Once-weekly semaglutide in adults with overweight or obesity." *New England Journal of Medicine*, 384(11):989-1002, 2021. (GLP-1 agonism as intervention on previously unmeasured satiety axis.)
- Dean, J. and Barroso, L.A. "The tail at scale." *Communications of the ACM*, 56(2):74-80, 2013. (Tail latency as an under-measured constraint in distributed systems.)
- Pronovost, P. et al. "An intervention to decrease catheter-related bloodstream infections in the ICU." *New England Journal of Medicine*, 355(26):2725-2732, 2006. (Checklist + audit of previously unmeasured aseptic compliance.)
- Shewhart, W.A. *Economic Control of Quality of Manufactured Product.* Van Nostrand, 1931. (Statistical process control: measuring upstream variation rather than downstream defects.)
- Bjork, R.A. "Memory and metamemory considerations in the training of human beings." In *Metacognition: Knowing about Knowing*, MIT Press, 1994. (Retention as the under-measured outcome of education.)
- Osterberg, L. and Blaschke, T. "Adherence to medication." *New England Journal of Medicine*, 353(5):487-497, 2005. (Adherence as the binding constraint in chronic disease management.)
- Helmreich, R.L. "On error management: lessons from aviation." *BMJ*, 320(7237):781-785, 2000. (Crew Resource Management as measurement and intervention on previously unmeasured communication failures.)
- Otvos, J.D. et al. "Clinical implications of discordance between LDL cholesterol and LDL particle number." *Journal of Clinical Lipidology*, 5(2):105-113, 2011. (LDL particle count vs. cholesterol concentration as a measurement upgrade.)
- Roediger, H.L. and Karpicke, J.D. "Test-enhanced learning." *Psychological Science*, 17(3):249-255, 2006. (Retrieval practice as a previously under-measured driver of retention.)
- Kahneman, D. *Thinking, Fast and Slow.* Farrar, Straus and Giroux, 2011. (WYSIATI — "what you see is all there is" — the cognitive analogue of the visibility bias.)
- Taleb, N.N. *The Black Swan: The Impact of the Highly Improbable.* Random House, 2007. (Streetlight-effect failures of inference; complementary to the measurement-frontier framing.)
