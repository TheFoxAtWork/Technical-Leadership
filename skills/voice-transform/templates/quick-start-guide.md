# Voice Transform Quick Start Guide

**Purpose**: Get started with voice-transform in 0, 10, or 30 minutes based on your needs.

---

## Installation (5 minutes)

### Step 1: Clone and Symlink

```bash
# Clone the Technical-Leadership repo (if you haven't already)
cd /Users/YOUR_USER/Documents/GitHub
git clone git@github.com:TheFoxAtWork/Technical-Leadership.git

# Create symlink to the skill
ln -s /Users/YOUR_USER/Documents/GitHub/Technical-Leadership/skills/voice-transform \
      ~/.claude/skills/voice-transform
```

Replace `YOUR_USER` with your actual username.

### Step 2: Verify Installation

```bash
ls -la ~/.claude/skills/voice-transform
```

You should see a symlink pointing to the Technical-Leadership directory.

---

## Three Usage Paths

Choose your path based on how much time you have and how much customization you want.

### Path 1: Instant Use (0 minutes)
**Goal**: Use default patterns immediately  
**Time**: 0 minutes (already installed)  
**Value**: Proven structure/tone/explanatory patterns

```bash
/voice-transform "Your draft text here"
```

**What you get**:
- Short paragraphs (3-5 sentences)
- Clear scaffolding and structure
- Concrete over abstract language
- Active voice transformations
- Professional conversational tone
- No vocabulary customization (uses generic improvements only)

**Best for**: Quick cleanup of AI-generated text, trying the skill before customizing

---

### Path 2: Personalized Vocabulary (10 minutes)
**Goal**: Add your personal voice while keeping proven patterns  
**Time**: 10-15 minutes  
**Value**: Default patterns + your vocabulary preferences

```bash
/voice-transform --customize
```

This launches an interactive questionnaire covering:
1. Contraction style (always/context/never)
2. Verb preference (concrete/collaborative/analytical)
3. Emoji policy (never/sparingly/strategic/freely)
4. Signature phrases (3-5 phrases that sound like you)
5. Forbidden words (corporate jargon to avoid)
6. Metaphor style (technical/everyday/rare)
7. Audience formality (1-5 scale per audience type)
8. Technical depth (summary-first/deep-first/layered)
9. Sentence complexity (short/varied/complex)
10. Writing samples (optional)

**After answering**, the skill generates:
```
~/.claude/skills/voice-transform/customized/vocabulary-config.json
```

**Now use it**:
```bash
/voice-transform "Your draft text here"
```

**What you get**:
- All default structural and tonal patterns
- Your preferred verbs and phrases
- Your forbidden words avoided
- Your emoji policy applied
- Your audience formality levels

**Best for**: Most users who want their AI output to sound like them

---

### Path 3: Advanced Pattern Customization (30+ minutes)
**Goal**: Full control over transformation patterns  
**Time**: 30+ minutes  
**Value**: Complete customization of structure/tone/vocabulary

**Step 1**: Copy defaults to customized directory

```bash
mkdir -p ~/.claude/skills/voice-transform/customized
cp ~/.claude/skills/voice-transform/defaults/structure-patterns.md \
   ~/.claude/skills/voice-transform/customized/custom-patterns.md
```

**Step 2**: Edit custom-patterns.md

```bash
code ~/.claude/skills/voice-transform/customized/custom-patterns.md
```

**What you can customize**:
- Paragraph length (default 3-5 sentences → change to 2-3)
- Scaffolding structure (modify hierarchy rules)
- List usage patterns (when to use numbered vs bullets)
- Explanatory approach (examples-first vs summary-first)
- Meta-commentary frequency (more or fewer reader check-ins)

**Step 3**: Use with custom patterns

```bash
/voice-transform "Your draft text here"
```

**What you get**:
- Your custom structural patterns (overrides defaults)
- Your vocabulary config (if you completed Path 2)
- Full control over transformation logic

**Best for**: Power users who understand WHY patterns work and want to tune them

---

## Troubleshooting

### Problem: Symlink creation fails

**Symptom**:
```
ln: /Users/YOUR_USER/.claude/skills/voice-transform: File exists
```

**Solution**:
```bash
# Remove existing symlink or directory
rm ~/.claude/skills/voice-transform

# Recreate symlink
ln -s /Users/YOUR_USER/Documents/GitHub/Technical-Leadership/skills/voice-transform \
      ~/.claude/skills/voice-transform
```

---

### Problem: Skill not found

**Symptom**:
```
Error: Skill 'voice-transform' not found
```

**Solution**:
```bash
# Verify symlink exists
ls -la ~/.claude/skills/voice-transform

# Verify it points to Technical-Leadership
readlink ~/.claude/skills/voice-transform

# Should show: /Users/YOUR_USER/Documents/GitHub/Technical-Leadership/skills/voice-transform
```

---

### Problem: Config file validation fails

**Symptom**:
```
Error: Invalid vocabulary-config.json
```

**Solution**:
```bash
# Check JSON syntax
cat ~/.claude/skills/voice-transform/customized/vocabulary-config.json | jq .

# If syntax error, compare against template
diff ~/.claude/skills/voice-transform/customized/vocabulary-config.json \
     ~/.claude/skills/voice-transform/templates/vocabulary-config-template.json

# If broken, regenerate
/voice-transform --customize
```

---

### Problem: Transformations not applying vocabulary config

**Symptom**: Output doesn't use your preferred verbs or avoid your forbidden words

**Solution**:
```bash
# Verify config exists
ls -la ~/.claude/skills/voice-transform/customized/vocabulary-config.json

# If missing, regenerate
/voice-transform --customize

# If exists, check it's valid JSON
cat ~/.claude/skills/voice-transform/customized/vocabulary-config.json | jq .
```

---

### Problem: Want to reset to defaults

**Solution**:
```bash
# Remove customization
rm -rf ~/.claude/skills/voice-transform/customized/

# Skill will use defaults only
/voice-transform "Your text here"

# To re-customize
/voice-transform --customize
```

---

## Tips for Best Results

### 1. Start with Defaults
Don't customize until you've used defaults a few times. You might find they already work well for you.

### 2. Customize Vocabulary First
Path 2 (vocabulary customization) gives you most of the personalization value in 10 minutes. Only go to Path 3 if you need structural changes.

### 3. Provide Good Input
The skill transforms existing text. Better input = better output.

**Good input**:
- AI-generated content that needs humanizing
- Draft text that's technically correct but sounds generic
- Status updates that need formality adjustment

**Poor input**:
- Gibberish or incomplete sentences
- Content with factual errors (transformation preserves meaning)
- Empty text

### 4. Match Context to Audience
If output formality seems wrong, check your audience formality config. Leadership should be 4-5, team should be 2-3.

### 5. Iterate on Config
Your first customization won't be perfect. Use the skill, notice what feels off, regenerate config with adjustments.

---

## What's Included

When you install voice-transform, you get:

**Defaults** (shipped, proven patterns):
- `defaults/structure-patterns.md` - Paragraph length, scaffolding, lists
- `defaults/tone-patterns.md` - Direct address, difficulty acknowledgment, concrete>abstract
- `defaults/explanatory-patterns.md` - If/then/else, examples-first, meta-commentary
- `defaults/validation-checklist.md` - Quality checks

**Templates** (for customization):
- `templates/vocabulary-questionnaire.md` - 10-question interactive guide
- `templates/vocabulary-config-template.json` - JSON schema
- `templates/quick-start-guide.md` - This file

**Examples**:
- `examples/before-after-defaults.md` - Transformation demonstrations

**Engine**:
- `SKILL.md` - Transformation logic and orchestration

---

## Next Steps

**After installation**:
1. Test with defaults: `/voice-transform "Your text"`
2. Review output and decide if customization is needed
3. If needed, run `/voice-transform --customize`
4. Use regularly and iterate on config

**Getting help**:
- Check `README.md` for overview
- See `examples/before-after-defaults.md` for transformation examples
- Review `defaults/validation-checklist.md` for quality criteria

---

**Last updated**: 2026-07-17  
**Purpose**: Quick start guide for voice-transform skill installation and usage
