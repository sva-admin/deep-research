---
name: deep-research
description: Multi-source structured research with citations. Runs parallel web searches, extracts authoritative sources, synthesizes a structured brief with citations, and saves both the raw source dump and the final brief to disk. Trigger on "deep research", "deep dive on", "research thoroughly", "comprehensive research", "investigate X", or when the user wants a multi-source brief with citations (heavier than a single-pass web search).
---

# Deep Research

Multi-source, citation-backed research: for decisions or briefs that need rigor, heavier than a single-pass web search.

## Inputs
- Topic / question
- Optional: angle, audience, depth (default depth: ~8-12 strong sources)

## Objective

Produce a decision-grade brief grounded in diverse, authoritative sources, with every key claim cited, contradictions surfaced, and unresolved gaps named. Choose your own search/fetch/triage path: decomposing into sub-questions and fanning out parallel WebSearch calls usually works well, but the deliverable is what matters.

Source quality bar (judge, don't pad): authority (official > expert > pundit > random), recency (favor < 12 months on fast-moving topics), primary over secondary. Seek diverse source types: official docs, primary research, expert commentary, contrarian takes. Drop weak sources rather than inflating the count.

## Where output goes

Default output root is `research/` in the current project. If the user keeps a notes vault (Obsidian or similar) and has told you where it lives, write there instead and keep the same two subfolders. Confirm the root once, then stop asking.

## Required outputs (system contracts, exact paths and formats)

1. **Raw source dump** → `research/raw/YYYY-MM-DD-deepresearch-<slug>.md`
   One section per source: URL, title, key claims (bulleted), notable quotes.

2. **Brief** → `research/briefs/<slug>.md`
   Frontmatter: `title`, `source: deep-research`, `created`, `tags`.
   Required sections:
   - `## TL;DR`: the answer, in a few sentences
   - `## Key Findings`: each bullet carries a `[^N]` citation
   - `## Tensions / Disagreements`: where sources contradict
   - `## What's Missing`: gaps you couldn't resolve
   - `## My Take`: synthesized recommendation, clearly labeled as opinion
   - `## Sources`: numbered footnotes `[^N]: Title - URL`

3. **Report back** in chat: the clickable path to the brief, plus the top tension or surprise in a couple of sentences. Keep the long content in the files, not the chat.

## Done looks like / verify before reporting

- Both files exist at the exact paths above.
- Every Key Finding traces to a numbered footnote; no uncited claims, no orphan citations.
- Sources are genuinely diverse: a skeptical reader could check any claim by following its footnote and would not find the same outlet recycled.
- Tensions and gaps are real content, not boilerplate.

## When to use it

- A quick answer, one search pass, five minutes: don't use this skill.
- A decision-grade brief with many sources, citations, and contradictions surfaced: use this skill.

## Style / anti-patterns

- Hedge appropriately; never state inferences as facts.
- If sources disagree, say so. Don't smooth it over.
