# Structure Patterns

**Purpose**: Universal structural patterns for clear, scannable, and actionable writing.

These patterns create explicit progression that readers can follow independently, regardless of personal writing style.

---

## 1. Clear Scaffolding

Structure content with explicit progression that readers can follow independently.

**Pattern**: Unit → Topic → Subsection with numbers/headers

**Why this works**:
- Readers can jump to relevant sections
- Complex content becomes navigable
- Progress is visible and measurable

**Example**:
- ❌ "We'll cover several topics"
- ✅ "Three areas: Introspection (mastery over yourself), Extrospection (working with others), Operations (day-to-day execution)"

**Application**:
- Use clear hierarchy: main topic → subtopics → details
- Number sections when order matters or count is significant
- Make structure visible, not assumed

---

## 2. Questions as Organizational Devices

Questions guide thinking and create natural section breaks.

**Pattern**: Lead with question, follow with structured exploration

**Why this works**:
- Questions activate reader's thinking
- Creates natural breaks between sections
- Frames content as dialogue, not lecture

**Example**:
- ❌ "Consider your work satisfaction levels"
- ✅ "How do you feel about your life at work? Avoid the one-word answer—if you're reading this in January, you're probably feeling some dread about diving back in."

**Application**:
- Start sections with the question readers are asking
- Use questions to transition between topics
- Let questions guide the structure, not just decorate it

---

## 3. If/Then/Else Explanations

Complex ideas get structured logic that readers can verify independently.

**Pattern**: Provide assumptions (if), logic/process (then), and exceptions/caveats (else)

**Why this works**:
- Makes reasoning explicit and verifiable
- Readers can check if assumptions apply to them
- Exceptions prevent misapplication

**Structure**:
1. **If** = assumptions or prior knowledge you assume to be present
2. **Then** = content that is logic-based, independently verifiable, or conveys a process readers can follow
3. **Else** = defines exceptions to the explanation, caveats, or safeguards for error correction

**Example**:
```
If your team uses microservices (assumption),
Then isolating the auth service lets you upgrade without affecting other services (logic),
Else for monoliths, feature flags provide isolation without architectural changes (exception).
```

**Application**:
- Use for technical decisions, recommendations, or complex explanations
- Make assumptions explicit so readers can evaluate applicability
- Provide exception handling so misapplication is less likely

---

## 4. List Usage

Choose list type based on what you're communicating.

**Pattern**:
- **Sequential thinking** → numbered lists (order matters)
- **Parallel concepts** → bullets (order doesn't matter)

**Why this matters**:
- Numbers signal "follow these in order" or "count is significant"
- Bullets signal "these are options" or "all are equally important"
- Wrong choice confuses readers about how to use the information

**Examples**:

**Numbered** (sequential steps):
```
1. Detect context and formality level
2. Apply structural patterns
3. Apply vocabulary preferences
4. Validate output
```

**Bullets** (parallel options):
```
Key questions to ask:
- What are we trying to accomplish?
- What is the priority?
- When does it need to be completed?
- What format or medium does it need to be in?
```

**Application**:
- Default to bullets unless order matters
- Use numbers when steps must happen in sequence
- Use numbers when the count itself is significant (3 principles, 5 areas)

---

## 5. Short Paragraphs

**Pattern**: Rarely more than 4-5 sentences before a break

**Why this works**:
- Visual breathing room makes content scannable
- Short chunks are easier to process
- Readers can pause and reflect between ideas

**Application**:
- 3-5 sentences, then break
- One idea per paragraph when possible
- Line breaks create visual breathing room
- Long wall-of-text paragraphs signal "skip this"

**Examples**:

❌ **Too long** (wall of text):
```
The framework provides several benefits including improved code quality and better maintainability over time. When teams adopt this approach they often see reduced bug counts and faster feature delivery. However it's important to note that the initial setup requires some investment in training and tooling. Most teams report that this investment pays off within the first quarter of adoption. The key is to start small with a single service or component and expand from there as the team gains confidence and experience with the patterns.
```

✅ **Better** (broken up):
```
The framework improves code quality and maintainability. Teams typically see reduced bugs and faster feature delivery.

The initial setup requires training and tooling investment. Most teams report this pays off within the first quarter.

Start small: pick one service or component. Expand as the team gains confidence with the patterns.
```

---

## Quick Reference

**Scaffolding**: Unit → Topic → Subsection with clear headers  
**Questions**: Lead with question, follow with exploration  
**If/Then/Else**: Assumptions (if), logic (then), exceptions (else)  
**Lists**: Numbered for sequential, bullets for parallel  
**Paragraphs**: 3-5 sentences max, visual breathing room

---

**Last updated**: 2026-07-16  
**Source**: Extracted from fox-voice skill structural patterns
