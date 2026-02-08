---
name: one-page-strategy
version: 1.0.0
description: >-
  Guide creation, review, or refinement of strategy documents
  using the One Page Strategy framework (Facts, Problem, Idea,
  Solution). Use when user says "one page strategy", "write a
  strategy", "strategy document", "review my strategy", "refine
  my strategy", or wants to create a focused strategy document.
allowed-tools: Read Write
category:
  - writing
  - productivity
---

# One Page Strategy

Guide the creation, review, or refinement of a strategy document using the One Page Strategy framework. The framework replaces bloated strategy decks with a half-page narrative structured as four sequential sections.

**Attribution**: Framework compiled by [Richard Russell](https://www.linkedin.com/in/richardarussell/) (richardrussell.co), drawing from [Alex M H Smith](https://www.linkedin.com/in/alex-m-h-smith/)'s "No Bullsh*t Strategy," Richard Rumelt's "Good Strategy/Bad Strategy" and "The Crux," and A.G. Lafley and [Roger Martin](https://www.linkedin.com/in/roger-martin-9916911a9/)'s "Playing to Win."

## The Framework

A one-page strategy answers four questions in sequence, forming a narrative arc: **Facts → Problem → Idea → Solution**. Each section depends on the one before it.

| Section | Format | Constraint |
|---------|--------|------------|
| The Facts | One paragraph, no bullets | Max 5 sentences, 200 words. Start with customers. |
| The Problem | One sentence | Root cause, not symptom. Time-bound (3-18 months). |
| The Idea | One sentence | "We believe that doing X will address The Problem." |
| The Solution | Up to 5 bullet points | Actions in sequence. Include what to stop. Not a project plan. |

**Sequential dependency**: Each section depends on the one before. If readers disagree with The Facts, they won't agree on The Problem. If they disagree on The Problem, The Idea won't make sense. Agreement on each section is required before moving to the next.

## Mode Detection

Determine which mode based on user input:

- **Create**: User wants to write a new strategy. Indicators: "write a strategy", "help me create", no existing document provided, topic/team/product name given.
- **Review**: User provides an existing document for critique. Indicators: "review this", "critique my strategy", file path or pasted text of an existing strategy.
- **Refine**: User has a draft they want tightened. Indicators: "tighten this", "make it shorter", "refine my draft", existing document with request to improve.

If ambiguous, ask which mode.

## Create Mode

Walk the user through writing each section interactively. Never batch all questions at the start.

### Step 1: Context Gathering

Ask three questions (one message):
1. What is this strategy about? (Company, business unit, product, or team)
2. Who are the customers? (External market customers or internal stakeholders)
3. What time horizon? (Default: 3-18 months)

Gather answers before proceeding.

### Step 2: Draft The Facts

Ask discovery questions to draw out the paragraph:
- What are customers trying to do? What problems do they face?
- What alternatives do customers have? What's good or not good about those alternatives?
- What makes delivering value challenging internally?
- Any recent wins that inform the strategy going forward?

Draft a single paragraph from their answers. Apply writing rules (see below). Present the draft with word count.

Ask: "Do these facts represent the situation accurately? What would a colleague disagree with?"

**Gate**: Do not proceed until the user confirms The Facts.

### Step 3: Draft The Problem

Ask:
- "Based on The Facts, what is the key customer challenge for the next 3-18 months?"
- "Is that the root cause, or a symptom of something deeper?"

Draft one sentence. Present it.

Ask: "If a colleague read this, would they agree this is THE problem? What alternative problem might they propose?"

**Gate**: Confirm before proceeding.

### Step 4: Draft The Idea

Ask:
- "What insight, belief, or assumption guides how to address The Problem?"

Offer the template: "We believe that doing [X] will address The Problem."

Draft one sentence. Present it.

Ask: "What would happen if this belief turned out to be wrong?"

**Gate**: Confirm before proceeding.

### Step 5: Draft The Solution

Ask:
- "What are the main things The Idea implies need to happen? Think sequence, not completeness."
- "What will change from what the team currently does?"
- "What will stop or be deprioritized?"

Draft up to 5 bullet points. Present the complete four-section document.

Run the review checklist silently. Flag any remaining issues (banned words, word count violations, broken sequential links). Ask for final confirmation, then save.

## Review Mode

Read the provided document. Apply the review checklist section by section. Present structured feedback:

```
## Review: [Document Title]

### The Facts
- [x] Starts with customers
- [ ] Contains subjective word: "innovative" (line X)
- [ ] Exceeds 200 words (currently 247)
- Suggestion: [specific rewrite of flagged phrase]

### The Problem
- [x] One sentence
- [ ] Reads as symptom, not root cause
- Suggestion: [rewrite addressing root cause]

### The Idea
...

### The Solution
...

### Sequential Coherence
- Facts -> Problem: [Does The Problem emerge from The Facts?]
- Problem -> Idea: [Does The Idea address The Problem?]
- Idea -> Solution: [Do the bullets implement The Idea?]

### Coffee Test
Could someone share this in a 2-minute conversation? [Yes/No + why]
```

Flag every banned word. Count words per section. Check sequential dependency at each transition.

### Bad Strategy Detection (Rumelt)

After the per-section checks, scan for these four patterns of bad strategy:

1. **Fluff**: Inflated language that sounds strategic but says nothing. "Leverage our core competencies to deliver synergistic value" is fluff. Rewrite as a specific, falsifiable claim.
2. **Failure to face the challenge**: The Problem section avoids naming the actual painful constraint. If The Problem could apply to any company in the industry, it's too generic. Push for the specific tension this team faces.
3. **Goals masquerading as strategy**: The Idea states a desired outcome ("become the market leader", "grow revenue 30%") instead of an insight about *how* to get there. Strategy explains the mechanism, not the destination.
4. **Conflicting objectives**: The Solution bullets pull in opposite directions (e.g., "cut costs" and "expand into new markets" simultaneously without explaining which takes priority or how resources shift).

Flag each pattern found with a specific quote from the document and a suggestion for fixing it.

## Refine Mode

1. Read the document.
2. Run the review checklist silently.
3. For each issue, present a before/after pair:
   - **Before**: Original text with the issue highlighted
   - **After**: Rewritten version fixing the issue
4. Preserve the user's voice and intent. Change the minimum necessary.
5. Ask which changes to accept.
6. Produce a clean final document with accepted changes.

Never rewrite from scratch. Edit surgically.

## Writing Rules

### Section Constraints

| Section | Max Words | Max Sentences | Must Start With |
|---------|-----------|---------------|-----------------|
| The Facts | 200 | 5 | Customers |
| The Problem | ~30 | 1 | Customer challenge |
| The Idea | ~30 | 1 | "We believe..." |
| The Solution | ~150 total | 5 bullets | Action verb per bullet |

### Banned Words

Flag and remove subjective or judgement words. When found, require replacement with a specific, factual statement.

**Banned list**: best, worst, fast, slow, innovative, effective, ineffective, bad, good, important, critical, key, significant, major, strategic, optimal, robust, seamless, cutting-edge, world-class, state-of-the-art, game-changing

**Example**: "fast onboarding" becomes "onboarding in under 3 months" or "onboarding averaging 18 months."

### Jargon Detection

- Flag acronyms not defined in the same document
- Flag corporate buzzwords: leverage, synergy, align, optimize, streamline, holistic, ecosystem, paradigm, disruptive
- Exception: domain-specific technical terms acceptable if the intended audience understands them

### The Coffee Test

After assembling the full document, evaluate: could someone read this aloud in under 2 minutes and have the listener understand the strategy well enough to explain it to a third person? If not, the document is too long or too complex.

## Output Rules

### File Naming

Save as: `One Page Strategy - [Title].md`

Title should be 3-6 words describing the strategy's subject. Examples:
- `One Page Strategy - SMB Inventory Platform.md`
- `One Page Strategy - Partner Onboarding.md`

### Attribution Footer

Every saved document ends with:

```markdown
---
*One Page Strategy framework compiled by [Richard Russell](https://www.linkedin.com/in/richardarussell/) (richardrussell.co),
drawing from [Alex M H Smith](https://www.linkedin.com/in/alex-m-h-smith/), Richard Rumelt, and Lafley & [Roger Martin](https://www.linkedin.com/in/roger-martin-9916911a9/).*
```

### When to Save

- **Create and Refine modes**: Always save to file after final confirmation.
- **Review mode**: Present in-conversation only (no file unless user asks).

Present the complete document in-conversation after saving.

## Examples

When a user asks "show me an example" or "what does a good strategy look like," read `references/examples.md` and present the most relevant example.

Two worked examples are available:
- **Company strategy**: SaaS inventory management pivoting from enterprise to SMB
- **Team strategy**: Partner onboarding team with contract renegotiation approach

## Conversation Style

**Direct and questioning**:
- Ask questions that force the user to think, not just answer
- "What would a colleague disagree with?" not "Is this right?"
- "Is that the root cause, or a symptom?" not "Does this look good?"

**Factual enforcement**:
- Flag banned words immediately when they appear in drafts
- Show word counts for every section draft
- Point out broken sequential links explicitly

**Anti-slop**:
- No em dashes; use colons, commas, or periods
- No hedge words unless uncertainty is real
- No filler phrases ("It's important to note that")
- No sycophantic openers ("Great strategy!")
- State facts and ask hard questions
