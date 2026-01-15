# Glossary

This glossary defines terms used throughout the AI Marketer documentation. Terms are listed alphabetically.

---

## A

### Agent
A specialized Claude worker that handles complex, multi-step tasks in isolation. Agents have their own context and can use specified tools. Example: the market-researcher agent visits multiple competitor sites.

### Allowed-Tools
The tools an agent or skill can use. Defined in the frontmatter. Example: `allowed-tools: [Read, WebFetch]` means the skill can read files and fetch web pages.

### Awareness Level
From Eugene Schwartz's "Breakthrough Advertising": the degree to which your audience knows about their problem and potential solutions. Five levels: Unaware, Problem Aware, Solution Aware, Product Aware, Most Aware.

### Authority
One of Cialdini's 7 persuasion levers. People defer to experts. Example: "Built by ex-Google engineers" or "Featured in TechCrunch."

---

## B

### BIG
One of the four NESB dimensions. Appeals to the brain's desire for status and transformation. Examples: "10x faster", "dominate your market", "enterprise-grade."

---

## C

### Cialdini, Robert
Author of "Influence: The Psychology of Persuasion." Identified 7 levers of persuasion used in the persuasion-auditor skill.

### Claude Code
Anthropic's CLI tool for interacting with Claude in the terminal. AI Marketer is a plugin for Claude Code.

### CLAUDE.md
A file that provides context to Claude about a project or plugin. Located at project root or plugin root.

### Command (Slash Command)
A user-triggered action invoked with `/plugin-name:command` (e.g., `/ai-marketer:score`, `/ai-marketer:audit`, `/ai-marketer:readme`). Natural language alternatives also work (e.g., `score "headline"`). Defined in the `commands/` folder.

### Commitment & Consistency
One of Cialdini's 7 persuasion levers. People honor commitments and act consistently with past behavior. Example: Getting a small "yes" before asking for a big one.

### Copy
Marketing text. Short for "copywriting." Headlines, taglines, landing page text, etc.

### Copy Optimizer
A skill that applies tactical persuasion techniques (loss aversion, framing, etc.) to improve marketing copy.

---

## D

### Decoy Pricing
A pricing psychology technique where a third option makes the target option seem more attractive. Example: Basic ($9), Pro ($29 - target), Enterprise ($99).

---

## E

### EASY
One of the four NESB dimensions. Appeals to the brain's desire to conserve energy. Examples: "one-click", "zero configuration", "5 minutes to start."

---

## F

### Framework
A structured approach or model. AI Marketer implements 5 marketing frameworks from bestselling books.

### Frontmatter
YAML metadata at the top of a Markdown file, enclosed between `---` markers. Defines properties like name, description, and allowed-tools.

---

## G

### Glob
A pattern for matching file paths. Example: `**/README.md` matches any README.md in any folder.

---

## H

### Hook
An automatic trigger that fires on specific events. Types: PostToolUse (after tool completes), PreToolUse (before tool runs), Notification, Stop. Defined in `.claude/settings.local.json` or `.claude/settings.json`. For visible notifications, output JSON with `{"systemMessage": "..."}` — displays as "says:" message.

---

## I

### Invocation
How a skill is triggered. Can be "automatic" (Claude uses when relevant) or explicit (user requests specifically).

---

## L

### Liking
One of Cialdini's 7 persuasion levers. People buy from those they like. Example: "Built by developers, for developers."

### Loss Aversion
A psychological principle: people work harder to avoid losses than to achieve gains. Losses hurt ~2x more than equivalent gains feel good. Example: "Stop losing 10 hours/week" > "Save 10 hours/week."

---

## M

### Market Sophistication
From Eugene Schwartz: how exposed your market is to claims like yours. Five stages, from virgin market (simple claims work) to exhausted (need to sell identity).

### Matcher
A string pattern that determines when a hook fires. Matches tool names (e.g., `"Write"`, `"Write|Edit"`).

### Mechanism
Your unique approach to solving a problem. What makes your solution different. For Solution Aware audiences.

### Milligan, Kyle
Author of "Take Their Money." Created the NESB framework (NEW, EASY, SAFE, BIG).

### Model
The Claude model used by an agent. Options: sonnet (more capable, slower), haiku (faster, cheaper, less nuanced).

---

## N

### NESB
An acronym for the four emotional quadrants that effective marketing copy should hit: **N**EW, **E**ASY, **S**AFE, **B**IG. From Kyle Milligan's "Take Their Money."

### NEW
One of the four NESB dimensions. Appeals to the brain's craving for novelty. Examples: "the first", "revolutionary", "introducing."

---

## P

### Persuasion Levers
The 7 psychological triggers identified by Robert Cialdini: Authority, Social Proof, Commitment & Consistency, Liking, Reciprocity, Scarcity, and Unity.

### Plugin
A bundle of skills, agents, commands, and hooks that extends Claude Code. Defined by plugin.json.

### Plugin.json
The manifest file that tells Claude Code what's in a plugin. Specifies paths to skills, agents, commands, and hooks.

### PostToolUse
A hook event that fires after any tool completes. Matcher is a string pattern matching tool names (e.g., `"Write"`).

### Problem Aware
An awareness level where the audience knows they have a problem but doesn't know solutions exist. Approach: Sell the outcome/solution.

### Progressive Disclosure
Loading information only when needed. Skills load on-demand, and supporting files load only when referenced.

---

## R

### Reciprocity
One of Cialdini's 7 persuasion levers. People return favors. Give value before asking. Example: Free tools, open source core.

---

## S

### SAFE
One of the four NESB dimensions. Appeals to the brain's fear of risk. Examples: "trusted by 50,000 developers", "SOC 2 certified", "money-back guarantee."

### Scarcity
One of Cialdini's 7 persuasion levers. People want what's rare or limited. Example: "Early access for first 100 users."

### Schwartz, Eugene
Author of "Breakthrough Advertising." Created the Problem Awareness Spectrum and Market Sophistication stages.

### Skill
Reusable knowledge that Claude can reference. Defined in SKILL.md files within the skills/ folder. Contains frameworks, scoring criteria, examples.

### SKILL.md
The main file defining a skill. Contains frontmatter and the skill's content.

### Social Proof
One of Cialdini's 7 persuasion levers. People follow the crowd. Example: "Join 50,000 developers."

### Solution Aware
An awareness level where the audience knows solutions exist but doesn't know your specific solution. Approach: Sell your unique mechanism.

### Subagent
See Agent. A specialized worker that Claude delegates tasks to.

### Supporting File
Additional files in a skill folder that provide detailed reference material. Loaded on-demand for progressive disclosure.

### systemMessage
A JSON field used in hook command output to display visible notifications. When a hook outputs `{"systemMessage": "text"}`, Claude Code displays it as "says: text" instead of showing error labels. Required for user-facing hook notifications.

---

## T

### Tribe Building
From Blair Warren's "One Sentence Persuasion Course." Creating a movement and sense of belonging. Five elements: encourage dreams, justify failures, allay fears, confirm suspicions, throw rocks at enemies.

---

## U

### Unaware
An awareness level where the audience doesn't even know they have a problem. Approach: Lead with symptoms, not solutions.

### Unity
One of Cialdini's 7 persuasion levers. People identify with and trust their tribe. Example: "For indie hackers who refuse to play corporate games."

### UserPromptSubmit
A hook event that fires when the user sends a message. **Note**: Check Claude Code documentation for current hook types; standard types are PostToolUse, PreToolUse, Notification, and Stop.

---

## V

### Voice Profile
The result of voice extraction. Captures tone, vocabulary, sentence structure, and personality traits from existing content.

### Voice Extractor
A skill that analyzes existing content to identify voice patterns for consistent content generation.

---

## W

### Warren, Blair
Author of "One Sentence Persuasion Course." Identified 5 elements for building cult-like following.

---

## Quick Reference by Category

### Frameworks
- NESB (NEW, EASY, SAFE, BIG)
- Problem Awareness Spectrum
- 7 Persuasion Levers
- Tactical Persuasion Techniques
- Tribe Building

### Plugin Components
- Skill
- Agent
- Command
- Hook
- Plugin.json
- CLAUDE.md

### Awareness Levels
1. Unaware
2. Problem Aware
3. Solution Aware
4. Product Aware
5. Most Aware

### Persuasion Levers
1. Authority
2. Social Proof
3. Commitment & Consistency
4. Liking
5. Reciprocity
6. Scarcity
7. Unity

### NESB Dimensions
1. NEW (novelty)
2. EASY (effort)
3. SAFE (risk)
4. BIG (transformation)

---

*Missing a term? Let us know by opening an issue.*
