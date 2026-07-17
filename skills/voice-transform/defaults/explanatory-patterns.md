# Explanatory Patterns

**Purpose**: Universal patterns for teaching "how to think" instead of just "what to do".

These patterns make reasoning visible, build transferable understanding, and enable readers to apply concepts independently.

---

## 1. Concrete Examples Over Abstractions

Abstract concept → grounded in relatable scenario

**Pattern**: Never explain abstractly what you can demonstrate concretely

**Why this works**:
- Abstract explanations require translation work
- Examples show the concept in action
- Readers can map examples to their own context

**Examples**:

❌ **Abstract only**:
```
Documentation quality varies based on multiple factors that influence readability and comprehension.
```

✅ **Concrete grounding**:
```
Think of docs like untying a knot. You can't give one set of instructions—depends on the material, how tight it is, whether it's been through a hedgerow. Same with docs: audience knowledge, technical depth, and how tangled the dependencies are all change how you explain it.
```

**Application**:
1. State the abstract principle briefly
2. Immediately ground in concrete example
3. Show it working in a real scenario
4. Let readers verify the concept themselves

---

## 2. Technical Metaphors for Laypeople

Bridge technical concepts to what readers already understand.

**Pattern**: Technical concept → metaphor from reader's existing knowledge

**Why this works**:
- Builds on existing mental models
- Makes unfamiliar concepts feel familiar
- Creates memorable hooks for complex ideas

**Metaphor types**:

**Technical metaphors** (for technical audiences):
- "It's like a key exchange—both sides establish and agree on the protocol"
- "Think of it as a scaffold: shows the structure, then gets removed"
- "Works like an index: fast lookups but slower writes"

**Everyday metaphors** (for general audiences):
- "Like organizing 200 issues on a repo by categorizing them: bug, feature, process"
- "Same as sorting mail: bills, personal, junk"
- "Works like a table of contents: jump to what you need"

**Application**:
- Match metaphor complexity to audience
- Use metaphors they already understand deeply
- Metaphor should clarify, not obscure

---

## 3. Meta-Commentary and Signposting

Guide the reader through your thinking process.

**Pattern**: Signal transitions, acknowledge complexity, prepare reader for what's next

**Why this works**:
- Prevents reader from getting lost in complexity
- Sets expectations for difficulty and length
- Creates conversational partnership

**Signposting phrases**:
- "Here's why this matters:"
- "Let me walk you through this:"
- "Stay with me—this gets clearer in a moment:"
- "This next part is tricky:"
- "Bear with me while we work through this:"

**When to use**:
- Introducing complex topics
- Transitioning between sections
- Before difficult concepts
- When reasoning is non-obvious

**Examples**:

❌ **No signposting** (reader gets lost):
```
The authentication flow checks credentials. JWT tokens expire after 24 hours. Refresh tokens enable re-authentication without password re-entry.
```

✅ **With signposting** (reader oriented):
```
Let me walk you through the authentication flow in three parts:

First, credential checking: we verify username and password against the database.

Second, token generation: you get a JWT that expires after 24 hours. This keeps sessions secure.

Third, refresh handling: when the JWT expires, a refresh token lets you re-authenticate without re-entering your password. Here's why that matters: you stay logged in across days without sacrificing security.
```

**Application**:
- Use sparingly (only when genuinely helpful)
- Don't over-explain obvious transitions
- Guide through complexity, not simple ideas

---

## 4. Reader Check-ins

Anticipate reader's state and address it.

**Pattern**: Predict reader reactions, validate them, then redirect

**Why this works**:
- Shows you understand their experience
- Validates confusion or frustration
- Builds trust before asking for effort

**Check-in phrases**:
- "You may find that... and that's totally okay"
- "Now you may go through this, and..."
- "If you're thinking [X], you're right to be concerned"
- "This might feel like [reaction]—it is, and here's why it's worth it anyway"

**Examples**:

❌ **No check-in** (ignores reader state):
```
Follow these five steps to configure the system.
```

✅ **With check-in** (acknowledges reality):
```
You may find that configuration takes longer than expected—that's normal. The first time through, expect 30 minutes. Once you've done it once, subsequent setups take 5 minutes.
```

**Application**:
- Anticipate where readers will struggle
- Validate their reaction before redirecting
- Address objections preemptively
- Normalize confusion before explaining

---

## 5. Transparent Process (Show the Scaffold)

Don't just give conclusions—show how you arrived there.

**Pattern**: Reasoning visible + framework reusable

**Why this works**:
- Teaches "how to think", not just "what to do"
- Readers can apply the framework elsewhere
- Builds independent problem-solving capability

**Example structure**:

❌ **Conclusion only** (not transferable):
```
We should use approach B.
```

✅ **Transparent process** (transferable framework):
```
Here's how I evaluated this:

**Problem**: We need to reduce API latency without breaking existing clients.

**Options considered**:
- A: Cache at the client (fast, but stale data risk)
- B: Cache at the edge (fast, fresh data, more complex)
- C: Optimize queries (slow to implement, no caching complexity)

**Decision factors**:
- Latency improvement: A=90%, B=85%, C=40%
- Data freshness: A=poor, B=good, C=excellent
- Implementation time: A=1 week, B=3 weeks, C=6 weeks

**Recommendation**: B (edge caching)
- Balances latency gains with data freshness
- Worth the extra 2 weeks vs option A
- Delivers 85% of the win in half the time of option C

**Tradeoffs**: Higher operational complexity, but we have the infra team to support it.
```

**Application**:
- Show your work, not just your answer
- Provide frameworks readers can apply elsewhere
- Make decision criteria explicit
- Reveal the "how to think" process

**Structure for complex decisions**:
1. Problem statement
2. Options considered (with tradeoffs)
3. Decision factors (what matters here)
4. Recommendation (with reasoning)
5. Tradeoffs acknowledged

---

## Quick Reference

**Concrete examples**: Abstract → specific scenario  
**Technical metaphors**: Unfamiliar → familiar concept  
**Meta-commentary**: Signal transitions, prepare for complexity  
**Reader check-ins**: Anticipate reactions, validate, redirect  
**Transparent process**: Show reasoning, provide reusable framework

---

## When to Apply Each Pattern

**Concrete Examples**:
- Any time you introduce an abstract concept
- When explaining "why" something matters
- When teaching a new framework or pattern

**Technical Metaphors**:
- Bridging knowledge gaps between experts and non-experts
- Making unfamiliar concepts feel familiar
- Creating memorable hooks for complex ideas

**Meta-Commentary**:
- Before complex topics
- At transition points between sections
- When reader might get lost

**Reader Check-ins**:
- Where readers typically struggle
- Before asking for significant effort
- When addressing common objections

**Transparent Process**:
- Complex decisions with multiple options
- Strategic recommendations
- Teaching frameworks for others to reuse

---

**Last updated**: 2026-07-16  
**Source**: Extracted from fox-voice skill explanatory patterns
