---
**📍 Current Location:** [Pathway Home](../README.md) → 4. Agents

**📊 Progress:** Section 4 of 6 | ⏱️ Estimated time: 35 minutes

**Prerequisites:** [1. Ecosystem](../01-ecosystem/README.md), [3. GSD Framework](../03-gsd/README.md) — Understanding AI categories and structured workflows

---

# 4. AI Agents & Orchestration

## Table of Contents

- [Overview](#overview)
- [Agents vs Assistants - Deep Dive](#agents-vs-assistants---deep-dive)
- [Agent Architecture Patterns](#agent-architecture-patterns)
- [Delegation Patterns](#delegation-patterns)
- [Multi-Agent Orchestration](#multi-agent-orchestration)
- [Platform-Specific Agents](#platform-specific-agents)
- [Best Practices](#best-practices)
- [Common Pitfalls](#common-pitfalls)
- [Hands-On Exercises](#hands-on-exercises)
- [Resources](#resources)

---

## Overview

**What are AI Agents?**

AI agents are autonomous systems that work toward goals with minimal human intervention. Unlike assistants that respond to prompts, agents plan multi-step approaches, use tools, maintain state, and adapt based on results.

**Core Difference:**
```
Assistant: You ask → AI responds → You act → Repeat
Agent:     You set goal → Agent plans → Agent executes → Agent reports
```

**Why Agents Matter:**

Agents enable you to **delegate entire workflows** rather than guide every step. This shifts your role from "driver" to "manager" — you define outcomes, agents handle execution.

**Core Agent Capabilities:**

1. **Planning** - Break complex goals into actionable steps
2. **Tool Use** - Execute actions (API calls, file operations, commands)
3. **Memory** - Maintain context across actions and sessions
4. **Reasoning** - Evaluate results and adjust approach
5. **Autonomy** - Make tactical decisions without constant human input

**Evolution Path:**

```
Chatbots → Assistants → Copilots → Agents → Autonomous Agents
  ↓           ↓            ↓          ↓            ↓
Answer    Respond to   Proactive  Multi-step   Unsupervised
 Q&A      commands    suggestions  workflows     operation
```

**When to Use Agents vs Assistants:**

**Use Assistants when:**
- Learning concepts or exploring ideas
- Need explanations or guidance
- Want to maintain full control
- Task is conversational (Q&A, brainstorming)

**Use Agents when:**
- Task has clear goal and success criteria
- Multiple steps required
- Need tool use (file creation, API calls, commands)
- Ready to review outcomes rather than guide process

**Key Insight:** Agents don't eliminate human involvement — they shift it from execution to oversight. You verify outcomes, provide feedback, and course-correct rather than perform each step manually.

---

## Agents vs Assistants - Deep Dive 🟢 Beginner

### Capability Comparison

| Dimension | Assistant | Agent |
|-----------|-----------|-------|
| **Autonomy** | Reactive (prompted) | Proactive (goal-driven) |
| **Scope** | Single task | Multi-step workflows |
| **Memory** | Conversation only | Persistent state across sessions |
| **Planning** | No - suggests steps | Yes - decomposes goals autonomously |
| **Tool Use** | Limited (text generation) | Extensive (APIs, files, commands, databases) |
| **Decision Loop** | Human decides next action | Agent decides next action |
| **Error Handling** | Reports errors to human | Attempts autonomous recovery |
| **Verification** | Human tests outcome | Self-verifies when possible |

### The Agency Spectrum

```
Low Agency ←──────────────────────────────────────────→ High Agency

[Chatbot] → [Assistant] → [Copilot] → [Agent] → [Autonomous]
    ↓            ↓             ↓          ↓           ↓
  React      Execute      Suggest     Plan &      Independent
   to Q      commands      as you    Execute      operation
                           work      workflow
```

**Agency Level Examples:**

**Level 1: Chatbot (Zero Agency)**
```
You: "How do I deploy?"
Bot: "Run: npm run build && vercel deploy"
→ Bot provides information only
```

**Level 2: Assistant (Reactive)**
```
You: "Write a deployment script"
Assistant: [Generates script]
You: [Copy, save, execute manually]
→ Assistant helps, you act
```

**Level 3: Copilot (Contextual Suggestions)**
```
You: [Type "function deploy"]
Copilot: [Suggests complete implementation]
You: [Accept or modify]
→ Copilot anticipates needs
```

**Level 4: Agent (Goal Execution)**
```
You: "Deploy to production"
Agent:
  1. Runs tests
  2. Builds production bundle
  3. Uploads to server
  4. Runs migrations
  5. Restarts services
  6. Verifies deployment
→ Agent handles full workflow
```

**Level 5: Autonomous (Ongoing)**
```
You: "Maintain this service"
Autonomous Agent:
  - Monitors errors
  - Fixes simple bugs
  - Rolls back bad deploys
  - Notifies on complex issues
→ Agent operates continuously
```

### Mental Model Shift

**Old Model: Assistant (Conversational Partner)**

```
Your Role: Active participant
AI Role:   Knowledgeable consultant

Workflow:
1. You ask question
2. AI provides answer
3. You implement solution
4. You test
5. You fix issues
6. Repeat

Control: 100% yours
Speed:   Limited by your execution
```

**New Model: Agent (Delegated Employee)**

```
Your Role: Manager setting goals
AI Role:   Capable executor

Workflow:
1. You define goal & constraints
2. Agent plans approach
3. Agent implements
4. Agent tests
5. Agent fixes issues
6. You review outcome

Control: Strategic (set direction)
Speed:   Limited by agent capability
```

**Communication Pattern Changes:**

| Aspect | Assistant Communication | Agent Communication |
|--------|------------------------|---------------------|
| **Input** | Detailed instructions | Goal + constraints |
| **Output** | Suggestions & explanations | Completed work |
| **Feedback** | "That's wrong, here's why" | "This doesn't meet requirements, revise" |
| **Verification** | You test manually | Agent tests, you verify |
| **Iteration** | Explicit next prompt | Agent continues until done |

### Trade-offs: When NOT to Use Agents

**Agents Add Complexity:**
- Need clear goals and success criteria
- Require error handling and rollback strategies
- May make mistakes that compound
- Cost more (tokens for planning + execution + verification)

**Stick with Assistants if:**

❌ **Exploratory work**
```
"I'm not sure what I need yet"
→ Assistant helps you figure it out through conversation
```

❌ **Learning**
```
"Teach me how authentication works"
→ Assistant explains step-by-step
```

❌ **High-risk actions**
```
"Deploy to production with database migration"
→ Too risky for autonomous execution
```

❌ **Unclear requirements**
```
"Make the UI better"
→ Too vague for agent to execute
```

❌ **Rapid iteration**
```
"Try this, no that, wait go back"
→ Conversational flow better than agent replanning
```

**Use Agents when:**

✅ **Well-defined tasks**
```
"Implement password reset with email verification"
→ Clear goal, known pattern
```

✅ **Multi-step workflows**
```
"Set up CI/CD pipeline with testing and deployment"
→ Multiple sequential actions
```

✅ **Repetitive automation**
```
"Generate API endpoints for these 5 models"
→ Repetitive pattern
```

✅ **File-heavy operations**
```
"Refactor auth code into separate module"
→ Multiple file changes
```

### Real-World Example

**Scenario:** Create user authentication system

**Assistant Approach:**

```
Turn 1:
You: "How should I structure user authentication?"
Assistant: [Explains architecture options]

Turn 2:
You: "OK, using JWT. Show me the user model"
Assistant: [Provides code]
You: [Copy to user.ts]

Turn 3:
You: "Now the registration endpoint"
Assistant: [Provides code]
You: [Copy to routes/auth.ts]

Turn 4:
You: "How do I hash passwords?"
Assistant: [Explains bcrypt]

Turn 5:
You: "Write the password hashing function"
Assistant: [Provides code]
You: [Copy to utils/password.ts]

[...10 more turns...]

Result: 30 minutes of guided conversation
```

**Agent Approach:**

```
You: "Implement user authentication with:
      - JWT tokens (1 hour expiry)
      - Email/password registration
      - Login endpoint
      - Password hashing (bcrypt)
      - Middleware to protect routes
      
      Use our Express + TypeScript stack.
      Follow patterns in existing auth code.
      Include tests."

Agent:
[Creates user model: src/models/User.ts]
[Creates auth service: src/services/auth.ts]
[Creates endpoints: src/routes/auth.ts]
[Creates middleware: src/middleware/authenticate.ts]
[Creates tests: src/__tests__/auth.test.ts]
[Runs tests: ✓ All 12 tests pass]

Agent: "Authentication implemented. Files created:
        - 5 source files
        - 1 test file (12 tests)
        All tests passing. Ready for review."

Result: 5 minutes (agent work) + your review time
```

**Key Difference:**  
Assistant requires you to orchestrate. Agent orchestrates itself.

---

## Agent Architecture Patterns 🟡 Intermediate

### Core Components

Every agent system, regardless of platform, combines four fundamental components:

**1. Planning**
- Decompose goals into actionable steps
- Determine execution order
- Identify required tools/resources

**2. Memory**
- Short-term: Current task context
- Long-term: Cross-session knowledge
- Working: Results from previous steps

**3. Tool Use**
- External APIs
- File system operations
- Code execution
- Database queries

**4. Reasoning**
- Evaluate step outcomes
- Decide next action
- Handle errors and edge cases

### The ReAct Pattern

**ReAct** (Reason + Act) is the dominant agent architecture pattern.

**How ReAct Works:**

```
User Goal: "Find and fix the bug causing login failures"

┌─────────────────────────────────────────┐
│ 1. REASON (Thinking)                    │
│    "Need to check error logs first"     │
└─────────────────────────────────────────┘
         ↓
┌─────────────────────────────────────────┐
│ 2. ACT (Action)                         │
│    Tool: read_file("logs/error.log")    │
└─────────────────────────────────────────┘
         ↓
┌─────────────────────────────────────────┐
│ 3. OBSERVE (Result)                     │
│    "Error: Invalid token signature"     │
└─────────────────────────────────────────┘
         ↓
┌─────────────────────────────────────────┐
│ 4. REASON                               │
│    "Token signing might have changed"   │
└─────────────────────────────────────────┘
         ↓
┌─────────────────────────────────────────┐
│ 5. ACT                                  │
│    Tool: read_file("utils/jwt.ts")      │
└─────────────────────────────────────────┘
         ↓
┌─────────────────────────────────────────┐
│ 6. OBSERVE                              │
│    "Using HS256, secret changed last wk"│
└─────────────────────────────────────────┘
         ↓
┌─────────────────────────────────────────┐
│ 7. REASON                               │
│    "Old tokens invalid, need to update  │
│     secret or migrate tokens"           │
└─────────────────────────────────────────┘
         ↓
┌─────────────────────────────────────────┐
│ 8. ACT                                  │
│    Report findings + proposed solutions │
└─────────────────────────────────────────┘

Goal achieved: Root cause identified
```

**ReAct Loop Structure:**

```python
def react_agent(goal):
    context = {"goal": goal, "history": []}
    
    while not goal_achieved(context):
        # REASON: Decide next action
        thought = llm.generate(
            f"Goal: {goal}\n"
            f"History: {context['history']}\n"
            f"What should I do next?"
        )
        
        # ACT: Execute action
        action = extract_action(thought)
        result = execute_tool(action)
        
        # OBSERVE: Record result
        context['history'].append({
            "thought": thought,
            "action": action,
            "result": result
        })
        
        # Check if goal met
        if should_stop(context):
            break
    
    return context['history']
```

### Chain-of-Thought Reasoning

**Chain-of-Thought** (CoT) makes agent reasoning explicit:

**Without CoT:**
```
Agent: [Directly generates code]
→ Black box, can't debug reasoning
```

**With CoT:**
```
Agent thinks (visible):
"I need to:
1. Check current authentication method
2. Identify where tokens are validated
3. Find the signing secret location
4. Determine if secret rotated recently
5. Propose fix"

Agent acts:
[Executes each step with reasoning]
→ You can see WHY agent made each decision
```

### Tool Use Mechanics

Agents interact with tools through **function calling**:

**Tool Definition:**

```python
tools = [
    {
        "name": "read_file",
        "description": "Read contents of a file",
        "parameters": {
            "filepath": {
                "type": "string",
                "description": "Path to file"
            }
        }
    },
    {
        "name": "run_command",
        "description": "Execute shell command",
        "parameters": {
            "command": {
                "type": "string",
                "description": "Command to run"
            }
        }
    }
]
```

**Agent Tool Selection:**

```python
# Agent decides: "I need to read the config file"

agent_response = {
    "tool": "read_file",
    "parameters": {
        "filepath": "config/auth.ts"
    },
    "reasoning": "Need to check JWT configuration"
}

# Execute tool
result = read_file("config/auth.ts")

# Agent receives result and continues
```

### State Management

Agents maintain state across actions:

**Short-term Memory (Task Context):**
```python
task_state = {
    "goal": "Implement user registration",
    "steps_completed": [
        "Created user model",
        "Added validation schema"
    ],
    "current_step": "Implement registration endpoint",
    "files_modified": ["models/User.ts", "schemas/user.ts"]
}
```

**Long-term Memory (Cross-Session):**
```python
agent_knowledge = {
    "project_conventions": {
        "auth_pattern": "JWT with refresh tokens",
        "error_handling": "Custom AppError class",
        "test_framework": "Jest"
    },
    "past_decisions": [
        "Use Prisma for ORM (decided 2024-01-15)",
        "Prefer async/await over promises"
    ]
}
```

### Error Handling Patterns

**Pattern 1: Retry with Backoff**

```python
def agent_action_with_retry(action, max_retries=3):
    for attempt in range(max_retries):
        try:
            result = execute(action)
            return result
        except Exception as e:
            if attempt < max_retries - 1:
                # Agent reasons about error
                diagnosis = llm.diagnose_error(e)
                # Agent adjusts approach
                action = modify_based_on_error(action, diagnosis)
                time.sleep(2 ** attempt)  # Exponential backoff
            else:
                # Final attempt failed, escalate to human
                return {"error": str(e), "need_human": True}
```

**Pattern 2: Graceful Degradation**

```
Goal: Deploy application

Agent attempts:
1. Run full test suite → PASS
2. Build production bundle → FAIL (dependency error)
   ↓
   Agent diagnoses: Missing dependency
   Agent action: npm install missing-package
   Agent retries: Build → PASS
3. Deploy to staging → PASS
4. Run smoke tests → PASS
5. Deploy to production → Request human approval

→ Agent handled error autonomously, escalated risky action
```

---

## Delegation Patterns 🟡 Intermediate

### Task Decomposition Pattern

**Pattern:** Break complex goals into manageable subtasks.

**When to Use:**
- Goal involves 5+ distinct steps
- Steps can be parallelized or sequenced
- Each step has clear completion criteria

**Example: "Build Authentication System"**

**Agent Decomposition:**

```
Main Goal: Implement complete authentication

Decomposed Tasks:
1. Database Setup
   - Create User model (id, email, password_hash, created_at)
   - Add migration
   - Update Prisma schema

2. Password Management
   - Install bcrypt
   - Implement hash function
   - Implement verify function

3. JWT Handling
   - Install jose library
   - Implement token generation
   - Implement token verification
   - Implement refresh token rotation

4. API Endpoints
   - POST /auth/register
   - POST /auth/login
   - POST /auth/refresh
   - POST /auth/logout

5. Middleware
   - requireAuth middleware
   - extractUser middleware

6. Testing
   - Unit tests for password functions
   - Unit tests for JWT functions
   - Integration tests for endpoints

Each task is independently testable and completable.
```

**Code Example: Python Agent**

```python
class PlannerAgent:
    def decompose_goal(self, goal):
        prompt = f"""
        Break down this goal into specific, actionable subtasks:
        
        Goal: {goal}
        
        Return JSON array of tasks, each with:
        - name: Clear task name
        - description: What to do
        - dependencies: List of task names that must complete first
        - estimated_complexity: low/medium/high
        """
        
        response = llm.generate(prompt)
        tasks = json.loads(response)
        return tasks

class ExecutorAgent:
    def execute_task(self, task):
        print(f"Executing: {task['name']}")
        
        # Agent plans implementation
        plan = llm.generate(f"How to implement: {task['description']}")
        
        # Agent executes each step
        for step in plan['steps']:
            result = self.execute_step(step)
            if result['success']:
                print(f"  ✓ {step['name']}")
            else:
                return {"success": False, "error": result['error']}
        
        return {"success": True}

# Orchestrator
def build_feature(goal):
    planner = PlannerAgent()
    executor = ExecutorAgent()
    
    # Decompose
    tasks = planner.decompose_goal(goal)
    
    # Execute in order
    for task in tasks:
        result = executor.execute_task(task)
        if not result['success']:
            print(f"Failed: {task['name']}")
            break
    
    return "Complete"
```

### Specialist Delegation Pattern

**Pattern:** Route tasks to specialized agents based on domain.

**When to Use:**
- Tasks require different expertise (frontend vs backend vs testing)
- Specialists have different tool access
- Different error handling per domain

**Example: Full-Stack Feature Implementation**

```
Coordinator Agent receives: "Add product review feature"

Coordinator delegates:
┌────────────────────────────────────────────┐
│ Backend Specialist Agent                   │
│ - Create Review model                      │
│ - Add API endpoints                        │
│ - Implement validation                     │
└────────────────────────────────────────────┘
               ↓ (API complete)
┌────────────────────────────────────────────┐
│ Frontend Specialist Agent                  │
│ - Create review form component             │
│ - Add API client functions                 │
│ - Implement UI for displaying reviews      │
└────────────────────────────────────────────┘
               ↓ (UI complete)
┌────────────────────────────────────────────┐
│ Testing Specialist Agent                   │
│ - Write backend API tests                  │
│ - Write frontend component tests           │
│ - Write E2E user flow tests                │
└────────────────────────────────────────────┘
```

**Code Example:**

```python
class CoordinatorAgent:
    def __init__(self):
        self.backend = BackendAgent()
        self.frontend = FrontendAgent()
        self.testing = TestingAgent()
    
    def implement_feature(self, feature_description):
        # Analyze feature requirements
        requirements = self.analyze_requirements(feature_description)
        
        results = {}
        
        # Backend implementation
        if requirements['needs_api']:
            results['backend'] = self.backend.implement(
                requirements['backend_tasks']
            )
        
        # Frontend implementation (waits for backend)
        if requirements['needs_ui'] and results['backend']['success']:
            results['frontend'] = self.frontend.implement(
                requirements['frontend_tasks'],
                api_spec=results['backend']['api_spec']
            )
        
        # Testing (waits for both)
        if results['backend']['success'] and results['frontend']['success']:
            results['testing'] = self.testing.test_feature(
                backend=results['backend'],
                frontend=results['frontend']
            )
        
        return results

class BackendAgent:
    def implement(self, tasks):
        # Has access to backend tools
        tools = ['create_file', 'run_migration', 'start_server']
        
        for task in tasks:
            # Backend-specific implementation
            pass
        
        return {
            "success": True,
            "api_spec": {"endpoints": [...]}
        }
```

### Hierarchical Delegation Pattern

**Pattern:** Parent agent delegates to child agents, who may delegate further.

**Example: GSD Framework**

```
Orchestrator Agent
│
├─→ Planner Agent
│   │
│   ├─→ Research Agent (analyzes codebase)
│   └─→ Design Agent (creates task plan)
│
├─→ Executor Agent
│   │
│   ├─→ per plan in wave 1 (parallel)
│   ├─→ per plan in wave 2 (parallel, after wave 1)
│   └─→ per plan in wave 3 (parallel, after wave 2)
│
└─→ Verifier Agent
    │
    ├─→ Test Agent (runs tests)
    └─→ Quality Agent (checks requirements met)
```

**Hierarchy Example:**

```python
class OrchestratorAgent:
    def execute_phase(self, phase):
        # High-level coordination
        research = self.research_agent.gather_context(phase)
        plan = self.planner_agent.create_plan(phase, research)
        
        # Delegate execution to sub-agents
        results = []
        for wave in plan.waves:
            wave_results = self.execute_wave(wave)
            results.extend(wave_results)
        
        # Delegate verification
        verification = self.verifier_agent.verify(phase, results)
        
        return verification

    def execute_wave(self, wave):
        # Parallel execution of independent plans
        executors = [
            ExecutorAgent(plan) for plan in wave.plans
        ]
        
        results = []
        with ThreadPoolExecutor() as executor:
            futures = [executor.submit(agent.execute) for agent in executors]
            results = [f.result() for f in futures]
        
        return results
```

### Parallel Delegation Pattern

**Pattern:** Execute independent tasks simultaneously.

**When to Use:**
- Tasks have no dependencies
- Can run concurrently
- Want to minimize total time

**Example: Multi-File Refactoring**

```
Goal: Refactor authentication across 5 files

Sequential (Slow):
Agent processes file1 → file2 → file3 → file4 → file5
Time: 5 × 3 minutes = 15 minutes

Parallel (Fast):
┌─ Agent 1: file1 ─┐
├─ Agent 2: file2 ─┤
├─ Agent 3: file3 ─┼─→ Aggregate results
├─ Agent 4: file4 ─┤
└─ Agent 5: file5 ─┘
Time: max(3 minutes) = 3 minutes
```

**Code Example:**

```python
from concurrent.futures import ThreadPoolExecutor

class ParallelDelegator:
    def refactor_files(self, files):
        with ThreadPoolExecutor(max_workers=5) as executor:
            # Submit all tasks at once
            future_to_file = {
                executor.submit(self.refactor_single_file, f): f
                for f in files
            }
            
            # Collect results as they complete
            results = {}
            for future in as_completed(future_to_file):
                file = future_to_file[future]
                try:
                    results[file] = future.result()
                except Exception as e:
                    results[file] = {"error": str(e)}
            
            return results
    
    def refactor_single_file(self, filepath):
        agent = RefactorAgent()
        return agent.refactor(filepath)
```

### Prompt Templates for Delegation

**Template 1: Task Decomposition**

```markdown
You are a planning agent. Break down the following goal into specific,
actionable subtasks.

Goal: {goal}

Context:
- Tech stack: {stack}
- Constraints: {constraints}
- Existing patterns: {patterns}

Output JSON array with each task having:
- id: unique identifier
- name: clear task name
- description: what to accomplish
- dependencies: [list of task IDs that must complete first]
- estimated_effort: low/medium/high
- tools_needed: [list of required tools/dependencies]

Format:
```json
[
  {
    "id": "task-1",
    "name": "Create database schema",
    "description": "Define User and Review models in Prisma schema",
    "dependencies": [],
    "estimated_effort": "low",
    "tools_needed": ["prisma"]
  }
]
```
```

**Template 2: Specialist Routing**

```markdown
You are a coordinator agent. Analyze this task and determine which specialist
should handle it.

Task: {task_description}

Available Specialists:
1. Backend Agent - API endpoints, database, server-side logic
2. Frontend Agent - UI components, state management, client-side
3. DevOps Agent - CI/CD, deployment, infrastructure
4. Testing Agent - Unit, integration, E2E tests

Respond with:
- specialist: Name of appropriate specialist
- reasoning: Why this specialist
- subtasks: List of specific tasks for that specialist

Format:
```json
{
  "specialist": "Backend Agent",
  "reasoning": "Task involves database and API creation",
  "subtasks": ["Create Prisma model", "Add API endpoints", "Implement validation"]
}
```
```

---

## Multi-Agent Orchestration 🔴 Advanced

### Why Multiple Agents?

**Single Agent Limitations:**

```
Complex Goal: "Build and deploy e-commerce site"

Single Agent problems:
❌ Context window overflow (too much to track)
❌ Mixed concerns (design + code + testing + deployment)
❌ Sequential execution (slow)
❌ No specialization (generalist doing specialist work)
❌ Error in one part breaks everything
```

**Multi-Agent Advantages:**

```
✅ Divide and conquer (manageable chunks)
✅ Specialization (each agent expert in domain)
✅ Parallel execution (faster total time)
✅ Isolation (errors contained)
✅ Scalability (add agents as needed)
```

### Orchestration Patterns

**Pattern 1: Coordinator + Specialists**

```
        ┌─────────────────┐
        │  Coordinator    │ (Plans & delegates)
        └────────┬────────┘
                 │
      ┌──────────┴──────────┐
      │                     │
┌─────▼─────┐        ┌─────▼─────┐
│Specialist │        │Specialist │
│    A      │        │    B      │
└───────────┘        └───────────┘
```

**Example: GSD Framework**

```
Orchestrator (gsd CLI)
  ├─ Plan Phase: "Create plan for feature X"
  │    └─ Planner Agent → Produces PLAN.md
  │
  ├─ Execute Phase: "Execute plan"
  │    └─ Executor Agents (parallel) → Implement tasks
  │
  └─ Verify Phase: "Check goals met"
       └─ Verifier Agent → Produces VERIFICATION.md
```

**Pattern 2: Pipeline (Sequential)**

```
Agent A → Agent B → Agent C → Agent D
(Design)  (Implement) (Test)   (Deploy)
```

**Example: CI/CD Pipeline**

```
1. Linter Agent
   ↓ (code clean)
2. Test Agent
   ↓ (tests pass)
3. Build Agent
   ↓ (build succeeds)
4. Deploy Agent
   ↓ (deployed)
5. Monitoring Agent
```

**Pattern 3: Mesh (Interconnected)**

```
    Agent A ←→ Agent B
       ↕          ↕
    Agent C ←→ Agent D
    
(Agents communicate as needed)
```

**Example: Collaborative Code Review**

```
Security Agent ←→ Code Style Agent
       ↕                ↕
Performance Agent ←→ Test Coverage Agent

Each agent reviews independently, shares findings,
flags conflicts for human resolution.
```

### Communication Between Agents

**Mechanism 1: Shared Artifacts (Files)**

```
Agent A creates: task-plan.json
Agent B reads:   task-plan.json
Agent B creates: implementation-summary.json
Agent C reads:   implementation-summary.json

→ File system as communication layer
```

**Mechanism 2: Message Passing**

```python
class MessageBus:
    def __init__(self):
        self.queue = []
    
    def publish(self, sender, message_type, payload):
        self.queue.append({
            "sender": sender,
            "type": message_type,
            "payload": payload,
            "timestamp": time.time()
        })
    
    def subscribe(self, message_type):
        messages = [m for m in self.queue if m['type'] == message_type]
        return messages

# Agent A
bus.publish("planner", "plan_complete", {
    "plan_file": "PLAN.md",
    "tasks": 5
})

# Agent B
plans = bus.subscribe("plan_complete")
if plans:
    plan = plans[0]['payload']
    # Execute based on plan
```

**Mechanism 3: Structured Handoffs**

```yaml
# Handoff from Planner to Executor

planner_output:
  status: complete
  artifacts:
    plan: .gsd/phases/01-foundation/01-01-PLAN.md
  next_agent: executor
  context:
    phase: "01-foundation"
    plan: "01-01"
    tasks: 3
    must_haves:
      - "Project structure created"
      - "Dependencies installed"

executor_input:
  receives: planner_output
  validates:
    - plan file exists
    - tasks are actionable
  executes: all tasks in plan
  outputs: SUMMARY.md
```

### Workflow Diagrams

**GSD Multi-Agent Workflow:**

```
User: "Execute phase 1"
         ↓
   ┌─────────────┐
   │Orchestrator │
   └──────┬──────┘
          │ (delegates)
    ┌─────┴─────┐
    │  Planner  │
    └─────┬─────┘
          │ (creates PLAN.md)
    ┌─────▼─────────────────────┐
    │ PLAN.md                   │
    │ - Wave 1: [task1, task2]  │
    │ - Wave 2: [task3]         │
    └─────┬─────────────────────┘
          │
   ┌──────┴──────┐
   │Orchestrator │ (reads plan)
   └──────┬──────┘
          │ (spawns executors)
    ┌─────┴──────┬─────────┐
    │            │         │
┌───▼───┐   ┌───▼───┐ ┌───▼───┐
│Exec 1 │   │Exec 2 │ │Exec 3 │ Wave 1 (parallel)
│task1  │   │task2  │ │task3  │
└───┬───┘   └───┬───┘ └───┬───┘
    │           │         │
    └───────┬───┴─────────┘
            │ (all complete)
      ┌─────▼──────┐
      │Orchestrator│
      └─────┬──────┘
            │ (delegates verification)
      ┌─────▼────┐
      │ Verifier │
      └─────┬────┘
            │ (creates VERIFICATION.md)
      ┌─────▼─────────┐
      │ VERIFICATION  │
      │ ✓ Goals met   │
      └───────────────┘
```

---

## Platform-Specific Agents 🟡 Intermediate

### Claude Projects

**What:** Workspace-level persistent agent context in Claude web interface.

**Key Features:**
- Upload project knowledge (docs, schemas, patterns)
- Set project-level instructions
- Cross-conversation memory
- Artifact persistence

**Agent Use Case: Research Agent**

```markdown
Setup:
1. Create Claude Project: "Competitive Analysis"
2. Upload documents:
   - competitor-list.md
   - analysis-framework.md
   - past-research/
3. Set instructions:
   "You are a research analyst. When asked to research a company,
    use the analysis framework. Output markdown reports in our standard format."

Usage:
Conversation 1:
You: "Research Competitor A"
Claude: [Uses framework, creates report]

Conversation 2:
You: "Compare Competitors A and B"
Claude: [References previous research, creates comparison]

Conversation 3:
You: "Update Competitor A research with new product launch"
Claude: [Loads previous report, updates with new info]
```

**Best For:**
- Long-term projects with extensive documentation
- Iterative development
- Team collaboration (shared project knowledge)

**Limitations:**
- Web interface only (no IDE integration)
- Manual file management
- Requires Claude Pro subscription

### GitHub Copilot Agents

**What:** Custom agents that extend GitHub Copilot in your development environment.

**Key Features:**
- IDE-integrated (VS Code, Visual Studio, JetBrains)
- Access to full workspace
- Custom tool integration
- Extension ecosystem

**Agent Use Case: Test Generation Agent**

```typescript
// Custom Copilot Agent: test-generator

import { CopilotAgent } from '@github/copilot-sdk';

export const testGeneratorAgent: CopilotAgent = {
  name: 'test-generator',
  description: 'Generates comprehensive tests for code files',
  
  async execute(context) {
    const file = context.currentFile;
    const code = await file.read();
    
    // Agent analyzes code
    const analysis = await analyzeCode(code);
    
    // Agent generates tests
    const tests = await generateTests(analysis);
    
    // Agent creates test file
    await context.workspace.createFile(
      file.path.replace('.ts', '.test.ts'),
      tests
    );
    
    return {
      message: `Generated ${tests.length} tests`,
      artifacts: [testFile]
    };
  }
};
```

**Usage:**
```
In VS Code:
You: "@test-generator Create tests for auth.ts"
Agent: [Analyzes auth.ts, generates auth.test.ts with 15 tests]
```

**Best For:**
- Code-centric workflows
- IDE-integrated automation
- Custom tooling

### AutoGPT

**What:** Autonomous agent that pursues goals with minimal human intervention.

**Key Features:**
- High autonomy (runs until goal met or blocked)
- Plugin ecosystem for tools
- Web browsing and research
- File system access

**Agent Use Case: Web Research Agent**

```yaml
Goal: "Research and summarize the top 5 React state management libraries"

AutoGPT execution:
1. [Web search] "React state management libraries 2024"
2. [Read] Top 10 results
3. [Analyze] Extract key libraries
4. [Web search] "Redux vs Zustand vs Jotai comparison"
5. [Read] Comparison articles
6. [Create] summary.md with findings
7. [Done] Goal achieved

Output: Comprehensive markdown document with:
- Library overviews
- Comparison table
- Use case recommendations
```

**Best For:**
- Research and information gathering
- Autonomous long-running tasks
- Web interaction

**Limitations:**
- Can be unpredictable
- High token costs
- Requires monitoring

### LangChain Agents

**What:** Python framework for building custom agents with tool integration.

**Code Example:**

```python
from langchain.agents import initialize_agent, Tool
from langchain.llms import OpenAI

# Define tools
tools = [
    Tool(
        name="Search",
        func=google_search,
        description="Search the web for current information"
    ),
    Tool(
        name="Calculator",
        func=calculator,
        description="Perform mathematical calculations"
    ),
    Tool(
        name="CodeRunner",
        func=execute_python,
        description="Execute Python code and return results"
    )
]

# Initialize agent
llm = OpenAI(temperature=0)
agent = initialize_agent(
    tools,
    llm,
    agent="zero-shot-react-description",
    verbose=True
)

# Run agent
result = agent.run(
    "What is the square root of the number of GitHub stars "
    "the LangChain repository has?"
)

# Agent execution:
# 1. Searches GitHub for LangChain stars: 50,000
# 2. Calculates square root: 223.6
# 3. Returns: "Approximately 224"
```

**Best For:**
- Custom agent workflows
- Python developers
- Complex tool chains

### CrewAI

**What:** Framework for orchestrating multi-agent teams with roles and tasks.

**Code Example:**

```python
from crewai import Agent, Task, Crew

# Define agents with roles
researcher = Agent(
    role='Research Analyst',
    goal='Find and analyze relevant information',
    backstory='Expert at finding credible sources and synthesizing data',
    tools=[web_search, summarizer]
)

writer = Agent(
    role='Content Writer',
    goal='Create compelling, accurate content',
    backstory='Skilled writer who transforms research into engaging articles',
    tools=[grammar_checker, readability_analyzer]
)

editor = Agent(
    role='Editor',
    goal='Ensure quality and accuracy',
    backstory='Detail-oriented editor with high standards',
    tools=[fact_checker, style_guide]
)

# Define tasks
research_task = Task(
    description='Research the top 3 AI coding tools of 2024',
    agent=researcher
)

writing_task = Task(
    description='Write a 1000-word comparison article based on research',
    agent=writer,
    context=[research_task]  # Depends on research
)

editing_task = Task(
    description='Edit article for clarity, accuracy, and style',
    agent=editor,
    context=[writing_task]  # Depends on writing
)

# Create crew
crew = Crew(
    agents=[researcher, writer, editor],
    tasks=[research_task, writing_task, editing_task],
    verbose=True
)

# Execute workflow
result = crew.kickoff()
print(result)  # Final edited article
```

**Best For:**
- Role-based multi-agent systems
- Content creation workflows
- Complex multi-step processes

### Platform Comparison

| Platform | Best For | Autonomy | Setup | Cost | IDE Integration |
|----------|----------|----------|-------|------|-----------------|
| **Claude Projects** | Research, documentation | Medium | Easy | $$$ (Pro) | No (web only) |
| **Copilot Agents** | Code generation, testing | Medium | Easy | $$$ (Paid) | Yes (VS Code) |
| **AutoGPT** | Web research, automation | High | Medium | $ (API costs) | No |
| **LangChain** | Custom workflows | High | Hard | Free + API | Yes (Python) |
| **CrewAI** | Multi-agent teams | High | Medium | Free + API | Yes (Python) |

---

## Best Practices

**1. Start with Clear Goals**

❌ **Vague:** "Make the app better"
✅ **Specific:** "Add password reset with email verification, 1-hour token expiry"

**2. Define Success Criteria**

```markdown
Agent task: Implement user search

Success criteria:
✓ GET /api/users/search endpoint exists
✓ Accepts 'q' query parameter
✓ Returns max 20 results
✓ Response time < 500ms
✓ Tests pass
✓ Matches existing API patterns
```

**3. Provide Sufficient Context**

```markdown
Context to include:
- Tech stack and versions
- Existing patterns to follow
- Files to reference
- Constraints (what NOT to do)
- Performance requirements
```

**4. Implement Human-in-Loop Checkpoints**

```markdown
High-risk actions requiring approval:
- Database schema changes
- API contract modifications
- Production deployments
- Deleting resources
- Security-related changes
```

**5. Version Control Everything**

```bash
# Before agent work
git checkout -b agent-task-123

# Agent makes changes
# ...

# Review agent's work
git diff

# If good, merge. If not, reset.
git reset --hard origin/main
```

**6. Monitor Costs**

```python
# Track token usage
def agent_with_budget(task, max_tokens=100000):
    tokens_used = 0
    
    while not task_complete() and tokens_used < max_tokens:
        response = agent.execute_step()
        tokens_used += response.token_count
    
    if tokens_used >= max_tokens:
        log_warning(f"Hit budget limit: {tokens_used} tokens")
    
    return result
```

**7. Test Agent Outputs**

```python
# Automated verification
def verify_agent_work(agent_output):
    checks = [
        run_tests(),
        check_code_quality(),
        verify_requirements_met(),
        check_no_security_issues()
    ]
    
    if all(checks):
        return "APPROVED"
    else:
        return "NEEDS_REVISION"
```

**8. Document Agent Decisions**

```markdown
# Agent Decision Log

Task: Implement caching
Agent chose: Redis over in-memory cache

Reasoning:
- Persistence needed across restarts
- Multiple server instances require shared cache
- Redis already in tech stack

Tradeoffs:
- Added complexity: Need Redis instance
- Added latency: Network hop to Redis
- Benefit: Scalability and persistence
```

---

## Common Pitfalls

**1. Over-Automation**

❌ **Mistake:** Letting agent handle everything unsupervised
⚠️ **Result:** Compounding errors, wasted resources
✅ **Solution:** Add checkpoints for high-impact decisions

**2. Vague Instructions**

❌ **Mistake:** "Fix the bugs"
⚠️ **Result:** Agent doesn't know where to start or when done
✅ **Solution:** "Fix bug where login fails when email has uppercase characters"

**3. No Budget Limits**

❌ **Mistake:** Unlimited token budget
⚠️ **Result:** Runaway costs (especially with loops)
✅ **Solution:** Set max tokens/time per task

**4. Ignoring Agent Feedback**

❌ **Mistake:** Agent reports blocker, you don't intervene
⚠️ **Result:** Agent spinning wheels or making wrong assumptions
✅ **Solution:** Monitor agent progress, respond to blockers

**5. No Rollback Strategy**

❌ **Mistake:** Agent makes breaking changes, no way to undo
⚠️ **Result:** Manual cleanup, wasted time
✅ **Solution:** Always work in branches, commit incrementally

**6. Treating Agents Like Humans**

❌ **Mistake:** "Figure out what I want and build it"
⚠️ **Result:** Agent guesses wrong
✅ **Solution:** Explicit goals, constraints, examples

**7. No Verification**

❌ **Mistake:** Trusting agent output without testing
⚠️ **Result:** Bugs in production
✅ **Solution:** Always verify: run tests, review code, check requirements

**8. Insufficient Context**

❌ **Mistake:** "Add auth" (no stack, patterns, or constraints)
⚠️ **Result:** Agent implements wrong approach
✅ **Solution:** Provide tech stack, existing patterns, files to reference

---

## Hands-On Exercises

### Exercise 1: Agent vs Assistant Analysis (10 min)

**Goal:** Practice identifying when to use agents vs assistants.

**Scenarios:** For each, decide: Assistant or Agent?

1. "Explain how WebSockets work"
2. "Implement real-time chat with WebSockets"
3. "What are the tradeoffs of microservices?"
4. "Refactor this monolith into microservices"
5. "Debug why my API returns 500 errors"
6. "Review this pull request for security issues"

**Success Criteria:**
- Correctly categorize 5+/6 scenarios
- Explain reasoning for each

**Reflection:**
- What patterns emerge?
- How does scope affect choice?

---

### Exercise 2: Design Task Decomposition (15 min)

**Scenario:** You need to add "User Profile" feature to your app.

**Goal:** Break down into agent-executable subtasks.

**Requirements:**
- Users can view their profile
- Users can edit name, email, avatar
- Avatar uploads to cloud storage
- Email change requires verification

**Your Task:**
1. List 8-10 specific subtasks
2. Identify dependencies (which must complete first)
3. Mark which can run in parallel

**Template:**
```
Task 1: [Name]
- Description: [What to do]
- Dependencies: [None or list task numbers]
- Can parallelize with: [Task numbers]

Task 2: ...
```

**Success Criteria:**
- Tasks are specific and actionable
- Dependencies correct
- Identified parallelization opportunities

---

### Exercise 3: Implement Simple Orchestration (20 min)

**Goal:** Build a basic multi-agent coordinator.

**Scenario:** Orchestrate planner → executor → verifier flow.

**Code Template:**

```python
class PlannerAgent:
    def plan(self, goal):
        # Return list of tasks
        return ["task1", "task2", "task3"]

class ExecutorAgent:
    def execute(self, task):
        # Execute single task
        print(f"Executing: {task}")
        return {"success": True, "output": f"Completed {task}"}

class VerifierAgent:
    def verify(self, goal, results):
        # Check if goal met
        all_success = all(r["success"] for r in results)
        return {"goal_met": all_success}

def orchestrator(goal):
    # Your code here:
    # 1. Get plan from PlannerAgent
    # 2. Execute each task with ExecutorAgent
    # 3. Verify with VerifierAgent
    # 4. Return results
    pass

# Test
result = orchestrator("Build user authentication")
print(result)
```

**Success Criteria:**
- Orchestrator delegates to all three agents
- Tasks execute in order
- Verification runs after execution
- Returns final result

---

### Exercise 4: Explore Platform Agent (15 min)

**Goal:** Hands-on experience with a real agent platform.

**Choose one:**

**Option A: Claude Projects**
1. Create new Claude Project
2. Upload a sample README.md
3. Set project instructions: "You are a documentation expert. Always suggest improvements."
4. Ask: "Review this README for clarity"
5. In new conversation, reference previous feedback

**Option B: GitHub Copilot (if you have access)**
1. Open VS Code with a code file
2. Use Copilot Chat: "@workspace Explain the auth flow"
3. Ask: "Generate tests for [function name]"
4. Accept generated tests, run them

**Option C: LangChain (if you know Python)**
1. Install: `pip install langchain openai`
2. Create simple agent with search tool
3. Ask agent: "What's trending in web development this week?"
4. Observe agent's tool use

**Success Criteria:**
- Successfully used agent platform
- Observed how agent maintains context or uses tools
- Identified one strength and one limitation

**Reflection:**
- How did agent behavior differ from regular chat?
- What would you use this for in your workflow?

---

## Resources

### 1. LangChain Agents Documentation
**Type:** Technical Guide  
**Duration:** 40 min read  
**Level:** Intermediate to Advanced  
**Free:** Yes  
**Why this matters:** Comprehensive guide to building agents with ReAct pattern, tool use, and orchestration. Best technical resource for understanding agent architectures.  
**Best for:** Developers wanting to build custom agents  
**Link:** [python.langchain.com/docs/modules/agents/](https://python.langchain.com/docs/modules/agents/)

---

### 2. "AI Agents: Autonomous Systems" by Anthropic
**Type:** Research Article  
**Duration:** 25 min read  
**Level:** Intermediate  
**Free:** Yes  
**Why this matters:** Explains agent architectures, autonomy levels, safety considerations, and best practices for delegation from leading AI research lab.  
**Best for:** Understanding agent theory and safety  
**Link:** [anthropic.com/research](https://www.anthropic.com/research)

---

### 3. AutoGPT GitHub Repository
**Type:** Open Source Project  
**Duration:** 1-2 hours exploration  
**Level:** Advanced  
**Free:** Yes  
**Why this matters:** Real-world example of autonomous agent architecture. See how agents plan, execute, use tools, and self-correct in production code.  
**Best for:** Learning from practical implementation  
**Link:** [github.com/Significant-Gravitas/AutoGPT](https://github.com/Significant-Gravitas/AutoGPT)

---

### 4. CrewAI Documentation
**Type:** Framework Guide  
**Duration:** 35 min read  
**Level:** Intermediate  
**Free:** Yes  
**Why this matters:** Practical framework for multi-agent systems with role-based delegation. Excellent patterns for agent collaboration and task coordination.  
**Best for:** Building agent teams  
**Link:** [docs.crewai.com/](https://docs.crewai.com/)

---

### 5. "Building LLM Agents" on OpenAI Cookbook
**Type:** Tutorial  
**Duration:** 45 min read + code  
**Level:** Intermediate  
**Free:** Yes  
**Why this matters:** Official OpenAI guidance on building agents with function calling, tool use, and error handling with practical code examples.  
**Best for:** Hands-on implementation with OpenAI models  
**Link:** [cookbook.openai.com/](https://cookbook.openai.com/)

---

### 6. "The Rise of AI Agents" by a16z
**Type:** Industry Analysis  
**Duration:** 20 min read  
**Level:** Beginner  
**Free:** Yes  
**Why this matters:** High-level overview of agent landscape, use cases, market trends, and future predictions from venture capital perspective.  
**Best for:** Understanding agent ecosystem and opportunities  
**Link:** [a16z.com/ai-agents/](https://a16z.com/)

---

### 7. GitHub Copilot Agents Documentation
**Type:** Official Docs  
**Duration:** 30 min read  
**Level:** Beginner to Intermediate  
**Free:** Requires Copilot subscription  
**Why this matters:** Learn to build custom agents integrated with your development environment. IDE-native agent workflows.  
**Best for:** Extending Copilot with custom automation  
**Link:** [docs.github.com/copilot/](https://docs.github.com/en/copilot)

---

## What's Next?

**✅ You've completed: AI Agents & Orchestration**

You now understand:
- Agents vs assistants (core differences and capabilities)
- Delegation patterns for autonomous work
- Multi-agent orchestration strategies
- Platform-specific agent examples

**▶️ Next up:** [5. Skills →](../05-skills/README.md) — Learn about pre-built AI capabilities and skill integration

**Navigation:**
- [← Previous: 3. GSD Framework](../03-gsd/README.md)
- [Home: Learning Pathway](../README.md)
- [Next: 5. Skills →](../05-skills/README.md)

**Skip ahead** (if experienced):
- [Capstone →](../06-capstone/README.md) — Build your portfolio project

---
