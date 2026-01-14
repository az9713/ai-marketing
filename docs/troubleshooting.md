# Troubleshooting Guide

This guide helps you solve common problems with AI Marketer. Find your issue below and follow the steps to resolve it.

---

## Table of Contents

1. [Installation Issues](#installation-issues)
2. [Plugin Not Loading](#plugin-not-loading)
3. [Command Issues](#command-issues)
4. [Scoring Issues](#scoring-issues)
5. [Output Quality Issues](#output-quality-issues)
6. [Performance Issues](#performance-issues)
7. [Common Mistakes](#common-mistakes)
8. [Getting More Help](#getting-more-help)

---

## Installation Issues

### Problem: Claude Code Not Installed

**Symptoms**:
- `claude` command not found
- Terminal doesn't recognize Claude Code

**Solution**:

1. Install Claude Code:

   **Windows**:
   ```bash
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

2. Restart your terminal

3. Verify installation:
   ```bash
   claude --version
   ```

### Problem: Plugin Not Installing

**Symptoms**:
- Error when running `/plugins install ai-marketer`
- Plugin doesn't appear in list

**Solution**:

1. Check you're in the correct directory:
   ```bash
   # The .claude/plugins/ai-marketer folder should exist
   ls .claude/plugins/ai-marketer
   ```

2. If the folder exists, the plugin should auto-load when you start Claude Code from that directory

3. Start Claude Code from the project root:
   ```bash
   cd /path/to/ai-marketing
   claude
   ```

---

## Plugin Not Loading

### Problem: Commands Not Recognized

**Symptoms**:
- `/score` is treated as regular text
- Claude doesn't know about marketing frameworks

**Solution**:

1. **Verify you're in the right directory**:
   ```bash
   pwd
   # Should show path ending in ai-marketing
   ```

2. **Check plugin structure**:
   ```bash
   ls .claude/plugins/ai-marketer/
   # Should show: plugin.json, skills/, commands/, etc.
   ```

3. **Verify plugin.json exists and is valid**:
   ```bash
   cat .claude/plugins/ai-marketer/plugin.json
   ```
   Should show valid JSON like:
   ```json
   {
     "name": "ai-marketer",
     "version": "1.0.0",
     ...
   }
   ```

4. **Restart Claude Code**:
   - Exit Claude Code (type `exit` or Ctrl+C)
   - Start again: `claude`

5. **Test plugin loading**:
   ```
   What marketing commands do you have available?
   ```
   Claude should mention `/score`, `/audit`, `/readme`, etc.

### Problem: Skills Not Being Used

**Symptoms**:
- Claude gives generic responses
- Frameworks not applied

**Solution**:

1. **Be explicit in your request**:
   ```
   Use the NESB framework to score this headline: "Test headline"
   ```

2. **Check skill files exist**:
   ```bash
   ls .claude/plugins/ai-marketer/skills/
   # Should show skill folders
   ```

3. **Verify SKILL.md frontmatter**:
   Each skill should have valid frontmatter:
   ```yaml
   ---
   name: skill-name
   description: What it does
   ---
   ```

---

## Command Issues

### Problem: /score Returns No Output

**Symptoms**:
- Command runs but nothing happens
- No score displayed

**Solution**:

1. **Provide input correctly**:
   ```
   /score "Your headline in quotes"
   ```

2. **Try without quotes for simple headlines**:
   ```
   /score Simple headline here
   ```

3. **Check command file**:
   ```bash
   cat .claude/plugins/ai-marketer/commands/score.md
   ```
   Ensure frontmatter has `name: score`

### Problem: /audit Fails on URL

**Symptoms**:
- Error message about URL
- Can't access the page

**Solution**:

1. **Verify URL is public**:
   - Open the URL in your browser
   - If you need to log in, Claude can't access it

2. **Try with HTTPS**:
   ```
   /audit https://github.com/username/repo
   ```

3. **For private repos, paste content instead**:
   ```
   /audit

   Here's my README content:
   [paste content]
   ```

### Problem: /readme Doesn't Ask Questions

**Symptoms**:
- README generated without asking for input
- Generic output

**Solution**:

1. **Provide context upfront**:
   ```
   /readme

   My project is a CLI tool for developers that helps with X.
   Target audience: Y
   Differentiator: Z
   ```

2. **Ask for interactive mode**:
   ```
   /readme - please ask me questions about my project first
   ```

---

## Scoring Issues

### Problem: Scores Seem Too High/Low

**Symptoms**:
- Weak headline gets high score
- Strong headline gets low score

**Solution**:

1. **Understand NESB scoring**:
   - Score is 0-40 total (10 per dimension)
   - 28+ is "strong"
   - 20-27 is "average"
   - Below 20 is "weak"

2. **Check for specific dimensions**:
   ```
   Score this and explain each dimension: "Your headline"
   ```

3. **Request breakdown**:
   ```
   Give me a detailed NESB breakdown with justification for each score
   ```

### Problem: Inconsistent Scores

**Symptoms**:
- Same headline gets different scores
- Scoring varies between sessions

**Solution**:

1. **This is expected behavior**: Claude's responses have natural variation

2. **For consistency, be specific**:
   ```
   Score this headline strictly against NESB criteria: "headline"
   ```

3. **Average multiple scores**: Run 3 times and average for important decisions

4. **Focus on ranges**: A headline scoring 25-30 is "strong" - exact number less important

---

## Output Quality Issues

### Problem: Generated Content Sounds Generic

**Symptoms**:
- README sounds like every other AI tool
- No personality in output

**Solution**:

1. **Use voice extraction first**:
   ```
   /voice

   Here's some of my writing:
   [paste 300-500 words of your existing content]
   ```

2. **Reference the voice profile**:
   ```
   Generate a README in my voice profile: [voice characteristics]
   ```

3. **Provide examples of what you like**:
   ```
   Generate content similar in style to this example: [example]
   ```

### Problem: Suggestions Don't Fit My Product

**Symptoms**:
- Improvement suggestions are off-target
- Examples don't match my domain

**Solution**:

1. **Provide more context**:
   ```
   My product is specifically for [audience] in [industry].
   Score this headline with that context: "headline"
   ```

2. **Ask for domain-specific examples**:
   ```
   Suggest improvements suitable for B2B developer tools
   ```

3. **Guide the output**:
   ```
   Improve this headline for a privacy-focused audience who values security
   ```

---

## Performance Issues

### Problem: Commands Take Too Long

**Symptoms**:
- Long wait times for responses
- Timeouts

**Solution**:

1. **This may be normal for**:
   - `/audit` (fetches and analyzes web pages)
   - `/compete` (visits competitor sites)
   - `/readme` (generates comprehensive content)

2. **For faster scoring**:
   - Use `/score` instead of `/audit` for quick checks
   - Score one headline at a time

3. **Check your internet connection**:
   - Web-based commands need internet access

### Problem: Claude Crashes or Hangs

**Symptoms**:
- No response for extended period
- Terminal becomes unresponsive

**Solution**:

1. **Force quit and restart**:
   - Press Ctrl+C multiple times
   - If unresponsive, close terminal
   - Restart: `claude`

2. **Try simpler input**:
   - Paste smaller content
   - Use shorter URLs
   - Test with basic commands first

---

## Common Mistakes

### Mistake 1: Not Being in the Right Directory

**Wrong**:
```bash
cd ~
claude
# Plugin not loaded - wrong directory
```

**Right**:
```bash
cd /path/to/ai-marketing
claude
# Plugin loads correctly
```

### Mistake 2: Expecting Code-Level Features

AI Marketer is a content-based plugin. It:
- ✅ Provides frameworks Claude can use
- ✅ Offers structured commands
- ❌ Cannot track state between sessions
- ❌ Cannot integrate with external APIs directly

### Mistake 3: Treating Scores as Absolute

NESB scores are **guidance, not gospel**:
- Use them to identify weak areas
- Don't obsess over hitting 40/40
- A 28/40 that sounds like you > 35/40 that sounds generic

### Mistake 4: Skipping Voice Extraction

**Problem**: Content sounds generic

**Solution**: Always run `/voice` first with samples of your existing content

### Mistake 5: Not Providing Context

**Vague**:
```
/score "Fast tool"
```

**Better**:
```
Score this headline for a B2B developer tools company targeting senior engineers: "Fast tool"
```

---

## Getting More Help

### Check the Documentation

| Document | What It Covers |
|----------|----------------|
| [Quick Start](./user-guide/quick-start.md) | Basic usage examples |
| [Complete Guide](./user-guide/complete-guide.md) | All features explained |
| [Command Reference](./user-guide/command-reference.md) | Detailed command docs |
| [FAQ](./faq.md) | Common questions |

### Search for Known Issues

Check if your issue is already known:
1. Search GitHub Issues
2. Look for similar problems
3. Check if there's a workaround

### Report a Bug

If nothing works:

1. **Gather information**:
   - What you tried to do
   - What happened instead
   - Error messages (if any)
   - Your environment (OS, Claude Code version)

2. **Open a GitHub Issue**:
   - Use the bug report template
   - Include reproduction steps
   - Add relevant screenshots

3. **Be specific**:
   - "It doesn't work" → Hard to help
   - "/score returns blank output when given a headline with quotes" → Actionable

---

## Quick Fixes Reference

| Problem | Quick Fix |
|---------|-----------|
| Commands not working | Restart Claude Code from project root |
| Low quality output | Use /voice first, provide more context |
| Scores seem wrong | Ask for detailed breakdown |
| Can't access URL | Paste content directly instead |
| Generic content | Extract voice first, be specific about audience |
| Slow performance | Use simpler commands, check internet |

---

*Still stuck? Open an issue on GitHub with details about your problem.*
