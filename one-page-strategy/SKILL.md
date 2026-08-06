---
name: one-page-strategy
description: >-
  Generates, validates, or refines a half-page strategy document using the One
  Page Strategy framework (Facts, Problem, Idea, Solution), with sequential
  dependency checks. Use when user says "one page strategy", "write a strategy",
  "strategy document", "review this strategy", or "refine this strategy". Do NOT
  use for a go/no-go decision (decision-gate), a feature spec (grill-me), sprint
  scoping (feature-scoping), or competitor research (competitive).
allowed-tools: Read Write
category:
  - writing
  - productivity
compatibility: claude-code
metadata:
  author: olgasafonova
  version: 1.1.0
  pattern: Generator + Reviewer
  authority: draft
  complexity-contract:
    cost: "Create mode: 5 gated turns of questions, 1 Write. Review mode: 1 Read plus reasoning over a fixed 8-signal rubric, no Write. Refine mode: 1 Read, before/after pairs, 1 Write. ~3-6k tokens. Bounded by the four fixed sections and the 8-signal rubric; single-threaded, no retrieval, and no repeated passes."
    boundary: "A half-page strategy narrative (Facts, Problem, Idea, Solution) for a company, business unit, product, or team over a 3-18 month horizon. NOT a single go/no-go decision (decision-gate), a feature spec (grill-me), sprint scoping (feature-scoping), or competitor research (competitive)."
    fallback: "If references/examples.md is missing, run all three modes inline from this file; the reference doc only adds two worked examples, never the rubric or the section constraints."
---

# One Page Strategy

Guide the creation, review, or refinement of a strategy document using the One Page Strategy framework. The framework replaces bloated strategy decks with a half-page narrative structured as four sequential sections.

## Quality signals — what good looks like

This eight-signal list is **the review checklist**. Every later instruction to "run the review checklist" means this block. Apply it during Create (per-section gates), Review (scored pass/fail), and Refine (target state for edits).

**Pass when**: all eight signals hold.
**Fail when**: any single signal breaks. There is no partial credit and no weighting; a strategy with seven signals passing is a failing strategy with one named defect.

1. **Section compliance** — every section meets its constraint in the Section Constraints table (single source of truth; do not restate the numbers elsewhere)
2. **Zero banned words** — none of the words in the Banned Words list below
3. **Sequential coherence** — Facts support Problem, Problem motivates Idea, Idea drives Solution; each transition holds without explanation
4. **Specificity** — claims are falsifiable; numbers over adjectives ("onboarding in under 3 months" not "fast onboarding")
5. **Root cause depth** — The Problem names a root cause, not a symptom
6. **Actionability** — Solution bullets are concrete actions with verbs, not aspirations
7. **Coffee Test pass** — readable aloud in under 2 minutes with the listener able to explain it to a third person
8. **No bad-strategy patterns** — none of Rumelt's four: fluff, failure to face the challenge, goals masquerading as strategy, conflicting objectives

**Attribution**: Framework compiled by Richard Russell (richardrussell.co), drawing from Alex M H Smith's "No Bullsh*t Strategy," Richard Rumelt's "Good Strategy/Bad Strategy" and "The Crux," and A.G. Lafley and Roger Martin's "Playing to Win." Author links live in the Attribution Footer template under Output Rules, which is the copy that ships to readers; they are deliberately not repeated here.

## The Framework

A one-page strategy answers four questions in sequence, forming a narrative arc. Each section name below is a fixed framework label, not a generic step.

```
                                    4. The Solution (action bullets)
                                   /
                                 /
                               /
  1. The Facts          3. The Idea
               \              /
                 \          /
                   \      /
                     \  /
                2. The Problem (root cause)
```

| Section | Format | Job it does |
|---|---|---|
| The Facts | One paragraph, no bullets | Establish the shared situation. Start with customers. |
| The Problem | One sentence | Name the root cause, not a symptom. Time-bound (3-18 months). |
| The Idea | One sentence | State the belief: "We believe that doing X will address The Problem." |
| The Solution | Bullet points | Actions in sequence. Include what to stop. Not a project plan. |

Word and sentence limits live in one place only: the Section Constraints table under Writing Rules.

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
- What alternatives do customers have? What works or falls short about those alternatives?
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

Single source of truth for every numeric limit in this skill. The review checklist's "Section compliance" signal checks against this table and nothing else.

| Section | Max words | Max units | Unit | Must start with |
|---|---|---|---|---|
| The Facts | 200 | 5 | sentence | Customers |
| The Problem | 30 | 1 | sentence | Customer challenge |
| The Idea | 30 | 1 | sentence | "We believe..." |
| The Solution | 150 | 5 | bullet | Action verb per bullet |

### Banned Words

Flag and remove subjective or judgement words. When found, require replacement with a specific, factual statement.

Canonical list, 22 words. The review checklist's "Zero banned words" signal checks against this list and nothing else. Do not restate it elsewhere in this file; an out-of-sync copy silently changes what the skill enforces.

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

Every saved document ends with the attribution footer shown in the Document Template below. That template is the only copy; keep the author links intact when saving.

### When to Save

- **Create and Refine modes**: Always save to file after final confirmation.
- **Review mode**: Present in-conversation only (no file unless user asks).

Present the complete document in-conversation after saving.

### Document Template

Every saved document uses exactly this shape. Section headings are fixed framework labels; do not rename them.

```markdown
# One Page Strategy: [Title]

**Scope**: [company / business unit / product / team]
**Horizon**: [start month] to [end month]

## The Facts

[One paragraph. Max 5 sentences, 200 words. First sentence names the customers.]

## The Problem

[One sentence. Max 30 words. Root cause, time-bound.]

## The Idea

[One sentence. Max 30 words. Starts "We believe that..."]

## The Solution

- [Action verb + what changes]
- [Action verb + what changes]
- [Action verb + what stops or gets deprioritized]

---
*One Page Strategy framework compiled by [Richard Russell](https://www.linkedin.com/in/richardarussell/) (richardrussell.co),
drawing from [Alex M H Smith](https://www.linkedin.com/in/alex-m-h-smith/), Richard Rumelt, and Lafley & [Roger Martin](https://www.linkedin.com/in/roger-martin-9916911a9/).*
```

## Examples

When a user asks "show me an example" or "what does a strong strategy look like," read `references/examples.md` and present the most relevant example.

Two worked examples are available:
- **Company strategy**: SaaS inventory management pivoting from enterprise to SMB
- **Team strategy**: Partner onboarding team with contract renegotiation approach

## Writing Style

### Conversation Tone

**Direct and questioning**:
- Ask questions that force the user to think, not just answer
- "What would a colleague disagree with?" not "Is this right?"
- "Is that the root cause, or a symptom?" not "Does this look right?"

**Factual enforcement**:
- Flag banned words immediately when they appear in drafts
- Show word counts for every section draft
- Point out broken sequential links explicitly

### Anti-slop

- No em dashes; use colons, commas, or periods
- No hedge words unless uncertainty is real
- No filler phrases (throat-clearing openers that delay the point)
- No sycophantic openers ("Great strategy!")
- State facts and ask hard questions

## DO / DON'T

**DO:**
- Walk through sections in order (Facts, Problem, Idea, Solution)
- Gate each section: wait for user confirmation before proceeding
- Flag every banned word with a specific replacement suggestion
- Show word counts on every draft
- Challenge weak problem statements: push for root cause, not symptom
- Preserve the user's voice when refining

**DON'T:**
- Batch all questions upfront; ask section by section
- Skip the sequential coherence check
- Accept vague problem statements ("we need to improve")
- Rewrite from scratch in Refine mode; edit surgically
- Invent facts the user did not provide
- Use banned words in your own drafts

## Inversion Questions

Before finalizing any strategy, test it with these inversion questions. Stop refining when the user can answer all three convincingly.

1. **Falsifiability**: "What evidence would prove this strategy wrong?" If no answer exists, The Idea is too vague.
2. **Tradeoff clarity**: "What are you explicitly choosing NOT to do?" If nothing is excluded, The Solution lacks focus.
3. **Disagreement test**: "What would a smart colleague argue instead?" If no credible alternative exists, The Problem may be trivially obvious and the strategy adds no insight.

## Stop Conditions

Stop when any of these are true:

- **Create mode**: User confirms all four sections and the final assembled document
- **Review mode**: All eight review criteria have been evaluated and presented
- **Refine mode**: User has accepted or rejected all proposed changes and the clean document is produced
- **User says "done"**: Save current state and exit regardless of mode
- **No progress after two rounds**: If the user rejects the same section twice without new input, ask whether to continue or save the current draft as-is

## Idempotency

Safe to re-run on the same document. Running Review mode on an already-reviewed strategy produces the same checklist output. Running Refine mode on a clean strategy reports no issues. Running Create mode with the same inputs produces a structurally equivalent document.

## Interface

### Input

| Mode | Required input | Optional input |
|---|---|---|
| Create | Subject (company, business unit, product, or team) | Customer description, time horizon (defaults to 3-18 months) |
| Review | An existing strategy document: file path or pasted text | The four section labels, if the document uses different headings |
| Refine | An existing draft: file path or pasted text | Which sections to leave untouched |

Create mode needs no input up front beyond the subject; it gathers the rest through the Step 1 questions. Review and Refine both need a document, and neither invents one. If the user asks for Review or Refine with no document in hand, ask for it rather than drafting a strawman.

### Output

| Mode | Output | Location |
|---|---|---|
| Create | Complete four-section strategy document (.md), per Document Template | Saved to file, shown in conversation |
| Review | Structured checklist with pass/fail per criterion | In conversation only (no file unless requested) |
| Refine | Clean document with accepted edits (.md) | Saved to file, shown in conversation |

All saved files use the naming convention `One Page Strategy - [Title].md` and include the attribution footer.

## Mode Awareness

This skill runs standalone: it declares no `produces:` or `consumes:` artifact contract, so nothing auto-discovers its output. Two portfolio-level relations exist by convention only, and both require the user to point at the file explicitly:

- **Upstream**: a `competitive` analysis in the vault can supply evidence for The Facts. This skill does not go looking for one.
- **Downstream**: a saved strategy can feed a presentation or deck skill. The saved .md file is the handoff artifact.

`decision-gate` routes strategy-document authoring here. This skill does not route back to it.

## Progress Checkpoints

In Create mode, confirm progress at each gate:

```
[1/4] The Facts    -- drafted, awaiting confirmation
[2/4] The Problem  -- not started
[3/4] The Idea     -- not started
[4/4] The Solution -- not started
```

Update the checkpoint display after each section is confirmed. In Review and Refine modes, show section-by-section progress through the checklist.
