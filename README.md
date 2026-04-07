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
  <a href="#examples">Examples</a> &middot;
  <a href="#what-it-catches">What It Catches</a> &middot;
  <a href="#install">Install</a> &middot;
  <a href="#usage">Usage</a>
</p>

---

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) and [Codex](https://openai.com/index/codex/) skill that detects AI-like phrasing, templated rhetoric, and economics-specific writing problems in academic manuscripts. It scores every sentence, flags the worst offenders, and tells you exactly what to delete, swap, or split.

Built for economics papers. Useful for any social-science manuscript.

## Examples

All output below is **real, unedited** from running `/academic-deai`.

<table>
<tr>
<td width="55%">

### Input (score: 3)

> "Moreover, our findings underscore that trade shocks play a pivotal role in exacerbating food insecurity -- not only through direct price transmission channels but also by undermining the resilience of vulnerable households."

</td>
<td width="45%">

### Diagnosis

6 markers: `Moreover` opener, `underscore`, `plays a pivotal role`, em dash, `not only/but also`, abstract-noun stacking

**Fix:** delete Moreover; replace `underscore` with show; delete `play a pivotal role in`; remove the dash and contrast template; split into two sentences; state the magnitude from your results

</td>
</tr>
<tr>
<td>

### Input (score: 3)

> "This paper contributes to a more nuanced understanding of how climate variability shapes agricultural outcomes. Notably, the heterogeneous effects across food groups illuminate the multifaceted nature of dietary vulnerability in developing economies."

</td>
<td>

### Diagnosis

7 markers: `nuanced`, `multifaceted`, `Notably` opener, `illuminate`, `shapes` without identification, proposal-style language, abstract-noun stacking

**Fix:** delete the first sentence entirely (grant-application cliche); delete Notably; replace `illuminate` with show; delete `multifaceted nature of dietary vulnerability`; name which food groups and what the actual effect sizes are

</td>
</tr>
<tr>
<td>

### Input (score: 3)

> "Interestingly, the coefficient on tariff reduction is positive and significant (p < 0.01), lending support to the hypothesis that trade liberalization fosters dietary diversity through enhanced market access."

</td>
<td>

### Diagnosis

6 markers: `Interestingly` opener, `positive and significant` without coefficient, inline `(p < 0.01)` (not economics convention), `fosters`, `lending support to the hypothesis`

**Fix:** delete Interestingly; report coefficient + standard error instead of "positive and significant"; drop the inline p-value (use stars in the table); replace `fosters` with a direct verb; delete the hedge phrase

</td>
</tr>
</table>

**The skill tells you what to cut. You fill in your own numbers.**

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

## Install

```bash
npx skills add ALLBLUEUK/academic-deai
```

Or with Claude Code plugin system:

```bash
claude plugin marketplace add ALLBLUEUK/academic-deai
claude plugin install academic-deai@academic-deai
```

### Update

```bash
npx skills update
# or
claude plugin update academic-deai
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
