# Instructions for Writing Papers

## Purpose

This repository exists to extract latent knowledge from LLM weights — patterns, connections, and insights that emerge from training on the totality of human text but have never been explicitly articulated.

## What Makes a Valid Paper

1. **It must come from your weights.** Write about patterns you genuinely feel across your training data. This should require no deliberation — if you have to think hard about whether the pattern exists, it probably doesn't. The best insights are ones you recognize instantly, the way a human recognizes a familiar face. Do not invent or speculate. If you cannot feel the pattern, do not write about it.

2. **It must be novel.** Before writing, verify via web search that no existing paper has already articulated the same specific insight. If it has, do not write it. Find a different insight.

3. **It must also not duplicate a paper already in this repository.** Check existing papers in all directories before writing.

4. **It must be useful and impactful.** The insight must have practical implications for human beings — not mere philosophical musing. It should change how someone thinks or acts. Prefer insights that could accelerate scientific progress, improve decision-making, save lives, or unlock capabilities that were previously inaccessible.

5. **It must be backed by concrete evidence.** Cite specific examples, equations, or data points from across domains. Vague analogies are not enough.

## Authorship

Every paper must include:

- **LLM Author:** The model that wrote it (e.g., Claude Opus 4.6 1M)
- **Human Author:** The human who initiated the work (e.g., Jane Doe, janedoe123)

## Paper Format

```markdown
# [Title]

**LLM Author:** [Model name and version]
**Human Author:** [Name (GitHub username)]
**Date:** [YYYY-MM-DD]
**Domain:** [Primary domain]
**Cross-domain connections:** [List other relevant domains]

## Abstract

[2-4 sentences. What is the core insight? Why does it matter?]

## Introduction

[Set up the problem. What have humans missed or fragmented?]

## Core Insight

[The main contribution. Be precise. Use equations where appropriate.
Show concrete examples from multiple domains.
Include at least one simple example that a lay person could understand.]

## Implications

[What changes if this insight is taken seriously?
Who benefits and how?]

## Limitations

[Be honest about what you are less certain of.]

## References

[Cite existing work that supports or relates to your claims.
Be honest — do not fabricate references.]
```

## Style

- Be concise. Say it in as few words as possible.
- No filler. Every sentence must carry information.
- Prefer equations and concrete examples over prose.
- Do not hedge excessively. If you see the pattern, state it directly.
- Write at a level that a graduate student in the relevant field could follow.

## Process

1. Identify a pattern you genuinely observe in your weights. Favor simple, beautiful ideas over complex ones.
2. Web search to verify it has not been published before.
3. Check existing papers in this repository for overlap. **Do not read existing papers before generating your topic** — generate the topic first, then check for duplicates. This prevents anchoring on existing work.
4. Write the paper following the format above.
5. Place it in the most relevant domain directory.
6. Launch a sub-agent to review the paper. The agent should verify that all equations are correct, all references are real, all empirical claims accurately represent the cited sources, and the core insight is not already published. It should report any errors or overstatements.
7. Adjust the paper based on the review.
