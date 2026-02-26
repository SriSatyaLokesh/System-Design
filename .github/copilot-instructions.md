# GitHub Copilot Instructions

## Project Overview

This is a **GSD Framework** (Goal → Spec → Deliver) repository containing educational content about AI tools and workflows. The primary deliverable is a curated learning pathway in `Agentic AI/` teaching users to work effectively with AI assistants, agents, and copilots.

**Key Principle:** This project uses the GSD methodology for structured planning and execution. All work follows a phase-based approach with explicit requirements, plans, and verification steps.

## Repository Structure

```
System-Design/
├── .gsd/                          # GSD Framework metadata (DO NOT edit directly without reading STATE.md first)
│   ├── PROJECT.md                 # Project brief and scope
│   ├── ROADMAP.md                 # Phase-based roadmap with requirements
│   ├── STATE.md                   # Current status - ALWAYS READ THIS FIRST
│   ├── REQUIREMENTS.md            # All requirements with traceability
│   ├── config.json                # Planning behavior (mode, depth, parallelization)
│   ├── phases/                    # Phase-specific plans, research, summaries
│   │   └── XX-phase-name/
│   │       ├── XX-YY-PLAN.md      # Executable plan with tasks
│   │       ├── XX-YY-SUMMARY.md   # Outcome summary post-execution
│   │       ├── XX-RESEARCH.md     # Discovery/research findings
│   │       └── XX-VERIFICATION.md # Goal-backward verification report
│   └── templates/                 # Document templates
├── .github/
│   ├── instructions/              # Reusable instruction files (checkpoints, git, TDD, etc.)
│   └── skills/                    # Specialized agent skills (execute-plan, verify-phase, etc.)
└── Agentic AI/                    # Learning content (numbered sections 01-06)
```

## Critical Workflows

### 1. Starting Any Work - READ STATE.md FIRST

**ALWAYS** read `.gsd/STATE.md` before making any changes:

```bash
# Check current phase, progress, blockers
cat .gsd/STATE.md
```

This tells you:
- Current phase and plan
- What's been completed
- Active blockers
- Next steps

### 2. Git Commit Strategy - Atomic Task Commits

**Core Principle:** Commit outcomes, not process. Each task gets its own commit immediately after completion.

**Commit Format:**
```
{type}({phase}-{plan}): {task-name}

- [Key change 1]
- [Key change 2]
- [Key change 3]
```

**Commit Types:**
- `feat` - New feature/functionality
- `fix` - Bug fix
- `docs` - Documentation/content creation
- `test` - Test-only changes
- `refactor` - Code cleanup
- `chore` - Dependencies, config, tooling

**Example:**
```bash
# Task completion commit
git add "Agentic AI/01-ecosystem/README.md"
git commit -m "docs(02-01): create AI ecosystem taxonomy

- Added AI assistants, agents, copilots definitions with examples
- Created comparison framework with 6 dimensions
- Added decision matrix for chat vs repo AI"

# Plan completion metadata commit (after all tasks done)
git add .gsd/phases/02-foundational-learning-content/02-01-SUMMARY.md .gsd/STATE.md .gsd/ROADMAP.md
git commit -m "docs(02-01): complete ecosystem content plan

Tasks completed: 3/3
- Create unified AI taxonomy
- Build comparison framework 
- Curate resources with context

SUMMARY: .gsd/phases/02-foundational-learning-content/02-01-SUMMARY.md"
```

**What NOT to commit:**
- Intermediate PLAN.md creation (commit with plan completion)
- RESEARCH.md during creation (commit with plan)
- Minor planning tweaks
- "Fixed typo" without task context

See [.github/instructions/git-integration.instructions.md](.github/instructions/git-integration.instructions.md) for full details.

### 3. Content Creation Pattern

When creating educational content in `Agentic AI/`:

1. **Structure:** Use hierarchical headings (##, ###, ####) with clear section markers
2. **Length:** Content is typically substantial (500-2000 lines per section)
3. **Format:** Markdown with:
   - Code blocks with language specifiers
   - Comparison tables
   - Bulleted lists for clarity
   - Emoji sparingly for visual markers (✅, ⚠️, 💡)
4. **Curation:** 5-7 resources maximum per topic with context (what, why, when)
5. **Examples:** Always include concrete examples (specific tools, real commands, actual workflows)

Example pattern from existing content:
```markdown
## Tool Category

**What:** [Definition in 1-2 sentences]

**Key Characteristics:**
- Point 1
- Point 2
- Point 3

**Examples:**
- **Product A** - [Specific use case]
- **Product B** - [Specific use case]

**When to Use:**
[Scenario-based guidance]

**Comparison Table:**
| Dimension | Option 1 | Option 2 |
|-----------|----------|----------|
| ...       | ...      | ...      |
```

### 4. Phase Execution Workflow

Phases follow this lifecycle:

1. **Research** → Creates `XX-RESEARCH.md` with discovery findings
2. **Planning** → Creates `XX-YY-PLAN.md` with executable tasks
3. **Execution** → Execute tasks, commit per task
4. **Summary** → Create `XX-YY-SUMMARY.md` after plan completion
5. **Verification** → Create `XX-VERIFICATION.md` checking goal achievement

**Plan Structure (`PLAN.md`):**
- Frontmatter with metadata (phase, plan, wave, dependencies, must_haves)
- `<objective>` - What and why
- `<context>` - Files to reference
- `<tasks>` - Executable task list with clear actions

**Verification Pattern:**
- Goal-backward analysis (does codebase achieve phase goal?)
- 3-level artifact check: Existence → Substantive → Wired
- Truth verification (can learner achieve stated outcomes?)
- Gap identification (what's missing or incorrect)

See [.github/skills/execute-plan/SKILL.md](.github/skills/execute-plan/SKILL.md) and [.github/skills/verify-phase/SKILL.md](.github/skills/verify-phase/SKILL.md).

## Configuration

### Mode Settings (`.gsd/config.json`)

```json
{
  "mode": "yolo",              // brave | yolo | safe
  "depth": "quick",            // quick | standard | deep
  "parallelization": true,     // Execute plans in parallel waves
  "commit_docs": true,         // Commit docs files
  "model_profile": "balanced"  // quality | balanced | budget
}
```

**Current Project:** yolo mode + quick depth = fast iteration with minimal checkpoints

## Project-Specific Conventions

### Content Quality Standards

- **Curation over comprehensiveness:** 5-7 resources max per topic (avoid "everything trap")
- **Context required:** Every resource link needs "what, why, when" annotation
- **Concrete over abstract:** Real product names, specific commands, actual file paths
- **Progressive complexity:** Beginner-friendly explanations first, advanced concepts later
- **Mobile-friendly:** Markdown-native formatting (renders on GitHub mobile)

### File Naming

- Phases: `XX-descriptive-name/` (01-foundation-structure)
- Plans: `XX-YY-PLAN.md` (phase-plan numbering)
- Summaries: `XX-YY-SUMMARY.md`
- Phase-level docs: `XX-RESEARCH.md`, `XX-VERIFICATION.md`

### Cross-References

Use relative paths for internal links:
```markdown
[→ Explore Tools](02-tools/README.md)
[@.gsd/PROJECT.md](.gsd/PROJECT.md)
```

## Common Anti-Patterns to Avoid

- ❌ Editing `.gsd/STATE.md` without reading it first
- ❌ Creating stub content (always provide substantive implementation)
- ❌ Generic advice without specific examples
- ❌ Resource dumps (30+ links with no context)
- ❌ Committing "WIP" or intermediate planning docs
- ❌ Batch committing multiple completed tasks (1 task = 1 commit)
- ❌ Changing requirements without updating ROADMAP.md

## Key Files to Reference

**Before any work:**
- [.gsd/STATE.md](.gsd/STATE.md) - Current status and blockers
- [.gsd/PROJECT.md](.gsd/PROJECT.md) - Project scope and constraints

**For implementation patterns:**
- [Agentic AI/01-ecosystem/README.md](Agentic AI/01-ecosystem/README.md) - Example of comparison framework
- [Agentic AI/02-tools/README.md](Agentic AI/02-tools/README.md) - Example of tool guides with exercises

**For process guidance:**
- [.github/instructions/git-integration.instructions.md](.github/instructions/git-integration.instructions.md) - Commit strategy
- [.github/instructions/verification-patterns.instructions.md](.github/instructions/verification-patterns.instructions.md) - Quality checks
- [.github/skills/execute-plan/SKILL.md](.github/skills/execute-plan/SKILL.md) - Plan execution workflow

## Quick Reference

**Check project status:**
```bash
cat .gsd/STATE.md
```

**See current phase requirements:**
```bash
cat .gsd/ROADMAP.md
```

**Find active plan:**
```bash
ls .gsd/phases/XX-current-phase/
```

**Verify content quality:**
```bash
wc -l "Agentic AI/XX-section/README.md"  # Should be substantial (500+ lines)
```
