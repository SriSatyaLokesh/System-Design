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

**PRD = Product Requirements Document**

In traditional software development, PRDs document what to build for stakeholders and teams. In GSD/Agentic AI context, PRDs serve a dual purpose:

**1. Single Source of Truth**

The PRD becomes the canonical reference that:
- Documents decisions so they don't need to be remade
- Persists across AI sessions (solves context loss)
- Aligns all contributors (human and AI)
- Prevents scope creep with explicit boundaries

**2. AI Agent Instruction Manual**

AI agents use PRDs to:
- Understand the complete project vision
- Generate code that aligns with requirements
- Make micro-decisions within defined constraints
- Self-verify implementation against criteria

**The Shift:**

**Traditional PRD:**
```
Audience: Human developers
Purpose: Communicate what stakeholders want
Format: Business-focused, user stories
Detail Level: High-level, devs fill in technical gaps
```

**GSD/AI PRD:**
```
Audience: AI agents (+ humans)
Purpose: Enable autonomous execution
Format: Technical + business context
Detail Level: Specific enough AI doesn't guess wrong
```

**Example Difference:**

**Traditional:**
> "Users should be able to log in to the system."

**GSD/AI:**
> "Users authenticate via email/password using JWT tokens.
> - POST /auth/login endpoint accepts email + password
> - Returns JWT valid for 7 days
> - Invalid credentials return 401 with error message
> - Successful login redirects to /dashboard
> - No social auth in MVP (explicit non-goal)"

The AI version eliminates ambiguity that would cause AI to over-engineer or guess incorrectly.

**Why PRDs Matter for AI:**

**Without PRD:**
```
Session 1: AI builds login (guesses at implementation)
Session 2: AI forgets session 1 approach
Session 3: AI uses different patterns
→ Inconsistent codebase
```

**With PRD:**
```
Session 1: AI reads PRD, implements per spec
Session 2: AI reads PRD, stays consistent
Session 3: AI reads PRD, follows same patterns
→ Coherent codebase
```

**Mental Model:**

Think of PRD as:
- **Contract** between you and AI agent
- **Blueprint** AI executes from
- **Reference manual** AI consults repeatedly
- **Quality checklist** for verifying outcomes

### PRD Structure & Components

**Best-in-Class PRD Template:**

For a comprehensive, battle-tested PRD structure, see:

📄 **[Best PRD Template](https://github.com/SriSatyaLokesh/best-prd-template)**

This template has been refined through real-world usage and provides a complete framework for both human and AI collaboration.

**Core Sections of an Effective AI-Ready PRD:**

---

**1. Executive Summary**

**Purpose:** 2-3 sentence project overview

**What to Include:**
- What are you building?
- Who is it for?
- Why does it matter?

**Example:**
```markdown
## Executive Summary

A developer portfolio website that showcases projects, skills, and
contact information. Targeted at software engineers seeking employment
or freelance opportunities. Differentiates through clean design and
fast load times (< 2 seconds).
```

**Why AI Needs This:**
- Provides context for all micro-decisions
- Helps AI prioritize (e.g., "fast load times" → optimize assets)

---

**2. Goals & Non-Goals**

**Purpose:** Crystal clear boundaries

**Goals (What you WILL build):**
```markdown
## Goals

### Primary Goals
- Display 6-10 featured projects with descriptions
- Contact form with email integration
- Mobile-responsive design
- Deployed to production with custom domain

### Secondary Goals (Nice-to-have)
- Dark mode toggle
- Animated section transitions
- Blog integration (if time permits)
```

**Non-Goals (What you WILL NOT build):**
```markdown
## Non-Goals

- ❌ User authentication (not needed)
- ❌ Backend database (static site)
- ❌ Content management system
- ❌ E-commerce functionality
- ❌ Multi-language support
- ❌ Native mobile apps

Rationale: Keeping scope minimal for MVP launch in 2 weeks.
```

**Why This Section is Critical:**
- Prevents AI from over-engineering
- Stops feature creep before it starts
- AI can say "that's out of scope" when you request extras

---

**3. User Stories / Use Cases**

**Purpose:** Define user interactions

**Format:**
```markdown
## User Stories

**As a** [user type]
**I want** [goal]
**So that** [benefit]

**Acceptance Criteria:**
- [ ] Specific testable condition 1
- [ ] Specific testable condition 2
```

**Example:**
```markdown
### User Story 1: View Projects

**As a** potential employer
**I want** to browse developer's featured projects
**So that** I can assess their skills and experience

**Acceptance Criteria:**
- [ ] Projects displayed in grid layout (3 columns desktop, 1 mobile)
- [ ] Each project shows: title, description, tech stack, links
- [ ] Clicking thumbnail opens project details
- [ ] "View Code" button links to GitHub repo
- [ ] "Live Demo" button links to deployed project
- [ ] Projects load in < 1 second
```

**Why AI Needs This:**
- Provides clear implementation targets
- Acceptance criteria = verification checklist
- AI knows when feature is "done"

---

**4. Technical Requirements**

**Purpose:** Specify architecture and tech stack

**What to Include:**
- Technology choices (languages, frameworks, libraries)
- Architecture decisions (SPA vs MPA, REST vs GraphQL)
- External dependencies (APIs, services)
- Performance requirements
- Browser/device support
- Security considerations

**Example:**
```markdown
## Technical Requirements

### Tech Stack
- **Frontend:** React 18 + TypeScript + Vite
- **Styling:** Tailwind CSS
- **Deployment:** Vercel
- **Forms:** Formspree (email handling)
- **Analytics:** Plausible (privacy-focused)

### Architecture Decisions
- Single-page application (SPA) with client-side routing
- No backend server (serverless functions for contact form only)
- Static generation for fast initial load
- Code-splitting for optimal bundle size

### Performance Targets
- First Contentful Paint: < 1.5s
- Lighthouse score: > 90
- Bundle size: < 200KB gzipped

### Browser Support
- Chrome, Firefox, Safari, Edge (latest 2 versions)
- Mobile: iOS Safari 14+, Chrome Android

### Security
- HTTPS only (Vercel provides)
- Form spam protection (Formspree built-in)
- No sensitive data stored client-side
```

**Why This Matters:**
- AI understands constraints ("must use React")
- Prevents architectural drift
- Performance requirements guide optimization decisions

---

**5. Success Criteria**

**Purpose:** Define "done"

**Functional Success:**
```markdown
## Success Criteria

### Functional Requirements
- [ ] All 6 sections render correctly
- [ ] Navigation works (smooth scroll to sections)
- [ ] Contact form submits and shows confirmation
- [ ] All external links open in new tabs
- [ ] Responsive on mobile, tablet, desktop
- [ ] Works without JavaScript (progressive enhancement)
```

**Quality bar:**
```markdown
### Quality Requirements
- [ ] No console errors or warnings
- [ ] All images optimized (WebP format)
- [ ] Accessibility: WCAG AA compliant
- [ ] SEO: Meta tags, Open Graph, Twitter Card
- [ ] Performance: Lighthouse score > 90
```

**Launch Criteria:**
```markdown
### Launch Readiness
- [ ] Custom domain configured
- [ ] SSL certificate active
- [ ] Analytics tracking verified
- [ ] Tested on 5 different devices
- [ ] All placeholder content replaced
- [ ] Resume PDF uploaded and linked
```

---

**6. Constraints**

**Purpose:** Document limitations

```markdown
## Constraints

### Time
- MVP must ship within 2 weeks
- Daily time budget: 2-3 hours

### Budget
- $0/month (free tier services only)
- Vercel free tier, Formspree free tier

### Technical
- No backend server (static hosting only)
- Must work offline after initial load (PWA optional)
- Accessibility is required, not optional

### Scope
- Focus on quality over quantity of features
- 6-8 projects maximum (curated, not comprehensive)
```

**Why AI Needs Constraints:**
- Makes practical trade-offs ("no server" → client-side only)
- Respects time budget (chooses simpler implementations)
- Prioritizes correctly (accessibility required → include from start)

---

**7. Open Questions / Risks**

```markdown
## Open Questions

- Should projects filter by technology?
  - Decision: Not in MVP, add if user feedback requests

- Dark mode: auto-detect or toggle?
  - Decision: Toggle in header, respect system preference as default

## Risks

| Risk | Mitigation |
|------|------------|
| Contact form spam | Use Formspree's built-in spam protection |
| Slow image loading | Lazy load below fold, optimize all images |
| Browser compatibility | Test on BrowserStack early |
```

**Using the PRD:**

Every AI prompt should reference the PRD:
```
"According to our PRD (see PROJECT.md), implement the contact
form section following the technical requirements (React + TypeScript)
and meeting the success criteria (form validation, confirmation message)."
```

### Writing PRDs for AI Agents

**AI-Assisted PRD Creation:**

You don't have to write PRDs alone! Modern AI tools have built-in skills for PRD generation:

**🤖 GitHub Copilot + Awesome-Copilot Extension:**
- Install: [awesome-copilot VS Code extension](https://marketplace.visualstudio.com/items?itemName=mohitmishra.awesome-copilot)
- Includes PRD writing templates and patterns
- Helps structure requirements and technical specs
- Suggests acceptance criteria based on user stories

**🧠 Claude Code (Claude Sonnet 4.5):**
- Has deep understanding of PRD best practices
- Can critique and improve your PRD drafts
- Excellent at identifying gaps or ambiguities
- Helps break down high-level goals into detailed specs

**Prompt Pattern for PRD Generation:**

```markdown
**To Claude/Copilot:**

I need to create a PRD for [project brief].

Follow this structure:
1. Executive Summary
2. Goals & Non-Goals
3. User Stories with Acceptance Criteria
4. Technical Requirements
5. Success Criteria
6. Constraints

My project: [describe in 2-3 sentences]

Key requirements:
- [Requirement 1]
- [Requirement 2]
- [Requirement 3]

Generate a comprehensive PRD following best practices.
```

**Guidelines for Effective AI-Ready PRDs:**

**1. The Detail Sweet Spot**

**Too Vague:**
```markdown
❌ "Build a good user experience"
```

**Too Specific:**
```markdown
❌ "Use #3B82F6 for the primary button background with
    2px border radius and 0.3s cubic-bezier(0.4, 0, 0.2, 1)
    transition on the transform property when hovering"
```

**Just Right:**
```markdown
✅ "Primary buttons use blue color scheme (Tailwind blue-500)
    with subtle hover animation. Maintain accessibility contrast
    standards (WCAG AA minimum)."
```

**The Rule:**
- Specify **what** and **why**
- Let AI determine **how** (within constraints)
- Provide examples when patterns matter

---

**2. Structure for Sequential Reading**

AI reads PRDs top-to-bottom. Structure accordingly:

**Good Order:**
```
1. Executive Summary (context)
2. Goals & Non-Goals (boundaries)
3. User Stories (what to build)
4. Technical Requirements (how to build)
5. Success Criteria (definition of done)
6. Constraints (limitations)
```

Each section builds on previous ones.

**In Practice:**
- AI reads "Goals" → understands scope
- AI reads "Non-Goals" → won't over-engineer
- AI reads "Technical Requirements" → uses right tools
- AI reads "Success Criteria" → knows when done

---

**3. Call Out Ambiguities Explicitly**

**Instead of leaving AI to guess:**
```markdown
❌ "Implement user authentication"
```

**Be explicit about what's decided vs open:**
```markdown
✅ "Implement user authentication:
    
    Decided:
    - Email + password (no social auth in MVP)
    - JWT tokens with 7-day expiry
    - Bcrypt for password hashing
    
    Open (AI choose):
    - Which JWT library (jose, jsonwebtoken, etc.)
    - Database table structure (optimize as needed)
    - Specific field validation patterns"
```

**Pattern:**
```markdown
### [Feature Name]

**Hard Requirements:**
- [Must-have 1]
- [Must-have 2]

**Preferences:**
- [Nice-to-have 1]
- [Nice-to-have 2]

**Open to AI:**
- [Decision AI can make]
- [Implementation detail AI chooses]

**Explicitly Out:**
- [Thing not to include]
```

---

**4. Provide Examples of Desired Outcomes**

**Abstract Requirements:**
```markdown
✗ "Create a clean, modern card layout"
```

**Concrete Examples:**
```markdown
✓ "Create card components similar to GitHub repository cards:
   - Title + description + metadata row
   - Subtle border, shadow on hover
   - Consistent spacing (padding: 1.5rem)
   
   Reference: https://github.com/explore
   
   Or provide design mockup: see design/cards.png"
```

**Types of Examples:**

**Code Examples:**
```markdown
"Folder structure should follow this pattern:

src/
├── components/
│   ├── Button/
│   │   ├── Button.tsx
│   │   ├── Button.test.tsx
│   │   └── index.ts
│   └── Card/
└── ...

Each component in own folder with test and index."
```

**Data Examples:**
```markdown
"API should return this shape:

{
  "user": {
    "id": "usr_abc123",
    "email": "user@example.com",
    "name": "John Doe",
    "created_at": "2026-01-15T10:30:00Z"
  },
  "token": "eyJhbG..."
}"
```

**Visual Examples:**
```markdown
"UI layout:

┌─────────────────────────────┐
│ Header (Logo + Nav)         │
├─────────────────────────────┤
│                             │
│  Content Area               │
│  (centered, max-width 1200) │
│                             │
├─────────────────────────────┤
│ Footer                      │
└─────────────────────────────┘"
```

---

**5. Use Consistent Terminology**

Pick terms and stick with them:

**Inconsistent:**
```markdown
❌ Section 1: "User accounts"
❌ Section 2: "User profiles"
❌ Section 3: "Member data"
```

**Consistent:**
```markdown
✅ Throughout PRD: "users" and "user accounts"
```

**Create a glossary in complex PRDs:**
```markdown
## Terminology

- **User:** Anyone with an account (authenticated)
- **Visitor:** Browsing without account (anonymous)
- **Admin:** User with elevated permissions
- **Project:** User's work portfolio entry
- **Skill:** Technology or capability tag
```

---

**6. Version Your PRD**

```markdown
# Project: Developer Portfolio

**Version:** 1.2
**Last Updated:** 2026-02-25
**Status:** In Development

## Changelog

### v1.2 (2026-02-25)
- Added dark mode requirement
- Removed blog integration (deferred to v2)
- Updated tech stack (Vite → Next.js)

### v1.1 (2026-02-20)
- Clarified performance targets
- Added accessibility requirements

### v1.0 (2026-02-15)
- Initial PRD
```

**Why Versioning Matters:**
- AI references specific version
- You track evolution of requirements
- Team stays aligned on current spec

---

**PRD Writing Workflow with AI:**

**Step 1: Brain Dump**
```markdown
You: "I want to build [project]. Here are my rough ideas:
- [Idea 1]
- [Idea 2]
- [Idea 3]

Help me structure this into a PRD."
```

**Step 2: AI Generates Draft**
Claude/Copilot creates structured PRD.

**Step 3: You Refine**
- Add domain knowledge AI lacks
- Delete over-engineered suggestions
- Clarify ambiguities
- Add constraints (time, budget)

**Step 4: AI Reviews**
```markdown
You: "Review this PRD. Identify:
- Gaps or missing information
- Ambiguities that could cause issues
- Over-scoped features to cut
- Technical risks to address"
```

**Step 5: Iterate**
Refine based on AI feedback.

**Step 6: Finalize**
When PRD feels complete, start implementation.

---

**Common Pitfalls:**

**1. PRD Too Long**
- If PRD > 2000 words, probably too detailed
- Break into phases or modules

**2. PRD Too Short**
- If PRD < 500 words, probably too vague
- AI will guess and guess wrong

**3. Requirements Hidden in Prose**
```markdown
❌ "We think it would be nice if users could maybe
    filter projects, and it might be good to have
    some kind of search functionality..."

✅ **Feature: Project Filtering**
    - Filter by technology (dropdown)
    - Filter by year (range slider)
    - Filters combine (AND logic)
```

**4. No Acceptance Criteria**
Every feature needs testable criteria.

**5. Forgetting Non-Goals**
Not saying what you WON'T build = scope  creep.

---

**Golden Rule:**

> Write PRDs for your future self (or AI agent) who joins the project cold in 3 weeks and needs to understand everything quickly.

If the PRD confuses you after you've slept on it, it will confuse AI even more.

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
