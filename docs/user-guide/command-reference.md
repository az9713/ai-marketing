# Command Reference

This document provides detailed reference information for all AI Marketer commands. Each command is explained with syntax, parameters, examples, and expected output.

---

## How Commands Work

There are two ways to invoke any command:

| Method | Syntax | Mechanism |
|--------|--------|-----------|
| **Natural Language** | `score "headline"` | Claude uses CLAUDE.md instructions |
| **Slash Command** | `/ai-marketer:score "headline"` | Claude loads `commands/score.md` |

### Are the results different?

**No.** Both methods produce identical results because:

1. **CLAUDE.md is always loaded** when Claude enters the project directory
2. CLAUDE.md contains the complete framework instructions
3. Both methods have access to the same scoring knowledge

The slash command formally invokes the plugin command file, while natural language relies on CLAUDE.md directly. The output is the same.

*For technical details, see [Invocation Explained](../developer-guide/invocation-explained.md).*

---

## Quick Reference Table

| Command | Purpose | Input | Output |
|---------|---------|-------|--------|
| `score` | Score headline/copy | Text | NESB score (0-40) |
| `audit` | Full marketing audit | URL or text | Full report (0-100) |
| `readme` | Generate README | Interactive | Markdown file |
| `compete` | Analyze competitor | URL | Competitive analysis |
| `voice` | Extract voice patterns | URL or text | Voice profile |

---

## `score` - Headline Scoring

### Purpose
Instantly score any headline, tagline, or piece of copy against the NESB framework (NEW, EASY, SAFE, BIG).

### Syntax
```
score <text>
score "<text with spaces>"
```

Or with slash command (if plugin registered): `/ai-marketer:score <text>`

### Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| text | Yes | The headline or copy to score |

### Examples

**Example 1: Simple headline**
```
score AI-powered code completion
```

**Example 2: Complex headline (use quotes)**
```
score "Stop losing hours to debugging. Ship 3x faster with context-aware AI."
```

**Example 3: Tagline**
```
score "Ship faster. Break nothing."
```

### Output Format

```
NESB Score: 32/40 (Strong)

| Dimension | Score | Analysis |
|-----------|-------|----------|
| NEW | 8/10 | "Context-aware" implies novel approach |
| EASY | 7/10 | "Ship 3x faster" = effort reduction |
| SAFE | 6/10 | Implied by "context-aware" but could add proof |
| BIG | 9/10 | "3x faster" is a transformational claim |

Strengths:
- Loss aversion opening ("Stop losing")
- Specific outcome claim (3x)
- Mechanism hint (context-aware)

Improvements:
- Add social proof for SAFE dimension
- Consider adding user count

Alternative:
"Stop losing hours to debugging. Join 50,000 developers
who ship 3x faster with context-aware AI."
Score: 36/40
```

### Scoring Criteria

| Score Range | Rating | Meaning |
|-------------|--------|---------|
| 0-10 | Weak | Missing most emotional triggers |
| 11-20 | Below Average | Has 1-2 triggers, needs work |
| 21-27 | Average | Functional but not compelling |
| 28-34 | Strong | Hits most triggers effectively |
| 35-40 | Excellent | Optimized for conversion |

### Tips
- Always test multiple variations
- Aim for 28+ before publishing
- The "Alternative" suggestions are starting points, not final copy
- Combine multiple suggestions to create your best version

---

## `audit` - Full Marketing Audit

### Purpose
Analyze any URL or content against all 5 marketing frameworks to get a comprehensive quality score and improvement recommendations.

### Syntax
```
audit <url>
audit [paste content directly]
```

Or with slash command (if plugin registered): `/ai-marketer:audit <url>`

### Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| url/content | Yes | The URL to analyze or text to audit |

### Examples

**Example 1: GitHub repository**
```
audit https://github.com/yourusername/your-project
```

**Example 2: Landing page**
```
audit https://your-product.com
```

**Example 3: Pasted content**
```
audit

Here's my README content:
# My Project
An AI-powered tool for developers...
[rest of content]
```

### Output Format

```
Marketing Audit Report
======================

URL: https://github.com/example/project
Content Type: GitHub README

OVERALL SCORE: 58/100

Section Breakdown
-----------------

1. NESB Analysis: 22/40
   | Dimension | Score | Finding |
   |-----------|-------|---------|
   | NEW | 5/10 | Generic "AI-powered" claim |
   | EASY | 6/10 | Quick start present but buried |
   | SAFE | 4/10 | No social proof |
   | BIG | 7/10 | Good outcome claims |

2. Persuasion Levers: 3/7 present
   ✅ Authority - Technical credentials mentioned
   ✅ Liking - Friendly, relatable tone
   ✅ Reciprocity - Free to use
   ❌ Social Proof - No user numbers or testimonials
   ❌ Scarcity - N/A for open source
   ❌ Unity - No community aspect
   ❌ Commitment - No progressive engagement

3. Awareness Level: Solution Aware
   Current copy assumes audience knows solutions exist.
   Recommendation: Add Problem Aware messaging for
   broader appeal.

4. Tactical Elements: 4/10
   ❌ Loss aversion framing
   ❌ Specific social proof
   ✅ Contrast with alternatives
   ✅ Feature-to-benefit translation (partial)

5. Tribe Building: 1/5 elements
   ✅ Encourage dreams (somewhat)
   ❌ Justify failures
   ❌ Allay fears
   ❌ Confirm suspicions
   ❌ Throw rocks at enemies

Top 5 Recommendations
---------------------
1. Add user/download numbers to hero section (+8 points)
2. Include a testimonial quote (+6 points)
3. Lead with pain point, not features (+5 points)
4. Add "Get started in 30 seconds" claim (+4 points)
5. Define a common enemy for tribe building (+4 points)

Rewritten Hero Section
----------------------
Current:
"An AI-powered development tool"

Suggested:
"Stop losing hours to debugging. The first AI that
reads your entire codebase - ship 10x faster with
zero setup. Trusted by 10,000+ developers."
```

### Scoring Components

| Component | Max Points | Weight |
|-----------|------------|--------|
| NESB Score | 40 | 40% |
| Persuasion Levers | 7 (×4.3) = 30 | 30% |
| Tactical Elements | 10 | 10% |
| Tribe Building | 5 (×4) = 20 | 20% |
| **Total** | **100** | **100%** |

### Tips
- Run audit before and after changes to measure improvement
- Focus on the "Top 5 Recommendations" for biggest impact
- Use the "Rewritten" sections as inspiration, not final copy
- Re-audit until you hit 70+ for quality content

---

## `readme` - Generate README

### Purpose
Generate a conversion-focused GitHub README applying all 5 marketing frameworks.

### Syntax
```
readme
```

Or with slash command (if plugin registered): `/ai-marketer:readme`

### Parameters
This command is interactive. Claude will ask you questions.

### Interactive Flow

**Step 1: Project Description**
```
Claude: What does your project do?
(Explain it like you would to a smart friend who isn't technical)

You: It's a CLI tool that helps developers write better commit messages
by analyzing the code changes and suggesting descriptions.
```

**Step 2: Target Audience**
```
Claude: Who is this for? Who would benefit most?

You: Developers who work in teams and want consistent,
meaningful commit history.
```

**Step 3: Differentiation**
```
Claude: What makes this different from alternatives?
(Or if there are no direct alternatives, what's unique about your approach?)

You: Unlike simple templates, it actually reads the diff and
understands what changed. It also learns your team's style.
```

**Step 4: Social Proof**
```
Claude: Do you have any social proof? This could be:
- Number of users/downloads
- GitHub stars
- Testimonials
- Notable users/companies
- Media mentions

You: We have 500 GitHub stars and 2,000 weekly downloads.
One user said "This saved me 30 minutes every day."
```

### Output Format

Claude generates a complete README with:

```markdown
# CommitGenius

**Stop writing vague commit messages. Start telling meaningful stories.**

The first AI that reads your actual code changes - not just the files - to suggest clear,
consistent commit messages. Trusted by 2,000+ developers weekly.

[![GitHub stars](https://img.shields.io/github/stars/you/commitgenius)](...)
[![Weekly Downloads](https://img.shields.io/npm/dw/commitgenius)](...)

## The Problem

We've all been there:
- "Fixed stuff"
- "Updates"
- "WIP"

Bad commit messages make debugging a nightmare and code review impossible.

## The Solution

CommitGenius reads your diff and understands what you actually changed:

```bash
$ git diff | commitgenius

Suggested: "Add user authentication with JWT tokens
- Implement login/logout endpoints
- Add token refresh middleware
- Include rate limiting for auth routes"
```

[Continue with full README structure...]
```

### README Sections Generated

1. **Hero** - NESB-optimized headline and one-liner
2. **Problem Statement** - Pain point that resonates
3. **Solution** - Your product with key differentiator
4. **Quick Start** - Get running in minimal steps
5. **Features** - Benefits, not just features
6. **Social Proof** - Stars, users, testimonials
7. **Comparison** - vs alternatives (if applicable)
8. **Contributing** - How to contribute
9. **License** - License information

### Tips
- Be specific in your answers - vague input = generic output
- If you don't have social proof yet, be honest - Claude can suggest alternatives
- Review and customize the output - it's a starting point
- Run `audit` on the generated README to verify quality

---

## `compete` - Competitor Analysis

### Purpose
Analyze competitor websites or repositories to identify positioning gaps and differentiation opportunities.

### Syntax
```
compete <url>
```

Or with slash command (if plugin registered): `/ai-marketer:compete <url>`

### Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| url | Yes | Competitor's website or GitHub repo URL |

### Examples

**Example 1: Competitor website**
```
compete https://competitor-product.com
```

**Example 2: Competitor GitHub**
```
compete https://github.com/competitor/their-tool
```

**Example 3: Multiple competitors**
```
compete https://competitor1.com
compete https://competitor2.com
compete https://competitor3.com
```

### Output Format

```
Competitor Analysis Report
==========================

Target: https://competitor-product.com
Product: CompetitorTool
Category: AI Development Tools

POSITIONING ANALYSIS
--------------------

Headline: "AI-powered coding assistant"
Tagline: "Write code faster"

NESB Score: 24/40
| Dimension | Score | Notes |
|-----------|-------|-------|
| NEW | 5/10 | Generic AI claim |
| EASY | 8/10 | Strong ease messaging |
| SAFE | 6/10 | User numbers present |
| BIG | 5/10 | Vague improvement claims |

Target Audience: Solution Aware developers
Primary Lever: Ease of use
Secondary Lever: Social proof

STRENGTHS
---------
✅ Clear quick-start flow
✅ Free tier available
✅ 50,000 users claimed
✅ Integration with popular IDEs

WEAKNESSES
----------
❌ Generic positioning ("AI-powered")
❌ No unique mechanism explained
❌ Weak differentiation from alternatives
❌ No tribe/community aspect
❌ Features-focused, not outcomes-focused

YOUR OPPORTUNITIES
------------------

1. Positioning Gap: No one owns "privacy-first"
   Counter-position: "The AI that never sees your code"

2. Messaging Gap: All competitors focus on speed
   Counter-position: Focus on accuracy/quality

3. Audience Gap: All target enterprise
   Counter-position: "Built for indie devs and small teams"

4. Mechanism Gap: No one explains HOW their AI works
   Counter-position: Transparent, explainable AI

5. Tribe Gap: No competitor builds community
   Counter-position: Build a movement around [shared value]

COUNTER-POSITIONING SUGGESTIONS
-------------------------------

Instead of: "AI-powered coding assistant"
Try: "The first AI that [your unique mechanism]"

Instead of: "Write code faster"
Try: "Stop [specific pain point] forever"

Differentiation angle:
"Unlike [Competitor] which [their approach],
we [your unique approach] because [reason]."
```

### Analysis Components

| Component | What It Analyzes |
|-----------|------------------|
| Positioning | Headline, tagline, value proposition |
| NESB Score | Their headline against the 4 quadrants |
| Awareness Target | Which awareness level they target |
| Persuasion Levers | Which of the 7 they use |
| Gaps | What they're NOT doing |

### Tips
- Analyze 2-3 direct competitors minimum
- Look for patterns in what they ALL do (opportunity to be different)
- Look for what NONE do (opportunity to own a space)
- Use the counter-positioning suggestions as starting points
- Your differentiation should be true and sustainable

---

## `voice` - Voice Extraction

### Purpose
Analyze existing content to extract voice patterns for consistent brand messaging across all generated content.

### Syntax
```
voice <url>
voice [paste existing content]
```

Or with slash command (if plugin registered): `/ai-marketer:voice <url>`

### Parameters
| Parameter | Required | Description |
|-----------|----------|-------------|
| url/content | Yes | Source of existing content to analyze |

### Examples

**Example 1: GitHub profile**
```
voice https://github.com/yourusername
```

**Example 2: Twitter profile**
```
voice https://twitter.com/yourhandle
```

**Example 3: Blog or website**
```
voice https://your-blog.com
```

**Example 4: Pasted samples**
```
voice

Here's some of my existing writing:

"I built this because I was tired of overengineered solutions.
Most tools treat you like an idiot. This one doesn't.
It does one thing well and gets out of your way."

"Look, we could spend weeks debating architecture.
Or we could ship something that works.
I prefer the second option."
```

### Output Format

```
Voice Profile
=============

VOICE IN 3 WORDS
----------------
Direct, Practical, No-Nonsense

TONE RATINGS
------------
| Dimension | Rating | Notes |
|-----------|--------|-------|
| Formality | 2/5 | Casual, conversational |
| Technical | 3/5 | Technical but accessible |
| Humor | 2/5 | Dry, understated |
| Directness | 5/5 | Very direct, no hedging |

SIGNATURE PATTERNS
------------------

Sentence Structure:
- Short, punchy sentences (avg 8 words)
- Minimal filler words
- Lists of 3 items frequently

Vocabulary:
- "Look," as opener
- "Actually" for emphasis
- Avoids: corporate jargon, superlatives, emojis

Rhetorical Patterns:
- "I built this because..." openings
- Problem-first framing
- "Most X do Y. This one doesn't." contrast

Personality Markers:
- Self-deprecating when appropriate
- Acknowledges trade-offs honestly
- Strong opinions, loosely held

PLATFORM ADAPTATIONS
--------------------

| Platform | Adaptations |
|----------|-------------|
| GitHub | More technical detail, same directness |
| Twitter | Shorter, same punchy style, occasional thread |
| LinkedIn | Slightly more formal, still direct |
| Blog | Longer-form, same personality |

GENERATION GUIDELINES
---------------------

When writing content for this voice:

1. Keep sentences under 12 words average
2. Lead with the problem or pain
3. Use "you" and "I" frequently
4. Avoid: "leverage", "synergy", "world-class", etc.
5. State opinions directly without hedging
6. Use contrast structures: "Most X. Not this."
7. Don't use emojis unless quoting someone
8. Acknowledge limitations honestly
9. Prefer concrete examples over abstract claims
10. End with clear action, not vague inspiration

SAMPLE OUTPUTS
--------------

Headline in this voice:
❌ "Leverage AI-powered solutions for enhanced productivity"
✅ "Stop debugging. Start shipping. One command."

Product description in this voice:
❌ "Our revolutionary platform enables seamless integration..."
✅ "It reads your code. It finds the bugs. You fix them in half the time."
```

### Sources Analyzed

| Source | What It Extracts |
|--------|------------------|
| GitHub READMEs | Technical communication style |
| GitHub Issues/PRs | Collaborative tone |
| Twitter/X | Casual voice, hot takes |
| LinkedIn | Professional voice |
| Blog posts | Long-form style |
| Pasted text | Whatever you provide |

### Tips
- Provide at least 500 words of sample content for accurate analysis
- Include samples from multiple contexts if possible
- Use this BEFORE generating any content
- Save your voice profile and reference it in generation requests
- Re-extract if your voice has evolved significantly

---

## Command Combinations

### Best Practice Workflow

```
1. voice https://github.com/yourusername
   (Establish your voice first)

2. compete https://competitor1.com
   compete https://competitor2.com
   (Understand the landscape)

3. readme
   (Generate README with context)

4. audit [the generated readme]
   (Verify quality)

5. score "your headline options"
   (Fine-tune headlines)
```

### Quick Improvement Flow

```
1. audit https://github.com/you/project
   (See current state)

2. score "current headline"
   (Diagnose headline)

3. [Make improvements based on feedback]

4. audit [updated content]
   (Verify improvement)
```

---

## Error Messages

| Error | Meaning | Solution |
|-------|---------|----------|
| "Could not access URL" | URL unreachable | Check URL is public |
| "No content found" | Page has no analyzable text | Try a different page |
| "Rate limited" | Too many requests | Wait a moment |
| "Invalid command" | Syntax error | Check command format |

---

## Getting Help

If you need help with commands:

1. Type `help` in Claude Code for general help
2. See this documentation for detailed reference
3. Check [Troubleshooting](../troubleshooting.md) for common issues
4. Report bugs on GitHub Issues

---

*Next: [Frameworks Explained](./frameworks-explained.md) for deep dives into each marketing framework.*
