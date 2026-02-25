# 4. Agents in Depth

## Table of Contents

- [Overview](#overview)
- [Agents vs Assistants](#agents-vs-assistants)
- [Delegation Patterns](#delegation-patterns)
- [Multi-Agent Orchestration](#multi-agent-orchestration)
- [Platform Examples](#platform-examples)
- [Resources](#resources)
- [Navigation](#navigation)

## Overview

AI agents represent a paradigm shift from conversational assistants to autonomous systems capable of executing complex tasks with minimal human intervention. Understanding agent architecture, capabilities, and limitations is crucial for effectively delegating work at scale.

This section moves beyond surface-level concepts to explore how agents actually work: their decision-making loops, tool use patterns, memory systems, and coordination mechanisms. You'll learn to think in terms of delegation rather than instruction, setting up agents for success.

By mastering agent concepts and patterns, you'll gain the ability to architect agent-based workflows, troubleshoot agent failures, and design multi-agent systems that tackle problems too complex for single-agent approaches.

## Agents vs Assistants

### Autonomy Spectrum

AI assistants and agents exist on a **spectrum of autonomy**—how much they can operate independently.

```
Low Autonomy ←────────────────────────────→ High Autonomy

[Assistants]     [Copilots]     [Agents]     [Future AGI]
    │                │               │              │
ChatGPT         GitHub          AutoGPT      Hypothetical
Claude          Copilot         Devin        Full autonomy
    │                │               │              │
You direct    Suggests as   Executes with   Independent
every step     you work      oversight       operation
```

**Assistants (Low Autonomy)**
- **Control:** You're 100% in control
- **Pattern:** You ask → It responds → Waits for next instruction
- **Decision Making:** Zero autonomous decisions
- **Use Case:** Learning, brainstorming, getting explanations

**Copilots (Moderate Autonomy)**
- **Control:** You maintain control, AI proactively suggests
- **Pattern:** AI watches your work → Suggests relevant help
- **Decision Making:** AI chooses what to suggest, you choose whether to accept
- **Use Case:** Real-time coding assistance, inline completions

**Agents (High Autonomy)**
- **Control:** You set goals, agent figures out execution
- **Pattern:** You assign task → Agent plans & executes → Reports back
- **Decision Making:** Agent makes tactical decisions autonomously
- **Use Case:** Multi-step tasks, automation, complex problem-solving

**Different Autonomy = Different Mental Models**

| Aspect | Assistant Mental Model | Agent Mental Model |
|--------|------------------------|--------------------|
| **Your Role** | Driver asking for directions | Manager delegating to employee |
| **AI Role** | Map/GPS giving info | Employee executing task |
| **Communication** | Question-answer | Goal-outcome |
| **Trust Level** | Trust the information | Trust the execution |
| **Verification** | Validate answer makes sense | Verify task completed correctly |

**Trust Calibration**

As autonomy increases, you need different trust strategies:

**Assistants:** Verify responses, but no risk of unwanted actions
**Copilots:** Review suggestions before accepting
**Agents:** Set clear boundaries, verify outcomes, have rollback plans

**Example: "Create a User Model"**

**Assistant approach:**
```
You: "What should a User model include?"
Assistant: "Consider id, email, password_hash, created_at..."
You: [Take suggestion, write code yourself]
```

**Copilot approach:**
```
You type: class User
Copilot suggests: Complete class definition
You: [Accept or modify suggestion]
```

**Agent approach:**
```
You: "Create a User model with authentication fields, 
      validation, and database integration."
Agent: [Plans tasks, implements model, adds tests, commits code]
You: [Review completed work]
```

The higher the autonomy, the more you shift from "doing with help" to "reviewing what was done."

### Defining Characteristics

**What Makes an Agent an Agent?**

**1. Goal Orientation (vs Conversation Orientation)**

**Assistants:**
```
Oriented around conversation
→ Each response is self-contained
→ No persistent objective
→ Waits for your next prompt
```

**Agents:**
```
Oriented around goals
→ Given a goal, works toward completion
→ Maintains focus across multiple actions
→ Continues until goal achieved or blocked
```

**Example:**
```
Goal: "Research React 19 features and create summary doc"

Assistant: Would answer questions about React 19 if you ask
Agent: Would search docs, compile findings, format as doc, save file
```

**2. Tool Use & Action Taking**

**Assistants:**
- Generate text only
- Cannot interact with external systems
- You must copy-paste to apply suggestions

**Agents:**
- Use tools (search, file system, APIs, databases)
- Take actions (create files, run commands, make API calls)
- Change state of systems directly

**Example Tools:**
```
- search_web(query)
- read_file(path)
- write_file(path, content)
- run_command(cmd)
- query_database(sql)
- call_api(endpoint, data)
```

**3. Memory & Persistence Across Sessions**

**Assistants:**
```
Session A: Discuss plan
[Session ends]

Session B: Start fresh, explain context again
```

**Agents:**
```
Session A: Assign task, agent starts work
[Session ends]

Session B: Agent remembers task, continues from last checkpoint
```

Agents maintain:
- Task state (what's been done, what's next)
- Decisions made
- Artifacts created
- Problems encountered

**4. Error Recovery Without Human Intervention**

**Assistants:**
```
AI: [Provides broken code]
You: "This has an error"
AI: "Oh, here's the fix"
→ You had to identify and report the error
```

**Agents:**
```
Agent: [Runs code, gets error]
Agent: [Reads error, diagnoses issue]
Agent: [Attempts fix]
Agent: [Retries]
→ Handles error loop autonomously
```

**Agent Error Recovery Example:**
```
Task: Deploy application

1. Agent runs: npm run build
2. Error: "Module not found"
3. Agent diagnoses: Missing dependency
4. Agent action: npm install missing-package
5. Agent retries: npm run build
6. Success: Build complete
7. Agent continues: Deploy to server

→ You never intervened
```

**5. Multi-Step Planning**

**Assistants:** Single-step responses
```
You: "How do I deploy?"
Assistant: "Run these commands: [list]"
→ You execute each command
```

**Agents:** Multi-step execution
```
You: "Deploy the application"
Agent: 
  Step 1: Run tests
  Step 2: Build production bundle
  Step 3: Upload to server
  Step 4: Restart services
  Step 5: Verify deployment
→ Agent executes all steps
```

**Comparison Table:**

| Characteristic | Assistants | Agents |
|----------------|------------|--------|
| **Orientation** | Conversation | Goal |
| **Actions** | Text only | Uses tools |
| **Persistence** | Per-session | Cross-session |
| **Error Handling** | Ask human | Self-correct |
| **Planning** | Suggests steps | Executes plan |
| **Initiative** | Waits for prompts | Proactive |
| **Verification** | You test | Self-verifies |

**The Core Difference:**

> Assistants help you do work.  
> Agents do work for you.

You shift from "worker with AI consultant" to "manager with AI employee."

### Mental Model Shift

Working with agents requires a fundamentally different mental model than assistants.

**Old Model: Assistant (Conversational)**
```
You are: Active participant in every step
AI is: Knowledgeable consultant

Workflow:
1. You ask question
2. AI answers
3. You implement
4. You test
5. You fix issues
6. You move to next step

→ High involvement, full control
```

**New Model: Agent (Delegation)**
```
You are: Manager setting goals
AI is: Capable executor

Workflow:
1. You define goal & constraints
2. Agent plans approach
3. Agent implements
4. Agent tests
5. Agent fixes issues
6. You review outcome

→ Lower involvement, oversight control
```

**How This Changes Things:**

**1. Prompt Design Changes**

**Assistant Prompts (Detailed Instructions)**
```
"Show me how to create a REST API endpoint that:
 - Accepts POST requests
 - Validates input with Zod
 - Saves to database
 - Returns JSON response

Explain each step."

→ You want explanation to implement yourself
```

**Agent Prompts (Goals & Constraints)**
```
"Create a REST API endpoint for user registration.

Requirements:
 - POST /api/auth/register
 - Validate email and password
 - Hash password before saving
 - Return JWT token
 - Handle duplicate email errors

Constraints:
 - Use existing Express app structure
 - Follow patterns from login endpoint
 - Include unit tests

Don't:
 - Modify authentication middleware
 - Change database schema

Success criteria:
 - Endpoint works with curl
 - Tests pass
 - No duplicate code"

→ You define outcome, agent figures out steps
```

**2. Error Handling Changes**

**With Assistants:**
```
Problem occurs → You notice → You debug → You ask AI for help → You fix

→ You own the error resolution loop
```

**With Agents:**
```
Problem occurs → Agent notices → Agent debugs → Agent fixes → Agent continues

→ Agent owns error resolution, you set retry limits
```

**Agent Error Handling Setup:**
```
"If you encounter errors:
 1. Try to fix automatically (max 3 attempts)
 2. If unsolvable, document the issue and ask me
 3. Don't proceed past blocking errors
 4. Save progress before each major step"
```

**3. Workflow Integration Changes**

**Assistant Workflow:**
```
┌─ You ─────────────────────────┐
│  Think → Ask AI → Implement   │ 
│  Test → Debug → Ask AI → Fix  │
│  [Repeat for each step]        │
└────────────────────────────────┘
  → Tight feedback loop
  → You're always in the loop
```

**Agent Workflow:**
```
┌─ You ──────────┐  ┌─ Agent ────────────────────┐
│ Define goal    │→ │ Plan → Implement → Test    │
│ Set constraints│  │ Debug → Verify → Complete  │
│ Review result  │← │ [All steps autonomous]     │
└────────────────┘  └────────────────────────────┘
  → Handoff pattern
  → You check in at milestones
```

**4. Trust & Verification**

**Assistant Model:**
```
Trust: Verify each response before using
Risk: Low (you implement, you catch issues)
Review: Real-time, step-by-step
```

**Agent Model:**
```
Trust: Agent will attempt task, may make mistakes
Risk: Higher (agent takes actions directly)
Review: Batch, after completion or at checkpoints

Verification Strategy:
- Set checkpoints for critical decisions
- Review code changes before merge
- Test thoroughly before production
- Have rollback plan
```

**Mental Model Summary:**

**Thinking Shift:**
```
From: "How do I do this?" (You're the worker)
To:   "What needs to be done?" (You're the manager)
```

**Communication Shift:**
```
From: Detailed step-by-step instructions
To:   Clear goals with success criteria
```

**Control Shift:**
```
From: Control every step
To:   Control boundaries and verify outcomes
```

**Time Shift:**
```
From: Synchronous (wait for each response)
To:   Asynchronous (assign and check back)
```

**Example: Complete Mental Model Shift**

**Task: Add dark mode to app**

**Assistant Mental Model:**
```
You think:
"I need to:
 1. Ask how to implement dark mode
 2. Add theme context
 3. Ask how to persist preference
 4. Create toggle component
 5. Ask how to update all components
 6. Update CSS for each component
 7. Test manually"

→ You're thinking about HOW
→ You execute each step
```

**Agent Mental Model:**
```
You think:
"I need dark mode that:
 - Toggles between light/dark
 - Persists user preference
 - Updates all components
 - Matches design system colors

Agent should:
 - Follow our existing patterns
 - Not break current functionality
 - Include toggle in header
 - Test in both modes"

→ You're thinking about WHAT & WHY
→ Agent figures out HOW
```

**The Key Insight:**

> With assistants, you're the chef asking for recipe advice.  
> With agents, you're the customer ordering a meal.

You need to get comfortable with not seeing every step of the cooking process.

### Trust and Control

**The Trust Paradox:**

Agents are powerful because they work autonomously, but power requires trust. Building that trust while maintaining appropriate control is the key challenge.

**Trust Calibration Framework:**

```
Low Risk Tasks → High Trust (Let agent run)
High Risk Tasks → Low Trust (Tight oversight)
```

**Risk Assessment:**

**Low Risk = Safe forAutonomous Execution**
- Writing documentation
- Generating test cases
- Refactoring internal code
- Creating boilerplate structure
- Running read-only analysis

**Medium Risk = Checkpoints Needed**
- Implementing new features
- Modifying database schemas
- Changing API contracts
- Updating dependencies
- Deploying to staging

**High Risk = Tight Supervision**
- Deleting data or resources
- Deploying to production
- Modifying authentication/security
- Financial transactions
- Irreversible actions

**Maintaining Control: The Guardrail Strategy**

**1. Boundary Setting**

```markdown
Task: Refactor user authentication

PERMISSIONS:
✓ Modify files in /src/auth/
✓ Update unit tests
✓ Refactor internal functions

FORBIDDEN:
✗ Change database schema
✗ Modify API endpoints (breaking changes)
✗ Delete existing tests
✗ Deploy anywhere

→ Agent knows the safe zone
```

**2. Checkpoint Approval**

```
Agent Plan:
1. Analyze current code ✓ (Autonomous)
2. Propose refactor plan → [WAIT FOR APPROVAL]
3. Implement changes ✓ (Autonomous)
4. Run tests → [SHOW RESULTS]
5. Commit changes → [WAIT FOR APPROVAL]

→ Human decides at critical junctures
```

**3. Dry-Run Mode**

```
"Execute this task in dry-run mode:
 - Show what you WOULD do
 - Don't actually make changes
 - Explain reasoning for each step

I'll review and then give you permission to execute."

→ Preview actions before committing
```

**4. Rollback Mechanisms**

```
Before agent starts:
- Create git branch
- Back up critical data
- Document current state

If agent fails:
- Reset to previous state
- Review what went wrong
- Adjust constraints
- Retry with better guidance

→ Safety net for failures
```

**Graceful Degradation Strategies:**

**When Agents Fail: Recovery Patterns**

**Pattern 1: Incremental Fallback**
```
1. Agent attempts full autonomous execution
   ↓ [Fails]
2. Agent shows plan, asks for approval
   ↓ [Fails]
3. Agent executes one step at a time with confirmation
   ↓ [Fails]
4. Fall back to assistant mode (guide you through it)

→ Gracefully reduce autonomy until it works
```

**Pattern 2: Partial Success Acceptance**
```
Agent goal: Implement 5 features

Outcome:
✓ Feature 1: Complete
✓ Feature 2: Complete  
✗ Feature 3: Blocked (missing deps)
○ Feature 4: Not started
○ Feature 5: Not started

Action:
- Accept features 1-2
- Manually resolve feature 3 blocker
- Restart agent for features 4-5

→ Don't treat partial progress as total failure
```

**Pattern 3: Human-Agent Pairing**
```
Agent hits complex problem it can't solve

Instead of failing:
1. Agent documents the blocker
2. Agent proposes 2-3 approaches
3. You choose approach
4. Agent executes chosen path

→ Human provides strategic direction, agent handles tactics
```

**Pattern 4: Reduced Scope**
```
Original: "Build complete feature"
Agent struggles → Too complex

Reduced: "Build core functionality only"
Agent succeeds

Then: "Add edge case handling"
Agent succeeds

Finally: "Add error handling"
Agent succeeds

→ Break down further if agent overwhelmed
```

**Building Confidence: Incremental Delegation**

**Week 1: Toe in the Water**
```
Delegate: Write documentation for existing code
Risk: Very low
Goal: See agent capabilities and limitations
```

**Week 2: Simple Tasks**
```
Delegate: Generate unit tests for well-defined functions
Risk: Low (tests don't break production)
Goal: Build trust in agent's code quality
```

**Week 3: Isolated Features**
```
Delegate: Implement new standalone feature
Risk: Medium (contained blast radius)
Goal: Test agent with real work
```

**Week 4: Core Feature Work**
```
Delegate: Modify existing features
Risk: Medium-high
Goal: Agent working on production code
```

**Week 5: Complex Integration**
```
Delegate: Multi-file refactoring projects
Risk: High
Goal: Full confidence in agent capabilities
```

**Trust Indicators:**

**Green Flags (Increase Trust):**
- ✅ Agent asks clarifying questions when ambiguous
- ✅ Agent documents decisions and reasoning
- ✅ Agent runs tests before declaring done
- ✅ Agent acknowledges limitations
- ✅ Consistent quality across multiple tasks

**Red Flags (Increase Oversight):**
- ⚠️ Agent proceeds despite errors
- ⚠️ Agent makes assumptions without confirming
- ⚠️ Output quality varies wildly
- ⚠️ Agent doesn't handle edge cases
- ⚠️ Ignores constraints you specified

**The Trust Equation:**

```
Trust = (Successful Outcomes × Consistency) / Risk × Time

Increase trust by:
- More successful outcomes
- Consistent quality
- Starting with low risk
- Building over time
```

**Control vs Efficiency Tradeoff:**

```
Tight Control: Slow but safe
│    Review every step
│    
├── Checkpoint approvals
│    Agent shows plan, you approve
│
├── Boundary constraints  
│    Agent works autonomously in safe zone
│
└── Full autonomy: Fast but higher risk
     Agent completes task, you review outcome

Find your comfort level ↑
```

**Golden Rule of Agent Trust:**

> Trust, but verify.  
> Start with small, low-risk tasks.  
> Earn confidence through repeated success.  
> Never fully eliminate oversight for critical systems.

Think of it like teaching someone to drive:
- First: Empty parking lot (low risk)
- Then: Quiet neighborhood streets
- Then: Regular traffic
- Finally: Highway driving
- But even experienced drivers have accidents → insurance and rules still apply

Similarly, even "trusted" agents need appropriate guardrails.

## Delegation Patterns

### Effective Task Assignment

**Delegation to AI agents** requires a different mindset than delegating to humans. Agents need explicit structure where humans infer context.

**The Delegation Framework:**

```
Effective Delegation =
  Clear Goal +
  Sufficient Context +
  Defined Constraints +
  Success Criteria +
  Appropriate Guardrails
```

---

**1. Defining Clear Goals**

**Bad (Vague):**
```
❌ "Make the app better"
❌ "Fix the bugs"
❌ "Add some features"
```

**Good (Specific):**
```
✅ "Reduce page load time from 5s to under 2s"
✅ "Fix authentication redirect loop on logout"
✅ "Add email notification when order ships"
```

**SMART Goals for Agents:**
- **Specific:** Exactly what to build/fix
- **Measurable:** How to verify success
- **Achievable:** Within agent's capabilities
- **Relevant:** Aligns with project goals
- **Time-bound:** Reasonable completion estimate

---

**2. Providing Necessary Context**

**Context Types:**

**Project Context:**
```markdown
Project: E-commerce platform
Stack: Next.js 15 + PostgreSQL + Prisma
Hosting: Vercel
Current Phase: MVP (launch in 2 weeks)
```

**Technical Context:**
```markdown
Authentication: JWT (jose library)
State Management: React Context
Styling: Tailwind CSS
Testing: Jest + React Testing Library
```

**Task-Specific Context:**
```markdown
Relevant Files:
- src/components/Checkout.tsx (current implementation)
- src/services/stripe.ts (payment integration)
- lib/db/orders.ts (database operations)

Related Issues:
- Payment succeeds but order not created
- Happens only on mobile Safari
- Started after Stripe SDK update
```

**Example Delegation:**
```markdown
**Task:** Fix mobile Safari checkout bug

**Context:**
- E-commerce app (Next.js + Stripe)
- Recent Stripe SDK update from v3.2 → v3.5
- Payment Intent succeeds, but database order not created
- Only affects  iOS Safari (Chrome works fine)
- Error logs show: "TypeError: Cannot read 'metadata'"

**Goal:**
Payment completion should create order in all browsers

[... continue with constraints and success criteria]
```

---

**3. Specifying Success Criteria**

**Functional Criteria:**
```markdown
✅ Feature works as specified
✅ Handles expected inputs correctly
✅ Fails gracefully on invalid inputs
✅ Integrates with existing code
```

**Non-Functional Criteria:**
```markdown
✅ Performance: Response time < 200ms
✅ Security: Input sanitized, SQL injection prevented
✅ Accessibility: Keyboard navigable, screen reader friendly
✅ Maintainability: Follows project conventions
```

**Verification Criteria:**
```markdown
✅ All tests pass
✅ Manual testing checklist complete
✅ No console errors
✅ Code reviewed (by you or another agent)
```

---

**4. Setting Up Appropriate Guardrails**

**Scope Guardrails:**
```markdown
"Do NOT:
- Modify database schema (out of scope)
- Change API contracts (other code depends on them)
- Install new dependencies without approval
- Refactor unrelated code"
```

**Technical Guardrails:**
```markdown
"Must: 
- Use existing authentication middleware
- Follow our error handling pattern (AppError class)
- Maintain backward compatibility
- Add tests for new code"
```

**Quality Guardrails:**
```markdown
"Requirements:
- TypeScript strict mode (no `any` types)
- ESLint must pass with no warnings
- Test coverage > 80%
- Lighthouse accessibility score > 90"
```

### Agent Prompting Best Practices

**Agents think differently than humans.** Structure prompts for how agents process information.

---

**Pattern 1: Objective-First Structure**

**Human-Style (Context-heavy):**
```
"So we have this app, and it's been running for a while,
and users have been complaining about the search being slow,
maybe it's the database or maybe the algorithm, not sure,
but anyway we need to make it faster somehow..."

→ Agent struggles to find the objective
```

**Agent-Optimized:**
```
**Objective:** Reduce search response time from 3s to under 500ms

**Context:** Product search in e-commerce app...

→ Agent knows the goal immediately
```

**Template:**
```markdown
1. **Objective:** [One sentence - what success looks like]
2. **Context:** [Background information]
3. **Approach:** [How to achieve it, if you have preferences]
4. **Constraints:** [What NOT to do]
5. **Verification:** [How to test]
```

---

**Pattern 2: Anticipate Failure Modes**

**Basic Prompt:**
```
"Add user profile editing"
```

**Failure-Aware Prompt:**
```
"Add user profile editing

Anticipate these failure modes:
- User edits another user's profile → Verify ownership
- Concurrent edits → Handle optimistic concurrency
- Invalid data → Validate before saving
- File upload fails → Rollback other changes"
```

**Common Failure Modes by Feature Type:**

**Authentication:**
- Session expiry
- Simultaneous logins
- Brute force attacks
- Password reset token expiry

**Forms:**
- Invalid input
- Network failure mid-submit
- Duplicate submissions
- Required fields missing

**API Calls:**
- Timeout
- Rate limiting
- Invalid responses
- Authorization failures

**File Operations:**
- Permission errors
- Disk space
- Invalid file types
- Size limits exceeded

---

**Pattern 3: Specify Acceptable vs Unacceptable Approaches**

**Without Specification:**
```
"Implement caching"

→ Agent might choose:
  - In-memory (lost on restart)
  - Redis (requires new infrastructure)
  - Browser localStorage (privacy concerns)
  - Service Worker (complex)
```

**With Specification:**
```
"Implement caching

**Acceptable Approaches:**
- Browser sessionStorage (for current session)
- React Query caching (already in project)
- Simple Map() in memory for current page

**Unacceptable:**
- Do NOT use Redis (not in our stack)
- Do NOT use localStorage (privacy implications)
- Do NOT implement service worker (too complex for MVP)

**Preferred:** React Query since we already use it"
```

---

**Pattern 4: Environmental Context**

**Include:**
```markdown
**Environment:**
- Dev: local machine, hot reload, verbose logging
- Staging: Vercel preview, mirrors production, test data
- Production: real users, real money, zero downtime required

**Current Stage:** MVP pre-launch

**Implications:**
- Prioritize shipping over perfection
- OK to have technical debt (document it)
- NOT OK to skip security
- Performance nice-to-have (can optimize post-launch)
```

---

**Pattern 5: Decision-Making Authority**

**Specify what agent can decide:**

```markdown
**Agent Can Decide:**
- Variable names, function names
- Which utility library to use (lodash vs ramda)
- Code organization within files
- Specific validation messages

**Agent Cannot Decide (Ask First):**
- Database schema changes
- New npm dependencies
- API contract changes
- Architecture patterns

**Example Requiring Approval:**
"If you think this requires a database migration,
propose the migration but don't implement until I approve."
```

---

**Prompt Quality Checklist:**

Before sending prompt, verify:

- [ ] **Objective stated clearly** in first sentence
- [ ] **Context provided** (tech stack, files, current state)
- [ ] **Success criteria listed** (testable)
- [ ] **Constraints explicit** (what NOT to do)
- [ ] **Failure modes anticipated** (error handling)
- [ ] **Approaches specified** (acceptable solutions)
- [ ] **Decision authority** defined (what agent can decide)
- [ ] **Verification plan** included (how you'll test)

---

**Example: Complete Agent Prompt**

```markdown
**Objective:** Implement password reset flow for users who forget password

**Context:**
- Node.js + Express backend
- Email sending: Configured (Resend library, see lib/email.js)
- Database: PostgreSQL + Prisma
- Auth: JWT tokens (see utils/jwt.js)
- Frontend: React (password reset form exists at /reset-password)

**Requirements:**
1. POST /auth/forgot-password endpoint
   - Accepts { email }
   - Generates secure reset token (crypto.randomBytes)
   - Stores token in database with 1-hour expiry
   - Sends email with reset link
   - Returns 200 even if email doesn't exist (security)

2. POST /auth/reset-password endpoint
   - Accepts { token, newPassword }
   - Validates token not expired
   - Updates password (bcrypt hash)
   - Invalidates all existing sessions (for security)
   - Returns success

**Acceptable Approaches:**
- Use our existing User model (add reset_token, reset_token_expiry fields)
- Use bcrypt for password hashing (already in package.json)
- Use Prisma transactions for atomic updates

**Unacceptable:**
- Do NOT use new dependencies
- Do NOT send token in email body (send link instead)
- Do NOT skip token expiry check
- Do NOT allow weak passwords (min 8 chars enforced)

**Failure Modes to Handle:**
- Email service down → Log error, return 500
- Token expired → Return 400 "Token expired"
- Token invalid → Return 400 "Invalid token"
- Same token used twice → Invalidate after use

**Constraints:**
- Must follow our error handling pattern (throw AppError)
- Add to existing auth.js routes file
- Follow code style (async/await, JSDoc comments)
- No schema changes without approval (propose migration)

**Verification:**
I'll test by:
1. Requesting reset for valid email
2. Checking email received with link
3. Using link to reset password
4. Verifying old password no longer works
5. Verifying new password works
6. Trying expired token (should fail)
7. Trying same token twice (should fail second time)

**Decision Authority:**
- You decide: Token length, email subject line, error messages
- Ask me: Database migration (if schema changes needed)

**Time Estimate:** 2-3 hours
```

### Context Provisioning

Explain strategies for giving agents the context they need: what to include upfront, what agents can discover themselves, how to structure context for agent consumption, and managing context window limitations.

### Checkpoint and Verification

Detail how to build checkpoints into agent workflows: when to request human review, automated verification strategies, partial progress tracking, and recovering from agent missteps without starting over.

## Multi-Agent Orchestration

### Why Multiple Agents

Motivate multi-agent approaches: dividing complex problems by concern, enabling parallel execution, specializing agents for different tasks, and managing context limits through distribution.

### Coordination Patterns

Introduce common multi-agent patterns: sequential (agent A's output feeds agent B), parallel (multiple agents tackle independent tasks simultaneously), hierarchical (manager agent delegates to specialist agents), and collaborative (agents with shared context).

### Communication Mechanisms

Explain how agents communicate: shared artifacts (files, databases), message passing, API calls, and structured output formats. Strategies for ensuring agents understand each other's outputs.

### Conflict Resolution

Discuss handling conflicts in multi-agent systems: what happens when agents produce inconsistent outputs, strategies for detecting conflicts, approaches to resolution (priority rules, human tie-breaking, validation agents).

### Orchestration Frameworks

Survey tools and patterns for orchestrating multiple agents: frameworks like LangGraph and CrewAI, custom orchestration scripts, and when to use specialized platforms versus rolling your own coordination logic.

## Platform Examples

### GitHub Copilot Workspace

Introduce GitHub's multi-agent workspace environment: how it breaks down tasks, agents involved (planning, implementation, testing), workflow patterns, and integration with GitHub's development platform.

### Claude Projects

Explain Anthropic's approach to agentic workflows with Claude Projects: shared context across conversations, artifact persistence, and patterns for complex multi-turn agent interactions.

### Cursor Agent Mode

Detail Cursor's agent capabilities: autonomous coding sessions, file navigation and editing, how it maintains project context, and best practices for effective agent mode usage.

### Replit Agent

Describe Replit's approach to agentic development: from prompt to deployed app, how their agent handles different stages of development, and strengths/limitations of the platform.

### Emerging Platforms

Survey the broader landscape: Devin, AutoGPT, BabyAGI, and other agentic platforms. Common patterns across platforms and how to evaluate new entrants to the space.

## Resources

### LangChain Documentation on Agents
- **Type:** Official Documentation
- **Duration/Length:** 40 min read
- **Level:** Intermediate to Advanced
- **Why this matters:** Comprehensive technical guide to building AI agents with ReAct pattern, tool use, and multi-agent systems
- **Link:** [LangChain Agents](https://python.langchain.com/docs/modules/agents/)

### "AI Agents: Autonomous Systems" by Anthropic
- **Type:** Research Article
- **Duration/Length:** 25 min read
- **Level:** Intermediate
- **Why this matters:** Explains agent architectures, autonomy levels, and best practices for delegation from leading AI research lab
- **Link:** [Anthropic Research](https://www.anthropic.com/research)

### AutoGPT GitHub Repository
- **Type:** Open Source Project
- **Duration/Length:** 1-2 hours exploration
- **Level:** Advanced
- **Why this matters:** Real-world example of autonomous agent architecture - see how agents plan, execute, and self-correct
- **Link:** [AutoGPT GitHub](https://github.com/Significant-Gravitas/AutoGPT)

### "Building LLM-Powered Agents" by OpenAI
- **Type:** Technical Guide
- **Duration/Length:** 30 min read
- **Level:** Intermediate
- **Why this matters:** OpenAI's official guidance on building agents with GPT models, including tool use and orchestration patterns
- **Link:** [OpenAI Cookbook](https://cookbook.openai.com/)

### CrewAI Documentation
- **Type:** Framework Documentation
- **Duration/Length:** 35 min read
- **Level:** Intermediate
- **Why this matters:** Practical framework for building multi-agent systems with role-based delegation and coordination
- **Link:** [CrewAI Docs](https://docs.crewai.com/)

### "The Rise of AI Agents" by a16z
- **Type:** Industry Analysis Article
- **Duration/Length:** 20 min read
- **Level:** Beginner
- **Why this matters:** High-level overview of agent landscape, use cases, and future trends from leading VC perspective
- **Link:** [a16z Blog](https://a16z.com/)

## Navigation

**[← Previous: GSD Framework](../03-gsd/README.md)** | **[Next: Skills & Packages →](../05-skills/README.md)**
