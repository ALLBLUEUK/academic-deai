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

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) and [Codex](https://openai.com/index/codex/) skill that detects AI-like phrasing, templated rhetoric, and economics-specific writing problems in academic manuscripts. It scores every sentence, flags the worst offenders, and suggests the smallest fix that removes the AI trace.

## Before / After

<table>
<tr>
<td width="50%">

### Before (score: 3)

> "Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households. These results have important implications for policy design."

</td>
<td width="50%">

### After (score: 0)

> "Trade shocks raised food insecurity in our sample by 12%, mainly through higher import prices for staple grains (Table 3, col. 2). Households in the bottom income quintile saw twice the effect."

</td>
</tr>
<tr>
<td>

### Before (score: 3)

> "This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes. Notably, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

</td>
<td>

### After (score: 0)

> "Climate variability reduced calorie availability from cereals by 8% but had no detectable effect on legumes or dairy (Figure 2a). The difference reflects supply-chain length: cereals depend on rain-fed production with no import buffer in our sample countries."

</td>
</tr>
<tr>
<td>

### Before (score: 2)

> "Interestingly, the coefficient on tariff reduction is positive and significant, lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

</td>
<td>

### After (score: 0)

> "A 10pp tariff cut increased diet variety scores by 0.4 SD (p < 0.01, Table 4). The effect is concentrated in coastal provinces with port access, consistent with an import-channel mechanism."

</td>
</tr>
</table>

**Same evidence. Concrete numbers instead of inflated rhetoric.**

## What It Catches

### AI lexical markers
Flags verbs (`underscore`, `foster`, `leverage`, `illuminate`, `dovetail`, `undergird`), adjectives (`nuanced`, `multifaceted`, `overarching`, `pivotal`), and sentence openers (`Moreover`, `Notably`, `Interestingly`, `Taken together`) that are high-frequency AI fingerprints.

### Template sentences
Detects canned patterns: `plays a crucial role`, `has important implications for`, `fills a gap in the literature`, `warrants further investigation`, `a growing body of literature suggests`.

### Density, not just occurrence
A single `Moreover` is fine. Three in one section is a pattern. The skill uses per-paragraph and per-1000-word thresholds to avoid false positives.

### Economics-specific problems
Goes beyond AI detection into real writing quality:
- **Causal overreach**: using `cause`, `drive`, `shape` without identification strategy
- **Significance without magnitude**: "positive and significant" with no coefficient or unit
- **Missing comparison baseline**: "higher" / "increased" without saying relative to what
- **Unanchored mechanism claims**: "through several channels" with no variable or model object
- **Proposal-style language**: "fills an important gap", "offers novel insights" (grant application, not journal prose)

### Structure and figures
- Results sections that read off figures without explaining why the pattern matters
- Discussion sections that re-summarize instead of adding interpretation
- Figure legends that overlap data, inconsistent color mapping, dashboard aesthetics

### Sentence-level scoring
Every flagged sentence gets a score:

| Score | Meaning | Action |
|---|---|---|
| 0 | natural | no change |
| 1 | mildly templated | optional |
| 2 | suspicious | revise |
| 3 | strongly AI-like | revise now |

## Install

```bash
npx skills add ALLBLUEUK/academic-deai
```

Or with Claude Code plugin system:

```bash
claude plugin marketplace add ALLBLUEUK/academic-deai
claude plugin install academic-deai@academic-deai
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

### Example output

```
## Overall diagnosis
- Most common high-risk pattern: template transitions (Moreover/Furthermore density)
- Most important economics-writing issue: significance claims without magnitude
- Flagged sentences: 11 / 34

## High-risk AI markers
> "Moreover, our findings underscore that trade shocks play a pivotal role
> in exacerbating food insecurity."
- Rule triggered: 4.1 (underscore), 6.1 (em dash), 5 (Moreover opener), 6.1 (plays a pivotal role)
- Why: four independent AI markers in one sentence
- Minimal fix: cut Moreover, replace underscore with show, delete "play a pivotal role", state the magnitude
- Score: 3

> "These results have important implications for policy design."
- Rule triggered: 6.3 (implication template), 7.7 (gold-plated closing)
- Why: generic policy implication with no specificity
- Minimal fix: delete entire sentence or replace with a concrete policy-relevant finding
- Score: 3

## Economics-specific issues
- Causal overreach: "exacerbating" (line 4) without IV or diff-in-diff
- Significance without magnitude: "positive and significant" (line 12) -- no coefficient
- Missing baseline: "higher food insecurity" (line 7) -- higher than what?

## Density summary
- Em dashes: 3 in 4 paragraphs
- High-risk transitions: Moreover (2x), Notably (1x), Additionally (1x) = 4/6 paragraphs
- Abstract-noun stacking: resilience + vulnerability + transmission in same sentence (line 4)
```

## License

MIT
