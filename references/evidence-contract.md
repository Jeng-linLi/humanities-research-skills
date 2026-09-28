# Evidence Contract

**Hard rule: no claim without a source. A sentence that cannot be traced to a
record in the source registry must not enter the output.**

This is the single constraint that separates this skill pack from generic
research-assistant prompts. Every other file in this repo assumes it.

---

## 1. Source registry

Before writing anything, create `sources.yml`. One entry per source:

```yaml
- id: S07
  authors: "Li, J."
  year: 2024
  title: "Structured translingual practice in EMI classrooms"
  venue: "Journal of X"
  doi: "10.xxxx/yyyy"
  locator_type: page        # page | line | timestamp | paragraph
  file: "pdfs/S07.pdf"      # optional, local full text
```

Rules:

- Ids are stable. Never reuse an id after a source is dropped.
- If full text is unavailable, set `full_text: false` and mark every claim from
  it as `strength: A` (abstract-only).
- Every source you cite must exist here before you cite it. Backfilling later is
  how hallucinations get into manuscripts.

## 2. Evidence record

Every claim in every output carries a record:

| field | required | notes |
|---|---|---|
| `claim_id` | yes | `C001`, sequential |
| `claim` | yes | one sentence, one idea |
| `strength` | yes | `D` `P` `A` `I` (below) |
| `source_id` | yes | must exist in `sources.yml` |
| `locator` | yes | page / line / timestamp |
| `quote` | if `D` | verbatim, unedited |
| `note` | no | why this claim matters |

### Strength levels

| level | meaning | rules |
|---|---|---|
| `D` | direct quotation | verbatim quote required, with locator |
| `P` | paraphrase of a specific passage | locator required |
| `A` | based on abstract / metadata only | flagged in text as tentative |
| `I` | your inference from ≥2 records | must list all contributing `claim_id`s |

`I` is the only level allowed to contain reasoning. `D`/`P`/`A` describe what a
source says, nothing more.

## 3. Claim promotion gates

A claim moves through three states. Each gate is a check, not a formality.

| from → to | gate |
|---|---|
| note → draft | has `source_id`, `locator`, `strength`; quote verbatim if `D` |
| draft → manuscript | claim survives rereading the source at the locator |
| manuscript → published | every claim re-checked against source by a human |

The agent may promote note → draft. It must **not** mark anything as
"verified by human" — that field is human-only.

## 4. Failure protocol

- Source not found for a claim → the claim is deleted, not softened.
- Quote cannot be located in the source → strength downgraded to `A`, or deleted.
- Two sources conflict → both are reported, with the disagreement named. Never
  silently pick one.
- The user asks for something the sources don't support → say so explicitly and
  list what evidence would be needed.

## 5. Output footer

Every generated document ends with an evidence table:

```
| claim_id | claim | strength | source | locator |
|---|---|---|---|---|
```

No evidence table, no document.
