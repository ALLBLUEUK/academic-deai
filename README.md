<p align="center">
  <img src="https://em-content.zobj.net/source/apple/391/magnifying-glass-tilted-left_1f50d.png" width="100" />
</p>

<h1 align="center">academic-deai</h1>

<p align="center">
  <strong>Your paper should sound like you wrote it, not like a model completed a writing task.</strong>
</p>

<p align="center">
  <a href="https://github.com/ALLBLUEUK/academic-deai/stargazers"><img src="https://img.shields.io/github/stars/ALLBLUEUK/academic-deai?style=flat&color=yellow" alt="Stars"></a>
  <a href="https://github.com/ALLBLUEUK/academic-deai/commits/main"><img src="https://img.shields.io/github/last-commit/ALLBLUEUK/academic-deai?style=flat" alt="Last Commit"></a>
  <a href="LICENSE"><img src="https://img.shields.io/github/license/ALLBLUEUK/academic-deai?style=flat" alt="License"></a>
</p>

<p align="center">
  <a href="#before--after">Before / After</a> &middot;
  <a href="#what-it-catches">What It Catches</a> &middot;
  <a href="#install">Install</a> &middot;
  <a href="#usage">Usage</a>
</p>

---

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) and [Codex](https://openai.com/index/codex/) skill that detects AI-like phrasing, templated rhetoric, and economics-specific writing problems in academic manuscripts. It scores every sentence, flags the worst offenders, and tells you exactly what to delete, swap, or split.

Built for economics papers. Useful for any social-science manuscript.

## Before / After

<table>
<tr>
<td width="50%">

### Before (score: 3)

> "Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households. These results have important implications for policy design."

</td>
<td width="50%">

### After (score: 0)

> "Trade shocks worsened food insecurity through higher prices for imported staples and by reducing the purchasing power of low-income households."

</td>
</tr>
<tr>
<td>

### Before (score: 3)

> "This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes. Notably, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

</td>
<td>

### After (score: 0)

> "Climate variability affects agricultural outcomes unevenly across food groups: cereals and perishable crops show larger declines than legumes or dairy in our sample of developing economies."

</td>
</tr>
<tr>
<td>

### Before (score: 3)

> "Interestingly, the coefficient on tariff reduction is positive and significant, lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

</td>
<td>

### After (score: 0)

> "Tariff reductions are associated with higher dietary diversity, consistent with greater access to imported food varieties in the treated regions."

</td>
</tr>
</table>

**AI traces removed. Journal quality preserved.**

---

## What It Catches

### AI lexical markers
Flags verbs like `underscore`, `foster`, `leverage`, `illuminate`, `dovetail`, `undergird` and adjectives like `nuanced`, `multifaceted`, `overarching`, `pivotal` that are high-frequency AI fingerprints.

### Template sentences
Detects canned patterns: `plays a crucial role`, `has important implications for`, `fills a gap in the literature`, `warrants further investigation`, `a growing body of literature suggests`.

### Density, not just occurrence
A single `Moreover` is fine. Three in one section is a pattern. The skill uses per-paragraph and per-1000-word thresholds to avoid false positives.

### Economics-specific problems
Goes beyond AI detection into real writing quality:
- **Causal overreach**: `cause`, `drive`, `shape` without identification strategy
- **Significance without magnitude**: "positive and significant" with no coefficient or unit
- **Missing comparison baseline**: "higher" / "increased" without saying relative to what
- **Unanchored mechanism claims**: "through several channels" with no variable or model object
- **Proposal-style language**: "fills an important gap", "offers novel insights"
- **Non-standard notation**: inline p-values, `SD` abbreviation, parenthesis overload

### Structure and figures
- Results sections that read off figures without explaining why the pattern matters
- Discussion sections that re-summarize instead of adding interpretation
- Figure captions that restate conclusions instead of describing what is plotted

### Sentence-level scoring

| Score | Meaning | Action |
|---|---|---|
| 0 | natural | no change |
| 1 | mildly templated | optional |
| 2 | suspicious | revise |
| 3 | strongly AI-like | revise now |

---

## Full Skill Output

The block below is **unedited output** from running `/academic-deai` on the three Before sentences.

<details>
<summary>Click to expand</summary>

**Sentence 1** (score: 3)
> "Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households."

- Rules triggered: 5 (Moreover opener), 4.1 (underscore), 6.1 (plays a pivotal role), 7.1 (em dash), 7.2 (not only/but also), 7.4 (resilience + transmission + channels), 8.1 (exacerbating implies causal claim without stated identification)
- Why: six independent AI markers in a single sentence. The em dash opens a contrast clause that stacks abstract nouns without naming a variable, coefficient, or group.
- Minimal fix: delete Moreover; replace `underscore` with show; delete `play a pivotal role in`; remove the dash and contrast template; split into two sentences; state the magnitude from your results.

---

**Sentence 2** (score: 3)
> "This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes. Notably, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

- Rules triggered: 6.2 (contributes to a more nuanced understanding), 4.2 (nuanced + multifaceted), 5 (Notably opener), 4.1 (illuminate), 7.4 (vulnerability + nature + outcomes), 8.1 (shapes without identification), 8.5 (proposal-style)
- Why: the first sentence is a grant-application cliche. The second stacks two of the highest-frequency AI adjectives and names no food group, no magnitude, no direction.
- Minimal fix: delete the first sentence; delete Notably; replace `illuminate` with show; delete `multifaceted nature of dietary vulnerability`; name which food groups and what the actual effect sizes are.

---

**Sentence 3** (score: 3)
> "Interestingly, the coefficient on tariff reduction is positive and significant (p < 0.01), lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

- Rules triggered: 5 (Interestingly opener), 8.2 (positive and significant, no coefficient), 8.8 (inline p-value, parenthesis misuse), 4.1 (fosters), 6.4-adjacent (lending support to the hypothesis)
- Why: positive and significant tells the reader nothing about magnitude. The inline p-value is not economics convention. Fosters dietary diversity through enhanced market access is a mechanism claim with no variable anchoring it.
- Minimal fix: delete Interestingly; report coefficient + standard error instead of "positive and significant"; drop the inline p-value; replace `fosters` with a direct verb; delete the hedge phrase.

---

**Density summary**:
- Em dashes: 1
- AI transitions: 3/3 sentences open with Moreover, Notably, Interestingly
- Very-high-risk adjectives: nuanced, multifaceted
- Abstract-noun stacking: 2 instances
- Non-standard notation: inline p-value, no coefficient reported

</details>

---

## Install

```bash
npx skills add ALLBLUEUK/academic-deai
```

This installs to Claude Code, Codex, Cursor, and other supported agents automatically.

Or with Claude Code plugin system:

```bash
claude plugin marketplace add ALLBLUEUK/academic-deai
claude plugin install academic-deai@academic-deai
```

### Update

```bash
# reinstall to get the latest version
npx skills remove academic-deai -g
npx skills add ALLBLUEUK/academic-deai -g -y
```

## Usage

In Claude Code or Codex:

```
/academic-deai
```

Then paste your text, or point to a file:

```
/academic-deai
Review the Results section in draft-v3.tex
```

## License

MIT
