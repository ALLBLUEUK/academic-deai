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
  <a href="#real-output">Real Output</a> &middot;
  <a href="#what-it-catches">What It Catches</a> &middot;
  <a href="#install">Install</a> &middot;
  <a href="#usage">Usage</a>
</p>

---

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) and [Codex](https://openai.com/index/codex/) skill that detects AI-like phrasing, templated rhetoric, and economics-specific writing problems in academic manuscripts. It scores every sentence, flags the worst offenders, and suggests the smallest fix that removes the AI trace.

Built for economics papers. Useful for any social-science manuscript.

## Real Output

The following is **actual output** from running `/academic-deai` on a sample paragraph. Nothing has been edited.

### Input

> "Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households. These results have important implications for policy design. Notably, the coefficient on tariff reduction is positive and significant (p < 0.01), lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access. A one-standard-deviation increase in trade openness is associated with a 0.4 SD improvement in diet quality scores. This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes. Interestingly, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

### Output (abbreviated)

**Overall diagnosis**: 6/6 sentences flagged. Most common pattern: AI template sentence openers. Most important economics issue: significance without magnitude + non-standard notation.

**Sentence 1** (score: 3)
> "Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households."

Rules triggered: Moreover opener, `underscore` (AI verb), `plays a pivotal role` (role template), em dash, not only/but also contrast, abstract-noun stacking (resilience + transmission + channels).

Minimal fix: delete Moreover, replace underscore, remove pivotal role, state the magnitude:
> "Trade shocks increased food insecurity by X% in our sample, mainly through higher import prices for staple grains."

---

**Sentence 2** (score: 3)
> "These results have important implications for policy design."

Rules triggered: implication template, gold-plated closing. Zero information content. Which policy? What design change?

Minimal fix: delete entirely.

---

**Sentence 3** (score: 3)
> "Notably, the coefficient on tariff reduction is positive and significant (p < 0.01), lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

Rules triggered: Notably opener, `positive and significant` without coefficient, inline p-value (not economics convention), `fosters` (AI verb), `lending support to the hypothesis` (AI hedging).

Minimal fix: report coefficient + standard error, drop the p-value, replace fosters:
> "A 10 percentage point tariff reduction raised the diet diversity index by 0.8 points (0.03), significant at the 1% level."

---

**Sentence 4** (score: 2)
> "A one-standard-deviation increase in trade openness is associated with a 0.4 SD improvement in diet quality scores."

Rules triggered: `SD` abbreviation (economics papers write "standard deviations" or use original units), no benchmark for magnitude.

Minimal fix: report in original index units, add a comparison for scale.

---

**Sentence 5** (score: 3)
> "This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes."

Rules triggered: `contributes to a more nuanced understanding` (top AI cliche), `nuanced` (AI fingerprint), `shapes` (causal language without identification).

Minimal fix: delete. If a contribution claim is needed, state the specific finding.

---

**Sentence 6** (score: 3)
> "Interestingly, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

Rules triggered: Interestingly opener, `illuminate` (AI verb), `multifaceted` (AI adjective), abstract-noun stacking without concrete variable.

Minimal fix: name the food groups and the actual pattern:
> "Effects differ across food groups: cereals show the largest decline (X%), while legumes are unaffected."

---

**Density summary**:
- Em dashes: 1/1 paragraph
- AI transitions: 3/6 sentences (Moreover, Notably, Interestingly)
- Abstract-noun stacking: 2 instances
- Non-standard notation: SD abbreviation, inline p-value

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
- **Non-standard notation**: inline p-values, SD abbreviation, parenthesis overload

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
