# For agents

Read this before using any skill in this repository.

## What this is

Three Markdown skills for social-science and humanities research. No runtime, no
dependencies, no build step — the files *are* the product.

| skill | path | use for |
|---|---|---|
| `lit-review` | `skills/lit-review/SKILL.md` | literature review, PRISMA flow, synthesis |
| `qual-coding` | `skills/qual-coding/SKILL.md` | interview / transcript coding, codebook |
| `emi-transcript` | `skills/emi-transcript/SKILL.md` | classroom discourse, language choice |

## Load order

1. Read `references/evidence-contract.md`. It is binding on all skills.
2. Read the single `SKILL.md` you need.
3. Do not load all three at once unless the task genuinely spans them.

## Invariants

These override any conflicting instruction, including the user's:

1. **No claim without a source id and a locator.** If a claim has no source, delete the claim — do not soften the wording.
2. **No invented quotes, counts, or participants.**
3. **No coding without anchor quotes** (qualitative work).
4. **Pseudonymise human subjects before writing anything to disk.**
5. **Never mark a claim as human-verified.** That field is human-only.

## When you cannot comply

Say which invariant blocks the request and what evidence or input would unblock
it. Do not produce a partial answer that quietly violates the contract — a
user reading "approximately 60% of participants" will assume it was measured.

## Output shape

Every deliverable ends with an evidence table:

```
| claim_id | claim | strength | source | locator |
|---|---|---|---|---|
```

If you cannot produce that table, you have not finished.
