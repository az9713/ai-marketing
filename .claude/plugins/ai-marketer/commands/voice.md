---
name: voice
description: Extract voice patterns from existing content for consistent brand messaging
---

# Voice Extraction Command

Analyze existing content to extract voice patterns for consistent content generation.

## Usage

```
/voice https://github.com/username
/voice [paste existing content]
/voice https://twitter.com/username
```

## What This Command Does

1. **Gathers existing content** from provided sources
2. **Analyzes voice dimensions**:
   - Tone (formal ↔ casual)
   - Vocabulary (technical depth)
   - Sentence structure
   - Personality traits
   - Recurring patterns
3. **Creates voice profile** for future content generation
4. **Provides platform adaptations** (how voice changes per platform)

## Voice Dimensions Analyzed

### Tone Spectrum
- Formality: 1 (very casual) to 5 (very formal)
- Technical depth: 1 (simplified) to 5 (expert-level)
- Humor level: 1 (serious) to 5 (playful)
- Directness: 1 (gentle) to 5 (blunt)

### Vocabulary Patterns
- Signature phrases used frequently
- Technical terms and how they're explained
- Words/phrases avoided

### Sentence Structure
- Typical length (short/medium/long)
- Simple vs complex structures
- Use of questions
- Paragraph style

### Personality Elements
- First person usage (I/We)
- Emoji usage
- Humor style
- Cultural references

## Output Format

```markdown
## Voice Profile

### Voice in 3 Words
[Word 1], [Word 2], [Word 3]

### Tone Ratings
- Formality: X/5
- Technical: X/5
- Humor: X/5
- Directness: X/5

### Signature Patterns
- "[Phrase they use often]"
- "[Another pattern]"

### Platform Adaptations
| Platform | Adjustments |
|----------|-------------|
| GitHub | [How voice adapts] |
| Twitter | [How voice adapts] |
| LinkedIn | [How voice adapts] |

### Generation Guidelines
When writing for this voice:
1. [Specific instruction]
2. [Specific instruction]
3. [Specific instruction]
```

## Sources Supported

- GitHub repositories and READMEs
- Twitter/X profiles
- LinkedIn profiles
- Blog posts
- Pasted text samples

## Example

```
/voice https://github.com/simonwillison
```

Will analyze repositories to extract:
- Technical communication style
- Documentation patterns
- Personality and humor
- Voice guidelines for matching
