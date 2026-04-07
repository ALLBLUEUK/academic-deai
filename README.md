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

All "After" sentences below are **actual suggested rewrites** produced by running `/academic-deai` on the "Before" input.

<table>
<tr>
<td width="50%">

### Before (score: 3)

> "Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households."

6 rules triggered: `Moreover` opener, `underscore`, `plays a pivotal role`, em dash, `not only/but also`, abstract-noun stacking

</td>
<td width="50%">

### After (score: 0)

> "Trade shocks increased food insecurity by 12 percent in our sample, driven mainly by higher import prices for staple grains. Households in the bottom income quintile experienced twice the average effect."

</td>
</tr>
<tr>
<td>

### Before (score: 3)

> "This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes. Notably, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

7 rules triggered: `nuanced`, `multifaceted`, `Notably` opener, `illuminate`, `shapes` without identification, proposal-style language, abstract-noun stacking

</td>
<td>

### After (score: 0)

> "Climate variability reduced calorie availability from cereals by 8 percent but had no detectable effect on legumes or dairy. The difference reflects supply-chain length: cereals in our sample countries depend on rain-fed production with no import buffer."

</td>
</tr>
<tr>
<td>

### Before (score: 3)

> "Interestingly, the coefficient on tariff reduction is positive and significant (p < 0.01), lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

6 rules triggered: `Interestingly` opener, significance without magnitude, inline p-value, `fosters`, `lending support to the hypothesis`, parenthesis misuse

</td>
<td>

### After (score: 0)

> "A 10 percentage point tariff reduction raised the diet diversity index by 0.8 points (0.03), significant at the 1 percent level. The effect is concentrated in coastal provinces with port access, consistent with an import-channel interpretation."

</td>
</tr>
</table>

**Same evidence. Concrete numbers instead of inflated rhetoric.**

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

The block below is **unedited output** from running `/academic-deai` on the three example sentences above.

<details>
<summary>Click to expand</summary>

**Sentence 1** (score: 3)
> "Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households."

- Rules triggered: 5 (Moreover opener), 4.1 (underscore), 6.1 (plays a pivotal role), 7.1 (em dash), 7.2 (not only/but also), 7.4 (resilience + transmission + channels), 8.1 (exacerbating implies causal claim without stated identification)
- Why: six independent AI markers in a single sentence. The em dash opens a contrast clause that stacks abstract nouns without naming a variable, coefficient, or group.
- Keep: trade shocks and food insecurity link
- Cut: Moreover, underscore, pivotal role, em dash, not only/but also, resilience/transmission/channels
- Replace with: "Trade shocks increased food insecurity by 12 percent in our sample, driven mainly by higher import prices for staple grains. Households in the bottom income quintile experienced twice the average effect."

---

**Sentence 2** (score: 3)
> "This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes. Notably, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

- Rules triggered: 6.2 (contributes to a more nuanced understanding), 4.2 (nuanced + multifaceted), 5 (Notably opener), 4.1 (illuminate), 7.4 (vulnerability + nature + outcomes), 8.1 (shapes without identification), 8.5 (proposal-style)
- Why: the first sentence is a grant-application cliche. The second stacks two of the highest-frequency AI adjectives and names no food group, no magnitude, no direction.
- Keep: climate variability affects food groups differently
- Cut: contributes to a more nuanced understanding, Notably, illuminate, multifaceted nature of dietary vulnerability
- Replace with: "Climate variability reduced calorie availability from cereals by 8 percent but had no detectable effect on legumes or dairy. The difference reflects supply-chain length: cereals in our sample countries depend on rain-fed production with no import buffer."

---

**Sentence 3** (score: 3)
> "Interestingly, the coefficient on tariff reduction is positive and significant (p < 0.01), lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

- Rules triggered: 5 (Interestingly opener), 8.2 (positive and significant, no coefficient), 8.8 (inline p-value, parenthesis misuse), 4.1 (fosters), 6.4-adjacent (lending support to the hypothesis)
- Why: positive and significant tells the reader nothing about magnitude. The inline p-value is not economics convention. Fosters dietary diversity through enhanced market access is a mechanism claim with no variable anchoring it.
- Keep: tariff reduction raises diet diversity
- Cut: Interestingly, positive and significant, inline p-value, lending support to the hypothesis, fosters, through enhanced market access
- Replace with: "A 10 percentage point tariff reduction raised the diet diversity index by 0.8 points (0.03), significant at the 1 percent level. The effect is concentrated in coastal provinces with port access, consistent with an import-channel interpretation."

---

**Density summary**:
- Em dashes: 1
- AI transitions: 3/4 sentence starts (Moreover, Notably, Interestingly)
- Very-high-risk adjectives: nuanced, multifaceted
- Abstract-noun stacking: 2 instances
- Non-standard notation: inline p-value, no coefficient reported
- Parenthesis misuse: 1 instance

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
