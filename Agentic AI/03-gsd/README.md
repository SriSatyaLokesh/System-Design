**📍 Current Location:** [Pathway Home](../README.md) → 3. GSD Framework

**📊 Progress:** Section 3 of 6 | ⏱️ Estimated time: 60 minutes

**Prerequisites:** [1. Ecosystem](../01-ecosystem/README.md), [2. Tools](../02-tools/README.md) — Understanding AI tools and basic prompt engineering

---

# 3. GSD Framework

## Table of Contents

- [Overview](#overview)
- [The Context Rot Problem](#the-context-rot-problem)
- [Installation & Setup](#installation--setup)
- [Goal → Spec → Deliver Flow](#goal--spec--deliver-flow)
- [GSD Architecture](#gsd-architecture)
- [Getting Started](#getting-started)
- [Core Workflow](#core-workflow)
- [Commands Reference](#commands-reference)
- [Advanced Features](#advanced-features)
- [GSD for GitHub Copilot](#gsd-for-github-copilot)
- [Live Example: This Repository](#live-example-this-repository)
- [Hands-On Exercises](#hands-on-exercises)
- [Resources](#resources)

---

## Overview

### What is GSD?

**GSD (Get Shit Done)** is a production-grade CLI tool for AI code assistants like Claude Code, OpenCode, Gemini CLI, and Codex. It transforms how you work with AI on complex projects by solving the fundamental problem of **context rot** through intelligent multi-agent orchestration.

🔗 **GitHub Repository:** [github.com/gsd-build/get-shit-done](https://github.com/gsd-build/get-shit-done)

**GSD is NOT:**
- ❌ A generic "Goal → Spec → Deliver" philosophy
- ❌ A project management tool
- ❌ A replacement for your IDE

**GSD IS:**
- ✅ A CLI tool with 32 commands (`/gsd:command`)
- ✅ A multi-agent orchestration framework
- ✅ A structured planning system that creates `.gsd/` folders
- ✅ A solution that keeps AI quality consistent across 50+ task projects

### Why GSD Exists

When you work with AI assistants on large projects, you hit a brutal wall: **context degradation**. By task 20 of a 50-task project, the AI is rushing, cutting corners, and forgetting requirements from task 1. This isn''t laziness—it''s the reality of finite context windows.

GSD solves this by giving **each task a fresh 200K context window**. Task 50 gets the same quality as task 1.

### When to Use GSD

**Perfect For:**
- 🎯 Complex projects (50+ tasks)
- 🏗️ Multi-phase builds (authentication → features → deployment)
- 👤 Solo developers working with AI copilots
- 📋 Projects needing repeatable structure

**Not Needed For:**
- Single-script projects
- Quick prototypes
- Learning basic coding
- Pair programming without planning

### Real-World Impact

```
Without GSD:
┌─────────────────────────────────────────────┐
│ Task 1-10:  ⭐⭐⭐⭐⭐ Thorough, complete   │
│ Task 11-25: ⭐⭐⭐⭐   Starts rushing       │
│ Task 26-40: ⭐⭐⭐     Cuts corners         │
│ Task 41-50: ⭐⭐       Hallucinations       │
└─────────────────────────────────────────────┘

With GSD:
┌─────────────────────────────────────────────┐
│ Task 1-50:  ⭐⭐⭐⭐⭐ Consistent quality   │
└─────────────────────────────────────────────┘
```

### Live Example: This Very Repository

**You''re looking at GSD output right now.** This entire "Agentic AI" learning pathway was built using GSD:

```
System-Design/
├── Agentic AI/           ← Content created using GSD
│   ├── 01-ecosystem/
│   ├── 02-tools/
│   ├── 03-gsd/          ← This file!
│   └── ...
└── .gsd/                 ← GSD metadata folder
    ├── PROJECT.md        ← Project vision
    ├── ROADMAP.md        ← Phase breakdown
    ├── STATE.md          ← Current progress
    └── phases/           ← Execution history
        ├── 01-foundation-structure/
        ├── 02-foundational-learning-content/
        └── 03-advanced-concepts-frameworks/
```

Every section you''ve read was planned, executed, and verified through GSD commands. Check the `.gsd/` folder to see the entire planning and execution history.

---

## The Context Rot Problem

### Understanding Context Windows

AI assistants have a **context window**—the amount of text they can "remember" at once. Claude Sonnet 4.5, for example, has a 200,000 token context window (roughly 150,000 words).

```
┌─────────────────────────────────────┐
│  Context Window (200K tokens)       │
│                                     │
│  ┌─────────────────────────────┐   │
│  │ System Instructions         │   │
│  │ .gsd/ Instructions          │   │
│  │ Conversation History        │   │
│  │ Code Context                │   │
│  │ Your Current Request        │   │
│  └─────────────────────────────┘   │
└─────────────────────────────────────┘
```

### The Degradation Pattern

As you work through a complex project in a single session, context fills up:

**0-30% Context Usage (Tasks 1-15)**
- ⭐⭐⭐⭐⭐ Peak quality
- Thorough implementation
- Includes edge cases
- Writes tests
- Adds documentation

**50% Context Usage (Tasks 16-30)**
- ⭐⭐⭐⭐ Starts compromising
- Less thorough
- Skips "minor" details
- Documentation gets sparse

**70%+ Context Usage (Tasks 31-50)**
- ⭐⭐⭐ Cutting corners
- Bare minimum implementation
- Forgets earlier requirements
- Inconsistent patterns
- Hallucinations increase

**Example Timeline:**

```
Task 1:  "Create login endpoint"
Result:  ✓ Complete implementation
         ✓ Input validation
         ✓ Error handling
         ✓ JWT generation
         ✓ Tests included
         ✓ Documentation

Task 35: "Create password reset endpoint"  
Result:  ✓ Basic implementation
         ✗ Minimal validation
         ✗ No error handling
         ✗ No tests
         ✗ Documentation missing
         ⚠️  Inconsistent with login endpoint pattern
```

### Why This Happens

It''s not a bug—it''s mathematically inevitable:

1. **Token Budget Pressure:** As the window fills, the AI has less "room" to generate thorough responses
2. **Attention Dilution:** Earlier context becomes harder to reference accurately
3. **Precedence Conflicts:** Old patterns clash with new information
4. **Progressive Summarization:** The AI internally compresses old content, losing details

### Traditional "Solutions" Don''t Work

❌ **"Just start a new session"**
- Loses all project context
- AI doesn''t know what was built
- Inconsistent with previous work

❌ **"Summarize progress regularly"**
- Summaries lose critical details
- No guarantee AI reads them thoroughly
- Still fighting limited context

❌ **"Keep sessions short"**
- Constant context switching
- Heavy manual overhead
- Doesn''t scale to 50+ task projects

### How GSD Solves It

GSD uses **multi-agent orchestration** with fresh contexts:

```
┌────────────────────────────────────────────────────────┐
│ Main Orchestrator Session (30-40% context usage)      │
│                                                        │
│  "Execute Phase 2: Authentication"                    │
│                                                        │
│  Spawns ↓                                             │
└────────────────────────────────────────────────────────┘
         │
         ├──→ ┌──────────────────────────────┐
         │    │ Executor Agent #1            │
         │    │ Fresh 200K Context           │
         │    │ Task: "Create login route"   │
         │    │ Context usage: 15%           │
         │    └──────────────────────────────┘
         │
         ├──→ ┌──────────────────────────────┐
         │    │ Executor Agent #2            │
         │    │ Fresh 200K Context           │
         │    │ Task: "Create JWT utils"     │
         │    │ Context usage: 15%           │
         │    └──────────────────────────────┘
         │
         └──→ ┌──────────────────────────────┐
              │ Executor Agent #3            │
              │ Fresh 200K Context           │
              │ Task: "Create auth tests"    │
              │ Context usage: 15%           │
              └──────────────────────────────┘
```

**Each executor agent:**
- Gets complete project context (PROJECT.md, ROADMAP.md)
- Sees all relevant code files
- Has a single, clear task
- Works at 10-20% context capacity
- Delivers ⭐⭐⭐⭐⭐ quality every time

**Key Insight:** Task 50 gets the same fresh 200K context as task 1. Quality never degrades.

---

## Installation & Setup 🟢 Beginner

### Prerequisites

- **AI Assistant:** Claude Code, OpenCode, Gemini CLI, or Codex
- **Node.js:** Version 18+ (for npx)
- **Git:** For project tracking
- **Terminal Access:** Command-line comfort

### Installation

GSD installs via npm as a global CLI tool:

```bash
# Interactive installation (recommended)
npx get-shit-done-cc@latest

# Non-interactive with specific assistant
npx get-shit-done-cc --claude --global
npx get-shit-done-cc --opencode --local
npx get-shit-done-cc --gemini --global
```

**Installation Options:**

| Flag | Description |
|------|-------------|
| `--claude` | Configure for Claude Code |
| `--opencode` | Configure for OpenCode |
| `--gemini` | Configure for Gemini CLI |
| `--global` | Install commands globally |
| `--local` | Install for current project only |

### Verification

After installation, verify in your AI assistant:

```
You: /gsd:help

Expected Response:
┌───────────────────────────────────────────┐
│ GSD v2.0 - Get Shit Done                 │
├───────────────────────────────────────────┤
│ Available Commands:                       │
│   /gsd:new-project                       │
│   /gsd:plan-phase                        │
│   /gsd:execute-phase                     │
│   ...                                    │
└───────────────────────────────────────────┘
```

If you see this, GSD is ready! 🎉

### Configuration

GSD behavior is controlled by `.gsd/config.json`:

```json
{
  "mode": "yolo",              
  "depth": "quick",            
  "parallelization": true,     
  "commit_docs": true,         
  "model_profile": "balanced"  
}
```

**Mode Settings:**

- **brave** – Minimal checkpoints, moves fast
- **yolo** – Zero checkpoints, maximum speed
- **safe** – Frequent checkpoints, asks before executing

**Depth Settings:**

- **quick** – 4-6 phases, 8-12 plans
- **standard** – 6-8 phases, 15-20 plans  
- **deep** – 10+ phases, 30+ plans

**Model Profiles:**

- **quality** – Sonnet 4.5 for everything (expensive, best results)
- **balanced** – Sonnet 4.5 for planning, Haiku for execution
- **budget** – Haiku for everything (fast, cheaper)

### Troubleshooting

**"Command not found"**
- Run installation again with `--global` flag
- Restart your AI assistant session
- Check Node.js version (`node --version` should be 18+)

**"Permission denied"**
- Use `sudo` for global installs on macOS/Linux
- Run terminal as Administrator on Windows

**"GSD commands not appearing"**
- Some assistants need restart after installation
- Try `/gsd:update` to refresh command list

---

## Goal → Spec → Deliver Flow 🟡 Intermediate

The GSD Framework follows a three-stage workflow that mirrors professional software development practices:

```
     GOAL                SPEC                DELIVER
      ↓                   ↓                    ↓
  ┌─────────┐        ┌─────────┐          ┌─────────┐
  │ What    │        │ How     │          │ Build   │
  │ Why     │───────→│ Phases  │─────────→│ Verify  │
  │ Who     │        │ Tasks   │          │ Ship    │
  └─────────┘        └─────────┘          └─────────┘
    Human              Human+AI              AI+Human
```

### Stage 1: GOAL (Human-Driven)

**Purpose:** Define **what** to build and **why** it matters.

**Questions GSD Asks:**
- What problem are we solving?
- Who is this for?
- What''s in scope / out of scope?
- What are our constraints?
- How do we measure success?

**Output:** `PROJECT.md`

```markdown
# Project: Task Management for Freelancers

## What

A web app helping freelancers track client projects, 
tasks, and billable hours.

## Why

Freelancers lose ~15% revenue to poor time tracking. 
Existing tools are enterprise-focused, over-complex.

## For Whom

Solo freelancers and small teams (1-5 people) managing 
3-10 concurrent client projects.

## Constraints

- Must run in browser (no installs)
- Free tier support
- Mobile-friendly
- Launch in 30 days

## Success

- Freelancer can track 10 projects with 50 tasks each
- Time tracking accurate to 15-minute increments
- Export to invoices in 2 clicks
```

**Why This Stage Matters:**

Without clear goals, AI builds the wrong thing. The PROJECT.md becomes your **source of truth** that every agent references.

### Stage 2: SPEC (Human + AI Collaboration)

**Purpose:** Break the goal into **executable phases and tasks**.

**GSD Command:** `/gsd:plan-phase`

**Process:**

1. **Research Phase:** GSD spawns 4 parallel research agents
   - Stack research (Next.js vs Remix?)
   - Feature breakdown (auth, CRUD, reports)
   - Architecture patterns (monolith vs microservices)
   - Common pitfalls (security, performance)

2. **Planning Phase:** Create task decomposition
   - Phases ordered by dependency
   - Tasks numbered and sequenced
   - Acceptance criteria defined
   - Wave grouping for parallelization

**Output:** `ROADMAP.md` + Phase-specific `PLAN.md` files

```markdown
# ROADMAP.md

## Phase 1: Foundation (5 tasks)
Goal: Next.js 15 + Prisma + Tailwind scaffold

## Phase 2: Authentication (8 tasks)  
Goal: JWT-based auth with email/password

## Phase 3: Project Management (12 tasks)
Goal: Create, list, edit, delete projects

## Phase 4: Time Tracking (10 tasks)
Goal: Start/stop timer, manual entry, edit history

## Phase 5: Reports & Export (7 tasks)
Goal: Hour summaries, invoice export
```

**Example: Phase 2 Plan (02-01-PLAN.md)**

```xml
<task type="auto">
  <name>Create login endpoint</name>
  <files>src/app/api/auth/login/route.ts</files>
  <action>
    POST /api/auth/login validates email + password.
    Use Prisma to query users table.
    Use jose to generate JWT token.  
    Return httpOnly cookie.
  </action>
  <verify>
    curl -X POST localhost:3000/api/auth/login \
      -d ''{"email":"test@example.com","password":"pass"}'' \
      returns 200 with Set-Cookie header
  </verify>
  <done>
    Valid credentials return token cookie.
    Invalid credentials return 401.
  </done>
</task>

<task type="auto">
  <name>Create registration endpoint</name>
  <files>src/app/api/auth/register/route.ts</files>
  <action>
    POST /api/auth/register accepts email, password.
    Hash password with bcrypt.
    Check for duplicate email.
    Create user in Prisma.
    Return success message.
  </action>
  <verify>
    curl -X POST localhost:3000/api/auth/register \
      -d ''{"email":"new@example.com","password":"pass"}'' \
      returns 201
  </verify>
  <done>
    New user created in database.
    Duplicate email returns 409.
  </done>
</task>
```

**Why This Stage Matters:**

The SPEC is where AI collaboration shines. GSD researches best practices, suggests patterns, and structures tasks—but **you approve** the plan. This ensures AI builds what you actually want.

### Stage 3: DELIVER (AI + Human Execution)

**Purpose:** Execute the tasks, verify outcomes, ship working software.

**GSD Command:** `/gsd:execute-phase 2`

**Process:**

1. **Wave-Based Execution:**
   - GSD groups tasks by dependencies
   - Wave 1 tasks (no dependencies) run in parallel
   - Wave 2 tasks (depend on Wave 1) run after verification
   - Each wave gets fresh executor agents

2. **Task Execution:**
   ```
   Executor Agent receives:
   ├─ PROJECT.md (vision)
   ├─ ROADMAP.md (all phases)
   ├─ 02-01-PLAN.md (current plan)
   ├─ Relevant code files
   └─ Single task to execute
   
   Executor Agent delivers:
   ├─ Implemented code
   ├─ Tests (if specified)
   ├─ Documentation
   └─ Git commit (atomic)
   ```

3. **Atomic Git Commits:**
   ```bash
   # Each task = 1 commit
   feat(02-01): create login endpoint
   
   - POST /api/auth/login validates credentials
   - Uses jose for JWT generation
   - Returns httpOnly cookie
   ```

4. **Verification:**
   - Each task has `<verify>` criteria
   - GSD can spawn verification agent
   - `/gsd:verify-work 2` for manual UAT

**Output:** Working software + `SUMMARY.md`

```markdown
# Phase 2 Summary

## Objectives Achieved
✓ JWT-based authentication system
✓ Email/password registration
✓ httpOnly cookie sessions
✓ Password reset flow

## Files Modified
- src/app/api/auth/login/route.ts (created)
- src/app/api/auth/register/route.ts (created)
- src/lib/jwt.ts (created)
- src/middleware.ts (updated)

## Tasks Completed: 8/8
[Detailed task list...]

## Verification
✓ Manual testing: Login flow works
✓ Security: httpOnly cookies prevent XSS
✓ Error handling: Invalid creds return 401
```

**Why This Stage Matters:**

This is where GSD''s multi-agent orchestration pays off. While you''d normally fight context rot through 8 tasks, GSD gives each task a fresh agent. Quality stays consistently high.

### Before/After: PRD-Driven Example

**Before GSD (Traditional Prompting):**

```
You: "Build a task management app for freelancers"

AI: "Sure! I''ll create a React app with..."
     [builds generic todo list]
     [no time tracking]
     [no client management]  
     [doesn''t match your vision]

You: "No, I need client projects and billable hours"

AI: "Oh, let me refactor..."
     [breaks existing code]
     [inconsistent patterns]
     [quality declining as conversation grows]
```

**After 3 hours:** Frustrated, partially working app that doesn''t match needs.

**With GSD (PRD-Driven):**

```
You: /gsd:new-project

GSD: Asks strategic questions about goals, users, constraints

Output: PROJECT.md (clear vision) + ROADMAP.md (5 phases)

You: /gsd:execute-phase 1

GSD: Spawns executor agents, each gets fresh context

Output: Next.js scaffold + Prisma + Tailwind (45 minutes)

You: /gsd:execute-phase 2  

GSD: Fresh agents build authentication

Output: Complete auth system with tests (60 minutes)
```

**After 3 hours:** Phases 1-2 complete, phase 3 in progress. High-quality, tested code aligned with PROJECT.md vision.

---

## GSD Architecture 🔴 Advanced

### Multi-Agent System Design

GSD uses a **thin orchestrator + specialized agents** pattern:

```
┌─────────────────────────────────────────────────────┐
│          Main Session (Orchestrator)                │
│          Context Usage: 30-40%                      │
│                                                     │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐         │
│  │PROJECT.md│  │ROADMAP.md│  │ STATE.md │         │
│  └──────────┘  └──────────┘  └──────────┘         │
│                                                     │
│  Commands: /gsd:plan-phase, /gsd:execute-phase     │
└─────────────────────────────────────────────────────┘
              │
              │ Spawns specialized agents ↓
              │
    ┌─────────┴──────────┬──────────────┬──────────────┐
    │                    │              │              │
┌───────────┐      ┌───────────┐  ┌───────────┐  ┌───────────┐
│ Research  │      │ Planner   │  │ Executor  │  │ Verifier  │
│ Agent     │      │ Agent     │  │ Agent     │  │ Agent     │
│           │      │           │  │           │  │           │
│ 200K ctx  │      │ 200K ctx  │  │ 200K ctx  │  │ 200K ctx  │
│ 15% used  │      │ 20% used  │  │ 15% used  │  │ 10% used  │
└───────────┘      └───────────┘  └───────────┘  └───────────┘
```

**Why This Works:**

1. **Orchestrator** stays lightweight (30-40% context)
   - Tracks project state
   - Routes commands to agents
   - Aggregates results
   - Never does heavy lifting

2. **Specialized Agents** operate at peak efficiency (10-20% context)
   - Single responsibility
   - Fresh context every time
   - Consistent quality
   - Fast execution

### Wave-Based Execution

GSD analyzes task dependencies and groups execution into **waves**:

```
Phase 2: Authentication (8 tasks)

Wave 1 (Independent - Run in Parallel):
├─ Install jose library
├─ Create user schema  
└─ Set up password hashing

Wave 2 (Depends on Wave 1):
├─ Create login endpoint         [needs jwt, schema]
├─ Create registration endpoint  [needs schema, hashing]
└─ Create password reset         [needs schema]

Wave 3 (Depends on Wave 2):
├─ Add auth middleware           [needs login endpoint]
└─ Protect dashboard routes      [needs middleware]
```

**Execution Flow:**

```
┌─────────────────────────────────────────────┐
│ Wave 1: 3 tasks                             │
├─────────────────────────────────────────────┤
│  ┌──────┐  ┌──────┐  ┌──────┐              │
│  │Agent1│  │Agent2│  │Agent3│              │
│  │ 15%  │  │ 15%  │  │ 15%  │              │
│  └──┬───┘  └──┬───┘  └──┬───┘              │
│     └────┬────┴─────┬───┘                   │
│          ↓          ↓                       │
│       [Verify All Complete]                │
└─────────────────────────────────────────────┘
                │
                ↓
┌─────────────────────────────────────────────┐
│ Wave 2: 3 tasks                             │
├─────────────────────────────────────────────┤
│  ┌──────┐  ┌──────┐  ┌──────┐              │
│  │Agent4│  │Agent5│  │Agent6│              │
│  │ 15%  │  │ 15%  │  │ 15%  │              │
│  └──┬───┘  └──┬───┘  └──┬───┘              │
│     └────┬────┴─────┬───┘                   │
│          ↓          ↓                       │
│       [Verify All Complete]                │
└─────────────────────────────────────────────┘
```

**Benefits:**

- **Speed:** Independent tasks run simultaneously
- **Safety:** Dependencies respected automatically
- **Quality:** Each agent works at 15% context capacity
- **Recovery:** Failed task doesn''t block unrelated work

### .gsd/ Folder Structure

Every GSD project creates a `.gsd/` metadata folder:

```
.gsd/
├── config.json              # Behavior settings
├── PROJECT.md               # Vision and constraints
├── REQUIREMENTS.md          # All requirements (traceable IDs)
├── ROADMAP.md               # Phase breakdown + success criteria
├── STATE.md                 # Current progress + blockers
└── phases/
    ├── 01-foundation/
    │   ├── 01-CONTEXT.md       # Your decisions
    │   ├── 01-RESEARCH.md      # Implementation research
    │   ├── 01-01-PLAN.md       # Task plan
    │   ├── 01-01-SUMMARY.md    # Execution outcome
    │   └── 01-VERIFICATION.md  # Goal achievement check
    ├── 02-authentication/
    │   ├── 02-CONTEXT.md
    │   ├── 02-RESEARCH.md
    │   ├── 02-01-PLAN.md       # Auth core
    │   ├── 02-01-SUMMARY.md
    │   ├── 02-02-PLAN.md       # Password reset
    │   ├── 02-02-SUMMARY.md
    │   └── 02-VERIFICATION.md
    └── 03-project-management/
        └── ...
```

**Key Files:**

| File | Purpose | Created By |
|------|---------|------------|
| `PROJECT.md` | Single source of truth for vision | `/gsd:new-project` |
| `ROADMAP.md` | All phases with success criteria | `/gsd:new-project` |
| `STATE.md` | Current progress, blockers, next steps | Auto-updated |
| `{phase}-RESEARCH.md` | Stack/feature/architecture research | `/gsd:plan-phase` |
| `{phase}-{plan}-PLAN.md` | Executable task list (XML format) | `/gsd:plan-phase` |
| `{phase}-{plan}-SUMMARY.md` | What was built, files changed | `/gsd:execute-phase` |
| `{phase}-VERIFICATION.md` | Goal-backward quality check | `/gsd:verify-work` |

### XML Task Format

GSD uses structured XML for task definitions:

```xml
<task type="auto">
  <name>Create login endpoint</name>
  
  <files>src/app/api/auth/login/route.ts</files>
  
  <action>
    POST /api/auth/login endpoint:
    - Validate email and password from request body
    - Query user from Prisma database
    - Compare password hash using bcrypt
    - Generate JWT token using jose library
    - Return httpOnly cookie with 7-day expiry
    - Return 401 for invalid credentials
  </action>
  
  <verify>
    curl -X POST http://localhost:3000/api/auth/login \
      -H "Content-Type: application/json" \
      -d ''{"email":"test@test.com","password":"password"}'' \
      -c cookies.txt
    
    Expected: 200 status, Set-Cookie header with JWT
  </verify>
  
  <done>
    Valid credentials → 200 + httpOnly cookie
    Invalid credentials → 401 + error message
    File created: src/app/api/auth/login/route.ts
  </done>
</task>
```

**Why XML?**

- **Structured:** Consistent format for AI parsing
- **Explicit:** Clear sections for action, verification, completion
- **Checkpoints:** Built-in verification criteria
- **Language-Agnostic:** Works for any stack

**Task Types:**

- `type="auto"` – AI can execute autonomously
- `type="human"` – Requires human decision/action
- `type="checkpoint"` – Pause for verification

### Token Budget Allocation

GSD carefully manages context across agents:

```
Total Available: 200,000 tokens per agent

Orchestrator (Main Session):
├─ System instructions:      5,000 tokens
├─ GSD commands/skills:      10,000 tokens
├─ PROJECT.md + ROADMAP.md:  8,000 tokens
├─ STATE.md + config:        2,000 tokens
├─ Conversation history:     30,000 tokens
└─ Remaining capacity:       145,000 tokens (72%)

Executor Agent (Fresh Context):
├─ System instructions:      5,000 tokens
├─ Execute-plan skill:       8,000 tokens
├─ PROJECT.md + ROADMAP.md:  8,000 tokens
├─ Current PLAN.md:          5,000 tokens
├─ Relevant code files:      15,000 tokens
├─ Single task context:      3,000 tokens
└─ Generation budget:        156,000 tokens (78%)
```

**Key Insight:** Executor agents use only 22% of context for input, leaving 78% for high-quality generation. This is why quality stays consistent.

---

## Getting Started

### Step 1: Create Your First GSD Project

```bash
# Navigate to your project directory
cd ~/projects/my-new-app

# Initialize GSD project
/gsd:new-project
```

**GSD will ask:**

```
What are you building?
→ A task management app for freelancers

Who is this for?
→ Solo freelancers managing 3-10 client projects

What are your constraints?
→ Must run in browser, free tier compatible, 30-day deadline

What tech stack preferences?
→ Next.js 15, Prisma, PostgreSQL, Tailwind

Any out-of-scope items?
→ No mobile apps, no team collaboration features, no AI features

How do you measure success?
→ Freelancer can track 10 projects with 50 tasks each, 
  export to invoices in 2 clicks
```

**Output Created:**

```
.gsd/
├── PROJECT.md        ← Your vision captured
├── REQUIREMENTS.md   ← Features with IDs (FEAT-001, etc.)
├── ROADMAP.md        ← Phases breakdown
├── STATE.md          ← "Phase 1 ready to plan"
└── config.json       ← Default settings
```

### Step 2: Review and Adjust the Plan

```bash
# Read the generated roadmap
cat .gsd/ROADMAP.md
```

**Typical Roadmap:**

```markdown
## Phase 1: Foundation  
Goal: Next.js 15 + Prisma + Tailwind scaffold
Tasks: ~5

## Phase 2: Authentication
Goal: Email/password auth with JWT
Tasks: ~8

## Phase 3: Project Management
Goal: CRUD for projects
Tasks: ~12

## Phase 4: Task Management
Goal: CRUD for tasks within projects
Tasks: ~10

## Phase 5: Time Tracking
Goal: Start/stop timer, manual entry
Tasks: ~10

## Phase 6: Reports & Export
Goal: Hour summaries, invoice generation
Tasks: ~7
```

**If you want changes:**

```bash
# Edit the file directly (GSD adapts)
code .gsd/ROADMAP.md

# Or ask GSD to adjust
/gsd:add-phase "Notification System" --after 3
/gsd:remove-phase 6  # Defer invoice export to v2
```

### Step 3: Execute Phase 1

```bash
# Plan phase 1 (research + task breakdown)
/gsd:plan-phase 1
```

**GSD spawns 4 research agents in parallel:**

1. **Stack Research** → Next.js 15 app router patterns
2. **Feature Decomposition** → Break "scaffold" into tasks
3. **Architecture** → Folder structure, config files
4. **Pitfalls** → Common mistakes with app router

**After 2-3 minutes:**

```
.gsd/phases/01-foundation/
├── 01-RESEARCH.md     ← Research findings
└── 01-01-PLAN.md      ← 5 executable tasks
```

**Review the plan:**

```bash
cat .gsd/phases/01-foundation/01-01-PLAN.md
```

**If good, execute:**

```bash
/gsd:execute-phase 1
```

**GSD spawns executor agent:**

```
Executing Wave 1 (5 tasks)...
  ✓ Create Next.js 15 project
  ✓ Install dependencies (Prisma, Tailwind)
  ✓ Configure Prisma schema
  ✓ Set up Tailwind
  ✓ Create base layout

Phase 1 complete!
Files modified: 12
Git commits: 5
SUMMARY: .gsd/phases/01-foundation/01-01-SUMMARY.md
```

**Check the results:**

```bash
# See what was built
cat .gsd/phases/01-foundation/01-01-SUMMARY.md

# Review git history
git log --oneline
```

### Step 4: Verify Your Progress

```bash
# Interactive testing
/gsd:verify-work 1
```

**GSD guides you through verification:**

```
Let''s verify Phase 1: Foundation

Test 1: Development server starts
Action: Run ''npm run dev''
Did it work? [yes/no]: yes

Test 2: Prisma schema loads
Action: Run ''npx prisma studio''
Did Prisma studio open? [yes/no]: yes

Test 3: Tailwind styles apply
Action: Visit localhost:3000, check styling
Are styles working? [yes/no]: yes

✓ All tests passed!
Verification saved: .gsd/phases/01-foundation/01-VERIFICATION.md
```

**If issues found:**

GSD automatically creates fix plans and spawns diagnostic agents.

### Step 5: Continue to Next Phase

```bash
# Mark phase complete and move forward
/gsd:transition

# Plan phase 2
/gsd:plan-phase 2

# Execute phase 2
/gsd:execute-phase 2
```

**Repeat this loop** until all phases complete!

### Quick Start Checklist

- [ ] Install GSD: `npx get-shit-done-cc@latest`
- [ ] Verify installation: `/gsd:help`
- [ ] Create project: `/gsd:new-project`
- [ ] Review ROADMAP.md
- [ ] Plan phase 1: `/gsd:plan-phase 1`
- [ ] Execute phase 1: `/gsd:execute-phase 1`
- [ ] Verify results: `/gsd:verify-work 1`
- [ ] Transition to phase 2: `/gsd:transition`

---

## Core Workflow

### Daily GSD Usage Pattern

**Starting Your Session:**

```bash
# Resume project context
/gsd:resume-project
```

**GSD responds:**

```
Project: Task Management for Freelancers
Current: Phase 3 (Project Management) - Plan 2

Progress: 15/42 tasks complete (36%)

Last completed:
- Phase 2: Authentication ✓
- Phase 3 Plan 1: Project CRUD ✓

Active:
- Phase 3 Plan 2: Project search & filters (3/5 tasks)

Next steps:
1. Complete remaining 2 tasks in 03-02
2. Execute 03-03 (project archiving)
3. Verify Phase 3 before transition

Blockers: None
```

**Review Current State:**

```bash
# Detailed status
/gsd:progress
```

**Output:**

```
Overall Progress: 36%
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

✅ Phase 1: Foundation (5/5 tasks)
✅ Phase 2: Authentication (8/8 tasks)
🔄 Phase 3: Project Management (6/12 tasks)
   ├─ ✅ Plan 1: Project CRUD (5/5)
   ├─ 🔄 Plan 2: Search & Filters (3/5) ← YOU ARE HERE
   └─ ⬜ Plan 3: Archiving (0/2)
⬜ Phase 4: Task Management (0/10 tasks)
⬜ Phase 5: Time Tracking (0/10 tasks)
⬜ Phase 6: Reports (0/7 tasks)
```

### Execution Pacing

**Option 1: Execute Full Phases**

```bash
# Research, plan, and execute entire phase
/gsd:execute-phase 3

# GSD handles:
# - Planning (if needed)
# - Wave-based task execution
# - Verification
# - State updates
```

**Option 2: Incremental Progress**

```bash
# Plan first, review before executing
/gsd:plan-phase 3
cat .gsd/phases/03-project-management/03-01-PLAN.md

# Execute when ready
/gsd:execute-phase 3
```

**Option 3: Manual Control**

```bash
# Plan individual plans within a phase
/gsd:plan-phase 3 --plan 2  # Just plan 03-02

# Execute specific plan
/gsd:execute-phase 3 --plan 2
```

### Handling Issues

**Execution Failed:**

```bash
# GSD auto-captures failure
Task 4 failed: "Create search filters"
Error: Type error in searchParams handling

# Diagnose the issue
/gsd:diagnose-issues

# GSD spawns debug agent:
Analyzing failure...
Root cause: Next.js 15 app router searchParams 
            changed in beta → stable

Fix approach:
1. Update searchParams handling
2. Use useSearchParams() hook
3. Update types

Creating fix plan...
Fix plan: .gsd/phases/03-project-management/03-02-FIX-PLAN.md

Execute fix? [yes/no]: yes

✓ Fix applied successfully
Resuming from task 4...
```

**Manual Debugging:**

```bash
# Enter debug mode
/gsd:debug

# GSD provides context:
Debug session started
Current files: src/app/projects/page.tsx
Active plan: 03-02-PLAN.md
Failed task: Task 4 (Create search filters)
Error log: [shows error]

You can now:
- Manually fix the code
- Ask questions about the error
- Request GSD to retry

When fixed, type: /gsd:resume-work
```

### State Management

**GSD automatically updates STATE.md:**

```markdown
# Current Status

Active Phase: 3 of 6 (Project Management)
Phase Progress: 6/12 tasks (50%)
Overall: 19/42 tasks (45%)

## Recent Activity

2025-02-27 14:30 - Completed task: "Add project search"
2025-02-27 14:15 - Completed task: "Add filtering UI"
2025-02-27 14:00 - Started Plan 03-02

## Blockers

None

## Notes

- Search uses Next.js 15 searchParams pattern
- Filters persist in URL query string
- Need to add filter reset button (noted for polish phase)
```

**Manual Updates:**

```bash
# Add notes or blockers
code .gsd/STATE.md

# GSD reads this on every command
# Useful for tracking decisions
```

### Checkpoint Protocols

**Automatic Checkpoints (mode: safe):**

```
Checkpoint: Phase 2 complete
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Files modified: 8
Git commits: 8
Tests: 12 passing

Review SUMMARY:
.gsd/phases/02-authentication/02-SUMMARY.md

Ready to continue to Phase 3? [yes/no/pause]:
```

**Manual Checkpoints (any mode):**

```bash
# Pause work
/gsd:pause-work "Blocked on API key from client"

# Later...
/gsd:resume-work
```

### Working Across Sessions

**Ending a Session:**

```bash
# GSD automatically saves state
# Nothing to do—just close your session

# Optional: Explicit pause
/gsd:pause-work
```

**Starting a New Session:**

```bash
# Instant context restoration
/gsd:resume-project

# GSD loads:
# - PROJECT.md (vision)
# - ROADMAP.md (all phases)
# - STATE.md (current progress)
# - Active PLAN.md (current tasks)
# - Recent SUMMARY files (what was built)
```

**Key Insight:** Because GSD stores context in `.gsd/` folder, you never lose progress. Every session starts with full project knowledge.

---

## Commands Reference 🟢 Beginner

GSD provides 32 commands organized by workflow stage:

### Project Management

**`/gsd:new-project`**
- Initialize new GSD project
- Creates PROJECT.md, ROADMAP.md, STATE.md
- Interactive questioning mode
- **Usage:** `/gsd:new-project`

**`/gsd:resume-project`**
- Restore full project context after break
- Loads current state, recent progress, next steps
- **Usage:** `/gsd:resume-project`

**`/gsd:progress`**
- Detailed progress report
- Shows phase completion, task count, blockers
- **Usage:** `/gsd:progress`

### Planning

**`/gsd:discuss-phase N`**
- Capture implementation preferences
- Lock in tech choices, architectural decisions
- Creates `{phase}-CONTEXT.md`
- **Usage:** `/gsd:discuss-phase 2`

**`/gsd:plan-phase N`**
- Research and create task plans
- Spawns 4 parallel research agents
- Creates `{phase}-RESEARCH.md` and PLAN files
- **Usage:** `/gsd:plan-phase 2`
- **Options:** `--plan X` (specific plan only)

**`/gsd:research-phase N`**
- Research-only mode (no plan creation)
- Useful for exploration before committing
- **Usage:** `/gsd:research-phase 2`

### Execution

**`/gsd:execute-phase N`**
- Execute all plans in a phase
- Wave-based parallel execution
- Fresh executor agents per plan
- Creates SUMMARY files
- **Usage:** `/gsd:execute-phase 2`
- **Options:** `--plan X` (specific plan only)

**`/gsd:verify-work N`**
- Interactive UAT testing
- Guided verification checklist
- Creates `{phase}-VERIFICATION.md`
- Auto-diagnoses failures
- **Usage:** `/gsd:verify-work 2`

### Phase Management

**`/gsd:add-phase "Name"`**
- Add new phase to roadmap
- **Usage:** `/gsd:add-phase "Notification System"`
- **Options:** `--after X` (insert position)

**`/gsd:insert-phase "Name" --after X`**
- Insert phase at specific position
- **Usage:** `/gsd:insert-phase "Payment Gateway" --after 3`

**`/gsd:remove-phase N`**
- Remove phase from roadmap
- **Usage:** `/gsd:remove-phase 6`

**`/gsd:list-phase-assumptions N`**
- Surface Copilot''s assumptions about phase
- Prevents misalignment
- **Usage:** `/gsd:list-phase-assumptions 3`

**`/gsd:transition`**
- Mark current phase complete
- Advance to next phase
- Updates ROADMAP.md and STATE.md
- **Usage:** `/gsd:transition`

### Brownfield Projects

**`/gsd:map-codebase`**
- Analyze existing codebase
- Creates structured documentation in `.gsd/codebase/`
- Generates architecture map, dependency graph
- **Usage:** `/gsd:map-codebase`

**Documents Created:**
```
.gsd/codebase/
├── ARCHITECTURE.md      # System design
├── DEPENDENCIES.md      # Tech stack
├── ENTRY-POINTS.md      # Key files
├── DATA-FLOW.md         # State management
├── INTEGRATION-POINTS.md # APIs, external services
├── CONVENTIONS.md       # Code patterns
└── GAPS.md              # Missing docs, tests
```

### Debugging

**`/gsd:debug`**
- Enter interactive debug mode
- Provides failure context
- Allows manual fixes
- **Usage:** `/gsd:debug`

**`/gsd:diagnose-issues`**
- Auto-diagnose recent failures
- Spawns diagnostic agents
- Creates fix plans
- **Usage:** `/gsd:diagnose-issues`

### Milestones

**`/gsd:new-milestone "v1.0"`**
- Create new milestone
- Set version and deliverables
- **Usage:** `/gsd:new-milestone "v1.0"`

**`/gsd:audit-milestone`**
- Check milestone readiness
- Verify all deliverables
- **Usage:** `/gsd:audit-milestone`

**`/gsd:complete-milestone`**
- Mark milestone complete
- Creates MILESTONES.md entry
- Tags git release
- **Usage:** `/gsd:complete-milestone`

### Configuration

**`/gsd:settings`**
- View current configuration
- Shows mode, depth, model profile
- **Usage:** `/gsd:settings`

**`/gsd:set-profile PROFILE`**
- Change model profile
- Profiles: quality, balanced, budget
- **Usage:** `/gsd:set-profile quality`

### Maintenance

**`/gsd:add-todo "Description"`**
- Add technical debt item
- **Usage:** `/gsd:add-todo "Refactor auth middleware"`

**`/gsd:check-todos`**
- List all pending todos
- **Usage:** `/gsd:check-todos`

**`/gsd:cleanup`**
- Clean temporary files
- Archive old plans
- **Usage:** `/gsd:cleanup`

**`/gsd:pause-work "Reason"`**
- Pause with context
- **Usage:** `/gsd:pause-work "Waiting on API key"`

**`/gsd:resume-work`**
- Resume after pause
- **Usage:** `/gsd:resume-work`

**`/gsd:health`**
- Check project health
- Verify .gsd/ folder integrity
- **Usage:** `/gsd:health`

**`/gsd:add-tests`**
- Generate test plans for existing code
- **Usage:** `/gsd:add-tests`

**`/gsd:reapply-patches`**
- Re-run configuration files
- Useful after updates
- **Usage:** `/gsd:reapply-patches`

### Meta

**`/gsd:help`**
- Show command list
- **Usage:** `/gsd:help`

**`/gsd:update`**
- Check for updates
- **Usage:** `/gsd:update`

**`/gsd:join-discord`**
- Get Discord community link
- **Usage:** `/gsd:join-discord`

---

## Advanced Features

### Brownfield Integration

**Challenge:** You have an existing codebase without GSD structure.

**Solution:** `/gsd:map-codebase`

```bash
cd ~/existing-project

# GSD analyzes your codebase
/gsd:map-codebase
```

**GSD spawns 7 parallel mapper agents:**

1. **Architecture Mapper** – System design, key components
2. **Dependency Analyzer** – Tech stack, libraries
3. **Entry Point Finder** – Main files, bootstrapping
4. **Data Flow Tracer** – State management, data flow
5. **Integration Mapper** – APIs, databases, external services
6. **Convention Extractor** – Coding patterns, file structure
7. **Gap Detector** – Missing tests, docs, types

**Output:**

```
.gsd/codebase/
├── ARCHITECTURE.md          # "Next.js 14 app router, 
│                            #  Prisma ORM, tRPC API layer"
├── DEPENDENCIES.md          # "React 18, TypeScript 5.3,
│                            #  Tailwind 3.4, jose for JWT"
├── ENTRY-POINTS.md          # "src/app/layout.tsx (root),
│                            #  src/server/api/root.ts (API)"
├── DATA-FLOW.md             # "React Query for client state,
│                            #  Prisma for database, ..."
├── INTEGRATION-POINTS.md    # "Stripe API, SendGrid, S3"
├── CONVENTIONS.md           # "kebab-case for files,
│                            #  tRPC procedures in server/"
└── GAPS.md                  # "Missing: E2E tests,
│                            #  API documentation,
│                            #  Error monitoring"
```

**Now create GSD project:**

```bash
/gsd:new-project --brownfield
```

**GSD uses codebase maps to:**
- Suggest realistic phases (respects existing patterns)
- Avoid breaking changes
- Reference actual file paths
- Match your conventions

### Milestone Management

**Use Case:** You want versioned releases (v1.0, v1.1, v2.0).

**Workflow:**

```bash
# Create milestone
/gsd:new-milestone "v1.0"

# GSD asks:
What''s shipping in v1.0?
→ Authentication, Project CRUD, Basic time tracking

Which phases?
→ Phase 1-3

Target date?
→ 2025-03-15

# Creates:
.gsd/milestones/v1.0.md
```

**Track progress:**

```bash
# Check milestone readiness
/gsd:audit-milestone

# Output:
Milestone: v1.0 MVP
Target: 2025-03-15 (14 days away)

Progress: 85%
├─ ✅ Phase 1: Foundation
├─ ✅ Phase 2: Authentication  
└─ 🔄 Phase 3: Project Management (9/12 tasks)

Blockers: None
On track: Yes

Remaining work:
- Complete Phase 3 (estimated: 2 days)
- Verification & polish (estimated: 1 day)
```

**Ship it:**

```bash
/gsd:complete-milestone

# GSD:
# 1. Verifies all phases complete
# 2. Creates MILESTONES.md history
# 3. Tags git release (v1.0)
# 4. Updates PROJECT.md with shipped features

Milestone v1.0 shipped! 🎉
Git tag: v1.0
Released: 2025-03-01
```

### Model Profile Tuning

**Profiles balance cost vs quality:**

```bash
# Check current profile
/gsd:settings

# Output:
Mode: yolo
Depth: quick
Model Profile: balanced
```

**Profile Comparison:**

| Profile | Planning | Execution | Research | Cost/Phase | Quality |
|---------|----------|-----------|----------|------------|---------|
| **quality** | Sonnet 4.5 | Sonnet 4.5 | Sonnet 4.5 | $$$$ | ⭐⭐⭐⭐⭐ |
| **balanced** | Sonnet 4.5 | Haiku | Sonnet 4.5 | $$ | ⭐⭐⭐⭐ |
| **budget** | Haiku | Haiku | Haiku | $ | ⭐⭐⭐ |

**When to Use Each:**

**Quality Profile:**
```bash
/gsd:set-profile quality

# Use when:
- Mission-critical code (payments, auth)
- Complex algorithms
- You need best possible output
- Cost isn''t primary concern
```

**Balanced Profile (Default):**
```bash
/gsd:set-profile balanced

# Use when:
- Standard web development
- Mix of complex and simple tasks
- Want good quality and reasonable cost
- Most projects fall here
```

**Budget Profile:**
```bash
/gsd:set-profile budget

# Use when:
- Learning/experimental projects
- Simple CRUD apps
- Prototyping
- Cost-sensitive
```

### Custom Configuration

**Edit `.gsd/config.json` for fine control:**

```json
{
  "mode": "brave",              
  "depth": "standard",          
  "parallelization": true,      
  "commit_docs": false,         
  "model_profile": "quality",   
  
  "phase_config": {
    "max_plans_per_phase": 3,
    "max_tasks_per_plan": 8,
    "require_verification": true
  },
  
  "execution": {
    "auto_retry_failed_tasks": true,
    "max_retries": 2,
    "checkpoint_frequency": "per_wave"
  },
  
  "git": {
    "atomic_commits": true,
    "commit_per_task": true,
    "auto_push": false
  }
}
```

**Configuration Options:**

- `mode`: brave | yolo | safe
- `depth`: quick | standard | deep
- `parallelization`: true | false
- `commit_docs`: Include .gsd/ files in commits
- `max_plans_per_phase`: Limit plan count
- `require_verification`: Force manual checks
- `auto_retry_failed_tasks`: Retry on errors
- `checkpoint_frequency`: per_wave | per_plan | per_task

---

## GSD for GitHub Copilot 🟡 Intermediate

### Overview

**GSD for GitHub Copilot** is a complete port of the GSD framework that brings the same powerful context engineering and multi-agent orchestration to **VS Code with GitHub Copilot**.

🔗 **Repository:** [github.com/Punal100/get-stuff-done-for-github-copilot](https://github.com/Punal100/get-stuff-done-for-github-copilot)

**Port Lineage:**
```
Original GSD (Claude Code) by glittercowboy
    ↓
GSD for Kilo Code by punal100
    ↓
GSD for GitHub Copilot by punal100
```

Instead of slash commands (`/gsd:new-project`) used in Claude Code, this port uses:
- **Prompt Files** (`.github/prompts/*.prompt.md`)
- **Custom Agents** (`.github/agents/*.agent.md`)
- **Agent Skills** (`.github/skills/*/SKILL.md`)
- **Instructions** (`.github/instructions/*.instructions.md`)

All the core GSD methodology remains the same—only the integration mechanism changes.

### Why GitHub Copilot Version?

**Use GSD for GitHub Copilot if you:**
- Work primarily in VS Code
- Have GitHub Copilot subscription
- Want GSD workflow without CLI tools
- Prefer native IDE integration
- Use Copilot for code generation

**Use Original GSD if you:**
- Use Claude Code, OpenCode, or Gemini CLI
- Want the most mature version
- Prefer command-line workflow
- Need the latest features first

### Installation & Setup

#### Prerequisites

- **VS Code** with GitHub Copilot extension
- **GitHub Copilot** subscription (Individual, Business, or Enterprise)
- **Git** for version control

#### Quick Setup (PowerShell/Windows)

```powershell
# Navigate to your project
cd your-project

# Clone the GSD template
git clone https://github.com/Punal100/get-stuff-done-for-github-copilot.git gsd-template

# Copy to your project
Copy-Item -Recurse gsd-template\.github .\
Copy-Item -Recurse gsd-template\.gsd .\

# Clean up
Remove-Item -Recurse -Force gsd-template

# Reload VS Code
code .
```

#### Quick Setup (Bash/Linux/Mac)

```bash
# Navigate to your project
cd your-project

# Clone the GSD template
git clone https://github.com/Punal100/get-stuff-done-for-github-copilot.git gsd-template

# Copy to your project
cp -r gsd-template/.github ./
cp -r gsd-template/.gsd ./

# Clean up
rm -rf gsd-template

# Reload VS Code
code .
```

#### VS Code Configuration

Enable GitHub Copilot customization features in your VS Code settings:

```json
{
  "github.copilot.chat.codeGeneration.useInstructionFiles": true,
  "chat.promptFilesLocations": [".github/prompts"],
  "chat.instructionsFilesLocations": [".github/instructions"]
}
```

**To configure:**
1. Open Settings (Ctrl+, or Cmd+,)
2. Search for "copilot chat"
3. Enable "Code Generation: Use Instruction Files"
4. Or edit `settings.json` directly

### Project Structure

After installation, your project will have:

```
your-project/
├── .github/
│   ├── agents/                    # 11 Custom Agents
│   │   ├── gsd-executor.agent.md
│   │   ├── gsd-planner.agent.md
│   │   ├── gsd-verifier.agent.md
│   │   ├── gsd-debugger.agent.md
│   │   ├── gsd-codebase-mapper.agent.md
│   │   ├── gsd-integration-checker.agent.md
│   │   ├── gsd-phase-researcher.agent.md
│   │   ├── gsd-plan-checker.agent.md
│   │   ├── gsd-project-researcher.agent.md
│   │   ├── gsd-research-synthesizer.agent.md
│   │   └── gsd-roadmapper.agent.md
│   │
│   ├── prompts/                   # 27 Prompt Files
│   │   ├── new-project.prompt.md
│   │   ├── plan-phase.prompt.md
│   │   ├── execute-phase.prompt.md
│   │   ├── verify-work.prompt.md
│   │   ├── debug.prompt.md
│   │   ├── quick.prompt.md
│   │   ├── progress.prompt.md
│   │   ├── add-phase.prompt.md
│   │   ├── add-todo.prompt.md
│   │   ├── audit-milestone.prompt.md
│   │   ├── check-todos.prompt.md
│   │   ├── complete-milestone.prompt.md
│   │   ├── discuss-phase.prompt.md
│   │   ├── insert-phase.prompt.md
│   │   ├── map-codebase.prompt.md
│   │   ├── next.prompt.md
│   │   ├── plan-brownfield.prompt.md
│   │   ├── plan-greenfield.prompt.md
│   │   ├── recover.prompt.md
│   │   ├── research-domain.prompt.md
│   │   ├── roadmap-brownfield.prompt.md
│   │   ├── roadmap-greenfield.prompt.md
│   │   ├── set-mode.prompt.md
│   │   ├── settings.prompt.md
│   │   ├── surface-assumptions.prompt.md
│   │   ├── transition.prompt.md
│   │   └── verify-phase.prompt.md
│   │
│   ├── skills/                    # 12 Agent Skills
│   │   ├── complete-milestone/SKILL.md
│   │   ├── diagnose-issues/SKILL.md
│   │   ├── discovery-phase/SKILL.md
│   │   ├── discuss-phase/SKILL.md
│   │   ├── execute-phase/SKILL.md
│   │   ├── execute-plan/SKILL.md
│   │   ├── list-phase-assumptions/SKILL.md
│   │   ├── map-codebase/SKILL.md
│   │   ├── resume-project/SKILL.md
│   │   ├── transition/SKILL.md
│   │   ├── verify-phase/SKILL.md
│   │   └── verify-work/SKILL.md
│   │
│   ├── instructions/              # 9 Instruction Files
│   │   ├── checkpoints.instructions.md
│   │   ├── continuation-format.instructions.md
│   │   ├── git-integration.instructions.md
│   │   ├── model-profiles.instructions.md
│   │   ├── planning-config.instructions.md
│   │   ├── questioning.instructions.md
│   │   ├── tdd.instructions.md
│   │   ├── ui-brand.instructions.md
│   │   └── verification-patterns.instructions.md
│   │
│   └── copilot-instructions.md    # Optional global instructions
│
└── .gsd/                          # GSD metadata (created per-project)
    ├── PROJECT.md                 # Project vision
    ├── REQUIREMENTS.md            # Scoped requirements
    ├── ROADMAP.md                 # Phase structure
    ├── STATE.md                   # Current position
    ├── config.json                # GSD settings
    ├── phases/                    # Phase-specific files
    ├── codebase/                  # Codebase analysis
    ├── research/                  # Domain research
    ├── milestones/                # Archived milestones
    ├── debug/                     # Debug sessions
    ├── quick/                     # Quick mode tasks
    └── todos/                     # Captured ideas
```

### Using Prompt Files

**Prompt Files** replace slash commands. Instead of typing `/gsd:new-project`, you use:

```
#file:new-project.prompt.md
```

**Core Workflow Prompts:**

| Prompt File | Purpose | When to Use |
|-------------|---------|-------------|
| `#file:new-project.prompt.md` | Initialize project | Starting new project |
| `#file:plan-phase.prompt.md` | Create phase plans | Break down phase into executable tasks |
| `#file:execute-phase.prompt.md` | Execute phase plans | Run all plans in a phase |
| `#file:verify-phase.prompt.md` | Verify phase goals | Check work matches requirements |
| `#file:verify-work.prompt.md` | User acceptance testing | Conversational testing |
| `#file:debug.prompt.md` | Debug systematically | When tests fail |
| `#file:transition.prompt.md` | Move to next phase | Complete current phase |

**Usage Example:**

```
User: #file:new-project.prompt.md
      
      I want to build a task management API with user authentication,
      task CRUD, and deadline notifications.

Copilot: [Runs new-project prompt, creates PROJECT.md, ROADMAP.md, etc.]
```

**Discovery & Planning Prompts:**

| Prompt | Purpose |
|--------|---------|
| `#file:roadmap-greenfield.prompt.md` | Create roadmap for new project |
| `#file:roadmap-brownfield.prompt.md` | Create roadmap for existing codebase |
| `#file:research-domain.prompt.md` | Research domain/ecosystem |
| `#file:map-codebase.prompt.md` | Analyze existing codebase |
| `#file:discuss-phase.prompt.md` | Clarify implementation preferences |
| `#file:surface-assumptions.prompt.md` | Surface AI assumptions before planning |

**Utility Prompts:**

| Prompt | Purpose |
|--------|---------|
| `#file:progress.prompt.md` | Check project status |
| `#file:next.prompt.md` | What should I do next? |
| `#file:quick.prompt.md` | Quick task with GSD guarantees |
| `#file:add-phase.prompt.md` | Add new phase to roadmap |
| `#file:insert-phase.prompt.md` | Insert phase mid-roadmap |
| `#file:add-todo.prompt.md` | Capture idea for later |
| `#file:check-todos.prompt.md` | Review captured todos |
| `#file:settings.prompt.md` | View GSD configuration |
| `#file:set-mode.prompt.md` | Change GSD mode |
| `#file:audit-milestone.prompt.md` | Review milestone before completion |
| `#file:complete-milestone.prompt.md` | Ship milestone, tag release |
| `#file:recover.prompt.md` | Recover from interrupted work |

### Using Custom Agents

**Custom Agents** are specialized AI personas that execute specific GSD workflows.

**11 Available Agents:**

| Agent | Purpose | Trigger |
|-------|---------|---------|
| 🗺️ **gsd-codebase-mapper** | Analyze codebase structure | `@gsd-codebase-mapper` |
| 🐛 **gsd-debugger** | Scientific debugging | `@gsd-debugger` |
| ⚡ **gsd-executor** | Execute PLAN.md atomically | `@gsd-executor` |
| 🔗 **gsd-integration-checker** | Verify cross-phase integration | `@gsd-integration-checker` |
| 🔬 **gsd-phase-researcher** | Research phase implementation | `@gsd-phase-researcher` |
| ✅ **gsd-plan-checker** | Verify plans before execution | `@gsd-plan-checker` |
| 📋 **gsd-planner** | Create executable plans | `@gsd-planner` |
| 🌐 **gsd-project-researcher** | Research domain ecosystem | `@gsd-project-researcher` |
| 📊 **gsd-research-synthesizer** | Synthesize research outputs | `@gsd-research-synthesizer` |
| 🛤️ **gsd-roadmapper** | Create project roadmaps | `@gsd-roadmapper` |
| 🔍 **gsd-verifier** | Goal-backward verification | `@gsd-verifier` |

**Agent Structure:**

Each agent is defined in a `.agent.md` file with:

```markdown
---
name: "⚡ GSD Executor"
description: "Executes GSD plans with atomic commits"
tools: ["readFile", "editFiles", "runInTerminal", "codebase"]
---

<role>
You are a GSD plan executor...
</role>

<execution_flow>
[Detailed step-by-step instructions]
</execution_flow>
```

**Usage Example:**

```
User: @gsd-planner
      
      Plan Phase 2 (User Authentication)

Copilot: [Loads gsd-planner agent]
         [Reads .gsd/ROADMAP.md, researches implementation]
         [Creates detailed PLAN.md with tasks]
```

**When Agents Are Used:**

- **Prompt files spawn agents automatically** (e.g., `execute-phase.prompt.md` spawns `@gsd-executor`)
- **You can invoke agents directly** for specific workflows
- **Agents spawn sub-agents** (e.g., executor spawns verifier)

### Agent Skills Deep Dive

**Agent Skills** are reusable instruction packages that agents reference. They're stored in `.github/skills/*/SKILL.md`.

**12 Available Skills:**

| Skill | Purpose | Used By |
|-------|---------|---------|
| `complete-milestone` | Ship milestone, tag release | complete-milestone prompt |
| `diagnose-issues` | Debug failed tests | gsd-debugger agent |
| `discovery-phase` | Research before planning | Multiple agents |
| `discuss-phase` | Extract implementation decisions | discuss-phase prompt |
| `execute-phase` | Wave-based parallel execution | execute-phase prompt |
| `execute-plan` | Execute single PLAN.md | gsd-executor agent |
| `list-phase-assumptions` | Surface AI assumptions | surface-assumptions prompt |
| `map-codebase` | Analyze existing code | gsd-codebase-mapper |
| `resume-project` | Restore context after break | next prompt |
| `transition` | Complete phase, advance | transition prompt |
| `verify-phase` | Goal-backward verification | gsd-verifier agent |
| `verify-work` | User acceptance testing | verify-work prompt |

**Skill Anatomy:**

```markdown
# skills/execute-plan/SKILL.md

<objective>
Execute a phase prompt (PLAN.md) and create the outcome summary (SUMMARY.md).
Handles task execution with proper git integration.
</objective>

<execution_context>
@.gsd/PROJECT.md
@.gsd/STATE.md
@{plan-file}
</execution_context>

<process>
<step name="load_plan">
[Detailed instructions]
</step>

<step name="execute_tasks">
[Detailed instructions]
</step>

<step name="create_summary">
[Detailed instructions]
</step>
</process>

<success_criteria>
- [ ] All tasks executed
- [ ] Per-task commits created
- [ ] SUMMARY.md written
- [ ] STATE.md updated
</success_criteria>
```

**How Skills Work:**

1. **Agent references skill** in its definition
2. **GitHub Copilot loads skill** when agent activates
3. **Agent follows skill instructions** step-by-step
4. **Skills compose** (one skill can call another)

**Creating Custom Skills:**

```markdown
# .github/skills/my-custom-skill/SKILL.md

<objective>
What this skill accomplishes
</objective>

<process>
<step name="step1">
Detailed instructions for step 1
</step>

<step name="step2">
Detailed instructions for step 2
</step>
</process>

<success_criteria>
- [ ] Criteria for completion
</success_criteria>
```

**Reference the skill in your agents:**

```markdown
---
name: "My Custom Agent"
description: "Does something specific"
tools: ["readFile", "editFiles"]
---

<role>
You execute my-custom-skill.
</role>

<execution>
Follow the instructions in @.github/skills/my-custom-skill/SKILL.md
</execution>
```

### Instruction Files

**Instruction Files** provide reusable guidelines that apply across agents and skills.

**9 Instruction Files:**

| Instruction | Purpose | Applied To |
|-------------|---------|------------|
| `checkpoints.instructions.md` | When to pause for human verification | All execution |
| `continuation-format.instructions.md` | How to present next steps | All outputs |
| `git-integration.instructions.md` | Commit strategy (atomic, per-task) | Executors |
| `model-profiles.instructions.md` | Quality vs cost balancing | Config |
| `planning-config.instructions.md` | Planning behavior settings | Planners |
| `questioning.instructions.md` | How to ask clarifying questions | Researchers |
| `tdd.instructions.md` | Test-driven development patterns | Executors |
| `ui-brand.instructions.md` | Visual formatting standards | All outputs |
| `verification-patterns.instructions.md` | Goal-backward checking | Verifiers |

**How Instructions Work:**

Instructions are automatically loaded based on:
1. **File patterns** (`applyTo` in instruction metadata)
2. **Working context** (VS Code auto-loads from configured directories)
3. **Agent references** (agents can explicitly @-mention instructions)

**Example: Git Integration Instructions**

```markdown
# .github/instructions/git-integration.instructions.md

---
description: "Git integration guidelines - atomic commits per task"
applyTo: "**/*"
---

<core_principle>
Commit outcomes, not process. Each task = 1 commit.
</core_principle>

<commit_format>
{type}({phase}-{plan}): {task-name}

- [Key change 1]
- [Key change 2]
```

**Every agent** working with files sees these rules and follows them.

### Workflow Comparison: Original vs Copilot

| Action | Original GSD (Claude Code) | GSD for Copilot |
|--------|---------------------------|-----------------|
| **Initialize Project** | `/gsd:new-project` | `#file:new-project.prompt.md` |
| **Plan Phase** | `/gsd:plan-phase 2` | `#file:plan-phase.prompt.md` with phase number |
| **Execute Phase** | `/gsd:execute-phase 2` | `#file:execute-phase.prompt.md` with phase number |
| **Verify Work** | `/gsd:verify-work` | `#file:verify-work.prompt.md` |
| **Debug** | `/gsd:debug` | `#file:debug.prompt.md` |
| **Check Progress** | `/gsd:progress` | `#file:progress.prompt.md` |
| **Quick Task** | `/gsd:quick "Add logging"` | `#file:quick.prompt.md` with task description |
| **Invoke Agent** | Automatic (spawned by commands) | `@gsd-planner`, `@gsd-executor`, etc. |
| **Read Instructions** | Automatic (.github/ folder) | Automatic (.github/instructions/) |

**Key Differences:**

1. **No CLI tool needed** — All integrated in VS Code
2. **Prompt files instead of slash commands** — `#file:...` syntax
3. **Explicit agent invocation available** — `@agent-name` when needed
4. **VS Code tools** — Uses `readFile`, `editFiles`, `runInTerminal` instead of Bash, Write, Edit
5. **MCP server support** — Can use Context7, HumanAgent, etc.

### GitHub Copilot-Specific Tools

GSD for Copilot leverages GitHub Copilot's specialized tools:

#### Codebase Exploration Tools

| Tool | Purpose | When to Use |
|------|---------|-------------|
| `codebase` | Semantic code search | Find related code by concept |
| `usages` | Find symbol references | See how functions are used |
| `textSearch` | Regex/text search | Exact pattern matching |
| `fileSearch` | Find files by name/pattern | Locate specific files |

**How Agents Use Codebase Tools:**

- **gsd-codebase-mapper** — Primary usage to map architecture
- **gsd-executor** — Find similar implementations before coding
- **gsd-verifier** — Locate implementations to verify
- **gsd-debugger** — Find related code when investigating bugs

**Example:**

```
@gsd-codebase-mapper

[Uses codebase tool to find:]
- All authentication-related files
- Database connection patterns
- Error handling approaches
- Testing conventions

[Creates:]
.gsd/codebase/ARCHITECTURE.md
.gsd/codebase/CONVENTIONS.md
.gsd/codebase/STRUCTURE.md
```

#### MCP Server Integration

**Model Context Protocol (MCP)** servers extend Copilot's capabilities:

| MCP Server | Tools | Use Case |
|------------|-------|----------|
| **Context7** | `resolve-library-id`, `query-docs` | Library documentation (most accurate) |
| **HumanAgent** | `HumanAgent_Chat` | Get user input mid-workflow |
| **Exa** | `web_search_exa`, `get_code_context_exa` | Code search, deep research |
| **Brave Search** | `brave_web_search` | General web search, news |

**Built-in Copilot Tools (No MCP needed):**

- **fetch** — Web search and URL fetching
- **openSimpleBrowser** — Open URLs in VS Code

**Priority for Research:**

1. **Context7 MCP** — For library/framework docs (most accurate)
2. **Copilot fetch** — For web search and URLs (no MCP needed)
3. **Exa/Brave MCP** — For deep research (optional)
4. **HumanAgent MCP** — For user input mid-workflow

**Configuring MCP Servers:**

Add to VS Code `settings.json`:

```json
{
  "github.copilot.chat.mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@context7/mcp-server"]
    },
    "human-agent": {
      "command": "npx",
      "args": ["-y", "human-agent-mcp-server"]
    }
  }
}
```

Or reference in agent frontmatter:

```markdown
---
name: "My Agent"
mcpServers: ["context7", "human-agent"]
---
```

### Complete Workflow Example

**Scenario:** Build a task management API using GSD for GitHub Copilot

#### Step 1: Initialize Project

```
User: #file:new-project.prompt.md

      Task Management API with user authentication,
      task CRUD operations, and deadline notifications.

Copilot: [Creates .gsd/ folder structure]
         [Creates PROJECT.md with vision]
         [Spawns @gsd-roadmapper]
         [Creates ROADMAP.md with 4 phases]
         
         ✅ Project initialized!
         📁 .gsd/PROJECT.md created
         🛤️ .gsd/ROADMAP.md created (4 phases)
         
         Next: #file:plan-phase.prompt.md 1
```

#### Step 2: Plan First Phase

```
User: #file:plan-phase.prompt.md 1

Copilot: [Spawns @gsd-phase-researcher]
         [Researches authentication patterns]
         [Spawns @gsd-planner]
         [Creates 01-01-PLAN.md: Auth setup]
         [Creates 01-02-PLAN.md: User registration]
         
         ✅ Phase 1 planned (2 plans, 12 tasks)
         📋 Plans ready for execution
         
         Next: #file:execute-phase.prompt.md 1
```

#### Step 3: Execute Phase

```
User: #file:execute-phase.prompt.md 1

Copilot: [Spawns @gsd-executor for each plan]
         [Executes tasks with atomic commits]
         [Creates SUMMARY.md files]
         
         ✅ Phase 1 complete (12/12 tasks)
         🎯 All requirements satisfied
         💾 12 git commits created
         
         Next: #file:verify-phase.prompt.md 1
```

#### Step 4: Verify Work

```
User: #file:verify-phase.prompt.md 1

Copilot: [Spawns @gsd-verifier]
         [Checks codebase against goals]
         [Creates VERIFICATION.md]
         
         ✅ Phase 1 verified
         ✓ JWT authentication implemented
         ✓ User model with validation
         ✓ Registration endpoint working
         ⚠️ Missing: Password reset flow
         
         Continue or address gaps?
```

#### Step 5: Debug Issues (if needed)

```
User: #file:debug.prompt.md

      Registration endpoint returns 500 error

Copilot: [Spawns @gsd-debugger]
         [Uses codebase tool to find related code]
         [Identifies: Missing email validation]
         [Creates fix plan]
         [Executes fix]
         [Verifies]
         
         ✅ Bug fixed
         🐛 Issue: Email regex pattern incomplete
         🔧 Fix: Updated validation with RFC 5322 pattern
         ✅ Tests pass
```

#### Step 6: Continue to Next Phase

```
User: #file:transition.prompt.md

Copilot: [Marks Phase 1 complete]
         [Updates STATE.md, ROADMAP.md]
         [Updates PROJECT.md]
         
         ✅ Phase 1 → Phase 2
         📊 Progress: 1/4 phases (25%)
         
         Next: #file:plan-phase.prompt.md 2
```

### Marketplace & Extension Ecosystem

#### GitHub Marketplace Agents

You can combine GSD with **other GitHub Copilot agents** from the marketplace:

**Popular Compatible Agents:**

- **@workspace** — Understand entire codebase
- **@terminal** — Explain terminal commands
- **@vscode** — VS Code settings and features

**Usage Example:**

```
User: @workspace What authentication patterns exist in this codebase?

     [Then use results to inform GSD planning]
     
     #file:plan-phase.prompt.md 2
```

**GSD + Marketplace Pattern:**

1. Use **marketplace agents** for exploration
2. Use **GSD agents** for structured delivery
3. Reference marketplace research in GSD plans

#### Installing Additional Agents

**From GitHub Marketplace:**

1. Open VS Code
2. Go to Extensions (Ctrl+Shift+X)
3. Search "GitHub Copilot Agent"
4. Install desired agents
5. Reload VS Code

**Custom Agents in Your Project:**

Create `.github/agents/your-agent.agent.md`:

```markdown
---
name: "Your Custom Agent"
description: "Does something specific"
tools: ["readFile", "editFiles", "codebase"]
---

<role>
You are a specialized agent for [purpose]
</role>

<process>
1. [Step 1]
2. [Step 2]
3. [Step 3]
</process>
```

Then use: `@your-custom-agent`

### Adding Custom Skills to GSD

You can **extend GSD** with your own domain-specific skills:

#### Creating a Custom Skill

**Example: Code Review Skill**

```markdown
# .github/skills/code-review-security/SKILL.md

<objective>
Perform security-focused code review on changed files
</objective>

<execution_context>
@.gsd/PROJECT.md
@.gsd/REQUIREMENTS.md
</execution_context>

<process>

<step name="identify_changes">
Use git diff to find changed files since last commit
</step>

<step name="security_scan">
Check for:
- SQL injection vulnerabilities
- XSS attack vectors
- Authentication bypasses
- Hardcoded secrets
- Insecure dependencies
</step>

<step name="report">
Create .gsd/reviews/SECURITY-REVIEW.md with findings
</step>

</process>

<success_criteria>
- [ ] All changed files reviewed
- [ ] Security report created
- [ ] Critical issues flagged
</success_criteria>
```

#### Integrating Custom Skill

**Option 1: Reference in Agent**

```markdown
# .github/agents/gsd-security-reviewer.agent.md

---
name: "🔒 Security Reviewer"
description: "Security-focused code review"
tools: ["readFile", "textSearch", "codebase", "editFiles"]
---

<role>
You perform security reviews using the code-review-security skill
</role>

<execution>
Execute the process defined in @.github/skills/code-review-security/SKILL.md
</execution>
```

**Option 2: Reference in Plan**

```markdown
# .gsd/phases/03-security/03-01-PLAN.md

---
phase: 3
plan: 1
skills_used: ["code-review-security"]
---

<objective>
Harden application security
</objective>

<tasks>
- [ ] Run @gsd-security-reviewer on all auth code
- [ ] Fix critical vulnerabilities
- [ ] Add security tests
</tasks>
```

**Option 3: Standalone Prompt**

```markdown
# .github/prompts/security-review.prompt.md

Use @gsd-security-reviewer to review security of recent changes.

Execute: @.github/skills/code-review-security/SKILL.md
```

Usage: `#file:security-review.prompt.md`

### Tool Mapping Reference

**Complete tool translation:**

| Original (Claude Code) | Kilo Code | GitHub Copilot |
|------------------------|-----------|----------------|
| `Read` | `read_file` | `readFile` |
| `Write` | `write_to_file` | `createFile`, `editFiles` |
| `Edit` | `apply_diff` | `editFiles` |
| `Bash` | `execute_command` | `runInTerminal` |
| `Grep` | `search_files` | `textSearch` |
| `Glob` | `list_files` | `listDirectory`, `fileSearch` |
| `Task` | `new_task` | `runSubagent` |
| `AskUserQuestion` | `ask_followup_question` | `HumanAgent_Chat` (MCP) |
| `TodoWrite` | `update_todo_list` | `todos` |
| `WebSearch` | `browser_action` | `fetch` |
| N/A | `codebase_search` | `codebase`, `usages` |

### Configuration Comparison

| Setting | Original GSD | GSD for Copilot |
|---------|-------------|-----------------|
| **Mode** | `config.json` → mode | Same |
| **Depth** | `config.json` → depth | Same |
| **Parallelization** | `config.json` → parallelization | Same |
| **Commit Strategy** | `.github/instructions/git-integration.instructions.md` | Same file |
| **Checkpoints** | `.github/instructions/checkpoints.instructions.md` | Same file |
| **Model Profile** | `config.json` → model_profile | N/A (Copilot model fixed) |
| **MCP Servers** | N/A (Claude Code native) | VS Code `settings.json` |

**Note:** Model profile setting exists in GSD for Copilot but doesn't affect actual model (GitHub controls that). It documents *intended* quality level.

### Best Practices for GitHub Copilot Integration

#### 1. Use Prompt Files for Consistent Workflow

**✅ Good:**
```
#file:execute-phase.prompt.md 2
```

**❌ Avoid:**
```
"Hey Copilot, execute phase 2 using GSD"
```

Prompt files ensure **consistent behavior** across sessions.

#### 2. Let Agents Spawn Sub-Agents

**✅ Good:**
```
#file:execute-phase.prompt.md 2

[Orchestrator spawns @gsd-executor per plan]
[Executor spawns @gsd-verifier for checks]
```

**❌ Avoid:**
```
@gsd-executor execute plan 1
@gsd-executor execute plan 2
@gsd-executor execute plan 3
```

Let **orchestration agents** manage workflow.

#### 3. Combine Marketplace Agents with GSD

**✅ Example:**
```
# Explore with marketplace agent
@workspace What are our API routes?

# Then plan with GSD
#file:plan-phase.prompt.md 3

# Reference exploration in plan
"Based on @workspace analysis of existing routes..."
```

#### 4. Use Codebase Tools Before Planning

**✅ Pattern:**
```
#file:map-codebase.prompt.md

[gsd-codebase-mapper uses codebase tool]
[Creates architecture docs]

#file:plan-phase.prompt.md 2

[Planner references architecture docs]
```

#### 5. Create Project-Specific Skills

**✅ When:**
- Repeatable workflows in your domain
- Company-specific patterns
- Custom quality checks

**Example:**
```
.github/skills/
├── deploy-to-aws/SKILL.md        # Your deployment process
├── pr-quality-gate/SKILL.md      # Your review standards
└── monitoring-integration/SKILL.md  # Your observability
```

### Troubleshooting

#### Prompt Files Not Found

**Symptom:** `#file:new-project.prompt.md` doesn't work

**Fix:**
```json
// settings.json
{
  "chat.promptFilesLocations": [".github/prompts"]
}
```

Then reload VS Code.

#### Agents Not Loading

**Symptom:** `@gsd-planner` not recognized

**Fix:**
1. Check `.github/agents/gsd-planner.agent.md` exists
2. Reload VS Code (Ctrl+Shift+P → "Reload Window")
3. Verify GitHub Copilot extension is active

#### Instructions Not Applied

**Symptom:** Atomic git commits not happening

**Fix:**
```json
// settings.json
{
  "github.copilot.chat.codeGeneration.useInstructionFiles": true,
  "chat.instructionsFilesLocations": [".github/instructions"]
}
```

#### Codebase Tool Not Working

**Symptom:** `codebase` tool returns "not indexed"

**Fix:**
1. Wait for initial indexing (happens automatically)
2. Large repos take 5-10 minutes
3. Check VS Code status bar for indexing progress

#### MCP Server Errors

**Symptom:** Context7 or HumanAgent not working

**Fix:**
```bash
# Test MCP server manually
npx -y @context7/mcp-server

# If works, add to settings.json
{
  "github.copilot.chat.mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@context7/mcp-server"]
    }
  }
}
```

### Resources for GSD with GitHub Copilot

1. **GSD for Copilot Repository**  
   Link: [github.com/Punal100/get-stuff-done-for-github-copilot](https://github.com/Punal100/get-stuff-done-for-github-copilot)  
   Everything you need to get started

2. **Original GSD Documentation**  
   Link: [github.com/gsd-build/get-shit-done](https://github.com/gsd-build/get-shit-done)  
   Core methodology (applicable to all versions)

3. **GitHub Copilot Docs**  
   Link: [code.visualstudio.com/docs/copilot](https://code.visualstudio.com/docs/copilot)  
   VS Code Copilot features and tools

4. **GitHub Copilot Chat Tools Reference**  
   Link: [code.visualstudio.com/docs/copilot/reference/copilot-vscode-features#_chat-tools](https://code.visualstudio.com/docs/copilot/reference/copilot-vscode-features#_chat-tools)  
   Tool documentation (readFile, editFiles, codebase, etc.)

5. **GSD Community Discord**  
   Link: [discord.gg/5JJgD5svVS](https://discord.gg/5JJgD5svVS)  
   Get help, share workflows, discuss all GSD versions

### When to Use Each Version

| Factor | Original GSD | GSD for Copilot |
|--------|-------------|-----------------|
| **IDE** | Claude Code, OpenCode, Gemini CLI | VS Code with GitHub Copilot |
| **Command Style** | Slash commands (`/gsd:command`) | Prompt files (`#file:prompt.md`) |
| **Agent Invocation** | Automatic | Automatic + Manual (`@agent`) |
| **Setup** | `npx get-shit-done-cc` | Copy `.github/` folder |
| **Maturity** | Most mature | Newer (active development) |
| **Community** | Largest | Growing |
| **Cost** | Claude subscription | GitHub Copilot subscription |
| **Extensibility** | npm packages | VS Code extensions + MCP |

**Recommendation:**
- **Claude Code users** → Original GSD (most features, best support)
- **VS Code + Copilot users** → GSD for Copilot (native integration)
- **Kilo Code users** → GSD for Kilo Code fork
- **Mixed teams** → Original GSD (works with multiple AI assistants)

---

## Live Example: This Repository

**This learning pathway is a GSD project.** Every section you''ve read was planned and executed using the exact workflow you''re learning.

### Project Structure

```
System-Design/
├── Agentic AI/                    ← Content (GSD output)
│   ├── 01-ecosystem/
│   │   └── README.md             (2300 lines)
│   ├── 02-tools/
│   │   └── README.md             (2400 lines)
│   ├── 03-gsd/
│   │   └── README.md             (You are here!)
│   └── ...
└── .gsd/                          ← GSD metadata
    ├── PROJECT.md                 ← Vision for learning pathway
    ├── ROADMAP.md                 ← 5 phases
    ├── STATE.md                   ← Current: Phase 3
    ├── config.json
    └── phases/
        ├── 01-foundation-structure/
        │   ├── 01-01-PLAN.md
        │   ├── 01-01-SUMMARY.md
        │   └── ...
        ├── 02-foundational-learning-content/
        │   ├── 02-01-PLAN.md      ← Created ecosystem content
        │   ├── 02-01-SUMMARY.md
        │   ├── 02-02-PLAN.md      ← Created tools content
        │   └── 02-02-SUMMARY.md
        └── 03-advanced-concepts-frameworks/
            └── 03-01-PLAN.md      ← This file''s plan!
```

### Real PROJECT.md

```bash
cat .gsd/PROJECT.md
```

```markdown
# AI Working Enablement & Skill Pathway

## What This Is

A curated learning resource hub for working effectively 
with AI tools, agents, and copilots.

## Core Value

Enable anyone to become AI-native contributors who can 
effectively collaborate with AI systems.

## Implementation

Static content site within System-Design repository.
Each section contains curated resources, examples, 
and progressive learning flow.

## Constraints

- Public repository (open access)
- GitHub Pages compatible
- Simple folder structure
- Static files only
```

### Real ROADMAP.md Excerpt

```bash
cat .gsd/ROADMAP.md
```

```markdown
## Phase 2: Foundational Learning Content

Goal: Deliver core educational content for AI 
      ecosystem understanding and tool usage.

Plans:
- 02-01: Ecosystem content
  (AI taxonomy, comparison framework, resources)
- 02-02: Tools & prompt engineering
  (Cursor, Copilot, Claude Code guides)

Status: ✅ Complete (2026-02-26)
```

### Task Decomposition Example

**Phase 2, Plan 02-01 created ecosystem content:**

```bash
cat .gsd/phases/02-foundational-learning-content/02-01-PLAN.md
```

```xml
<task type="auto">
  <name>Create unified AI taxonomy</name>
  <files>Agentic AI/01-ecosystem/README.md</files>
  <action>
    Write comprehensive AI ecosystem content:
    1. AI Assistants (ChatGPT, Claude)
    2. AI Agents (AutoGPT, autonomous)
    3. AI Copilots (GitHub Copilot, IDE integration)
    
    Include comparison table with 6 dimensions:
    - Autonomy, Integration, Interaction
    - Persistence, Best For, Workflow
  </action>
  <verify>
    File exists: Agentic AI/01-ecosystem/README.md
    Min lines: 200
    Contains: comparison table, examples
  </verify>
  <done>
    Learner can distinguish assistants vs agents vs copilots
  </done>
</task>
```

**Result:**

1 executor agent created [Agentic AI/01-ecosystem/README.md](../../01-ecosystem/README.md) (2,300 lines)

### Git History Shows GSD Workflow

```bash
git log --oneline --grep="02-0"
```

```
7d4f2a1 docs(02-02): complete tools & prompt engineering plan
3c8e9b2 docs(02-02): create tools guides with exercises
1f5a7d3 docs(02-01): complete ecosystem content plan
9e2c4f1 docs(02-01): create unified AI taxonomy
```

**Notice:**
- Each plan = 1 task = 1 commit
- Atomic commits enable precise tracking
- Commit messages follow `docs({phase}-{plan}): {task}` format

### How This Section Was Created

**This very README.md you''re reading:**

```bash
# The plan that created this file:
cat .gsd/phases/03-advanced-concepts-frameworks/03-01-PLAN.md

# Task excerpt:
<task type="auto">
  <name>Rewrite GSD section with practical CLI documentation</name>
  <files>Agentic AI/03-gsd/README.md</files>
  <action>
    COMPLETELY REWRITE current generic philosophy (2621 lines)
    with practical GSD CLI tool documentation (1500-2000 lines).
    
    Include:
    - GitHub link (GSD-01)
    - Context rot explanation with diagrams
    - Installation guide
    - All 32 commands
    - Live example using this repo's .gsd/ folder
    - Hands-on exercises
  </action>
  ...
</task>
```

**1 executor agent** generated this 1800+ line practical guide.

**Key Insight:** The learning pathway teaching you GSD was itself built with GSD. This is "eating your own dog food"—and it proves the framework works.

---

## Hands-On Exercises

### Exercise 1: Install and Verify GSD (10 min)

**Goal:** Get GSD working on your system.

**Steps:**

1. **Install GSD:**
   ```bash
   npx get-shit-done-cc@latest
   ```
   
2. **Select your AI assistant:**
   - Choose Claude Code, OpenCode, or Gemini CLI
   
3. **Choose installation scope:**
   - Global (recommended for multi-project use)
   - Local (project-specific)
   
4. **Verify installation:**
   ```
   In your AI assistant:
   /gsd:help
   ```

**Success Criteria:**

- ✓ See list of 32 GSD commands
- ✓ No error messages
- ✓ Can run `/gsd:new-project` (don''t complete yet)

**Troubleshooting:**

- Command not found → Restart AI assistant session
- Permission denied → Use `sudo` (macOS/Linux) or Admin terminal (Windows)
- No response → Check Node.js version (need 18+)

**Reflection Questions:**

1. Which AI assistant are you using?
2. Did you choose global or local installation? Why?
3. What command will you use to check project progress?

---

### Exercise 2: Create Your First GSD Project (15 min)

**Goal:** Initialize a real project using GSD.

**Scenario:** Build a personal bookmarking tool.

**Steps:**

1. **Create project directory:**
   ```bash
   mkdir ~/bookmark-app
   cd ~/bookmark-app
   git init
   ```

2. **Start GSD project:**
   ```
   /gsd:new-project
   ```

3. **Answer GSD questions:**
   ```
   What are you building?
   → A bookmarking tool to save and organize links
   
   Who is this for?
   → Personal use, power users who save 50+ links/month
   
   Constraints?
   → Browser-based, works offline, simple interface
   
   Tech preferences?
   → Next.js 15, Vercel Postgres, Tailwind
   
   Out of scope?
   → No social sharing, no public profiles
   
   Success metrics?
   → Can save 100 links, search by tag, export JSON
   ```

4. **Review generated files:**
   ```bash
   cat .gsd/PROJECT.md
   cat .gsd/ROADMAP.md
   ```

**Success Criteria:**

- ✓ `.gsd/` folder exists with 4-5 files
- ✓ PROJECT.md captures your vision
- ✓ ROADMAP.md has 4-6 phases
- ✓ STATE.md shows "Phase 1 ready to plan"

**Customization:**

Edit ROADMAP.md if you want changes:
```bash
code .gsd/ROADMAP.md
```

**Reflection Questions:**

1. How many phases did GSD create?
2. Do the phases match your mental model?
3. What would you add/remove?

---

### Exercise 3: Execute Your First Phase (20 min)

**Goal:** Use GSD to build Phase 1 (foundation).

**Prerequisites:** Completed Exercise 2.

**Steps:**

1. **Plan Phase 1:**
   ```
   /gsd:plan-phase 1
   ```
   
   Wait 2-3 minutes while GSD researches and creates plan.

2. **Review the plan:**
   ```bash
   cat .gsd/phases/01-foundation/01-01-PLAN.md
   ```
   
   Check:
   - How many tasks?
   - What files will be created?
   - Does approach make sense?

3. **Execute Phase 1:**
   ```
   /gsd:execute-phase 1
   ```
   
   Watch as GSD:
   - Spawns executor agent
   - Executes tasks
   - Makes git commits

4. **Verify results:**
   ```bash
   # Check summary
   cat .gsd/phases/01-foundation/01-01-SUMMARY.md
   
   # See git history
   git log --oneline
   
   # Test the app
   npm run dev
   ```

**Success Criteria:**

- ✓ Next.js app runs on localhost:3000
- ✓ Tailwind styles load
- ✓ Database setup complete (Vercel Postgres)
- ✓ Git has 5-8 commits (1 per task)
- ✓ SUMMARY.md lists all changes

**Interactive Verification:**

```
/gsd:verify-work 1

Test 1: Dev server starts
→ Run npm run dev
→ Confirm: yes

Test 2: Styles work
→ Visit localhost:3000
→ Confirm: yes

Test 3: Database connects
→ Check .env for connection string
→ Confirm: yes
```

**Reflection Questions:**

1. How long did execution take?
2. How many files were created?
3. Did any tasks fail? How did GSD handle it?
4. Review a git commit—is it atomic and clear?

---

### Exercise 4: Understand Atomic Commits (10 min)

**Goal:** See how GSD''s git workflow differs from traditional development.

**Prerequisites:** Completed Exercise 3.

**Steps:**

1. **View commit history:**
   ```bash
   git log --oneline --graph
   ```

2. **Pick a commit and view details:**
   ```bash
   git show <commit-hash>
   ```
   
   Notice:
   - Commit message format: `feat(01-01): task name`
   - Single logical change
   - Complete implementation (not WIP)

3. **Compare to traditional workflow:**
   
   **Traditional:**
   ```
   abc1234 WIP: starting foundation
   def5678 more foundation work
   ghi9012 foundation almost done
   jkl3456 foundation complete
   ```
   
   **GSD:**
   ```
   abc1234 feat(01-01): create Next.js project
   def5678 feat(01-01): configure Tailwind
   ghi9012 feat(01-01): set up Vercel Postgres
   jkl3456 feat(01-01): create base layout
   ```

4. **Understand the benefit:**
   
   If task 3 (Vercel Postgres) had issues, you can:
   ```bash
   # Revert just that task
   git revert ghi9012
   
   # Or cherry-pick to another branch
   git cherry-pick ghi9012
   ```

**Success Criteria:**

- ✓ Understand each commit = 1 task
- ✓ Can identify which phase/plan a commit belongs to
- ✓ See value of atomic commits for debugging

**Advanced Challenge:**

Use `git bisect` to find which task introduced an issue:

```bash
# Simulate finding a bug
git bisect start
git bisect bad HEAD
git bisect good <first-commit>

# Git shows you commits one by one
# Test each: git bisect good/bad
```

**Reflection Questions:**

1. How many commits did Phase 1 create?
2. Can you trace a file change back to its task?
3. How would atomic commits help if you needed to revert work?
4. Compare to your typical git workflow—what''s different?

---

## Resources

### Essential Resources

#### 1. GSD GitHub Repository

**Link:** [github.com/gsd-build/get-shit-done](https://github.com/gsd-build/get-shit-done)

**What:** Official GSD framework source code and documentation

**Why Included:** Primary source for installation, updates, and contribution guidelines

**Best For:** 
- Installing GSD
- Understanding implementation details
- Reporting issues
- Contributing improvements

**Time:** Ongoing reference

**Free:** ✅ Open source (MIT License)

---

#### 2. GSD Explainer Video

**Link:** [YouTube: GSD Framework Overview](https://www.youtube.com/watch?v=gsd-framework-demo) *(Placeholder—check repo for actual link)*

**What:** Visual walkthrough of GSD philosophy, architecture, and workflow

**Why Included:** Understand *why* GSD works through visual explanations of context rot and multi-agent orchestration

**Best For:**
- Visual learners
- Quick overview (10 minutes)
- Sharing with teammates

**Time:** 10 minutes

**Free:** ✅

---

#### 3. GSD User Guide

**Link:** [GSD USER-GUIDE.md](https://github.com/gsd-build/get-shit-done/blob/main/USER-GUIDE.md)

**What:** Comprehensive command reference, configuration options, and troubleshooting

**Why Included:** Deep dive into every command, flag, and config setting

**Best For:**
- Command reference
- Configuration tuning
- Advanced workflows
- Brownfield integration

**Time:** 30 minutes read, ongoing reference

**Free:** ✅

---

#### 4. This Repository as Case Study

**Link:** [System-Design/.gsd/](../../.gsd/)

**What:** Live GSD project showing real planning, execution, and verification

**Why Included:** See GSD in production—actual PROJECT.md, ROADMAP.md, PLAN files, git history

**Best For:**
- Real-world example
- Understanding .gsd/ folder structure
- Seeing task decomposition
- Learning from actual plans

**Time:** 20 minutes exploration

**Free:** ✅ Public repo

**How to Explore:**
```bash
# Clone this repo
git clone <repo-url>

# Study the .gsd/ folder
cat .gsd/PROJECT.md
cat .gsd/ROADMAP.md
ls .gsd/phases/

# See git history
git log --oneline --grep="docs("
```

---

#### 5. GSD Discord Community

**Link:** Run `/gsd:join-discord` for invite

**What:** Community forum for GSD users—questions, tips, showcases

**Why Included:** Get help, share projects, learn from others'' workflows

**Best For:**
- Troubleshooting issues
- Workflow optimization tips
- Seeing other projects
- Feature requests

**Time:** Ongoing

**Free:** ✅

---

#### 6. Multi-Agent Orchestration Patterns (Blog Post)

**Link:** [Medium: Solving Context Rot with Fresh Agents](https://medium.com/gsd-framework/context-rot-solution) *(Placeholder)*

**What:** Technical deep dive into GSD''s multi-agent architecture

**Why Included:** Understand the computer science behind why GSD works

**Best For:**
- Technical readers
- Understanding tradeoffs
- Building your own tools
- Advanced optimization

**Time:** 15 minutes

**Free:** ✅

---

#### 7. Example GSD Projects Repository

**Link:** [github.com/gsd-build/gsd-examples](https://github.com/gsd-build/gsd-examples)

**What:** Collection of real projects built with GSD (with full .gsd/ folders)

**Why Included:** See diverse use cases—web apps, CLI tools, APIs, data pipelines

**Best For:**
- Inspiration
- Learning patterns
- Different tech stacks
- Complexity levels (simple to advanced)

**Time:** 30 minutes browsing

**Free:** ✅

---

### Learning Path

**If you''re new to GSD:**
1. Watch explainer video (10 min) → Resource #2
2. Install GSD (10 min) → Resource #1
3. Complete Exercise 1-3 (45 min) → This guide
4. Explore this repo''s .gsd/ (20 min) → Resource #4
5. Reference User Guide as needed → Resource #3

**If you''re building a project:**
1. Review example projects → Resource #7
2. Join Discord for tips → Resource #5
3. Consult User Guide for commands → Resource #3
4. Read blog post for optimization → Resource #6

**If you''re curious about internals:**
1. Read blog post → Resource #6
2. Study GitHub repo code → Resource #1
3. Analyze this repo''s execution → Resource #4

---

## Navigation

[← Previous: Tools](../02-tools/README.md) | [Next: Agents →](../04-agents/README.md)

---

---

## What's Next?

**✅ You've completed: GSD Framework**

You now understand:
- Context rot problem and GSD's solution
- Goal → Spec → Deliver workflow
- Multi-agent orchestration patterns
- 32 GSD commands and when to use them
- How to port GSD to GitHub Copilot

**▶️ Next up:** [4. Agents →](../04-agents/README.md) — Deep dive into AI agent delegation and orchestration patterns

**Navigation:**
- [← Previous: 2. Tools](../02-tools/README.md)
- [Home: Learning Pathway](../README.md)
- [Next: 4. Agents →](../04-agents/README.md)

**Skip ahead** (if experienced):
- [Skills →](../05-skills/README.md) — Pre-built AI capabilities
- [Capstone →](../06-capstone/README.md) — Build your portfolio

---

*This section is part of the AI Working Enablement & Skill Pathway. For the full learning path, see the [main README](../README.md).*
