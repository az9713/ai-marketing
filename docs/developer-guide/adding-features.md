# Adding New Features

This guide walks you through adding new features to the AI Marketer plugin. We'll cover adding skills, commands, agents, hooks, and content templates with real examples you can follow.

---

## Table of Contents

1. [Deciding What to Add](#deciding-what-to-add)
2. [Adding a New Skill](#adding-a-new-skill)
3. [Adding a New Command](#adding-a-new-command)
4. [Adding a New Agent](#adding-a-new-agent)
5. [Adding a Hook](#adding-a-hook)
6. [Adding a Content Template](#adding-a-content-template)
7. [Complete Example: Adding Email Marketing](#complete-example-adding-email-marketing)

---

## Deciding What to Add

Before writing code, decide which component type fits your feature:

### Decision Tree

```
What does your feature do?
│
├── Provides reference knowledge Claude should know?
│   └── → Add a SKILL
│
├── Needs a user-invokable action?
│   └── → Add a COMMAND
│
├── Requires long-running work with many steps?
│   └── → Add an AGENT
│
├── Should trigger automatically on an event?
│   └── → Add a HOOK
│
└── Provides a template for content generation?
    └── → Add a CONTENT TEMPLATE (supporting file)
```

### Quick Reference

| Feature Type | When to Use | Example |
|--------------|-------------|---------|
| Skill | Claude needs to reference knowledge | A new marketing framework |
| Command | User needs a quick action | `/email` to generate email copy |
| Agent | Complex, multi-step work | Deep competitive research |
| Hook | Automatic trigger needed | Auto-review on file save |
| Template | Structured content output | Email sequence template |

---

## Adding a New Skill

### Use Case
Add a skill when you want Claude to have access to reference material it can use when relevant.

### Step-by-Step

#### Step 1: Create the Skill Folder

```bash
# Navigate to skills directory
cd .claude/plugins/ai-marketer/skills

# Create your skill folder
mkdir my-new-skill
```

#### Step 2: Create SKILL.md

Create the file `my-new-skill/SKILL.md`:

```markdown
---
name: my-new-skill
description: Brief description of what this skill provides
allowed-tools: [Read, WebFetch]
invocation: automatic
---

# My New Skill

## Overview

Explain what this skill is for and when Claude should use it.

## Core Concepts

### Concept 1

Explain the first key concept.

**Key points:**
- Point 1
- Point 2
- Point 3

### Concept 2

Explain the second key concept.

## How to Apply

When using this skill, follow these steps:

1. First step
2. Second step
3. Third step

## Examples

### Example 1: Basic Usage

**Input**: "Example input"
**Output**: "Example output"

### Example 2: Advanced Usage

**Input**: "Complex example"
**Output**: "Complex output"

## Common Mistakes

1. **Mistake 1**: Explanation and how to avoid
2. **Mistake 2**: Explanation and how to avoid
```

#### Step 3: Add Supporting Files (Optional)

If your skill needs detailed reference material, create supporting files:

```markdown
# my-new-skill/detailed-reference.md

# Detailed Reference

[Extended content that Claude can load when needed]
```

Reference it from SKILL.md:
```markdown
For detailed information, see [detailed-reference.md](./detailed-reference.md).
```

#### Step 4: Test the Skill

1. Restart Claude Code
2. Ask Claude something that should trigger the skill
3. Verify Claude uses the skill appropriately

### Example: Adding a Pricing Framework Skill

Let's add a skill for pricing psychology:

**File**: `skills/pricing-optimizer/SKILL.md`

```markdown
---
name: pricing-optimizer
description: Apply pricing psychology to optimize how prices are presented
allowed-tools: [Read]
invocation: automatic
---

# Pricing Optimizer

## Overview

Apply proven pricing psychology techniques to optimize how prices are presented in marketing copy.

## Core Techniques

### Charm Pricing
Prices ending in 9 or 7 are perceived as better deals.
- $99 vs $100 → $99 feels significantly cheaper
- $97 → Implies a calculated, specific value

### Anchoring
Show a higher price first to make the actual price feel like a deal.
- "Normally $500, now $299"
- "Enterprise plan: $999/mo. Starter: $29/mo"

### Bundling vs Unbundling
- Bundle when you want to hide component costs
- Unbundle when individual items seem more valuable

### Decoy Pricing
Offer 3 options where the middle option is the target:
- Basic: $9/mo (limited)
- Pro: $29/mo ← Target (best value)
- Enterprise: $99/mo (overkill for most)

## Application

When reviewing pricing copy:

1. Check for charm pricing (ends in 9/7)
2. Look for anchoring opportunities
3. Evaluate pricing tier structure
4. Suggest decoy options if applicable

## Examples

### Before (Weak)
"Our tool costs $30 per month."

### After (Optimized)
"Join 5,000 teams who chose the Pro plan at $29/mo.
(Save $120/year vs monthly billing)"
```

---

## Adding a New Command

### Use Case
Add a command when you want users to be able to explicitly trigger an action with `/command`.

### Step-by-Step

#### Step 1: Create the Command File

```bash
cd .claude/plugins/ai-marketer/commands
```

Create file `mycommand.md`:

```markdown
---
name: mycommand
description: One-line description for /help listing
---

# My Command

## Purpose

Explain what this command does and when to use it.

## Usage

```
/mycommand <required-param> [optional-param]
```

## Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| required-param | Yes | What this is for |
| optional-param | No | Optional configuration |

## Examples

### Basic Usage
```
/mycommand "example input"
```

### With Options
```
/mycommand "example" --option value
```

## What Happens

When the user runs this command:

1. Step 1 of what Claude should do
2. Step 2
3. Step 3

## Output Format

The output should include:

1. First section
2. Second section
3. Recommendations

## Error Handling

If [condition], respond with [message].
```

#### Step 2: Test the Command

1. Restart Claude Code
2. Type `/mycommand test`
3. Verify it works as expected

### Example: Adding /email Command

**File**: `commands/email.md`

```markdown
---
name: email
description: Generate marketing email copy using persuasion frameworks
---

# Email Command

## Purpose

Generate compelling marketing email copy applying all 5 marketing frameworks.

## Usage

```
/email <type> [context]
```

## Email Types

| Type | Description |
|------|-------------|
| welcome | Welcome/onboarding email |
| launch | Product launch announcement |
| followup | Follow-up sequence |
| abandoned | Cart/trial abandonment |
| newsletter | Regular newsletter |

## Examples

```
/email welcome
/email launch "New feature: AI code review"
/email abandoned
```

## Process

When the user runs /email:

1. Ask for email type if not specified
2. Ask for product/feature context if not provided
3. Load the voice-extractor skill if voice profile exists
4. Apply all 5 marketing frameworks:
   - NESB for subject line and CTA
   - Persuasion levers throughout
   - Awareness-appropriate messaging
   - Tactical optimizations
   - Tribe-building elements
5. Generate the email with:
   - Subject line (scored)
   - Preview text
   - Body copy
   - CTA button text
   - P.S. line (if applicable)

## Output Format

```
## Email: [Type]

### Subject Line
[Subject] (NESB Score: X/40)

### Preview Text
[First line visible in inbox]

### Body

[Full email body with sections marked]

### CTA
[Button text]

### P.S.
[Optional closing hook]

---

### Analysis
- Persuasion levers used: [list]
- Awareness level targeted: [level]
- Key improvements applied: [list]
```
```

---

## Adding a New Agent

### Use Case
Add an agent when you need isolated, focused work that may be long-running or require many steps.

### Step-by-Step

#### Step 1: Create the Agent File

```bash
cd .claude/plugins/ai-marketer/agents
```

Create file `my-agent.md`:

```markdown
---
name: my-agent
description: What this agent specializes in
model: sonnet
allowed-tools: [Read, WebFetch, Grep, Glob]
---

# My Agent

## Role

You are a specialized agent for [specific purpose].

## Capabilities

You can:
- Capability 1
- Capability 2
- Capability 3

## Instructions

When delegated a task:

1. First, understand the specific request
2. Break it down into steps
3. Execute each step thoroughly
4. Compile findings into structured output
5. Return results to main context

## Output Format

Your output should be structured as:

### Summary
[Brief overview]

### Detailed Findings
[Organized sections]

### Recommendations
[Actionable items]

## Constraints

- Only do what's requested
- Stay focused on your specialty
- Return structured, actionable output
```

#### Step 2: Choose the Right Model

| Model | Best For | Considerations |
|-------|----------|----------------|
| `sonnet` | Complex reasoning, content generation | Slower, more expensive, higher quality |
| `haiku` | Simple checks, scoring, validation | Faster, cheaper, less nuanced |

#### Step 3: Define Allowed Tools

Only give the agent tools it needs:

| Tool | Purpose |
|------|---------|
| Read | Read files |
| Write | Create/modify files |
| WebFetch | Fetch web pages |
| Glob | Find files |
| Grep | Search file contents |
| Task | Delegate to other agents |

### Example: Adding an Email Sequence Agent

**File**: `agents/email-sequence-writer.md`

```markdown
---
name: email-sequence-writer
description: Creates complete email marketing sequences
model: sonnet
allowed-tools: [Read, WebFetch]
---

# Email Sequence Writer Agent

## Role

You are a specialized agent for creating complete email marketing sequences. You generate cohesive multi-email campaigns that guide recipients through a journey.

## Capabilities

- Generate welcome sequences (3-7 emails)
- Create launch sequences (pre-launch, launch, post-launch)
- Write nurture sequences
- Develop re-engagement campaigns

## Process

When creating a sequence:

1. Understand the goal (welcome, convert, re-engage)
2. Map the recipient journey
3. Plan email topics and timing
4. Write each email applying all frameworks
5. Ensure cohesive narrative across sequence
6. Add subject line variations for A/B testing

## Output Format

### Sequence: [Name]

**Goal**: [What this sequence achieves]
**Length**: [Number] emails over [timeframe]
**Trigger**: [What starts this sequence]

---

#### Email 1: [Name]
**Timing**: [When sent]
**Subject**: [Subject line] (NESB: X/40)
**Alt Subject**: [Alternative for A/B test]

[Body copy]

**CTA**: [Button text]

---

#### Email 2: [Name]
[Same format]

---

### Sequence Notes
- Key persuasion arc: [how levers build across emails]
- Fallback paths: [what happens if no engagement]
```

---

## Adding a Hook

### Use Case
Add a hook when you want something to happen automatically in response to an event.

### Step-by-Step

#### Step 1: Edit hooks.json

Open `.claude/plugins/ai-marketer/hooks/hooks.json`:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": {
          "tool": "Write",
          "path": "**/README.md"
        },
        "description": "Remind to audit README",
        "command": "echo '[AI-Marketer] README updated - run audit (or /ai-marketer:audit) for quality check'"
      }
    ],
    "UserPromptSubmit": [
      {
        "matcher": {
          "prompt": "(?i).*(readme|marketing).*"
        },
        "description": "Suggest commands on marketing keywords",
        "command": "echo '[AI-Marketer] Commands available: audit, score, readme (or /ai-marketer:*)'"
      }
    ]
  }
}
```

#### Step 2: Add Your Hook

Add a new object to the appropriate array:

```json
{
  "hooks": {
    "PostToolUse": [
      // ... existing hooks ...
      {
        "matcher": {
          "tool": "Write",
          "path": "**/*email*.md"
        },
        "description": "Remind to check email copy",
        "command": "echo '[AI-Marketer] Email content created - score subject lines with score (or /ai-marketer:score)'"
      }
    ]
  }
}
```

#### Step 3: Understand Matchers

**PostToolUse matchers**:
```json
{
  "tool": "Write",           // Tool name: Write, Read, etc.
  "path": "**/pattern.md"    // Glob pattern for file path
}
```

**UserPromptSubmit matchers**:
```json
{
  "prompt": "(?i)regex.*"    // Regex pattern for user input
                             // (?i) = case insensitive
}
```

### Hook Limitations

Hooks can only run shell commands. Keep them simple:
- Echo reminders/suggestions
- No complex logic
- No direct Claude interaction

---

## Adding a Content Template

### Use Case
Add a template when you want structured output for a specific content type.

### Step-by-Step

#### Step 1: Create the Template File

Templates go in the content-generator skill:

```bash
cd .claude/plugins/ai-marketer/skills/content-generator
```

Create file `email-sequence.md`:

```markdown
# Email Sequence Templates

## Welcome Sequence (5 Emails)

### Email 1: The Welcome
**Timing**: Immediately on signup
**Goal**: Confirm decision, set expectations

Subject: [NESB-optimized subject]

Body structure:
1. Acknowledge their decision (Encourage dreams)
2. What to expect next
3. One quick win they can do now
4. Soft CTA

### Email 2: The Quick Win
**Timing**: Day 2
**Goal**: Deliver immediate value

Subject: [Loss aversion angle]

Body structure:
1. The problem they're avoiding
2. Here's how to solve it (tutorial/tip)
3. Social proof
4. CTA to feature

[Continue with emails 3-5...]

---

## Launch Sequence (7 Emails)

### Pre-Launch Email 1: The Tease
**Timing**: 7 days before
**Goal**: Build anticipation

[Template structure...]
```

#### Step 2: Reference from Main Skill

Update `content-generator/SKILL.md`:

```markdown
## Available Templates

- [GitHub README](./github-readme.md)
- [Social Posts](./social-posts.md)
- [Email Sequences](./email-sequence.md)  ← New

When generating [content type], reference the appropriate template.
```

---

## Complete Example: Adding Email Marketing

Let's walk through adding complete email marketing support.

### What We'll Create

1. **Skill**: Email marketing framework knowledge
2. **Command**: `/email` for quick generation
3. **Agent**: For complex email sequences
4. **Template**: Email structures
5. **Hook**: Remind to score subject lines

### Step 1: Create the Skill

**File**: `skills/email-optimizer/SKILL.md`

```markdown
---
name: email-optimizer
description: Apply email marketing best practices and psychology
allowed-tools: [Read]
invocation: automatic
---

# Email Optimizer

## Overview

Apply proven email marketing psychology to create high-converting emails.

## Key Metrics to Optimize

### Open Rate (Subject Line)
- NESB applies directly
- 6-10 words optimal
- Personalization increases opens 26%
- Emoji: Test in your audience

### Click Rate (Body + CTA)
- Single focus per email
- CTA above the fold AND at bottom
- Urgency/scarcity where authentic
- Social proof before CTA

### Reply Rate (Conversational)
- Ask questions
- Write like a human
- Personal stories work
- End with specific question

## Subject Line Formulas

### Loss Aversion
- "Don't miss [opportunity]"
- "You're leaving [thing] behind"
- "Last chance: [offer]"

### Curiosity Gap
- "[Number] things about [topic] (the third will surprise you)"
- "I was wrong about [thing]"
- "Why [unexpected statement]"

### Direct Benefit
- "Get [benefit] in [timeframe]"
- "How to [achieve goal] without [pain]"
- "[Benefit] starts here"

## Email Body Structure

### The AIDA Framework
1. **Attention**: Hook in first line
2. **Interest**: Build relevance
3. **Desire**: Paint the outcome
4. **Action**: Clear single CTA

### The PAS Framework
1. **Problem**: Agitate the pain
2. **Agitation**: Make it worse
3. **Solution**: Your answer

## Common Mistakes

1. **Multiple CTAs**: One email, one action
2. **Too long**: 50-125 words ideal for most emails
3. **Weak subject**: Subject line IS the email for 50%+ who don't open
4. **No preview text**: First line shows in inbox - make it count
```

### Step 2: Create the Command

**File**: `commands/email.md`

```markdown
---
name: email
description: Generate marketing email copy with framework optimization
---

# Email Command

## Purpose

Generate compelling marketing email copy applying all 5 marketing frameworks.

## Usage

```
/email [type]
```

## Types

| Type | Description |
|------|-------------|
| welcome | Welcome/onboarding email |
| launch | Product launch announcement |
| promo | Promotional/sale email |
| newsletter | Regular update email |
| followup | Follow-up after action |

## Process

1. If type not specified, ask for email type
2. Ask for product/context if needed
3. Apply email-optimizer skill
4. Apply all 5 marketing frameworks
5. Generate email with scored subject line

## Output Format

```
## Email: [Type]

### Subject Line Options
1. "[Subject A]" (NESB: X/40)
2. "[Subject B]" (NESB: X/40)
3. "[Subject C]" (NESB: X/40)

### Preview Text
[First line visible in inbox]

### Email Body

[Complete email with sections marked]

### CTA
Button: [CTA Text]
Link destination: [Where it goes]

---

### Optimization Notes
- Primary lever: [which persuasion lever dominates]
- Awareness level: [which level this targets]
- Estimated reading time: [X seconds]
```
```

### Step 3: Create the Agent

**File**: `agents/email-sequence-writer.md`

```markdown
---
name: email-sequence-writer
description: Creates complete email marketing sequences
model: sonnet
allowed-tools: [Read]
---

# Email Sequence Writer

## Role

You are a specialist in creating cohesive email marketing sequences that guide subscribers through a journey.

## Capabilities

- Welcome sequences (onboarding new users)
- Launch sequences (building to a launch)
- Nurture sequences (warming leads)
- Re-engagement sequences (win-back campaigns)

## Instructions

When creating a sequence:

1. Understand the goal and audience
2. Map the emotional journey
3. Plan email timing and topics
4. Ensure each email builds on the last
5. Apply frameworks to every email
6. Include subject line alternatives for testing

## Output

For each email in the sequence:

```
### Email [N]: [Name]

**Timing**: [When sent relative to trigger]
**Goal**: [What this email achieves]
**Emotional State**: [How reader should feel]

**Subject Line**: [Main subject] (NESB: X/40)
**Alt Subjects**:
- [Alternative 1]
- [Alternative 2]

**Preview Text**: [First line visible]

**Body**:
[Full email text]

**CTA**: [Button text]

**Transition to Next**: [How this leads to email N+1]
```
```

### Step 4: Create the Template

**File**: `skills/content-generator/email-templates.md`

```markdown
# Email Templates

## Welcome Email Template

```
Subject: [Personal greeting + benefit]

Hey [Name],

You just did something [X]% of people never do: [action they took].

That tells me you're serious about [goal].

Here's what happens next:
1. [First thing]
2. [Second thing]
3. [Third thing]

But first, let me give you a quick win.

[One actionable tip they can use immediately]

Try it now. I'll check back tomorrow.

[Signature]

P.S. [Reinforce the win or add social proof]
```

## Launch Email Template

```
Subject: [Announcement with NEW + BIG elements]

[Name],

I've been working on something for [time period].

Today, it's ready.

Introducing [Product]: [one-sentence description].

Here's what makes it different:
- [Unique benefit 1]
- [Unique benefit 2]
- [Unique benefit 3]

[Number] people already [social proof action].

[CTA Button: Action + Urgency]

This [scarcity element: price/availability/bonus] ends [deadline].

[Signature]
```

## Follow-up Email Template

```
Subject: [Reference to previous email + new hook]

Hey [Name],

Yesterday I shared [thing].

But I forgot to mention [additional value].

[Expand on additional value]

If you're still [situation], here's what I'd do:

1. [Step 1]
2. [Step 2]
3. [Step 3]

[Softer CTA with different angle]

[Signature]
```
```

### Step 5: Add the Hook

**File**: `hooks/hooks.json` (add to existing)

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": {
          "tool": "Write",
          "path": "**/README.md"
        },
        "description": "Remind to audit README",
        "command": "echo '[AI-Marketer] README updated - run audit (or /ai-marketer:audit) for quality check'"
      },
      {
        "matcher": {
          "tool": "Write",
          "path": "**/*email*.md"
        },
        "description": "Remind to score email subject lines",
        "command": "echo '[AI-Marketer] Email content created. Run score (or /ai-marketer:score) on subject lines for optimization.'"
      }
    ]
  }
}
```

### Step 6: Update CLAUDE.md

Add to `.claude/plugins/ai-marketer/CLAUDE.md`:

```markdown
## Email Marketing

In addition to the 5 core frameworks, use the email-optimizer skill when generating email content. Key considerations:

- Subject lines must score 28+ on NESB
- Single CTA per email
- Apply loss aversion in subject lines
- Use the PAS or AIDA structure for body copy
```

### Step 7: Test Everything

1. Restart Claude Code
2. Test the command:
   ```
   /email welcome
   ```
3. Verify skill is used:
   ```
   Generate a product launch email for my AI code review tool
   ```
4. Test the hook by writing an email file
5. Verify the sequence agent works for complex requests

---

## Checklist for New Features

Before considering a feature complete:

- [ ] Created necessary files in correct locations
- [ ] Frontmatter is valid YAML
- [ ] Name matches filename (for commands)
- [ ] Description is clear and helpful
- [ ] Examples are included
- [ ] Updated CLAUDE.md if needed
- [ ] Tested basic functionality
- [ ] Tested edge cases
- [ ] Documentation updated

---

*Next: [Testing Guide](./testing.md)*
