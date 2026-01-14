---
name: score
description: Quick score of a headline or copy against NESB framework
---

# Quick Score Command

Get an instant NESB score for any headline or copy.

## Usage

```
/score "Your headline here"
/score Your headline without quotes also works
```

## What This Command Does

1. **Takes the input text**
2. **Scores against NESB**:
   - NEW (0-10): How novel/fresh?
   - EASY (0-10): How friction-free?
   - SAFE (0-10): How trustworthy?
   - BIG (0-10): How transformational?
3. **Provides overall score** (0-40)
4. **Suggests improvements** for weak dimensions
5. **Generates alternatives** that score higher

## Quick Output Format

```
## NESB Score: XX/40

| Dim | Score | Why |
|-----|-------|-----|
| NEW | X/10 | [reason] |
| EASY | X/10 | [reason] |
| SAFE | X/10 | [reason] |
| BIG | X/10 | [reason] |

### Stronger Alternatives
1. "[Improved version 1]" - XX/40
2. "[Improved version 2]" - XX/40
```

## Examples

```
/score AI-powered code completion
```
→ Score: 12/40 (weak - generic, no specifics)

```
/score The first AI that reads your entire codebase - ship 10x faster with zero setup
```
→ Score: 34/40 (strong - hits all 4 dimensions)

## Use Cases

- Testing headlines before publishing
- Comparing variations
- Quick copy improvement
- Learning the NESB framework
