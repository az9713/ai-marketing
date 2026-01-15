# AI Marketer Test Documentation

This document provides comprehensive test results for all 10 use cases documented in the [Quick Start Guide](./user-guide/quick-start.md). Each test demonstrates how the marketing frameworks work in practice, with actual inputs, mock data, and expected outputs.

**Purpose**: Help new users understand what to expect when using AI Marketer commands.

---

## Table of Contents

1. [Testing Methodology](#testing-methodology)
2. [Test 1: Score a Headline](#test-1-score-a-headline)
3. [Test 2: Improve a Weak Headline](#test-2-improve-a-weak-headline)
4. [Test 3: Audit GitHub README](#test-3-audit-github-readme)
5. [Test 4: Compare Two Headlines](#test-4-compare-two-headlines)
6. [Test 5: Generate a README](#test-5-generate-a-readme)
7. [Test 6: Analyze a Competitor](#test-6-analyze-a-competitor)
8. [Test 7: Extract Writing Voice](#test-7-extract-writing-voice)
9. [Test 8: Write a Tweet Thread](#test-8-write-a-tweet-thread)
10. [Test 9: Rewrite with Loss Aversion](#test-9-rewrite-with-loss-aversion)
11. [Test 10: Create a Tagline](#test-10-create-a-tagline)
12. [Summary](#summary)

---

## Testing Methodology

### How Tests Were Conducted

All tests were executed within Claude Code with the AI Marketer plugin loaded. The plugin reads instructions from `CLAUDE.md` which contains:
- Command definitions (`/score`, `/audit`, `/readme`, `/compete`, `/voice`)
- Framework reference (NESB, Cialdini's 7 Levers, etc.)
- Output format specifications

### Mock Data Usage

For tests requiring external data (URLs, competitor websites), mock data was used to ensure reproducible results:

| Test | Mock Data Type |
|------|----------------|
| Test 3 (Audit) | Used the ai-marketing repo itself |
| Test 5 (README) | Mock project: CSV-to-JSON CLI tool |
| Test 6 (Compete) | Fictional competitor: "CodeAI Pro" |
| Test 7 (Voice) | Sample developer writing provided inline |
| Test 8 (Thread) | Mock project: CSV-to-JSON CLI tool |

### Pass/Fail Criteria

Each test was evaluated against:
1. **Format Compliance**: Output matches documented format
2. **Framework Application**: Correct frameworks applied
3. **Actionable Output**: Results are useful and specific
4. **Score Accuracy**: NESB scores align with framework definitions

---

## Test 1: Score a Headline

### What This Tests
The `/score` command evaluates a headline against the NESB framework (NEW, EASY, SAFE, BIG), providing a score from 0-40 and improvement suggestions.

### Framework Used
📘 *Take Their Money* (Milligan) — NESB scoring for the 4 emotional triggers

### Input
```
score AI-powered code completion tool
```

### Expected Behavior
- Score the headline 0-40 across 4 dimensions
- Identify weak dimensions with explanations
- Suggest stronger alternatives

### Test Output

```
## NESB Score: 14/40

| Dim  | Score | Assessment |
|------|-------|------------|
| NEW  | 3/10  | Generic - "AI-powered" is overused, no unique mechanism |
| EASY | 4/10  | "Completion" implies ease but not stated explicitly |
| SAFE | 3/10  | No trust signals, no social proof, no guarantees |
| BIG  | 4/10  | "Tool" is small - no transformation promised |

### Stronger Alternatives
1. "The first AI that reads your entire codebase - ship 10x faster with zero setup." - 32/40
2. "Stop debugging. Start shipping. Trusted by 50,000 developers." - 30/40
```

### Analysis

| Dimension | Why This Score |
|-----------|----------------|
| NEW (3/10) | "AI-powered" appears in thousands of product descriptions. No unique mechanism or differentiator. |
| EASY (4/10) | "Completion" suggests less typing, but no explicit ease claim like "zero config" or "one-click". |
| SAFE (3/10) | No social proof (user counts), no testimonials, no guarantees, no authority signals. |
| BIG (4/10) | "Tool" is a small word. No transformation language like "10x", "revolutionize", or "dominate". |

### Result: ✅ PASS

---

## Test 2: Improve a Weak Headline

### What This Tests
Given a low-scoring headline, Claude generates multiple alternatives that score higher on NESB.

### Framework Used
📘 *Take Their Money* (Milligan) — improving headlines by optimizing each NESB dimension

### Input
```
My headline scored 14/40: "AI-powered code completion tool"

Can you give me 5 alternatives that score higher?
```

### Expected Behavior
- Generate 5 alternative headlines
- Each should score higher than 14/40
- Explain why each scores better

### Test Output

```
Here are 5 alternatives with higher NESB scores:

| # | Headline | Score | Why It's Better |
|---|----------|-------|-----------------|
| 1 | "Stop debugging. Start shipping." | 28/40 | Loss aversion (BIG), implies ease (EASY) |
| 2 | "The coding AI that actually understands your codebase." | 30/40 | Differentiator (NEW), implies competence (SAFE) |
| 3 | "10x faster coding. Zero learning curve. Trusted by 50,000 devs." | 35/40 | Hits all 4: NEW (10x), EASY (zero curve), SAFE (50k), BIG (10x) |
| 4 | "Write code like a senior engineer — in half the time." | 27/40 | Identity (SAFE), outcome (BIG), ease (EASY) |
| 5 | "The first AI that reads your entire codebase before suggesting." | 31/40 | Unique mechanism (NEW), implies accuracy (SAFE) |
```

### Analysis

**Why #3 scores highest (35/40):**
- **NEW**: "10x" is a specific, bold claim
- **EASY**: "Zero learning curve" explicitly addresses effort
- **SAFE**: "50,000 devs" provides concrete social proof
- **BIG**: "10x faster" promises transformation

**Pattern observed**: Headlines that hit all 4 dimensions explicitly score 30+.

### Result: ✅ PASS

---

## Test 3: Audit GitHub README

### What This Tests
The `/audit` command performs a comprehensive marketing analysis against all 5 frameworks.

### Frameworks Used
- 📘 *Take Their Money* (Milligan) — NESB scoring
- 📘 *Influence* (Cialdini) — 7 Persuasion Levers audit

### Mock Data
Used the actual AI Marketing repository: `https://github.com/az9713/ai-marketing`

### Input
```
audit https://github.com/az9713/ai-marketing
```

### Expected Behavior
- Diagnose awareness level
- Score NESB (0-40)
- Check all 7 persuasion levers
- Provide specific improvements

### Test Output

```
## Marketing Audit Report

**URL:** https://github.com/az9713/ai-marketing

### Overall Score: 72/100

---

### NESB Analysis: 28/40

| Dim  | Score | Assessment |
|------|-------|------------|
| NEW  | 7/10  | "First Claude Code plugin" + unique mechanism (5 frameworks) |
| EASY | 7/10  | "No configuration. No marketing degree required." |
| SAFE | 6/10  | References 5 bestselling books, but no user counts yet |
| BIG  | 8/10  | "Start converting" - transformation promise clear |

---

### Persuasion Levers: 5/7 present

| Lever | Present | Evidence |
|-------|---------|----------|
| ✅ Authority | Yes | 5 bestselling books, named authors |
| ✅ Social Proof | Partial | Book citations, but no user numbers |
| ✅ Reciprocity | Yes | Free plugin, MIT license |
| ✅ Liking | Yes | Developer-friendly tone, "built for developers" |
| ✅ Unity | Yes | "Developers who know their product is great" |
| ❌ Scarcity | No | N/A for open source |
| ❌ Commitment | No | No progressive engagement flow |

---

### Top 3 Improvements

1. **Add user/download numbers** - Even "10+ early adopters" builds social proof
2. **Add a testimonial quote** - One developer quote would boost SAFE
3. **Add before/after examples with real projects** - Concrete proof of transformation
```

### Analysis

**Strengths identified:**
- Clear unique mechanism (5 frameworks)
- Good authority signals (book references)
- Developer-friendly tone

**Gaps identified:**
- No quantified social proof (user counts)
- No testimonials
- No progressive engagement (commitment lever)

### Result: ✅ PASS

---

## Test 4: Compare Two Headlines

### What This Tests
Scoring two headlines side-by-side to demonstrate the power of loss aversion framing.

### Frameworks Used
- 📘 *Take Their Money* (Milligan) — NESB scoring
- 📘 *Yes! 50 Ways* (Cialdini et al.) — loss aversion principle

### Input
```
score "Build apps faster with AI"
score "Stop losing weekends to debugging. Ship in hours, not days."
```

### Expected Behavior
- Score both headlines
- Show clear winner with explanation
- Demonstrate loss aversion principle

### Test Output

```
#### Headline A: "Build apps faster with AI"

## NESB Score: 18/40

| Dim  | Score | Assessment |
|------|-------|------------|
| NEW  | 4/10  | Generic - everyone claims AI |
| EASY | 5/10  | "Faster" implies ease but vague |
| SAFE | 3/10  | No proof, no trust signals |
| BIG  | 6/10  | "Faster" is a benefit but not transformational |

---

#### Headline B: "Stop losing weekends to debugging. Ship in hours, not days."

## NESB Score: 29/40

| Dim  | Score | Assessment |
|------|-------|------------|
| NEW  | 6/10  | Specific framing (weekends, hours vs days) |
| EASY | 8/10  | "Hours, not days" - clear time savings |
| SAFE | 6/10  | Relatable pain point builds trust |
| BIG  | 9/10  | Loss aversion ("stop losing weekends") is powerful |

---

### Winner: Headline B (+11 points)

**Why:** Loss aversion ("stop losing") is 2x more motivating than gain framing
("build faster"). Specific time contrast ("hours, not days") beats vague claims.
```

### Analysis

**Key insight demonstrated:**
- Loss framing ("stop losing") outperforms gain framing ("build faster")
- Specific numbers ("hours, not days") beat vague claims ("faster")
- Relatable pain points ("weekends to debugging") create emotional connection

### Result: ✅ PASS

---

## Test 5: Generate a README

### What This Tests
The `/readme` command generates a framework-optimized README from project details.

### Frameworks Used
- 📘 *Take Their Money* (Milligan) — NESB-optimized hero
- 📘 *Influence* (Cialdini) — social proof sections
- 📘 *Breakthrough Advertising* (Schwartz) — awareness-matched messaging

### Mock Data

**Mock Project:** A CLI tool that converts CSV files to JSON

| Question | Answer |
|----------|--------|
| What does it do? | Converts CSV files to JSON |
| Who is it for? | Developers working with data pipelines |
| What makes it different? | 10x faster, handles malformed CSVs |
| Social proof? | Used by 500 developers |

### Input
```
readme
```
(Then provide mock project details when prompted)

### Expected Behavior
- Generate complete README
- Lead with benefits, not features
- Hit all 4 NESB dimensions in hero
- Include social proof section

### Test Output

```markdown
# csv-to-json

**Stop wrestling with broken CSV parsers. Convert any CSV to clean JSON in milliseconds.**

The fastest CSV-to-JSON converter that actually handles real-world data —
malformed rows, encoding issues, and all. Trusted by 500+ developers in production.

[![npm](https://img.shields.io/npm/v/csv-to-json)](https://npmjs.com/csv-to-json)
[![Downloads](https://img.shields.io/badge/developers-500%2B-green)](https://github.com)

## The Problem

You've got CSVs. They're messy. Existing parsers choke on:
- Malformed rows
- Mixed encodings
- Inconsistent delimiters

**You just want JSON. Without the headaches.**

## The Solution

```bash
npx csv-to-json input.csv output.json
```

That's it. 30 seconds to clean JSON.

## Why csv-to-json?

| Feature | Others | csv-to-json |
|---------|--------|-------------|
| Speed | Seconds | **Milliseconds** |
| Malformed rows | ❌ Crashes | ✅ Auto-repairs |
| Encoding | UTF-8 only | ✅ Auto-detects |

## Quick Start

```bash
npm install -g csv-to-json
csv-to-json data.csv --pretty
```

## Who Uses This

> "Saved us hours of data pipeline debugging." — @devuser

500+ developers trust csv-to-json in production.
```

### Analysis

**NESB breakdown of generated hero:**
- **NEW**: "Actually handles real-world data" (differentiator)
- **EASY**: "Milliseconds", "30 seconds to clean JSON"
- **SAFE**: "500+ developers in production"
- **BIG**: "Stop wrestling" (loss aversion), complete solution

**Hero NESB Score: 31/40**

### Result: ✅ PASS

---

## Test 6: Analyze a Competitor

### What This Tests
The `/compete` command analyzes competitor positioning to find differentiation opportunities.

### Frameworks Used
- 📘 *Take Their Money* (Milligan) — NESB scoring
- 📘 *Breakthrough Advertising* (Schwartz) — market sophistication analysis
- 📘 *Influence* (Cialdini) — identifying missing persuasion levers

### Mock Data

**Fictional Competitor: CodeAI Pro**

| Attribute | Value |
|-----------|-------|
| Hero | "AI-Powered Development Platform" |
| Tagline | "Build faster with AI" |
| Social proof | "10,000+ users" |
| Mechanism | Not explained |

### Input
```
compete https://competitor-product.com
```

### Expected Behavior
- Score competitor's NESB
- Identify their persuasion levers
- Find positioning gaps
- Suggest differentiation strategies

### Test Output

```
## Competitor Analysis: CodeAI Pro

**URL:** https://competitor-product.com

---

### Positioning
"The AI-powered development platform for modern teams"

**Target Audience:** Development teams at mid-size companies

---

### NESB Score: 22/40

| Dim  | Score | Assessment |
|------|-------|------------|
| NEW  | 4/10  | Generic "AI-powered" — no unique mechanism |
| EASY | 6/10  | "Build faster" implies ease |
| SAFE | 7/10  | "10,000+ users" provides social proof |
| BIG  | 5/10  | "Modern teams" — vague transformation |

---

### Strengths
- ✅ Strong social proof (10,000+ users)
- ✅ Clean, professional design
- ✅ Clear pricing page

### Weaknesses
- ❌ Generic "AI-powered" claims (everyone says this)
- ❌ No unique mechanism explained (why is their AI different?)
- ❌ No community/movement aspect
- ❌ No specific pain point addressed

---

### Your Opportunity

| Gap | Your Counter-Position |
|-----|----------------------|
| Generic AI claims | Position as "The first AI that [specific mechanism]" |
| No pain point | Lead with specific developer pain: "Stop losing hours to..." |
| No tribe | Build community: "For developers who refuse to..." |
| Enterprise focus | Own indie/startup niche: "Built for solo devs, not committees" |

**Recommended positioning:**
"The [specific niche] alternative to CodeAI Pro — built for developers who ship, not committees."
```

### Analysis

**Gaps identified for exploitation:**
1. Generic claims → Counter with specific mechanism
2. Enterprise focus → Counter-position for indie developers
3. No community → Build tribe/movement
4. No pain point → Lead with developer frustrations

### Result: ✅ PASS

---

## Test 7: Extract Writing Voice

### What This Tests
The `/voice` command analyzes existing content to extract a voice profile for consistent content generation.

### Framework Used
🔧 *Supporting Capability* — Voice extraction ensures framework-optimized content sounds authentic

### Mock Data

**Sample Writing Provided:**
```
I built this because I was tired of the problem.
Most tools overcomplicate things. This one doesn't.
It does one thing well. No config. No BS.
If you've ever rage-quit a setup wizard, this is for you.
```

### Input
```
voice

Here's some of my existing writing:
"I built this because I was tired of the problem.
Most tools overcomplicate things. This one doesn't.
It does one thing well. No config. No BS.
If you've ever rage-quit a setup wizard, this is for you."
```

### Expected Behavior
- Analyze tone dimensions
- Identify signature patterns
- Create reusable voice profile
- Provide generation guidelines

### Test Output

```
## Voice Profile

### Voice in 3 Words
**Direct, Practical, Relatable**

---

### Tone Analysis

| Dimension | Score | Notes |
|-----------|-------|-------|
| Formality | 2/5 | Casual, conversational |
| Technical | 2/5 | Avoids jargon |
| Humor | 3/5 | Dry, frustrated humor ("rage-quit") |
| Directness | 5/5 | Very direct, no fluff |
| Warmth | 3/5 | Empathetic but not soft |

---

### Signature Patterns

1. **Short, punchy sentences** — Average 6 words per sentence
2. **"I built this because..."** openings — Personal origin story
3. **Problem-first framing** — Leads with pain, then solution
4. **Anti-establishment tone** — "No BS", against complexity
5. **Second-person connection** — "If you've ever..."

---

### Vocabulary Fingerprint

| Uses | Avoids |
|------|--------|
| "Tired of", "rage-quit" | Corporate jargon |
| "One thing well" | Feature lists |
| "No config, no BS" | Technical specs |
| Direct pronouns (I, you) | Passive voice |

---

### When Generating for This Voice

1. Keep sentences under 10 words
2. Use "I" and "you" frequently
3. Start with the problem, not the solution
4. Include one moment of frustrated humor
5. Avoid: "leverage", "utilize", "solution", "platform"
6. End with relatable developer experience
```

### Analysis

**Voice characteristics identified:**
- Very direct (5/5 directness)
- Casual tone (2/5 formality)
- Problem-first structure
- Anti-corporate vocabulary

**Practical application:** Future content generation should follow these patterns to maintain authentic voice.

### Result: ✅ PASS

---

## Test 8: Write a Tweet Thread

### What This Tests
Generating a viral-optimized tweet thread that applies multiple frameworks.

### Frameworks Used
- 📘 *Influence* (Cialdini) — social proof in testimonials
- 📘 *Yes! 50 Ways* (Cialdini et al.) — storytelling hook
- 📘 *One Sentence Persuasion* (Warren) — tribe-building through shared struggle

### Mock Data

**Mock Project:** CSV-to-JSON CLI tool
- 500 developers using it
- Handles malformed data
- Fast conversion

### Input
```
Generate a 5-tweet thread announcing my project: a CLI tool that converts
CSV to JSON, handles malformed data, used by 500 developers.
```

### Expected Behavior
- 5-tweet thread
- Hook → Problem → Solution → Proof → CTA structure
- Apply persuasion frameworks

### Test Output

```
## Tweet Thread (5 tweets)

---

**Tweet 1 (Hook):**
I spent 3 months building in silence.

Today, I'm sharing csv-to-json.

It does one thing: converts messy CSVs to clean JSON.

Here's what I learned 🧵

---

**Tweet 2 (Problem):**
Most CSV parsers fail on real data.

They assume perfect formatting.
They choke on encoding issues.
They crash on malformed rows.

That's why 90% of data pipeline bugs start with "the CSV was weird."

---

**Tweet 3 (Solution):**
csv-to-json works differently.

Instead of failing on bad data, it repairs it.
Instead of guessing encoding, it detects it.

The result? Clean JSON in milliseconds, not hours of debugging.

---

**Tweet 4 (Proof):**
Don't take my word for it:

"Saved us hours of data pipeline debugging." — @datadev

500+ developers are already using it in production.

---

**Tweet 5 (CTA):**
Try it free:
npm install -g csv-to-json

Star on GitHub: github.com/user/csv-to-json

What's the worst CSV you've ever had to parse? 👇
```

### Analysis

**Thread structure:**
1. **Hook**: Personal story + curiosity gap
2. **Problem**: Agitate shared pain
3. **Solution**: Contrast mechanism
4. **Proof**: Social proof + testimonial
5. **CTA**: Clear action + engagement question

**Frameworks applied:**
- Cialdini's Social Proof (500 developers, testimonial)
- Warren's tribe-building (shared struggle with CSVs)
- Yes! 50 Ways storytelling (personal journey)

### Result: ✅ PASS

---

## Test 9: Rewrite with Loss Aversion

### What This Tests
Transforming gain-framed copy into loss-framed copy using loss aversion principles.

### Framework Used
📘 *Yes! 50 Ways to Be Persuasive* (Cialdini et al.) — loss aversion is one of the 50 evidence-based persuasion tactics

### Input
```
Rewrite this using loss aversion: "Increase your productivity by 50%"
```

### Expected Behavior
- Transform from gain frame to loss frame
- Explain why loss framing is stronger
- Provide multiple alternatives

### Test Output

```
## Loss Aversion Rewrite

### Original (Gain Frame)
> "Increase your productivity by 50%"

### Loss Aversion Rewrite
> "Stop losing 4 hours every day to context switching"

---

### Why It's Stronger

| Aspect | Original | Rewrite |
|--------|----------|---------|
| Frame | Gain (+50%) | Loss (4 hours/day) |
| Specificity | Vague percentage | Concrete time |
| Emotional trigger | Aspiration | Fear of waste |
| Psychological power | 1x | **2x** (loss aversion) |

---

### The Science

Research shows people work **twice as hard to avoid losses** as they do to
achieve equivalent gains.

- "Stop losing" triggers immediate attention
- Specific time loss (4 hours) is more tangible than abstract percentage
- Daily framing ("every day") compounds the perceived loss

---

### More Alternatives

1. **"Stop losing 20 hours every week to busywork"** — Weekly compounds impact
2. **"You're bleeding 4 hours daily. Here's how to stop."** — Urgent, visceral
3. **"Every hour you waste on X is an hour you'll never get back"** — Irreversibility
```

### Analysis

**Key transformations:**
| Gain Frame | Loss Frame |
|------------|------------|
| "Increase" | "Stop losing" |
| "50%" | "4 hours" (specific) |
| Abstract benefit | Concrete pain |

**Why this works:** Kahneman's research shows losses are psychologically 2x more impactful than equivalent gains.

### Result: ✅ PASS

---

## Test 10: Create a Tagline

### What This Tests
Generating multiple taglines that each score 25+ on NESB.

### Frameworks Used
- 📘 *Take Their Money* (Milligan) — NESB scoring (25/40 minimum target)
- 📘 *Influence* (Cialdini) — Unity and Liking levers in tribal messaging

### Mock Data

**Project:** CSV-to-JSON converter CLI
**Constraint:** Each tagline must score 25/40 or higher

### Input
```
Create 5 taglines for a CSV-to-JSON converter CLI.
Each should score at least 25/40 on NESB.
```

### Expected Behavior
- Generate 5 taglines
- Each scores 25+
- Show NESB breakdown for each

### Test Output

```
## 5 NESB-Optimized Taglines

---

### 1. "Messy CSVs in. Clean JSON out. Milliseconds."
**Score: 28/40**
- NEW: 6/10 — Implies handling messy data (differentiator)
- EASY: 8/10 — "Milliseconds" = instant
- SAFE: 6/10 — Predictable outcome
- BIG: 8/10 — Transformation clear

---

### 2. "The last CSV parser you'll ever need."
**Score: 26/40**
- NEW: 5/10 — "Last" implies finality/uniqueness
- EASY: 7/10 — No more searching
- SAFE: 7/10 — Confidence, reliability
- BIG: 7/10 — End of a journey

---

### 3. "500 developers. Zero CSV headaches."
**Score: 31/40**
- NEW: 6/10 — Specific number is unexpected
- EASY: 8/10 — "Zero headaches"
- SAFE: 9/10 — 500 developers = social proof
- BIG: 8/10 — Complete pain elimination

---

### 4. "Stop debugging CSVs. Start shipping."
**Score: 29/40**
- NEW: 6/10 — Fresh framing
- EASY: 7/10 — Implies time savings
- SAFE: 6/10 — Reliable outcome implied
- BIG: 10/10 — Loss aversion + transformation

---

### 5. "Broken CSVs? Fixed. In one command."
**Score: 27/40**
- NEW: 6/10 — Problem-solution clarity
- EASY: 9/10 — "One command" = minimal effort
- SAFE: 6/10 — Predictable fix
- BIG: 6/10 — Solves specific pain
```

### Analysis

**Score distribution:**
- All 5 taglines score 25+ ✅
- Highest: #3 at 31/40 (strong social proof)
- Average: 28.2/40

**Best performer breakdown (#3: "500 developers. Zero CSV headaches."):**
- SAFE dimension dominates (9/10) due to specific social proof
- "Zero headaches" is powerful EASY claim
- Specific number (500) creates unexpected NEW element

### Result: ✅ PASS

---

## Summary

### Overall Test Results

| Test | Use Case | Result | Key Framework |
|------|----------|--------|---------------|
| 1 | Score a Headline | ✅ PASS | NESB |
| 2 | Improve a Weak Headline | ✅ PASS | NESB |
| 3 | Audit GitHub README | ✅ PASS | NESB + Cialdini |
| 4 | Compare Two Headlines | ✅ PASS | NESB + Loss Aversion |
| 5 | Generate a README | ✅ PASS | All 5 Frameworks |
| 6 | Analyze a Competitor | ✅ PASS | NESB + Schwartz + Cialdini |
| 7 | Extract Writing Voice | ✅ PASS | Supporting Capability |
| 8 | Write a Tweet Thread | ✅ PASS | Cialdini + Warren |
| 9 | Rewrite with Loss Aversion | ✅ PASS | Yes! 50 Ways |
| 10 | Create a Tagline | ✅ PASS | NESB + Cialdini |

**Result: 10/10 tests passed**

### Key Insights from Testing

1. **NESB is foundational** — Used in 8 of 10 tests
2. **Loss aversion is powerful** — Gain frames score 10+ points lower than loss frames
3. **Specific numbers beat vague claims** — "500 developers" > "many users"
4. **Voice extraction enables authenticity** — Framework-optimized content can still sound human
5. **Multi-framework audits reveal gaps** — Combining frameworks catches more issues

### How to Use These Tests

1. **As learning examples** — Study the outputs to understand framework application
2. **As benchmarks** — Compare your own outputs to these results
3. **As templates** — Use output formats as starting points
4. **As validation** — Verify your plugin installation produces similar results

---

## Acknowledgements

- Inspired by: ["These 5 Books Reveal Why Most AI Products Don't Sell"](https://www.youtube.com/watch?v=OLjTWl4Ci10)
- All tests executed by: [Claude Code](https://claude.ai/code) + Claude Opus 4.5
- Test documentation generated: January 2025
