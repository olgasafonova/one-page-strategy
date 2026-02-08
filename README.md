# One Page Strategy

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-green?logo=anthropic&logoColor=white)](https://docs.anthropic.com/en/docs/claude-code)
[![Claude Projects](https://img.shields.io/badge/Claude-Projects-orange?logo=anthropic&logoColor=white)](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
[![Cursor](https://img.shields.io/badge/Cursor-Rules-purple)](https://cursor.com/docs/context/rules)
[![Windsurf](https://img.shields.io/badge/Windsurf-Rules-blue)](https://docs.windsurf.com)
[![GitHub Copilot](https://img.shields.io/badge/GitHub_Copilot-Instructions-black?logo=github&logoColor=white)](https://docs.github.com/en/copilot/customizing-copilot/adding-repository-custom-instructions-for-github-copilot)

[![skillcheck passed](https://raw.githubusercontent.com/olgasafonova/one-page-strategy/main/skillcheck-passed.svg)](https://getskillcheck.com)

An AI skill that guides you through writing, reviewing, or refining strategy documents using the **One Page Strategy** framework. Works in any tool that supports custom instructions.

Replace bloated strategy decks with a half-page narrative structured as four sequential sections: **Facts, Problem, Idea, Solution.**

## What It Does

| Mode | Description |
|------|-------------|
| **Create** | Walk through each section interactively with gated confirmation at every step |
| **Review** | Critique an existing strategy against framework rules and Rumelt's bad strategy patterns |
| **Refine** | Tighten a draft with before/after pairs, preserving your voice |

The skill enforces writing discipline: banned subjective words, word limits per section, jargon detection, sequential coherence checks, and the "coffee test" (can you share this in 2 minutes?).

## Installation

### Claude Code

```bash
# Clone and copy to skills directory
git clone https://github.com/olgasafonova/one-page-strategy.git
cp -r one-page-strategy/one-page-strategy ~/.claude/skills/
```

Or copy manually: place the `one-page-strategy/` folder into `~/.claude/skills/`.

### Claude Desktop / Web (Projects)

1. Open [claude.ai](https://claude.ai) or Claude Desktop
2. Create or open a Project
3. Go to Project Knowledge
4. Upload `one-page-strategy/SKILL.md` as a file

### Cursor

Copy `one-page-strategy/SKILL.md` content into your `.cursorrules` or project rules file.

### Windsurf

Copy `one-page-strategy/SKILL.md` content into your `.windsurfrules` file.

### GitHub Copilot

Copy `one-page-strategy/SKILL.md` content into `.github/copilot-instructions.md` in your repository.

### Cline

Paste `one-page-strategy/SKILL.md` content into Cline's custom instructions (Settings > Custom Instructions).

### Aider

Copy `one-page-strategy/SKILL.md` content into your `.aider.conf.yml` conventions file or pass with `--read`.

### ChatGPT

Create a custom GPT and paste `one-page-strategy/SKILL.md` content into the Instructions field.

## Usage

Start a conversation and say:

- **"one page strategy"** or **"write a strategy"** to create a new one
- **"review my strategy"** with a document to get a critique
- **"refine my strategy"** with a draft to tighten it

### Create Mode walkthrough

The skill asks questions in stages, never all at once:

1. **Context**: What's this strategy about? Who are the customers? Time horizon?
2. **The Facts**: Discovery questions about customers, alternatives, internal challenges. Drafts a paragraph (max 200 words, 5 sentences).
3. **The Problem**: One sentence. Root cause, not symptom. "Is that the root cause, or a symptom of something deeper?"
4. **The Idea**: One sentence. "We believe that doing X will address The Problem."
5. **The Solution**: Up to 5 bullet points in sequence. Includes what to stop.

Each section requires confirmation before moving to the next. The skill asks: *"What would a colleague disagree with?"*

### Review Mode checks

- Word counts and sentence limits per section
- Banned subjective words (best, innovative, strategic, seamless, etc.)
- Undefined acronyms and corporate jargon
- Sequential coherence (does each section follow from the previous?)
- Rumelt's four bad strategy patterns:
  - Fluff masquerading as insight
  - Failure to face the actual challenge
  - Goals disguised as strategy
  - Conflicting objectives

## The Framework

| Section | Format | Constraint |
|---------|--------|------------|
| The Facts | One paragraph | Max 5 sentences, 200 words. Start with customers. |
| The Problem | One sentence | Root cause, not symptom. 3-18 month horizon. |
| The Idea | One sentence | "We believe that doing X will address The Problem." |
| The Solution | Up to 5 bullets | Actions in sequence. Include what to stop. |

Each section depends on the one before. Disagreement at any level invalidates everything downstream.

## Attribution

Framework compiled by [Richard Russell](https://www.linkedin.com/in/richardarussell/) (richardrussell.co), drawing from:

- [Alex M H Smith](https://www.linkedin.com/in/alex-m-h-smith/)'s "No Bullsh*t Strategy" ([Basic Arts](https://basicarts.org/))
- [Richard Rumelt](https://www.linkedin.com/in/richard-rumelt-18520828/)'s "Good Strategy/Bad Strategy" and "The Crux"
- [A.G. Lafley](https://www.linkedin.com/in/ag-lafley-2381b3201/) and [Roger Martin](https://www.linkedin.com/in/roger-martin-9916911a9/)'s "Playing to Win"

## License

MIT
