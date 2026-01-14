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

**What to expect**: The plugin auto-loads because it's in the `.claude/plugins/` folder. Verify by asking Claude: "What marketing commands are available?"

---

## 10 Things You Can Do Right Now

### Use Case 1: Score a Headline (30 seconds)

**The Problem**: You've written a headline but don't know if it's good.

**The Solution**: Use `/score` to get instant feedback.

```
/score AI-powered code completion tool
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

---

### Use Case 3: Audit Your GitHub README (2 minutes)

**The Problem**: Your project has a README, but you're not sure if it's compelling.

**The Solution**: Use `/audit` to analyze it.

```
/audit https://github.com/yourusername/your-project
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

---

### Use Case 4: Compare Two Headlines (1 minute)

**The Problem**: You have two headline options and can't decide which is better.

**The Solution**: Score both and compare.

```
/score "Build apps faster with AI"
```

Then:

```
/score "Stop losing weekends to debugging. Ship in hours, not days."
```

**What You'll See**: Scores for each, making the winner clear.

**What You Learned**: Loss aversion ("stop losing") often beats gain framing ("build faster").

---

### Use Case 5: Generate a README (3 minutes)

**The Problem**: You need a new README for your project.

**The Solution**: Use `/readme` to generate one.

```
/readme
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

---

### Use Case 6: Analyze a Competitor (2 minutes)

**The Problem**: You want to know how your competitors position themselves.

**The Solution**: Use `/compete` to analyze their website.

```
/compete https://competitor-product.com
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

---

### Use Case 7: Extract Your Writing Voice (2 minutes)

**The Problem**: You want generated content to sound like YOU, not generic AI.

**The Solution**: Use `/voice` to analyze your existing content.

```
/voice https://github.com/yourusername
```

Or paste some of your writing:

```
/voice

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

---

## What's Next?

Now that you've tried these quick wins:

1. **Go deeper**: Read the [Complete User Guide](./complete-guide.md)
2. **Understand the frameworks**: See [Frameworks Explained](./frameworks-explained.md)
3. **Learn all commands**: Check the [Command Reference](./command-reference.md)

## Quick Reference Card

| Command | What It Does | Example |
|---------|--------------|---------|
| `/score` | Score a headline | `/score "Your headline"` |
| `/audit` | Full marketing audit | `/audit https://github.com/user/repo` |
| `/readme` | Generate README | `/readme` |
| `/compete` | Analyze competitor | `/compete https://competitor.com` |
| `/voice` | Extract voice | `/voice https://github.com/user` |

## Tips for Success

1. **Start with scoring** - It's the fastest way to learn what works
2. **Always check NESB** - If you're not hitting all 4, you're leaving impact on the table
3. **Use loss aversion** - "Stop losing" beats "Start gaining"
4. **Add social proof** - Numbers and testimonials build trust
5. **Match your voice** - Consistent voice feels authentic

---

**Congratulations!** You've completed the Quick Start Guide. You now know more about marketing psychology than most developers ever learn.

*Next: [Complete User Guide](./complete-guide.md)*
