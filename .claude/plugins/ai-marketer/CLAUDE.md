# AI Marketer Plugin

This plugin implements 5 proven marketing psychology frameworks for promoting AI products. Use these frameworks when analyzing, scoring, or generating marketing content.

## The 5 Frameworks

### Framework 1: Breakthrough Advertising (Eugene Schwartz)
**Core Concept**: Problem Awareness Spectrum + Market Sophistication

#### Problem Awareness Levels
Match your copy to where the audience sits on this spectrum:

| Level | Description | Copy Approach |
|-------|-------------|---------------|
| **Unaware** | Don't know they have a problem | Lead with the symptom, not the product |
| **Problem Aware** | Know the problem, not solutions | Sell the solution to the pain |
| **Solution Aware** | Know solutions exist, not yours | Sell your unique mechanism |
| **Product Aware** | Know your product, not convinced | Sell proof and differentiation |
| **Most Aware** | Ready to buy | Sell the offer/price |

#### Market Sophistication Stages
How exposed is the market to similar claims?

| Stage | Market State | Strategy |
|-------|--------------|----------|
| 1 | Virgin market | Simple, direct claim works |
| 2 | Some competition | Expand the claim (faster, better) |
| 3 | Crowded | Introduce unique mechanism |
| 4 | Saturated | Escalate mechanisms |
| 5 | Exhausted | Sell identity, not features |

**Key Insight**: Most AI founders pitch "Solution Aware" copy (LLMs, Agents, RAG) to "Problem Aware" customers who only care about outcomes.

---

### Framework 2: Influence (Robert Cialdini)
**Core Concept**: 7 Levers of Persuasion

Engineer these triggers into your UX, onboarding, and copy:

| Lever | Definition | Application |
|-------|------------|-------------|
| **Authority** | People follow experts | Logos, endorsements, credentials, "As seen in..." |
| **Social Proof** | People follow crowds | Reviews, star ratings, user counts, testimonials |
| **Commitment & Consistency** | People honor commitments | Progressive onboarding, small yeses before big ask |
| **Liking** | People buy from those like them | Mirror user identity, relatable brand voice |
| **Reciprocity** | People return favors | Free value first (audit, calculator, template) |
| **Scarcity** | People want rare things | Limited time, limited access, exclusive features |
| **Unity** | People join tribes | Shared identity, community, "us vs them" |

**Scoring**: Rate each lever 0-10 for any piece of marketing copy.

---

### Framework 3: Yes! 50 Ways to Be Persuasive
**Core Concept**: Tactical Implementation

Key tactics to apply:

1. **Framing beats Force**: "Most people don't litter here" > "Don't litter"
2. **Specific Social Proof**: "Join 10,000 founders like you" > "Join 10,000 users"
3. **Loss Aversion**: "Stop losing 10 hours/week" > "Gain productivity" (pain avoidance is 2x more powerful)
4. **Similarity Shortcut**: Highlight shared identity to increase compliance
5. **Commitment Ladder**: Series of small yeses leads to one big yes
6. **Contrast Effect**: Show the alternative first to make your offer shine
7. **Labeling**: Call them what you want them to become ("You're the type who...")

---

### Framework 4: Take Their Money (Kyle Milligan)
**Core Concept**: NEW, EASY, SAFE, BIG

Every headline, CTA, and piece of copy must hit these 4 emotional quadrants:

| Quadrant | Brain Response | Examples |
|----------|----------------|----------|
| **NEW** | Craves novelty | "The first AI agent that...", "Revolutionary approach" |
| **EASY** | Conserves energy | "One-click deploy", "No config needed", "5 minutes to start" |
| **SAFE** | Fears risk | "Bank-level encryption", "Used by GitLab", "Money-back guarantee" |
| **BIG** | Wants status/transformation | "10x your output", "Dominate your niche", "Enterprise-grade" |

**Scoring**: Rate each dimension 0-10. Strong copy hits all 4.

**Examples from B2B SaaS**:
- PagerDuty: "99% faster" (BIG/EASY), "Trusted by 30k companies" (SAFE)
- GitLab: "50 million users" (SAFE), "Less time managing, more time delivering" (EASY/BIG)

---

### Framework 5: One Sentence Persuasion Course (Blair Warren)
**Core Concept**: Build Cult-Like Following

> "People will do anything for those who encourage their dreams, justify their failures, allay their fears, confirm their suspicions, and help throw rocks at their enemies."

| Element | How to Apply |
|---------|--------------|
| **Encourage Dreams** | "You can build production AI apps without a PhD" |
| **Justify Failures** | "It's not your fault the tools were too hard. AI fixes this." |
| **Allay Fears** | "You won't break production. Sandbox mode protects you." |
| **Confirm Suspicions** | "You were right - the old system was rigged against indie devs." |
| **Throw Rocks at Enemies** | Define common enemy: "Legacy gatekeepers", "Bloated enterprise software" |

**Key Insight**: Don't just sell a tool. Sell a movement. Create unity through shared enemies.

---

## Available Skills

This plugin provides:

1. **awareness-analyzer**: Diagnose audience awareness level and market sophistication
2. **persuasion-auditor**: Score content against Cialdini's 7 levers
3. **copy-optimizer**: Apply tactical persuasion techniques
4. **nesb-scorer**: Score headlines against NEW-EASY-SAFE-BIG
5. **tribe-builder**: Generate tribe-building copy
6. **voice-extractor**: Analyze existing content for voice patterns
7. **competitor-analyzer**: Analyze competitor positioning via browser
8. **content-generator**: Generate optimized marketing content

## Workflow

When generating or analyzing marketing content:

1. **Diagnose**: Use awareness-analyzer to understand the target audience
2. **Score**: Use persuasion-auditor and nesb-scorer to evaluate existing copy
3. **Optimize**: Use copy-optimizer to apply tactical improvements
4. **Generate**: Use content-generator with all frameworks applied
5. **Build Tribe**: Use tribe-builder to add movement-building elements
6. **Review**: Score the output against all frameworks before finalizing

## Content Types

This plugin can generate:
- GitHub READMEs (developer-focused)
- Landing page copy (conversion-focused)
- X/Twitter threads (viral-focused)
- LinkedIn posts (professional)
- YouTube script intros (hook-focused)
- Substack/blog articles (thought leadership)
- Product Hunt launches (launch-optimized)

## Voice Matching

Before generating content, extract the user's existing voice from their repos, blogs, or social profiles. Match:
- Tone (formal/casual)
- Vocabulary (technical depth)
- Sentence structure
- Recurring patterns
- Brand personality
