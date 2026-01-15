# AI Marketer - Project Context

## What This Project Is

AI Marketer is a Claude Code plugin that helps developers write better marketing content for their projects. It implements 5 proven marketing psychology frameworks from bestselling books.

---

## COMMANDS - IMPORTANT

When the user asks to score, audit, generate a readme, analyze competitors, or extract voice, execute these commands immediately. Users can type naturally (e.g., "score this headline") or use slash commands if the plugin is registered.

### score [text]

Score the given headline/copy against the NESB framework (0-40).

**How to score:**
- **NEW** (0-10): Is it novel? "The first...", "Unlike...", unique mechanism?
- **EASY** (0-10): Is it effortless? "One-click", "Zero config", "5 minutes"?
- **SAFE** (0-10): Is it trustworthy? "Trusted by X", testimonials, guarantees?
- **BIG** (0-10): Is the outcome transformational? "10x", "Dominate", major result?

**Output format:**
```
## NESB Score: XX/40

| Dim  | Score | Assessment |
|------|-------|------------|
| NEW  | X/10  | [why]      |
| EASY | X/10  | [why]      |
| SAFE | X/10  | [why]      |
| BIG  | X/10  | [why]      |

### Stronger Alternatives
1. "[improved version]" - XX/40
2. "[improved version]" - XX/40
```

**Scoring guide:**
- 0-15: Weak (generic, forgettable)
- 16-24: Average (missing dimensions)
- 25-32: Strong (hits most triggers)
- 33-40: Exceptional (hits all 4 powerfully)

### audit [URL or content]

Full marketing audit against all 5 frameworks:
1. Diagnose awareness level (Schwartz)
2. Score NESB (Milligan)
3. Check 7 persuasion levers (Cialdini)
4. Identify tactical improvements (Yes! 50 Ways)
5. Assess tribe-building elements (Warren)

Output: Comprehensive report with scores and specific improvements.

### readme

Generate an optimized GitHub README. Ask the user:
1. What does your project do?
2. Who is it for?
3. What makes it different?
4. Any social proof (users, stars)?

Then generate a README that:
- Leads with benefits (not features)
- Hits all 4 NESB dimensions in the hero
- Includes social proof section
- Has quick-start in under 30 seconds
- Uses loss-aversion framing

### compete [URL]

Analyze competitor positioning:
1. Fetch and analyze their website/README
2. Score their NESB
3. Identify their persuasion levers
4. Find gaps in their positioning
5. Suggest differentiation opportunities

### voice [URL or content]

Extract voice profile from existing content:
- Tone (formal/casual)
- Technical level
- Sentence patterns
- Vocabulary preferences
- Brand personality

Output a voice profile that can be used for future content generation.

---

## The 5 Marketing Frameworks

### Framework 1: Problem Awareness Spectrum (Schwartz)

| Level | Description | Copy Approach |
|-------|-------------|---------------|
| **Unaware** | Don't know they have a problem | Lead with the symptom |
| **Problem Aware** | Know the problem, not solutions | Sell the outcome |
| **Solution Aware** | Know solutions exist, not yours | Sell your mechanism |
| **Product Aware** | Know you, not convinced | Sell proof & differentiation |
| **Most Aware** | Ready to buy | Sell the offer/price |

**Key insight**: Most AI founders pitch "Solution Aware" copy to "Problem Aware" audiences.

### Framework 2: 7 Persuasion Levers (Cialdini)

| Lever | Definition | Application |
|-------|------------|-------------|
| **Authority** | People follow experts | Logos, endorsements, credentials |
| **Social Proof** | People follow crowds | User counts, testimonials |
| **Commitment** | People honor commitments | Progressive onboarding |
| **Liking** | People buy from those like them | Relatable brand voice |
| **Reciprocity** | People return favors | Free value first |
| **Scarcity** | People want rare things | Limited availability |
| **Unity** | People join tribes | Shared identity, community |

### Framework 3: Tactical Techniques (Yes! 50 Ways)

Key tactics:
- **Loss Aversion**: "Stop losing X" > "Gain X" (2x more powerful)
- **Specific Social Proof**: "10,000 senior engineers" > "thousands of users"
- **Framing**: "Most developers do X" > "Don't do Y"
- **Similarity**: Highlight shared identity
- **Contrast Effect**: Show alternative first

### Framework 4: NESB (Milligan)

Every headline must hit 4 emotional triggers:

| Trigger | Brain Response | Examples |
|---------|----------------|----------|
| **NEW** | Craves novelty | "The first...", "Revolutionary" |
| **EASY** | Conserves energy | "One-click", "Zero config" |
| **SAFE** | Fears risk | "Trusted by...", "Guaranteed" |
| **BIG** | Wants transformation | "10x", "Dominate", "Transform" |

### Framework 5: Tribe Building (Warren)

> "People will do anything for those who encourage their dreams, justify their failures, allay their fears, confirm their suspicions, and help throw rocks at their enemies."

| Element | Application |
|---------|-------------|
| **Encourage Dreams** | "You can build production AI without a PhD" |
| **Justify Failures** | "It's not your fault - the tools were too hard" |
| **Allay Fears** | "You won't break production" |
| **Confirm Suspicions** | "The old system was rigged" |
| **Throw Rocks** | Define common enemy: "Legacy gatekeepers" |

---

## Project Structure

```
ai-marketing/
├── CLAUDE.md                          # This file (auto-loaded by Claude)
├── README.md                          # GitHub README
├── LICENSE                            # MIT License
├── docs/                              # Documentation
│   ├── user-guide/                    # User documentation
│   └── developer-guide/               # Developer documentation
└── .claude/
    └── plugins/
        └── ai-marketer/               # Plugin files
            ├── .claude-plugin/        # Plugin manifest
            │   └── plugin.json
            ├── skills/                # Framework details
            ├── agents/                # Agent definitions
            └── commands/              # Command references
```

---

## Acknowledgements

- Inspired by: ["These 5 Books Reveal Why Most AI Products Don't Sell"](https://www.youtube.com/watch?v=OLjTWl4Ci10)
- Generated by: [Claude Code](https://claude.ai/code) + Claude Opus 4.5
