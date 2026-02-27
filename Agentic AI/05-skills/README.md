> [!NOTE]
> **📍 Current Location:** [Pathway Home](../README.md) → 5. Skills  
> **📊 Progress:** Section 5 of 6 | ⏱️ Estimated time: 25 minutes  
> **Prerequisites:** [1. Ecosystem](../01-ecosystem/README.md), [4. Agents](../04-agents/README.md) — Understanding AI tools and agent patterns

---

# 5. AI Skills & Capabilities

## Table of Contents

- [Overview](#overview)
- [Understanding AI Skills](#understanding-ai-skills--beginner)
  - [Definition](#definition)
  - [Anatomy of a Skill](#anatomy-of-a-skill)
  - [Concrete Skill Examples](#concrete-skill-examples)
  - [Skill Categories](#skill-categories)
- [Skill Packaging & Integration](#skill-packaging--integration)
  - [Standard Skill Format](#standard-skill-format)
  - [Integration Patterns](#integration-patterns)
  - [Code Examples for Skill Loading](#code-examples-for-skill-loading)
- [Platform Skill Formats](#platform-skill-formats)
  - [Platform Comparison Table](#platform-comparison-table)
  - [Format Deep Dive](#format-deep-dive)
- [Skill Repositories & Discovery](#skill-repositories--discovery)
  - [Claude Skills Repository](#claude-skills-repository)
  - [Awesome AI Skills Repository](#awesome-ai-skills-repository)
  - [This Repository's Skills](#this-repositorys-skills)
- [Creating Your Own Skills](#creating-your-own-skills--advanced)
  - [Skill Design Workflow](#skill-design-workflow)
  - [Testing and Iteration](#testing-and-iteration)
- [Best Practices](#best-practices)
- [Common Pitfalls](#common-pitfalls)
- [Hands-On Exercises](#hands-on-exercises)
- [Resources](#resources)
- [Navigation](#navigation)

---

## Overview

### What Are AI Skills?

Think of AI skills as **reusable capability packages**—pre-written instructions that teach an AI assistant or agent how to perform a specific task consistently and effectively.

Just as software developers rely on libraries instead of writing every function from scratch, people working with AI can leverage **skills** to standardize how their AI assistant handles recurring tasks like code reviews, data analysis, or documentation generation.

**The Library Analogy:**

```
Traditional Software          AI Workflow
─────────────────────        ─────────────────────

📦 Libraries (reusable)   →   📄 Skills (reusable)
├─ axios (HTTP calls)         ├─ Code Review Skill
├─ lodash (utilities)         ├─ Task Decomposition Skill  
└─ moment (dates)             └─ Documentation Gen Skill

import { axios }          →   Load skill into AI context
axios.get('api')          →   AI applies skill to input
```

### Why Skills Matter

**Without Skills (Ad-hoc Prompting):**
```
You: "Review this code"
AI: *Generic surface-level feedback*
You: "Check for security issues too"
AI: *Improved but inconsistent*
You: "What about error handling?"
AI: *Keeps adapting but no pattern*
```

Every code review requires the same tedious back-and-forth. Quality depends on how thoroughly you prompt each time.

**With Skills (Packaged Capability):**
```
You: "Review this code using Code Review Skill"
AI: *Applies comprehensive checklist:*
    ✅ Security vulnerabilities (OWASP Top 10)
    ✅ Error handling patterns
    ✅ Maintainability metrics
    ✅ Test coverage gaps
    ✅ Performance concerns
```

The skill encodes **institutional knowledge**—consistent, repeatable, improvable.

### Skill vs Prompt

| Aspect | One-off Prompt | AI Skill |
|--------|----------------|----------|
| **Reusability** | Write each time | Write once, use forever |
| **Consistency** | Varies per person | Standardized execution |
| **Maintenance** | N/A (lost after use) | Version controlled |
| **Shareability** | Copy-paste text | Packaged file |
| **Composability** | Hard to combine | Can chain skills |
| **Evolution** | Reinvent patterns | Iteratively improve |

**Example Evolution:**
```
1. Raw Prompt (ephemeral):
   "Can you review my Python code?"

2. Template (copy-paste):
   "Review code for: security, errors, readability"

3. Skill (reusable markdown):
   # Code Review Skill
   - OWASP security checks
   - Error handling patterns
   - Cyclomatic complexity < 15
   - Test coverage > 80%
   [Detailed instructions...]

4. Skill Library (organizational asset):
   .github/skills/code-review/SKILL.md
   Used by: 50 developers, 200 PRs/month
```

### The Evolution Pathway

```
┌────────────────┐
│  Raw Prompts   │  "Fix this bug"
│   (Day 1)      │   Every time is different
└────────┬───────┘
         │
         ▼
┌────────────────┐
│ Prompt Library │  "Fix bug using template #7"
│  (Week 1-2)    │   Copy-paste common prompts
└────────┬───────┘
         │
         ▼
┌────────────────┐
│  AI Skills     │  Load "Debug Skill" into AI
│  (Month 1-3)   │   Packaged, versioned, shareable
└────────┬───────┘
         │
         ▼
┌────────────────┐
│ Skill Ecosystem│  Organization-wide skill library
│  (Ongoing)     │   Curated, maintained, governed
└────────────────┘
```

**Key Insight:** Skills transform AI from "helpful assistant you instruct" to "specialized colleague with expertise."

---

## Understanding AI Skills 🟢 Beginner

### Definition

**AI Skill:** A structured document (typically Markdown or plain text) containing detailed instructions that enable an AI assistant or agent to perform a specific capability reliably.

Skills are human-readable but AI-optimized—written in natural language but structured for consistent interpretation by language models.

### Anatomy of a Skill

A well-designed skill contains five essential components:

```markdown
# 1. Metadata
name: skill-identifier
version: 1.2.0
author: creator-name
tags: [category, domain, use-case]

# 2. Objective
What capability does this skill provide?
What problem does it solve?

# 3. Instructions
Step-by-step execution logic
Decision trees for edge cases
Output format specifications

# 4. Examples
2-3 demonstration cases showing:
- Input format
- Execution trace
- Expected output

# 5. Constraints
What NOT to do
Boundary conditions
Error handling
```

### Concrete Skill Examples

#### Example 1: Code Review Skill

```markdown
---
name: code-review
version: 2.1.0
tags: [coding, quality, security]
---

# Code Review Skill

## Objective
Systematically review code for security vulnerabilities, quality issues, 
maintainability concerns, and test coverage gaps. Produce actionable feedback 
with severity ratings.

## Instructions

Execute review in this order:

**1. Security Analysis**
- Check OWASP Top 10 vulnerabilities:
  - SQL Injection (parameterized queries?)
  - XSS (input sanitization?)
  - Authentication issues (secure session management?)
  - Sensitive data exposure (encryption at rest/transit?)
- Flag: ❌ Critical, ⚠️  High, 💡 Moderate

**2. Error Handling**
- Validate input at boundaries
- Proper try-catch usage (specific exceptions)
- Graceful degradation (fallback strategies)
- Logging for debugging (no sensitive data in logs)

**3. Maintainability**
- Function length < 50 lines (exception: <100 if inherently complex)
- Cyclomatic complexity < 15
- Meaningful variable names (no \x\, \	mp\, \data2\)
- Comments for "why", not "what"

**4. Test Coverage**
- Unit tests for business logic
- Edge case coverage (null, empty, boundary values)
- Integration tests for external dependencies
- Fail test to verify it catches issues

**5. Code Smells**
- Duplicated logic (DRY violations)
- God classes/functions (SRP violations)
- Tight coupling (dependency injection opportunities)

## Output Format

\\\
Code Review Summary
===================

✅ **Security**: [Summary of findings or "No issues"]  
⚠️  **Error Handling**: [Issues found]  
💡 **Maintainability**: [Suggestions]  
📊 **Test Coverage**: [Assessment]  

Priority Fixes:
1. [Critical issue]
2. [High priority issue]

Recommendations:
- [Improvement 1]
- [Improvement 2]
\\\

## Example Execution

**Input:**
\\\python
def login(username, password):
    result = db.execute(f"SELECT * FROM users WHERE name='{username}'")
    if result[0]['password'] == password:
        return True
    return False
\\\

**Output:**
\\\
Code Review Summary
===================

❌ **Security**: CRITICAL - SQL Injection vulnerability
   - Line 2: Unparameterized query allows SQL injection
   - Line 3: Plain text password comparison (no hashing)

⚠️  **Error Handling**: No error handling
   - No validation for null/empty inputs
   - No try-catch for database errors
   - Assumes result[0] exists (IndexError risk)

💡 **Maintainability**: Acceptable structure but missing types
   - Consider type hints: \def login(username: str, password: str) -> bool\

📊 **Test Coverage**: No tests found
   - Add test for SQL injection attempt
   - Add test for wrong password
   - Add test for non-existent user

Priority Fixes:
1. CRITICAL: Use parameterized queries
2. CRITICAL: Hash passwords (use bcrypt/argon2)
3. HIGH: Add input validation
4. MEDIUM: Implement error handling

Recommendation:
\\\python
def login(username: str, password: str) -> bool:
    if not username or not password:
        raise ValueError("Username and password required")
    
    try:
        result = db.execute(
            "SELECT * FROM users WHERE name = ?", 
            (username,)
        )
        if result and bcrypt.checkpw(password, result[0]['password_hash']):
            return True
    except DatabaseError as e:
        logger.error(f"Login failed: {e}")
        raise
    
    return False
\\\
\\\
```

## Anti-Patterns
- ❌ Generic feedback: "Code looks good" (not actionable)
- ❌ Overwhelming detail: Don't list 50 minor style issues
- ❌ False positives: Flagging intentional design choices
- ❌ Missing context: Ignoring project-specific patterns

## Success Criteria
- All 5 review categories addressed
- Clear severity ratings (Critical/High/Medium/Low)
- Concrete code examples for fixes
- Execution time < 2 minutes for 100-line function
```

---

#### Example 2: Task Decomposition Skill

This is one of the core skills used by the GSD framework in this repository.

**What:** Break complex project goals into executable, dependency-ordered tasks

**How:** Analyze requirements, identify dependencies, assign wave numbers for parallelization

**Used By:** GSD planner agent when creating PLAN.md files

**Reference in This Repo:** [.github/skills/plan-phase/SKILL.md](../../.github/skills/plan-phase/SKILL.md)

**Key Patterns:**
```markdown
## Task Decomposition Process

1. **Goal Analysis**
   - What is the end state?
   - What artifacts must exist?
   - What behavior must work?

2. **Dependency Mapping**
   - Task A requires Task B → B before A
   - Tasks C, D, E independent → Same wave

3. **Wave Assignment**
   Wave 1: Foundation tasks (no dependencies)
   Wave 2: Tasks depending on Wave 1
   Wave 3: Integration tasks
   
4. **Task Granularity**
   - Each task: 15-45 minutes
   - If > 45 min → decompose further
   - If < 15 min → combine related tasks

5. **Output Format**
   XML structure with wave numbers:
   <task wave="1">Create database schema</task>
   <task wave="2" depends="schema">Seed test data</task>
```

**Example Usage:**
```
Input: "Build user authentication system"

Output Tasks:
Wave 1:
- Create User model (database schema)
- Set up JWT library dependencies

Wave 2:
- Implement registration endpoint (POST /auth/register)
- Implement login endpoint (POST /auth/login)
- Create password hashing utility

Wave 3:
- Add authentication middleware
- Protect routes requiring auth
- Add refresh token rotation

Wave 4:
- Write integration tests
- Document API endpoints
```

---

#### Example 3: Verification Skill (Goal-Backward Analysis)

**What:** Verify that implementation actually achieves stated goals (not just that tasks were completed)

**How:** Three-level artifact check—Existence → Substantive → Wired

**Used By:** GSD verifier agent after phase completion

**Reference in This Repo:** [.github/skills/verify-phase/SKILL.md](../../.github/skills/verify-phase/SKILL.md)

**Three-Level Verification:**

```markdown
Level 1: Existence Check
- Does the artifact exist on disk?
- Is it committed to version control?

Level 2: Substantive Check  
- Is it a real implementation or just a stub?
- Does it contain actual logic/content?
- Does it meet minimum quality bar?

Level 3: Wired Check
- Is the artifact integrated into the system?
- Does it execute/run/render as expected?
- Can end user access the functionality?
```

**Example Application:**

```
Goal: "User can register and log in"

Verification:

✅ Level 1: Existence
- ✅ File: src/auth/register.ts exists (347 lines)
- ✅ File: src/auth/login.ts exists (289 lines)
- ✅ Route: POST /auth/register registered
- ✅ Route: POST /auth/login registered

✅ Level 2: Substantive
- ✅ Password hashing: bcrypt with salt rounds = 10
- ✅ Validation: Email format + password strength
- ✅ Database: User table schema includes required fields
- ✅ JWT: Tokens contain user ID + 1hr expiry

⚠️  Level 3: Wired (Issue Found)
- ✅ Routes respond to HTTP requests
- ✅ Database writes persist
- ❌ CORS not configured: Frontend can't call API
- ❌ Rate limiting missing: Brute force vulnerability

Gap: Routes exist but CORS prevents browser access.
Fix Required: Add CORS middleware for frontend origin.
```

**Truth Verification Principle:**

Don't just check that code exists—verify that **learner/user can achieve stated outcome**.

---

### Skill Categories

Skills can be grouped by function:

| Category | Purpose | Examples |
|----------|---------|----------|
| **Planning** | Break down complex work | Task decomposition, Roadmap generation |
| **Execution** | Perform development tasks | Code generation, API client creation |
| **Verification** | Validate quality/correctness | Code review, UAT testing, Goal-backward analysis |
| **Analysis** | Extract insights from data | Log analysis, Performance profiling |
| **Generation** | Create artifacts | Documentation, README, API specs |
| **Transformation** | Convert formats | Markdown to HTML, JSON to CSV |
| **Orchestration** | Coordinate multi-step workflows | CI/CD pipeline, Multi-agent coordination |

---
 Awesome AI Skills Repository

**Community Collection:** Search GitHub for "awesome-ai-skills", "prompt-engineering", or browse curated skill lists

**Structure of Awesome Lists:**

```markdown
# Awesome AI Skills

A curated list of high-quality AI skills/prompts organized by category.

## Planning & Strategy
- [Task Decomposition](skills/task-decomposition.md) - Break goals into executable tasks ⭐ 1.2k
- [Roadmap Generation](skills/roadmap-gen.md) - Create project roadmaps ⭐ 800
- [Decision Matrix](skills/decision-matrix.md) - Multi-criteria analysis ⭐ 650

## Coding & Development
- [Code Review](skills/code-review.md) - Comprehensive reviews (security + quality) ⭐ 2.1k
- [Test Generation](skills/test-gen.md) - Unit tests with edge cases ⭐ 1.5k
- [API Documentation](skills/api-docs.md) - Generate OpenAPI specs ⭐ 900
- [Refactoring Advisor](skills/refactor.md) - Suggest code improvements ⭐ 750

## Analysis & Data
- [Data Profiling](skills/data-profile.md) - Statistical dataset summaries ⭐ 600
- [Log Analysis](skills/log-analysis.md) - Parse and analyze application logs ⭐ 450
- [Performance Audit](skills/perf-audit.md) - Identify bottlenecks ⭐ 550

## Writing & Documentation
- [Technical Writer](skills/tech-writer.md) - Clear technical documentation ⭐ 1.1k
- [Meeting Notes](skills/meeting-notes.md) - Structured summaries from transcripts ⭐ 800
- [README Generator](skills/readme-gen.md) - Comprehensive README from codebase ⭐ 950
```

**Curated Highlights (Cross-Platform):**

**1. Code Review Skill**
- **Capability:** OWASP security + code quality analysis
- **Platforms:** Claude, ChatGPT, Copilot
- **Use Case:** Automate pull request reviews
- **Why Notable:** Comprehensive checklist, actionable output
- **Find:** Search "ai-code-review-skill" on GitHub

**2. Test Generation Skill**
- **Capability:** Generate unit tests with edge case coverage
- **Platforms:** GitHub Copilot, LangChain, Claude
- **Use Case:** TDD workflows, coverage improvement
- **Why Notable:** Framework-agnostic, mocking strategies included
- **Find:** GitHub Copilot Marketplace or awesome-lists

**3. API Documentation Generator**
- **Capability:** Create OpenAPI specs from code annotations
- **Platforms:** Claude, ChatGPT
- **Use Case:** Keep docs synchronized with code
- **Why Notable:** Reduces manual documentation burden
- **Find:** Search "openapi-generator-skill"

**4. Data Profiling Skill**
- **Capability:** Statistical summary + quality assessment of datasets
- **Platforms:** Claude (with Code Interpreter), ChatGPT Advanced Data Analysis
- **Use Case:** Exploratory data analysis
- **Why Notable:** Detects missing data, outliers, distributions
- **Find:** Data analysis skill collections

**5. Meeting Notes Transformer**
- **Capability:** Convert meeting transcripts to structured summaries
- **Platforms:** Claude, ChatGPT
- **Use Case:** Post-meeting documentation
- **Why Notable:** Extracts action items, decisions, attendees
- **Find:** Search "meeting-notes-skill" or "transcript-summarizer"

**6. Decision Matrix Builder**
- **Capability:** Multi-criteria decision analysis with weighted scoring
- **Platforms:** Claude, ChatGPT
- **Use Case:** Strategic planning, vendor selection
- **Why Notable:** Structured approach to complex decisions
- **Find:** Business analysis skill collections

**7. Slide Deck Outliner**
- **Capability:** Generate presentation structure from topic
- **Platforms:** Claude, ChatGPT
- **Use Case:** Rapid prototyping of talks/pitches
- **Why Notable:** Saves hours of outline creation
- **Find:** Search "presentation-skill" or "slide-outliner"

**Quality Evaluation Checklist:**

When browsing community skills, assess:

- ✅ **Clear Objective:** Does it explain what problem it solves?
- ✅ **Detailed Instructions:** Step-by-step, not just high-level
- ✅ **Examples Included:** 2+ demonstrations with inputs/outputs
- ✅ **Recent Updates:** Maintained within last 6 months
- ✅ **User Feedback:** Stars, issues, testimonials

---

### This Repository's Skills

**Live Examples in .github/skills/**

This repository uses the GSD framework, which is skill-based. You can study these skills to understand production patterns:

**Available Skills:**

1. **[execute-plan](../../.github/skills/execute-plan/SKILL.md)**
   - **Purpose:** Execute a PLAN.md and create outcome SUMMARY.md
   - **Pattern:** Task execution with git integration
   - **Lines:** ~1,884 (comprehensive)

2. **[verify-phase](../../.github/skills/verify-phase/SKILL.md)**
   - **Purpose:** Goal-backward verification (did we achieve phase goal?)
   - **Pattern:** Existence → Substantive → Wired checks
   - **Lines:** ~800

3. **[discovery-phase](../../.github/skills/discovery-phase/SKILL.md)**
   - **Purpose:** Research before planning (depth-configurable)
   - **Pattern:** Quick verify / Standard / Deep dive
   - **Lines:** ~600

4. **[transition](../../.github/skills/transition/SKILL.md)**
   - **Purpose:** Mark phase complete and advance to next
   - **Pattern:** Progress tracking, PROJECT.md evolution
   - **Lines:** ~500

**How to Explore:**

```bash
# Navigate to skills directory
cd .github/skills/

# List available skills
ls

# Read a skill
cat execute-plan/SKILL.md

# Study the pattern:
# 1. Frontmatter with metadata
# 2. <purpose> section
# 3. <required_reading> dependencies
# 4. <process> with <step> elements
# 5. Examples and edge cases
```

**Learning Exercise:**

Pick one skill (e.g., erify-phase) and trace how it's used:

1. Find where skill is invoked (search codebase for erify-phase)
2. See what inputs it receives
3. Observe what outputs it produces
4. Understand why it's structured this way

**Best For:** Understanding real-world skill architecture used in production

---

## Creating Your Own Skills 🔴 Advanced

### Skill Design Workflow

**Step 1: Identify Capability Gap**

Ask: "What task do I repeat often that could be standardized?"

Examples:
- "I keep asking for code reviews in the same format"
- "I manually check PRs for the same security issues"
- "I write similar API documentation templates"

**Step 2: Define Objective**

Write 2-3 sentences:
- **What** capability does this skill provide?
- **What problem** does it solve?
- **What outcome** should it produce?

Example:
```
Skill: PR Quality Gate

Objective: Automatically check pull requests for merge readiness.
Evaluates: tests passing, code coverage > 80%, no security vulnerabilities,
PR description complete, CI/CD success. Outputs: Pass/Fail + blockers list.
```

**Step 3: Write Instructions**

Break capability into steps:

```markdown
## Instructions

1. **Analyze PR Context**
   - Read PR title and description
   - Check linked issue/ticket
   - Review file changes (count, types)

2. **Run Automated Checks**
   - Verify CI/CD status (all checks green?)
   - Check test coverage report (> 80%?)
   - Run security scan (0 Critical/High?)

3. **Assess PR Description**
   - Contains "What" (changes made)
   - Contains "Why" (motivation/context)
   - Lists testing performed

4. **Generate Gate Decision**
   - If all pass → "✅ Ready to Merge"
   - If any fail → "❌ Blocked" + list blockers
```

**Step 4: Add 2-3 Examples**

Show the skill in action:

```markdown
## Example 1: PR Passes Gate

**Input:**
- PR #142: "Add user authentication"
- Description: [Complete with what/why/testing]
- CI Status: ✅ All checks passed
- Coverage: 87%
- Security Scan: 0 issues

**Output:**
\\\
✅ PR Ready to Merge

All quality gates passed:
- ✅ CI/CD: All checks green
- ✅ Coverage: 87% (target: 80%)
- ✅ Security: No vulnerabilities
- ✅ Description: Complete

Approved for merge.
\\\

## Example 2: PR Blocked

**Input:**
- PR #143: "Update payment logic"
- Description: "Fixed bug" (minimal)
- CI Status: ⚠️  1 test failing
- Coverage: 65%
- Security Scan: 1 High severity issue

**Output:**
\\\
❌ PR Blocked - Cannot Merge

Blockers:
1. ❌ CI/CD: Test failing (test/payment.test.ts:42)
2. ❌ Coverage: 65% (target: 80%, need +15%)
3. ❌ Security: SQL Injection vulnerability (src/payment.ts:28)
4. ⚠️  Description: Missing "Why" and testing details

Required Actions:
- Fix failing test
- Add tests to reach 80% coverage
- Address SQL Injection (use parameterized query)
- Expand PR description

Re-run gate after fixing.
\\\
```

**Step 5: Document Anti-Patterns**

What NOT to do:

```markdown
## Anti-Patterns

- ❌ **Ignoring Context:** Blocking PR because coverage dipped 1% due to refactoring
  (Check: Did overall coverage improve elsewhere?)

- ❌ **False Positives:** Flagging intentional design patterns as security issues
  (Verify: Is this actually a vulnerability in context?)

- ❌ **Over-Automation:** Auto-blocking without explanation
  (Always: Provide clear, actionable feedback)
```

**Step 6: Define Success Criteria**

How to verify skill worked correctly:

```markdown
## Success Criteria

- [ ] Decision reached within 30 seconds
- [ ] All 4 gate criteria evaluated
- [ ] Clear pass/fail with specific blockers
- [ ] No false positives (flagging non-issues)
- [ ] Actionable feedback (tell developer what to fix)
```

---

### Testing and Iteration

**Test with Real Inputs:**

```bash
# Create test cases
test-cases/
├── happy-path/       # Should pass
├── blocked-coverage/ # Should fail (coverage)
├── blocked-ci/       # Should fail (CI)
└── edge-cases/       # Unusual scenarios
```

**Refine Based on Results:**

1. Run skill on 10 diverse test cases
2. Check output quality:
   - Are decisions correct?
   - Is feedback actionable?
   - Any false positives/negatives?
3. Update instructions to handle gaps
4. Add new examples for edge cases
5. Repeat until consistent quality

**Version Your Skill:**

```markdown
---
name: pr-quality-gate
version: 1.0.0 → 1.1.0 (after refinements)
updated: 2026-02-27
changelog:
  - 1.1.0: Added edge case handling for monorepo coverage
  - 1.0.1: Fixed false positive for intentional assertions
  - 1.0.0: Initial release
---
```

---

## Best Practices

### Principle 1: Single Responsibility

**Do:** One skill, one capability
```
✅ "Code Review Skill" - Reviews code
✅ "Test Generation Skill" - Generates tests
```

**Don't:** God skills that do everything
```
❌ "Ultimate Dev Skill" - Reviews, tests, docs, deploys, makes coffee
```

### Principle 2: Clear Instructions

**Do:** Step-by-step, no ambiguity
```
✅ "Check for SQL injection: Look for string concatenation in queries"
```

**Don't:** Vague guidance
```
❌ "Make sure code is secure"
```

### Principle 3: Examples-Driven

**Do:** Show, don't just tell (2-3 examples minimum)
```
✅ Include input → execution trace → output for each example
```

**Don't:** Abstract instructions without demonstrations
```
❌ Just instructions, no examples
```

### Principle 4: Version Control

**Do:** Track changes, maintain compatibility
```markdown
version: 2.1.0
changelog:
  - 2.1.0: Added edge case handling
  - 2.0.0: Breaking change - new output format
  - 1.0.0: Initial release
```

**Don't:** Silent updates that break dependencies
```
❌ Modify skill without version bump
```

### Principle 5: Testable

**Do:** Define success criteria, validate outputs
```markdown
## Success Criteria
- [ ] Completes in < 60 seconds
- [ ] Output matches format specification
- [ ] No false positives in test suite (100 cases)
```

**Don't:** "Looks good" without verification
```
❌ No way to measure skill quality
```

---

## Common Pitfalls

### ❌ Pitfall 1: Vague Skill

**Problem:** "Be helpful and thorough"  
**Why it fails:** No actionable instructions for AI  
**Fix:** Specific steps with decision criteria

### ❌ Pitfall 2: God Skill

**Problem:** Skill tries to do 10 different things  
**Why it fails:** Maintenance nightmare, hard to debug, inconsistent quality  
**Fix:** Break into focused sub-skills

### ❌ Pitfall 3: Example-Free

**Problem:** Abstract instructions without demonstrations  
**Why it fails:** AI can't infer intent, produces inconsistent results  
**Fix:** Add 2-3 concrete examples with inputs/outputs

### ❌ Pitfall 4: Stale Skill

**Problem:** Created once, never updated  
**Why it fails:** Breaks silently as context changes  
**Fix:** Version control, regular reviews, changelog

### ❌ Pitfall 5: No Constraints

**Problem:** Doesn't specify what NOT to do  
**Why it fails:** AI explores unintended behaviors  
**Fix:** Explicit anti-patterns section

---

## Hands-On Exercises

### Exercise 1: Analyze a GSD Skill (15 minutes)

**Scenario:** Study a production skill in this repository

**Steps:**
1. Read [.github/skills/execute-plan/SKILL.md](../../.github/skills/execute-plan/SKILL.md)
2. Identify these components:
   - Metadata (name, description)
   - Objective/Purpose
   - Instructions (how many steps?)
   - Examples (present?)
   - Success criteria
3. Answer:
   - What makes this skill effective?
   - What patterns can you reuse?
   - How is it structured differently than a prompt?

**Success Criteria:**
- Can list 3 design patterns used in the skill
- Can explain why it's 1,884 lines (comprehensive instructions)
- Understands when to use this skill vs simpler approach

---

### Exercise 2: Create a Simple Skill (25 minutes)

**Scenario:** Design a "Bug Report Analyzer" skill

**Goal:** Extract structured information from bug reports

**Steps:**

1. **Define Objective** (5 min)
   ```
   What: Extract title, reproduction steps, expected/actual behavior
   Why: Standardize bug report intake for triage
   Output: Structured JSON with severity assessment
   ```

2. **Write Instructions** (10 min)
   ```markdown
   ##Instructions
   
   1. Parse bug report text
   2. Extract:
      - Title/Summary
      - Steps to reproduce
      - Expected behavior
      - Actual behavior
      - Environment (OS, version)
   3. Assess severity:
      - CRITICAL: Data loss, security breach
      - HIGH: Core functionality broken
      - MEDIUM: Feature impaired
      - LOW: Cosmetic issue
   4. Output JSON format:
      {
        "title": "...",
        "reproduction_steps": ["step1", "step2"],
        "expected": "...",
        "actual": "...",
        "severity": "HIGH",
        "missing_info": ["Screenshot needed"]
      }
   ```

3. **Add 2 Examples** (8 min)
   - Example 1: Well-formed bug report → complete JSON
   - Example 2: Incomplete bug report → JSON with missing_info

4. **Document Anti-Patterns** (2 min)
   - ❌ Guessing missing information (should flag as missing)
   - ❌ Over-/under-estimating severity

**Success Criteria:**
- Skill produces consistent structured output
- Identifies missing information
- Severity assessment matches guidelines

---

### Exercise 3: Compose Multiple Skills (30 minutes)

**Scenario:** Build "Code Quality Workflow" from sub-skills

**Goal:** Combine Code Review + Test Generation skills

**Steps:**

1. **Design Workflow** (10 min)
   ```
   Parent Skill: Code Quality Workflow
   
   Step 1: Apply Code Review Skill → identify gaps
   Step 2: Apply Test Generation Skill → cover gaps
   Step 3: Aggregate results → unified report
   ```

2. **Write Orchestration Instructions** (15 min)
   ```markdown
   ## Instructions

   1. **Security & Quality Review**
      - Load: code-review-skill.md
      - Execute on: [target files]
      - Collect: security_issues, quality_issues

   2. **Generate Tests for Gaps**
      - Load: test-generation-skill.md
      - Input: code + security_issues (prioritize vulnerable areas)
      - Generate: test_suite covering edge cases

   3. **Aggregate Report**
      - Combine findings:
        - Security: [Critical/High only]
        - Quality: [Top 5 issues]
        - Tests: [Coverage metrics]
      - Output: Quality dashboard
   ```

3. **Test Workflow** (5 min)
   - Run on sample codebase
   - Verify both sub-skills execute
   - Check aggregated output quality

**Success Criteria:**
- Workflow executes sub-skills in order
- Results from skill 1 inform skill 2
- Unified report combines both outputs
- More comprehensive than either skill alone

---

### Exercise 4: Integrate Skill into Claude Project (20 minutes)

**Scenario:** Add custom skill to Claude for persistent use

**Goal:** Skill consistently applied across conversations

**Steps:**

1. **Create Claude Project** (5 min)
   - Open Claude
   - Create new Project: "Code Review Assistant"

2. **Upload Skill** (5 min)
   - Write skill markdown (use Exercise 2 or real skill)
   - Add to Project Knowledge

3. **Write System Instructions** (5 min)
   ```
   You have access to the Bug Report Analyzer skill.
   
   When user provides a bug report:
   1. Apply the skill from Project Knowledge
   2. Extract structured information
   3. Present findings in JSON format
   
   Proactively suggest using the skill when you detect unstructured bug reports.
   ```

4. **Test** (5 min)
   - Paste a bug report
   - Verify Claude applies skill
   - Check output matches expected format

**Success Criteria:**
- Claude recognizes when to apply skill
- Output follows skill instructions consistently
- Skill persists across conversations in that Project

---

## Resources

### Anthropic Model Context Protocol (MCP) Documentation
- **Type:** Official Documentation
- **Duration:** 45 min read
- **Level:** Intermediate to Advanced
- **What:** Complete technical guide to building MCP servers that extend Claude's capabilities
- **Why:** Learn to create production-grade skills with external integrations
- **Best for:** Developers building Claude-integrated tools
- **Free:** Yes
- **Link:** [Anthropic MCP Docs](https://www.anthropic.com/news/model-context-protocol)

### GitHub Copilot Extensions Marketplace
- **Type:** Platform / Marketplace
- **Duration:** 30 min exploration
- **Level:** Beginner to Intermediate
- **What:** Browse available extensions/skills for GitHub Copilot
- **Why:** See what's possible, evaluate quality patterns, find reusable skills
- **Best for:** Developers using GitHub Copilot
- **Free:** Yes (extensions may vary)
- **Link:** [Copilot Extensions](https://github.com/marketplace?type=apps&copilot_app=true)

### OpenAI GPTs Store
- **Type:** Platform / Marketplace
- **Duration:** 20 min exploration
- **Level:** Beginner
- **What:** Explore thousands of custom GPTs (packaged skills)
- **Why:** Understand capabilities, interaction patterns, quality indicators
- **Best for:** Anyone using ChatGPT
- **When to browse:** Looking for pre-built skills before creating your own, exploring what's possible
- **Free:** Yes (requires ChatGPT Plus for some GPTs)
- **Link:** [GPTs Store](https://chat.openai.com/gpts)

### Prompt Engineering Guide - Skill Patterns
- **Type:** Documentation / Tutorial
- **Duration:** 35 min read + exercises
- **Level:** Intermediate
- **What:** Design patterns for creating reusable AI capabilities
- **Why:** Learn theoretical foundations of skill design
- **Best for:** Understanding architecture principles
- **Free:** Yes
- **Link:** [Prompt Engineering Guide](https://www.promptingguide.ai/)

### Awesome AI Skills - GitHub Collection
- **Type:** Curated List
- **Duration:** 1-2 hours browsing
- **Level:** Beginner to Advanced
- **What:** Community-curated collection of high-quality AI skills with examples and ratings
- **Why:** Discover what exists, avoid reinventing, learn from quality examples
- **Best for:** Discovering reusable patterns and avoiding reinventing the wheel, finding skills across platforms
- **Free:** Yes
- **Link:** Search GitHub for "awesome-ai-skills" or "awesome-prompts"

### LangChain Tools Documentation
- **Type:** Documentation
- **Duration:** 30 min read
- **Level:** Intermediate (Python knowledge helpful)
- **What:** Comprehensive catalog of pre-built tools/skills for LangChain agents
- **Why:** See code-based skill implementations, integration patterns
- **Best for:** Python developers building AI agents
- **Free:** Yes
- **Link:** [LangChain Tools](https://python.langchain.com/docs/integrations/tools/)

### This Repository's .github/skills/
- **Type:** Live Code Examples
- **Duration:** 1-2 hours studying
- **Level:** Intermediate to Advanced
- **What:** Production skills used by GSD framework (execute-plan, verify-phase, etc.)
- **Why:** Real-world skill architecture, patterns you can copy
- **Best for:** Understanding how skills work in practice
- **When to study:** After completing Section 3 (GSD Framework), want to see real-world skill examples
- **Free:** Yes (this repo)
- **Link:** [.github/skills/](../../.github/skills/)

---

## What's Next?

**✅ You've completed: AI Skills & Capabilities**

You now understand:
- What AI skills are and how they work
- Skill packaging formats and integration patterns
- Platform-specific skill implementations
- How to create and test your own skills

**▶️ Next up:** [6. Capstone →](../06-capstone/README.md) — Build a complete portfolio project demonstrating everything you've learned

**Navigation:**
- [← Previous: 4. Agents](../04-agents/README.md)
- [Home: Learning Pathway](../README.md)
- [Next: 6. Capstone →](../06-capstone/README.md)

---

*This section is part of the AI Working Enablement & Skill Pathway. For the full learning path, see the [main README](../README.md).*
