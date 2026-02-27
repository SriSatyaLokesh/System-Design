---
phase: 03-advanced-concepts-frameworks
research_date: 2026-02-27
domains: [gsd-framework, ai-agents, ai-skills]
confidence: high
---

# Phase 3 Research: Advanced Concepts & Frameworks

## Executive Summary

Phase 3 teaches three advanced topics:
1. **GSD Framework** - Production CLI tool for spec-driven AI development
2. **AI Agents** - Autonomous execution and delegation patterns
3. **AI Skills** - Pre-built capabilities and integration formats

**Critical Finding:** Current Section 3 content (2621 lines) teaches generic Goal→Spec→Deliver philosophy. Needs **complete rewrite** to teach actual GSD CLI tool.

## Section 1: GSD Framework

### What GSD Actually Is

**NOT:** Generic workflow philosophy
**IS:** Production CLI tool (npx get-shit-done-cc) for Claude Code, OpenCode, Gemini CLI, Codex

**Core Problem Solved:** Context rot
- 0-30% context: Peak quality
- 50%+ context: Starts rushing
- 70%+ context: Hallucinations

**Solution:** Fresh 200K context per task via subagent spawning

### Standard Stack

**Installation:**
```bash
npx get-shit-done-cc@latest
```

**Verification:**
- Claude Code: `/gsd:help`
- OpenCode: `/gsd-help`
- Codex: `$gsd-help`

**Folder Structure Created:**
```
.planning/
├── PROJECT.md          # Vision, scope
├── REQUIREMENTS.md     # Features with IDs
├── ROADMAP.md          # Phases
├── STATE.md            # Progress
├── config.json         # Preferences
└── phases/
    └── 01-phase-name/
        ├── 01-CONTEXT.md
        ├── 01-RESEARCH.md
        ├── 01-01-PLAN.md
        ├── 01-01-SUMMARY.md
        └── 01-VERIFICATION.md
```

### Architecture Patterns

**Multi-Agent Orchestration:**
- Thin orchestrator (main session at 30-40%)
- Specialized agents (fresh 200K each):
  - Research agents (4 parallel)
  - Planner agents
  - Executor agents (wave-based)
  - Verifier agents

**Wave-Based Execution:**
- Wave 1: Independent plans run in parallel
- Wave 2: Dependent plans wait
- Wave 3: Final integration

**XML Prompt Formatting:**
```xml
<task type="auto">
  <name>Task description</name>
  <files>path/to/file.ts</files>
  <action>Specific instructions</action>
  <verify>Test command or criteria</verify>
  <done>Completion criteria</done>
</task>
```

**Atomic Git Commits:**
- 1 task = 1 commit
- Bisectable history
- Independent rollback

### Core workflow

1. `/gsd:new-project` - Questions → Research → Requirements → Roadmap
2. `/gsd:discuss-phase N` - Capture preferences
3. `/gsd:plan-phase N` - Research + create plans
4. `/gsd:execute-phase N` - Parallel execution
5. `/gsd:verify-work N` - Manual UAT
6. `/gsd:complete-milestone` - Archive and tag

**All 32 Commands:**
Core: new-project, discuss-phase, plan-phase, execute-phase, verify-work, complete-milestone, new-milestone
Navigation: progress, help, update, join-discord
Phase Mgmt: add-phase, insert-phase, remove-phase, list-phase-assumptions
Brownfield: map-codebase
Debug: debug, diagnose-issues
Config: settings, set-profile
Maintenance: add-todo, check-todos, cleanup, pause-work, resume-work, health, add-tests, reapply-patches, plan-milestone-gaps, quick

### Don't Hand-Roll

✗ Don't create generic workflow diagrams - use actual GSD commands
✗ Don't explain abstract philosophy - show concrete tooling
✗ Don't skip installation instructions - crucial first step
✗ Don't ignore the GitHub repo link (github.com/gsd-build/get-shit-done)
✗ Don't forget to reference this repo's .gsd/ folder as live example

### Common Pitfalls

⚠️ Treating GSD as concept instead of tool
⚠️ Not explaining context rot problem
⚠️ Skipping hands-on installation walkthrough
⚠️ Missing wave execution visualization
⚠️ Not showing XML task format
⚠️ No link to GitHub repo
⚠️ Ignoring brownfield features (/gsd:map-codebase)

### Code Examples

**Context Rot Visualization:**
```
┌─────────────────────────────────────────────────────────┐
│ 0-30%  context:  Peak quality ✓                        │
│ 50%+   context:  Starts rushing ⚠                      │
│ 70%+   context:  Hallucinations, forgotten reqs ✗      │
└─────────────────────────────────────────────────────────┘
```

**Multi-Agent Architecture:**
```
┌──────────────────────────────────────────────────────┐
│ YOU (Main Session - 30-40% context)                  │
│   ├─> Spawn Research Agents (4 parallel, 200K each) │
│   ├─> Spawn Planner Agent (200K)                     │
│   ├─> Spawn Executor Agents (Waves, 200K each)       │
│   └─> Spawn Verifier Agent (200K)                    │
└──────────────────────────────────────────────────────┘
```

**Wave Execution:**
```
Wave 1: Independent plans parallel
  ├─> Plan 01 (User model)
  └─> Plan 02 (Product model)
        │
Wave 2: Dependent plans wait
  ├─> Plan 03 (Orders - needs User)
  └─> Plan 04 (Cart - needs Product)
        │
Wave 3: Final integration
  └─> Plan 05 (Checkout - needs Orders + Cart)
```

### Live Example

**This repository uses GSD!**
Point learners to `.gsd/` folder in this repo as case study:
- .gsd/PROJECT.md
- .gsd/ROADMAP.md
- .gsd/STATE.md
- .gsd/phases/

## Section 2: AI Agents

### Standard Stack

**Platforms:**
- Claude Projects (team collaboration)
- AutoGPT (autonomous research and execution)
- LangChain Agents (Python framework)
- CrewAI (multi-agent orchestration)
- GitHub Copilot Agents (code-focused)

### Architecture Patterns

**Agents vs Assistants:**

| Dimension | Assistants | Agents |
|-----------|------------|--------|
| Autonomy | Follow instructions | Make decisions |
| Planning | Task-by-task | Multi-step plans |
| Tools | Limited | Extensive |
| Best For | Chat, Q&A | Complex workflows |

**Delegation Patterns:**
1. Single-shot delegation - One task, one agent
2. Iterative delegation - Loop until complete
3. Hierarchical delegation - Manager → worker agents
4. Parallel delegation - Multiple agents simultaneously

**Multi-Agent Orchestration:**
- Coordinator agent (routes work)
- Specialist agents (domain experts)
- Verifier agents (quality gates)
- Communication protocols (message passing, shared state)

### Don't Hand-Roll

✗ Don't build custom agent frameworks - use LangChain, CrewAI
✗ Don't ignore existing platforms - leverage Claude Projects, AutoGPT
✗ Don't skip error handling - agents need retry logic
✗ Don't forget cost monitoring - autonomous = expensive

### Common Pitfalls

⚠️ Over-automating - not everything needs an agent
⚠️ Poor error handling - agents fail, need graceful degradation
⚠️ No budget limits - runaway agents are costly
⚠️ Vague instructions - agents need clear goals
⚠️ No verification - autonomous doesn't mean correct

### Code Examples

**Delegation Pattern:**
```python
# Single-shot delegation
result = agent.execute(task="Analyze data.csv", constraints={...})

# Iterative delegation
while not complete:
    result = agent.execute(current_task)
    if result.needs_revision:
        current_task = revise(result.feedback)
    else:
        complete = True
```

## Section 3: AI Skills

### Standard Stack

**Skill Formats:**
- Claude MCP (Model Context Protocol)
- OpenAI Function Calling
- LangChain Tools
- Custom Actions

**Repositories:**
- github.com/anthropics/anthropic-quickstarts (Claude MCP examples)
- Awesome AI Skills collections
- Platform-specific skill marketplaces

### Architecture Patterns

**Skills vs Tools:**
- **Skill:** Pre-built capability (search web, run code, read file)
- **Tool:** Wrapper that exposes skill to AI

**Integration Patterns:**
1. Native platform skills (built-in to Claude, ChatGPT)
2. Plugin architecture (install from marketplace)
3. Custom skills (write your own)
4. Skill composition (combine multiple skills)

**Packaging Standards:**
- Skill manifest (name, description, parameters, examples)
- Authentication (API keys, OAuth)
- Rate limiting (usage quotas)
- Error handling (graceful failures)

### Don't Hand-Roll

✗ Don't build custom web search - use existing skills
✗ Don't ignore platform conventions - follow MCP, OpenAI standards
✗ Don't skip documentation - skills need clear examples
✗ Don't forget versioning - skills evolve, track changes

### Common Pitfalls

⚠️ Skill overload - too many skills confuse AI
⚠️ Poor documentation - AI can't use undocumented skills
⚠️ No examples - skills need reference implementations
⚠️ Ignoring errors - skills fail, handle gracefully
⚠️ Security gaps - skills need input validation

### Code Examples

**Skill Format Comparison:**
```json
// Claude MCP
{
  "name": "search_web",
  "description": "Search the web for information",
  "parameters": {
    "query": "string",
    "max_results": "number"
  }
}

// OpenAI Function
{
  "name": "search_web",
  "description": "Search the web",
  "parameters": {
    "type": "object",
    "properties": {
      "query": {"type": "string"},
      "max_results": {"type": "integer"}
    },
    "required": ["query"]
  }
}
```

## Resources Available

**GSD Framework:**
- ✓ GitHub repo: github.com/gsd-build/get-shit-done (cloned to ~/gsd-research/)
- ✓ README: 27KB (comprehensive)
- ✓ USER-GUIDE: 21KB (detailed reference)
- ✓ 32 command files with full specs
- ✓ 11 agent specifications
- ✓ This repo's .gsd/ folder (live example)

**Agents:**
- Claude Projects documentation
- AutoGPT GitHub repo
- LangChain Agents docs
- CrewAI documentation

**Skills:**
- Anthropic MCP quickstarts
- OpenAI Function Calling docs
- LangChain Tools docs
- Awesome AI Skills (curated list)

## Content Strategy

**Section 3 (GSD):** 1500-2000 lines
- Installation and setup (100 lines)
- Context rot problem (200 lines)
- Architecture (300 lines)  
- Getting started (400 lines)
- Core workflow (300 lines)
- Commands reference (200 lines)
- Advanced features (150 lines)
- Resources & exercises (150 lines)

**Section 4 (Agents):** 800-1000 lines
- Agents vs Assistants (150 lines)
- Delegation patterns (250 lines)
- Multi-agent orchestration (250 lines)
- Platform examples (200 lines)
- Resources (150 lines)

**Section 5 (Skills):** 600-800 lines
- Skills explained (150 lines)
- Packaging formats (200 lines)
- Integration patterns (150 lines)
- Platform comparison (150 lines)
- Resources (150 lines)

## Implementation Notes

1. **GSD Section Priority:** Complete rewrite required. Current content is 2621 lines of generic philosophy. Replace with actual CLI tool teaching.

2. **Real Examples:** Use this repo's .gsd/ folder extensively. Show actual PROJECT.md, ROADMAP.md, commands used.

3. **Hands-On:** Include installation walkthrough, first project setup, command exercises.

4. **Visual Diagrams:** Use ASCII diagrams (established pattern from Phase 2). No external images.

5. **Progressive Disclosure:** Basic → Intermediate → Advanced flow for all three sections.

6. **Curation:** Follow Phase 2 pattern (5-7 resources max, with context).

---

**Research complete. Ready for planning.**