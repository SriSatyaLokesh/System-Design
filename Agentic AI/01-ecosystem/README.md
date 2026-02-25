# 1. Ecosystem

## Table of Contents

- [Overview](#overview)
- [AI Assistants](#ai-assistants)
- [AI Agents](#ai-agents)
- [AI Copilots](#ai-copilots)
- [Chat vs Repo AI](#chat-vs-repo-ai)
- [Resources](#resources)
- [Navigation](#navigation)

## Overview

The AI ecosystem is rapidly evolving with distinct categories of AI systems designed to augment human capabilities in different ways. Understanding these distinctions is fundamental to choosing the right tool for your workflow and maximizing productivity gains.

This section explores the landscape of AI-powered development tools, from simple chat interfaces to sophisticated agent-based systems. You'll learn when to use each type, understand their strengths and limitations, and gain clarity on terminology that often gets conflated in everyday conversations.

By mastering the ecosystem fundamentals, you'll develop an intuitive understanding of which AI approach fits different scenarios—whether you need quick answers, collaborative coding assistance, or autonomous task execution.

## AI Assistants

### What are AI Assistants

AI Assistants are conversational AI systems that interact with you through natural language dialogue. Think of them as knowledgeable colleagues you can chat with—you ask questions, they provide answers, explanations, or suggestions.

The key characteristic of assistants is their **request-response pattern**: you make a request, they respond, then wait for your next instruction. They don't act on their own; they need you to guide the conversation and decide what to do with their suggestions.

Unlike autonomous AI agents (which we'll cover next), assistants keep **humans in the loop** at every step. They augment your decision-making by providing information, generating ideas, or explaining complex concepts—but you remain in control of what actually happens.

Think of it this way: An assistant is like having a smart intern who can answer questions and draft responses, but always waits for your approval before taking action.

### Key Characteristics

**Conversational Interface**  
You interact using natural language—no need to learn special commands or syntax. Just type or speak what you need.

**Context Awareness Within Sessions**  
Assistants remember earlier parts of your conversation, so you can refer back to previous topics without repeating yourself. However, this memory is typically limited to the current chat session.

**Ability to Explain Reasoning**  
Good assistants can explain *why* they suggested something or *how* they arrived at an answer, helping you learn and build trust in their responses.

**Adaptability**  
They adjust their responses based on your feedback, tone, and preferences within a conversation.

**Key Limitations:**
- **No Task Persistence:** Once the chat ends, the assistant doesn't continue working on your behalf
- **Requires Explicit Instructions:** They won't proactively suggest next steps unless you ask
- **Limited Autonomy:** They can't take actions outside the conversation (like editing files or running code) without specific tool integration

### When to Use AI Assistants

**AI Assistants Excel At:**

✅ **Brainstorming Ideas**  
When you need creative input or want to explore different approaches to a problem.

✅ **Getting Quick Explanations**  
"What does this error message mean?" or "How does OAuth work?"—assistants are perfect for learning on the fly.

✅ **Exploratory Problem-Solving**  
When you're not sure of the best approach and want to discuss options before committing.

✅ **Learning New Concepts**  
Breaking down complex topics into understandable chunks with examples and analogies.

✅ **Getting Unstuck**  
When you're facing a specific issue and need a fresh perspective or debugging help.

**When to Choose Other AI Types:**

❌ **Repetitive Tasks** → Use Agents (they can automate workflows)  
❌ **Real-Time Code Suggestions** → Use Copilots (they integrate directly into your IDE)  
❌ **Multi-Step Autonomous Work** → Use Agents (they can execute plans without constant supervision)

### Popular Examples

**ChatGPT (OpenAI)**
- **Best For:** General-purpose assistance, code generation, creative writing
- **Strengths:** Wide knowledge base, strong at explaining concepts, good code generation
- **Notable Feature:** GPT-4 excels at complex reasoning and multi-step problem solving

**Claude (Anthropic)**
- **Best For:** Long documents analysis, nuanced conversations, coding assistance
- **Strengths:** Large context window (200K+ tokens), careful and thoughtful responses, good at following complex instructions
- **Notable Feature:** Excels at analyzing entire codebases or long technical documents

**Gemini (Google)**
- **Best For:** Multimodal tasks, integration with Google services, research
- **Strengths:** Can process images and text together, strong coding capabilities, access to real-time information
- **Notable Feature:** Deep integration with Google ecosystem (Docs, Sheets, etc.)

**GitHub Copilot Chat**
- **Best For:** Coding questions within your IDE, explaining code in context
- **Strengths:** Understands your codebase, suggests contextual solutions
- **Notable Feature:** Lives inside VS Code/Visual Studio—no context switching

**Quick Comparison:**
| Assistant | Context Size | Best Use Case | Key Differentiator |
|-----------|--------------|---------------|--------------------|
| ChatGPT | ~128K tokens | General purpose | Strong reasoning |
| Claude | ~200K tokens | Document analysis | Largest context |
| Gemini | ~100K tokens | Multimodal tasks | Google integration |
| Copilot Chat | Code-aware | In-IDE coding help | Repository context |

## AI Agents

### What are AI Agents

AI Agents are systems that can **autonomously work toward goals** with minimal human intervention. Unlike assistants that wait for your next instruction, agents take initiative, make decisions, and execute multi-step plans on their own.

The defining concept is **agency**—the ability to:
- **Make decisions** based on the current situation
- **Take actions** using tools and APIs (like editing files, running commands, searching the web)
- **Adapt** their approach based on outcomes and feedback
- **Own tasks** from start to completion

**Key Difference from Assistants:**

| AI Assistants | AI Agents |
|---------------|------------|
| "What should I do next?" | "I'll handle this task for you" |
| Reactive (waits for you) | Proactive (takes initiative) |
| Suggests actions | Executes actions |
| You own the task | Agent owns the task |

**Simple Analogy:**  
- **Assistant:** A consultant who gives advice but doesn't implement  
- **Agent:** A freelancer you hire to complete a project with minimal supervision

### Agent Capabilities

**Tool Use**  
Agents can interact with external systems: search the web, edit files, run code, query databases, call APIs. This is what enables them to take real actions in the world.

**Multi-Step Planning**  
Given a goal like "analyze this codebase and create a summary report," agents can:
1. Break it into steps (scan files, identify patterns, extract key info)
2. Execute each step in sequence
3. Adjust the plan if something doesn't work

**Memory and State Management**  
Agents maintain context across multiple interactions. They remember what they've tried, what worked, and what didn't—building a persistent understanding of the task.

**Error Recovery**  
When something fails (API error, unexpected data format), agents can:
- Recognize the problem
- Try alternative approaches
- Ask for clarification when truly stuck

**Goal-Oriented Behavior**  
Agents evaluate their progress toward the goal and adjust strategies accordingly. They don't just follow a script—they adapt based on outcomes.

**The Agent Spectrum:**

🔹 **Simple Agents:** Execute predefined workflows with minimal decision-making  
🔸 **Moderate Agents:** Handle branching logic, basic error handling, limited tool use  
🔶 **Complex Agents:** Multi-tool orchestration, sophisticated planning, advanced reasoning  
🔺 **Multi-Agent Systems:** Multiple specialized agents collaborating on complex tasks

### Agent Architecture Patterns

**ReAct (Reasoning + Acting)**  
The most common agent pattern:
1. **Reason:** Agent thinks about what to do next
2. **Act:** Agent takes an action (uses a tool, searches, etc.)
3. **Observe:** Agent sees the result
4. **Repeat:** Continue reasoning and acting until goal is achieved

Example:
```
Thought: "I need to find the user authentication logic"
Action: Search codebase for "auth" and "login"
Observation: Found 3 files: auth.ts, login.tsx, middleware.ts
Thought: "auth.ts likely contains the core logic"
Action: Read auth.ts
Observation: File contains JWT token generation
Thought: "Found it! Now I can answer the user's question"
```

**Tool-Calling Loops**  
Agents repeatedly call tools until the task is complete, with each tool call informed by previous results.

**Hierarchical Agents**  
A "manager" agent delegates sub-tasks to specialized "worker" agents:
- Manager: "Analyze this codebase"
- Worker 1: "I'll handle the backend files"
- Worker 2: "I'll analyze the frontend"
- Manager: Combines results into final report

**Multi-Agent Collaboration**  
Multiple agents with different specialties work together:
- Research Agent: Gathers information
- Coding Agent: Implements solutions
- Review Agent: Checks quality and suggests improvements

These patterns enable agents to tackle complex, multi-faceted problems that would overwhelm a single linear process.

### When to Use AI Agents

**✅ Agents Add Value For:**

**Repetitive Tasks with Clear Success Criteria**  
*Example:* "Run tests, fix any failures, commit when all pass"  
Agents can loop through fix attempts without needing your input each time.

**Workflows Needing Automation**  
*Example:* "Every time a PR is created, check code quality, run tests, and post a summary"  
Agents can handle the entire workflow autonomously.

**Tasks Requiring Multiple Tool Interactions**  
*Example:* "Research this error, check Stack Overflow, read docs, then suggest a fix"  
Agents can orchestrate multiple searches and syntheses without manual coordination.

**"Set It and Forget It" Scenarios**  
*Example:* "Generate a project scaffold, set up CI/CD, and initialize the database"  
Give the agent a goal and let it work while you focus elsewhere.

**Long-Running Research or Analysis**  
*Example:* "Analyze all API endpoints in this codebase and document their contracts"  
Agents can work through large tasks methodically.

**❌ When Agents Aren't Ideal:**

- **Creative exploration** where you want to guide each step (use Assistants)
- **Real-time collaboration** while you code (use Copilots)
- **High-stakes decisions** requiring human judgment at each step
- **Undefined goals** where the objective isn't clear yet

## AI Copilots

### What are AI Copilots

AI Copilots represent a **middle ground between assistants and agents**—they're proactive like agents but keep humans in the driver's seat like assistants.

The copilot paradigm is based on **real-time collaboration**: as you work, the copilot watches your context and offers relevant suggestions at exactly the right moment. You decide whether to accept, modify, or ignore each suggestion.

**The "Pilot + Co-Pilot" Model:**
- **You (Pilot):** Make all final decisions, maintain control, own the work
- **AI (Co-Pilot):** Monitors context, suggests next steps, fills in tedious details, catches mistakes

**Key Characteristics:**

🎯 **Contextually Aware:** Copilots understand what you're working on *right now*—your current file, cursor position, recent edits  
⚡ **Real-Time:** Suggestions appear as you type, not after you ask  
✋ **Non-Intrusive:** Suggestions are easy to accept or dismiss with a keystroke  
🔄 **Iterative:** They learn from your accept/reject patterns to improve suggestions  

**Difference from Assistants:**
- Assistants: You ask, they respond
- Copilots: They proactively suggest based on your current context

**Difference from Agents:**
- Agents: Autonomously complete tasks
- Copilots: Suggest actions but you make every decision

### Copilot Integration Patterns

**Inline Code Suggestions**  
As you type, copilots generate completions for the current line or entire functions:
```javascript
// You type:
function calculateTotal(
// Copilot suggests:
function calculateTotal(items: Item[]): number {
  return items.reduce((sum, item) => sum + item.price, 0);
}
```
You press Tab to accept, or keep typing to ignore.

**Context-Aware Autocompletions**  
Copilots analyze:
- Your current file and cursor position
- Related files in your project
- Variable names and types in scope
- Comments describing intent

They use this context to suggest relevant, project-specific code.

**Proactive Recommendations**  
Copilots spot patterns and suggest improvements:
- "This function is similar to one in utils.ts—want to reuse it?"
- "You're repeating this logic—consider extracting a helper"
- "Missing error handling here—want to add a try-catch?"

**Workflow Augmentation**  
Beyond code completion:
- Generate test cases based on your implementation
- Write commit messages based on your changes
- Explain complex code sections
- Refactor code according to requested patterns

**The Collaboration Model in Practice:**

| Phase | You Do | Copilot Does |
|-------|--------|-------------|
| Planning | Decide what to build | Suggests architecture patterns |
| Writing | Guide overall structure | Fills in implementation details |
| Refining | Review and adjust | Catches edge cases, suggests improvements |
| Testing | Define test scenarios | Generates test code |

You remain in control at every step, but the copilot handles tedious details and prevents common mistakes.

### GitHub Copilot Overview

GitHub Copilot was the first mainstream AI copilot for developers, launching in 2021 and fundamentally changing how many developers work.

**How It Works:**
- Integrates directly into popular IDEs (VS Code, Visual Studio, JetBrains, Neovim)
- Analyzes your code in real-time as you type
- Uses AI models trained on billions of lines of public code
- Provides context-aware suggestions based on your project

**Types of Assistance:**

**1. Inline Completions**  
The core feature—code suggestions as you type, from single lines to entire functions.

**2. Copilot Chat**  
Conversational interface within your IDE:
- Ask questions about your code
- Request refactoring or explanations
- Debug issues with AI assistance
- Generate documentation

**3. Slash Commands**  
Quick actions in chat:
- `/explain` - Explain selected code
- `/fix` - Suggest fixes for problems
- `/tests` - Generate tests for code
- `/doc` - Generate documentation

**Impact on Developer Workflows:**

📈 **Faster Development:** Developers report 30-50% faster completion of tasks  
🎯 **Better Focus:** Spend mental energy on design, not syntax  
📚 **Learning Aid:** See idiomatic patterns and best practices in context  
🐛 **Fewer Bugs:** Suggestions often include edge case handling  
✍️ **Less Boilerplate:** Automate repetitive patterns and structure  

**Real Developer Feedback:**
> "It's like having a senior developer pair programming with you, suggesting solutions as you go."

### Other Copilot Examples

**Code-Focused Copilots:**

**Cursor**
- **What It Is:** AI-first code editor (fork of VS Code)
- **Unique Feature:** "Cmd+K" to edit code with AI inline, multi-file editing awareness
- **Best For:** Developers wanting deeper AI integration than Copilot offers
- **Link:** [cursor.sh](https://cursor.sh)

**Codeium**
- **What It Is:** Free alternative to GitHub Copilot
- **Unique Feature:** Support for 70+ languages, unlimited completions on free tier
- **Best For:** Teams looking for cost-effective AI assistance
- **Link:** [codeium.com](https://codeium.com)

**Tabnine**
- **What It Is:** Privacy-focused AI code assistant
- **Unique Feature:** Can train on your private codebase, runs locally for security
- **Best For:** Enterprise teams with strict data privacy requirements
- **Link:** [tabnine.com](https://www.tabnine.com)

**Amazon CodeWhisperer**
- **What It Is:** AWS's code copilot
- **Unique Feature:** Security scanning, AWS API suggestions, free for individual use
- **Best For:** AWS-heavy development environments
- **Link:** [AWS CodeWhisperer](https://aws.amazon.com/codewhisperer)

**Specialized Copilots Beyond Code:**

**Microsoft Copilot (Office)**
- Assists with Word documents, Excel formulas, PowerPoint presentations
- Example: "Summarize this document" or "Create a chart from this data"

**Adobe Firefly**
- AI copilot for creative work (image generation, editing)
- Integrated into Photoshop, Illustrator

**Notion AI**
- Writing copilot for documentation and notes
- Helps draft, summarize, and organize content

**Gamma**
- Presentation copilot that generates slide decks from prompts

**The Trend:** Copilots are expanding into every domain where real-time, contextual AI assistance adds value—from code to design to data analysis to writing.

## Chat vs Repo AI

### Chat-Based AI Tools

Chat-based AI tools (like ChatGPT, Claude web interface, Gemini) interact through conversation windows where you paste code snippets and ask questions.

**The Interaction Model:**
1. You copy code from your project
2. Paste it into a chat window with your question
3. The AI analyzes the snippet and responds
4. You copy the suggested solution back to your project

**Strengths:**

✅ **Quick Answers**  
"What does this error mean?" → Instant explanation without leaving your browser

✅ **Explaining Concepts**  
"How does async/await work?" → Clear explanations with examples

✅ **Algorithm Help**  
"How do I implement binary search?" → Complete implementations with explanations

✅ **Debugging Isolated Issues**  
Paste a problematic function, get specific fix suggestions

✅ **Learning and Exploration**  
Great for understanding new concepts or languages

✅ **No Setup Required**  
Just open a browser—no IDE integration needed

**Limitations:**

❌ **No Codebase Context**  
The AI doesn't know about your project structure, other files, or dependencies

❌ **Difficult for Large Refactors**  
Can't see how changes in one file affect others across your project

❌ **Manual Copy-Paste**  
Context switching between browser and IDE interrupts flow

❌ **Limited Code Understanding**  
May suggest solutions incompatible with your project's architecture or patterns

❌ **No Real-Time Assistance**  
You have to stop coding, context switch, and ask

**Best Use Cases:**
- Learning new concepts
- Debugging specific error messages
- Getting algorithm implementations
- Understanding unfamiliar code patterns
- Quick consultations when stuck

### Repository-Aware AI Tools

Repository-aware AI tools (like GitHub Copilot with workspace context, Cursor, Sourcegraph Cody) have access to your **entire codebase**, enabling much more sophisticated assistance.

**How They Work:**

📂 **Indexing**  
The tool scans and indexes your entire repository, building an understanding of:
- File structure and organization
- Dependencies between modules
- Coding patterns and conventions
- API contracts and data models

🔍 **Cross-File Reasoning**  
When you ask a question or trigger a suggestion, the AI considers:
- Related files and functions
- How changes propagate through the system
- Existing patterns you follow in the project

🏗️ **Architectural Awareness**  
The tool understands your project's architecture:
- Where business logic lives vs UI code
- How data flows through the system
- What conventions you follow (naming, structure, etc.)

**Powerful Capabilities:**

✨ **Multi-File Changes**  
*Example:* "Rename this API endpoint everywhere it's used"  
→ Updates route definition, controller, tests, and client calls

✨ **Context-Specific Suggestions**  
*Example:* Suggesting code that follows your project's existing patterns, not generic examples

✨ **Architectural Questions**  
*Example:* "Where should I add validation for user input in this system?"  
→ Understands your layered architecture and suggests the right place

✨ **Impact Analysis**  
*Example:* "What would break if I change this function signature?"  
→ Identifies all call sites across the codebase

**The Context Advantage:**

Imagine asking "How do I add authentication here?":

| Chat AI (No Context) | Repo-Aware AI |
|----------------------|---------------|
| Suggests generic OAuth implementation | Sees you already use Passport.js in auth/ |
| Might suggest different patterns | Follows your existing middleware pattern |
| You adapt generic code to fit | Generates code that fits immediately |
| Doesn't know your user model | Uses your actual User type definition |

Repo-aware tools give suggestions that feel like they understand your project—because they do.

### When to Use Each

**Use Chat-Based AI When:**

🎓 **Learning New Concepts**  
*Example:* "Explain how React hooks work" → No project context needed

🐛 **Quick Debugging**  
*Example:* "Why am I getting TypeError: Cannot read property 'map' of undefined?" → The error message has enough context

🔧 **Isolated Problems**  
*Example:* "How do I sort this array of objects by date?" → Self-contained question

💡 **Algorithm Implementations**  
*Example:* "Show me how to implement Dijkstra's algorithm" → No codebase knowledge required

📚 **Researching Options**  
*Example:* "What are the pros and cons of SQL vs NoSQL?" → General advice, not project-specific

**Use Repository-Aware AI When:**

♻️ **Refactoring**  
*Example:* "Extract this repeated logic into a shared utility" → Needs to see all usage sites

✨ **Adding Features**  
*Example:* "Add pagination to the user list endpoint" → Needs to understand your API patterns

🏗️ **Architectural Changes**  
*Example:* "Move authentication logic to middleware" → Requires codebase-wide understanding

🔄 **Cross-File Changes**  
*Example:* "Rename User to Account throughout the project" → Must track references everywhere

📋 **Following Project Patterns**  
*Example:* "Add a new API endpoint" → Should follow your existing routing and controller patterns

🔍 **Codebase Navigation**  
*Example:* "Where is the email validation logic?" → Needs to search your repository

**Decision Framework:**

```
Does your question require understanding your specific codebase?
│
├─ NO → Chat AI is fine
│   └─ Examples: Learning, general algorithms, concept explanations
│
└─ YES → Use repo-aware AI
    └─ Examples: Feature implementation, refactoring, multi-file changes
```

**Pro Tip:** Many developers use both:
- Chat AI for learning and quick questions
- Repo-aware AI (Copilot/Cursor) for actual development work

### The Spectrum of Context

AI tools exist on a spectrum from **zero context** to **full codebase understanding**. Where a tool falls on this spectrum determines what it can help you with—and how accurately.

**The Context Spectrum:**

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  Zero Context          Partial Context      Full Context   │
│        ↓                      ↓                    ↓        │
│   [Chat AI]            [IDE Copilot]      [Repo-Aware AI]  │
│                                                             │
│    Fast ←──────────────────────────────────→ Accurate      │
│   Simple ←──────────────────────────────────→ Deep         │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Zero Context (Chat AI)**
- **Sees:** Only what you paste in the chat
- **Speed:** Instant—no indexing needed
- **Accuracy:** Generic answers, may not fit your project
- **Simplicity:** Easy—just ask a question
- **Example:** ChatGPT, Claude web interface

**Partial Context (Basic IDE Copilots)**
- **Sees:** Current file, maybe a few related files
- **Speed:** Real-time suggestions as you type
- **Accuracy:** Decent—understands immediate context
- **Simplicity:** Install and start coding
- **Example:** GitHub Copilot (basic mode)

**Full Context (Repository-Aware AI)**
- **Sees:** Entire codebase, dependencies, patterns
- **Speed:** May need brief indexing time
- **Accuracy:** High—suggestions fit your architecture
- **Complexity:** Requires setup and repository access
- **Example:** Cursor, Sourcegraph Cody, Copilot Workspace

**The Core Tradeoff:**

**📊 Speed & Simplicity vs Depth & Accuracy**

| Scenario | Choose Less Context | Choose More Context |
|----------|---------------------|---------------------|
| Learning a concept | ✓ Chat is enough | |
| Quick algorithm | ✓ Chat is fine | |
| Adding a new feature | | ✓ Need project patterns |
| Large refactor | | ✓ Need cross-file awareness |
| Emergency debug (no setup) | ✓ Chat for quick ideas | |
| Production development | | ✓ Use repo-aware tools |

**Why Context Matters—Example:**

You ask: "Add error handling to this API endpoint"

| Tool | Response |
|------|----------|
| **Chat AI** | Generic try-catch with console.log |
| **File-Context Copilot** | try-catch that matches your code style |
| **Repo-Aware AI** | Uses your existing ErrorHandler class, logs to your logging service, returns errors matching your API contract |

More context = more relevant, production-ready suggestions.

**Best Practice:**  
Start with the minimum context needed for your task. As tasks get more complex and project-specific, move toward tools with richer context awareness.

## Resources

### Anthropic's Introduction to Claude
- **Type:** Documentation
- **Duration/Length:** 15 min read
- **Level:** Beginner
- **Why this matters:** Official guide to one of the leading AI assistants, explains conversational AI fundamentals and best practices
- **Link:** [Anthropic Claude Documentation](https://docs.anthropic.com/claude/docs/intro-to-claude)

### GitHub Copilot Documentation
- **Type:** Official Documentation
- **Duration/Length:** 20 min read
- **Level:** Beginner to Intermediate
- **Why this matters:** Complete guide to the pioneering AI copilot—setup, features, and best practices for AI-assisted coding
- **Link:** [GitHub Copilot Docs](https://docs.github.com/en/copilot)

### "What Are AI Agents?" by LangChain
- **Type:** Article
- **Duration/Length:** 10 min read
- **Level:** Intermediate
- **Why this matters:** Clear explanation of agent concepts, ReAct pattern, and tool use from a leading agent framework
- **Link:** [LangChain Agent Docs](https://python.langchain.com/docs/modules/agents/)

### OpenAI's GPT Best Practices
- **Type:** Documentation
- **Duration/Length:** 25 min read
- **Level:** Beginner to Advanced
- **Why this matters:** Comprehensive guide to getting the most out of AI assistants through better prompting and task decomposition
- **Link:** [OpenAI Best Practices](https://platform.openai.com/docs/guides/prompt-engineering)

### "AI Copilots: The Evolution of Developer Tools" by Sourcegraph
- **Type:** Blog Article
- **Duration/Length:** 12 min read
- **Level:** Beginner
- **Why this matters:** Explains the copilot paradigm and how repository-aware AI changes development workflows
- **Link:** [Sourcegraph Blog](https://about.sourcegraph.com/blog)

### Cursor IDE Documentation
- **Type:** Documentation
- **Duration/Length:** 15 min read
- **Level:** Intermediate
- **Why this matters:** Demonstrates advanced copilot features and codebase-aware AI assistance patterns
- **Link:** [Cursor Documentation](https://cursor.sh/docs)

### "Understanding AI Agents" by Anthropic
- **Type:** Article
- **Duration/Length:** 8 min read
- **Level:** Beginner
- **Why this matters:** Clarifies the distinction between assistants and agents, when to use each, with practical examples
- **Link:** [Anthropic Blog](https://www.anthropic.com/research)

## Navigation

**[Next: Tools & Platforms →](../02-tools/README.md)**
