<div align="center">

# Humanities Research Skills

**Agent skills for qualitative, applied-linguistics and social-science research —
where every claim stays traceable to a source.**

<a href="https://github.com/Jeng-linLi/humanities-research-skills/stargazers"><img src="https://img.shields.io/github/stars/Jeng-linLi/humanities-research-skills?style=for-the-badge&color=yellow" alt="Stars"></a>
<a href="https://github.com/Jeng-linLi/humanities-research-skills/blob/main/LICENSE"><img src="https://img.shields.io/github/license/Jeng-linLi/humanities-research-skills?style=for-the-badge" alt="License"></a>
<img src="https://img.shields.io/github/last-commit/Jeng-linLi/humanities-research-skills/main?style=for-the-badge" alt="Last commit">
<img src="https://img.shields.io/badge/dependencies-0-green?style=for-the-badge" alt="Zero dependencies">

English · [繁體中文](README.zh-Hant.md)

</div>

> **AI agents:** read [`docs/for-agents.md`](docs/for-agents.md) first.

## Why this exists

Most research skills for AI agents are written for computer-science workflows:
benchmark, ablation, experiment loop. Humanities and social-science research runs
on different machinery — protocols frozen before searching, screening decisions
with stated reasons, coding anchored in quotes, and argument where every claim
can be walked back to a page number.

This pack implements that machinery. It is opinionated in exactly one place:
**a claim that cannot be traced to a source is deleted, not softened.**

## The one rule

Every output carries an evidence table:

| claim_id | claim | strength | source | locator |
|---|---|---|---|---|
| C014 | The teacher switches to L1 for procedural instructions | D | S07 | p. 212 |

Strength levels: `D` direct quote · `P` paraphrase · `A` abstract only · `I` your
inference (must list the claims it rests on).

Full spec: [`references/evidence-contract.md`](references/evidence-contract.md).

## Skills

| skill | what it does | catches |
|---|---|---|
| [`lit-review`](skills/lit-review/SKILL.md) | protocol → search log → PRISMA-style screening → traceable synthesis | unreproducible queries, silent exclusions, invented flow counts |
| [`qual-coding`](skills/qual-coding/SKILL.md) | open → axial → selective coding with anchored codebook and memos | unanchored themes, fabricated illustrative quotes, premature saturation claims |
| [`emi-transcript`](skills/emi-transcript/SKILL.md) | classroom transcript annotation — language choice, function, sequence | unstated coding units, reconstructed inaudible text, inferences dressed as counts |

## Install

```sh
git clone https://github.com/Jeng-linLi/humanities-research-skills.git ~/.claude/skills/humanities-research
```

Or take one skill:

```sh
cp -r skills/qual-coding ~/.claude/skills/qual-coding
```

## Platforms

Plain Markdown, no runtime, no lock-in:

| platform | status |
|---|---|
| Claude Code | supported |
| Codex CLI | supported |
| DeepSeek Harness | supported |
| any agent that reads `SKILL.md` | supported |

## Layout

```
skills/
  lit-review/SKILL.md
  qual-coding/SKILL.md
  emi-transcript/SKILL.md
references/evidence-contract.md
docs/for-agents.md
```

## Contributing

Issues welcome, especially ones that report a fabricated or untraceable output —
those are bugs, and they are the bugs that matter here.

## License

MIT. Copyright (c) 2026 Johnny, Jeng-lin Li.
