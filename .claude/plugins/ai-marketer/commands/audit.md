---
name: audit
description: Full marketing audit of a page or content against all 5 frameworks
---

# Marketing Audit Command

Run a comprehensive marketing audit on content or a URL.

## Usage

```
/ai-marketer:audit [url or paste content]
/ai-marketer:audit https://example.com
/ai-marketer:audit "Your headline or copy to audit"
```

Or use natural language (when CLAUDE.md is loaded):
```
audit https://example.com
```

## What This Command Does

1. **Fetches/reads the content** (URL or provided text)
2. **Analyzes awareness level** targeting
3. **Scores against NESB** (NEW, EASY, SAFE, BIG)
4. **Audits persuasion levers** (Cialdini's 7)
5. **Checks tactical techniques** (framing, social proof, etc.)
6. **Evaluates tribe elements** (Blair Warren's 5)
7. **Provides improvement recommendations**

## Process

When invoked, apply these skills in sequence:
1. Use **awareness-analyzer** to diagnose audience targeting
2. Use **nesb-scorer** to score headlines and copy
3. Use **persuasion-auditor** for full 7-lever audit
4. Use **copy-optimizer** to identify tactical opportunities
5. Use **tribe-builder** to check for movement elements

## Output

Provide a consolidated audit report with:
- Overall marketing effectiveness score
- Framework-by-framework breakdown
- Top 3 priority improvements
- Quick wins vs strategic changes
- Rewritten headline alternatives

## Example

```
/ai-marketer:audit https://github.com/user/repo
```

Will analyze the README and provide:
- Current NESB score
- Missing persuasion elements
- Awareness level assessment
- Specific improvement suggestions
