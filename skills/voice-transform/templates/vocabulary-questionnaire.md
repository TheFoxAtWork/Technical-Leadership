# Vocabulary Customization Questionnaire

**Purpose**: Generate a personalized vocabulary configuration in 10 minutes.

Answer these questions to customize how the voice-transform skill handles vocabulary while preserving the proven structural and tonal patterns.

---

## Question 1: Contraction Style

How do you prefer to use contractions in professional writing?

**Options**:
- **A**: Always use contractions ("you're", "it's", "doesn't") - feels natural and conversational
- **B**: Context-dependent - formal docs get fewer, team communication gets more
- **C**: Avoid contractions - prefer formal style ("you are", "it is", "does not")

**Your answer**: ___

**Why this matters**: Contractions affect formality. "You're" reads casual, "you are" reads formal. Most professional writing benefits from natural contractions (option A or B).

---

## Question 2: Verb Preference Style

Which verb style best matches your professional communication?

**Options**:
- **A**: Concrete action verbs - "drove", "built", "shipped", "resolved"
- **B**: Collaborative language - "aligned", "partnered", "enabled", "supported"
- **C**: Analytical precision - "analyzed", "evaluated", "determined", "measured"

**Your answer**: ___

**Examples**:
- A: "We drove the migration from design to production in 3 months"
- B: "We aligned with three teams to enable the migration rollout"
- C: "We analyzed migration risks and determined a phased rollout approach"

**Why this matters**: Your verb style signals your role perspective. Pick what feels most authentic to how you work.

---

## Question 3: Emoji Policy

How do you use emoji in professional communication?

**Options**:
- **A**: Never - emoji doesn't belong in professional writing
- **B**: Sparingly - only in informal team contexts when genuinely additive
- **C**: Strategic - use emoji to signal tone or emphasize key points
- **D**: Freely - emoji is a natural part of how I communicate

**Your answer**: ___

**Why this matters**: Emoji changes perceived professionalism. Mismatch between your policy and output feels inauthentic.

---

## Question 4: Signature Phrases

What are 3-5 phrases that sound distinctly like you?

These can be:
- Transition phrases ("Here's why:", "Let me walk you through")
- Explanatory hooks ("Think of it like", "The key insight is")
- Structural markers ("Three areas:", "Breaking this down:")

**Your phrases**:
1. ___
2. ___
3. ___
4. ___ (optional)
5. ___ (optional)

**Why this matters**: These phrases create voice consistency. When readers see them, they know it's you.

---

## Question 5: Forbidden Words

What corporate jargon or overused phrases do you actively avoid?

**Common examples**:
- "leverage" (unless mechanical advantage)
- "synergize"
- "circle back"
- "bandwidth" (prefer "time" or "capacity")
- "touch base" (prefer "discuss" or "check in")
- "drill down"
- "move the needle"

**Your forbidden words** (add to defaults or modify):
1. ___
2. ___
3. ___
4. ___ (optional)
5. ___ (optional)

**Why this matters**: Removing jargon you personally dislike keeps your authentic voice.

---

## Question 6: Metaphor Style

How often do you use metaphors or analogies in explanations?

**Options**:
- **A**: Technical metaphors frequently - "key exchange", "scaffold", "rate limiting"
- **B**: Everyday metaphors occasionally - "like organizing a closet", "similar to untying a knot"
- **C**: Rarely use metaphors - prefer direct literal explanations

**Your answer**: ___

**If you use metaphors, provide 2-3 examples you commonly use**:
1. ___
2. ___
3. ___ (optional)

**Why this matters**: Metaphors create memorable explanations but can feel forced if overused or mismatched to your style.

---

## Question 7: Audience Formality Scale

For each audience type, rate your formality on a 1-5 scale:
- **1** = Very casual (lots of contractions, conversational, personal)
- **3** = Balanced (professional but personable)
- **5** = Very formal (fewer contractions, impersonal, structured)

**Your ratings**:
- Leadership / Executive stakeholders: ___
- Peers / Same-level colleagues: ___
- Your team / Direct reports: ___
- Cross-functional / Other departments: ___
- External / Public communication: ___

**Why this matters**: Knowing your formality preferences per audience lets the skill match your natural code-switching.

---

## Question 8: Technical Depth Approach

When explaining technical concepts, what's your default approach?

**Options**:
- **A**: Summary-first - give the conclusion, then details for those who want them
- **B**: Deep-first - explain the mechanics, then summarize the implications
- **C**: Layered - brief summary, then progressive detail for different reader depths

**Your answer**: ___

**Why this matters**: This affects how examples and explanations are ordered. Mismatch frustrates your audience.

---

## Question 9: Sentence Complexity Preference

What's your natural sentence style?

**Options**:
- **A**: Short & punchy - one idea per sentence, rarely more than 15 words
- **B**: Varied rhythm - mix of short and medium sentences for flow
- **C**: Complex allowed - comfortable with longer sentences when needed

**Your answer**: ___

**Why this matters**: Sentence length affects readability and pacing. Your preference should match your role and audience.

---

## Question 10: Writing Samples (Optional)

Do you have 3-5 writing samples you're proud of that we can analyze for vocabulary patterns?

**Options**:
- **Yes** - I'll provide file paths or paste content
- **No** - use my questionnaire answers only

**If yes, provide**:
- Sample 1 (file path or paste excerpt): ___
- Sample 2: ___
- Sample 3: ___
- Sample 4 (optional): ___
- Sample 5 (optional): ___

**Why this matters**: Real writing samples reveal patterns you might not consciously recognize. Optional but highly valuable.

---

## What Happens Next

Your answers will generate a `vocabulary-config.json` file with:
- Contraction policy and examples
- Preferred verb style and examples
- Emoji usage rules
- Signature phrases to use
- Forbidden words to avoid
- Metaphor frequency and examples
- Audience-specific formality levels
- Technical depth preference
- Sentence complexity targets

The voice-transform skill will use this config to customize vocabulary **while preserving the proven structural and tonal patterns** (short paragraphs, clear scaffolding, concrete examples, etc.).

---

## Generating Your Config

To generate your `vocabulary-config.json` from these answers:

```bash
/voice-transform --customize
```

The skill will:
1. Present these questions interactively
2. Validate your answers
3. Generate `~/.claude/skills/voice-transform/customized/vocabulary-config.json`
4. Confirm the config is valid
5. You can now use `/voice-transform` with your personal vocabulary preferences

---

**Quick Start**: Most users answer questions 1-7 and skip writing samples initially. You can always regenerate later with writing samples for higher fidelity.

**Time estimate**: 10-15 minutes for questions 1-7, 20-30 minutes if including writing samples.

---

**Last updated**: 2026-07-16  
**Purpose**: Interactive questionnaire for personalizing voice-transform vocabulary
