---
name: qual-coding
description: Qualitative coding with an auditable codebook — open, axial and selective coding on interview or transcript data, with anchored quotes and memo trail. Use for 質性編碼, thematic analysis, grounded theory coding, interview analysis, or when the user needs to code transcripts and build a codebook.
---

# Qualitative coding

Turns raw transcripts into a codebook where every code is anchored in real text.
`references/evidence-contract.md` is binding, with one addition: for qualitative
work the **anchor quote is the source of truth**, not the code name.

## Step 0 — Prepare

- Normalise the transcript: one utterance per row, keep speaker labels and timestamps.
- Pseudonymise participants before anything else (`P01`, `T01`). Never write real names, schools or places into outputs.
- Save as `data/transcript.tsv`: `id \t speaker \t timestamp \t text`

If the transcript is machine-generated, flag it: ASR errors are not data. Mark
uncertain segments `[inaudible]` and exclude them from coding.

## Step 1 — Open coding

Work line by line. For each segment either assign an existing code or create one.

A new code needs: `code`, `definition`, `inclusion`, `exclusion`, `example_id`.

Codes must be close to the data in this pass. Do not import a framework yet.

## Step 2 — Axial coding

Group codes into categories, and look for:

- conditions → action/interaction → consequences
- recurring sequences
- negative cases (data that contradicts the emerging pattern)

Negative cases are reported, not discarded.

## Step 3 — Selective coding

Name the core category and state, in one paragraph, how the other categories
relate to it. If no core category is defensible, say so — a review with no
single core category is a valid result.

## Step 4 — Memos

Every category gets a memo: what it is, why it matters, what contradicts it,
what to look for next. Memos are dated and never deleted.

## Outputs

`codebook.md`:

```
### [code name]
- definition:
- inclusion / exclusion:
- segments: n
- anchors: [S012] "..." · [S078] "..."
- memo:
```

`coding-matrix.csv`: `segment_id, speaker, timestamp, codes, memo_id`

## Hard constraints

- **No code without at least one anchor quote.** An unanchored theme is a fabrication.
- Never invent illustrative quotes. If you need an example, pull a real one or leave it blank.
- Report code frequency as counts of segments, not as percentages of "participants who said" unless you actually counted participants.
- Do not claim saturation unless you have coded to the point of no new codes and can show when that happened.
- Inter-coder agreement: if a second coder exists, report the procedure and disagreements. If not, state that coding was single-author.

## Files

```
data/transcript.tsv
codebook.md
coding-matrix.csv
memos/
```
