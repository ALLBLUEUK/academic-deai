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

> "Trade shocks increased food insecurity by 12 percent in our sample, driven by higher import prices for staple grains. Households in the bottom income quintile experienced twice the effect, as shown in Table 3."

</td>
</tr>
<tr>
<td>

### Before (score: 3)

> "This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes. Notably, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

</td>
<td>

### After (score: 0)

> "Climate variability reduced calorie availability from cereals by 8 percent but had no detectable effect on legumes or dairy. The difference reflects supply-chain length: cereals in our sample countries depend on rain-fed production with no import buffer."

</td>
</tr>
<tr>
<td>

### Before (score: 3)

> "Notably, the coefficient on tariff reduction is positive and significant (p < 0.01), lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

</td>
<td>

### After (score: 0)

> "A 10 percentage point tariff reduction raised the diet diversity index by 0.8 points (0.03). The effect is concentrated in coastal provinces with port access, consistent with an import-channel interpretation."

</td>
</tr>
</table>

**Same evidence. Concrete numbers instead of inflated rhetoric.**

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
Every flagged sentence gets a score:

| Score | Meaning | Action |
|---|---|---|
| 0 | natural | no change |
| 1 | mildly templated | optional |
| 2 | suspicious | revise |
| 3 | strongly AI-like | revise now |

---

## Full Example

The following is **actual output** from running `/academic-deai` on a sample paragraph. Nothing has been edited.

<details>
<summary>Click to expand full skill output</summary>

### Input

> "Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households. These results have important implications for policy design. Notably, the coefficient on tariff reduction is positive and significant (p < 0.01), lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access. A one-standard-deviation increase in trade openness is associated with a 0.4 SD improvement in diet quality scores. This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes. Interestingly, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

### Output

**Overall diagnosis**: 6/6 sentences flagged. Most common pattern: AI template sentence openers. Most important economics issue: significance without magnitude + non-standard notation.

**Sentence 1** (score: 3)
> "Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households."

Rules triggered: Moreover opener, `underscore`, `plays a pivotal role`, em dash, not only/but also contrast, abstract-noun stacking.
Minimal fix: delete Moreover, replace underscore, remove pivotal role, state the magnitude.

**Sentence 2** (score: 3)
> "These results have important implications for policy design."

Rules triggered: implication template, gold-plated closing. Zero information content.
Minimal fix: delete entirely.

**Sentence 3** (score: 3)
> "Notably, the coefficient on tariff reduction is positive and significant (p < 0.01), lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

Rules triggered: Notably opener, significance without magnitude, inline p-value, `fosters`, "lending support to the hypothesis".
Minimal fix: report coefficient and standard error, drop the p-value, replace fosters.

**Sentence 4** (score: 2)
> "A one-standard-deviation increase in trade openness is associated with a 0.4 SD improvement in diet quality scores."

Rules triggered: `SD` abbreviation, no benchmark for magnitude.
Minimal fix: report in original units, add a benchmark.

**Sentence 5** (score: 3)
> "This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes."

Rules triggered: `contributes to a more nuanced understanding`, `nuanced`, `shapes` without identification.
Minimal fix: delete, or state the specific contribution.

**Sentence 6** (score: 3)
> "Interestingly, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

Rules triggered: Interestingly opener, `illuminate`, `multifaceted`, abstract-noun stacking.
Minimal fix: name the food groups and the actual pattern.

**Density summary**:
- Em dashes: 1 in 1 paragraph
- AI transitions: 3/6 sentences open with Moreover, Notably, Interestingly
- Abstract-noun stacking: 2 instances
- Non-standard notation: SD abbreviation, inline p-value

</details>

---

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

## License

MIT
