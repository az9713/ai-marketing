# Developer Getting Started

Welcome! This guide will help you set up your development environment for working on the AI Marketer plugin. No prior experience with Claude Code plugins is required.

---

## Table of Contents

1. [What You'll Be Working With](#what-youll-be-working-with)
2. [Prerequisites](#prerequisites)
3. [Setting Up Your Environment](#setting-up-your-environment)
4. [Understanding the Project Structure](#understanding-the-project-structure)
5. [Your First Change](#your-first-change)
6. [Running and Testing](#running-and-testing)
7. [Common Development Tasks](#common-development-tasks)
8. [Next Steps](#next-steps)

---

## What You'll Be Working With

### The Big Picture

AI Marketer is a **Claude Code plugin**. Claude Code is Anthropic's CLI tool that lets you interact with Claude in your terminal. Plugins extend Claude Code with additional capabilities.

```
┌─────────────────────────────────────────────────────────────────┐
│                         Claude Code                              │
│                                                                  │
│   ┌──────────────────────────────────────────────────────────┐  │
│   │                    AI Marketer Plugin                     │  │
│   │                                                          │  │
│   │   ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐   │  │
│   │   │ Skills  │  │ Agents  │  │Commands │  │  Hooks  │   │  │
│   │   │ (8)     │  │ (3)     │  │ (5)     │  │ (2)     │   │  │
│   │   └─────────┘  └─────────┘  └─────────┘  └─────────┘   │  │
│   │                                                          │  │
│   └──────────────────────────────────────────────────────────┘  │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

### What Each Component Does

| Component | Purpose | Files |
|-----------|---------|-------|
| **Skills** | Reusable knowledge that Claude can reference | Markdown files with frontmatter |
| **Agents** | Specialized workers for complex tasks | Markdown files with agent config |
| **Commands** | User-triggered actions (like `/score`) | Markdown files defining the command |
| **Hooks** | Automatic triggers on events | JSON configuration |

### The Technology Stack

Everything is built with:
- **Markdown**: All skills, agents, and commands are Markdown files
- **JSON**: Configuration files (plugin.json, hooks.json)
- **No JavaScript/Python**: This isn't a traditional codebase - it's content

**Good news**: If you can write Markdown, you can contribute to this project.

---

## Prerequisites

### 1. Claude Code Installed

First, ensure Claude Code is installed on your machine.

**Windows**:
```bash
# Open PowerShell as Administrator
winget install Anthropic.ClaudeCode
```

**macOS**:
```bash
brew install claude-code
```

**Linux**:
```bash
curl -fsSL https://claude.ai/install.sh | sh
```

**Verify installation**:
```bash
claude --version
# Should output something like: Claude Code v2.x.x
```

### 2. A Text Editor

You'll need a text editor. Recommended options:

- **VS Code** (free) - Excellent Markdown preview
- **Cursor** (free) - VS Code fork with AI features
- **Sublime Text** (free/paid) - Lightweight and fast

Any editor that can open Markdown files will work.

### 3. Git (Optional but Recommended)

For version control:

**Windows**:
```bash
winget install Git.Git
```

**macOS**:
```bash
xcode-select --install
```

**Linux**:
```bash
sudo apt install git  # Debian/Ubuntu
sudo dnf install git  # Fedora
```

### 4. Basic Markdown Knowledge

If you're new to Markdown, here's a 2-minute primer:

```markdown
# This is a heading
## This is a smaller heading

This is a paragraph.

**This is bold text**
*This is italic text*

- This is a bullet point
- Another bullet point

1. Numbered item
2. Another numbered item

`This is inline code`

```
This is a code block
```

| Column 1 | Column 2 |
|----------|----------|
| Cell 1   | Cell 2   |
```

That's 90% of what you'll need.

---

## Setting Up Your Environment

### Step 1: Navigate to the Project

```bash
# Windows
cd C:\Users\YourName\path\to\ai-marketing

# macOS/Linux
cd /path/to/ai-marketing
```

### Step 2: Understand the Plugin Location

The plugin lives in a special folder:

```
ai-marketing/
├── .claude/
│   └── plugins/
│       └── ai-marketer/      <-- The plugin folder
│           ├── plugin.json   <-- Plugin manifest
│           ├── CLAUDE.md     <-- Plugin-level context
│           ├── README.md     <-- Plugin documentation
│           ├── skills/       <-- All skills here
│           ├── agents/       <-- All agents here
│           ├── commands/     <-- All commands here
│           └── hooks/        <-- Hooks configuration
└── docs/                     <-- Documentation
```

### Step 3: Open in Your Editor

**VS Code**:
```bash
code .
```

**Or manually**: Open your editor → File → Open Folder → Select the project folder

### Step 4: Start Claude Code

In a terminal, navigate to the project and run:

```bash
claude
```

This starts Claude Code with the plugin active.

### Step 5: Verify Plugin is Loaded

In Claude Code, try:

```
What marketing commands are available?
```

Claude should mention `/score`, `/audit`, `/readme`, `/compete`, and `/voice`.

---

## Understanding the Project Structure

### The Complete File Tree

```
.claude/plugins/ai-marketer/
│
├── plugin.json                 # Plugin manifest (name, version, paths)
├── CLAUDE.md                   # Reference material for Claude
├── README.md                   # Human-readable plugin docs
│
├── skills/                     # Knowledge modules
│   ├── awareness-analyzer/     # Framework 1
│   │   ├── SKILL.md           # Main skill definition
│   │   └── awareness-levels.md # Supporting reference
│   │
│   ├── persuasion-auditor/     # Framework 2
│   │   ├── SKILL.md
│   │   └── cialdini-checklist.md
│   │
│   ├── copy-optimizer/         # Framework 3
│   │   └── SKILL.md
│   │
│   ├── nesb-scorer/            # Framework 4
│   │   └── SKILL.md
│   │
│   ├── tribe-builder/          # Framework 5
│   │   └── SKILL.md
│   │
│   ├── voice-extractor/        # Voice analysis
│   │   └── SKILL.md
│   │
│   ├── competitor-analyzer/    # Competition analysis
│   │   └── SKILL.md
│   │
│   └── content-generator/      # Content generation
│       ├── SKILL.md
│       ├── github-readme.md
│       └── social-posts.md
│
├── agents/                     # Subagent definitions
│   ├── market-researcher.md    # Research agent
│   ├── copy-writer.md          # Writing agent
│   └── content-reviewer.md     # Review agent
│
├── commands/                   # Slash commands
│   ├── audit.md               # /audit
│   ├── readme.md              # /readme
│   ├── score.md               # /score
│   ├── compete.md             # /compete
│   └── voice.md               # /voice
│
└── hooks/
    └── hooks.json             # Event triggers
```

### Key Files Explained

#### plugin.json
The plugin manifest. Tells Claude Code what's in the plugin.

```json
{
  "name": "ai-marketer",
  "version": "1.0.0",
  "description": "Marketing frameworks plugin",
  "skills": "skills",      // Points to skills folder
  "agents": "agents",      // Points to agents folder
  "commands": "commands",  // Points to commands folder
  "hooks": "hooks/hooks.json"
}
```

#### SKILL.md Files
Each skill has a `SKILL.md` file with frontmatter:

```markdown
---
name: nesb-scorer
description: Score content against NEW-EASY-SAFE-BIG framework
allowed-tools: [Read, WebFetch]
invocation: automatic or "nesb"
---

# NESB Scorer

[Content that Claude reads when using this skill]
```

The frontmatter (between `---`) is configuration. Everything after is the skill content.

#### Agent Files
Agents are specialized workers:

```markdown
---
name: content-reviewer
description: Reviews generated content quality
model: haiku
allowed-tools: [Read]
---

# Content Reviewer Agent

[Instructions for the agent]
```

#### Command Files
Commands are user-triggered:

```markdown
---
name: score
description: Score a headline against NESB framework
---

# Score Command

[Instructions for what happens when user types /score]
```

---

## Your First Change

Let's make a small change to see how development works.

### Task: Add a New Example to NESB Scorer

**Step 1**: Open the file

```
.claude/plugins/ai-marketer/skills/nesb-scorer/SKILL.md
```

**Step 2**: Find the examples section

Look for a section with example headlines.

**Step 3**: Add a new example

Add this before the existing examples:

```markdown
**Example: Tech Product**
- Original: "Cloud-based data solution"
- Score: 8/40 (Weak)
- Improved: "Stop losing sales to slow data. Get answers in milliseconds, not minutes. Trusted by 1,000+ e-commerce teams."
- Improved Score: 34/40
```

**Step 4**: Save the file

**Step 5**: Test it

Start Claude Code:
```bash
claude
```

Then try:
```
Score this headline: "Cloud-based data solution"
```

Claude should reference the NESB framework and potentially use your new example as reference.

---

## Running and Testing

### Testing a Skill

1. Start Claude Code:
   ```bash
   claude
   ```

2. Ask Claude to use the skill:
   ```
   Use the nesb-scorer skill to analyze: "Fast and reliable API"
   ```

3. Verify the output matches expectations

### Testing a Command

1. Start Claude Code:
   ```bash
   claude
   ```

2. Run the command:
   ```
   /score "Your test headline here"
   ```

3. Verify the output format and quality

### Testing an Agent

Agents are tested by triggering their use:

1. Start Claude Code:
   ```bash
   claude
   ```

2. Ask for something that triggers the agent:
   ```
   Do a deep competitive analysis of https://example.com
   ```

3. Claude should delegate to the market-researcher agent

### Debugging Issues

**If Claude doesn't recognize your changes**:

1. Make sure you saved the file
2. Restart Claude Code:
   ```bash
   # Exit Claude Code (Ctrl+C or type 'exit')
   claude
   ```

**If Claude gives unexpected output**:

1. Check the skill/agent/command file for errors
2. Look for unclosed frontmatter (`---`)
3. Verify the file is in the correct location

**If a command doesn't work**:

1. Check `plugin.json` points to the commands folder
2. Verify the command file has valid frontmatter
3. Check the command name matches what you're typing

---

## Common Development Tasks

### Adding a New Skill

1. Create a folder in `skills/`:
   ```
   skills/my-new-skill/
   ```

2. Create `SKILL.md`:
   ```markdown
   ---
   name: my-new-skill
   description: What this skill does
   allowed-tools: [Read, WebFetch]
   ---

   # My New Skill

   [Content here]
   ```

3. Restart Claude Code to load it

### Adding a New Command

1. Create file in `commands/`:
   ```
   commands/mycommand.md
   ```

2. Add content:
   ```markdown
   ---
   name: mycommand
   description: What /mycommand does
   ---

   # My Command

   When the user types /mycommand, do the following:

   [Instructions]
   ```

3. Restart Claude Code to load it

### Adding Supporting Files

Skills can have supporting files that load on-demand:

```
skills/my-skill/
├── SKILL.md              # Main skill (always loaded)
├── examples.md           # Supporting file (loaded when needed)
└── detailed-reference.md # Another supporting file
```

Reference them in SKILL.md:
```markdown
For detailed examples, see [examples.md](./examples.md).
```

### Modifying Hooks

Edit `hooks/hooks.json`:

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": {
          "tool": "Write",
          "path": "**/README.md"
        },
        "description": "What this hook does",
        "command": "echo 'Hook triggered'"
      }
    ]
  }
}
```

---

## Next Steps

Now that you have your environment set up:

1. **Read the Architecture Overview**: [architecture.md](./architecture.md)
   - Understand how all pieces fit together
   - Learn the design decisions

2. **Learn to Add Features**: [adding-features.md](./adding-features.md)
   - Step-by-step guide to adding new capabilities
   - Real examples you can follow

3. **Understand Testing**: [testing.md](./testing.md)
   - How to test your changes
   - What to verify before submitting

4. **Contributing Guidelines**: [contributing.md](./contributing.md)
   - How to submit your work
   - Code style and conventions

---

## Quick Reference

### File Locations
| What | Where |
|------|-------|
| Plugin manifest | `.claude/plugins/ai-marketer/plugin.json` |
| Skills | `.claude/plugins/ai-marketer/skills/` |
| Agents | `.claude/plugins/ai-marketer/agents/` |
| Commands | `.claude/plugins/ai-marketer/commands/` |
| Hooks | `.claude/plugins/ai-marketer/hooks/hooks.json` |

### Common Commands
| Task | Command |
|------|---------|
| Start Claude Code | `claude` |
| Exit Claude Code | `exit` or Ctrl+C |
| Check plugin loading | Ask "What marketing commands are available?" |

### Frontmatter Fields
| Field | Purpose |
|-------|---------|
| `name` | Identifier for the skill/agent/command |
| `description` | What it does |
| `allowed-tools` | What tools it can use |
| `model` | (Agents only) Which model to use |
| `invocation` | (Skills) How it's triggered |

---

## Need Help?

- Check [Troubleshooting](../troubleshooting.md) for common issues
- Read the [FAQ](../faq.md)
- Look at existing skills/agents/commands as examples
- Review the [Architecture](./architecture.md) for understanding

---

## Acknowledgements

This project was inspired by the YouTube video ["These 5 Books Reveal Why Most AI Products Don't Sell"](https://www.youtube.com/watch?v=OLjTWl4Ci10). All code and documentation were generated by [Claude Code](https://claude.ai/code) powered by Claude Opus 4.5.

---

*Next: [Architecture Overview](./architecture.md)*
