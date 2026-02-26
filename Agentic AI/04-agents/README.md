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

**The Context Challenge:**

Agents need information to work effectively, but:
- Too little context → Agents make wrong assumptions
- Too much context → Waste tokens, slower responses
- Wrong context → Agents focus on irrelevant details

**Goal:** Provide just enough, just-in-time context.

---

**What to Include Upfront:**

**Essential Context (Always Provide):**

1. **Task Definition**
   ```markdown
   What: Build user authentication
   Why: Enable secure access to protected resources
   Scope: Register, login, logout
   ```

2. **Technical Environment**
   ```markdown
   Stack: Node.js 20 + Express + PostgreSQL
   Key Dependencies: bcrypt, jsonwebtoken, Prisma
   Patterns: Async/await, error middleware
   ```

3. **Constraints & Boundaries**
   ```markdown
   Must: Follow existing auth patterns
   Must Not: Change database schema without approval
   Performance: Response < 1s
   ```

4. **Success Criteria**
   ```markdown
   Working: User can register and login
   Tested: Unit tests pass
   Verified: Manual testing checklist complete
   ```

---

**What Agents Can Discover:**

**Let agents find when possible:**

✅ **Code Patterns**
```
"Follow the pattern used in existing endpoints"
→ Agent reads code and infers structure
```

✅ **File Locations**
```
"Similar to the login function"
→ Agent searches codebase
```

✅ **Dependencies**
```
"Use bcrypt for hashing"
→ Agent checks if installed, reads docs
```

✅ **API Documentation**
```
"Integrate with Stripe"
→ Agent can read Stripe docs online
```

**When to be explicit:**

❌ **Custom/Proprietary Logic**
```
"Use our custom auth flow" ← Explain it
→ Agent can't discover internal decisions
```

❌ **Implicit Conventions**
```
"Follow our naming conventions" ← Show examples
→ Agent can't infer unwritten rules
```

❌ **Cross-System Dependencies**
```
"This affects the mobile app" ← Specify implications
→ Agent can't see external systems
```

---

**Structuring Context for Agents:**

**Pattern 1: Layered Context**

```markdown
# High-Level (Always read)
Task: Implement OAuth2 login
Goal: Users can sign in with Google

# Technical Details (Read if needed)
<details>
<summary>OAuth Flow Specifics</summary>

1. User clicks "Sign in with Google"
2. Redirect to Google OAuth consent
3. Google redirects back with code
4. Exchange code for tokens
5. Fetch user info
6. Create/update user in database
7. Return JWT
</details>

# Reference (Only if unclear)
<details>
<summary>Relevant Files</summary>

- `src/auth/oauth.ts` - OAuth utilities
- `src/models/User.ts` - User model
- `config/oauth.ts` - OAuth configuration
</details>
```

**Pattern 2: Progressive Disclosure**

```markdown
**Start here:**
Implement user search endpoint: GET /api/users/search?q=<query>

**If you need database details:**
Users table has: id, email, name, created_at
Use Prisma client (`prisma.user.findMany`)

**If you need performance specs:**
Must return results in < 500ms
Limit: 20 results max
Index exists on email and name fields

**If you need examples:**
See `/api/products/search` for similar search implementation
```

**Pattern 3: Context by Role**

```markdown
# For Planning Agent
- Project goals and constraints
- High-level architecture
- Available components

# For Implementation Agent  
- Specific task requirements
- Technical patterns to follow
- File locations and structures

# For Testing Agent
- Success criteria
- Edge cases to cover
- Testing utilities available
```

---

**Managing Context Window Limitations:**

**Problem:** Modern AI models have context limits (e.g., ~200K tokens for Claude)

**Solutions:**

**1. Context Pruning**
```markdown
# Instead of:
❌ "Read all 50 files in src/"

# Do:
✅ "Key files:
   - src/auth/login.ts (main auth logic)
   - src/models/User.ts (user model)
   - lib/jwt.ts (token generation)
   
   Other files follow same patterns."
```

**2. Summarize Large Context**
```markdown
# Instead of:
❌ [Paste entire 5000-line legacy codebase]

# Do:
✅ "Legacy auth system uses sessions stored in Redis.
   Key functions: createSession(), validateSession(), destroySession().
   We're migrating to JWT - new code should not use sessions."
```

**3. Context Pointers**
```markdown
# Instead of:
❌ [Include all API docs inline]

# Do:
✅ "Use Stripe SDK (v10.x docs: stripe.com/docs/api).
   Focus on: PaymentIntents, Customers, Webhooks."
```

**4. Chunked Context Loading**
```markdown
Phase 1: Agent plans approach
→ Provide: High-level context only

Phase 2: Agent implements specific part
→ Provide: Detailed context for that part only

Phase 3: Agent tests
→ Provide: Test requirements and examples
```

---

**Context Provisioning Strategies:**

**Strategy 1: Minimal + On-Demand**

```
Initial Prompt: [Minimal essential context]

Agent: "I need more details about X"
You: [Provide X details]

Agent: Proceeds with full context

→ Efficient, but interactive
```

**Strategy 2: Just-Enough Upfront**

```
Initial Prompt: [Everything agent likely needs]

Agent: Completes task autonomously

→ Faster, but may waste tokens
```

**Strategy 3: Hybrid**

```
Initial Prompt: 
  - Essential context (always needed)
  - Pointers to additional context ("See X if needed")

Agent: Decides what to retrieve

→ Balanced approach
```

---

**Context Templates:**

**Template: New Feature**
```markdown
**Feature:** [Name]
**Goal:** [What user can do]

**Technical Context:**
- Stack: [Technologies]
- Location: [Where code goes]
- Patterns: [Similar features to reference]

**Requirements:** [Functional specs]
**Constraints:** [What to avoid]
**Success Criteria:** [How to verify]

**Context References:**
- Similar feature: [Link/file]
- API docs: [URL if external]
- Design decisions: [Why we're doing this]
```

**Template: Bug Fix**
```markdown
**Bug:** [Description]
**Impact:** [Who/what is affected]

**Current Behavior:** [What happens now]
**Expected Behavior:** [What should happen]

**Context:**
- Reproduction steps: [How to trigger]
- Error logs: [Relevant messages]
- Recent changes: [What might have caused this]
- Affected files: [Where bug likely is]

**Constraints:** [What not to break while fixing]
```

**Template: Refactoring**
```markdown
**Refactor:** [What to improve]
**Why:** [Motivation]

**Current State:** [How it works now]
**Desired State:** [How it should work]

**Scope:**
- Files: [What to refactor]
- Tests: [What must still pass]
- Behavior: [What must not change]

**Context:**
- Patterns to follow: [New structure]
- Similar refactors: [Examples]
- Performance goals: [If applicable]
```

---

**Best Practices:**

✅ **Do:**
- Start with minimal context, add as needed
- Use collapsible sections for optional details
- Provide examples over explanations
- Link to docs rather than pasting docs
- Update context as you learn what agents actually need

❌ **Don't:**
- Dump entire codebase in context
- Assume agent knows your conventions
- Provide outdated context
- Mix multiple concerns in one context block
- Forget to specify what agent can decide vs must ask

### Checkpoint and Verification

**Why Checkpoints Matter:**

Agents can execute autonomously for hours, but:
- Wrong assumptions compound over time
- Late-stage failures waste all prior work  
- No visibility until completion might be too late

**Solution:** Strategic checkpoints for validation and course correction.

---

**When to Add Checkpoints:**

**After High-Impact Decisions:**
```markdown
Task: Refactor authentication system

Checkpoint 1: [AFTER PLANNING]
→ Agent proposes refactor approach
→ You review before implementation starts
→ Prevents entire wrong direction
```

**Before Irreversible Actions:**
```markdown
Task: Database migration

Checkpoint 2: [BEFORE MIGRATION]
→ Agent shows migration SQL
→ You verify no data loss
→ Then agent executes
```

**At Natural Break Points:**
```markdown
Task: Build 3-step checkout flow

Checkpoint 3: [AFTER EACH STEP]
→ Agent completes step 1 (cart)
→ You verify cart works
→ Agent proceeds to step 2 (shipping)
→ You verify shipping works  
→ Agent proceeds to step 3 (payment)
```

**After Long-Running Work:**
```markdown
Task: Generate 50 integration tests

Checkpoint 4: [AFTER FIRST 5]
→ Agent generates 5 tests
→ You review quality/pattern
→ Agent adjusts approach
→ Agent completes remaining 45
```

---

**Checkpoint Types:**

**1. Plan Approval Checkpoint**

```markdown
Agent Task: Implement search feature

[Agent generates plan]

Plan:
1. Add search input to UI
2. Create /api/search endpoint
3. Implement full-text search with PostgreSQL
4. Add debouncing for performance
5. Cache results in Redis

→ [CHECKPOINT: Review plan]

You: "Plan looks good, but skip Redis caching for now (MVP)."

Agent: Proceeds with adjusted plan
```

**2. Design Checkpoint**

```markdown
Agent Task: Design user profile page

[Agent proposes design]

Design:
- Left sidebar: Avatar, bio, stats
- Main content: Posts grid
- Top bar: Edit profile button

→ [CHECKPOINT: Design review]

You: "Move edit button to sidebar, add settings tab."

Agent: Updates design, then implements
```

**3. Implementation Checkpoint**

```markdown
Agent Task: Build payment flow (3 phases)

Phase 1: Cart total calculation ✅
→ [CHECKPOINT: Test cart calculation]
You: "Works! Continue."

Phase 2: Stripe integration ✅
→ [CHECKPOINT: Test payment]
You: "Works! Continue."

Phase 3: Order confirmation ✅
→ [CHECKPOINT: Test end-to-end]
You: "Complete!"
```

**4. Testing Checkpoint**

```markdown
Agent Task: Write tests for auth module

[Agent writes tests]

Tests:
✓ User registration
✓ Login with valid credentials
✓ Login with invalid credentials
✓ Token expiration

→ [CHECKPOINT: Review test coverage]

You: "Missing: password reset flow, concurrent sessions."

Agent: Adds missing tests
```

---

**Automated Verification Strategies:**

**Strategy 1: Continuous Testing**

```bash
# Agent implements feature
# After each file change:
→ Run relevant tests automatically
→ Agent sees results immediately
→ Agent fixes if tests fail
→ Continue when tests pass
```

**Example:**
```markdown
Agent: "I've implemented the login function."

[Auto-run: npm test -- auth.test.ts]

Result: 3/5 tests pass
  ✓ Valid login succeeds
  ✓ Invalid password fails
  ✗ Missing email handling
  ✗ SQL injection prevention
  ✓ Token generation

Agent: "I'll fix the failing tests."
[Agent adjusts code]
[Auto-run: tests again]

Result: 5/5 tests pass ✓

Agent: "Login implementation complete."
```

**Strategy 2: Type Checking**

```bash
# Agent writes TypeScript code
→ Run tsc --noEmit after each change
→ Agent sees type errors immediately
→ Agent fixes before proceeding
```

**Strategy 3: Linting**

```bash
# Agent writes code
→ Run eslint automatically
→ Catches common mistakes
→ Enforces style consistency
```

**Strategy 4: Build Verification**

```bash
# Agent makes changes
→ Run build after each phase
→ Ensures no breaking changes
→ Catches integration issues early
```

---

**Partial Progress Tracking:**

**Problem:** Agent fails at task 8 of 10. Do you lose all progress?

**Solution: Incremental Commits**

```markdown
Task: Implement 10 API endpoints

Agent approach:
1. Implement endpoint 1
2. Test endpoint 1
3. [COMMIT: "feat: add user GET endpoint"]
4. Implement endpoint 2  
5. Test endpoint 2
6. [COMMIT: "feat: add user POST endpoint"]
...
8. Implement endpoint 8
9. Test endpoint 8 [FAILS]

Outcome:
✅ Endpoints 1-7 committed (saved)
❌ Endpoint 8 broken
○ Endpoints 9-10 not attempted

→ You have 7 working endpoints
→ Only need to fix endpoint 8
```

**Pattern: Checkpoint Commits**

```bash
git checkout -b feature/agent-work

# Agent works on task 1
[COMMIT] "task 1 complete"

# Agent works on task 2
[COMMIT] "task 2 complete"

# Agent works on task 3
[FAILS]

→ Rollback to task 2 commit
→ Fix task 3 differently
→ Progress not lost
```

---

**Progress Visibility Patterns:**

**Pattern 1: Explicit Progress Updates**

```markdown
Agent: "Starting task: Build checkout flow (5 steps)"

Agent: "[1/5] ✓ Cart component created"
Agent: "[2/5] ✓ Shipping form implemented"
Agent: "[3/5] ⚙️  Working on payment integration..."
...

→ You know exactly where agent is
```

**Pattern 2: Task Board Integration**

```markdown
Agent updates GitHub issues automatically:

[ ] Cart component
[ ] Shipping form
[ ] Payment integration
[ ] Order confirmation
[ ] Email receipt

↓

[✓] Cart component
[🔄] Shipping form (in progress)
[ ] Payment integration
[ ] Order confirmation
[ ] Email receipt
```

**Pattern 3: Artifact Versioning**

```markdown
Agent generates artifacts with versions:

- plan_v1.md (initial plan)
- plan_v2.md (adjusted after checkpoint)
- implementation_draft.ts (first attempt)
- implementation_final.ts (after fixes)

→ Full audit trail of agent's work
```

---

**Recovering from Agent Missteps:**

**Scenario 1: Wrong Approach**

```markdown
Agent: [Implements complex caching system]

Checkpoint: You review
You: "This is over-engineered. We just need simple in-memory cache."

❌ Don't: "Start over from scratch"

✅ Do: "Keep the cache interface you created, but simplify the implementation:
  - Remove Redis dependency
  - Use a Map() instead
  - Keep TTL logic
  - Remove cluster support"

Agent: [Adjusts implementation (30 min vs 3 hour redo)]
```

**Scenario 2: Code Doesn't Work**

```markdown
Agent: "Login implemented."

Testing: Login fails with 500 error

❌ Don't: "Fix it" (vague)

✅ Do:
  1. Show error logs
  2. Describe what you tried
  3. Point to suspicious code
  4. Give specific fix direction

Example: "Login returns 500. Error: 'Cannot read property id of undefined'.
  Issue seems to be in line 45 where you access user.id before
  checking if user exists. Add null check first."

Agent: [Fixes specific issue]
```

**Scenario 3: Partial Success**

```markdown
Agent task: Implement 5 features

Outcome:
✓ Feature 1: Perfect
✓ Feature 2: Perfect  
⚠️  Feature 3: Works but inefficient
✗ Feature 4: Broken
○ Feature 5: Not started

✅ Recovery:
1. Commit features 1-2 (save progress)
2. Create checkpoint: "Features 1-2 complete"
3. Ask agent to optimize feature 3
4. Ask agent to fix feature 4
5. Ask agent to implement feature 5

→ Build on success, fix failures incrementally
```

---

**Checkpoint Prompt Patterns:**

**Pattern 1: Explicit Checkpoints**

```markdown
Task: Migrate user authentication to OAuth

1. Analyze current auth system
   → [STOP: Show me your analysis]

2. Design OAuth integration
   → [STOP: Show me the design, wait for approval]

3. Implement OAuth flow
   → [STOP: Show me working demo]

4. Migrate existing users
   → [STOP: Show migration plan before executing]

5. Remove old auth code
   → [STOP: Confirm everything works first]
```

**Pattern 2: Conditional Checkpoints**

```markdown
Task: Optimize database queries

Rules:
- If query optimization > 30% faster: Proceed
- If query optimization < 10% faster: Stop, consult me
- If query breaks existing functionality: Stop immediately
- If unsure about approach: Stop, ask first
```

**Pattern 3: Threshold Checkpoints**

```markdown
Task: Generate test cases

- After first 5 tests: Stop, I'll review pattern
- After 25 tests: Stop, check if we have good coverage
- After 50 tests: Stop, assess if more needed
- If edge case unclear: Stop, ask for guidance
```

---

**Verification Checklist:**

Before considering agent task "complete":

**Functional Verification:**
- [ ] Feature works as specified
- [ ] Edge cases handled
- [ ] Error states covered
- [ ] Integration points working

**Technical Verification:**
- [ ] Tests written and passing
- [ ] Code follows project patterns
- [ ] No new linter errors
- [ ] No new type errors
- [ ] Performance acceptable

**Quality Verification:**
- [ ] Code is readable
- [ ] Comments where needed
- [ ] No obvious security issues
- [ ] No hardcoded secrets

**Documentation Verification:**
- [ ] README updated if needed
- [ ] API docs updated
- [ ] Comments explain why, not what

---

**Best Practices:**

✅ **Do:**
- Add checkpoints before irreversible actions
- Use automated verification where possible
- Commit progress incrementally
- Make recovery paths explicit
- Celebrate partial success

❌ **Don't:**
- Wait until end to verify
- Discard partial work on failure
- Accept "looks good" without testing
- Skip verification "just this once"
- Punish agents for asking questions at checkpoints

## Multi-Agent Orchestration

### Why Multiple Agents

**Single Agent Limitations:**

```
One agent trying to:
- Plan architecture
- Write backend code
- Write frontend code
- Write tests
- Review security
- Deploy to production

Problems:
1. Context overload (can't hold everything)
2. Mode switching (planning ↔ coding ↔ testing)
3. Loss of specialization
4. Difficult to parallelize
5. Errors compound across concerns
```

**Multi-Agent Solution:**

```
Instead:
┌─────────────────┐
│ Architect Agent │ → Designs system structure
└─────────────────┘
        ↓
┌─────────────────┐   ┌─────────────────┐
│ Backend Agent  │   │ Frontend Agent │ → Parallel implementation
└─────────────────┘   └─────────────────┘
        ↓                   ↓
┌───────────────────────────────────┐
│         Testing Agent          │ → Verifies both
└───────────────────────────────────┘
```

---

**Benefits of Multiple Agents:**

**1. Separation of Concerns**

```markdown
Instead of one agent doing everything:

✗ Agent 1: Plan + Code + Test + Deploy
  → Context switches, loses focus

✓ Agent A: Planning only
✓ Agent B: Coding only
✓ Agent C: Testing only
  → Each stays in its domain
```

**2. Parallel Execution**

```markdown
Sequential (Single Agent):
[Backend] → [Frontend] → [Tests]
Time: 6 hours

Parallel (Multi-Agent):
[Backend] 
[Frontend] } simultaneous
[Tests]    
Time: 2 hours

→ 3x faster
```

**3. Specialized Expertise**

```markdown
Each agent optimized for its role:

Security Agent:
  "You are a security expert. Analyze code for:
   - SQL injection
   - XSS vulnerabilities
   - Authentication flaws
   - Data exposure risks"

Performance Agent:
  "You are a performance expert. Identify:
   - N+1 queries
   - Unnecessary re-renders
   - Bundle size issues
   - Cache opportunities"

→ Deeper expertise per domain
```

**4. Context Management**

```markdown
Single Agent Context:
[████████████████████] 200K tokens (maxed out)
→ Can't fit more information

Multi-Agent Context:
Agent A: [████████░░░░░░░░░░░░] 80K (architecture)
Agent B: [█████████░░░░░░░░░░░] 90K (implementation)
Agent C: [██████░░░░░░░░░░░░░░] 60K (testing)
→ Total effective context: 230K tokens
```

---

**When to Use Multiple Agents:**

**Use Multi-Agent for:**

✅ **Large projects**
```
Project: Full e-commerce platform
→ Too much for one agent's context
```

✅ **Complex workflows**
```
Workflow: Design → Review → Implement → Test → Deploy
→ Distinct stages benefit from specialization
```

✅ **Parallel tasks**
```
Tasks: Build 5 microservices simultaneously  
→ 5 agents = 5x speed
```

✅ **Quality gates**
```
Flow: Dev agent codes → Security agent reviews
→ Independent verification
```

---

**Stick with Single Agent for:**

❌ **Simple tasks**
```
Task: Add a button to a page
→ Overhead not worth it
```

❌ **Tightly coupled work**
```
Task: Refactor single file
→ Hard to split meaningfully
```

❌ **Exploratory work**
```
Task: "Investigate why performance is slow"
→ Needs holistic exploration
```

---

**Example: Multi-Agent E-Commerce Build**

**Single Agent Approach:**
```markdown
Agent: Build e-commerce site

Agent does (sequentially):
1. Design architecture
2. Set up database
3. Build auth system
4. Build product catalog
5. Build cart
6. Build checkout
7. Write all tests
8. Deploy

Time: 20 hours (sequential)
Context: Constantly maxed out
Quality: Spread too thin
```

**Multi-Agent Approach:**
```markdown
Architect Agent:
  "Design system architecture"
  Output: Architecture document
  Time: 2 hours

  ↓

Parallel Phase 1:
  Auth Agent: Build authentication (2 hours)
  Product Agent: Build catalog (3 hours)
  Cart Agent: Build cart (2 hours)

  ↓

Integration Agent:
  "Connect all services" (1 hour)

  ↓

Parallel Phase 2:
  Testing Agent: Write integration tests (2 hours)
  Security Agent: Security audit (2 hours)

  ↓

Deployment Agent:
  "Deploy to production" (1 hour)

Total Time: ~8 hours (60% faster)
Context: Each agent focused
Quality: Specialized attention per area
```

### Coordination Patterns

**Coordinating multiple agents** requires clear patterns to prevent chaos.

---

**Pattern 1: Sequential (Pipeline)**

**Structure:**
```
Agent A → Agent B → Agent C

Each agent's output becomes next agent's input
```

**Example: Code Generation Pipeline**
```markdown
Planning Agent:
  Input: "Build user registration"
  Output: Technical specification
        ↓
Coding Agent:
  Input: Technical specification
  Output: Source code
        ↓
Testing Agent:
  Input: Source code + specification
  Output: Test suite
        ↓
Review Agent:
  Input: Code + tests
  Output: Approval or revision requests
```

**When to use:**
- Each stage depends on previous completion
- Clear handoff points
- Quality gates between stages

**Pros:**
- Simple to reason about
- Clear dependencies
- Easy to debug (check each stage)

**Cons:**
- Slower (no parallelism)
- Blocked if one agent stalls

---

**Pattern 2: Parallel (Fan-out/Fan-in)**

**Structure:**
```
          Start
            ↓
    ┌─────┼─────┐
    ↓       ↓       ↓
 Agent A  Agent B  Agent C  (parallel)
    ↓       ↓       ↓
    └─────┼─────┘
            ↓
        Combine
```

**Example: Microservices Development**
```markdown
Architecture:
  Input: System requirements
  Output: Service boundaries
        ↓
        Split tasks:
        │
   ┌────┼────┐
   │      │      │
   ↓      ↓      ↓
Auth    Product  Payment  (parallel agents)
Agent   Agent    Agent
   │      │      │
   └────┼────┘
        ↓
Integration Agent:
  Combines all services
```

**When to use:**
- Independent tasks
- No dependencies between agents
- Time-critical (need speed)

**Pros:**
- Maximum speed (true parallelism)
- Scales horizontally
- Failure isolation

**Cons:**
- More complex coordination
- Need integration step
- Harder to debug

---

**Pattern 3: Hierarchical (Manager/Worker)**

**Structure:**
```
       Manager Agent
            │
    ┌─────┼─────┐
    ↓       ↓       ↓
 Worker1  Worker2  Worker3
    │       │       │
    └───────┼─────┘
            │
       Manager (aggregates)
```

**Example: Code Review System**
```markdown
Manager Agent:
  1. Receives: "Review this PR"
  2. Breaks down:
     - Files changed: 15
     - Assigns to workers:
       * Worker 1: Files 1-5
       * Worker 2: Files 6-10
       * Worker 3: Files 11-15
  3. Collects worker results
  4. Produces: Comprehensive review

Worker Agents:
  - Each reviews assigned files
  - Reports back to manager
  - Manager synthesizes final review
```

**When to use:**
- Task can be subdivided
- Need central coordination
- Dynamic workload distribution

**Pros:**
- Dynamic scaling (add workers as needed)
- Central oversight
- Load balancing

**Cons:**
- Manager is bottleneck
- Manager complexity
- More coordination overhead

---

**Pattern 4: Collaborative (Shared Context)**

**Structure:**
```
       Shared Workspace
       (files, database)
              ↑↓
    ┌─────┼─────┐
    ↑↓      ↑↓      ↑↓
Agent A  Agent B  Agent C

(All agents read/write shared state)
```

**Example: Codebase Maintenance**
```markdown
Shared: Git repository

Refactor Agent:
  - Improves code structure
  - Commits changes

Test Agent:
  - Pulls latest code
  - Adds missing tests
  - Commits tests

Docs Agent:
  - Pulls latest code
  - Updates documentation
  - Commits docs

All agents work on same repo, coordinate via git
```

**When to use:**
- Shared artifact (code, document)
- Iterative refinement
- Multiple perspectives needed

**Pros:**
- Natural collaboration
- Shared understanding
- Emergent quality

**Cons:**
- Conflict potential
- Coordination complexity
- Race conditions

---

**Pattern 5: Debate/Consensus**

**Structure:**
```
Agent A: Proposes solution X
Agent B: Critiques, proposes Y
Agent C: Synthesizes X + Y → Z

→ Iterative until consensus
```

**Example: Architecture Decision**
```markdown
Proposal Agent:
  "Use microservices architecture"
  Reasoning: [scalability, independence]

Critic Agent:
  "Microservices adds complexity"
  Alternative: "Monolith with modules"
  Reasoning: [simpler, team size, timeline]

Synthesis Agent:
  Reviews both arguments
  Decision: "Modular monolith now,
             split to microservices later"
  Reasoning: Best of both approaches
```

**When to use:**
- High-stakes decisions
- Multiple valid approaches
- Need robust solution

**Pros:**
- Considers multiple perspectives
- Higher quality decisions
- Catches blind spots

**Cons:**
- Slower (iterative)
- Can be indecisive
- Requires synthesis capability

---

**Choosing a Pattern:**

| Pattern | Use When | Speed | Complexity |
|---------|----------|-------|------------|
| **Sequential** | Clear stages, dependencies | Slow | Low |
| **Parallel** | Independent tasks | Fast | Medium |
| **Hierarchical** | Dividable work, coordination needed | Fast | High |
| **Collaborative** | Shared artifact, iterative | Medium | High |
| **Debate** | Critical decisions, multiple perspectives | Slow | Medium |

---

**Hybrid Patterns:**

**Example: Full Development Workflow**

```markdown
Phase 1: Debate (Architecture decision)
  → Multiple agents propose, discuss, consensus

Phase 2: Hierarchical (Task breakdown)
  → Manager splits work to workers

Phase 3: Parallel (Implementation)
  → Workers implement independently

Phase 4: Collaborative (Integration)
  → All agents refine shared codebase

Phase 5: Sequential (Deployment)
  → Test → Security → Deploy

→ Different patterns for different phases
```

### Communication Mechanisms

**Agents need to exchange information.** How you design communication affects reliability and debuggability.

---

**Mechanism 1: Shared Files**

**How it works:**
```
Agent A writes: output.json
Agent B reads: output.json
Agent B writes: result.json
Agent C reads: result.json
```

**Example:**
```markdown
Planning Agent:
  Writes: plan.md
  Content:
  ```
  # Implementation Plan
  - Feature 1: User auth
  - Feature 2: Dashboard
  - Feature 3: Reports
  ```

Coding Agent:
  Reads: plan.md
  Implements each feature
  Writes: implementation_status.json
  Content:
  ```json
  {
    "completed": ["User auth", "Dashboard"],
    "inProgress": ["Reports"],
    "blocked": []
  }
  ```

Testing Agent:
  Reads: implementation_status.json
  Tests completed features
  Writes: test_results.json
```

**Pros:**
- Simple to implement
- Easy to inspect (humans can read files)
- Persistent (survives agent restarts)
- Version control friendly

**Cons:**
- File naming conflicts
- No real-time communication
- Manual synchronization

**Best for:** Sequential workflows, document handoffs

---

**Mechanism 2: Database/Shared State**

**How it works:**
```sql
Agent A: INSERT INTO tasks (id, status, result)
Agent B: SELECT * FROM tasks WHERE status='pending'
Agent B: UPDATE tasks SET status='complete'
```

**Example:**
```markdown
Workflow Table:
| task_id | agent      | status      | output          |
|---------|------------|-------------|---------------|
| 1       | planner    | complete    | plan.md       |
| 2       | backend    | in_progress | null          |
| 3       | frontend   | pending     | null          |
| 4       | testing    | pending     | null          |

Backend Agent:
  1. SELECT * WHERE task_id=2
  2. Performs work
  3. UPDATE tasks SET status='complete', output='...' WHERE task_id=2

Frontend Agent:
  Polls: SELECT * WHERE agent='frontend' AND status='pending'
  Starts when backend complete
```

**Pros:**
- Centralized state
- Query capabilities
- Atomic updates (transactions)
- Multiple agents can read simultaneously

**Cons:**
- Database dependency
- Schema design needed
- Connection management

**Best for:** Complex workflows, status tracking, multiple agents

---

**Mechanism 3: Message Queue**

**How it works:**
```
Agent A: PUBLISH(queue="tasks", message={...})
Agent B: SUBSCRIBE(queue="tasks")
Agent B: Receives message, processes, ACK
```

**Example:**
```markdown
Queue: code_review_requests

Dev Agent:
  ```python
  publish("code_review_requests", {
    "pr_id": 123,
    "files": ["auth.ts", "user.ts"],
    "author": "dev_agent"
  })
  ```

Review Agent (listening):
  ```python
  message = subscribe("code_review_requests")
  # message = {pr_id: 123, files: [...], ...}
  
  review_result = perform_review(message["files"])
  
  publish("code_review_results", {
    "pr_id": 123,
    "status": "approved",
    "comments": [...]
  })
  
  ack(message) # Remove from queue
  ```

Dev Agent (listening for results):
  ```python
  result = subscribe("code_review_results")
  process_review_feedback(result)
  ```
```

**Pros:**
- Async (agents don't block)
- Reliable (messages persist until acknowledged)
- Scalable (multiple workers per queue)
- Decoupled (agents don't need to know each other)

**Cons:**
- Infrastructure requirement (RabbitMQ, Redis, etc.)
- More complex
- Debugging harder

**Best for:** High-volume, distributed systems, async workflows

---

**Mechanism 4: API Calls**

**How it works:**
```
Agent A: HTTP POST to Agent B's endpoint
Agent B: Processes request, returns response
```

**Example:**
```markdown
Agent B (runs as service):
  ```python
  @app.post("/analyze-code")
  def analyze(code: str):
      result = perform_analysis(code)
      return {"issues": result}
  ```

Agent A:
  ```python
  response = requests.post(
      "http://agent-b/analyze-code",
      json={"code": "function login() {...}"}
  )
  
  issues = response.json()["issues"]
  # Process issues
  ```
```

**Pros:**
- Synchronous (immediate response)
- Standard protocol (HTTP/REST)
- Request/response clear
- Easy testing (curl, Postman)

**Cons:**
- Agents must run simultaneously
- Network dependency
- Timeout handling needed

**Best for:** Synchronous interactions, service-oriented agents

---

**Mechanism 5: Structured Output Formats**

**The Key Problem:**

Agents produce text, but next agent needs structured data.

**Solution: Enforce Output Schema**

**Example: JSON Schema**

```markdown
Agent A Prompt:
  "Analyze code and output JSON matching this schema:
  
  {
    "type": "object",
    "properties": {
      "issues": {
        "type": "array",
        "items": {
          "type": "object",
          "properties": {
            "severity": {"enum": ["low", "medium", "high"]},
            "line": {"type": "number"},
            "message": {"type": "string"}
          },
          "required": ["severity", "line", "message"]
        }
      }
    }
  }"

Agent A Output:
  ```json
  {
    "issues": [
      {"severity": "high", "line": 42, "message": "SQL injection risk"},
      {"severity": "low", "line": 15, "message": "Unused variable"}
    ]
  }
  ```

Agent B:
  Can safely parse and process JSON
```

---

**Format Options:**

**JSON:**
```json
{
  "task": "implement_auth",
  "status": "complete",
  "files": ["auth.ts", "user.ts"],
  "tests_passed": true
}
```
✅ **Pros:** Universal, parseable, typed
❌ **Cons:** Verbose, JSON formatting errors

---

**YAML:**
```yaml
task: implement_auth
status: complete
files:
  - auth.ts
  - user.ts
tests_passed: true
```
✅ **Pros:** Human-readable, less verbose
❌ **Cons:** Indentation sensitive, parsing issues

---

**Markdown + Frontmatter:**
```markdown
---
task: implement_auth
status: complete
---

# Implementation Summary

Completed authentication system with:
- JWT tokens
- Password hashing
- Session management

Files modified:
- auth.ts
- user.ts
```
✅ **Pros:** Human + machine readable, rich content
❌ **Cons:** More complex parsing

---

**XML (less common):**
```xml
<result>
  <task>implement_auth</task>
  <status>complete</status>
  <files>
    <file>auth.ts</file>
    <file>user.ts</file>
  </files>
</result>
```
✅ **Pros:** Schema validation (XSD)
❌ **Cons:** Verbose, less popular in modern systems

---

**Ensuring Agents Understand Each Other:**

**Strategy 1: Explicit Contracts**

```markdown
Planning Agent Output Contract:
  Format: JSON
  Schema:
  {
    "features": [{ "name": str, "priority": int, "description": str }],
    "dependencies": [str],
    "timeline": str
  }

Coding Agent Input Contract:
  Expects: JSON matching planning agent's output schema
  Required fields: features[].name, features[].description
```

**Strategy 2: Validation Layer**

```python
def validate_agent_output(output, expected_schema):
    try:
        validate(instance=output, schema=expected_schema)
        return True
    except ValidationError as e:
        log_error(f"Agent output invalid: {e}")
        return False

# Between agents:
planner_output = planner_agent.run()
if validate_agent_output(planner_output, PLANNER_SCHEMA):
    coder_agent.run(input=planner_output)
else:
    handle_error()
```

**Strategy 3: Self-Describing Outputs**

```json
{
  "_meta": {
    "agent": "planner_v1",
    "timestamp": "2026-02-25T10:30:00Z",
    "schema_version": "1.0"
  },
  "data": {
    "features": [...],
    "timeline": "2 weeks"
  }
}
```

→ Next agent knows: who produced this, when, what version

---

**Communication Best Practices:**

✅ **Do:**
- Define clear contracts between agents
- Validate outputs before passing to next agent
- Use structured formats (JSON, YAML)
- Include metadata (timestamp, agent ID, version)
- Version your schemas
- Log all inter-agent communication

❌ **Don't:**
- Rely on free-form text between agents
- Assume agents understand implicit formats
- Skip validation
- Use brittle parsing (regex on natural language)
- Change formats without versioning

### Conflict Resolution

**When multiple agents work together, conflicts are inevitable.**

---

**Types of Conflicts:**

**1. Output Conflicts**

```markdown
Scenario: Two agents review same code

Agent A (Security Focus):
  "This code is insecure - use parameterized queries"
  Recommendation: Rewrite with prepared statements

Agent B (Performance Focus):
  "This code is too slow - use raw SQL with indexes"
  Recommendation: Optimize with direct queries

→ Conflicting recommendations
```

**2. Resource Conflicts**

```markdown
Scenario: Two agents modify same file

Agent A:
  Modifies: src/auth.ts (adds OAuth)

Agent B:
  Modifies: src/auth.ts (adds 2FA)

→ Git merge conflict
```

**3. Priority Conflicts**

```markdown
Scenario: Limited resources

Agent A: "Deploy feature X now (high priority)"
Agent B: "Fix critical bug Y first (urgent)"

→ Both can't go first
```

**4. Logical Conflicts**

```markdown
Scenario: Consistency requirements

Frontend Agent:
  Creates: POST /api/users (expects {email, password})

Backend Agent:
  Implements: POST /api/users (expects {username, email, password})

→ Contract mismatch
```

---

**Detecting Conflicts:**

**Strategy 1: Schema Validation**

```python
# Define expected contract
API_CONTRACT = {
    "endpoint": "/api/users",
    "method": "POST",
    "request": {"email": "string", "password": "string"},
    "response": {"id": "number", "token": "string"}
}

# Frontend agent produces:
frontend_contract = {...}

# Backend agent produces:
backend_contract = {...}

# Detect conflict:
if frontend_contract != backend_contract:
    raise ConflictError("API contract mismatch")
```

**Strategy 2: Automated Testing**

```markdown
Integration Tests (run between agent phases):

1. Frontend agent creates UI
2. Backend agent creates API
3. Run integration tests:
   → Do they work together?

If tests fail:
  → Conflict detected
```

**Strategy 3: Diff Analysis**

```bash
# Agent A makes changes
git checkout -b agent-a
[Agent A modifications]
git commit -m "Agent A work"

# Agent B makes changes
git checkout main
git checkout -b agent-b  
[Agent B modifications]
git commit -m "Agent B work"

# Detect conflict:
git merge agent-a
→ CONFLICT in src/auth.ts
```

**Strategy 4: Consistency Checks**

```python
def check_consistency(agent_outputs):
    issues = []
    
    # Check for contradictions
    if agent_a.recommendation == "use REST" and \
       agent_b.recommendation == "use GraphQL":
        issues.append("API style conflict")
    
    # Check for incompatibilities  
    if agent_a.requires("postgres") and \
       agent_b.requires("mongodb"):
        issues.append("Database conflict")
    
    return issues
```

---

**Resolution Strategies:**

**Strategy 1: Priority Rules**

```markdown
Define hierarchy:

1. Security Agent > Performance Agent
   → Security concerns override performance

2. Backend Agent > Frontend Agent (for API contracts)
   → Backend defines API, frontend adapts

3. Senior Agent > Junior Agent
   → More experienced takes precedence

Example:
  Security Agent: "Use parameterized queries" (Priority 1)
  Performance Agent: "Use raw SQL" (Priority 2)
  
  Resolution: Use parameterized queries (Security wins)
```

**Strategy 2: Human Tie-Breaking**

```markdown
When agents conflict:

1. Agents produce different solutions
2. System detects conflict
3. Pause execution
4. Present options to human:
   
   "Conflict detected:
   
   Option A (Security Agent):
     Use parameterized queries
     Pros: Secure, best practice
     Cons: Slightly slower setup
   
   Option B (Performance Agent):
     Use raw SQL with validation
     Pros: Faster execution
     Cons: Requires careful validation
   
   Which approach?"

5. Human decides
6. Execution continues
```

**Strategy 3: Validation Agent**

```markdown
Add dedicated conflict resolver:

┌──────────┐   ┌────────────┐
│ Agent A  │   │ Agent B    │
└─────┬────┘   └─────┬──────┘
      │             │
      └────┬──────┘
            ↓
  ┌─────────────────┐
  │ Validation Agent │
  │                 │
  │ - Checks outputs │
  │ - Detects conflicts│
  │ - Proposes synthesis│
  └─────────────────┘

Validation Agent Prompt:
  "Review outputs from Agent A and Agent B.
   If they conflict:
   - Identify the conflict
   - Consider both perspectives
   - Propose a solution that addresses both concerns
   - Explain tradeoffs"
```

**Strategy 4: Synthesis/Compromise**

```markdown
Find middle ground:

Agent A: "Use microservices (scalability)"
Agent B: "Use monolith (simplicity)"

Synthesis Agent:
  "Use modular monolith:
   - Single deployment (like monolith)
   - Clear module boundaries (like microservices)
   - Can split later if needed
   
   Addresses:
   ✓ Agent A's concern: Can scale
   ✓ Agent B's concern: Stays simple initially"
```

**Strategy 5: Voting (Multiple Agents)**

```markdown
When 3+ agents involved:

Question: "What authentication approach?"

Agent A: JWT (stateless)
Agent B: Sessions (server-side)
Agent C: JWT (stateless)
Agent D: JWT (stateless)
Agent E: Sessions (server-side)

Vote Result:
  JWT: 3 votes
  Sessions: 2 votes

Decision: Use JWT (majority)
```

---

**Preventing Conflicts:**

**Prevention 1: Clear Boundaries**

```markdown
Define ownership:

Backend Agent: Owns API contracts
  → Defines endpoints, request/response shapes

Frontend Agent: Consumes API contracts
  → Must adapt to backend's API

→ Frontend can't conflict with backend on API design
```

**Prevention 2: Shared Specification**

```markdown
Before implementation:

1. Architecture Agent: Creates specification
   Output: api_spec.yaml (OpenAPI)

2. Both agents read same spec:
   Backend Agent: Implements spec
   Frontend Agent: Consumes spec

→ Both working from same source of truth
```

**Prevention 3: Communication Protocols**

```markdown
Before Agent B starts:
  → Agent B reads Agent A's output
  → Agent B confirms understanding
  → Agent B asks clarifying questions
  → Then Agent B proceeds

→ Prevents misinterpretation
```

**Prevention 4: Checkpoints**

```markdown
After each agent phase:
  → Human reviews output
  → Confirms correctness
  → Approves next agent to proceed

→ Catches conflicts early
```

---

**Handling Unresolvable Conflicts:**

**Scenario: Genuine tradeoff, no clear winner**

```markdown
Conflict:
  Agent A: "Prioritize speed (cache aggressively)"
  Agent B: "Prioritize accuracy (always fresh data)"

These are fundamentally opposed.

Resolution:
  1. Escalate to human:
     "This is a product decision:
      - Fast but potentially stale data?
      - Slow but always accurate?"
  
  2. Human provides product context:
     "For this use case, accuracy is critical (financial data).
      Use Agent B's approach."
  
  3. Document decision:
     "We chose accuracy over speed because [rationale]."
  
  4. Both agents align to decision
```

---

**Best Practices:**

✅ **Do:**
- Define agent boundaries clearly
- Establish priority rules upfront
- Use shared specifications
- Automate conflict detection
- Document resolution decisions
- Have escalation path to humans

❌ **Don't:**
- Let agents silently overwrite each other
- Assume agents will "figure it out"
- Ignore conflicts (they compound)
- Always favor one agent (breeds bad practices)
- Resolve conflicts randomly

### Orchestration Frameworks

**Building multi-agent systems from scratch is complex.** Frameworks provide structure and tooling.

---

**Why Use a Framework:**

❌ **Without Framework (DIY):**
```python
# You implement:
- Agent communication (files? APIs? queues?)
- Task distribution (who does what?)
- State management (track progress)
- Error handling (what if agent fails?)
- Retry logic
- Logging and observability
- Checkpoints
- Result aggregation

→ 100s of lines of orchestration code
→ Hard to test
→ Easy to introduce bugs
```

✅ **With Framework:**
```python
# Framework provides:
- Communication patterns (built-in)
- Task routing (automatic)
- State persistence (handled)
- Error handling (configurable)
- Retry mechanisms (included)
- Monitoring (integrated)

→ You focus on agent logic, not plumbing
```

---

**Popular Frameworks:**

### **1. LangGraph**

**What it is:** Graph-based agent orchestration from LangChain

**Key Concept:** Agents are nodes, flows are edges

**Example:**
```python
from langgraph.graph import StateGraph

# Define state
class AgentState(TypedDict):
    task: str
    plan: str
    code: str
    tests: str
    status: str

# Create graph
workflow = StateGraph(AgentState)

# Add nodes (agents)
workflow.add_node("planner", planner_agent)
workflow.add_node("coder", coder_agent)
workflow.add_node("tester", tester_agent)

# Define edges (flow)
workflow.add_edge("planner", "coder")
workflow.add_edge("coder", "tester")

# Conditional routing
def should_retry(state):
    return "coder" if state["status"] == "tests_failed" else END

workflow.add_conditional_edges(
    "tester",
    should_retry
)

# Compile
app = workflow.compile()

# Run
result = app.invoke({"task": "Build login feature"})
```

**Strengths:**
- Visual graph structure
- Built-in state management
- Conditional routing
- LangChain ecosystem integration

**Best for:**
- Complex workflows
- Iterative refinement (retry loops)
- Python projects

**Learn more:** [LangGraph Docs](https://python.langchain.com/docs/langgraph)

---

### **2. CrewAI**

**What it is:** Role-based multi-agent framework

**Key Concept:** Agents have roles, tasks are assigned based on expertise

**Example:**
```python
from crewai import Agent, Task, Crew

# Define agents with roles
architect = Agent(
    role="Software Architect",
    goal="Design scalable system architecture",
    backstory="Expert in distributed systems with 15 years experience",
    tools=[research_tool, diagram_tool]
)

developer = Agent(
    role="Senior Developer",
    goal="Implement features following architecture",
    backstory="Full-stack developer specializing in Python and React",
    tools=[code_tool, test_tool]
)

reviewer = Agent(
    role="Code Reviewer",
    goal="Ensure code quality and security",
    backstory="Security-focused engineer",
    tools=[linting_tool, security_scanner]
)

# Define tasks
design_task = Task(
    description="Design auth system architecture",
    agent=architect
)

implement_task = Task(
    description="Implement auth based on design",
    agent=developer,
    context=[design_task]  # Depends on design
)

review_task = Task(
    description="Review auth implementation",
    agent=reviewer,
    context=[implement_task]
)

# Create crew
crew = Crew(
    agents=[architect, developer, reviewer],
    tasks=[design_task, implement_task, review_task],
    process="sequential"  # or "hierarchical"
)

# Execute
result = crew.kickoff()
```

**Strengths:**
- Role-based (intuitive mental model)
- Built-in task dependencies
- Automatic context passing
- Simple API

**Best for:**
- Team-like workflows
- Clear role specialization
- Sequential or hierarchical processes

**Learn more:** [CrewAI Docs](https://docs.crewai.com/)

---

### **3. AutoGen (Microsoft)**

**What it is:** Conversational multi-agent framework

**Key Concept:** Agents converse until task complete

**Example:**
```python
from autogen import AssistantAgent, UserProxyAgent, GroupChat, GroupChatManager

# Define agents
planner = AssistantAgent(
    name="Planner",
    system_message="You create implementation plans"
)

coder = AssistantAgent(
    name="Coder",
    system_message="You write code based on plans"
)

tester = AssistantAgent(
    name="Tester",
    system_message="You write and run tests"
)

user = UserProxyAgent(
    name="User",
    human_input_mode="NEVER",  # or "ALWAYS" for human-in-loop
    code_execution_config={"use_docker": True}
)

# Group chat (agents discuss)
groupchat = GroupChat(
    agents=[user, planner, coder, tester],
    messages=[],
    max_round=10
)

manager = GroupChatManager(groupchat=groupchat)

# Start conversation
user.initiate_chat(
    manager,
    message="Build a REST API for user management"
)

# Agents converse:
# Planner: "I suggest we create 4 endpoints..."
# Coder: "I'll implement the POST /users endpoint first..."
# Tester: "I'll write tests for that endpoint..."
# (continues until complete)
```

**Strengths:**
- Natural conversation flow
- Human-in-the-loop easy
- Code execution built-in
- Flexible agent interactions

**Best for:**
- Dynamic workflows
- Research/exploration tasks
- Human oversight needed

**Learn more:** [AutoGen Docs](https://microsoft.github.io/autogen/)

---

### **4. LangChain Agents (Classic)**

**What it is:** Single-agent with tools (simpler than LangGraph)

**Key Concept:** One agent with multiple tools

**Example:**
```python
from langchain.agents import create_openai_functions_agent, AgentExecutor
from langchain.tools import Tool

# Define tools
def search_code(query: str) -> str:
    # Search codebase
    return f"Found: {query} in src/auth.ts"

def run_tests(file: str) -> str:
    # Run tests
    return f"Tests passed for {file}"

tools = [
    Tool(
        name="SearchCode",
        func=search_code,
        description="Search for code patterns"
    ),
    Tool(
        name="RunTests",
        func=run_tests,
        description="Execute test suite"
    )
]

# Create agent
agent = create_openai_functions_agent(llm, tools, prompt)
executor = AgentExecutor(agent=agent, tools=tools)

# Run
result = executor.invoke({"input": "Find auth code and test it"})

# Agent decides:
# 1. Use SearchCode tool
# 2. Use RunTests tool
# 3. Report results
```

**Strengths:**
- Simple to set up
- Good for single-agent + tools
- Extensive tool ecosystem

**Best for:**
- Simple workflows
- Tool-heavy tasks
- Getting started

**Learn more:** [LangChain Docs](https://python.langchain.com/docs/modules/agents/)

---

### **5. Custom Scripts (Roll Your Own)**

**When frameworks are overkill:**

```python
# Simple sequential workflow
def orchestrate():
    # Phase 1: Planning
    plan = run_agent(
        role="planner",
        task="Design auth system"
    )
    save_artifact("plan.md", plan)
    
    # Phase 2: Implementation
    code = run_agent(
        role="coder",
        task="Implement auth system",
        context=plan
    )
    save_artifact("auth.ts", code)
    
    # Phase 3: Testing
    tests = run_agent(
        role="tester",
        task="Write tests for auth",
        context=code
    )
    save_artifact("auth.test.ts", tests)
    
    return {"plan": plan, "code": code, "tests": tests}

def run_agent(role, task, context=None):
    prompt = f"""
    Role: {role}
    Task: {task}
    {f'Context: {context}' if context else ''}
    """
    
    return llm.invoke(prompt)
```

**Pros:**
- Full control
- No dependencies
- Easy to debug
- Simple to understand

**Cons:**
- More code to write
- Manual error handling
- No built-in features

**Best for:**
- Simple workflows
- Learning/prototyping
- Custom requirements

---

**Framework Comparison:**

| Framework | Complexity | Flexibility | Best For |
|-----------|------------|-------------|----------|
| **LangGraph** | High | Very High | Complex workflows, conditional logic |
| **CrewAI** | Low | Medium | Role-based teams, clear delegation |
| **AutoGen** | Medium | High | Conversational agents, dynamic |
| **LangChain Agents** | Low | Medium | Single agent + tools |
| **Custom** | Medium | Maximum | Full control, simple needs |

---

**Choosing a Framework:**

**Use LangGraph if:**
✅ Complex workflow with loops/conditions
✅ Need state persistence
✅ Checkpoints and retries important
✅ Already using LangChain

**Use CrewAI if:**
✅ Clear role specialization
✅ Sequential or hierarchical tasks
✅ Want simple, intuitive API
✅ Team-like collaboration

**Use AutoGen if:**
✅ Agents should discuss/negotiate
✅ Human-in-the-loop needed
✅ Dynamic, exploratory tasks
✅ Code execution required

**Use LangChain Agents if:**
✅ Single agent sufficient
✅ Tool-focused (not multi-agent)
✅ Simple, straightforward flow

**Use Custom Script if:**
✅ Very simple workflow
✅ Learning/prototyping
✅ Unique requirements
✅ Minimal dependencies preferred

---

**Getting Started:**

**1. Start Simple:**
```python
# Week 1: Single agent, no framework
result = llm.invoke("Write a function...")

# Week 2: Single agent with tools (LangChain)
agent_with_tools = create_agent(tools=[search, test])

# Week 3: Sequential multi-agent (custom)
plan = planner_agent.run()
code = coder_agent.run(plan)

# Week 4: Framework (CrewAI or LangGraph)
crew = Crew(agents=[...], tasks=[...])
```

**2. Learn by Example:**
- Clone framework example repos
- Run tutorials
- Modify for your use case
- Gradually add complexity

**3. Common Patterns:**
- Plan → Implement → Test
- Research → Decide → Execute
- Draft → Review → Revise
- Parallel implementation → Integration

---

**Resources:**

- **LangGraph:** [Tutorials](https://python.langchain.com/docs/langgraph/tutorials), [Examples](https://github.com/langchain-ai/langgraph/tree/main/examples)
- **CrewAI:** [Getting Started](https://docs.crewai.com/), [Examples](https://github.com/joaomdmoura/crewAI-examples)
- **AutoGen:** [Documentation](https://microsoft.github.io/autogen/), [Notebooks](https://github.com/microsoft/autogen/tree/main/notebook)
- **Comparison:** [Multi-Agent Frameworks Comparison](https://blog.langchain.dev/langgraph-multi-agent-workflows/)

## Platform Examples

### GitHub Copilot Workspace

**GitHub Copilot Workspace** brings multi-agent workflows to GitHub's native environment.

**What It Is:**

```
Copilot Workspace = GitHub + Multi-Agent Planning & Execution

Not just code completion → Full task automation
```

---

**How It Works:**

**1. Task Input**

You provide:
- GitHub Issue URL
- Natural language description
- Bug report

**Example:**
```
Input: "Fix bug #234 - users can't reset password"

OR

Input: github.com/org/repo/issues/234
```

---

**2. Planning Phase**

**Agent: Planner**

Automatically:
1. **Analyzes the issue**
   - Reads issue description
   - Reads comments
   - Identifies affected code

2. **Explores codebase**
   - Finds relevant files
   - Understands current implementation
   - Identifies dependencies

3. **Creates plan**
   ```markdown
   ## Plan: Fix Password Reset Bug
   
   ### Analysis
   - Issue: Reset token validation failing
   - Root cause: Token expiry check using wrong timezone
   - Files affected: auth/reset.ts, utils/time.ts
   
   ### Proposed Changes
   1. Fix timezone handling in utils/time.ts
   2. Update token validation in auth/reset.ts
   3. Add test for timezone edge case
   
   ### Testing Strategy
   - Unit test: Token expiry with different timezones
   - Integration test: Full reset flow
   ```

**You review and approve plan** (or request changes)

---

**3. Implementation Phase**

**Agent: Coder**

After you approve plan:

1. **Implements changes**
   - Modifies files per plan
   - Follows project conventions
   - Adds comments

2. **Writes tests**
   - Unit tests for new logic
   - Integration tests for the feature

3. **Shows you the diff**
   ```diff
   // utils/time.ts
   - const now = new Date();
   + const now = new Date().toISOString();
   
   // auth/reset.ts
   - if (token.expiry < now) {
   + if (new Date(token.expiry) < new Date(now)) {
   ```

**You review the implementation**

---

**4. Testing Phase**

**Agent: Tester**

1. **Runs tests automatically**
   ```
   ✓ Token validation with UTC timezone
   ✓ Token validation with PST timezone
   ✓ Full password reset flow
   ✓ Expired token rejection
   ```

2. **Reports results**
   - All tests pass → Ready to commit
   - Tests fail → Agent fixes or asks for guidance

---

**5. PR Creation**

**Agent creates Pull Request:**

```markdown
## Fix password reset timezone bug

Fixes #234

### Changes
- Fixed timezone handling in token expiry check
- Added UTC normalization for consistent comparisons
- Added tests for multiple timezone scenarios

### Testing
- ✓ All existing tests pass
- ✓ New tests verify timezone handling
- ✓ Manual testing completed

### Files Changed
- `auth/reset.ts` - Fixed token validation
- `utils/time.ts` - Added UTC normalization
- `tests/auth.test.ts` - Added timezone tests
```

**You review PR and merge** (or request changes)

---

**Agents Involved:**

```
┌────────────────────┐
│  Analysis Agent   │ → Understands issue & codebase
└──────────┬─────────┘
           ↓
┌──────────┬─────────┐
│ Planning Agent  │ → Creates implementation plan
└──────────┬─────────┘
           ↓
┌──────────┬─────────┐
│ Coding Agent    │ → Implements changes
└──────────┬─────────┘
           ↓
┌──────────┬─────────┐
│ Testing Agent   │ → Writes & runs tests
└──────────┬─────────┘
           ↓
┌──────────┬─────────┐
│ PR Agent        │ → Creates pull request
└────────────────────┘

(You approve at each stage)
```

---

**Workflow Patterns:**

**Pattern 1: Bug Fix**
```
1. Paste GitHub issue
2. Agent analyzes bug
3. Agent proposes fix
4. You approve
5. Agent implements & tests
6. Agent creates PR
7. You merge
```

**Pattern 2: New Feature**
```
1. Describe feature ("Add dark mode")
2. Agent plans implementation
3. You refine plan
4. Agent implements incrementally
5. You review each phase
6. Agent creates PR
```

**Pattern 3: Refactoring**
```
1. "Refactor auth module for testability"
2. Agent analyzes current structure
3. Agent proposes refactor approach
4. You approve strategy
5. Agent refactors (tests still pass)
6. Agent creates PR
```

---

**Integration with GitHub:**

✅ **Direct Issue Integration**
- Paste issue URL → Agent reads automatically
- Comments on issue with plan
- Links PR to issue

✅ **Branch Management**
- Creates feature branch
- Commits incrementally
- Follows branch naming conventions

✅ **PR Automation**
- Auto-generates PR description
- Tags reviewers
- Links related issues
- Adds labels

✅ **CI/CD Integration**
- Waits for CI checks
- Shows test results
- Suggests fixes if tests fail

---

**Strengths:**

✅ Native GitHub integration (seamless)
✅ Multi-agent (specialized for each phase)
✅ Full context (entire repo + issues + PRs)
✅ Iterative (review at each stage)
✅ Production-ready code (follows conventions)

---

**Limitations:**

⚠️ GitHub-only (no GitLab, Bitbucket support)
⚠️ Requires GitHub Copilot subscription
⚠️ Best for GitHub-hosted projects

---

**Best For:**

✅ Teams already using GitHub
✅ Issue-driven development
✅ Want tight GitHub integration
✅ Production codebases

---

**Getting Started:**

1. **Enable Copilot Workspace** (GitHub settings)
2. **Open an issue** in your repo
3. **Click "Open in Workspace"**
4. **Let agent analyze and plan**
5. **Review and approve**
6. **Agent implements**
7. **Review PR and merge**

**Learn More:** [GitHub Copilot Workspace Docs](https://github.com/features/copilot)

### Claude Projects

**Claude Projects** enable persistent, agentic workflows within Claude's interface.

**What It Is:**

```
Claude Project = Shared Context + Persistent Memory + Multi-Turn Workflows

Not a single conversation → An ongoing workspace
```

---

**Key Features:**

**1. Persistent Context**

```markdown
Regular Claude:
  Each conversation starts fresh
  Context lost between sessions
  Must re-explain project every time

Claude Project:
  Context persists across conversations
  Claude "remembers" your project
  Can reference previous work
```

**Example:**
```
Day 1:
You: "I'm building an e-commerce site with Next.js.
      Here's the database schema... [paste]"
Claude: [Helps with implementation]

Day 2 (new conversation):
You: "Add product reviews feature"
Claude: "Based on your e-commerce schema from yesterday,
         I'll add a reviews table linked to products..."
         
→ Claude remembers the context
```

---

**2. Knowledge Base**

**Upload project files:**

```
Project: My E-Commerce App

Knowledge:
- schema.prisma (database schema)
- api-docs.md (API documentation)
- style-guide.md (coding standards)
- architecture.md (system design)
- common-patterns.md (code patterns)
```

**Claude can reference these anytime:**

```
You: "Add a new API endpoint for orders"

Claude: [Reads api-docs.md]
        [Reads schema.prisma]
        [Reads common-patterns.md]
        
        "Following your REST patterns and schema,
         here's the POST /api/orders endpoint..."
```

---

**3. Custom Instructions**

**Set project-level behavior:**

```markdown
Project Instructions:

"You are a senior developer working on an e-commerce platform.

Always:
- Follow our TypeScript strict mode conventions
- Use Prisma for database queries
- Include error handling
- Write JSDoc comments
- Suggest tests for new features

Code Style:
- 2-space indentation
- Descriptive variable names
- Async/await (no .then())
- Zod for validation

Architecture:
- Controllers handle requests
- Services contain business logic
- Repositories handle data access

When unsure:
- Ask clarifying questions
- Reference uploaded documentation
- Explain tradeoffs"
```

**Claude follows these in every conversation within the project.**

---

**Agentic Workflows:**

**Pattern 1: Iterative Development**

```markdown
Conversation 1: Planning
You: "I want to add user reviews"
Claude: [Proposes schema, API design, validation rules]
You: "Good, let's start with the database"

Conversation 2: Database
Claude: [Remembers proposal, creates migration]
You: "Looks good, now the API"

Conversation 3: API Implementation  
Claude: [Remembers schema, creates endpoints]
You: "Add pagination"
Claude: [Updates API with pagination]

Conversation 4: Testing
You: "Write tests for the review API"
Claude: [Remembers implementation, writes tests]

→ Each conversation builds on previous work
```

**Pattern 2: Code Review Agent**

```markdown
Project Setup:
- Upload: coding-standards.md
- Upload: security-checklist.md
- Instructions: "Act as code reviewer"

Usage:
You: "Review this PR..."
     [Paste code]

Claude: [Checks against standards]
        [Checks against security checklist]
        [Provides detailed review]
        
You: "Focus on the auth changes"
Claude: [Deep dive on auth, references security checklist]
```

**Pattern 3: Documentation Maintainer**

```markdown
Project Setup:
- Upload: Current API docs
- Upload: Architecture diagrams
- Instructions: "Keep documentation updated"

Usage:
You: "I just added a new /api/subscriptions endpoint.
      Update the API docs."

Claude: [Reads current docs]
        [Maintains consistent format]
        [Adds subscription endpoint]
        [Updates table of contents]
```

---

**Artifact Persistence:**

```markdown
Claude generates artifacts (code, docs, diagrams)
→ Artifacts persist in project
→ Can reference in later conversations

Example:

Day 1:
Claude generates: database_schema.sql (artifact)

Day 3:
You: "Update the schema to add reviews"
Claude: [Loads database_schema.sql artifact]
        [Modifies it]
        [Saves updated version]
        
→ Continuous refinement
```

---

**Multi-Turn Agent Interactions:**

**Example: Debugging Session**

```markdown
Turn 1:
You: "Users report login failures"
Claude: "I need more information:
         - What error messages do they see?
         - Does it happen for all users or some?
         - Any recent changes to auth code?"

Turn 2:
You: "Error: 'Invalid token'. Happens randomly.
      We updated to jose library v5 last week."
Claude: [Researches jose v5]
        "Likely breaking change in v5. Check token signing algorithm.
         Can you share your JWT config?"

Turn 3:
You: [Pastes config]
Claude: "Found it! v5 requires explicit alg parameter.
         Here's the fix: [code]"

Turn 4:
You: "That fixed it! Add tests so this doesn't happen again."
Claude: [Writes test for JWT signing]
        [Writes test for token validation]
```

→ **Claude acts as persistent debugging partner**

---

**Comparison to Regular Claude:**

| Feature | Regular Claude | Claude Projects |
|---------|---------------|------------------|
| **Context** | Per-conversation | Persistent across conversations |
| **Knowledge** | Must explain each time | Upload once, reference always |
| **Instructions** | Per-prompt | Project-level defaults |
| **Artifacts** | Lost after session | Persist in project |
| **Continuity** | None | Full memory of past work |
| **Use Case** | One-off questions | Ongoing development |

---

**Best For:**

✅ **Long-running projects**
  - E-commerce site (months of development)
  - Internal tool (ongoing maintenance)

✅ **Iterative workflows**
  - Build feature → Test → Refine → Repeat

✅ **Documentation-heavy**
  - Projects with extensive internal docs
  - Need to follow specific patterns

✅ **Team collaboration**
  - Share project with team members
  - Everyone has same context

---

**Limitations:**

⚠️ Claude web interface (not IDE-integrated)
⚠️ Manual copy-paste for code
⚠️ No direct file system access
⚠️ Requires Claude Pro subscription

---

**Tips for Success:**

✅ **Upload comprehensive docs:**
```
- README.md (project overview)
- PATTERNS.md (code conventions)
- DATABASE.md (schema + relationships)
- API.md (endpoint documentation)
- CHANGELOG.md (track what changed)
```

✅ **Set clear instructions:**
```markdown
Instructions:
- Always ask clarifying questions
- Reference uploaded docs
- Explain your reasoning
- Suggest tests
- Warn about breaking changes
```

✅ **Use conversations strategically:**
```
Conv 1: Planning phase
Conv 2: Implementation
Conv 3: Testing
Conv 4: Debugging

→ Logical progression
```

✅ **Update knowledge regularly:**
```
After major changes:
→ Upload updated schema
→ Upload new API docs
→ Keep context fresh
```

---

**Getting Started:**

1. **Create Project** in Claude interface
2. **Upload key documents** (schema, docs, patterns)
3. **Set project instructions** (behavior, style, rules)
4. **Start first conversation** (planning or exploration)
5. **Build iteratively** (each conversation progresses project)

**Learn More:** [Claude Projects Guide](https://www.anthropic.com/claude)

### Cursor Agent Mode

**Cursor Agent Mode** transforms Cursor from an AI code assistant into an autonomous coding agent.

**What It Is:**

```
Cursor Normal Mode:
  You write code, AI suggests completions
  
Cursor Agent Mode:
  AI writes code autonomously, you guide and review
```

---

**How It Works:**

**1. Activate Agent Mode**

```
Cursor IDE:

Cmd/Ctrl + Shift + I → Opens agent panel

OR

Click "Agent" button in sidebar
```

**2. Give Agent a Task**

```
You (in agent panel):
"Implement user authentication with JWT tokens"

Agent:
"I'll implement JWT authentication. Here's my plan:

1. Create auth types (User, Token)
2. Implement token generation function
3. Create login endpoint
4. Add authentication middleware
5. Write tests

Shall I proceed?"
```

**3. Agent Executes Autonomously**

```markdown
Agent's Actions (You watch in real-time):

[Creating src/types/auth.ts]
  ✓ Created type definitions

[Creating src/utils/jwt.ts]
  ✓ Implemented token generation
  ✓ Added verify function

[Creating src/routes/auth.ts]
  ✓ POST /login endpoint
  ✓ Error handling

[Creating src/middleware/auth.ts]
  ✓ Protect route middleware

[Creating tests/auth.test.ts]
  ✓ Login tests
  ✓ Token validation tests
  
[Running tests]
  ✓ All tests pass
  
Agent: "Authentication implemented. Ready for review."
```

---

**Agent Capabilities:**

**1. File Navigation**

```
Agent can:
✅ Read any file in workspace
✅ Search across codebase
✅ Understand file relationships
✅ Find dependencies

Example:
"Add pagination to user list"
→ Agent finds: src/api/users.ts
→ Agent reads current implementation
→ Agent adds pagination
```

**2. Multi-File Editing**

```
Agent can:
✅ Create new files
✅ Modify multiple files simultaneously
✅ Delete files
✅ Rename/move files

Example:
"Refactor auth into separate module"
→ Agent creates src/auth/ directory
→ Agent moves auth code to new files
→ Agent updates imports
→ Agent tests still pass
```

**3. Terminal Commands**

```
Agent can:
✅ Run npm/yarn commands
✅ Execute tests
✅ Run linters
✅ Build project

Example:
Agent: "Need to install jose library"
      [Runs: npm install jose]
      [Installs dependency]
      [Continues implementation]
```

**4. Context Understanding**

```
Agent maintains:
✅ Full project context (all files)
✅ Recent changes
✅ Your coding patterns
✅ Project structure

Agent adapts:
✅ Follows your code style
✅ Uses your preferred libraries
✅ Matches existing patterns
```

---

**Autonomous Workflows:**

**Workflow 1: Feature Implementation**

```markdown
You: "Add product search with filters"

Agent Plan:
1. Analyze current product model
2. Add search endpoint to API
3. Implement query logic (filters, sorting)
4. Add frontend search component
5. Connect frontend to API
6. Write tests
7. Update documentation

Agent executes all steps autonomously

You: [Review final diff]
```

**Workflow 2: Bug Fix**

```markdown
You: "Fix the memory leak in the websocket handler"

Agent:
1. Reads websocket handler code
2. Identifies issue (listeners not cleaned up)
3. Adds cleanup logic
4. Tests fix
5. Verifies memory usage

Agent: "Fixed: Added listener cleanup in disconnect handler.
        Tested with 1000 connections - no leak."
```

**Workflow 3: Refactoring**

```markdown
You: "Split the monolithic user controller
      into separate controllers per concern"

Agent:
1. Analyzes user controller (500 lines)
2. Identifies concerns:
   - Auth (login, register)
   - Profile (get, update)
   - Preferences (get, update)
3. Creates separate files
4. Moves code to appropriate files
5. Updates routes
6. Runs tests  ✓

Agent: "Refactored into 3 controllers.
        All tests pass. Code coverage maintained."
```

---

**How Agent Maintains Project Context:**

**1. Workspace Understanding**
```
On startup, Agent indexes:
- File structure
- Import relationships
- Code patterns
- Configuration files
- Test structure

→ Agent knows your project layout
```

**2. Pattern Recognition**
```
Agent learns:
- How you structure components
- Your error handling patterns
- Test organization
- Naming conventions

→ Agent generates consistent code
```

**3. Incremental Context**
```
As you work:
- Agent sees your edits
- Agent learns from your corrections
- Agent improves suggestions

→ Agent adapts to your style
```

---

**Checkpoints and Review:**

**Cursor shows diffs in real-time:**

```diff
// src/auth.ts
+ export function generateToken(userId: string): string {
+   return jwt.sign({ id: userId }, SECRET, { expiresIn: '1h' });
+ }
```

**You can:**
✅ **Accept** → Agent continues
✅ **Reject** → Agent reverts, tries different approach
✅ **Modify** → Edit agent's code, agent learns
✅ **Pause** → Stop and give new instructions

---

**Agent Mode Best Practices:**

**1. Clear Task Descriptions**

```
❌ Vague:
"Fix the bug"

✅ Specific:
"Fix the authentication bug where tokens expire
too quickly. Should be 1 hour, currently 1 minute.
Issue is in src/auth/jwt.ts"
```

**2. Set Boundaries**

```
"Implement product reviews.

Constraints:
- Don't modify existing user table
- Use Prisma for database
- Follow patterns in src/features/comments
- Add tests

Don't:
- Install new dependencies without asking
- Modify auth system"
```

**3. Incremental Complexity**

```
Start simple:
  "Create basic login form"
  → Agent builds form
  → You review

Then expand:
  "Add validation to login form"
  → Agent adds validation
  → You review

Then integrate:
  "Connect login form to API"
  → Agent connects
  → You test
```

**4. Review at Milestones**

```
For large tasks:
  "Implement checkout flow (5 steps)"
  
Agent: "I'll implement step 1 (cart summary) first.
        Please review before I proceed to step 2."
        
→ Prevents wrong direction compounding
```

---

**Strengths:**

✅ **IDE-integrated** (no copy-paste)
✅ **Autonomous** (minimal interaction needed)
✅ **Full file access** (can modify any file)
✅ **Real-time updates** (watch agent work)
✅ **Context-aware** (understands your project)

---

**Limitations:**

⚠️ Requires Cursor IDE (VS Code fork)
⚠️ Subscription required for agent mode
⚠️ Can make mistakes (review carefully)

---

**When to Use Agent Mode:**

✅ **Implementing boilerplate**
```
"Create CRUD endpoints for products"
→ Agent generates standard code quickly
```

✅ **Refactoring**
```
"Split monolith into modules"
→ Agent handles tedious reorganization
```

✅ **Test generation**
```
"Write tests for all API endpoints"
→ Agent generates comprehensive test suite
```

✅ **Debugging**
```
"Find and fix the race condition"
→ Agent analyzes code, proposes fix
```

---

**When NOT to Use:**

❌ **Exploratory coding** (you're figuring it out)
❌ **Learning** (you want to understand deeply)
❌ **Critical security code** (needs human expertise)
❌ **Novel algorithms** (agent might not get it right)

---

**Getting Started:**

1. **Install Cursor** (cursor.sh)
2. **Open your project**
3. **Press Cmd+Shift+I** (agent mode)
4. **Start with simple task**: "Add a hello world endpoint"
5. **Review agent's work**
6. **Gradually increase complexity**

**Learn More:** [Cursor Documentation](https://cursor.sh/docs)

### Replit Agent

**Replit Agent** enables end-to-end app development from natural language prompts.

**What It Is:**

```
Replit Agent = Prompt → Deployed App

Not just code generation → Complete application delivery
```

**Unique Value:** From idea to live URL in minutes, no local setup.

---

**How It Works:**

**1. Describe Your App**

```
You (in Replit):
"Build a todo list app with:
- User authentication
- Create, read, update, delete todos
- Mark as complete
- Filter by status
- Dark mode"
```

**2. Agent Plans**

```markdown
Replit Agent:

"I'll build a full-stack todo app with:

Frontend:
- React 18 + TypeScript
- Tailwind CSS for styling
- Dark mode toggle

Backend:
- Node.js + Express
- SQLite database
- JWT authentication

Features:
1. Registration and login
2. Todo CRUD operations
3. Status filtering
4. Responsive design

I'll set up the project structure, implement features,
and deploy to Replit hosting.

Ready to begin?"
```

**3. Agent Builds Everything**

```markdown
[Agent working...]

✓ Created project structure
✓ Set up React + Vite
✓ Configured Tailwind
✓ Created database schema
✓ Implemented auth endpoints
✓ Built todo API
✓ Created frontend components:
  - LoginForm
  - RegisterForm  
  - TodoList
  - TodoItem
  - FilterBar
  - ThemeToggle
✓ Integrated frontend with API
✓ Added error handling
✓ Tested app functionality
✓ Deployed to Replit

Agent: "Your app is live at:
        https://todo-app-username.replit.app
        
        Login with demo account:
        Email: demo@example.com
        Password: demo123"
```

**Time: ~5 minutes** for functional app

---

**Agent Handles Complete Stack:**

**1. Environment Setup**
```
Agent automatically:
✅ Chooses appropriate tech stack
✅ Installs dependencies
✅ Configures build tools
✅ Sets up dev server
✅ Configures environment variables
```

**2. Backend Implementation**
```
Agent creates:
✅ Database schema
✅ API endpoints
✅ Authentication system
✅ Data validation
✅ Error handling
✅ Middleware
```

**3. Frontend Implementation**
```
Agent builds:
✅ Component structure
✅ State management
✅ API integration
✅ Forms with validation
✅ Styling (Tailwind, CSS Modules, etc.)
✅ Responsive design
```

**4. Deployment**
```
Agent handles:
✅ Build configuration
✅ Production optimization
✅ Hosting setup
✅ Live URL generation
✅ Auto-reload on changes
```

---

**Development Stages:**

**Stage 1: Scaffolding**
```
Agent creates basic structure:

src/
  components/
  api/
  utils/
  db/
package.json
vite.config.ts
tailwind.config.js

→ Full project setup in seconds
```

**Stage 2: Core Features**
```
Agent implements main functionality:

- User registration
- Login/logout
- Todo CRUD
- Basic UI

→ Functional MVP
```

**Stage 3: Enhancements**
```
Agent adds polish:

- Filtering
- Sorting
- Dark mode
- Loading states
- Error messages

→ Production-ready features
```

**Stage 4: Testing & Deployment**
```
Agent:

- Tests all endpoints
- Verifies UI flows
- Builds for production
- Deploys to Replit hosting

→ Live application
```

---

**Iterative Development:**

**After Initial Build:**

```markdown
You: "Add ability to set due dates on todos"

Agent:
1. Updates database schema (add due_date column)
2. Updates API (include due_date in responses)
3. Updates TodoForm (add date picker)
4. Updates TodoItem (display due date)
5. Tests new functionality
6. Redeploys

Agent: "Due dates added. Try creating a todo with a deadline."
```

**You can keep iterating:**

```
"Add email reminders for overdue todos"
"Sort by due date"
"Add categories/tags"
"Export todos to CSV"

→ Agent implements each request
→ App evolves continuously
```

---

**Strengths:**

✅ **Zero setup**
```
No need for:
- Local development environment
- npm install
- Database setup
- Hosting configuration

→ Everything in browser
```

✅ **Full-stack automation**
```
Agent handles:
- Frontend + Backend + Database
- Deployment + Hosting
- SSL certificates

→ Complete solution
```

✅ **Instant iteration**
```
Changes → Deployed immediately
No build/deploy wait

→ Fast feedback loop
```

✅ **Shareable instantly**
```
Get live URL immediately
Share with team/users
No deployment hassle
```

---

**Limitations:**

⚠️ **Replit platform lock-in**
```
Code runs on Replit
Migrating to AWS/Vercel requires work
```

⚠️ **Resource constraints**
```
Free tier: Limited CPU/memory
Not for production-scale apps
```

⚠️ **Tech stack decisions**
```
Agent chooses stack
May not match your preferences
```

⚠️ **Code quality variability**
```
Agent-generated code
May need refactoring
Test coverage varies
```

---

**Best Use Cases:**

**1. Rapid Prototyping**
```
"I need a demo for Friday's meeting"

→ Replit Agent: MVP in 10 minutes
→ Share live URL with stakeholders
→ Iterate based on feedback
```

**2. Learning Projects**
```
"I want to learn how authentication works"

→ Agent builds auth system
→ You study the code
→ Modify and experiment
```

**3. Internal Tools**
```
"Build a tool to convert CSV to JSON"

→ Agent creates web interface
→ Team uses immediately
→ No IT approval needed
```

**4. Hackathons**
```
24-hour hackathon

→ Agent handles boilerplate
→ You focus on unique features
→ Deploy and demo faster
```

---

**Not Ideal For:**

❌ **Production apps** (scalability limits)
❌ **Enterprise software** (complex requirements)
❌ **Highly custom** (agent uses standard patterns)
❌ **Offline apps** (cloud-based only)

---

**Example: Building a URL Shortener**

```markdown
Prompt:
"Create a URL shortener like bit.ly with:
- Paste long URL, get short URL
- Track click counts
- Custom short codes (optional)
- QR code generation
- Analytics dashboard"

Agent builds:

1. Backend (Node + Express):
   - POST /shorten (create short URL)
   - GET /:code (redirect to long URL + track)
   - GET /stats/:code (analytics)
   - Database: SQLite

2. Frontend (React):
   - URL input form
   - Short URL display with copy button
   - QR code generation (react-qr-code)
   - Analytics page (charts with recharts)

3. Features:
   - Custom codes support
   - Click tracking
   - Recent links list
   - Shareable analytics

Time: 8 minutes
Result: https://url-shortener-you.replit.app

→ Functional URL shortener, ready to use
```

---

**Comparison to Other Platforms:**

| Feature | Replit Agent | Copilot Workspace | Cursor Agent |
|---------|--------------|------------------|---------------|
| **Setup** | None (cloud) | GitHub integration | Local IDE |
| **Scope** | Full app | Code changes | Code editing |
| **Deployment** | Automatic | Manual (GH Actions) | Manual |
| **Stack** | Agent chooses | Your existing | Your existing |
| **Best For** | Prototypes | GitHub projects | Existing codebases |

---

**Getting Started:**

1. **Go to Replit.com**
2. **Click "Create Repl"**
3. **Select "Agent mode"**
4. **Describe your app**:
   ```
   "Build a recipe sharing app where users can:
   - Post recipes with ingredients and steps
   - Search and filter recipes
   - Rate and comment
   - Save favorites"
   ```
5. **Watch agent build**
6. **Get live URL**
7. **Iterate as needed**

**Learn More:** [Replit Agent Documentation](https://replit.com/agent)

### Emerging Platforms

**The agentic AI landscape is rapidly evolving.** Here's what's emerging beyond the established players.

---

### **Devin (Cognition AI)**

**What It Is:** "AI software engineer" - fully autonomous agent

**Key Features:**
```
✅ Complete autonomy (can work for hours unsupervised)
✅ Plans entire projects
✅ Writes code across multiple files
✅ Debugs failures independently
✅ Uses terminal, browser, code editor
✅ Learns from documentation
```

**Example Workflow:**
```markdown
You: "Build a Slack bot that summarizes GitHub PRs"

Devin:
1. Researches Slack API docs
2. Researches GitHub API docs
3. Plans architecture
4. Sets up Node.js project
5. Implements Slack integration
6. Implements GitHub integration
7. Adds summarization logic
8. Tests bot
9. Debugs issues
10. Deploys to hosting
11. Provides documentation

Time: 3-4 hours (mostly autonomous)
```

**Unique Aspects:**
- **Runs in sandbox** (own terminal, browser, editor)
- **Self-debugging** (fixes own errors)
- **Long-running** (can work overnight)

**Status:** Early access, waitlist

**Learn More:** [devin.ai](https://devin.ai)

---

### **AutoGPT**

**What It Is:** Open-source autonomous agent framework

**Key Features:**
```
✅ Goal-oriented (you set goal, it figures out steps)
✅ Memory persistence (remembers context)
✅ Internet access (searches, reads docs)
✅ File operations (reads/writes files)
✅ Self-reflection (critiques own work)
```

**Example:**
```python
# Set goal
autogpt.run(goal="Research competitors and create comparison table")

# AutoGPT:
1. Searches for competitor websites
2. Visits and scrapes data
3. Analyzes features
4. Creates comparison spreadsheet
5. Writes summary report

→ Autonomous research agent
```

**Unique Aspects:**
- **Open source** (self-hostable)
- **Plugin system** (extensible)
- **Self-prompting** (generates own prompts)

**Status:** Active development, free to use

**Learn More:** [github.com/Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT)

---

### **GPT Engineer**

**What It Is:** Generate entire codebases from prompts

**Key Features:**
```
✅ Clarification phase (asks questions before building)
✅ Full project scaffolding
✅ Database schema generation
✅ API implementation
✅ Frontend generation
```

**Example:**
```bash
$ gpt-engineer my-app

Prompt: "Build a blog with authentication"

GPT Engineer:
Q: "What database? (PostgreSQL, MySQL, SQLite)"
You: "PostgreSQL"

Q: "What auth? (JWT, Sessions, OAuth)"
You: "JWT"

Q: "Frontend framework? (React, Vue, Svelte)"
You: "React"

[Generates]:
my-app/
  backend/
    auth/
    api/
    db/
  frontend/
    components/
    pages/
  tests/
  README.md
  
→ Complete project structure
```

**Unique Aspects:**
- **Interactive** (clarifies requirements)
- **Opinionated** (best practices built-in)
- **Iterative improvement** (refines based on feedback)

**Status:** Open source, active

**Learn More:** [github.com/AntonOsika/gpt-engineer](https://github.com/AntonOsika/gpt-engineer)

---

### **Sweep (Sweep AI)**

**What It Is:** AI that handles GitHub issues autonomously

**Key Features:**
```
✅ GitHub integration (monitors issues)
✅ Automatic PR creation
✅ Code search (finds relevant files)
✅ Test generation
✅ Responds to review comments
```

**Workflow:**
```markdown
1. Label issue with "sweep"
   GitHub Issue #123: "Add dark mode"
   
2. Sweep agent:
   - Reads issue
   - Searches codebase for theme code
   - Plans implementation
   - Creates branch
   - Implements dark mode
   - Writes tests
   - Creates PR
   
3. You review PR

4. If you comment: "Add toggle to navbar"
   → Sweep updates PR automatically
```

**Unique Aspects:**
- **GitHub-native** (lives in your repo)
- **Automatic** (watches for labeled issues)
- **Conversational PR updates** (responds to review feedback)

**Status:** Available (free tier + paid)

**Learn More:** [sweep.dev](https://sweep.dev)

---

### **Smol Developer**

**What It Is:** Minimalist AI developer in Python

**Key Features:**
```
✅ Extremely simple (~200 lines)
✅ Educational (learn how agents work)
✅ Hackable (easy to modify)
✅ Generates scaffolds
```

**Example:**
```python
import smol_dev

smol_dev.develop(
    prompt="Build a CLI tool to convert markdown to PDF",
    framework="Python + Click"
)

# Generates:
# - Project structure
# - CLI boilerplate
# - Conversion logic
# - README
```

**Unique Aspects:**
- **Tiny** (understand entire codebase)
- **Learning-focused** (see how it works)
- **Fork-friendly** (customize easily)

**Status:** Open source, stable

**Learn More:** [github.com/smol-ai/developer](https://github.com/smol-ai/developer)

---

### **Aider**

**What It Is:** AI pair programming in terminal

**Key Features:**
```
✅ Works with git
✅ Multi-file editing
✅ Commits automatically
✅ Uses diff for efficiency
✅ Works with any editor
```

**Example:**
```bash
$ aider

Aider: What do you want to work on?
You: Add logging to all API endpoints

Aider: I'll add logging. [Shows diff]

  api/users.ts:
  + logger.info('GET /users called')
  
  api/products.ts:
  + logger.info('GET /products called')
  
Apply changes? (y/n): y

Aider: [Commits: "Add logging to API endpoints"]
```

**Unique Aspects:**
- **Git-integrated** (automatic commits)
- **Terminal-based** (works with any editor)
- **Efficient** (sends diffs, not full files)

**Status:** Open source, active development

**Learn More:** [aider.chat](https://aider.chat)

---

## **Common Patterns Across Platforms:**

**1. Autonomy Spectrum**
```
Low ←─────────────────────────→ High

Copilot   Cursor   Replit   Devin
   |         |        |       |
Suggest  Execute  Build  Autonomous
          w/review  MVP    for hours
```

**2. Integration Approach**
```
IDE-Native:  Cursor, Copilot
Web-Based:   Replit, Devin
GitHub:      Copilot Workspace, Sweep
Terminal:    Aider, AutoGPT
```

**3. Workflow Focus**
```
Code completion:    Copilot, Codeium
File editing:       Cursor, Copilot Chat
Full features:      Replit, GPT Engineer
Full projects:      Devin, AutoGPT
GitHub issues:      Sweep
Pair programming:   Aider
```

---

## **Evaluating New Platforms:**

**Ask These Questions:**

❓ **Autonomy Level**
```
- How much can it do without supervision?
- Does it ask for approval?
- Can it self-correct errors?
```

❓ **Integration**
```
- Works with my editor?
- Integrates with my workflow?
- Requires context switching?
```

❓ **Context Understanding**
```
- Can it see my entire codebase?
- Does it remember past interactions?
- Can it search docs/web?
```

❓ **Trust & Safety**
```
- What can it access?
- Can it make irreversible changes?
- How do I review its work?
```

❓ **Maturity**
```
- Production-ready or experimental?
- Active development?
- Community support?
```

---

## **The Future (2024-2026):**

**Predictions:**

**1. Increased Autonomy**
```
Current: Agents work for minutes
Future:  Agents work for days

"Build and maintain this service" → Agent handles ongoing work
```

**2. Multi-Agent Standard**
```
Current: Single agent per task
Future:  Agent teams (planner, coder, tester, deployer)

→ Specialized agents collaborating
```

**3. Platform Consolidation**
```
Many platforms today
→ Some will merge
→ Standards will emerge
→ Interoperability improves
```

**4. Enterprise Adoption**
```
Current: Mostly individual developers
Future:  Corporate IT departments, standardized agents

→ "Agent engineer" becomes a job title
```

---

## **Staying Current:**

✅ **Follow These:**
- [r/AutonomousAgents](https://reddit.com/r/AutonomousAgents)
- [AI Agent Builders](https://twitter.com/i/lists/1679935305394982912)
- [LangChain Blog](https://blog.langchain.dev)
- [Anthropic Research](https://www.anthropic.com/research)

✅ **Try New Platforms:**
- Start with free tiers
- Build same project on different platforms
- Compare results

✅ **Experiment:**
- Most platforms have demos
- Low cost to trial
- Learn what works for you

---

**Bottom Line:**

The agent platform landscape is **rapidly evolving**. What's cutting-edge today may be standard tomorrow. 

**Strategy:**
1. Master fundamentals (this learning pathway)
2. Try multiple platforms
3. Find what fits your workflow
4. Stay flexible as tools evolve

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
