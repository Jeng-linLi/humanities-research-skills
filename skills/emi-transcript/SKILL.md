---
name: emi-transcript
description: Classroom transcript analysis for EMI and multilingual settings — episode segmentation, language-choice and function annotation, with frequency tables and anonymised output. Use for EMI 課堂語料, classroom discourse, translanguaging analysis, translingual practice, or when the user needs to annotate and quantify classroom talk.
---

# EMI classroom transcript analysis

Annotation engine for classroom talk in English-medium and multilingual
settings. Design goal: the annotation scheme is **explicit and replaceable**, so
the user can swap in their own framework instead of inheriting a black box.

## Step 0 — Ethics gate

Before any analysis:

- participants pseudonymised (`T01` teacher, `S01` student, `P01` participant)
- institution, course and date generalised
- confirm consent covers the analysis being requested

If consent status is unknown, stop and ask. Do not proceed on assumption.

## Step 1 — Segment

Split the transcript into episodes (activity boundaries) and turns.

`segments.tsv`: `segment_id, episode_id, speaker, timestamp_start, timestamp_end, text`

Keep timestamps. Analysis without timing cannot answer questions about sequence
or amount of talk.

## Step 2 — Declare the scheme

Default dimensions, each with allowed values. **Override them if the user has a
framework** — record the override in `scheme.md` so the coding is reproducible.

| dimension | default values |
|---|---|
| language choice | `L2-only` · `L1-only` · `mixed-intra-turn` · `mixed-inter-turn` |
| discourse function | `explaining` · `questioning` · `scaffolding` · `managing` · `evaluating` · `other` |
| pedagogic move | `initiation` · `response` · `feedback` · `other` |
| participant | `teacher` · `student` · `group` · `unknown` |

Definition of `mixed` must be stated explicitly (word-level? clause-level? turn-level?)
because the count depends entirely on that unit.

## Step 3 — Annotate

One row per segment, every dimension filled or marked `n/a`. Never leave a cell
blank — blank means "coder skipped it" and corrupts the counts.

## Step 4 — Quantify

Report only what the data supports:

- distribution per dimension (counts + % of segments)
- cross-tabulation of two dimensions, e.g. language choice × discourse function
- episode-level comparison, if episodes are comparable
- talk time by participant, if timestamps are reliable

## Step 5 — Interpret

Link patterns back to episodes: what was the class doing when the pattern
appears? Numbers alone are not findings.

## Hard constraints

- Timestamps and speaker labels are never modified or inferred.
- Do not reconstruct inaudible text. Mark `[inaudible]` and exclude from counts; report the excluded proportion.
- ASR output is treated as provisional: flag likely errors, do not silently correct them.
- Quantification is descriptive. Do not run inferential statistics on a single classroom without saying so.
- Every interpretive claim about **why** a pattern occurs is `strength: I` under the evidence contract and must list the segments it rests on.

## Files

```
scheme.md
segments.tsv
annotations.tsv
frequency.md
sources.yml
```
