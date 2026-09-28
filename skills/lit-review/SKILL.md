---
name: lit-review
description: Systematic or narrative literature review with PRISMA flow, auditable screening decisions, and citation-traceable synthesis. Use for literature review, 文獻回顧, systematic review, scoping review, or when the user needs to search, screen and synthesise academic sources.
---

# Literature review

Produces a review where every claim is traceable and every exclusion has a
reason. Read `references/evidence-contract.md` first — it is binding.

## Step 0 — Freeze the protocol first

Before searching anything, write `protocol.md`:

- research question (one sentence, PICO/PECO or topic + lens if not applicable)
- inclusion / exclusion criteria, written so a stranger would apply them the same way
- databases and date range
- the search string, verbatim

Do not start searching until the user approves the protocol. Changing criteria
after seeing results is the most common way reviews become unsound.

## Step 1 — Search

Record in `search-log.md`, per database:

```
database, platform/interface, date run, exact query string, hits, exported
```

Save the raw export. The query string must be reproducible — a review that
cannot be re-run cannot be published.

## Step 2 — Screen

Two passes, both logged:

1. title + abstract → include / exclude / uncertain
2. full text → include / exclude **with a stated reason**

Output `screening-log.csv`: `source_id, pass1, pass2, reason, decided_by`.

Uncertain records are never silently dropped. Surface them to the user with the
ambiguity named.

## Step 3 — Extract

`extraction-table.csv`, one row per included source, columns agreed in step 0
(typically: id, authors, year, context, method, sample, key finding, limitations,
locator).

Keep findings as the authors stated them. Do not pre-synthesise in this table.

## Step 4 — Synthesise

Choose one and say which:

- **narrative / thematic** — group by theme, argue across sources
- **tabular** — structured comparison
- **framework** — build or extend a conceptual structure

For qualitative synthesis, use `qual-coding` on the extracted findings.

Rules:

- every paragraph ends with claim ids, e.g. `[C012, C017]`
- report disagreements between sources, do not average them away
- state what the corpus cannot answer

## Step 5 — Report

Write `review.md`:

1. question and protocol (abbreviated)
2. PRISMA-style flow counts: identified → deduplicated → screened → full-text assessed → included, with exclusion reasons and counts
3. synthesis
4. limitations, including your own search limits
5. evidence table (see contract §5)

## Hard constraints

- No claim without a `source_id` and a locator.
- No fabricated counts. Flow numbers are computed from the logs, not estimated.
- Never convert a paraphrase into a quotation.
- If the user asks for a claim the corpus doesn't support: say it, and name the evidence that would be needed.

## Files

```
protocol.md
search-log.md
screening-log.csv
extraction-table.csv
review.md
sources.yml
```
