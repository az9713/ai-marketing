---
name: compete
description: Analyze a competitor's website and positioning
---

# Competitor Analysis Command

Analyze a competitor's website to understand their positioning and find opportunities.

## Usage

```
/compete https://competitor.com
/compete [competitor name]
```

## What This Command Does

1. **Navigates to competitor site** (using browser automation)
2. **Extracts positioning elements**:
   - Hero headline and value proposition
   - Target audience signals
   - Unique mechanism claims
   - Social proof shown
   - Pricing if visible
3. **Scores against frameworks**:
   - NESB analysis of their copy
   - Persuasion levers used
   - Awareness level they're targeting
4. **Identifies opportunities**:
   - Gaps in their positioning
   - Underserved angles
   - Differentiation opportunities

## Browser Automation

This command uses Claude in Chrome when available:
1. Creates a new tab for research
2. Navigates to competitor URL
3. Extracts page content
4. Falls back to WebFetch if browser unavailable

## Output Format

```markdown
## Competitor Analysis: [Name]

### Their Positioning
**Headline**: "[Their main headline]"
**Target**: [Who they're targeting]
**Mechanism**: [Their unique claim]

### Framework Scores
- NESB: XX/40
- Persuasion Levers: XX/70
- Awareness Target: [Level]

### Strengths
1. [What they do well]
2. [Another strength]

### Weaknesses
1. [Gap you can exploit]
2. [Missing element]

### Differentiation Opportunities
1. [How to position against them]
2. [Underserved angle]
```

## Multiple Competitors

For comparing multiple competitors:
```
/compete https://competitor1.com https://competitor2.com
```

Will provide:
- Side-by-side comparison
- Common patterns in the market
- White space no one occupies
- Recommended unique positioning

## Example

```
/compete https://linear.app
```

Will analyze Linear's positioning and provide:
- Their NESB scores
- Persuasion tactics used
- Opportunities to differentiate
- Recommended counter-positioning
