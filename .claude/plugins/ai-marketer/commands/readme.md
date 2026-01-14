---
name: readme
description: Generate an optimized GitHub README applying all 5 marketing frameworks
---

# README Generator Command

Generate a marketing-optimized GitHub README for your project.

## Usage

```
/readme
/readme [project name or description]
```

## What This Command Does

1. **Gathers project context** (existing files, description)
2. **Extracts voice** from existing content if available
3. **Determines target audience** awareness level
4. **Generates README** applying all 5 frameworks
5. **Scores the output** for quality assurance
6. **Provides variations** for different angles

## Interactive Flow

1. If project context is unclear, ask about:
   - What does the project do?
   - Who is it for?
   - What's the key differentiator?
   - What social proof exists?

2. Generate draft README with:
   - Hero section (NESB-optimized headline)
   - Quick start (emphasize EASY)
   - Features with benefits (not just features)
   - Social proof section
   - Installation instructions
   - Comparison to alternatives (if applicable)

3. Score the output:
   - NESB analysis
   - Persuasion lever check
   - Tribe element review

4. Offer refinements based on feedback

## README Structure

```markdown
# [Product Name]

**[NESB-optimized tagline]**

[Badges for social proof + credibility]

[Quick start in 3 lines or less]

## Why [Product Name]?

[Problem agitation + unique mechanism]

## Features

[Benefits, not just features]

## Used By

[Social proof: logos, testimonials]

## Installation

[Simple, copy-paste commands]

## Documentation

[Links to learn more]
```

## Example

```
/readme
```

Will prompt for project details, then generate:
- Hero section with NESB-optimized headline
- Quick start emphasizing ease
- Feature list with benefit framing
- Social proof section
- Full framework scoring
