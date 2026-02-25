# 3. GSD Framework

## Table of Contents

- [Overview](#overview)
- [GSD Framework Overview](#gsd-framework-overview)
- [Goal → Spec → Deliver Flow](#goal--spec--deliver-flow)
- [PRD-Driven Execution](#prd-driven-execution)
- [Task Decomposition](#task-decomposition)
- [Resources](#resources)
- [Navigation](#navigation)

## Overview

The GSD (Goal → Spec → Deliver) Framework represents a systematic approach to AI-assisted software development that bridges the gap between high-level vision and executable implementation. It's designed to maximize AI agent effectiveness while maintaining human control over strategic decisions.

This section teaches you a proven workflow for translating ideas into shipped software using AI agents as force multipliers. Rather than ad-hoc prompting and hoping for good results, GSD provides a repeatable structure that consistently produces quality outcomes.

By mastering GSD, you'll gain confidence in delegating significant portions of development work to AI while ensuring alignment with your vision, catching issues early, and maintaining architectural coherence across complex projects.

## GSD Framework Overview

### The GSD Philosophy

The GSD Framework is built on a simple but powerful philosophy: **separate strategic thinking (what to build) from tactical execution (how to build it)**.

**Core Principles:**

**1. Humans Define Goals, AI Executes Specs**

You excel at:
- Understanding business problems
- Setting priorities
- Making architectural decisions
- Evaluating tradeoffs

AI excels at:
- Generating boilerplate code
- Following detailed specifications
- Finding implementation patterns
- Maintaining consistency

**The Framework:**
```
Human → Goal (What & Why)
  |
  v
Human + AI → Spec (How, broken down)
  |
  v
AI + Human → Deliver (Implementation)
```

**2. Structure as Scaffolding**

AI has weaknesses:
- Context amnesia (forgets across sessions)
- Scope creep (tends to over-build)
- Inconsistency (different approaches each time)

Structure compensates by:
- **Written Goals:** Persistent reference AI can always review
- **Detailed Specs:** Clear boundaries preventing scope expansion
- **Verification Checkpoints:** Catching inconsistencies early

**3. AI as Capable Collaborator, Not Autopilot**

The right mental model:
```
✓ AI is a skilled junior developer with:
  - Excellent technical knowledge
  - Fast execution speed
  - Needs clear direction
  - Benefits from oversight

✗ AI is NOT:
  - Magic that reads your mind
  - Capable of unsupervised strategic decisions
  - Reliable without verification
```

**The Philosophy in Practice:**

Instead of:
```
❌ "Build a task management app"
   → Vague, AI guesses at requirements
   → Results don't match your vision
   → Lots of back-and-forth fixing
```

GSD approach:
```
✅ Goal: "Task management app for freelancers to track 
          client projects with time tracking"
✅ Spec: [15 specific, ordered tasks with acceptance criteria]
✅ Deliver: AI implements each task, you verify
   → Aligned with vision
   → Predictable progress
   → Efficient execution
```

### Why Traditional Approaches Fall Short

**The "Just Ask AI" Approach**

Many developers try ad-hoc AI usage:
```
1. Have idea
2. Prompt AI: "Build X"
3. Get something
4. Realize it's not quite right
5. Try again with more details
6. Still not right
7. Give up or spend hours fixing
```

**Common Pitfalls:**

**1. Scope Creep**

```
You: "Create a user login form"
AI: [Builds form + validation + API integration + 
     database schema + password reset + OAuth + 
     2FA + session management]

Result: Way more than you asked for, and now you have
        to understand/maintain all of it
```

Without clear boundaries, AI over-engineers.

**2. Inconsistent Quality**

```
Session 1: "Create user model"
→ AI uses classes with private fields

Session 2: "Create product model"  
→ AI uses plain objects with interfaces

Session 3: "Create order model"
→ AI uses factory functions

Result: Codebase has 3 different patterns for same concept
```

Without specs, AI reinvents approaches each time.

**3. Architectural Drift**

```
Week 1: AI suggests REST API
Week 2: AI adds GraphQL for one feature
Week 3: AI introduces RPC for another

Result: Fragmented architecture with 3 API styles
```

Without upfront decisions, architecture evolves randomly.

**4. Context Loss Across Sessions**

```
Monday: AI helps build feature A
Tuesday: Different prompts, AI forgets Monday's patterns
Wednesday: Different AI tool, starts from scratch

Result: Rebuild context every session = massive inefficiency
```

**5. The "Almost Right" Trap**

```
AI generates code that:
✓ Looks right
✓ Runs without errors
✗ Has subtle bugs
✗ Doesn't handle edge cases
✗ Misses security concerns

You ship it → Production issues
```

Without verification checkpoints, issues slip through.

**The Cost:**

- **Time:** Hours spent iterating on vague prompts
- **Quality:** Inconsistent patterns, technical debt
- **Frustration:** "AI doesn't understand what I want"
- **Waste:** Discarding AI-generated code that missed the mark

**Why Frameworks Matter:**

Structured approaches like GSD:

✓ **Prevent scope creep** with clear Goals
✓ **Ensure consistency** with detailed Specs
✓ **Maintain architecture** with upfront decisions
✓ **Preserve context** with written documentation
✓ **Catch issues early** with verification steps

**The Reality:**

> Without structure, AI is a very fast way to build the wrong thing.  
> With structure, AI is a force multiplier that ships quality code.

GSD provides that structure.

### The Three Phases

GSD structures development into three distinct, sequential phases. Each phase has clear inputs, outputs, and objectives.

```
┌─────────────────────────────────────────────────────────────┐
│  GOAL → SPEC → DELIVER                                      │
│                                                              │
│  What+Why  →  How (Detailed)  →  Implementation+Verification│
└─────────────────────────────────────────────────────────────┘
```

**Phase 1: GOAL - Define Success**

**Purpose:** Crystallize what you're building and why

**Inputs:**
- Your idea or problem
- Constraints (time, tech, requirements)
- Success criteria (what does done look like?)

**Activities:**
- Write clear problem statement
- Define scope boundaries (what's IN, what's OUT)
- Identify success criteria
- Document non-goals (what you're explicitly NOT building)

**Outputs:**
- Goal document: 1-2 pages capturing the "what" and "why"
- Clear definition of done
- Constraints and assumptions documented

**Example Goal:**
```markdown
# Goal: Freelancer Time Tracker

## Problem
Freelancers lose billable hours because they forget to track time.

## Solution
Simple time tracking app that:
- Starts/stops timers for tasks
- Organizes by client and project
- Generates weekly reports

## Success Criteria
✓ User can start timer in <2 clicks
✓ Export report as CSV
✓ Works offline (sync later)

## Non-Goals
✗ Not building invoicing
✗ Not building team features
✗ Not building mobile app (web only)
```

**Phase 2: SPEC - Plan Implementation**

**Purpose:** Break goal into executable tasks with technical decisions made

**Inputs:**
- Goal document from Phase 1
- Technical constraints
- Your architectural preferences

**Activities:**
- Choose tech stack
- Design data models
- Break down into tasks (15-30 tasks typical)
- Order tasks by dependencies
- Define acceptance criteria per task

**Outputs:**
- Detailed PRD (Product Requirements Document)
- Task list with dependencies
- Technical decisions documented
- Acceptance criteria for each task

**Example Spec (excerpt):**
```markdown
# Spec: Time Tracker Implementation

## Tech Stack
- Frontend: React + TypeScript + Tailwind
- Backend: Node.js + Express + SQLite
- Deploy: Vercel (frontend) + Railway (backend)

## Data Model
- Timer: id, taskName, clientId, startTime, endTime
- Client: id, name, hourlyRate

## Tasks
1. Create database schema for Clients and Timers
2. Build API: POST /timers/start
3. Build API: POST /timers/stop
4. Create TimerControl component (start/stop buttons)
5. Create TimerDisplay component (shows running time)
...
```

**Phase 3: DELIVER - Execute and Verify**

**Purpose:** Implement the spec with AI assistance and verify quality

**Inputs:**
- Complete Spec/PRD from Phase 2
- Code environment setup

**Activities:**
- Execute tasks sequentially (or parallel where possible)
- Use AI to implement each task
- Verify each task meets acceptance criteria
- Fix issues before moving to next task
- Track progress

**Outputs:**
- Working implementation
- Tested code
- Documentation
- Deployed product (if applicable)

**Example Deliver Task:**
```markdown
## Task 3: Build API POST /timers/stop

Prompt to AI:
"Create POST endpoint /api/timers/stop that:
- Accepts { timerId }
- Finds timer in database
- Sets endTime to current timestamp
- Returns updated timer object
- Returns 404 if timer not found
- Returns 400 if timer already stopped"

Verification:
✓ Endpoint exists and responds
✓ Successfully stops running timer
✓ Handles error cases correctly
✓ Tests pass
```

**Phase Interdependencies:**

```
Goal is complete when:
  ✓ Problem clearly stated
  ✓ Success criteria defined
  ✓ Scope boundaries set
  → Ready for Spec phase

Spec is complete when:
  ✓ All technical decisions made
  ✓ Tasks broken down with acceptance criteria
  ✓ Dependencies identified
  → Ready for Deliver phase

Deliver is complete when:
  ✓ All tasks implemented
  ✓ Acceptance criteria met
  ✓ Working product exists
  → Project complete!
```

**Key Insight:**

> Each phase transforms uncertainty into clarity.  
> Goal: "I think I want X" → Clear requirements  
> Spec: "Clear requirements" → Executable plan  
> Deliver: "Executable plan" → Working software

### When to Use GSD

**GSD Shines For:**

**✅ Greenfield Projects**
```
Starting from scratch with clear vision
→ GSD helps structure the journey from idea to implementation

Example: Building a new SaaS product, internal tool, or portfolio project
```

**✅ Substantial Features**
```
Adding significant functionality to existing projects
→ GSD ensures feature aligns with overall architecture

Example: Adding payment processing, multi-tenancy, or real-time collaboration
```

**✅ Refactoring Initiatives**
```
Restructuring code while preserving functionality
→ GSD breaks down complex refactor into safe, verifiable steps

Example: Migrating from REST to GraphQL, extracting microservices, updating state management
```

**✅ Learning Projects**
```
Building to learn new technologies or patterns
→ GSD provides structure that accelerates learning

Example: First React project, learning TypeScript, exploring new framework
```

**✅ Complex Problem Solving**
```
Multi-faceted problems requiring coordinated solutions
→ GSD breaks complexity into manageable pieces

Example: Building ETL pipeline, implementing search with ranking, creating recommendation engine
```

**When Lightweight Approaches Suffice:**

**⚠️ Quick Experiments**
```
Testing ideas quickly, may throw away
→ Overhead of GSD not worth it

Just use: Direct AI prompts, rapid prototyping
```

**⚠️ Tiny Changes**
```
Fix typo, update dependency, tweak styling
→ Don't need formal structure

Just use: Direct edits or quick AI assistance
```

**⚠️ Well-Worn Paths**
```
Repeating something you've done many times
→ You know exactly what to do

Just use: Your experience + AI for speed
```

**⚠️ Exploration Mode**
```
You don't know what you want yet
→ Need to explore before committing to structure

Just use: Prototypes, spikes, conversations with AI
```

**Decision Framework:**

```
Will this take more than 2 hours of development?
├─ NO → Probably don't need GSD
│         Quick prompts likely sufficient
│
└─ YES → Do you know exactly what to build?
          ├─ NO → Explore first, then GSD
          │        Prototype → Learn → Goal → Spec → Deliver
          │
          └─ YES → Use GSD
                   Structure prevents problems at scale
```

**The Threshold:**

| Project Scope | Approach | Why |
|---------------|----------|-----|
| <2 hours | Ad-hoc AI prompts | Overhead not worth it |
| 2-8 hours | Lightweight: Goal + Deliver | Some structure helps |
| 8+ hours | Full GSD | Structure pays dividends |
| Multi-week | Full GSD + phases | Essential for success |

**Pro Tip: Hybrid Approach**

You can mix:
```
1. Explore with quick prototypes (no GSD)
2. Learn what you want to build
3. Throw away prototype
4. Apply GSD to build it right
```

**Example:**
```
Exploration (2 hours):
"Just trying different UI layouts with AI"
→ Learn: Cards work better than list view

GSD (8 hours):
Goal: "Dashboard with card-based layout"
Spec: [Detailed tasks]
Deliver: Production-quality implementation
```

**Golden Rule:**

> If you'll care about the code quality tomorrow, use GSD today.

## Goal → Spec → Deliver Flow

### Goal Phase: Defining Success

Deep dive into the Goal phase: capturing requirements, identifying constraints, defining success criteria, and articulating both what you want and what you explicitly don't want. Emphasize clarity over completeness.

### Spec Phase: Planning Implementation

Explore the Spec phase: breaking down goals into concrete tasks, identifying technical approaches, sequencing work logically, and creating a roadmap that AI can execute. Discuss balancing detail with flexibility.

### Deliver Phase: Execution & Verification

Detail the Deliver phase: systematic task execution, continuous verification against specs, handling deviations, and closing the loop back to goals. Explain checkpoints, validation patterns, and iteration strategies.

### Phase Transitions

Describe how to navigate transitions between phases: when a goal is "ready" to spec, when a spec is "ready" to deliver, and how to handle discoveries that require backtracking to earlier phases.

## PRD-Driven Execution

### What is a PRD in GSD Context

Explain Product Requirements Documents adapted for AI-agent execution: living documents that act as single source of truth, bridge human strategic thinking with agent tactical execution, and maintain project coherence.

### PRD Structure & Components

Detail effective PRD structure: executive summary, goals and non-goals, user stories or use cases, technical requirements, success criteria, and constraints. Show how each section guides different aspects of development.

### Writing PRDs for AI Agents

Provide guidelines for writing PRDs that AI can execute effectively: level of detail sweet spot, structuring for sequential reading, calling out ambiguities explicitly, and providing examples of desired outcomes.

### Maintaining PRD Relevance

Discuss strategies for keeping PRDs current as projects evolve: when to update vs when to create addendums, versioning approaches, and using PRDs as learning artifacts that improve over time.

## Task Decomposition

### Principles of Effective Decomposition

Explain core principles: breaking large problems into independently valuable chunks, ordering tasks by dependencies, sizing tasks for single-session execution, and creating clear success criteria per task.

### Granularity: Finding the Right Size

Discuss task sizing tradeoffs: too large means overwhelming context and difficulty troubleshooting failures; too small means overhead and fragmentation. Heuristics for right-sizing tasks for AI execution.

### Dependency Mapping

Teach how to identify and document task dependencies: which tasks must happen first, which can be parallelized, and how to sequence work to maximize progress while minimizing rework.

### Task Templates

Provide reusable patterns for common task types: "implement endpoint" task structure, "create UI component" template, "add test coverage" pattern, and "refactor for pattern X" format. Templates accelerate planning and improve consistency.

### From Tasks to Prompts

Bridge from task planning to execution: translating task descriptions into effective AI prompts, providing necessary context, specifying acceptance criteria, and setting up verification steps.

## Resources

### Notion's Guide to PRD Writing
- **Type:** Article  
- **Duration/Length:** 20 min read
- **Level:** Beginner to Intermediate
- **Why this matters:** Comprehensive guide to writing Product Requirements Documents with templates and real examples from Notion's team
- **Link:** [Notion PRD Guide](https://www.notion.so/)

### "Shape Up" by Basecamp
- **Type:** Free Online Book
- **Duration/Length:** 3-4 hours read
- **Level:** Intermediate
- **Why this matters:** Methodology for structuring product development work into manageable cycles - principles align well with GSD approach
- **Link:** [Shape Up Book](https://basecamp.com/shapeup)

### "The Holloway Guide to Technical Recruiting and Hiring"
- **Type:** Article Series
- **Duration/Length:** 30 min read (Task Breakdown section)
- **Level:** Intermediate
- **Why this matters:** Excellent section on breaking down complex technical projects into estimable tasks
- **Link:** [Holloway Guide](https://www.holloway.com/g/technicalrecruiting-hiring)

### Atlassian's Project Planning Guide
- **Type:** Documentation
- **Duration/Length:** 25 min read
- **Level:** Beginner
- **Why this matters:** Practical framework for project breakdown, task dependencies, and milestone planning
- **Link:** [Atlassian Guides](https://www.atlassian.com/work-management/project-management)

### "Making of a Manager" - Task Delegation Chapter
- **Type:** Book Chapter Summary
- **Duration/Length:** 15 min read
- **Level:** Intermediate
- **Why this matters:** Principles of effective delegation that apply equally to AI agents as to human team members
- **Link:** Available at major book retailers

### Linear's Product Development Methodology
- **Type:** Blog Article
- **Duration/Length:** 18 min read
- **Level:** Intermediate
- **Why this matters:** Modern approach to structuring development work with clear goals, specs, and execution cycles
- **Link:** [Linear Blog](https://linear.app/blog)

## Navigation

**[← Previous: Tools & Platforms](../02-tools/README.md)** | **[Next: Agents in Depth →](../04-agents/README.md)**
