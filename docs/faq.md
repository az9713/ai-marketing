# Frequently Asked Questions

Find answers to common questions about AI Marketer.

---

## General Questions

### What is AI Marketer?

AI Marketer is a Claude Code plugin that helps you write better marketing copy for your software products. It implements 5 proven marketing psychology frameworks from bestselling books and makes them accessible through simple commands.

### Do I need to read the marketing books first?

No. The plugin encodes the key concepts and makes them usable without reading the books. However, if you want deeper understanding, the books are:
1. "Breakthrough Advertising" by Eugene Schwartz
2. "Influence" by Robert Cialdini
3. "Yes! 50 Scientifically Proven Ways to Be Persuasive" by Cialdini et al.
4. "Take Their Money" by Kyle Milligan
5. "One Sentence Persuasion Course" by Blair Warren

### Is this just for GitHub READMEs?

No. While READMEs are a great starting point, AI Marketer works for:
- Landing pages
- Social media posts (Twitter/X, LinkedIn)
- Email marketing
- Blog posts
- YouTube scripts
- Product Hunt launches
- Any marketing copy

### Is this manipulation?

No. The frameworks help you communicate your value more effectively. They work best when you have a genuinely good product. They don't make bad products good—they make good products sound as good as they are.

---

## Getting Started

### How do I install the plugin?

1. Clone or download the project
2. Navigate to the project folder in your terminal
3. Start Claude Code: `claude`
4. The plugin loads automatically

### How do I know if the plugin is loaded?

Ask Claude: "What marketing commands are available?"

Claude should mention `/score`, `/audit`, `/readme`, `/compete`, and `/voice`.

### Do I need an internet connection?

Yes, for:
- `/audit` when analyzing URLs
- `/compete` when analyzing competitor sites
- Any web-based voice extraction

No, for:
- `/score` with text input
- Content generation from pasted text
- Voice extraction from pasted samples

---

## Using Commands

### What's the difference between /score and /audit?

| Command | Purpose | Speed | Depth |
|---------|---------|-------|-------|
| `/score` | Quick headline scoring | Fast | NESB only |
| `/audit` | Comprehensive analysis | Slower | All frameworks |

Use `/score` for quick iterations. Use `/audit` for thorough review.

### Can I score multiple headlines at once?

Yes. You can ask:
```
Score these headlines:
1. "First headline"
2. "Second headline"
3. "Third headline"
```

Or run `/score` multiple times.

### What score should I aim for?

For NESB (0-40 scale):
- **28+**: Strong, ready to use
- **21-27**: Average, could improve
- **Below 20**: Weak, needs work

For full audit (0-100 scale):
- **70+**: Good
- **50-69**: Needs improvement
- **Below 50**: Major revision needed

### Can I customize the scoring?

You can ask for specific focus:
```
Score this headline but weight SAFE higher because my audience
is risk-averse enterprise buyers
```

---

## Framework Questions

### What is NESB?

NESB stands for four emotional triggers that effective marketing should hit:
- **N**EW: Appeals to novelty-seeking
- **E**ASY: Appeals to effort-minimizing
- **S**AFE: Appeals to risk-avoidance
- **B**IG: Appeals to status/transformation

### What are the 7 persuasion levers?

From Robert Cialdini's research:
1. **Authority**: Expert credibility
2. **Social Proof**: Others doing it
3. **Commitment**: Small yeses lead to big yeses
4. **Liking**: People buy from those they like
5. **Reciprocity**: Give before you ask
6. **Scarcity**: Limited availability
7. **Unity**: Tribal belonging

### How do I know which awareness level to target?

Ask yourself:
- Does my audience know they have a problem? (If no → Unaware)
- Do they know solutions exist? (If no → Problem Aware)
- Do they know MY solution? (If no → Solution Aware)
- Have they considered buying from me? (If no → Product Aware)
- Are they ready to buy? (If yes → Most Aware)

### What's "throwing rocks at enemies" mean?

From Blair Warren's tribe-building framework. It means uniting your audience against a common enemy (not a person, but a system or approach):
- "Tired of bloated enterprise software?"
- "Done with tools designed by committees?"

This creates unity and loyalty.

---

## Quality & Output

### Why does my output sound generic?

Common causes:
1. **No voice extraction**: Run `/voice` first with samples of your writing
2. **Vague input**: Provide more context about your product and audience
3. **No examples**: Share examples of copy you like

### The AI suggestions don't fit my brand. What do I do?

1. Extract your voice profile first:
   ```
   /voice [paste 500+ words of your writing]
   ```

2. Reference your voice in requests:
   ```
   Generate headline alternatives that match this voice: [voice traits]
   ```

3. Provide brand guidelines:
   ```
   My brand is professional but friendly, avoids buzzwords,
   and uses short sentences.
   ```

### How do I get more creative suggestions?

Ask for more options:
```
Give me 10 headline alternatives, including some bold/unconventional ones
```

Or specify constraints:
```
Give me headlines that use humor
Give me headlines that start with a question
Give me headlines using loss aversion
```

### Are scores always accurate?

Scores are guidance, not absolute truth. They:
- Identify areas for improvement
- Compare relative strength of options
- Highlight missing elements

They don't:
- Guarantee conversion rates
- Account for your specific audience's preferences
- Replace actual A/B testing

---

## Technical Questions

### Can I add my own marketing frameworks?

Yes! See [Adding Features Guide](./developer-guide/adding-features.md). You can:
- Add new skills
- Create new commands
- Define new agents

### Can I use this with other Claude Code plugins?

Yes. Claude Code supports multiple plugins. AI Marketer won't conflict with other plugins.

### Does this work offline?

Partially:
- ✅ Scoring pasted text
- ✅ Generating content from descriptions
- ❌ Fetching URLs
- ❌ Analyzing live websites

### Can I export/save my results?

Claude Code can write files. Ask Claude to save output:
```
Save that README to README.md
```

Or copy from the terminal output.

### Does the plugin remember my voice profile?

Not automatically between sessions. For consistent voice:
1. Save your voice profile output to a file
2. Reference it in new sessions:
   ```
   Here's my voice profile: [paste profile]
   Generate content matching this voice
   ```

---

## Pricing & Access

### Is AI Marketer free?

AI Marketer itself is free and open source. However, you need:
- Claude Code (requires Claude account)
- A Claude account (has free tier with limits)

### Do I need Claude Pro?

The free Claude tier works, but:
- Has usage limits
- May be slower during high demand

Pro gives you priority access and higher limits.

---

## Comparison Questions

### How is this different from asking ChatGPT for marketing help?

AI Marketer:
- Implements specific, proven frameworks
- Provides structured scoring
- Uses consistent methodology
- Gives actionable, specific feedback

Generic ChatGPT:
- General knowledge
- Inconsistent approach
- No structured scoring
- Variable output quality

### How is this different from marketing agencies?

| Aspect | AI Marketer | Agency |
|--------|-------------|--------|
| Cost | Free (+ Claude account) | $$$$$ |
| Speed | Instant | Days/weeks |
| Availability | 24/7 | Business hours |
| Iteration | Unlimited | Revision limits |
| Understanding your product | You guide it | May need onboarding |

AI Marketer is great for:
- Quick iteration
- Testing ideas
- Learning frameworks
- Small teams/solo founders

Agencies are better for:
- Large campaigns
- Brand strategy
- Multi-channel coordination
- Hands-off execution

### Should I trust these frameworks?

The frameworks come from:
- Decades of marketing research
- Bestselling books with millions of copies sold
- Peer-reviewed psychology studies
- Real-world testing at scale

They're as evidence-based as marketing gets. But always:
- Test with your audience
- Measure actual results
- Iterate based on data

---

## Troubleshooting

### Plugin commands aren't working

See [Troubleshooting Guide](./troubleshooting.md). Quick fix: restart Claude Code from project directory.

### Scores seem wrong

Ask for detailed breakdown:
```
Score this and explain your reasoning for each NESB dimension
```

### Can't access a URL

- Check URL is public (no login required)
- Paste content directly instead:
  ```
  /audit

  Here's the content:
  [paste text]
  ```

---

## Contributing

### How can I contribute?

See [Contributing Guide](./developer-guide/contributing.md). Options:
- Report bugs
- Suggest features
- Add new frameworks/skills
- Improve documentation
- Share use cases

### I found a bug. Where do I report it?

Open an issue on GitHub with:
- What you tried to do
- What happened instead
- Steps to reproduce
- Your environment details

---

## Still Have Questions?

- Check the [Complete User Guide](./user-guide/complete-guide.md)
- Read the [Troubleshooting Guide](./troubleshooting.md)
- Search existing GitHub Issues
- Open a new issue if needed

---

*This FAQ is updated based on common user questions. Didn't find your answer? Open an issue!*
