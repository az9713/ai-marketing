# Testing Guide

This guide explains how to test your changes to the AI Marketer plugin. Since the plugin is content-based (Markdown files), testing is primarily manual verification.

---

## Table of Contents

1. [Testing Philosophy](#testing-philosophy)
2. [Testing Skills](#testing-skills)
3. [Testing Commands](#testing-commands)
4. [Testing Agents](#testing-agents)
5. [Testing Hooks](#testing-hooks)
6. [Test Cases](#test-cases)
7. [Regression Testing](#regression-testing)
8. [Troubleshooting Test Failures](#troubleshooting-test-failures)

---

## Testing Philosophy

### Why Manual Testing?

Unlike traditional code, Claude Code plugins are:
- **Content-based**: Markdown files interpreted by Claude
- **AI-evaluated**: Outputs depend on Claude's interpretation
- **Context-sensitive**: Same input may produce varied outputs

This means automated unit tests aren't practical. Instead, we use structured manual testing.

### Testing Goals

1. **Functionality**: Does the feature work as expected?
2. **Quality**: Is the output good/useful?
3. **Robustness**: Does it handle edge cases?
4. **Consistency**: Are outputs reasonably consistent?

### Testing Mindset

When testing:
- Try to break things (adversarial testing)
- Test edge cases, not just happy paths
- Document unexpected behaviors
- Compare before/after for changes

---

## Testing Skills

### Basic Skill Test

**Goal**: Verify the skill loads and is used appropriately.

**Steps**:

1. Start Claude Code:
   ```bash
   claude
   ```

2. Ask something that should trigger the skill:
   ```
   Analyze this headline using NESB: "AI-powered tool for developers"
   ```

3. Verify:
   - [ ] Claude uses the skill
   - [ ] Output matches expected format
   - [ ] Framework is applied correctly
   - [ ] Examples/reference material is used

### Skill Invocation Test

**Goal**: Verify explicit invocation works.

**Steps**:

1. If the skill has explicit invocation, test it:
   ```
   Use the nesb-scorer skill to analyze: "Your headline here"
   ```

2. Verify:
   - [ ] Skill is explicitly loaded
   - [ ] Output is appropriate

### Skill Integration Test

**Goal**: Verify skills work together.

**Steps**:

1. Ask for something requiring multiple skills:
   ```
   Do a full marketing audit of this headline using all available frameworks
   ```

2. Verify:
   - [ ] Multiple skills are used
   - [ ] Output combines insights from all
   - [ ] No conflicts between skills

### Skill Quality Test

**Goal**: Verify output quality.

**Steps**:

1. Prepare 3-5 test inputs with known expected quality
2. Run each through the skill
3. Rate output quality:
   - Score accuracy
   - Suggestion relevance
   - Format correctness

**Example Test Inputs**:

| Input | Expected Score Range | Expected Issues |
|-------|---------------------|-----------------|
| "AI-powered tool" | 10-15/40 | Generic, no NEW/EASY/SAFE/BIG |
| "10x faster coding" | 20-25/40 | Has BIG, missing SAFE |
| "Join 50,000 devs shipping faster" | 28-35/40 | Hits most dimensions |

---

## Testing Commands

### Command Recognition Test

**Goal**: Verify command is recognized.

**Steps**:

1. Start Claude Code:
   ```bash
   claude
   ```

2. Type the command:
   ```
   /score "test headline"
   ```

3. Verify:
   - [ ] Command is recognized (not treated as regular text)
   - [ ] Appropriate action is taken
   - [ ] Output format matches documentation

### Command Parameter Test

**Goal**: Verify parameters are handled correctly.

**Steps**:

1. Test with required parameters:
   ```
   /score "headline with all parameters"
   ```

2. Test without parameters (if optional):
   ```
   /score
   ```

3. Test with malformed input:
   ```
   /score
   /score ""
   /score very long headline without quotes that goes on and on
   ```

4. Verify:
   - [ ] Required parameters prompt if missing
   - [ ] Optional parameters use defaults
   - [ ] Malformed input is handled gracefully

### Command Output Test

**Goal**: Verify output quality and format.

**Steps**:

1. Run command with known input:
   ```
   /score "Stop losing hours to debugging. Ship 3x faster."
   ```

2. Verify output includes:
   - [ ] Score (in expected range)
   - [ ] Breakdown by dimension
   - [ ] Suggestions for improvement
   - [ ] Alternative headlines

3. Compare output format to documentation

### Command Edge Cases

Test these edge cases:

| Test Case | Input | Expected Behavior |
|-----------|-------|-------------------|
| Empty input | `/score ""` | Prompt for input |
| Very long input | `/score "[500 words]"` | Handle gracefully |
| Special characters | `/score "Test & <test>"` | Handle correctly |
| Non-English | `/score "Testez notre outil"` | Attempt to score |
| Numbers only | `/score "123456"` | Low score, explain why |

---

## Testing Agents

### Agent Delegation Test

**Goal**: Verify agent is called when appropriate.

**Steps**:

1. Ask for something that should trigger agent:
   ```
   Do a deep competitive analysis of https://github.com/example/repo
   ```

2. Verify:
   - [ ] Claude delegates to the agent
   - [ ] Agent performs expected work
   - [ ] Results return to main context

### Agent Isolation Test

**Goal**: Verify agent works in isolation.

**Steps**:

1. Ask for something with many steps:
   ```
   Analyze these 3 competitors and compare their positioning:
   - competitor1.com
   - competitor2.com
   - competitor3.com
   ```

2. Verify:
   - [ ] Agent handles all steps
   - [ ] Context doesn't leak back to main conversation
   - [ ] Results are structured and complete

### Agent Quality Test

**Goal**: Verify agent output quality.

**Steps**:

1. Prepare test URLs with known characteristics
2. Have agent analyze them
3. Compare output to expected insights

**Example**:
- Known high-quality landing page → Agent should identify good elements
- Known weak landing page → Agent should identify weaknesses

---

## Testing Hooks

### Hook Trigger Test

**Goal**: Verify hook fires on expected event.

**Steps**:

1. Trigger the event that should fire the hook:
   ```
   [Use Write tool to create a README.md file]
   ```

2. Verify:
   - [ ] Hook message appears
   - [ ] Message is helpful
   - [ ] Timing is appropriate

### Hook Matcher Test

**Goal**: Verify matcher patterns work correctly.

**Steps for PostToolUse**:

1. Test exact match:
   ```
   Write README.md  → Should trigger
   Write readme.md  → Should/shouldn't trigger (case sensitivity)
   Write OTHER.md   → Should NOT trigger
   ```

2. Test glob patterns:
   ```
   Write folder/README.md  → Should trigger (**)
   Write deep/nested/README.md → Should trigger (**)
   ```

**Steps for UserPromptSubmit**:

1. Test regex matches:
   ```
   "help with readme" → Should trigger (?i).*readme.*
   "help with README" → Should trigger (case insensitive)
   "help with file" → Should NOT trigger
   ```

### Hook Non-Interference Test

**Goal**: Verify hooks don't break normal operation.

**Steps**:

1. Perform normal operations
2. Verify hooks don't:
   - [ ] Block operations
   - [ ] Cause errors
   - [ ] Slow things down significantly

---

## Test Cases

### Standard Test Suite

Run these tests after any significant change:

#### Test Case 1: Basic Scoring
```
Input: /score "AI-powered development tool"
Expected:
- Score in range 10-18/40
- Identifies "generic" as issue
- Suggests specific improvements
```

#### Test Case 2: Good Headline Scoring
```
Input: /score "Stop losing 10 hours weekly. Join 50,000 devs shipping 10x faster."
Expected:
- Score in range 32-38/40
- High marks on all 4 dimensions
- Minimal improvement suggestions
```

#### Test Case 3: Full Audit
```
Input: /audit https://github.com/[known test repo]
Expected:
- Overall score provided
- NESB breakdown
- Persuasion lever analysis
- Specific recommendations
```

#### Test Case 4: README Generation
```
Input: /readme
(Then provide answers about a test product)
Expected:
- Complete README structure
- NESB-optimized headline
- Social proof section
- Quick-start guide
```

#### Test Case 5: Voice Extraction
```
Input: /voice [paste sample text]
Expected:
- Voice profile with 3 words
- Tone ratings
- Signature patterns
- Generation guidelines
```

### Edge Case Test Suite

#### Test Case E1: No Input
```
Input: /score
Expected: Prompt for headline input
```

#### Test Case E2: Invalid URL
```
Input: /audit https://nonexistent-site-12345.com
Expected: Graceful error message
```

#### Test Case E3: Non-Marketing Content
```
Input: /score "function calculateTotal(items) { return items.reduce((a,b) => a+b); }"
Expected: Low score with explanation that this isn't marketing copy
```

---

## Regression Testing

### What is Regression Testing?

After making changes, verify existing functionality still works.

### Regression Test Checklist

After any change, test:

- [ ] `/score` basic functionality
- [ ] `/audit` on a known URL
- [ ] `/readme` generation flow
- [ ] `/compete` on a known competitor
- [ ] `/voice` with sample text

### Change-Specific Testing

| If You Changed... | Also Test... |
|-------------------|--------------|
| Any skill | All commands that might use it |
| A command | That specific command thoroughly |
| An agent | Tasks that delegate to it |
| hooks.json | All hook triggers |
| plugin.json | Plugin loading entirely |

---

## Troubleshooting Test Failures

### Skill Not Loading

**Symptoms**:
- Claude doesn't use the skill
- Generic responses instead of framework-based

**Checks**:
1. Verify file is saved
2. Check frontmatter syntax (valid YAML between `---`)
3. Restart Claude Code
4. Check file is in correct location

### Command Not Recognized

**Symptoms**:
- `/command` treated as regular text
- No action taken

**Checks**:
1. Verify filename matches command name
2. Check frontmatter `name` field
3. Verify plugin.json points to commands folder
4. Restart Claude Code

### Agent Not Delegating

**Symptoms**:
- Claude handles everything in main context
- No agent behavior observed

**Checks**:
1. Verify agent file exists
2. Check frontmatter is valid
3. Check model specification (sonnet/haiku)
4. Try explicit agent request

### Hook Not Firing

**Symptoms**:
- Expected message doesn't appear
- No hook behavior

**Checks**:
1. Verify hooks.json syntax (valid JSON)
2. Check matcher pattern
3. Verify event is actually occurring
4. Test pattern separately

### Unexpected Output

**Symptoms**:
- Output doesn't match expected format
- Wrong information

**Checks**:
1. Check skill/command instructions
2. Verify examples in skill
3. Look for conflicting instructions
4. Test with simpler input

---

## Test Documentation Template

When adding new features, document tests:

```markdown
## Test: [Feature Name]

### Basic Functionality
- [ ] Test case 1: [description]
- [ ] Test case 2: [description]

### Edge Cases
- [ ] Empty input
- [ ] Invalid input
- [ ] Large input

### Integration
- [ ] Works with existing skills
- [ ] No conflicts

### Expected Outputs
[Example of expected output]

### Known Limitations
[Any known issues or limitations]
```

---

## Testing Best Practices

1. **Test after every change**: Don't accumulate untested changes
2. **Test in fresh session**: Restart Claude Code for clean state
3. **Document failures**: Note what broke and how
4. **Compare to baseline**: Know what "correct" looks like
5. **Test edge cases**: Most bugs hide at boundaries
6. **Get second opinion**: Have someone else try your feature

---

*Next: [Contributing Guide](./contributing.md)*
