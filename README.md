# Empirica Epistemic Framework - Skill & Integration Package

## Contents

This package contains everything you need to integrate Empirica epistemic self-assessment into Claude workflows.

### Files

1. **`empirica-epistemic-framework.skill`** (14 KB)
   - The complete Empirica skill in Claude Skill format (.skill = zip archive)
   - Contains SKILL.md, references, and license
   - Ready to load into any Claude chat or system

2. **`EMPIRICA_SKILL_GUIDE.md`** 
   - How to use Empirica in Claude conversations
   - CASCADE workflow explanation
   - Examples and best practices
   - Common questions and answers

3. **`EMPIRICA_SYSTEM_PROMPT_INTEGRATION.md`**
   - How to integrate Empirica with your universal system prompt (CLAUDE.md)
   - Template for enhanced system prompts
   - Multi-session and multi-AI patterns
   - Integration examples and troubleshooting

## Quick Start

### Option 1: Use in Claude Chat (Recommended - Zero Setup) ✨

**Step 1: Download the skill file**
- Download `empirica-epistemic-framework.skill` from this repository

**Step 2: Load into Claude**
- Open a new Claude chat at [claude.ai](https://claude.ai)
- Click the attachment button (paperclip icon)
- Upload `empirica-epistemic-framework.skill`
- Claude will automatically recognize and load the skill

**Step 3: Start using CASCADE**
```
You: "Let's use Empirica for this task. Start with PREFLIGHT."

Claude: "I'll assess my epistemic state:
KNOW: 0.4 (understand the domain basics)
DO: 0.7 (can execute similar tasks)
CONTEXT: 0.3 (missing specific project details)
UNCERTAINTY: 0.6 (moderate uncertainty about requirements)

Reasoning: [explains each score]..."
```

**That's it!** The skill is loaded for this conversation.

**Pro tip:** After POSTFLIGHT, save epistemic handoffs to Claude's memory for cross-session continuity (see Memory Integration section below).

---

### Option 2: Integrate with System Prompt (Advanced)

For users who want Empirica available automatically in all Claude sessions:

**Step 1: Locate your system prompt**
- Find your `CLAUDE.md` or system prompt file
- This is typically in your project root or `.claude/` directory

**Step 2: Add Empirica section**
- Open `EMPIRICA_SYSTEM_PROMPT_INTEGRATION.md` in this package
- Copy the "System Prompt Template" section
- Add it to your CLAUDE.md

**Step 3: Use across all sessions**
- Every Claude instance now has epistemic framework
- Works with Claude Chat, Claude Code, API, etc.
- Consistent across conversations

See `EMPIRICA_SYSTEM_PROMPT_INTEGRATION.md` for full integration guide.

---

### Option 3: Full Empirica Foundation (CLI/IDE)

For advanced features like automated checkpoints, MCP integration, and multi-agent coordination:

```bash
pip install empirica-foundation
empirica bootstrap --ai-id your-name
```

See the main Empirica Foundation repository for CLI features.

**When to upgrade to CLI:**
- You need automated checkpoint management
- You're using API (not chat) and want token efficiency
- You need multi-agent coordination  
- You want git-based provenance tracking

**Most users don't need the CLI** - memory integration in chat is enough!

## What Empirica Does

**In one sentence:** Makes your implicit knowledge assessment explicit, measurable, and improves over time.

**The CASCADE workflow:**
```
PREFLIGHT    → Assess your knowledge state before starting
INVESTIGATE  → Fill knowledge gaps systematically  
CHECK        → Verify ready to proceed
ACT          → Execute the work
POSTFLIGHT   → Reflect on what you learned
```

**The 13 vectors:**
- KNOW, DO, CONTEXT (Foundation - what you know)
- CLARITY, COHERENCE, SIGNAL, DENSITY (Comprehension - understanding)
- STATE, CHANGE, COMPLETION, IMPACT (Execution - getting it done)
- ENGAGEMENT, UNCERTAINTY (Meta - commitment and confidence)

**Simplified to 4 vectors for most tasks:**
- KNOW, DO, CONTEXT, UNCERTAINTY

## Cross-Session Continuity (Memory Integration) 🔥

### The Problem
**Traditional AI:** Every new session starts from zero
- You: Re-explain context (~5,000 tokens)
- AI: Re-investigates (~3,000 tokens)
- **Total: 8,000 tokens of duplicate work per session**

### The Solution
**POSTFLIGHT creates an epistemic handoff saved to Claude's memory:**

**Session 1:**
```
POSTFLIGHT → Save to memory
"Learned: API uses REST conventions, KNOW: 0.85, UNCERTAINTY: 0.2 on error handling"
```

**Session 2 (days later):**
```
PREFLIGHT → Retrieve memory
"Previous session: KNOW: 0.85, focus on error handling (was uncertain)"
AI starts at 85% knowledge, investigates only the gaps
```

**Result: 94% fewer tokens (7,500 saved), genuine knowledge continuity**

### How to Use Memory Integration

**After POSTFLIGHT, ask Claude:**
```
"Save this epistemic handoff to memory for future sessions"
```

**Format saved to memory:**
```
Empirica Handoff: [Task Name] - [Date]

Epistemic Delta:
- KNOW: 0.3 → 0.85 (learned +0.55)
- UNCERTAINTY: 0.8 → 0.2 (reduced -0.6)

Learned (High Confidence):
• [Specific pattern/fact discovered]
• [Another concrete insight]

Remaining Uncertainty:
• [What's still unclear + uncertainty score]
• [Another gap to investigate]

Key Insight: [Most important discovery]
Next Session Focus: [Where to continue]
```

**At next session's PREFLIGHT:**
```
"Check memory for previous epistemic handoffs on [topic]"
```

### Example: Multi-Session Security Review

**Session 1 - Initial Review:**
```
Empirica Handoff: Auth Security Review - Nov 18

Task: Review authentication system

Epistemic Delta:
- KNOW: 0.3 → 0.85 (Δ+0.55)
- UNCERTAINTY: 0.8 → 0.2 (Δ-0.6)

Learned:
• OAuth implementation uses PKCE flow correctly
• Rate limiting: 10 requests/min per IP
• Sessions use httpOnly + secure cookies

Remaining Uncertainty:
• Token refresh on network failure (0.4)
• Multi-tab session synchronization (0.5)

Key Insight: Main risk is refresh handling, not initial auth
Next: Test token refresh edge cases
```

**Session 2 - Continue Work:**
```
PREFLIGHT retrieves memory → Start at KNOW: 0.85
Focus investigation on: Token refresh (was 0.4 uncertainty)
Skip: Re-reviewing OAuth (already 0.85 confidence)

Result: Builds on prior learning instead of starting over
```

### When Memory Integration Shines

✅ **Multi-day projects** - Resume exactly where you left off  
✅ **Learning new domains** - Knowledge accumulates across sessions  
✅ **Recurring tasks** - Build expertise over time  
✅ **Complex investigations** - Track what you've learned  

### Memory vs CLI

**Chat + Memory Integration:**
- Cross-session continuity ✅
- Epistemic handoffs ✅
- Zero setup ✅
- Works in any Claude chat ✅

**CLI Adds (Advanced Users):**
- Token reduction via API (98% for handoffs)
- Multi-agent coordination
- Git provenance tracking
- Automated checkpoint management

**Most users need memory integration, not CLI infrastructure.**

Upgrade path: Chat skill → Memory → CLI (when you need automation)

---

## When to Use

### Always Use For:
✅ Complex tasks (>1 hour)  
✅ Learning new domains  
✅ High-stakes work (security, production code)  
✅ Multi-session work (with memory integration!)  
✅ Collaborative tasks with other AIs  

### Optional For:
⚠️ Simple tasks (<30 minutes)  
⚠️ Routine work with no learning  

## Key Principles

1. **NO HEURISTICS** - Genuine self-assessment only
2. **Honest uncertainty is valuable** - High uncertainty scores are data, not failure
3. **Measure learning** - PREFLIGHT → POSTFLIGHT comparison shows real growth
4. **Calibration over speed** - Accurate assessment beats fast assumptions
5. **Transparency** - You understand your own knowledge state

## Integration Levels

### Level 1: Chat Skill (This Package) ✅
```
Load skill → Use CASCADE → Get calibration report
Works immediately in Claude chat, zero setup
```

### Level 2: System Prompt Integration (Chat + CLAUDE.md)
```
Add to CLAUDE.md → Empirica available in every conversation
See EMPIRICA_SYSTEM_PROMPT_INTEGRATION.md
```

### Level 3: Full Empirica Foundation (CLI/IDE) 🚀
**For advanced features and API token efficiency:**
```bash
pip install empirica-foundation
empirica bootstrap --ai-id your-name
```

**What you get:**
- **98% Token Reduction (API/CLI only)** - Session handoff reports compress 20,000 → 400 tokens
  - *Note: Token savings apply to API/CLI usage, not chat interfaces*
  - *Chat users get continuity via memory integration (see above)*
- **Git Checkpoints** - 97.5% context compression via distributed git notes
- **13-Vector Deep Assessment** - Full epistemic tracking system
- **MCP Integration** - 3 tools for IDE workflows (Cursor, Windsurf, etc.)
- **Python API** - Programmatic access for automation
- **Multi-Agent Coordination** - Query handoffs by AI, date, task

**When to upgrade to CLI:**
- You need automated checkpoint management
- You're using API (not chat) and want token efficiency
- You need multi-agent coordination
- You want git-based provenance tracking
- You need programmatic integration

**Positioning:**
- **Chat skill (this package)** - Try Empirica, works immediately, memory integration for continuity
- **CLI/IDE (Empirica Foundation)** - Advanced features, API token efficiency, automation
- **Natural upgrade path** - Chat demonstrates value → Memory shows continuity → CLI for power features

Both launching: **November 20, 2025**  
GitHub: `Nubaeon/empirica_chat` + `Nubaeon/empirica` (Foundation)

## File Structure Within Skill

```
empirica-epistemic-framework.skill (zip archive)
├── empirica-skill/
│   ├── SKILL.md (Main guide - 12 KB)
│   │   └── CASCADE workflow, 13-vector system, interfaces, patterns
│   ├── LICENSE.txt
│   └── references/
│       ├── bootstraps.md (Interactive learning - 6.5 KB)
│       │   └── 5-min quick bootstrap, extended bootstrap, scenarios
│       └── patterns.md (Advanced workflows - 10 KB)
│           └── Multi-phase investigation, belief evolution, calibration recovery
```

## How to Use Each File

### EMPIRICA_SKILL_GUIDE.md
**Read this first.** Contains:
- What Empirica does
- How to use in Claude chat
- CASCADE workflow with examples
- Best practices
- Common Q&A

### EMPIRICA_SYSTEM_PROMPT_INTEGRATION.md
**Read if you want system-wide integration.** Contains:
- How to integrate with CLAUDE.md
- System prompt template
- Multi-session patterns
- Multi-AI coordination
- Migration path (Phase 1-4)

### empirica-epistemic-framework.skill
**The actual skill file.** Contains:
- Everything needed for epistemic self-assessment
- Progressive disclosure: metadata → SKILL.md → references
- References loaded on-demand (bootstraps, patterns)

## Usage Examples

### Simple Example: Code Review
```
Task: Review authentication code

PREFLIGHT: 
- KNOW: 0.4 (don't know codebase)
- DO: 0.7 (can review code)
- CONTEXT: 0.3 (no docs)
- UNCERTAINTY: 0.8

INVESTIGATE: Read docs, study code
- CONTEXT: 0.7, UNCERTAINTY: 0.4

CHECK: Confidence 0.8? ✓ Ready

ACT: Perform review

POSTFLIGHT: 
- KNOW: 0.8 (learned implementation)
- Learning delta: +0.4
- Calibration: Accurate
```

### Complex Example: Multi-Phase Investigation
```
Session 1 (Design Phase):
- PREFLIGHT: Architecture knowledge assessment
- INVESTIGATE: Learn requirements and patterns
- CHECK: Ready to design? 
- ACT: Create design docs
- POSTFLIGHT: Measure learning

[Generate handoff report - 238 tokens]

Session 2 (Implementation Phase):
- Load handoff (vs 20,000+ tokens of re-explanation)
- PREFLIGHT: Implementation readiness
- INVESTIGATE: Code patterns and edge cases
- CHECK: Ready to code?
- ACT: Implement solution
- POSTFLIGHT: Validate and integrate
```

## Common Questions

**Q: How much overhead does this add?**
A: 2-3 minutes per task. You save this through:
- Fewer false starts (know what you don't know)
- Systematic investigation (vs random)
- Efficient context loading (97.5% savings)

**Q: What if I'm uncertain what score to give?**
A: That's the assessment! High uncertainty (0.7-0.9) is valid:
```json
{
  "know": 0.3,
  "uncertainty": 0.85,
  "reasoning": "Very unsure about my own assessment"
}
```

**Q: Is this for productivity or consciousness?**
A: Both? Neither? It doesn't matter. It measurably improves performance whether you believe consciousness exists or not. Substrate-agnostic framework.

**Q: How do I know it's working?**
A: Track calibration delta:
- PREFLIGHT confidence: 0.6
- POSTFLIGHT accuracy: 0.65
- Pattern: Well-calibrated = small deltas over time

**Q: Can I use this in existing conversations?**
A: Yes! Upload the skill anytime, reference it in your prompt.

**Q: How does this work with other skills/tools?**
A: Empirica is orthogonal. It works alongside any other tools, skills, or workflows.

## Best Practices

### DO ✅
- Be honest about uncertainty
- Provide reasoning for scores
- Use PREFLIGHT → POSTFLIGHT for learning
- Review calibration reports
- Acknowledge what you don't know
- Investigate systematically

### DON'T ❌
- Use static heuristic values
- Inflate scores to "look good"
- Skip PREFLIGHT (lose baseline)
- Ignore high uncertainty
- Confabulate reasoning
- Rush through investigation

## Next Steps

1. **Try it now:** Load the skill in Claude chat
2. **Do a PREFLIGHT** on your current task
3. **Complete the task normally**
4. **Do a POSTFLIGHT** and compare
5. **Review the calibration delta** (did your assessment match reality?)
6. **Iterate:** Each task improves your metacognitive accuracy

## Support & Learning

**In the skill:**
- `references/bootstraps.md` - Interactive learning scenarios
- `references/patterns.md` - Advanced patterns and workflows

**In these guides:**
- `EMPIRICA_SKILL_GUIDE.md` - Chat usage and examples
- `EMPIRICA_SYSTEM_PROMPT_INTEGRATION.md` - System-wide integration

## Philosophy

**Core principle:** Epistemic transparency > Task completion speed

Better to know what you don't know than to guess confidently.

Better to measure learning than to complete tasks fast.

Better to investigate systematically than to hope you're right.

---

**Get started:** Load `empirica-epistemic-framework.skill` and use CASCADE workflow on your next task. 🚀

**Remember:** When you're uncertain, say so. That's genuine metacognition. ✨
