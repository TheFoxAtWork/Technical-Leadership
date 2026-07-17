# Voice Transform Skill

**Purpose**: Transform AI-generated content using proven structural and tonal patterns while allowing personal vocabulary customization.

**Default behavior**: Works immediately with battle-tested patterns. Vocabulary customization optional via `--customize` flag.

---

## Invocation

```bash
# Use with defaults (no customization required)
/voice-transform "Your draft text here"

# Or provide file path
/voice-transform path/to/draft.md

# Customize vocabulary (interactive questionnaire)
/voice-transform --customize

# Show current configuration
/voice-transform --show-config
```

---

## How It Works

### Three-Layer Architecture

1. **Transformation Engine** (this file)
   - Orchestrates transformation process
   - Loads patterns and configuration
   - Applies transformations in sequence
   - Validates output quality

2. **Pattern Defaults** (in `defaults/`)
   - Structure patterns (paragraph length, scaffolding, lists)
   - Tone patterns (direct address, concrete>abstract, permission structures)
   - Explanatory patterns (if/then/else, examples-first, meta-commentary)
   - Validation checklist (quality checks)

3. **Vocabulary Customization** (optional, in `customized/`)
   - User-specific vocabulary preferences
   - Generated from questionnaire or edited directly
   - Overrides vocabulary while preserving structural patterns

---

## Transformation Flow

When you invoke `/voice-transform "text"`:

### Step 1: Load Configuration

```
Check for: ~/.claude/skills/voice-transform/customized/vocabulary-config.json
- If exists → Load vocabulary preferences
- If not → Use empty config (defaults only)
```

**Graceful fallback**: Missing config doesn't break transformation. Defaults work standalone.

### Step 2: Detect Context

Analyze input to determine:

**Formality level**:
- High (5): Formal language, leadership audience, external communication
- Medium (3): Balanced professional + personality, strategic docs
- Low (1-2): Conversational, team communication, internal

**Context markers**:
- File path patterns (e.g., `/status-updates/` vs `/team-notes/`)
- Content markers (presence of audience names, technical depth)
- Length and structure (short comment vs long document)

**Audience inference**:
- Leadership vocabulary → high formality
- Team-specific references → low formality
- Cross-functional language → medium formality

### Step 3: Load Patterns

**Pattern priority system**:
```
For each pattern type (structure/tone/explanatory):
  Check: customized/custom-patterns.md#<pattern_name>
    → If exists: Use custom pattern (user override)
    → If not: Use defaults/<pattern-type>.md (shipped default)
```

**Loaded patterns**:
- Structure: Paragraph length, scaffolding, questions, if/then/else, lists
- Tone: Direct address, difficulty acknowledgment, permission, concrete>abstract, contractions
- Explanatory: Examples-first, metaphors, meta-commentary, reader check-ins, transparent process

### Step 4: Apply Structural Transformations

Transform structure using patterns from `defaults/structure-patterns.md`:

**Paragraph breaks**:
- Target: 3-5 sentences per paragraph
- Insert breaks when paragraph exceeds 5 sentences
- Preserve intentional long paragraphs (lists, code blocks)

**Scaffolding**:
- Detect implicit structure in content
- Add explicit headers (Unit → Topic → Subsection)
- Number sections when order matters or count is significant

**List conversion**:
- Sequential concepts → numbered lists
- Parallel concepts → bullet lists
- Ensure lists have clear introduction

**If/then/else framing**:
- Detect complex decisions or recommendations
- Add "If" (assumptions), "Then" (logic), "Else" (exceptions) structure
- Make reasoning explicit

### Step 5: Apply Tonal Transformations

Transform tone using patterns from `defaults/tone-patterns.md`:

**Direct address**:
- "You" for positive framing → preserve
- "You" for criticism → change to "it/that/this"
- Example: "You failed" → "This approach missed"

**Difficulty acknowledgment**:
- Detect minimizing language ("just", "simply", "easy")
- Add acknowledgment before solutions
- Example: "Just follow these steps" → "This is complex. Here's how to approach it:"

**Permission structures**:
- Add realistic expectations
- Normalize struggle and iteration
- Example: "Complete all items" → "You won't finish everything. Progress over perfection."

**Concrete over abstract**:
- Detect vague language ("various", "some", "several", "potential")
- Replace with specific numbers, names, examples
- Example: "Some challenges" → "Three blockers (FIPS requirements, timeline, budget)"

**Contraction policy** (from vocabulary config if present):
- `policy: "always"` → Add contractions throughout
- `policy: "context"` → More in low formality, fewer in high
- `policy: "never"` → Expand contractions

### Step 6: Apply Explanatory Transformations

Transform explanations using patterns from `defaults/explanatory-patterns.md`:

**Concrete examples**:
- Detect abstractions without grounding
- Add concrete examples or scenarios
- Example: "Alignment mechanisms" → "Build a shared protocol, like a key exchange, for how you'll communicate"

**Technical metaphors**:
- Match metaphor style to audience (technical vs everyday)
- Use metaphors from config if provided
- Example: "Aggregation framework" → "Think of it as a table of contents for data"

**Meta-commentary**:
- Add signposting for complex topics
- Guide reader through transitions
- Example: Add "Here's why this matters:" before critical sections

**Reader check-ins**:
- Anticipate confusion or objections
- Validate before redirecting
- Example: "You may find this takes longer than expected—that's normal."

**Transparent process**:
- Show reasoning, not just conclusions
- Add "Why" sections to recommendations
- Provide frameworks readers can reuse

### Step 7: Apply Vocabulary Preferences

If `vocabulary-config.json` exists, apply custom vocabulary:

**Verb replacement**:
- Replace avoided verbs (from config) with preferred verbs
- Example (config: avoid "leverage", prefer "use"):
  - "Leverage the framework" → "Use the framework"

**Forbidden words**:
- Replace corporate jargon with plain language
- Example: "bandwidth" → "time" or "capacity"

**Signature phrases**:
- Incorporate user's signature phrases where appropriate
- Example: Insert "Here's why:" before reasoning sections

**Emoji policy** (from config):
- `usage: "never"` → Remove all emoji
- `usage: "sparingly"` → Keep only if genuinely additive in allowed contexts
- `usage: "strategic"` → Add emoji to signal tone in appropriate contexts
- `usage: "freely"` → Preserve or add emoji naturally

**Metaphor style**:
- `frequency: "technical"` → Use technical metaphors
- `frequency: "everyday"` → Use everyday comparisons
- `frequency: "rare"` → Minimize metaphor use

**Formality adjustment** (from config `audience_formality`):
- Match detected audience to config formality level
- Adjust contraction frequency
- Adjust sentence complexity
- Adjust emoji usage

### Step 8: Validate Output

Check transformed content against `defaults/validation-checklist.md`:

**Structure checks**:
- [ ] Paragraphs 3-5 sentences max
- [ ] Clear scaffolding and headers
- [ ] Appropriate list usage
- [ ] Abstract concepts have concrete examples

**Tone checks**:
- [ ] "You" for positive only
- [ ] Difficulty acknowledged
- [ ] Permission structures present
- [ ] Natural contractions

**Vocabulary checks**:
- [ ] Active voice dominates
- [ ] Specific verbs over generic
- [ ] No corporate jargon (or user's forbidden words)
- [ ] Concrete numbers and specifics

**Red flags** (fail fast):
- ❌ Performative personality (excessive !!!, emoji storms)
- ❌ Corporate speak (synergize, circle back, etc.)
- ❌ Vague language (some, various, potential)
- ❌ Passive voice dominance
- ❌ Missing scaffold (conclusions without reasoning)

**If red flags present**: Flag for manual review before returning

### Step 9: Generate Annotations

Create transformation annotations showing what changed:

**Annotation format**:
```markdown
## Transformations Applied

### Structural
- Broke 8-sentence paragraph into 3 paragraphs (target: 3-5 sentences)
- Added "Why this matters" scaffolding for recommendation section
- Converted parallel concepts to bullet list

### Tonal
- "You failed to consider" → "This approach missed" (direct address for problems)
- Added difficulty acknowledgment: "This is complex. Here's how..."
- "Just follow these steps" → "Here's the approach" (no false simplification)

### Vocabulary
- "Leverage the framework" → "Use the framework" (avoided verb from config)
- "Various challenges" → "Three blockers: X, Y, Z" (concrete over abstract)
- "Bandwidth" → "time" (forbidden word from config)

### Explanatory
- Added concrete example: "Think of it like organizing a closet"
- Added "Why" section to recommendation
- Signposted transition: "Here's why this matters:"
```

**Annotation level** (configurable):
- `minimal`: Only major transformations
- `detailed`: All transformations with reasoning (default)
- `none`: No annotations (just transformed text)

### Step 10: Return Output

Return:
1. **Transformed text** (primary output)
2. **Annotations** (what changed and why, if enabled)
3. **Validation status** (pass/warn/fail)

**Output format**:
```markdown
# Transformed Content

[Transformed text here]

---

# Transformation Annotations

[Annotations showing what changed]

---

# Validation Status

✅ Structure: Passed (paragraphs 3-5 sentences, clear scaffolding)
✅ Tone: Passed (direct address appropriate, difficulty acknowledged)
✅ Vocabulary: Passed (active voice, specific verbs, no jargon)
✅ Explanatory: Passed (concrete examples, reasoning shown)

**Overall**: PASS
```

---

## Customization System

### Interactive Questionnaire (`--customize`)

When invoked with `--customize` flag:

1. **Load questionnaire** from `templates/vocabulary-questionnaire.md`
2. **Present 10 questions interactively**:
   - Contraction style
   - Verb preference
   - Emoji policy
   - Signature phrases
   - Forbidden words
   - Metaphor style
   - Audience formality (per audience type)
   - Technical depth preference
   - Sentence complexity
   - Writing samples (optional)

3. **Generate `vocabulary-config.json`** from answers
4. **Validate JSON schema** against `templates/vocabulary-config-template.json`
5. **Save to** `~/.claude/skills/voice-transform/customized/vocabulary-config.json`
6. **Confirm** config is valid and ready to use

**Writing sample analysis** (optional):
- If user provides sample files
- Extract vocabulary patterns (common verbs, phrase structures, contractions frequency)
- Populate config with extracted patterns
- Higher fidelity than questionnaire alone

### Manual Configuration

Users can manually edit:

**Vocabulary config**:
```bash
code ~/.claude/skills/voice-transform/customized/vocabulary-config.json
```

**Custom patterns** (advanced):
```bash
cp ~/.claude/skills/voice-transform/defaults/structure-patterns.md \
   ~/.claude/skills/voice-transform/customized/custom-patterns.md

code ~/.claude/skills/voice-transform/customized/custom-patterns.md
```

**Validation**: Schema validation on load prevents broken configs

---

## Context Detection Rules

**High Formality** (5):
- File paths: `/leadership/`, `/external/`, `/formal/`
- Content markers: "Dear", formal salutations, executive names
- Audience: Leadership, external, cross-organizational

**Medium Formality** (3):
- File paths: `/status/`, `/strategic/`, `/docs/`
- Content markers: Project names, cross-functional references
- Audience: Peers, cross-functional, strategic docs

**Low Formality** (1-2):
- File paths: `/team/`, `/internal/`, `/notes/`
- Content markers: First names, team-specific jargon, casual tone
- Audience: Direct team, mentoring, internal communication

**Audience-specific formality** (from config):
- If vocabulary config has `audience_formality` mapping
- Match detected audience to config level
- Override context detection if config is explicit

---

## Integration Hooks

This skill can be invoked by other skills:

**From `/fox-eod-hunt`**:
```
/voice-transform --input path/to/eod-draft.md --context eod-summary
```

**From weekly status skills**:
```
/voice-transform --input path/to/weekly-draft.md --context weekly-ops --formality high
```

**Programmatic usage**:
- Other skills can call voice-transform
- Pass context and formality explicitly
- Receive transformed text + annotations

---

## Configuration Files

### Required (Shipped with Skill)

- `defaults/structure-patterns.md` - Paragraph length, scaffolding, lists
- `defaults/tone-patterns.md` - Direct address, concrete>abstract, permission
- `defaults/explanatory-patterns.md` - If/then/else, examples, metaphors
- `defaults/validation-checklist.md` - Quality validation criteria
- `templates/vocabulary-questionnaire.md` - Interactive customization guide
- `templates/vocabulary-config-template.json` - JSON schema
- `examples/before-after-defaults.md` - Transformation examples

### Optional (User-Generated)

- `customized/vocabulary-config.json` - Personal vocabulary preferences
- `customized/custom-patterns.md` - Advanced pattern overrides (power users)

---

## Error Handling

**Missing config**: Use defaults (no error)  
**Invalid config JSON**: Warn user, fall back to defaults, suggest regeneration  
**Missing pattern file**: Fail gracefully with clear error message  
**Validation failure**: Return transformed text + warnings, don't block output  
**Red flag detection**: Flag for review, return untransformed if critical

---

## Performance Notes

**Typical transformation time**: 2-5 seconds for 500-word input  
**Bottlenecks**: Pattern matching and vocabulary replacement  
**Optimization**: Pattern caching for repeated transformations  
**Limitations**: Very large documents (>5000 words) may be slow

---

## Example Usage

### Basic Transformation

```bash
/voice-transform "I successfully facilitated the meeting and we were able to address the key concerns that were raised by stakeholders."
```

**Output**:
```
"I drove the meeting to a decision. We resolved three key concerns (compliance, timeline, budget) raised by stakeholders."

## Transformations Applied
- "Successfully facilitated" → "drove" (active verb)
- "Were able to address" → "resolved" (active voice, specific)
- "Key concerns" → "three key concerns (compliance, timeline, budget)" (concrete, numbered)
```

### With Customization

```bash
# First, customize
/voice-transform --customize
# Answer: avoid "drove", prefer "led"

# Then transform
/voice-transform "I successfully facilitated the meeting."
```

**Output**:
```
"I led the meeting to a decision."

## Transformations Applied
- "Successfully facilitated" → "led" (preferred verb from config)
```

---

## Troubleshooting

**Problem**: Transformed text doesn't match my style  
**Solution**: Run `/voice-transform --customize` to set vocabulary preferences

**Problem**: Too formal / too casual  
**Solution**: Check detected formality level. Adjust `audience_formality` in config.

**Problem**: Vocabulary config not loading  
**Solution**: Verify JSON is valid: `cat customized/vocabulary-config.json | jq .`

**Problem**: Want to reset to defaults  
**Solution**: `rm -rf customized/` to remove all customizations

---

**Last updated**: 2026-07-16  
**Version**: 1.0  
**Purpose**: Voice transformation engine with progressive customization
