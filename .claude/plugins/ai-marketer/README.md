# AI Marketer

**Stop writing marketing copy that sounds like every other AI tool. Start converting.**

The first Claude Code plugin that applies 5 proven marketing psychology frameworks to your content - so your GitHub repos, landing pages, and social posts actually get noticed.

[![Claude Code Plugin](https://img.shields.io/badge/Claude_Code-Plugin-7C3AED)](https://claude.ai)
[![Based on 5 Bestselling Books](https://img.shields.io/badge/Based_on-5_Bestselling_Books-green)](https://github.com)
[![MIT License](https://img.shields.io/badge/License-MIT-blue)](LICENSE)

## The Problem

You've built something amazing. But your README sounds like every other AI tool: *"AI-powered solution for..."*

Generic copy doesn't convert. And most developers don't have time to study marketing psychology.

**That's why 90% of great projects never get the attention they deserve.**

## The Solution

AI Marketer brings 5 proven marketing frameworks into your Claude Code workflow:

| Framework | What It Does | Based On |
|-----------|--------------|----------|
| **Awareness Analyzer** | Match your copy to your audience's awareness level | *Breakthrough Advertising* (Schwartz) |
| **Persuasion Auditor** | Score content against 7 psychological triggers | *Influence* (Cialdini) |
| **Copy Optimizer** | Apply tactical persuasion techniques | *Yes! 50 Scientifically Proven Ways* |
| **NESB Scorer** | Ensure every headline hits NEW, EASY, SAFE, BIG | *Take Their Money* (Milligan) |
| **Tribe Builder** | Create movement-building copy that inspires loyalty | *One Sentence Persuasion Course* (Warren) |

## Quick Start

```bash
# Navigate to the project folder containing the plugin
cd /path/to/ai-marketing

# Start Claude Code (plugin auto-loads from .claude/plugins/)
claude

# Score any headline instantly
/score "Your AI product headline here"

# Full marketing audit of your repo
/audit https://github.com/you/your-project

# Generate an optimized README
/readme
```

**That's it.** No configuration. No marketing degree required.

## What You Can Do

### `/score` - Instant Headline Scoring

```
/score AI-powered code completion

> NESB Score: 12/40 (Weak)
> - NEW: 3/10 - Generic, everyone says this
> - EASY: 4/10 - Implied but not stated
> - SAFE: 2/10 - No trust signals
> - BIG: 3/10 - Small improvement promised
>
> Try instead: "The first AI that reads your entire codebase -
> ship 10x faster with zero setup. Trusted by 50,000 developers."
> Score: 34/40
```

### `/audit` - Full Marketing Audit

Analyze any URL or content against all 5 frameworks:
- Awareness level diagnosis
- NESB scoring
- Persuasion lever check
- Tactical improvement opportunities
- Tribe-building elements

### `/readme` - Generate Optimized README

Creates a conversion-focused README that:
- Leads with benefits, not features
- Includes social proof sections
- Uses loss-aversion framing
- Hits all 4 NESB dimensions
- Matches your existing voice

### `/compete` - Competitor Analysis

Analyze competitor websites to find:
- Gaps in their positioning
- Underserved angles you can own
- Differentiation opportunities
- Counter-positioning strategies

### `/voice` - Extract Your Voice

Analyze your existing content to:
- Extract tone and vocabulary patterns
- Create a voice profile for consistency
- Adapt for different platforms
- Never sound like generic AI output

## Why These Frameworks?

These aren't random marketing tips. They're the distilled wisdom from 5 bestselling books that have shaped modern advertising:

1. **Breakthrough Advertising** by Eugene Schwartz - The Bible of direct response marketing
2. **Influence** by Robert Cialdini - The science of persuasion, cited 100,000+ times
3. **Yes! 50 Scientifically Proven Ways** by Cialdini et al - Evidence-based tactics
4. **Take Their Money** by Kyle Milligan - Modern copywriting for the internet age
5. **One Sentence Persuasion Course** by Blair Warren - How movements are built

## Before & After

### Before (Generic AI Copy)
> "An AI-powered development tool that helps developers write better code faster using advanced machine learning."

**NESB Score: 14/40** - Generic, forgettable, sounds like everyone else.

### After (Framework-Optimized)
> "Stop losing hours to debugging. Join 10,000 senior engineers who ship 3x faster with context-aware AI. Unlike generic autocomplete, we read your entire codebase."

**NESB Score: 35/40**
- **NEW**: "context-aware", "read your entire codebase"
- **EASY**: "3x faster"
- **SAFE**: "10,000 senior engineers"
- **BIG**: "Stop losing hours"

## Plugin Structure

```
.claude/plugins/ai-marketer/
├── skills/           # 8 specialized marketing skills
├── agents/           # 3 subagents for complex tasks
├── commands/         # 5 slash commands
└── hooks/            # Auto-review triggers
```

## The Frameworks in Detail

### 1. Problem Awareness Spectrum (Schwartz)

Your audience isn't one-size-fits-all. They're at different stages:

| Level | What They Know | Your Approach |
|-------|----------------|---------------|
| Unaware | Don't know they have a problem | Lead with symptoms |
| Problem Aware | Feel pain, don't know solutions exist | Sell the outcome |
| Solution Aware | Know solutions exist, not yours | Sell your mechanism |
| Product Aware | Know you, haven't bought | Sell proof & offers |
| Most Aware | Ready to buy | Sell price & urgency |

**Most AI founders pitch "Solution Aware" copy to "Problem Aware" audiences.** That's why they don't convert.

### 2. The 7 Persuasion Levers (Cialdini)

Every piece of marketing should trigger at least 3:

- **Authority** - Expert endorsements, credentials
- **Social Proof** - Numbers, testimonials, logos
- **Commitment** - Progressive engagement
- **Liking** - Relatable brand personality
- **Reciprocity** - Free value before asking
- **Scarcity** - Limited availability
- **Unity** - Tribal belonging

### 3. NEW, EASY, SAFE, BIG (Milligan)

The 4 emotional triggers that bypass rational objections:

| Trigger | Brain Response | How to Hit It |
|---------|----------------|---------------|
| **NEW** | Craves novelty | "The first...", "Unlike..." |
| **EASY** | Conserves energy | "One-click", "Zero config" |
| **SAFE** | Fears risk | "Trusted by...", "Guaranteed" |
| **BIG** | Wants transformation | "10x", "Dominate", "Transform" |

### 4. Tribe Building (Warren)

> "People will do anything for those who encourage their dreams, justify their failures, allay their fears, confirm their suspicions, and help throw rocks at their enemies."

This is how movements are built. Not features - belonging.

## Who This Is For

- **Indie hackers** tired of great products getting ignored
- **Developer advocates** who need compelling content fast
- **Startup founders** who can't afford marketing agencies
- **Open source maintainers** who want more contributors
- **Anyone** who's written "AI-powered" in their README

## Who This Is NOT For

- People selling snake oil (the frameworks only amplify truth)
- Those who want to manipulate rather than communicate
- Anyone not committed to providing genuine value

## Contributing

This plugin is open source. Contributions welcome:

1. Fork the repository
2. Create a feature branch
3. Submit a pull request

Ideas for contributions:
- Additional content templates
- New platform formats (YouTube, newsletters)
- Framework refinements
- Language translations

## License

MIT - Use it, modify it, share it.

---

**Built for developers who know their product is great - and want the world to know it too.**

*Stop blending in. Start converting.*
