# Academic De-AI

A Claude Code / Codex skill that detects AI-like phrasing, templated rhetoric, and economics-specific writing problems in academic manuscripts.

## What it does

- Flags AI-coded verbs, adjectives, sentence openers, and template sentences
- Checks density thresholds (not just single occurrences)
- Detects economics-specific issues: causal overreach, significance without magnitude, missing comparison baselines, unanchored mechanism claims
- Scores each sentence 0-3 (natural to strongly AI-like)
- Suggests minimal revisions (cut/swap/split), never full rewrites

## Install

Add to your `~/.claude/settings.json`:

```json
{
  "enabledPlugins": {
    "academic-deai@ALLBLUEUK/academic-deai": true
  },
  "extraKnownMarketplaces": {
    "ALLBLUEUK/academic-deai": {
      "source": {
        "source": "github",
        "repo": "ALLBLUEUK/academic-deai"
      }
    }
  }
}
```

## Usage

In Claude Code or Codex, use `/academic-deai` then paste your text or provide a file path.

## License

MIT
