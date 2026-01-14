# AI Marketing Frameworks Plugin for Claude Code

---

# Part 1: Technical Design Documentation

## Claude Code Features Overview

Claude Code provides several extensibility mechanisms. Here's what each does and when to use it:

| Feature | Purpose | Invocation | Best For |
|---------|---------|------------|----------|
| **Skills** | Reusable knowledge/instructions that Claude can invoke | Automatic (model-triggered) or `/skill-name` | Domain expertise, workflows, reference docs |
| **Subagents** | Specialized agents for delegated tasks | Automatic delegation or explicit | Long-running tasks, parallel work, isolation |
| **Slash Commands** | User-triggered actions | `/command` in chat | Quick actions, user-initiated workflows |
| **Hooks** | Event-driven automation | Automatic on events | Pre/post processing, validation, notifications |
| **MCP Servers** | External tool integrations | Via MCP protocol | APIs, databases, external services |
| **Plugins** | Bundled packages of all above | Installation | Distribution, team sharing |

---

## Framework-to-Feature Mapping

### Framework 1: Breakthrough Advertising (Schwartz)
**Core Concept**: Problem Awareness Spectrum + Market Sophistication

| Concept | Claude Code Feature | Justification |
|---------|---------------------|---------------|
| Awareness diagnosis | **Skill** | Requires deep knowledge of the 5 awareness levels; skill provides reference material Claude can consult |
| Sophistication staging | **Skill** (same) | Part of the same analytical framework |
| Audience research | **Subagent** | May require browsing multiple pages, long-running research |
| Quick awareness check | **Slash Command** | User convenience for rapid diagnosis |

**Technical Decision**:
- **Skill** is primary because awareness analysis is *knowledge-intensive* - Claude needs the framework definitions available as reference
- **Subagent** for deep research because market research can require visiting multiple competitor sites, which benefits from background execution
- **Not a Hook** because this is user-initiated analysis, not automatic processing

---

### Framework 2: Influence (Cialdini)
**Core Concept**: 7 Persuasion Levers

| Concept | Claude Code Feature | Justification |
|---------|---------------------|---------------|
| 7-lever audit | **Skill** | Checklist-based analysis needs reference to all 7 levers |
| Scoring rubric | **Skill (supporting file)** | Progressive disclosure - main skill loads rubric when needed |
| UX/landing page audit | **Slash Command** | User wants quick `/audit` interface |
| Auto-audit on write | **Hook (PostToolUse)** | Can auto-trigger review after generating content |

**Technical Decision**:
- **Skill with supporting files** because the 7 levers need detailed definitions and examples
- **Hook** added for optional auto-review - when content is generated, automatically score it against the 7 levers
- **Not MCP** because this is analysis logic, not external service integration

---

### Framework 3: Yes! 50 Ways to Be Persuasive
**Core Concept**: Tactical Implementation (Framing, Social Proof, Loss Aversion)

| Concept | Claude Code Feature | Justification |
|---------|---------------------|---------------|
| Tactic reference | **Skill (supporting file)** | 50 tactics need reference documentation |
| Copy rewriting | **Skill** | Apply tactics to transform copy |
| Before/after examples | **Skill (supporting file)** | Progressive disclosure of examples |

**Technical Decision**:
- **Skill with multiple supporting files** because 50 tactics is too much for a single SKILL.md
- **Not a Subagent** because copy optimization is typically quick, synchronous work
- Tactics file loaded only when specific tactic is relevant (progressive disclosure)

---

### Framework 4: Take Their Money (Milligan)
**Core Concept**: NEW, EASY, SAFE, BIG quadrant

| Concept | Claude Code Feature | Justification |
|---------|---------------------|---------------|
| NESB scoring | **Skill** | Simple 4-dimension framework fits in one skill |
| Headline generator | **Skill (same)** | Generation follows from scoring |
| Quick scoring | **Slash Command** | `/nesb "your headline"` for instant feedback |

**Technical Decision**:
- **Single Skill** because the framework is concise (4 dimensions)
- **Slash Command** for user convenience - most common use case is scoring a headline
- **Not a Hook** because you want to consciously score, not auto-score everything

---

### Framework 5: One Sentence Persuasion Course (Blair Warren)
**Core Concept**: Encourage dreams, Justify failures, Allay fears, Confirm suspicions, Throw rocks

| Concept | Claude Code Feature | Justification |
|---------|---------------------|---------------|
| Tribe copy generation | **Skill** | Needs the 5-element framework as reference |
| Enemy identification | **Skill (within tribe-builder)** | Part of "throw rocks" element |
| Community voice | **Subagent** | May need to analyze community discussions to find shared enemies |

**Technical Decision**:
- **Skill** for the core framework
- **Subagent** option for deep community research (browsing forums, analyzing discussions)
- **Not MCP** because this is analytical/generative, not external service

---

### Cross-Cutting Capabilities

| Capability | Claude Code Feature | Justification |
|------------|---------------------|---------------|
| **Voice Extraction** | **Skill + Subagent** | Skill defines how to extract; Subagent does the browsing |
| **Competitor Analysis** | **Subagent + MCP** | Long-running, browser-based; uses Chrome MCP for web access |
| **Content Generation** | **Skill** | Knowledge-intensive, needs templates and framework synthesis |
| **Content Review** | **Subagent** | Can review in background while user continues |
| **Slash Commands** | **Commands** | User-facing shortcuts to common workflows |
| **Auto-review** | **Hook** | PostToolUse hook to review generated content |

---

## Why This Combination?

### Skills (Primary Choice)
Skills are the backbone because marketing frameworks are **knowledge-intensive**:
- They require reference material (the framework definitions, examples, checklists)
- They benefit from progressive disclosure (supporting files loaded when needed)
- They can be invoked automatically by Claude when relevant
- They can be combined (generate content -> auto-score against all frameworks)

### Subagents (For Long-Running Tasks)
Subagents are used for:
- **Market research** - may need to visit 5-10 competitor sites
- **Voice extraction** - analyzing multiple existing content pieces
- **Content review** - can run in background after generation

Why subagents over regular skills?
- Isolation: Subagents have their own context, preventing main conversation pollution
- Parallelism: Can run multiple analyses simultaneously
- Background execution: User can continue while research happens

### Slash Commands (User Convenience)
Commands provide quick access:
- `/audit` - one-command full marketing audit
- `/nesb` - quick headline scoring
- `/readme` - generate optimized README

Why commands over just skills?
- Explicit user intent (skills auto-trigger, commands are deliberate)
- Parameter passing (`/audit https://competitor.com`)
- Discoverability (users can `/help` to see available commands)

### Hooks (Automation)
Hooks handle automatic processing:
- **PostToolUse on Write** - auto-review generated marketing content
- **Stop hook** - ensure generated content meets minimum quality score

Why hooks?
- Ensures consistency (every generated piece gets reviewed)
- Reduces manual steps (no need to explicitly request review)
- Can block low-quality output before it's presented

### MCP (External Integration)
MCP is used for:
- **Chrome integration** - browser automation for competitor analysis
- Potential future: social media APIs, analytics platforms

Why MCP over Bash scripts?
- Standardized protocol for tool integration
- Better security model (permission-based)
- Reusable across sessions

### Plugins (Packaging)
Everything is wrapped in a single plugin because:
- **Distribution**: Easy to share/install (`claude plugin install ai-marketer`)
- **Cohesion**: All marketing tools in one logical package
- **Configuration**: Single place for plugin settings
- **Updates**: Version and update the entire toolkit together

---

## What's NOT Used (and Why)

| Feature | Why Not Primary |
|---------|-----------------|
| **Only Slash Commands** | Would miss auto-triggering; user has to remember every command |
| **Only Hooks** | Frameworks need to be invoked on-demand, not just reactively |
| **Only Subagents** | Overkill for quick scoring/analysis; adds latency |
| **Only MCP** | Most logic is analysis/generation, not external services |

---

## Feature Interaction Flow

```
User Request: "Optimize my GitHub README"
         |
         v
+-------------------------------------------------------------+
|  /readme Slash Command                                       |
|  (User-triggered entry point)                                |
+-------------------------------------------------------------+
         |
         v
+-------------------------------------------------------------+
|  Voice Extractor Skill                                       |
|  (Auto-triggered to match user's existing style)             |
|  +-- Subagent: Browse user's existing repos if needed        |
+-------------------------------------------------------------+
         |
         v
+-------------------------------------------------------------+
|  Awareness Analyzer Skill                                    |
|  (Determine target audience awareness level)                 |
+-------------------------------------------------------------+
         |
         v
+-------------------------------------------------------------+
|  Content Generator Skill                                     |
|  (Generate README applying all 5 frameworks)                 |
|  +-- Uses: NESB, Tribe Builder, Persuasion frameworks        |
+-------------------------------------------------------------+
         |
         v
+-------------------------------------------------------------+
|  PostToolUse Hook                                            |
|  (Auto-triggered after Write)                                |
|  +-- Content Reviewer Subagent scores the output             |
+-------------------------------------------------------------+
         |
         v
+-------------------------------------------------------------+
|  Interactive Approval                                        |
|  (User reviews score, requests refinements if needed)        |
+-------------------------------------------------------------+
```

---

# Part 2: Implementation Plan

Build a single Claude Code plugin called `ai-marketer` that implements the 5 marketing frameworks from the video into actionable skills, subagents, and commands for promoting AI products (starting with GitHub repos).

### Frameworks to Implement

| # | Book | Core Concept | Tool Purpose |
|---|------|--------------|--------------|
| 1 | Breakthrough Advertising | Problem Awareness & Market Sophistication | Audience diagnosis |
| 2 | Influence | 7 Persuasion Levers | UX/copy audit |
| 3 | Yes! 50 Ways | Tactical Persuasion | Copy optimization |
| 4 | Take Their Money | NEW, EASY, SAFE, BIG | Headline/CTA scoring |
| 5 | One Sentence Persuasion | Encourage, Justify, Allay, Confirm, Throw Rocks | Tribe-building copy |

---

## Plugin Architecture

```
.claude/plugins/ai-marketer/
├── plugin.json                    # Plugin manifest
├── CLAUDE.md                      # Plugin-level context
│
├── skills/
│   ├── awareness-analyzer/        # Framework 1: Diagnose audience awareness
│   │   ├── SKILL.md
│   │   └── awareness-levels.md
│   │
│   ├── persuasion-auditor/        # Framework 2: 7 levers audit
│   │   ├── SKILL.md
│   │   └── cialdini-checklist.md
│   │
│   ├── copy-optimizer/            # Framework 3: Tactical improvements
│   │   ├── SKILL.md
│   │   └── tactics-reference.md
│   │
│   ├── nesb-scorer/               # Framework 4: NEW-EASY-SAFE-BIG
│   │   ├── SKILL.md
│   │   └── nesb-examples.md
│   │
│   ├── tribe-builder/             # Framework 5: Cult-like following
│   │   ├── SKILL.md
│   │   └── tribe-patterns.md
│   │
│   ├── voice-extractor/           # Analyze existing content for voice
│   │   └── SKILL.md
│   │
│   ├── competitor-analyzer/       # Browser-based competitive analysis
│   │   └── SKILL.md
│   │
│   └── content-generator/         # Generate marketing content
│       ├── SKILL.md
│       ├── github-readme.md
│       ├── landing-page.md
│       ├── social-posts.md
│       └── blog-article.md
│
├── agents/
│   ├── market-researcher.md       # Deep competitive/market research
│   ├── copy-writer.md             # Generate optimized marketing copy
│   └── content-reviewer.md        # Review & score generated content
│
├── commands/
│   ├── audit.md                   # /audit - Full marketing audit
│   ├── generate.md                # /generate - Create marketing content
│   ├── score.md                   # /score - Score copy against frameworks
│   └── compete.md                 # /compete - Analyze competitors
│
└── hooks/
    └── hooks.json                 # Post-generation review hooks
```

---

## Core Skills Design

### 1. Awareness Analyzer (`/awareness`)

**Purpose**: Diagnose where target audience sits on the awareness spectrum

**Input**: Product description + target audience
**Output**:
- Awareness level diagnosis (Unaware -> Most Aware)
- Market sophistication stage (1-5)
- Recommended messaging approach
- Example headlines for each awareness level

**Implementation**:
```markdown
# SKILL.md frontmatter
---
name: awareness-analyzer
description: Diagnose audience awareness level using Schwartz's framework
allowed-tools: [Read, WebFetch, Task]
---
```

### 2. Persuasion Auditor (`/persuade`)

**Purpose**: Audit content against Cialdini's 7 persuasion levers

**Input**: Marketing copy (landing page, README, etc.)
**Output**:
- Score for each lever (0-10): Authority, Social Proof, Commitment, Liking, Reciprocity, Scarcity, Unity
- Missing opportunities identified
- Specific improvement suggestions

### 3. Copy Optimizer (`/optimize`)

**Purpose**: Apply tactical persuasion techniques

**Tactics to check**:
- Framing (negative -> positive reframe)
- Specific social proof (generic -> targeted)
- Loss aversion (gain -> avoid loss)
- Similarity shortcuts
- Commitment laddering

### 4. NESB Scorer (`/nesb`)

**Purpose**: Score headlines/copy against NEW-EASY-SAFE-BIG

**Output**:
- Individual scores (0-10) for each dimension
- Overall effectiveness score
- Rewritten alternatives hitting all 4 quadrants

### 5. Tribe Builder (`/tribe`)

**Purpose**: Generate copy that builds cult-like following

**The 5 elements**:
1. Encourage their dreams
2. Justify their failures
3. Allay their fears
4. Confirm their suspicions
5. Help throw rocks at enemies

**Output**: Copy variants hitting each element + combined version

### 6. Voice Extractor (`/voice`)

**Purpose**: Analyze existing content to extract voice patterns

**Input**: URLs to existing repos, blog posts, social profiles
**Output**:
- Voice characteristics (tone, vocabulary, sentence structure)
- Recurring patterns and phrases
- Brand personality traits
- Voice guidelines document for consistent generation

### 7. Competitor Analyzer (`/compete`)

**Purpose**: Use browser automation to analyze competitor positioning

**Uses**: Claude in Chrome + Chrome MCP (fallback)
**Output**:
- Competitor awareness level targeting
- Persuasion levers used
- NESB scoring of their copy
- Differentiation opportunities

### 8. Content Generator (`/market`)

**Purpose**: Generate marketing content applying all frameworks

**Content types**:
- GitHub README (developer-focused)
- Landing page copy (conversion-focused)
- X/Twitter thread (viral-focused)
- LinkedIn post (professional)
- YouTube script intro (hook-focused)
- Substack/blog article (thought leadership)
- Product Hunt launch (launch-optimized)

---

## Subagents Design

### Market Researcher Agent

**Trigger**: Complex competitive analysis requiring multiple sites
**Tools**: WebFetch, Chrome MCP, Read, Grep
**Behavior**:
- Visits competitor sites
- Extracts positioning data
- Compiles comparative analysis
- Returns structured report

### Copywriter Agent

**Trigger**: Content generation requests
**Tools**: Read, Write, Task (for research)
**Behavior**:
- Loads voice profile (if exists)
- Applies all 5 frameworks
- Generates drafts for approval
- Iterates based on feedback

### Content Reviewer Agent

**Trigger**: After content generation
**Tools**: Read
**Behavior**:
- Scores generated content against all frameworks
- Identifies weak spots
- Suggests specific improvements
- Provides final approval recommendation

---

## Slash Commands

| Command | Description | Skill(s) Used |
|---------|-------------|---------------|
| `/audit <url>` | Full marketing audit of a page | All analyzers |
| `/readme` | Generate optimized GitHub README | Content generator |
| `/landing` | Generate landing page copy | Content generator |
| `/tweet` | Generate X/Twitter thread | Content generator |
| `/linkedin` | Generate LinkedIn post | Content generator |
| `/score <text>` | Score copy against all frameworks | All scorers |
| `/compete <url>` | Analyze competitor | Competitor analyzer |
| `/voice <urls>` | Extract voice from content | Voice extractor |

---

## Hooks

### PostToolUse Hook: Auto-Review

After any Write operation in marketing content files, automatically trigger the Content Reviewer agent to score the output.

```json
{
  "hooks": {
    "PostToolUse": [{
      "matcher": "Write",
      "command": "echo 'Content written - review recommended'"
    }]
  }
}
```

---

## Implementation Plan

### Phase 1: Foundation (Core Plugin Structure)
1. Create plugin directory structure
2. Write `plugin.json` manifest
3. Create `CLAUDE.md` with framework reference
4. Set up basic skill templates

### Phase 2: Analysis Skills
5. Implement Awareness Analyzer skill
6. Implement Persuasion Auditor skill
7. Implement NESB Scorer skill
8. Implement Copy Optimizer skill
9. Implement Tribe Builder skill

### Phase 3: Research & Voice
10. Implement Voice Extractor skill
11. Implement Competitor Analyzer skill (with browser integration)
12. Create Market Researcher subagent

### Phase 4: Content Generation
13. Implement Content Generator skill (GitHub README template)
14. Add landing page template
15. Add social media templates (X, LinkedIn)
16. Add blog/article templates
17. Create Copywriter subagent

### Phase 5: Commands & Integration
18. Create slash commands
19. Implement Content Reviewer subagent
20. Add PostToolUse hooks
21. Test end-to-end workflow

### Phase 6: Testing & Refinement
22. Test on user's GitHub repos
23. Self-promote the plugin (meta-test)
24. Refine based on results

---

## File Inventory (To Create)

| File | Purpose |
|------|---------|
| `.claude/plugins/ai-marketer/plugin.json` | Plugin manifest |
| `.claude/plugins/ai-marketer/CLAUDE.md` | Plugin context |
| `.claude/plugins/ai-marketer/skills/awareness-analyzer/SKILL.md` | Framework 1 |
| `.claude/plugins/ai-marketer/skills/persuasion-auditor/SKILL.md` | Framework 2 |
| `.claude/plugins/ai-marketer/skills/copy-optimizer/SKILL.md` | Framework 3 |
| `.claude/plugins/ai-marketer/skills/nesb-scorer/SKILL.md` | Framework 4 |
| `.claude/plugins/ai-marketer/skills/tribe-builder/SKILL.md` | Framework 5 |
| `.claude/plugins/ai-marketer/skills/voice-extractor/SKILL.md` | Voice analysis |
| `.claude/plugins/ai-marketer/skills/competitor-analyzer/SKILL.md` | Competition |
| `.claude/plugins/ai-marketer/skills/content-generator/SKILL.md` | Generation |
| `.claude/plugins/ai-marketer/agents/market-researcher.md` | Research agent |
| `.claude/plugins/ai-marketer/agents/copy-writer.md` | Writing agent |
| `.claude/plugins/ai-marketer/agents/content-reviewer.md` | Review agent |
| `.claude/plugins/ai-marketer/commands/*.md` | Slash commands |

---

## Verification Plan

1. **Unit test each skill**: Run each skill independently with sample input
2. **Integration test**: Run `/audit` on a real GitHub repo README
3. **Generation test**: Use `/readme` to generate new README for this plugin
4. **Meta-test**: Use all tools to create marketing for this plugin itself
5. **Browser test**: Run `/compete` on a competitor product page

---

## Success Criteria

- [ ] All 5 frameworks implemented as functional skills
- [ ] Voice extraction works on existing GitHub repos
- [ ] Content generation produces platform-appropriate output
- [ ] Browser integration works for competitive analysis
- [ ] Interactive approval workflow functions correctly
- [ ] Plugin can market itself (meta-validation)
