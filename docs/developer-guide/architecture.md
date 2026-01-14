# Architecture Overview

This document explains how the AI Marketer plugin is structured and why design decisions were made. Understanding this architecture will help you make informed contributions.

---

## Table of Contents

1. [High-Level Architecture](#high-level-architecture)
2. [Component Deep Dives](#component-deep-dives)
3. [Data Flow](#data-flow)
4. [Design Decisions](#design-decisions)
5. [Framework-to-Feature Mapping](#framework-to-feature-mapping)
6. [Extension Points](#extension-points)

---

## High-Level Architecture

### The Big Picture

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                              Claude Code                                     │
│                                                                             │
│  ┌─────────────────────────────────────────────────────────────────────┐   │
│  │                        AI Marketer Plugin                            │   │
│  │                                                                      │   │
│  │   ┌───────────────────────────────────────────────────────────┐     │   │
│  │   │                    KNOWLEDGE LAYER                         │     │   │
│  │   │                                                            │     │   │
│  │   │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐         │     │   │
│  │   │  │Awareness│ │Persuasion│ │  NESB   │ │  Tribe  │         │     │   │
│  │   │  │Analyzer │ │ Auditor │ │ Scorer  │ │ Builder │         │     │   │
│  │   │  └─────────┘ └─────────┘ └─────────┘ └─────────┘         │     │   │
│  │   │                                                            │     │   │
│  │   │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐         │     │   │
│  │   │  │  Copy   │ │  Voice  │ │Competitor│ │ Content │         │     │   │
│  │   │  │Optimizer│ │Extractor│ │ Analyzer│ │Generator│         │     │   │
│  │   │  └─────────┘ └─────────┘ └─────────┘ └─────────┘         │     │   │
│  │   │                                                            │     │   │
│  │   └───────────────────────────────────────────────────────────┘     │   │
│  │                              │                                       │   │
│  │                              ▼                                       │   │
│  │   ┌───────────────────────────────────────────────────────────┐     │   │
│  │   │                   EXECUTION LAYER                          │     │   │
│  │   │                                                            │     │   │
│  │   │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐    │     │   │
│  │   │  │   Market     │  │    Copy      │  │   Content    │    │     │   │
│  │   │  │  Researcher  │  │   Writer     │  │   Reviewer   │    │     │   │
│  │   │  │   (Agent)    │  │   (Agent)    │  │   (Agent)    │    │     │   │
│  │   │  └──────────────┘  └──────────────┘  └──────────────┘    │     │   │
│  │   │                                                            │     │   │
│  │   └───────────────────────────────────────────────────────────┘     │   │
│  │                              │                                       │   │
│  │                              ▼                                       │   │
│  │   ┌───────────────────────────────────────────────────────────┐     │   │
│  │   │                   INTERFACE LAYER                          │     │   │
│  │   │                                                            │     │   │
│  │   │  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐  │     │   │
│  │   │  │/audit  │ │/readme │ │/score  │ │/compete│ │/voice  │  │     │   │
│  │   │  └────────┘ └────────┘ └────────┘ └────────┘ └────────┘  │     │   │
│  │   │                                                            │     │   │
│  │   └───────────────────────────────────────────────────────────┘     │   │
│  │                              │                                       │   │
│  │                              ▼                                       │   │
│  │   ┌───────────────────────────────────────────────────────────┐     │   │
│  │   │                   AUTOMATION LAYER                         │     │   │
│  │   │                                                            │     │   │
│  │   │  ┌──────────────────────────────────────────────────────┐ │     │   │
│  │   │  │                      HOOKS                            │ │     │   │
│  │   │  │  PostToolUse: Auto-review after Write                │ │     │   │
│  │   │  │  UserPromptSubmit: Suggest commands on keywords      │ │     │   │
│  │   │  └──────────────────────────────────────────────────────┘ │     │   │
│  │   │                                                            │     │   │
│  │   └───────────────────────────────────────────────────────────┘     │   │
│  │                                                                      │   │
│  └─────────────────────────────────────────────────────────────────────┘   │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### The Four Layers

| Layer | Purpose | Components |
|-------|---------|------------|
| **Knowledge** | Reference material Claude consults | Skills (8 total) |
| **Execution** | Workers that perform complex tasks | Agents (3 total) |
| **Interface** | Entry points for users | Commands (5 total) |
| **Automation** | Background triggers | Hooks (2 triggers) |

---

## Component Deep Dives

### Skills: The Knowledge Layer

Skills are **reference documents** that Claude consults when needed. They contain:
- Framework definitions
- Scoring criteria
- Examples
- Instructions

#### Skill Structure

```
skills/
└── skill-name/
    ├── SKILL.md         # Main skill file (required)
    ├── reference.md     # Supporting material (optional)
    └── examples.md      # Examples (optional)
```

#### Skill Frontmatter

```yaml
---
name: nesb-scorer              # Identifier
description: Score headlines   # What it does
allowed-tools: [Read, WebFetch] # Tools it can use
invocation: automatic          # How it's triggered
---
```

**Invocation types**:
- `automatic`: Claude uses it when relevant
- `"keyword"`: User can explicitly invoke with `/keyword`

#### When Skills Load

Skills load on-demand, not all at once. This is called **progressive disclosure**:

1. Claude sees a request
2. Claude identifies relevant skill(s)
3. Only those skills are loaded
4. Supporting files load only when referenced

This keeps context efficient.

### Agents: The Execution Layer

Agents are **specialized workers** for complex tasks. They run in isolation with their own context.

#### When to Use Agents

| Use Case | Why Agent? |
|----------|------------|
| Deep research | May visit many pages |
| Content generation | Benefits from focused context |
| Quality review | Isolation prevents bias |

#### Agent Structure

```yaml
---
name: market-researcher        # Identifier
description: Research competitors # What it does
model: sonnet                  # Which model (sonnet/haiku)
allowed-tools: [Read, WebFetch, Task] # Available tools
---

# Market Researcher Agent

[Instructions for the agent]
```

#### Agent Models

| Model | Use For | Trade-offs |
|-------|---------|------------|
| `sonnet` | Complex reasoning, generation | Slower, more capable |
| `haiku` | Simple checks, scoring | Faster, cheaper |

The content-reviewer uses `haiku` because it just needs to check boxes.
The copy-writer uses `sonnet` because it needs to create quality content.

### Commands: The Interface Layer

Commands are **user-triggered actions**. They provide a consistent interface.

#### Command Structure

```yaml
---
name: score
description: Score a headline against NESB
---

# Score Command

## Usage
/score <headline>

## What This Does
[Instructions]
```

#### Command Naming

Commands are invoked with `/name`:
- `/score` → commands/score.md
- `/audit` → commands/audit.md

The `name` in frontmatter must match the filename (without .md).

### Hooks: The Automation Layer

Hooks **trigger automatically** on events. They run in the background.

#### Available Events

| Event | When It Fires |
|-------|--------------|
| `PostToolUse` | After any tool completes |
| `UserPromptSubmit` | When user sends a message |

#### Hook Configuration

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
        "command": "echo '[AI-Marketer] README written - consider /audit'"
      }
    ],
    "UserPromptSubmit": [
      {
        "matcher": {
          "prompt": "(?i).*(readme|marketing).*"
        },
        "description": "Suggest commands on keywords",
        "command": "echo '[AI-Marketer] Available: /audit, /score, /readme'"
      }
    ]
  }
}
```

#### Matcher Types

**Tool matchers** (for PostToolUse):
- `tool`: Which tool (e.g., "Write", "Read")
- `path`: File pattern (glob, e.g., "**/README.md")

**Prompt matchers** (for UserPromptSubmit):
- `prompt`: Regex pattern to match user input

---

## Data Flow

### Typical User Workflow

```
User types: /score "My AI tool helps developers"
            │
            ▼
┌───────────────────────────────────────────────────┐
│ COMMAND LAYER                                      │
│                                                    │
│  score.md recognizes the /score command           │
│  Extracts: headline = "My AI tool helps..."       │
│                                                    │
└────────────────────────┬──────────────────────────┘
                         │
                         ▼
┌───────────────────────────────────────────────────┐
│ KNOWLEDGE LAYER                                    │
│                                                    │
│  Claude loads nesb-scorer/SKILL.md                │
│  Gets: scoring criteria, examples, format         │
│                                                    │
└────────────────────────┬──────────────────────────┘
                         │
                         ▼
┌───────────────────────────────────────────────────┐
│ CLAUDE PROCESSING                                  │
│                                                    │
│  Applies NESB framework to headline               │
│  Calculates scores for each dimension             │
│  Generates suggestions                            │
│                                                    │
└────────────────────────┬──────────────────────────┘
                         │
                         ▼
┌───────────────────────────────────────────────────┐
│ OUTPUT                                             │
│                                                    │
│  NESB Score: 14/40 (Weak)                        │
│  NEW: 3/10 - Generic claim                       │
│  EASY: 4/10 - "helps" is vague                   │
│  ...                                              │
│                                                    │
└───────────────────────────────────────────────────┘
```

### Complex Workflow (Audit)

```
User types: /audit https://github.com/user/repo
            │
            ▼
┌───────────────────────────────────────────────────┐
│ COMMAND LAYER: audit.md                           │
│                                                    │
│  Recognizes /audit command                        │
│  URL to analyze: https://github.com/user/repo    │
│                                                    │
└────────────────────────┬──────────────────────────┘
                         │
            ┌────────────┴────────────┬──────────────────┐
            ▼                         ▼                   ▼
┌──────────────────┐     ┌──────────────────┐     ┌──────────────────┐
│ awareness-analyzer│     │ nesb-scorer      │     │ persuasion-auditor│
│                  │     │                  │     │                  │
│ Diagnose level   │     │ Score headline   │     │ Check 7 levers   │
└────────┬─────────┘     └────────┬─────────┘     └────────┬─────────┘
         │                        │                        │
         └────────────────────────┴────────────────────────┘
                                  │
                                  ▼
                    ┌──────────────────────────┐
                    │ copy-optimizer           │
                    │ tribe-builder            │
                    │                          │
                    │ Additional analysis      │
                    └────────────┬─────────────┘
                                 │
                                 ▼
                    ┌──────────────────────────┐
                    │ COMBINED REPORT          │
                    │                          │
                    │ Overall Score: 45/100   │
                    │ NESB: 22/40             │
                    │ Persuasion: 3/7         │
                    │ Recommendations...       │
                    └──────────────────────────┘
```

### Agent Delegation

```
User types: Analyze my top 3 competitors
            │
            ▼
┌───────────────────────────────────────────────────┐
│ CLAUDE MAIN CONTEXT                                │
│                                                    │
│  Recognizes this needs deep research              │
│  Delegates to market-researcher agent             │
│                                                    │
└────────────────────────┬──────────────────────────┘
                         │
                         ▼
┌───────────────────────────────────────────────────┐
│ AGENT: market-researcher                           │
│ (Separate context, own conversation)              │
│                                                    │
│  1. Visits competitor1.com                        │
│  2. Analyzes positioning                          │
│  3. Visits competitor2.com                        │
│  4. Analyzes positioning                          │
│  5. Visits competitor3.com                        │
│  6. Analyzes positioning                          │
│  7. Compiles comparative report                   │
│                                                    │
└────────────────────────┬──────────────────────────┘
                         │
                         ▼
┌───────────────────────────────────────────────────┐
│ RETURN TO MAIN CONTEXT                            │
│                                                    │
│  Agent returns structured findings                │
│  Claude presents to user                          │
│                                                    │
└───────────────────────────────────────────────────┘
```

---

## Design Decisions

### Why Skills Instead of Just Instructions?

**Alternative considered**: Put all instructions in a single large prompt.

**Why we chose skills**:

| Aspect | Single Prompt | Skills |
|--------|--------------|--------|
| Context usage | All loaded always | On-demand loading |
| Maintenance | One huge file | Modular files |
| Reusability | Copy-paste | Reference by name |
| Updates | Edit one file | Edit relevant skill |

Skills allow progressive disclosure and modular organization.

### Why Agents for Some Tasks?

**Alternative considered**: Do everything in the main context.

**Why we chose agents for specific tasks**:

| Aspect | Main Context | Agents |
|--------|--------------|--------|
| Long-running tasks | Clutters history | Isolated context |
| Parallel work | Sequential only | Can run in parallel |
| Focused work | Distractions possible | Single-purpose |
| Resource usage | Shares with user chat | Independent |

Agents are better for:
- Deep research (many web visits)
- Content generation (focused context)
- Background review (non-blocking)

### Why Commands Instead of Just Natural Language?

**Alternative considered**: Let users just describe what they want.

**Why we chose commands**:

| Aspect | Natural Language | Commands |
|--------|-----------------|----------|
| Discoverability | Hidden | `/help` lists all |
| Consistency | Varies | Predictable format |
| Speed | Parsing overhead | Direct trigger |
| Learning curve | Lower initially | Standard patterns |

Commands provide consistency while skills handle natural language nuance.

### Why Hooks Sparingly?

**Alternative considered**: Hook into everything.

**Why we use hooks sparingly**:

| Consideration | Aggressive Hooks | Sparse Hooks |
|---------------|-----------------|--------------|
| User control | Less | More |
| Surprise behavior | Frequent | Rare |
| Performance | Overhead on every action | Minimal overhead |
| Debugging | Hard | Easy |

We use hooks only for helpful reminders, not mandatory checks.

---

## Framework-to-Feature Mapping

Here's why each marketing framework is implemented as a specific feature:

### Framework 1: Breakthrough Advertising → Skill

**Why Skill?**
- Requires reference to 5 awareness levels
- Knowledge-intensive, not action-intensive
- Used in combination with other skills

### Framework 2: Influence (7 Levers) → Skill + Checklist

**Why Skill + Supporting File?**
- 7 levers need detailed definitions
- Checklist format natural for scoring
- Progressive disclosure (main skill → checklist when needed)

### Framework 3: 50 Tactics → Skill

**Why Skill?**
- Tactical techniques to reference
- Applied during optimization
- Not standalone actions

### Framework 4: NESB → Skill + Command

**Why Both?**
- Skill: Detailed framework for Claude to reference
- Command: Quick `/score` for users

The command provides fast access; the skill provides depth.

### Framework 5: Tribe Building → Skill

**Why Skill?**
- 5 elements to apply
- Used during content generation
- Knowledge-based, not action-based

### Voice Extraction → Skill + Agent Option

**Why This Combination?**
- Skill: Defines HOW to extract voice
- Agent (optional): For deep research across many content pieces

### Competitor Analysis → Agent + Skill

**Why This Combination?**
- Agent: Visits multiple pages (long-running)
- Skill: Provides analysis framework

### Content Generation → Skill + Agent

**Why This Combination?**
- Skill: Templates and guidelines
- Agent: Focused generation context

---

## Extension Points

### Adding a New Framework

If you want to add a new marketing framework:

1. **Create a skill folder**: `skills/my-framework/`
2. **Create SKILL.md** with the framework definition
3. **Add supporting files** if needed
4. **Update CLAUDE.md** to reference it
5. **(Optional) Create a command** if users need direct access

### Adding a New Content Type

To add a new content type (e.g., YouTube descriptions):

1. **Add template** in `skills/content-generator/youtube-description.md`
2. **Update content-generator SKILL.md** to reference it
3. **(Optional) Add a command** like `/youtube`

### Adding a New Hook

To add a new automatic trigger:

1. **Edit hooks/hooks.json**
2. **Add matcher** for the event you want to catch
3. **Add command** that runs when triggered

### Adding a New Agent

To add a specialized agent:

1. **Create file** in `agents/my-agent.md`
2. **Define frontmatter** with name, description, model, allowed-tools
3. **Write instructions** for what the agent should do

---

## Technical Constraints

### Context Limits

Claude has a context window limit. The architecture handles this through:
- Progressive disclosure (skills load on-demand)
- Agent isolation (separate contexts)
- Focused commands (minimal overhead)

### Tool Access

Not all tools are available to all components:

| Component | Available Tools |
|-----------|----------------|
| Skills | Depends on `allowed-tools` |
| Agents | Depends on agent's `allowed-tools` |
| Main context | All tools |
| Hooks | Echo only (shell commands) |

### File Size Considerations

Keep individual files focused:
- Skills: Under 1000 lines ideal
- Supporting files: Break up if too long
- Agents: Focused instructions

---

## Summary

The AI Marketer architecture:

1. **Skills** provide knowledge (what to know)
2. **Agents** handle execution (what to do)
3. **Commands** provide interface (how to access)
4. **Hooks** enable automation (when to act)

This separation of concerns allows:
- Easy maintenance
- Clear extension points
- Efficient resource usage
- Consistent user experience

---

*Next: [Adding New Features](./adding-features.md)*
