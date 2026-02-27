# GSD Framework Research Summary

**Research Date:** 2026-02-27
**Repository:** https://github.com/gsd-build/get-shit-done  
**Cloned to:** ~/gsd-research/

## Executive Summary

The GSD (Get Shit Done) Framework is a **production-grade CLI tool** for Claude Code, OpenCode, Gemini CLI, and Codex that solves context rot through fresh subagent spawning and multi-agent orchestration. It is NOT a generic workflow philosophy - it's specific tooling with 32 commands that create structured .planning/ folders.

## Core Problem Solved: Context Rot

Claude's quality degrades as context fills:
- **0-30% context:** Peak quality, thorough, comprehensive
- **50%+ context:** Starts rushing, cuts corners  
- **70%+ context:** Hallucinations, forgotten requirements

GSD Solution: Each task gets a fresh 200K context window. Task 50 has same quality as Task 1.

## Architecture

### Multi-Agent Orchestration
- **Thin orchestrator** (main session at 30-40%)
- **Specialized agents** (fresh 200K each):
  - Research agents (4 parallel)
  - Planner agents
  - Executor agents (wave-based)
  - Verifier agents

### Wave-Based Execution
Plans grouped by dependencies:
- **Wave 1:** Independent tasks run in parallel
- **Wave 2:** Tasks depending on Wave 1
- **Wave 3:** Final integration

### XML Prompt Formatting
Structured tasks with built-in verification:
\\\xml
<task type=\"auto\">
  <name>Create login endpoint</name>
  <files>src/app/api/auth/login/route.ts</files>
  <action>Use jose for JWT. Validate credentials. Return httpOnly cookie.</action>
  <verify>curl POST localhost:3000/api/auth/login returns 200</verify>
  <done>Valid creds return cookie, invalid return 401</done>
</task>
\\\

## Installation

\\\ash
# Interactive
npx get-shit-done-cc@latest

# Non-interactive
npx get-shit-done-cc --claude --global
npx get-shit-done-cc --opencode --local
\\\

Verify: \/gsd:help\ in Claude Code

## Core Workflow

1. **\/gsd:new-project\** - Initialize project
   - Questions → Research → Requirements → Roadmap
   - Creates: PROJECT.md, REQUIREMENTS.md, ROADMAP.md, STATE.md

2. **\/gsd:discuss-phase N\** - Capture preferences
   - Lock in implementation decisions
   - Creates: {phase}-CONTEXT.md

3. **\/gsd:plan-phase N\** - Research and plan
   - Parallel research (stack, features, arch, pitfalls)
   - Create atomic task plans
   - Creates: {phase}-RESEARCH.md, {phase}-{N}-PLAN.md

4. **\/gsd:execute-phase N\** - Execute plans
   - Wave-based parallel execution
   - Fresh context per plan
   - Atomic git commits (1 task = 1 commit)
   - Creates: {phase}-{N}-SUMMARY.md, {phase}-VERIFICATION.md

5. **\/gsd:verify-work N\** - Manual UAT
   - Interactive testing
   - Auto-diagnosis of failures
   - Creates: {phase}-UAT.md, fix plans if needed

6. **\/gsd:complete-milestone\** - Archive and tag

## Folder Structure

\\\
.planning/
├── PROJECT.md          # Vision, scope, constraints
├── REQUIREMENTS.md     # Features with traceable IDs
├── ROADMAP.md          # Phases with success criteria
├── STATE.md            # Current progress, blockers
├── config.json         # Mode, depth, parallelization
└── phases/
    └── 01-foundation/
        ├── 01-CONTEXT.md       # Your decisions
        ├── 01-RESEARCH.md      # How to implement
        ├── 01-01-PLAN.md       # Executable tasks
        ├── 01-01-SUMMARY.md    # What was built
        └── 01-VERIFICATION.md  # Goal achievement check
\\\

## All 32 Commands

### Core Workflow
- /gsd:new-project
- /gsd:discuss-phase
- /gsd:plan-phase
- /gsd:execute-phase
- /gsd:verify-work
- /gsd:audit-milestone
- /gsd:complete-milestone
- /gsd:new-milestone

### Navigation
- /gsd:progress
- /gsd:help
- /gsd:update
- /gsd:join-discord

### Phase Management
- /gsd:add-phase
- /gsd:insert-phase
- /gsd:remove-phase
- /gsd:list-phase-assumptions

### Brownfield
- /gsd:map-codebase

### Debugging
- /gsd:debug
- /gsd:diagnose-issues

### Configuration
- /gsd:settings
- /gsd:set-profile

### Maintenance
- /gsd:add-todo
- /gsd:check-todos
- /gsd:cleanup
- /gsd:pause-work
- /gsd:resume-work
- /gsd:health
- /gsd:add-tests
- /gsd:reapply-patches
- /gsd:plan-milestone-gaps
- /gsd:quick

## Key Features

1. **Fresh Context Per Task** - No quality degradation
2. **Atomic Git Commits** - 1 task = 1 commit, bisectable
3. **Wave-Based Parallelism** - Independent work runs simultaneously
4. **Automated Verification** - Goals checked, not just tasks
5. **Brownfield Support** - Add GSD to existing codebases
6. **Milestone Management** - Version tracking and releases
7. **State Persistence** - Resume anytime, zero context loss

## Configuration Options (.planning/config.json)

\\\json
{
  \"mode\": \"yolo\",              // brave | yolo | safe
  \"depth\": \"quick\",            // quick | standard | deep
  \"parallelization\": true,     // Execute plans in parallel
  \"model_profile\": \"balanced\" // quality | balanced | budget
}
\\\

## Live Example

**This repository uses GSD!**

The \.gsd/\ folder in this repo is a GSD-created structure:
- .gsd/PROJECT.md
- .gsd/REQUIREMENTS.md
- .gsd/ROADMAP.md
- .gsd/STATE.md
- .gsd/phases/

## Gap Analysis vs Current Section 3

**Current content (2621 lines):**
- ✗ Generic Goal → Spec → Deliver philosophy
- ✗ No specific tooling
- ✗ No commands
- ✗ No installation
- ✗ Abstract concepts

**Needed content:**
- ✓ CLI tool introduction
- ✓ Installation instructions  
- ✓ 32 commands reference
- ✓ Context rot explanation
- ✓ Multi-agent architecture
- ✓ Wave execution
- ✓ XML task format
- ✓ .planning/ folder structure
- ✓ Hands-on exercises
- ✓ Link to GitHub repo

## Resources Available

✓ **Repo:** ~/gsd-research/ (cloned)
✓ **README:** 27,292 bytes (workflow, commands, philosophy)
✓ **USER-GUIDE:** 21,331 bytes (detailed reference)
✓ **Commands:** 32 .md files with full specs
✓ **Agents:** 11 agent specifications
✓ **Blog post:** Provided by user (lesson structure)
✓ **Live example:** This repo's .gsd/ folder

## Recommended Section 3 Structure

1. **What is GSD?** (definition, installation, quick start)
2. **The Problem** (context rot visualized)
3. **How It Works** (architecture, agents, waves, XML)
4. **Getting Started** (first project walkthrough)
5. **Core Workflow** (6 main commands explained)
6. **Commands Reference** (all 32 with examples)
7. **Advanced Features** (brownfield, milestones, debugging)
8. **Resources & Exercises** (GitHub, Discord, hands-on)

## Key Talking Points

- \"Context rot is real - quality degrades as context fills\"
- \"Fresh subagent contexts = consistent quality\"
- \"Your main session stays at 30-40% while agents work\"
- \"1 task = 1 commit = clean git history\"
- \"Wave execution parallelizes independent work\"
- \"XML tasks have built-in verification\"
- \"This repo's .gsd/ folder was created by GSD\"

## Next Steps for Phase 3

1. Mark Phase 2 complete (/transition)
2. Plan Phase 3 (/plan-phase 3)
   - Use this research as context
   - Plan GSD section rewrite
   - Include Agents and Skills sections
3. Execute Phase 3 (/execute-phase 3)
   - Rewrite 03-gsd/README.md with actual GSD content
   - Create Agents content
   - Create Skills content

---

**Research complete. Ready for Phase 3 planning.**
