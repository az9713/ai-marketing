# AI Marketer - Project Context

## What This Project Is

AI Marketer is a Claude Code plugin that helps developers write better marketing content for their projects. It implements 5 proven marketing psychology frameworks from bestselling books and makes them accessible through simple slash commands.

## Project Structure

```
books_selling_ai_kochel/
├── CLAUDE.md                          # This file - project context
├── docs/                              # Documentation
│   ├── gemini3_summary.txt            # Original framework summary
│   ├── README_transcript.txt          # Source video transcript
│   └── technical-design.md            # Technical design decisions
│
└── .claude/
    └── plugins/
        └── ai-marketer/               # The main plugin
            ├── plugin.json            # Plugin manifest
            ├── CLAUDE.md              # Plugin-specific context
            ├── README.md              # Plugin README
            │
            ├── skills/                # 8 marketing skills
            │   ├── awareness-analyzer/
            │   ├── persuasion-auditor/
            │   ├── copy-optimizer/
            │   ├── nesb-scorer/
            │   ├── tribe-builder/
            │   ├── voice-extractor/
            │   ├── competitor-analyzer/
            │   └── content-generator/
            │
            ├── agents/                # 3 subagents
            │   ├── market-researcher.md
            │   ├── copy-writer.md
            │   └── content-reviewer.md
            │
            ├── commands/              # 5 slash commands
            │   ├── audit.md
            │   ├── compete.md
            │   ├── readme.md
            │   ├── score.md
            │   └── voice.md
            │
            └── hooks/
                └── hooks.json         # Automation hooks
```

## The 5 Marketing Frameworks

This plugin implements these frameworks:

1. **Breakthrough Advertising** (Eugene Schwartz)
   - Problem Awareness Levels: Unaware → Problem Aware → Solution Aware → Product Aware → Most Aware
   - Market Sophistication Stages: 1 (simple claims) → 5 (identity-based)

2. **Influence** (Robert Cialdini)
   - 7 Persuasion Levers: Authority, Social Proof, Commitment, Liking, Reciprocity, Scarcity, Unity

3. **Yes! 50 Ways to Be Persuasive** (Cialdini et al)
   - Tactical techniques: Framing, Specific Social Proof, Loss Aversion, Similarity, Commitment Ladder

4. **Take Their Money** (Kyle Milligan)
   - NESB Framework: Every piece of copy should hit NEW, EASY, SAFE, BIG

5. **One Sentence Persuasion** (Blair Warren)
   - 5 elements: Encourage dreams, Justify failures, Allay fears, Confirm suspicions, Throw rocks at enemies

## Key Commands

- `/score "headline"` - Quick NESB scoring (0-40)
- `/audit URL` - Full marketing audit against all frameworks
- `/readme` - Generate optimized GitHub README
- `/compete URL` - Analyze competitor positioning
- `/voice URL` - Extract voice patterns from existing content

## Development Guidelines

### When Modifying Skills
- Each skill has a SKILL.md with frontmatter (name, description, allowed-tools)
- Supporting files provide reference material (loaded via progressive disclosure)
- Keep instructions actionable and specific

### When Modifying Agents
- Agents have model specification (sonnet/haiku)
- Define clear trigger conditions
- Specify allowed tools explicitly

### When Modifying Commands
- Commands are user-invoked via `/command-name`
- Keep command names short and memorable
- Provide clear usage examples

## Content Generation Principles

When generating marketing content:
1. Always determine audience awareness level first
2. Score headlines against NESB before presenting
3. Include at least 3 persuasion levers
4. Use loss aversion framing where possible
5. Match the user's voice if a profile exists

## Testing

To test the plugin:
1. Use `/score` on sample headlines
2. Run `/audit` on a real GitHub repo
3. Generate content with `/readme`
4. Verify framework scores meet quality thresholds (NESB > 25/40)

## Common Tasks

### Adding a New Skill
1. Create directory in `skills/`
2. Add SKILL.md with frontmatter
3. Add supporting files as needed
4. Reference in plugin documentation

### Adding a New Command
1. Create command.md in `commands/`
2. Define name and description in frontmatter
3. Document usage and examples
4. Test with various inputs

### Updating Framework Reference
1. Edit `.claude/plugins/ai-marketer/CLAUDE.md`
2. Update relevant skill files
3. Ensure consistency across all references
