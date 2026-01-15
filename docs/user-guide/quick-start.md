# Quick Start Guide

Welcome! This guide will get you using AI Marketer in 5 minutes, with 10 hands-on examples you can try right away.

## Before You Begin

### What You Need

1. **Claude Code** installed on your computer
2. **This project** downloaded/cloned to your computer
3. **A terminal/command prompt** open

### Using the Plugin

The AI Marketer plugin is included in this project. To use it:

```bash
# Step 1: Open your terminal (Command Prompt on Windows, Terminal on Mac/Linux)

# Step 2: Navigate to this project folder
cd /path/to/ai-marketing

# Step 3: Start Claude Code
claude
```

**What to expect**: Claude reads the CLAUDE.md file which contains all framework instructions.

### Two Ways to Invoke Commands

| Method | Example | How It Works |
|--------|---------|--------------|
| **Natural Language** | `score "headline"` | Claude uses CLAUDE.md instructions directly |
| **Slash Command** | `/ai-marketer:score "headline"` | Claude loads `commands/score.md` from the plugin |

**Both methods produce identical results.** This is because CLAUDE.md (which contains the full scoring framework) is always loaded when Claude enters the project directory.

- **Natural language** is recommended for quick use
- **Slash commands** are formal plugin commands (useful for automation or explicit invocation)

**Verify it works** by typing: `score "test headline"`

---

## 20 Things You Can Do Right Now

### Basic Commands (Use Cases 1-10)

### Use Case 1: Score a Headline (30 seconds)

**The Problem**: You've written a headline but don't know if it's good.

**The Solution**: Use the `score` command to get instant feedback.

```
score AI-powered code completion tool
```

**What You'll See**:
```
NESB Score: 14/40 (Weak)

| Dim  | Score | Issue                        |
|------|-------|------------------------------|
| NEW  | 3/10  | Generic - everyone says this |
| EASY | 4/10  | No ease claim                |
| SAFE | 3/10  | No trust signals             |
| BIG  | 4/10  | Small improvement claimed    |

Try instead:
"The first AI that reads your entire codebase -
ship 10x faster with zero setup."
Score: 32/40
```

**What You Learned**: Headlines should hit 4 emotional triggers: NEW (novel), EASY (low effort), SAFE (trustworthy), BIG (transformational).

**Framework Used**: 📘 *Take Their Money* (Milligan) — NESB scoring for the 4 emotional triggers

---

### Use Case 2: Improve a Weak Headline (1 minute)

**The Problem**: Your headline scored low. How do you fix it?

**The Solution**: Ask Claude to improve it using the frameworks.

```
My headline scored 14/40: "AI-powered code completion tool"

Can you give me 5 alternatives that score higher?
```

**What You'll See**: 5 alternatives with scores, like:
1. "Stop debugging. Start shipping." (28/40)
2. "The coding AI that actually understands your codebase." (30/40)
3. "10x faster coding. Zero learning curve. Trusted by 50,000 devs." (35/40)

**What You Learned**: Good headlines combine novelty, ease, trust, and big outcomes.

**Framework Used**: 📘 *Take Their Money* (Milligan) — improving headlines by optimizing each NESB dimension

---

### Use Case 3: Audit Your GitHub README (2 minutes)

**The Problem**: Your project has a README, but you're not sure if it's compelling.

**The Solution**: Use the `audit` command to analyze it.

```
audit https://github.com/yourusername/your-project
```

**What You'll See**: A comprehensive report:
```
Marketing Audit Report

Overall Score: 45/100

NESB Analysis: 18/40
- Missing: Easy setup claims
- Missing: Social proof (user numbers, testimonials)

Persuasion Levers: 3/7 present
- ✅ Authority (technical credentials)
- ✅ Liking (friendly tone)
- ✅ Reciprocity (free to use)
- ❌ Social Proof (no user numbers)
- ❌ Scarcity (N/A for open source)
- ❌ Unity (no community aspect)
- ❌ Commitment (no progressive engagement)

Top 3 Improvements:
1. Add user/download numbers to hero section
2. Include a testimonial quote
3. Add "Get started in 30 seconds" quick-start
```

**What You Learned**: READMEs need more than features - they need proof and emotional triggers.

**Frameworks Used**: 📘 *Take Their Money* (Milligan) — NESB scoring | 📘 *Influence* (Cialdini) — 7 Persuasion Levers audit

---

### Use Case 4: Compare Two Headlines (1 minute)

**The Problem**: You have two headline options and can't decide which is better.

**The Solution**: Score both and compare.

```
score "Build apps faster with AI"
```

Then:

```
score "Stop losing weekends to debugging. Ship in hours, not days."
```

**What You'll See**: Scores for each, making the winner clear.

**What You Learned**: Loss aversion ("stop losing") often beats gain framing ("build faster").

**Frameworks Used**: 📘 *Take Their Money* (Milligan) — NESB scoring | 📘 *Yes! 50 Ways* (Cialdini et al.) — loss aversion principle

---

### Use Case 5: Generate a README (3 minutes)

**The Problem**: You need a new README for your project.

**The Solution**: Use the `readme` command to generate one.

```
readme
```

Claude will ask you:
1. What does your project do?
2. Who is it for?
3. What makes it different?
4. Do you have any social proof (users, stars, testimonials)?

**What You'll Get**: A complete, framework-optimized README with:
- NESB-optimized hero section
- Benefits (not just features)
- Social proof section
- Quick-start guide
- Comparison to alternatives

**What You Learned**: Good READMEs lead with benefits, include proof, and make getting started easy.

**Frameworks Used**: 📘 *Take Their Money* (Milligan) — NESB-optimized hero | 📘 *Influence* (Cialdini) — social proof sections | 📘 *Breakthrough Advertising* (Schwartz) — awareness-matched messaging

---

### Use Case 6: Analyze a Competitor (2 minutes)

**The Problem**: You want to know how your competitors position themselves.

**The Solution**: Use the `compete` command to analyze their website.

```
compete https://competitor-product.com
```

**What You'll See**:
```
Competitor Analysis: [Product Name]

Positioning: "The fastest way to [outcome]"
Target Audience: [Who they're targeting]
NESB Score: 28/40

Strengths:
- Strong social proof (10,000+ users)
- Clear ease messaging

Weaknesses:
- Generic "AI-powered" claims
- No community/movement aspect

Your Opportunity:
- Position as the "[specific niche] alternative"
- Emphasize [feature they lack]
```

**What You Learned**: Competitive analysis reveals gaps you can exploit.

**Frameworks Used**: 📘 *Take Their Money* (Milligan) — NESB scoring | 📘 *Breakthrough Advertising* (Schwartz) — market sophistication analysis | 📘 *Influence* (Cialdini) — identifying missing persuasion levers

---

### Use Case 7: Extract Your Writing Voice (2 minutes)

**The Problem**: You want generated content to sound like YOU, not generic AI.

**The Solution**: Use the `voice` command to analyze your existing content.

```
voice https://github.com/yourusername
```

Or paste some of your writing:

```
voice

Here's some of my existing writing:
"I built this because I was tired of [problem].
Most tools overcomplicate things. This one doesn't."
```

**What You'll See**: A voice profile:
```
Voice Profile

Voice in 3 words: Direct, Practical, Relatable

Tone:
- Formality: 2/5 (casual)
- Technical: 3/5 (moderate)
- Humor: 2/5 (dry)
- Directness: 5/5 (very direct)

Signature patterns:
- Short, punchy sentences
- "I built this because..." openings
- Problem-first framing

When generating for this voice:
1. Keep sentences under 15 words
2. Use "you" and "I" frequently
3. Avoid corporate jargon
```

**What You Learned**: Consistent voice makes your content feel authentic.

**Framework Used**: 🔧 *Supporting Capability* — Voice extraction is not derived from the 5 marketing books. It's a meta-skill that ensures framework-optimized content still sounds like you, not generic AI.

---

### Use Case 8: Write a Tweet Thread (2 minutes)

**The Problem**: You want to announce your project on Twitter/X.

**The Solution**: Ask Claude to generate a thread using the frameworks.

```
Generate a 5-tweet thread announcing my project [describe project].
Use the marketing frameworks to make it compelling.
```

**What You'll Get**: A thread like:

```
Tweet 1 (Hook):
I spent 6 months building in silence.
Today, I'm sharing [Product].
It does one thing: [outcome].
Here's what I learned 🧵

Tweet 2 (Problem):
Most [category] tools fail because [problem].
They assume [wrong assumption].
That's why 90% of [people] give up.

Tweet 3 (Solution):
[Product] works differently.
Instead of [old way], we [new way].
The result? [outcome with number].

Tweet 4 (Proof):
Don't take my word for it:
"[Testimonial]" - @user
[X] people are already using it.

Tweet 5 (CTA):
Try it free: [link]
Star on GitHub: [link]
What would you build with this?
```

**What You Learned**: Good threads hook with a story, agitate the problem, and end with proof + CTA.

**Frameworks Used**: 📘 *Influence* (Cialdini) — social proof in testimonials | 📘 *Yes! 50 Ways* (Cialdini et al.) — storytelling hook | 📘 *One Sentence Persuasion* (Warren) — tribe-building through shared struggle

---

### Use Case 9: Rewrite with Loss Aversion (1 minute)

**The Problem**: Your copy focuses on gains, but research shows losses are 2x more motivating.

**The Solution**: Ask Claude to flip to loss framing.

```
Rewrite this using loss aversion:
"Increase your productivity by 50%"
```

**What You'll Get**:
```
Original (Gain frame):
"Increase your productivity by 50%"

Loss aversion rewrite:
"Stop losing 4 hours every day to [problem]"

Why it's stronger:
- Specific time loss (4 hours) vs vague gain (50%)
- "Stop losing" triggers fear of loss
- People work harder to avoid losses than achieve gains
```

**What You Learned**: "Stop losing X" beats "Gain X" almost every time.

**Framework Used**: 📘 *Yes! 50 Ways to Be Persuasive* (Cialdini et al.) — loss aversion is one of the 50 evidence-based persuasion tactics

---

### Use Case 10: Create a Tagline (1 minute)

**The Problem**: You need a memorable tagline for your project.

**The Solution**: Ask Claude to generate options using NESB.

```
Create 5 taglines for [describe your project].
Each should score at least 25/40 on NESB.
```

**What You'll Get**:
```
1. "Ship faster. Break nothing." (28/40)
   - EASY + SAFE focus

2. "The last [tool] you'll ever need." (26/40)
   - BIG promise

3. "[Outcome] without the [pain]." (30/40)
   - EASY + NEW contrast

4. "Built for developers who hate [problem]." (27/40)
   - Unity + LIKING

5. "[Number] teams. Zero [problem]." (32/40)
   - SAFE (proof) + BIG (outcome)
```

**What You Learned**: Good taglines combine proof, ease, and big outcomes in few words.

**Frameworks Used**: 📘 *Take Their Money* (Milligan) — NESB scoring (25/40 minimum target) | 📘 *Influence* (Cialdini) — Unity and Liking levers in tribal messaging

---

### Advanced Capabilities (Use Cases 11-20)

### Use Case 11: Deep Market Research (Agent)

**The Problem**: You need comprehensive competitive intelligence across multiple competitors, not just one.

**The Solution**: Trigger the `market-researcher` agent for deep multi-site analysis.

```
Research the AI coding assistant market. Analyze the top 5 competitors
including Cursor, GitHub Copilot, Tabnine, Codeium, and Amazon CodeWhisperer.
Give me positioning gaps and opportunities.
```

**What Happens**: The `market-researcher` agent is spawned with browser automation capabilities. It:
1. Visits each competitor's website
2. Extracts positioning, pricing, and feature data
3. Identifies patterns and gaps
4. Returns a structured research report

**What You'll See**:
```
## Market Research Report

### Sources Analyzed
1. cursor.com
2. github.com/features/copilot
3. tabnine.com
4. codeium.com
5. aws.amazon.com/codewhisperer

### Competitive Landscape
| Competitor | Positioning | Strength | Weakness |
|------------|-------------|----------|----------|
| Cursor | "The AI Code Editor" | Full IDE experience | Requires switching editors |
| Copilot | "Your AI pair programmer" | GitHub integration | Privacy concerns |
...

### Opportunities Identified
1. No one owns the "enterprise security" position strongly
2. Gap in terminal-native experience
3. Underserved: agencies/consultancies
```

**What You Learned**: Agents can do autonomous research that would take you hours.

**Agent Used**: 🤖 `market-researcher` — Browser automation for multi-site competitive analysis

---

### Use Case 12: Batch Content Generation (Agent)

**The Problem**: You need multiple content pieces (README, tweets, LinkedIn post) and want consistent voice across all.

**The Solution**: Trigger the `copy-writer` agent for batch generation.

```
Generate a complete launch content kit for my project [describe project]:
1. GitHub README hero section
2. 5-tweet announcement thread
3. LinkedIn launch post
4. Product Hunt tagline

Use my voice profile and score each piece against the frameworks.
```

**What Happens**: The `copy-writer` agent is spawned. It:
1. Checks for existing voice profile
2. Generates each content piece applying all 5 frameworks
3. Scores each piece and provides variations
4. Maintains consistent voice across all outputs

**What You'll See**:
```
## Generated Content Kit

### Voice: Matched to extracted profile (Direct, Practical, Technical)

---

### 1. GitHub README Hero
> Stop losing hours to debugging. Ship 10x faster with AI that
> actually understands your codebase.

**NESB Score**: 32/40 | **Key levers**: Loss aversion, Social proof

---

### 2. Tweet Thread
**Tweet 1 (Hook):**
I spent 6 months building in silence.
Today I'm sharing [Product].
It does one thing: makes debugging obsolete.
🧵

[+ 4 more tweets]

**NESB Score**: 28/40 | **Key levers**: Story hook, Curiosity

---

### 3. LinkedIn Post
[Full post with formatting]

**NESB Score**: 30/40 | **Key levers**: Professional proof, Authority

---

### 4. Product Hunt Tagline
"Debug in seconds, not hours. AI that reads your whole codebase."

**NESB Score**: 31/40
```

**What You Learned**: Agents maintain context and consistency across multiple outputs.

**Agent Used**: 🤖 `copy-writer` — Batch content generation with framework scoring

---

### Use Case 13: Content Quality Review (Agent)

**The Problem**: You've written marketing content and want it scored against all 5 frameworks before publishing.

**The Solution**: Trigger the `content-reviewer` agent for comprehensive review.

```
Review this README hero section against all 5 marketing frameworks:

"Acme AI helps developers write better code using machine learning
algorithms trained on millions of repositories."
```

**What Happens**: The `content-reviewer` agent analyzes the content against all frameworks and provides specific improvement recommendations.

**What You'll See**:
```
## Content Review Report

### Content Reviewed
> "Acme AI helps developers write better code using machine learning..."

### Framework Scores

#### NESB Analysis
| Dimension | Score | Evidence | Issue |
|-----------|-------|----------|-------|
| NEW | 3/10 | "machine learning" | Generic, everyone claims this |
| EASY | 2/10 | None | No ease signals at all |
| SAFE | 2/10 | "millions of repos" | Weak proof, not specific |
| BIG | 4/10 | "better code" | Vague outcome |
| **Total** | 11/40 | | |

#### Persuasion Levers: 8/70
- Authority: 2/10 (claims expertise, no proof)
- Social Proof: 0/10 (no users mentioned)
...

#### Awareness Match: 4/10
Copy assumes Solution Aware but uses Unaware-level language.

### Overall Score: 38% (REWRITE)

### Quick Fixes
- Add specific user number: "Trusted by 10,000 developers"
- Add ease signal: "zero configuration"

### Strategic Improvements
- Define unique mechanism (what makes your ML different?)
- Add loss aversion: "Stop losing hours to..."

### Verdict
[ ] APPROVED
[ ] REVISE
[x] REWRITE - Needs significant work
```

**What You Learned**: Agents provide systematic quality gates before publishing.

**Agent Used**: 🤖 `content-reviewer` — Comprehensive framework scoring with verdicts

---

### Use Case 14: Diagnose Audience Awareness (Skill)

**The Problem**: Your marketing isn't converting. You might be speaking to the wrong awareness level.

**The Solution**: Use the `awareness-analyzer` skill to diagnose your audience.

```
Analyze the awareness level for my product:

Product: An AI tool that automatically fixes bugs in Python code
Audience: Senior Python developers at startups
Market: Growing, with competitors like Sourcery, Snyk, CodeClimate
```

**What You'll See**:
```
## Awareness Diagnosis

### Audience: Senior Python developers at startups
### Product: AI bug-fixing tool

### Problem Awareness Level: Solution Aware
**Evidence**: Audience knows AI code tools exist (Copilot, etc.),
             has tried linters and static analysis
**Implication**: Can't just say "AI fixes bugs" - need unique mechanism

### Market Sophistication Stage: Stage 3 (Crowded)
**Evidence**: Multiple competitors, similar claims ("AI-powered analysis")
**Implication**: Must differentiate with HOW, not just WHAT

### Recommended Messaging Strategy
Don't lead with "AI" - they've heard it. Lead with mechanism:
"The only tool that understands your code's intent, not just syntax"

### Sample Headlines by Awareness Level

**For Solution Aware (your audience):**
- "Unlike linters, we fix the bug, not just flag it"
- "Context-aware fixes, not pattern matching"

### Red Flags to Avoid
❌ Don't say "AI-powered" - table stakes, not differentiator
❌ Don't compare to general AI tools - compare to their current workflow
❌ Don't assume they don't know alternatives exist
```

**What You Learned**: Match your copy to where your audience actually is, not where you wish they were.

**Skill Used**: 🎯 `awareness-analyzer` — Audience diagnosis based on Schwartz's Breakthrough Advertising

---

### Use Case 15: Build Tribe-Level Copy (Skill)

**The Problem**: Your product works, but users aren't emotionally attached. No community. No movement.

**The Solution**: Use the `tribe-builder` skill to create movement-building copy.

```
Build tribe copy for my product:

Product: No-code AI builder for small businesses
Audience: Small business owners who can't afford developers
Enemy: Big tech gatekeeping, expensive agencies, complex tools
```

**What You'll See**:
```
## Tribe Building Copy

### Audience Profile
- **Who they are**: Small business owners, 1-10 employees
- **What they want**: Compete with bigger companies using AI

### The 5 Elements

#### 1. Encourage Dreams
> "You CAN use the same AI that Fortune 500 companies use.
> No developers required. No six-figure budget needed."

#### 2. Justify Failures
> "It's not your fault AI seemed out of reach. The tools were
> built for engineers, not business owners. That ends today."

#### 3. Allay Fears
> "You won't break anything. You won't get locked in.
> Everything you build is yours to keep, forever."

#### 4. Confirm Suspicions
> "You were right - those agencies charging $50k for a chatbot
> were ripping you off. This takes 10 minutes, not 10 weeks."

#### 5. Throw Rocks at Enemies
> "Big tech wants AI to stay complicated. They profit from your
> confusion. We're making AI as simple as sending an email."

### Combined Message
> "The tech giants want you to believe AI is only for companies
> with engineering teams. That's a lie. They profit from complexity.
> We built [Product] for the rest of us - business owners who just
> want tools that work. No code. No consultants. No gatekeepers.
> Join the small businesses taking AI back."

### Movement Language
- **Tagline**: "AI for the rest of us"
- **Call to action**: "Join 5,000 small businesses who fired their agencies"
```

**What You Learned**: Products compete on features. Movements compete on identity.

**Skill Used**: 🏴 `tribe-builder` — Blair Warren's One Sentence Persuasion framework

---

### Use Case 16: Generate a LinkedIn Post (Social)

**The Problem**: You need a professional LinkedIn post, not just Twitter content.

**The Solution**: Ask for LinkedIn-specific format using the content-generator templates.

```
Generate a LinkedIn post announcing that my SaaS just hit 1,000 users.
Product: AI writing assistant for developers
Use the LinkedIn format with proper spacing and hooks.
```

**What You'll See**:
```
## LinkedIn Post

I hit 1,000 users yesterday.

But not how you'd expect.

I didn't spend a dollar on ads.
I didn't have a viral launch.
I didn't even have a Product Hunt feature.

Here's what actually worked:

→ I wrote 50 posts about problems I faced as a developer
→ I replied to every single DM (still do)
→ I shipped a feature every week and shared the build process

The "growth hack" was having no growth hack.

Just solving a real problem for real people.

[Product] now helps 1,000 developers write better docs.

What's one thing that worked for you that "shouldn't" work?

---

#BuildInPublic #Developer #SaaS
```

**What You Learned**: LinkedIn needs different formatting - more whitespace, story-driven hooks, professional CTA.

**Template Used**: 📝 `content-generator/social-posts.md` — LinkedIn post structure and hook formulas

---

### Use Case 17: Watch Hooks in Action (Automation)

**The Problem**: You want automatic quality reminders when you write marketing content.

**The Solution**: The plugin has hooks that trigger automatically.

**Demo 1: PostToolUse Hook (README)**

When you ask Claude to write a README:
```
Write a README.md for my project in the current folder
```

After the file is written, you'll see:
```
[AI-Marketer] README written - consider running audit
(or /ai-marketer:audit) for quality check
```

**Demo 2: UserPromptSubmit Hook**

When you mention marketing topics:
```
I need help with my landing page copy
```

Before Claude responds, you'll see:
```
[AI-Marketer] Marketing content detected. Available commands:
audit, score, readme, compete, voice (or /ai-marketer:*)
```

**What You Learned**: Hooks provide automatic reminders and quality gates.

**Hooks Used**:
- ⚡ `PostToolUse` — Triggers after file writes
- ⚡ `UserPromptSubmit` — Triggers when marketing keywords detected

---

### Use Case 18: Deep Persuasion Audit (Skill)

**The Problem**: You want a detailed breakdown of all 7 Cialdini persuasion levers, not just a summary.

**The Solution**: Request a standalone persuasion audit.

```
Run a full persuasion audit on this landing page copy:

"Acme AI - The Smart Way to Code
Join 50,000 developers using Acme.
As featured in TechCrunch.
Start free, upgrade anytime.
Limited beta spots available."
```

**What You'll See**:
```
## Persuasion Lever Analysis

| Lever | Score | Evidence | Improvement |
|-------|-------|----------|-------------|
| Authority | 8/10 | "TechCrunch" | Add more logos |
| Social Proof | 7/10 | "50,000 developers" | Add testimonial |
| Commitment | 3/10 | "Start free" weak | Add progressive steps |
| Liking | 4/10 | Neutral tone | Add personality/story |
| Reciprocity | 2/10 | No free value shown | Add free tool/resource |
| Scarcity | 6/10 | "Limited beta" | Add countdown/number |
| Unity | 1/10 | No tribe identity | Add "for [tribe]" |

**Total: 31/70**

### Priority Fixes
1. **Add Unity (+5)**: Change to "Built for indie hackers who..."
2. **Add Reciprocity (+4)**: Offer free audit tool before signup
3. **Strengthen Commitment (+3)**: "Start with a 5-min tutorial"

### Rewritten with All Levers
> "Acme AI - Built for developers who hate writing boilerplate
>
> Join 50,000 developers who shipped 3x faster.
> 'Best tool I've found in 10 years' - @seniordev, TechCrunch featured
>
> Start with our free code analyzer (no signup).
> Then unlock full power - limited to 100 new users this week."
```

**What You Learned**: Each lever has specific tactics to maximize it.

**Skill Used**: 🔍 `persuasion-auditor` — Deep Cialdini analysis with tactical fixes

---

### Use Case 19: Full Workflow - Research to Content (Multi-Agent)

**The Problem**: You're launching a new product and need the complete flow: research → strategy → content → review.

**The Solution**: Use the full agent workflow.

```
I'm launching an AI scheduling tool for solopreneurs.

1. First, research the market (Calendly, Cal.com, SavvyCal)
2. Then diagnose the awareness level
3. Generate a README and launch tweet thread
4. Review all content before I publish
```

**What Happens**:

1. **market-researcher agent** → Gathers competitive intelligence
2. **awareness-analyzer skill** → Diagnoses where audience sits
3. **copy-writer agent** → Generates content with framework alignment
4. **content-reviewer agent** → Scores and approves/revises

**What You'll Get**: A complete launch kit with:
- Competitive gap analysis
- Awareness-matched messaging strategy
- Framework-optimized README (scored)
- Tweet thread (scored)
- Review verdict with fixes

**What You Learned**: Agents can be chained for end-to-end workflows.

**Agents/Skills Used**:
- 🤖 `market-researcher` → 🎯 `awareness-analyzer` → 🤖 `copy-writer` → 🤖 `content-reviewer`

---

### Use Case 20: Landing Page Copy (Content Generator)

**The Problem**: You need high-converting landing page copy, not just a README.

**The Solution**: Request landing page format with conversion focus.

```
Generate landing page copy for my product:
- Product: AI that reads legal documents and explains them in plain English
- Audience: Small business owners signing contracts
- Price: $29/month
- Social proof: 500 users, 4.9 stars
```

**What You'll See**:
```
## Landing Page Copy

### Hero Section
**Headline**: Stop signing contracts you don't understand.
**Subhead**: Upload any legal document. Get plain-English explanation in 60 seconds.
**CTA**: Try Free → See it work on your own document

NESB: 33/40

---

### Problem Section
> "Every year, small businesses lose $11 billion to contract disputes.
> Most of those losses? Hidden in clauses nobody explained."

Lever: Loss aversion ✓

---

### Solution Section
> "LegalLens reads your contracts like a lawyer would.
> Then explains them like a friend would."
>
> ✅ Upload any document (PDF, Word, images)
> ✅ Get plain-English summary in 60 seconds
> ✅ Flag risky clauses before you sign

Lever: Easy mechanism ✓

---

### Social Proof Section
> "Finally understand what I'm signing. Saved me from a terrible
> office lease." - Maria R., Restaurant Owner
>
> ⭐ 4.9 stars from 500 small business owners

Lever: Social proof + Specific identity ✓

---

### Pricing Section
> **$29/month** · Unlimited documents · Cancel anytime
>
> Less than one hour of lawyer time.
> Use it on every contract forever.

Lever: Contrast effect (vs lawyer cost) ✓

---

### Final CTA
> "Don't sign another contract confused.
> Upload your first document free - no credit card."

Lever: Reciprocity + Risk reversal ✓
```

**What You Learned**: Landing pages need different structure than READMEs - hero → problem → solution → proof → price → CTA.

**Skills Used**: 📝 `content-generator` + 🔍 `persuasion-auditor` + 🎯 `nesb-scorer`

---

## What's Next?

Now that you've tried these quick wins:

1. **See real examples**: Check the [Test Results](../test-results.md) for detailed outputs with mock data
2. **Go deeper**: Read the [Complete User Guide](./complete-guide.md)
3. **Understand the frameworks**: See [Frameworks Explained](./frameworks-explained.md)
4. **Learn all commands**: Check the [Command Reference](./command-reference.md)

## Quick Reference Card

### Commands (5)

| Command | What It Does | Example |
|---------|--------------|---------|
| `score` | Score a headline (NESB 0-40) | `score "Your headline"` |
| `audit` | Full marketing audit | `audit https://github.com/user/repo` |
| `readme` | Generate README | `readme` |
| `compete` | Analyze competitor | `compete https://competitor.com` |
| `voice` | Extract voice profile | `voice https://github.com/user` |

### Agents (3)

| Agent | What It Does | Trigger Example |
|-------|--------------|-----------------|
| `market-researcher` | Deep multi-site competitive research | "Research the top 5 competitors in [market]" |
| `copy-writer` | Batch content generation with scoring | "Generate a launch kit with README, tweets, LinkedIn" |
| `content-reviewer` | Review content against all frameworks | "Review this copy against all 5 frameworks" |

### Skills (8)

| Skill | What It Does | Trigger Example |
|-------|--------------|-----------------|
| `awareness-analyzer` | Diagnose audience awareness level | "Analyze the awareness level for my product" |
| `persuasion-auditor` | Score all 7 Cialdini levers | "Run a full persuasion audit on this copy" |
| `nesb-scorer` | Score NEW-EASY-SAFE-BIG | (used by `score` command) |
| `tribe-builder` | Create movement-building copy | "Build tribe copy for my product" |
| `copy-optimizer` | Apply tactical techniques | "Rewrite this using loss aversion" |
| `voice-extractor` | Extract writing style | (used by `voice` command) |
| `competitor-analyzer` | Analyze competitor positioning | (used by `compete` command) |
| `content-generator` | Generate optimized content | "Generate landing page copy" |

### Hooks (2)

| Hook | When It Fires | What It Does |
|------|---------------|--------------|
| `PostToolUse` | After writing README.md or landing pages | Suggests running audit/score |
| `UserPromptSubmit` | When you mention marketing keywords | Reminds about available commands |

### Slash Commands (Plugin Registered)

| Slash Command | Example |
|---------------|---------|
| `/ai-marketer:score` | `/ai-marketer:score "Your headline"` |
| `/ai-marketer:audit` | `/ai-marketer:audit https://github.com/user/repo` |
| `/ai-marketer:readme` | `/ai-marketer:readme` |
| `/ai-marketer:compete` | `/ai-marketer:compete https://competitor.com` |
| `/ai-marketer:voice` | `/ai-marketer:voice https://github.com/user` |

## Tips for Success

1. **Start with scoring** - It's the fastest way to learn what works
2. **Always check NESB** - If you're not hitting all 4, you're leaving impact on the table
3. **Use loss aversion** - "Stop losing" beats "Start gaining"
4. **Add social proof** - Numbers and testimonials build trust
5. **Match your voice** - Consistent voice feels authentic

---

**Congratulations!** You've completed the Quick Start Guide. You now know more about marketing psychology than most developers ever learn.

---

## Acknowledgements

This guide and the AI Marketer plugin were inspired by the YouTube video ["These 5 Books Reveal Why Most AI Products Don't Sell"](https://www.youtube.com/watch?v=OLjTWl4Ci10). All code and documentation were generated by [Claude Code](https://claude.ai/code) powered by Claude Opus 4.5.

---

*Next: [Complete User Guide](./complete-guide.md)*
