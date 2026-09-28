<div align="center">

# Humanities Research Skills 人文社科研究技能包

**給 AI agent 用的質性研究、應用語言學與社會科學研究技能——每一條結論都可追溯到出處。**

English · 繁體中文

</div>

> **給 AI agent：** 先讀 [`docs/for-agents.md`](docs/for-agents.md)。

## 為什麼做這個

現有的研究類 agent 技能幾乎都是為計算機科學寫的：benchmark、消融實驗、實驗循環。
人文社科的研究機器完全不同——檢索前先凍結 protocol、篩選要寫明排除理由、
編碼必須錨定原文、論證的每一步都能走回頁碼。

這個技能包實現的就是這套機器。它只在一個地方固執：
**無法追溯到出處的結論，刪掉，而不是把措辭改軟。**

## 唯一的那條規則

每份產出都必須附上證據表：

| claim_id | claim | strength | source | locator |
|---|---|---|---|---|
| C014 | 教師在程序性指令時切換到 L1 | D | S07 | p. 212 |

強度分級：`D` 直接引用 · `P` 轉述 · `A` 僅依據摘要 · `I` 你的推斷（必須列出所依據的 claim）。

完整規範：[`references/evidence-contract.md`](references/evidence-contract.md)。

## 三個技能

| 技能 | 做什麼 | 防的是什麼 |
|---|---|---|
| [`lit-review`](skills/lit-review/SKILL.md) | protocol → 檢索日誌 → PRISMA 式篩選 → 可追溯合成 | 不可復現的檢索式、無聲的排除、編造的流程計數 |
| [`qual-coding`](skills/qual-coding/SKILL.md) | 開放式 → 主軸 → 選擇式編碼，輸出帶錨點的編碼本與備忘 | 無錨點的主題、編造的示例引文、過早宣稱飽和 |
| [`emi-transcript`](skills/emi-transcript/SKILL.md) | 課堂轉寫標註：語言選擇、話語功能、序列 | 未申明的編碼單位、被復原的聽不清片段、把推斷包裝成計數 |

## 安裝

```sh
git clone https://github.com/Jeng-linLi/humanities-research-skills.git ~/.claude/skills/humanities-research
```

## 適用平臺

純 Markdown，無運行時，不綁定平臺：Claude Code、Codex CLI、DeepSeek Harness，
以及任何會讀 `SKILL.md` 的 agent。

## 授權

MIT。Copyright (c) 2026 Johnny, Jeng-lin Li。
