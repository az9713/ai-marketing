# Contributing Guide

Thank you for your interest in contributing to AI Marketer! This guide explains how to contribute effectively.

---

## Table of Contents

1. [Ways to Contribute](#ways-to-contribute)
2. [Getting Started](#getting-started)
3. [Making Changes](#making-changes)
4. [Submitting Your Work](#submitting-your-work)
5. [Code Style Guidelines](#code-style-guidelines)
6. [Review Process](#review-process)
7. [Recognition](#recognition)

---

## Ways to Contribute

### For Everyone

| Contribution Type | Description | Difficulty |
|-------------------|-------------|------------|
| Bug reports | Report issues you find | Easy |
| Documentation fixes | Fix typos, clarify text | Easy |
| Use case examples | Share how you use the tool | Easy |
| Feature suggestions | Propose new features | Easy |

### For Developers

| Contribution Type | Description | Difficulty |
|-------------------|-------------|------------|
| New skills | Add marketing frameworks | Medium |
| New commands | Add user actions | Medium |
| New templates | Add content types | Medium |
| New agents | Add specialized workers | Medium |
| Bug fixes | Fix reported issues | Varies |
| Performance improvements | Make things faster | Hard |

---

## Getting Started

### Step 1: Fork the Repository

1. Go to the project on GitHub
2. Click "Fork" button
3. You now have your own copy

### Step 2: Clone Your Fork

```bash
git clone https://github.com/YOUR-USERNAME/ai-marketing.git
cd ai-marketing
```

### Step 3: Create a Branch

Always work on a new branch, not main:

```bash
git checkout -b feature/my-new-feature
# or
git checkout -b fix/bug-description
```

**Branch naming conventions**:
- `feature/` for new features
- `fix/` for bug fixes
- `docs/` for documentation changes
- `refactor/` for code improvements

### Step 4: Set Up Development Environment

See [Developer Getting Started](./getting-started.md) for full setup instructions.

Quick version:
1. Ensure Claude Code is installed
2. Navigate to project folder
3. Start Claude Code: `claude`
4. Verify plugin loads

---

## Making Changes

### Before You Code

1. **Check for existing work**: Search issues/PRs for similar work
2. **Open an issue first**: For significant changes, discuss before coding
3. **Understand the architecture**: Read [Architecture Overview](./architecture.md)

### While Coding

1. **Make small, focused changes**: One feature or fix per PR
2. **Follow existing patterns**: Look at how similar things are done
3. **Test as you go**: Don't wait until the end
4. **Commit frequently**: Small, logical commits

### Commit Messages

Write clear, descriptive commit messages:

```
Good:
- "Add email marketing skill with PAS framework"
- "Fix NESB scoring for headlines with numbers"
- "Update README with new command examples"

Bad:
- "Updates"
- "Fixed stuff"
- "WIP"
```

**Format**:
```
[type]: [brief description]

[optional longer description]

[optional references to issues]
```

**Types**:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation change
- `refactor`: Code improvement (no behavior change)
- `test`: Adding tests
- `chore`: Maintenance tasks

**Examples**:
```
feat: add /email command for marketing email generation

Adds a new slash command that generates marketing emails
applying all 5 frameworks. Includes templates for:
- Welcome emails
- Launch emails
- Follow-up sequences

Closes #42
```

---

## Submitting Your Work

### Step 1: Test Your Changes

Before submitting:

1. Run through the [Testing Guide](./testing.md)
2. Verify all existing features still work
3. Test your new feature thoroughly

### Step 2: Update Documentation

If you added/changed functionality:

1. Update relevant docs in `docs/`
2. Add examples to commands/skills
3. Update CLAUDE.md if needed

### Step 3: Create Pull Request

1. Push your branch:
   ```bash
   git push origin feature/my-new-feature
   ```

2. Go to GitHub and click "New Pull Request"

3. Fill out the PR template:

```markdown
## Description
[What does this PR do?]

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation update
- [ ] Other (describe)

## Testing Done
- [ ] Tested basic functionality
- [ ] Tested edge cases
- [ ] Ran regression tests
- [ ] Updated/added documentation

## Related Issues
Closes #[issue number]

## Screenshots (if applicable)
[Add screenshots of new features]
```

### Step 4: Address Feedback

1. Respond to review comments
2. Make requested changes
3. Push updates to the same branch
4. The PR will update automatically

---

## Code Style Guidelines

### Markdown Files

**Structure**:
```markdown
# Title (H1 - only one per file)

Brief introduction.

---

## Table of Contents (for longer files)

1. [Section 1](#section-1)
2. [Section 2](#section-2)

---

## Section 1

Content...

### Subsection 1.1

More content...

---

## Section 2

Content...
```

**Formatting**:
- Use `---` to separate major sections
- Use tables for structured data
- Use code blocks with language tags
- Use bullet points for lists
- Keep lines under 100 characters when possible

**Example of good formatting**:
```markdown
## The NESB Framework

Every headline should hit these 4 quadrants:

| Quadrant | Brain Response | Example |
|----------|----------------|---------|
| NEW | Craves novelty | "The first..." |
| EASY | Conserves energy | "One-click..." |
| SAFE | Fears risk | "Trusted by..." |
| BIG | Wants status | "10x..." |

### Scoring Guidelines

Score each dimension 0-10:

1. **0-2**: Missing entirely
2. **3-5**: Present but weak
3. **6-8**: Strong
4. **9-10**: Exceptional
```

### Frontmatter

**Format**:
```yaml
---
name: skill-name
description: Brief, clear description
allowed-tools: [Tool1, Tool2]
invocation: automatic
---
```

**Rules**:
- Use lowercase for `name`
- Use hyphens, not underscores
- Keep `description` under 80 characters
- Only include allowed-tools the skill actually needs

### JSON Files

**Format**:
```json
{
  "key": "value",
  "array": [
    "item1",
    "item2"
  ],
  "nested": {
    "key": "value"
  }
}
```

**Rules**:
- 2-space indentation
- Double quotes for strings
- No trailing commas
- Validate JSON before committing

---

## Review Process

### What Reviewers Look For

1. **Functionality**: Does it work as intended?
2. **Quality**: Is the output good?
3. **Consistency**: Does it follow existing patterns?
4. **Documentation**: Is it well-documented?
5. **Testing**: Was it adequately tested?

### Review Timeline

- Simple fixes: 1-2 days
- New features: 3-5 days
- Major changes: 1-2 weeks

### Review Outcomes

| Outcome | Meaning |
|---------|---------|
| Approved | Ready to merge |
| Changes requested | Need modifications |
| Needs discussion | Requires further conversation |

### After Approval

1. Maintainer merges the PR
2. Changes go to main branch
3. Documentation updates automatically
4. You're credited in contributors list

---

## Recognition

### Contributors List

All contributors are recognized in:
- GitHub contributors page
- README credits section

### Types of Recognition

| Contribution | Recognition |
|--------------|-------------|
| Bug fix | Contributors list |
| New feature | Contributors list + feature credit |
| Major contribution | Contributors list + special mention |
| Ongoing contributions | Collaborator invite |

---

## Quick Reference

### File Locations

| Adding... | Location |
|-----------|----------|
| Skill | `.claude/plugins/ai-marketer/skills/[name]/SKILL.md` |
| Command | `.claude/plugins/ai-marketer/commands/[name].md` |
| Agent | `.claude/plugins/ai-marketer/agents/[name].md` |
| Hook | `.claude/plugins/ai-marketer/hooks/hooks.json` |
| User docs | `docs/user-guide/` |
| Dev docs | `docs/developer-guide/` |

### Checklist for PRs

- [ ] Branch created from latest main
- [ ] Changes are focused and small
- [ ] Follows existing patterns
- [ ] Tested thoroughly
- [ ] Documentation updated
- [ ] Commit messages are clear
- [ ] PR description complete
- [ ] No conflicts with main

### Getting Help

- Open an issue for questions
- Ask in discussions
- Ping maintainers in PR comments

---

## Thank You!

Every contribution matters. Whether you're fixing a typo or adding a major feature, you're helping make AI Marketer better for everyone.

We're excited to see what you build!

---

*Questions? Open an issue or start a discussion on GitHub.*
