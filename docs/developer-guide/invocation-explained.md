# Command Invocation Explained

This document clarifies the two different ways to invoke commands in AI Marketer and explains whether they produce the same results.

---

## The Two Invocation Mechanisms

### Mechanism 1: Slash Command (Formal)

```
/ai-marketer:score "Your headline"
```

**How it works:**
1. Claude Code recognizes the `/ai-marketer:score` syntax
2. Claude Code loads `commands/score.md` from the plugin
3. Claude follows the instructions in the command file
4. `CLAUDE.md` is also available as project context
5. Skills may be loaded based on their `invocation` setting

**When it works:**
- Plugin must be properly registered in `.claude-plugin/plugin.json`
- Command file must exist in `commands/` folder

### Mechanism 2: Natural Language (Informal)

```
score "Your headline"
```

**How it works:**
1. Claude reads `CLAUDE.md` when entering the project directory
2. `CLAUDE.md` contains command instructions (lines 25-55 for `score`)
3. Claude interprets "score" based on CLAUDE.md context
4. Claude executes the scoring using the framework knowledge in CLAUDE.md
5. Skills may be loaded based on their `invocation` setting

**When it works:**
- Must be in the project directory (so CLAUDE.md is loaded)
- Works even if the plugin is not formally registered

---

## Are the Results the Same?

### Short Answer: **Yes, the results are essentially identical.**

### Why?

Both mechanisms have access to the same knowledge:

| Resource | Slash Command | Natural Language |
|----------|---------------|------------------|
| `CLAUDE.md` | ✅ Available (project context) | ✅ Available (project context) |
| `commands/score.md` | ✅ Formally loaded | ❌ Not loaded |
| `skills/nesb-scorer/SKILL.md` | ✅ May be loaded | ✅ May be loaded |
| NESB Framework knowledge | ✅ From CLAUDE.md | ✅ From CLAUDE.md |

**Key insight**: `CLAUDE.md` is **always loaded** when Claude is in the project directory. This file contains the complete scoring instructions:

```markdown
### score [text]

Score the given headline/copy against the NESB framework (0-40).

**How to score:**
- **NEW** (0-10): Is it novel? "The first...", "Unlike...", unique mechanism?
- **EASY** (0-10): Is it effortless? "One-click", "Zero config", "5 minutes"?
- **SAFE** (0-10): Is it trustworthy? "Trusted by X", testimonials, guarantees?
- **BIG** (0-10): Is the outcome transformational? "10x", "Dominate", major result?
```

Since both mechanisms use CLAUDE.md (which contains the full framework), the scoring results are the same.

---

## Visual Comparison

### Slash Command Path

```
/ai-marketer:score "headline"
         │
         ▼
┌─────────────────────────────────┐
│ Claude Code Plugin System       │
│ Loads: commands/score.md        │
└─────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────┐
│ Project Context                 │
│ CLAUDE.md (always available)   │
│ - Contains NESB framework       │
│ - Contains scoring instructions │
└─────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────┐
│ Skills (if invocation matches)  │
│ skills/nesb-scorer/SKILL.md     │
└─────────────────────────────────┘
         │
         ▼
    [NESB Score Output]
```

### Natural Language Path

```
score "headline"
         │
         ▼
┌─────────────────────────────────┐
│ Project Context                 │
│ CLAUDE.md (always available)   │
│ - Contains NESB framework       │
│ - Contains scoring instructions │
└─────────────────────────────────┘
         │
         ▼
┌─────────────────────────────────┐
│ Skills (if invocation matches)  │
│ skills/nesb-scorer/SKILL.md     │
└─────────────────────────────────┘
         │
         ▼
    [NESB Score Output]
```

**The only difference**: The slash command path goes through `commands/score.md` first, but both paths use the same CLAUDE.md knowledge.

---

## When to Use Which?

| Scenario | Recommended | Reason |
|----------|-------------|--------|
| Quick testing | Natural language | Faster to type |
| Documentation examples | Both shown | Users may prefer either |
| Plugin not registered | Natural language | Slash commands won't work |
| Formal automation | Slash command | More explicit intent |

---

## The Role of Each File

### CLAUDE.md (Project Root)
- **Always loaded** when Claude enters the project
- Contains **executable instructions** for all commands
- Contains the **full 5 frameworks** for reference
- This is why natural language works

### commands/score.md (Plugin)
- Loaded **only when slash command is used**
- Contains command **metadata and format**
- References the framework but relies on CLAUDE.md for details

### skills/nesb-scorer/SKILL.md (Plugin)
- Contains the **most detailed** scoring criteria
- Has industry-specific examples and templates
- Loaded based on `invocation: user` setting
- Provides **additional depth** beyond CLAUDE.md

---

## Summary

| Question | Answer |
|----------|--------|
| Do both mechanisms work? | Yes |
| Do they produce the same results? | Yes (both use CLAUDE.md) |
| Is one "better" than the other? | No, use whichever you prefer |
| Why does natural language work? | CLAUDE.md contains full instructions |
| Why have slash commands? | Explicit invocation, plugin discoverability |

---

## Implications for Development

1. **CLAUDE.md is critical**: It must contain complete instructions because natural language relies on it entirely.

2. **Commands are optional shortcuts**: They provide explicit invocation but aren't required for functionality.

3. **Skills provide depth**: They contain detailed examples and templates that enhance both mechanisms.

4. **Keep them in sync**: If you update the scoring logic, update both CLAUDE.md and the skill file.

---

*See also: [Architecture Overview](./architecture.md) | [Adding Features](./adding-features.md)*
