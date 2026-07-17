# Voice Transform

**Transform AI-generated content using proven structural and tonal patterns.**

Works immediately out-of-box with defaults that have held up across thousands of transformations. Customize vocabulary in 10 minutes if you want your personal voice.

---

## Philosophy

**The Problem**: AI-generated content is structurally sound but tonally generic. Passive voice, corporate jargon, abstractions without grounding, conclusions without reasoning.

**The Insight**: Good writing follows universal structural patterns (short paragraphs, clear scaffolding, concrete examples) but personal voice comes from vocabulary choices (specific verbs, signature phrases, metaphor style).

**This Solution**: Separate the universal from the personal. Ship proven structural/tonal patterns as defaults that work for 80% of users. Make vocabulary customization optional and fast (10 minutes). Give power users full pattern control if needed.

**Connection to Technical Leadership**: Clear communication is a core technical leadership skill. The patterns in this skill come from effective technical writing practices—directness, transparency, reader-focused structure. Whether you're writing status updates, architecture docs, or team communication, these patterns make your writing more actionable and accessible.

**Why Open Source This**: Writing transformation shouldn't be proprietary. The patterns here are proven practices, not trade secrets. Share the scaffold so others can build on it.

---

## What This Skill Does

Takes generic AI-generated text and transforms it to be:
- **Clear**: Short paragraphs (3-5 sentences), explicit scaffolding, scannable structure
- **Direct**: Active voice, specific verbs, concrete over abstract
- **Professional**: Natural contractions, no corporate jargon, authentic tone
- **Accessible**: Examples-first, reasoning shown, reader-friendly explanations

**Three-layer architecture**:
1. **Transformation engine**: Orchestrates pattern application
2. **Pattern defaults**: Proven structure/tone/explanatory patterns (shipped, work immediately)
3. **Vocabulary customization**: Optional 10-minute questionnaire adds your personal voice

---

## Architecture & Design Rationale

### Why Three Layers?

**Layer 1: Transformation Engine** (SKILL.md)  
Orchestrates transformation. Detects context, loads patterns, applies transformations, validates output. This is the "how" of transformation.

**Layer 2: Pattern Defaults** (defaults/)  
Universal structural/tonal patterns that make writing clearer. Work for most users without customization. Examples: short paragraphs, active voice, concrete over abstract, if/then/else reasoning structures.

**Layer 3: Vocabulary Customization** (templates/, user-generated)  
Personal vocabulary preferences (verbs, phrases, emoji policy, formality levels). Optional 10-minute questionnaire. Overlays on patterns without replacing them.

**Why This Separation?**  
Structural patterns are universal. Vocabulary is personal. When you separate them:
- Defaults work immediately—no config required
- Customization takes 10 minutes, not hours (10 questions covers what matters)
- Power users can override specific patterns while keeping the rest

### Progressive Disclosure Principle

**Level 1 (0 min)**: Use defaults. No setup, patterns applied immediately.  
**Level 2 (10 min)**: Add personal vocabulary via questionnaire.  
**Level 3 (30+ min)**: Override patterns themselves (power users).

Each level delivers immediate value. Invest more time only if the defaults don't match your needs.

### Graceful Degradation

No config? Use defaults. Partial config? Fill gaps with defaults. Invalid config? Warn and fall back to defaults.

**Design goal**: Never break. Transformation always produces output.

### Pattern Priority System

For each transformation:
1. Check for user's custom pattern override (if exists)
2. Fall back to shipped default (always available)

Power users override specific patterns while keeping others as defaults.

---

## Quick Start

### Installation (5 minutes)

```bash
ln -s /Users/YOUR_USER/Documents/GitHub/Technical-Leadership/skills/voice-transform \
      ~/.claude/skills/voice-transform
```

Replace `YOUR_USER` with your actual username.

### Use Immediately (0 minutes)

```bash
/voice-transform "Your draft text here"
```

**What you get**: Default patterns applied (structure, tone, explanatory improvements). No customization required.

### Customize Vocabulary (10 minutes)

```bash
/voice-transform --customize
```

Answer 10 questions about:
- Contraction style (always/context/never)
- Verb preferences (concrete/collaborative/analytical)
- Emoji policy (never/sparingly/strategic/freely)
- Signature phrases (what sounds like you)
- Forbidden words (corporate jargon to avoid)
- Metaphor style (technical/everyday/rare)
- Audience formality (1-5 scale per audience)
- Technical depth (summary-first/deep-first/layered)
- Sentence complexity (short/varied/complex)
- Writing samples (optional)

Generates `~/.claude/skills/voice-transform/customized/vocabulary-config.json`

### Advanced Customization (30+ minutes, power users)

```bash
# Override default patterns
cp ~/.claude/skills/voice-transform/defaults/structure-patterns.md \
   ~/.claude/skills/voice-transform/customized/custom-patterns.md

# Edit patterns directly
code ~/.claude/skills/voice-transform/customized/custom-patterns.md
```

Customize paragraph length, scaffolding rules, explanatory approach, etc.

---

## What You Get

### Out-of-Box (Level 1: 0 minutes)

✅ **Structure patterns**:
- Short paragraphs (3-5 sentences)
- Clear scaffolding (Unit → Topic → Subsection)
- Questions as organizers
- If/then/else for complex ideas
- Appropriate list usage (numbered vs bullets)

✅ **Tone patterns**:
- Direct address ("you" for positive only)
- Difficulty acknowledged before solutions
- Permission to be imperfect
- Concrete over abstract
- Natural conversational tone

✅ **Explanatory patterns**:
- Concrete examples over abstractions
- Technical metaphors for clarity
- Meta-commentary (signposting)
- Reader check-ins
- Transparent process (show reasoning)

✅ **Quality validation**:
- Active voice check
- Corporate jargon removal
- Specificity verification
- Red flag detection

### With Vocabulary Customization (Level 2: 10 minutes)

✅ Everything from Level 1, plus:
- Your preferred verbs and phrases
- Your avoided words and jargon
- Your emoji policy applied
- Your audience formality levels
- Your metaphor style

### With Pattern Customization (Level 3: 30+ minutes)

✅ Everything from Level 2, plus:
- Custom paragraph length targets
- Custom scaffolding rules
- Custom explanatory approach
- Full control over transformation logic

---

## Upgrade Path

**Choose your level based on time and needs**:

| Level | Time | Value | Best For |
|-------|------|-------|----------|
| 1: Defaults | 0 min | Proven patterns | Quick cleanup, trying the skill |
| 2: Vocabulary | 10 min | Defaults + personal voice | Most users (recommended) |
| 3: Patterns | 30+ min | Full customization | Power users who understand why patterns work |

**Start at Level 1**: Use defaults first. Only customize if you notice specific vocabulary that doesn't match your style.

---

## How It Works

### Transformation Flow

1. **Load config** (if `vocabulary-config.json` exists, load it; otherwise use defaults only)
2. **Detect context** (formality level, audience, complexity)
3. **Load patterns** (check for custom patterns, fall back to defaults)
4. **Apply structural transformations** (paragraphs, scaffolding, lists, if/then/else)
5. **Apply tonal transformations** (direct address, difficulty acknowledgment, concrete>abstract)
6. **Apply explanatory transformations** (examples, metaphors, meta-commentary, reasoning)
7. **Apply vocabulary preferences** (if config exists: replace verbs, apply emoji policy, audience formality)
8. **Validate output** (quality checks against validation checklist)
9. **Generate annotations** (show what changed and why)
10. **Return transformed text** + annotations + validation status

### Pattern Priority

For each pattern type:
```
Check: customized/custom-patterns.md (user override)
  ↓
If not found: defaults/structure-patterns.md (shipped default)
```

**Graceful degradation**: No config? Use defaults. Partial config? Use defaults for missing fields.

---

## File Structure

```
voice-transform/
├── SKILL.md                          # Transformation engine
├── README.md                         # This file
├── defaults/                         # Shipped patterns (proven across use)
│   ├── structure-patterns.md        # Paragraph length, scaffolding, lists
│   ├── tone-patterns.md             # Direct address, concrete>abstract
│   ├── explanatory-patterns.md      # If/then/else, examples, metaphors
│   └── validation-checklist.md      # Quality validation
├── templates/                        # Customization helpers
│   ├── vocabulary-questionnaire.md  # 10-question interactive guide
│   ├── vocabulary-config-template.json # JSON schema
│   └── quick-start-guide.md         # Installation and usage guide
└── examples/
    └── before-after-defaults.md     # Transformation demonstrations
```

**User customizations** (not version controlled):
```
~/.claude/skills/voice-transform/
├── customized/
│   ├── vocabulary-config.json       # Generated from questionnaire
│   └── custom-patterns.md           # Optional pattern overrides
└── [symlinks to GitHub Technical-Leadership files]
```

---

## Examples

### Example 1: Basic Transformation

**Before**:
```
I successfully facilitated alignment across multiple business units. The meeting was 
productive and we were able to address several key concerns that had been raised.
```

**After**:
```
I drove alignment across three business units. We resolved three key concerns 
(compliance, timeline, budget) that had been raised.
```

**What changed**:
- "Successfully facilitated" → "drove" (active, specific verb)
- "Multiple" → "three" (concrete number)
- "Were able to address" → "resolved" (active voice)
- "Several key concerns" → "three key concerns (compliance, timeline, budget)" (specific, concrete)

### Example 2: With Vocabulary Customization

**Config**: Avoid "drove", prefer "led"

**Before**:
```
I successfully facilitated the migration strategy meeting.
```

**After**:
```
I led the migration strategy meeting to a decision.
```

**What changed**:
- "Successfully facilitated" → "led" (preferred verb from config, not default "drove")

### Example 3: Structural Transformation

**Before** (wall of text):
```
The framework provides several benefits including improved code quality and better 
maintainability over time. When teams adopt this approach they often see reduced bug 
counts and faster feature delivery. However it's important to note that the initial 
setup requires some investment in training and tooling. Most teams report that this 
investment pays off within the first quarter of adoption.
```

**After** (short paragraphs + concrete):
```
The framework improves code quality and maintainability. Teams typically see reduced 
bugs and faster feature delivery.

The initial setup requires training and tooling investment. Most teams report this 
pays off within the first quarter.
```

**What changed**:
- One 4-sentence paragraph → Two 2-sentence paragraphs (visual breathing room)
- "Provides several benefits including" → "improves" (direct, specific)
- "It's important to note that" → removed (hedging)
- Preserved concrete outcome (first quarter payoff)

---

## Design Principles

### 1. Progressive Disclosure
Complexity hidden until needed:
- Level 1 (defaults): Works immediately
- Level 2 (vocabulary): Easy 10-minute customization
- Level 3 (patterns): Full control for power users

### 2. Graceful Degradation
Transformation never breaks due to missing config:
- No config? Use defaults
- Partial config? Fill gaps with defaults
- Invalid config? Warn and fall back to defaults

### 3. Separation of Concerns
Universal patterns ≠ personal vocabulary:
- **Defaults** (structure/tone/explanatory): Universal, shipped, work for most users
- **Vocabulary** (verbs/phrases/emoji): Personal, easily customizable
- **Patterns** (advanced): Full control, requires understanding why patterns work

### 4. Clear Value Per Level
Each level provides immediate value:
- Defaults: "Get proven patterns immediately"
- Vocabulary: "Add your personal voice in 10 minutes"
- Patterns: "Full control for power users"

---

## Troubleshooting

### Skill not found

```bash
# Verify symlink
ls -la ~/.claude/skills/voice-transform

# Should point to GitHub Technical-Leadership repo
readlink ~/.claude/skills/voice-transform
```

### Config not loading

```bash
# Verify JSON is valid
cat ~/.claude/skills/voice-transform/customized/vocabulary-config.json | jq .

# Regenerate if broken
/voice-transform --customize
```

### Want to reset to defaults

```bash
# Remove all customizations
rm -rf ~/.claude/skills/voice-transform/customized/

# Skill will use defaults only
```

### Output doesn't match my style

```bash
# Customize vocabulary
/voice-transform --customize

# Check your answers align with your writing style
```

---

## Tips for Best Results

### 1. Start with Defaults
Don't customize until you've tried defaults a few times. They might already work well for you.

### 2. Vocabulary First, Patterns Later
10 minutes on vocabulary customization gives you 80% of personalization value. Only override patterns if you need structural changes.

### 3. Provide Good Input
Better input = better output:
- ✅ AI-generated content that needs humanizing
- ✅ Draft text that's technically correct but sounds generic
- ✅ Status updates that need formality adjustment
- ❌ Gibberish or incomplete sentences
- ❌ Content with factual errors (transformation preserves meaning)

### 4. Iterate on Config
Your first customization won't be perfect. Use the skill, notice what feels off, regenerate config with adjustments.

---

## What's Next

### After Installation

1. **Test with defaults**: `/voice-transform "Your text"`
2. **Review output**: Does it match your needs?
3. **Customize if needed**: `/voice-transform --customize`
4. **Use regularly**: Integrate into your workflow

### Getting Help

- **Quick Start**: See `templates/quick-start-guide.md`
- **Examples**: See `examples/before-after-defaults.md`
- **Patterns**: See files in `defaults/`
- **Validation**: See `defaults/validation-checklist.md`

---

## Credits

**Design**: Generalized from the fox-voice skill  
**Pattern Source**: Extracted from proven professional communication patterns  
**Author**: Emily Fox  
**Repository**: github.com/TheFoxAtWork/Technical-Leadership  
**License**: CC BY 4.0

---

**Last updated**: 2026-07-17  
**Version**: 1.0  
**Purpose**: Professional writing transformation with progressive customization
