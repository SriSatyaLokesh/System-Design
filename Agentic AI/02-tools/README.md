**📍 Current Location:** [Pathway Home](../README.md) → 2. Tools

**📊 Progress:** Section 2 of 6 | ⏱️ Estimated time: 45 minutes

**Prerequisites:** [1. Ecosystem](../01-ecosystem/README.md) — Understanding AI tool categories

---

# 2. Tools & Platforms

## Table of Contents

- [Overview](#overview)
- [Cursor](#cursor)
- [GitHub Copilot](#github-copilot)
- [Claude Code](#claude-code)
- [Hands-On Exercises](#hands-on-exercises)
- [Prompt Engineering Fundamentals](#prompt-engineering-fundamentals)
- [Resources](#resources)
- [Navigation](#navigation)

## Overview

The landscape of AI development tools has exploded in recent years, each offering unique approaches to augmenting developer productivity. Choosing the right tool requires understanding their philosophies, strengths, and integration patterns.

This section provides practical, hands-on exploration of leading AI coding tools. Rather than surface-level feature comparisons, you'll understand the design philosophy behind each platform, when to reach for one versus another, and how to extract maximum value from each tool.

By mastering these platforms, you'll build a versatile AI toolkit that adapts to different project needs—from quick inline suggestions to deep architectural reasoning to agentic task automation.

## Cursor 🟡 Intermediate

### What Is It?

Cursor is an artificial intelligence-first code editor built on Visual Studio Code, designed to make AI assistance feel native to your development workflow. Unlike traditional editors with AI plugins, Cursor integrates AI capabilities at its core—understanding your entire codebase, enabling natural-language code editing, and providing context-aware suggestions across multiple files.

### Key Philosophy

**Seamless AI Integration:** Cursor treats AI as a first-class feature, not an afterthought. Every interaction is designed to minimize friction between your intent and the code changes you need.

**Codebase-Aware Intelligence:** Cursor automatically indexes your entire project, allowing AI to understand relationships between files, follow your coding patterns, and make contextually relevant suggestions.

**When to Choose Cursor:**
- You want AI deeply integrated into your editor (not just suggestions)
- You're working on projects requiring multi-file awareness
- You prefer conversational interaction ("refactor this component across all files")
- You want the familiarity of VS Code with enhanced AI capabilities

### Getting Started

**Prerequisites:**
- **Operating System:** macOS, Windows, or Linux
- **No Separate API Key Required:** Cursor provides built-in AI models (optional: add your own OpenAI API key for GPT-4 access)
- **Prior Knowledge:** Basic coding familiarity; if you've used VS Code, you're already ahead

**Installation:**

1. **Download Cursor**
   - Visit [cursor.sh](https://cursor.sh)
   - Click "Download" for your operating system
   - Install like any standard application

2. **Launch and Configure**
   - Open Cursor (it automatically imports VS Code settings if you have it installed)
   - You'll see the familiar VS Code interface with AI features enabled

3. **Verify It Works**
   - Open any coding project (or create a new file)
   - Press `Cmd+K` (macOS) or `Ctrl+K` (Windows/Linux)
   - Type a command like "add a hello world function"
   - If you see AI-generated code suggestions, you're ready!

**Configuration:**

**Basic Setup (works immediately):**
- Default: Uses Cursor's built-in AI models—no API key needed

**Optional Advanced Setup:**
- **Add OpenAI API Key** (for GPT-4 access):
  1. Go to Settings (Cmd+, or Ctrl+,)
  2. Search for "API Key"
  3. Enter your OpenAI API key
  4. Now you can use GPT-4 models for enhanced suggestions

- **Privacy Modes:**
  - **Cloud Mode:** Sends code to AI models (default, best performance)
  - **Local Mode:** Uses local models (more private, requires setup)
  - Configure in Settings → Privacy

### Typical Workflow

**Example Scenario:** You need to refactor a user authentication flow from JWT-based auth to OAuth, affecting multiple files.

**Step 1: Open Your Project**
```bash
# Open project folder in Cursor
cursor /path/to/your/project
```

**Step 2: Use AI Command Mode (Cmd+K / Ctrl+K)**
```
You: "Refactor authentication from JWT to OAuth 2.0"
```

**Expected Behavior:**
- Cursor analyzes your codebase
- Identifies files related to authentication
- Proposes changes across multiple files (auth middleware, login routes, user model)
- Shows a diff preview

**Step 3: Review and Apply Changes**
- Review suggested changes file-by-file
- Accept all, reject some, or modify inline
- Cursor maintains consistency across files

**Step 4: Iterate with AI Chat**
```
You: "Add refresh token support to this OAuth implementation"
```

**Cursor responds:**
- Updates the OAuth flow
- Adds refresh token endpoints
- Modifies token storage logic

**Step 5: Autocomplete as You Code**
- As you manually refine code, Cursor provides inline suggestions
- Press `Tab` to accept, keep typing to reject

**Key Features to Know:**

- **Cmd+K Command Mode:** Give high-level instructions; Cursor handles multi-file changes
  - _When to use_: Big refactors, feature additions, structural changes
  
- **Codebase Indexing:** Cursor automatically understands your project structure
  - _When to use_: Always active—enables context-aware suggestions

- **Inline Editing:** See changes in real-time with diff view
  - _When to use_: Reviewing AI suggestions before accepting

- **Composer Mode:** Coordinate changes across many files simultaneously
  - _When to use_: Large-scale refactoring, adding features that touch multiple modules

- **Privacy Modes:** Choose between cloud AI or local models
  - _When to use_: Sensitive codebases requiring data privacy

### Tips & Best Practices

- **Start Small to Learn**: Try Cmd+K with simple requests ("add error handling to this function") before attempting large refactors
- **Use Command Mode for Big Changes**: Cmd+K is your tool for multi-file operations; Tab autocomplete is for small edits
- **Review All Changes**: AI is powerful but not perfect—always review diffs before accepting
- **Check Privacy Settings**: If working with proprietary or sensitive code, configure privacy mode appropriately
- **Leverage Codebase Awareness**: Cursor already knows your project structure—you don't need to explain it

**Common Pitfall to Avoid:**
- ❌ **Don't blindly accept multi-file changes**: Always review, especially for security-sensitive code (authentication, data validation, API endpoints)

### Next Steps

- **Try the hands-on exercise:** [Exercise 3: Multi-Tool Workflow](#exercise-3-multi-tool-workflow---build-a-feature)
- **Official Documentation:** [https://cursor.sh/docs](https://cursor.sh/docs)
- **Explore settings** to customize AI models, keyboard shortcuts, and privacy options

## GitHub Copilot 🟢 Beginner

### What Is It?

GitHub Copilot is an AI-powered pair programmer that lives directly in your code editor, providing real-time code suggestions as you type. Unlike chat-based AI tools where you describe what you want and copy results, Copilot generates code inline—right where your cursor is—keeping you in flow state.

### Key Philosophy

**Stay in Flow:** Copilot minimizes context switching by suggesting code as you type, treating comments as natural-language instructions. No need to leave your editor or break your concentration.

**Context from Open Files:** Copilot analyzes your current file and other open files in your workspace to match your project's patterns, understand your coding style, and suggest contextually relevant code.

**When to Choose GitHub Copilot:**
- You want real-time inline code suggestions as you type
- You're implementing features where the design is clear
- You prefer minimal disruption to your coding flow
- You want AI assistance tightly integrated with your IDE (VS Code, JetBrains, etc.)

### Getting Started

**Prerequisites:**
- **GitHub Account:** Free or paid GitHub account
- **Supported IDE:** VS Code, JetBrains IDEs, Neovim, or Visual Studio
- **Prior Knowledge:** Basic coding familiarity

**Installation:**

1. **Install the Extension**
   - Open VS Code (or your supported IDE)
   - Go to Extensions marketplace
   - Search for "GitHub Copilot"
   - Click "Install"

2. **Sign In**
   - After installation, you'll be prompted to sign in with GitHub
   - Authorize the extension

3. **Verify It Works**
   - Create a new file (e.g., `test.js`)
   - Type a comment: `// function that adds two numbers`
   - Press Enter and wait 1-2 seconds
   - If you see a gray suggestion appear, Copilot is working!

**Configuration:**

**Default setup works immediately** after installation—no additional configuration required.

**Optional:**
- **Enable/Disable for Specific Languages:** Settings → Extensions → GitHub Copilot
- **Manage Suggestions:** Configure when suggestions appear (automatic vs manual trigger)

### Typical Workflow

**Example Scenario:** You need to write a REST API endpoint for user authentication with validation.

**Step 1: Write a Descriptive Comment**
```javascript
// POST /auth/login endpoint that validates email and password
// Returns JWT token on success, error message on failure
```

**Step 2: Accept Copilot's Suggestion**
- Copilot generates the function structure:
```javascript
async function loginUser(req, res) {
  const { email, password } = req.body;
  // validation and logic suggested...
}
```

**Step 3: Iterate with More Comments**
```javascript
// Validate email format
// Check if user exists in database
// Verify password with bcrypt
// Generate JWT token with 1-hour expiry
```

**Expected Behavior:**
- As you type each comment, Copilot suggests the implementation
- Press `Tab` to accept, keep typing to reject
- Copilot learns from your acceptances and refines future suggestions

**Step 4: Cycle Through Alternatives**
- If the first suggestion isn't what you want:
  - Press `Alt+]` (Windows) or `Option+]` (Mac) to see alternative suggestions
  - Keep cycling until you find the right one

**Step 5: Use Copilot Chat for Questions**
- Open Copilot Chat (`Ctrl+Shift+I` / `Cmd+Shift+I`)
- Ask: "How should I handle password reset in this authentication flow?"
- Get explanations and code examples

**Key Features to Know:**

- **Inline Completions:** Code suggestions appear as gray text while you type
  - _When to use_: Writing functions, implementing algorithms, boilerplate code

- **Comment-to-Code:** Write natural language comments; Copilot generates code
  - _When to use_: Describing what you want before implementing

- **Alternative Suggestions:** Cycle through multiple options with keyboard shortcuts
  - _When to use_: First suggestion doesn't match your needs

- **Copilot Chat:** Conversational AI assistant within your IDE
  - _When to use_: Asking questions, debugging, refactoring, generating tests

- **Context Awareness:** Uses currently open files to inform suggestions
  - _When to use_: Always active—keep related files open for better suggestions

### Tips & Best Practices

- **Write Descriptive Comments:** Be specific about what you want—clearer comments yield better suggestions
- **Keep Relevant Files Open:** Copilot uses open files for context; close unrelated tabs to improve accuracy
- **Review Suggestions Carefully:** Don't blindly accept code—check for security issues, edge cases, and correctness
- **Use Tab for Accept, Esc for Reject:** Learn the keyboard shortcuts for faster workflow
- **Iterate:** If the suggestion is close but not perfect, accept it and modify—Copilot learns from your edits

**Common Pitfall to Avoid:**
- ❌ **Accepting without Reading:** Always review generated code for security vulnerabilities (SQL injection, XSS), correctness, and fit with your project

### Next Steps

- **Try the hands-on exercise:** [Exercise 1: GitHub Copilot - Generate a Validated Function](#exercise-1-github-copilot---generate-a-validated-function)
- **Official Documentation:** [https://docs.github.com/en/copilot](https://docs.github.com/en/copilot)
- **Explore Copilot Chat** for more conversational interactions with AI

## Claude Code 🟡 Intermediate

### What Is It?

Claude Code refers to using Anthropic's Claude AI for coding tasks through various interfaces: the web interface at claude.ai, API integrations, or IDE extensions like Continue. Claude is known for its exceptional reasoning abilities, ultra-long context window (200K+ tokens), and thoughtful, security-conscious code suggestions.

### Key Philosophy

**Long-Context Reasoning:** Claude can process entire codebases at once (hundreds of files), understanding complex relationships and architectural patterns that span multiple modules.

**Conversational Refinement:** Unlike inline suggestions, Claude works through iterative conversation—you describe a problem, Claude proposes solutions, you refine, and iterate until you reach the optimal implementation.

**When to Choose Claude Code:**
- You need to understand or refactor large, complex codebases
- You're designing system architecture and want to explore tradeoffs
- You prefer conversational iteration over inline suggestions
- You want to upload entire files or documentation for context-aware advice

### Getting Started

**Prerequisites:**
- **Anthropic Account:** Create free account at [claude.ai](https://claude.ai) or get API access from [console.anthropic.com](https://console.anthropic.com)
- **For IDE Integration:** VS Code + Continue extension (optional but recommended)
- **Prior Knowledge:** Basic coding familiarity

**Installation:**

**Option 1: Web Interface (Easiest)**
1. Visit [claude.ai](https://claude.ai)
2. Sign up or log in
3. Start a new conversation
4. Upload code files or paste code directly

**Option 2: IDE Integration (Recommended)**
1. Install Continue extension in VS Code:
   - Open VS Code Extensions
   - Search "Continue"
   - Click Install
2. Configure with Claude:
   - Open Continue settings
   - Add Anthropic API key (get from console.anthropic.com)
   - Select Claude as your model
3. Verify It Works:
   - Open a project in VS Code
   - Use Continue panel (usually on left sidebar)
   - Ask "Explain what this project does"
   - If Claude responds with codebase-aware answer, you're ready!

**Configuration:**

**Web Interface:**
- No configuration needed—works immediately after login

**IDE Integration (Continue):**
- **Add API Key:** Continue → Settings → Add Anthropic API key
- **Select Model:** Choose claude-3-sonnet (balanced) or claude-3-opus (best reasoning)

### Typical Workflow

**Example Scenario:** You're analyzing a legacy authentication system and need to understand its security vulnerabilities before adding OAuth support.

**Step 1: Provide Context (Upload Files)**
```
In claude.ai or Continue panel:
- Upload: auth.middleware.js
- Upload: user.controller.js
- Upload: jwt.service.js
- Upload: database schema documentation
```

**Step 2: Ask High-Level Questions**
```
You: "Analyze this authentication flow. What security vulnerabilities 
exist, and how would you refactor it to support OAuth 2.0?"
```

**Expected Behavior:**
- Claude reads all uploaded files
- Identifies security issues (e.g., weak password hashing, no rate limiting)
- Proposes OAuth integration strategy
- Explains tradeoffs

**Step 3: Iterate Conversationally**
```
You: "Show me how to implement the refresh token flow without breaking existing JWT sessions."

Claude: [Provides implementation with migration strategy]

You: "What database schema changes are needed?"

Claude: [Details schema migrations with backward compatibility]
```

**Step 4: Request Specific Code**
```
You: "Generate the OAuth middleware with error handling and logging."

Claude: [Provides complete, production-ready code]
```

**Step 5: Copy to Your Editor**
- Review Claude's suggestions
- Copy code to your editor
- Test and refine

**Key Features to Know:**

- **200K+ Token Context Window:** Upload entire codebases (~150,000 words worth of code and documentation)
  - _When to use_: Understanding large projects, multi-file refactors

- **Multi-File Awareness:** Understands relationships between files
  - _When to use_: Architectural decisions, cross-module changes

- **Conversational Refinement:** Iterate naturally through chat
  - _When to use_: Exploring solutions, understanding tradeoffs

- **Artifacts:** Generates complete, formatted code files you can download
  - _When to use_: Getting full implementations of functions, classes, or configs

- **Security-Conscious:** Tends to suggest secure patterns and warn about vulnerabilities
  - _When to use_: Authentication, authorization, data validation

### Tips & Best Practices

- **Upload Full Context:** Don't summarize—Claude can handle hundreds of files at once; give it everything relevant
- **Ask "Why" Questions:** Claude excels at explaining reasoning ("Why use this pattern instead of that one?")
- **Iterate:** First response is a starting point—refine through conversation ("Now add error handling", "Show alternatives")
- **Request Alternatives:** Ask "Show me 3 different approaches to this problem" to explore options
- **Use for Architecture:** Claude is excellent for system design questions before you start coding

**Common Pitfall to Avoid:**
- ❌ **Treating It Like Inline Suggestions:** Claude is for thoughtful consultation, not real-time autocomplete—use for design decisions, not typing assistance

### Official Learning Resources

**Skillshare Course:**
- **Search for "Claude AI" on [Skillshare.com](https://skillshare.com)**
  - Video courses covering Claude workflows and best practices
  - Recommended **after** completing Exercise 2 (Prompt Engineering Practice)
  - Cost: ~$15/month (free trial available)
  - Direct link: Visit skillshare.com and search "Claude AI" or "Anthropic"

**Free Alternatives:**
- **Anthropic Documentation:** [docs.anthropic.com](https://docs.anthropic.com)
- **Claude Web Tutorial:** [claude.ai/docs](https://claude.ai/docs)
- **YouTube:** Search "Claude AI for developers"
- **Anthropic Prompt Engineering Guide:** [Prompt engineering](https://docs.anthropic.com/claude/docs/prompt-engineering)

### Next Steps

- **Try the hands-on exercise:** [Exercise 2: Claude Code - Refactor for Readability](#exercise-2-claude-code-or-chat-ai---refactor-for-readability)
- **Official Documentation:** [https://docs.anthropic.com](https://docs.anthropic.com)
- **Explore Skillshare course** for video-based learning (search "Claude AI" on Skillshare)


- Careful about suggesting secure coding practices
- Thorough in explaining tradeoffs and potential issues

**Extended Context Window**  
Claude can handle **200K+ tokens** (roughly 150,000 words or 500+ pages):
- Paste entire files or multiple files at once
- Share architectural documents alongside code
- Maintain coherent conversations across large codebases
- No need to break up your question into tiny chunks

**Complex Multi-Step Reasoning**  
Claude excels at problems requiring deep thinking:
- Architectural design decisions
- Debugging subtle, multi-file issues
- Refactoring large systems
- Explaining complex legacy code

**Typical Usage Pattern:**

1. **Upload Context:** Share relevant files, docs, or entire modules
2. **Ask Complex Questions:** "How would you refactor this to support multi-tenancy?"
3. **Iterate:** Have a back-and-forth discussion about tradeoffs
4. **Get Implementation:** Request specific code changes
5. **Copy to Your Editor:** Manually apply Claude's suggestions

**Claude vs Copilot:**

| Aspect | GitHub Copilot | Claude |
|--------|----------------|--------|
| Integration | Lives in your IDE | Web-based or API |
| Use Case | Real-time coding assistance | Deep problem-solving |
| Context | Current project | Anything you paste (huge) |
| Workflow | Inline as you type | Separate consultation |
| Best For | Implementation speed | Architectural thinking |

### Code-Specific Strengths

**1. Parsing Complex Requirements**

Claude excels at understanding ambiguous or high-level requirements and breaking them down:

**Example:**
```
You: "We need a payment system that handles multiple currencies, 
      supports retries, and logs everything for compliance."

Claude: "I'll break this down into components:

1. Payment Gateway Interface
   - Abstract interface for multiple providers (Stripe, PayPal)
   - Currency conversion service with exchange rate caching

2. Retry Logic
   - Exponential backoff for transient failures
   - Circuit breaker for provider outages
   - Dead letter queue for manual review

3. Compliance Logging
   - Immutable audit log (append-only)
   - PCI-DSS compliant data masking
   - Tamper-proof timestamps

Let's start with the payment gateway interface. Here's the design..."
```

**2. Explaining Intricate Code**

Paste legacy or complex code, and Claude provides clear explanations:

```javascript
// You paste this cryptic code:
const f = (a) => a.reduce((b, c) => ({...b, [c.id]: c}), {});

// Claude explains:
"This function transforms an array into an object for O(1) lookups:

Input:  [{id: 1, name: 'Alice'}, {id: 2, name: 'Bob'}]
Output: {1: {id: 1, name: 'Alice'}, 2: {id: 2, name: 'Bob'}}

It uses:
- reduce: Accumulates an object
- Spread operator: Preserves previous entries
- [c.id]: Uses id as key (computed property)

Better variable names would be:
const arrayToObjectById = (items) => 
  items.reduce((acc, item) => ({...acc, [item.id]: item}), {})"
```

**3. Multi-File Reasoning**

Claude can understand relationships across multiple files:

**Example:**
```
You: [Paste UserController.ts, UserService.ts, and UserRepository.ts]
     "Why isn't user deletion working?"

Claude: "I see the issue across your files:

1. UserController.deleteUser() calls userService.delete(id)
2. UserService.delete() calls userRepository.delete(id)
3. But UserRepository.delete() doesn't return a Promise
4. UserService expects async, but doesn't await

Controller (line 45): ✓ Correctly awaits
Service (line 23): ✗ Missing await on repository call
Repository (line 67): ✗ Should be async function

Here are the fixes for each file..."
```

**4. Architectural Suggestions**

Claude provides well-reasoned architectural guidance:

```
You: "Should I use microservices or monolith for this e-commerce app?"

Claude: "For your context (team of 3, MVP in 3 months, unclear scale):

Recommendation: Start with a Modular Monolith

Why NOT microservices now:
1. Team too small to manage multiple services
2. Premature optimization for unknown scale
3. Adds operational complexity (networking, deployment)
4. Harder to iterate quickly during MVP phase

Why modular monolith:
1. Single deployment = faster iteration
2. Clear module boundaries = easy to extract later
3. Shared database = simpler transactions
4. Can become microservices when you hit scale constraints

Architecture suggestion:
/modules/
  /auth/      ← Could become auth-service later
  /products/  ← Could become product-service later
  /orders/    ← Could become order-service later
  /payments/  ← Could become payment-service later

Each module has its own API, models, and business logic.

Want me to show the project structure?"
```

**5. Detailed Technical Writing**

Claude generates high-quality documentation:

- **API Documentation:** Clear endpoint descriptions, parameter details, example requests/responses
- **Architecture Docs:** System diagrams (in text/Mermaid), component interactions, design decisions
- **README Files:** Installation, usage, contribution guidelines
- **Code Comments:** Explains *why*, not just *what*

**Comparison to Other AI Assistants:**

| Capability | Claude | ChatGPT | Copilot |
|------------|--------|---------|----------|
| Huge context (100K+ tokens) | ✅ Best | ⚠️ Limited | ⚠️ Limited |
| Architectural reasoning | ✅ Excellent | ✅ Good | ⚠️ Basic |
| Multi-file analysis | ✅ Excellent | ⚠️ Manual paste | ✅ Native (IDE) |
| Explaining complex code | ✅ Very clear | ✅ Good | ✅ Good |
| Real-time coding | ❌ No | ❌ No | ✅ Only this |
| Deep problem-solving | ✅ Best | ✅ Good | ⚠️ Chat mode |
| Mathematical/algorithmic | ✅ Excellent | ✅ Very good | ⚠️ Basic |

**When to Reach for Claude:**
- Designing system architecture
- Understanding large, unfamiliar codebases
- Debugging issues spanning multiple files
- Writing comprehensive technical documentation
- Analyzing complex algorithms or performance issues

### Working with Large Contexts

Claude's 200K+ token context window is a **game-changer** for coding tasks. Here's how to leverage it effectively.

**What 200K Tokens Means:**

- ~150,000 words
- ~500 pages of text
- Multiple large files simultaneously
- Entire small-to-medium codebases
- Technical docs + code + conversation history

**Strategy 1: Provide Full File Contents**

No more summarizing or excerpt extraction:

```
You can paste:

============ UserService.ts (500 lines) ============
[Full file content]

============ UserRepository.ts (300 lines) ============
[Full file content]

============ User.types.ts (150 lines) ============  
[Full file content]

"Claude, refactor UserService to use dependency injection
while maintaining all existing functionality."
```

Claude sees everything and can:
- Understand all dependencies
- Maintain consistency across files
- Spot issues you didn't mention
- Ensure nothing breaks

**Strategy 2: Share Architectural Documents**

Give Claude the full context of your system:

```
============ ARCHITECTURE.md ============
[Your full architecture documentation]

============ DATABASE_SCHEMA.md ============
[All tables and relationships]

============ TechService.ts ============
[The file you want to modify]

"Add caching to TechService following our
architecture patterns and database schema."
```

Claude will:
- Follow your established patterns
- Respect your architecture decisions
- Use the correct database schema
- Suggest improvements where appropriate

**Strategy 3: Upload Multiple Related Files**

When debugging or refactoring, provide the complete picture:

**Example: Debugging a Complex Issue**

```
"I'm getting intermittent authentication failures."

[Paste all related files:]
- auth.middleware.ts (main auth logic)
- jwt.service.ts (token generation/validation)
- user.repository.ts (user lookups)
- auth.config.ts (configuration)
- auth.test.ts (tests that pass)
- server.logs (actual error logs)

Claude can now:
1. See the complete auth flow
2. Spot race conditions between files
3. Identify configuration issues
4. Cross-reference logs with code
5. Provide precise fixes
```

**Strategy 4: Maintain Context Across Iterations**

You don't lose context in a single conversation:

```
First message: [Paste entire codebase structure]

You: "Explain the authentication flow"
Claude: [Explains based on full codebase]

You: "Now how would we add OAuth?"
Claude: [Suggests changes, remembering the full structure]

You: "Show me the database migrations needed"
Claude: [Provides migrations, still maintaining full context]
```

No need to re-paste files—Claude remembers the entire conversation.

**Strategy 5: Include Error Messages and Logs**

Paste comprehensive debugging information:

```
============ CODE ============
[The problematic function]

============ ERROR LOGS ============
[Full stack trace, not just first line]

============ RELATED CODE ============
[Files mentioned in stack trace]

============ ENVIRONMENT ============
Node v18.12.0
TypeScript 5.0.0
Express 4.18.0

"Help me debug this error"
```

Claude sees everything and can trace the issue accurately.

**Best Practices for Large Contexts:**

✅ **DO:**
- Use clear section dividers: `============ filename.ts ============`
- Include file paths: `// src/services/user.service.ts`
- Paste complete functions/files, not fragments
- Add context about what you're trying to achieve
- Include relevant comments from your code

❌ **DON'T:**
- Paste unformatted wall of text
- Include irrelevant files (stay focused)
- Forget to mention what you're asking about
- Omit important config or environment details

**Pro Tips:**

**1. Use Artifacts for Large Responses**

When Claude generates long code, it creates an "Artifact" (separate pane) so you can:
- View code without it cluttering the chat
- Copy the entire output easily
- Compare multiple versions

**2. Create a "Context Document"**

For ongoing projects, maintain a master context document:

```markdown
# Project Context for Claude

## Tech Stack
[Full tech stack details]

## Architecture Overview
[System design]

## Key Files and Their Roles
[Brief description of major files]

## Coding Conventions
[Your team's standards]

## Database Schema
[Full schema or link]
```

Paste this at the start of sessions → Instant full context.

**3. Iterative Refinement**

Use the persistent context to iterate:

```
1. Share full context
2. Get initial solution
3. "What if we also need to handle X?" ← Claude still has context
4. "How would this affect performance?" ← Still remembers everything
5. "Show me the tests" ← Complete picture maintained
```

**Example: Real Workflow**

```
Session Start:
[Paste 10 files, 3000 lines total]
[Paste architecture diagram]
[Paste API documentation]

You: "Refactor the user module to support multi-tenancy"

Claude: [Analyzes all files, suggests comprehensive changes]

You: "How does this affect the billing module?" 
      ← Doesn't need you to paste billing module again

Claude: [References billing code from original paste, shows impacts]

You: "Show me migration path from current to new structure"

Claude: [Provides step-by-step migration, maintaining full context]
```

**The Bottom Line:**

With Claude's large context, **don't hold back**. The more complete information you provide, the better and more accurate Claude's responses will be. Think of it as giving Claude a full download of your project's mental model.

### Integration Patterns

**1. Browser-Based Access (Claude.ai)**

**How:** Visit [claude.ai](https://claude.ai) and chat directly

**Best For:**
- Quick questions and consultations
- Analyzing large documents or codebases
- Architectural planning sessions
- Deep problem-solving

**Workflow:**
```
1. Copy files from your editor
2. Paste into Claude web interface
3. Have detailed conversation
4. Copy solutions back to your editor
```

**Pros:**  
✅ No setup required  
✅ Access from any device  
✅ Easy to share conversations  
✅ Full context window available  

**Cons:**  
❌ Manual copy-paste workflow  
❌ Context switching between browser and IDE  

**2. API Integration (Claude API)**

**How:** Use Anthropic's API to build custom tools

**Best For:**
- Custom automation scripts
- Internal tools for your team
- CI/CD integration
- Bulk processing tasks

**Example: Code Review Bot**
```python
import anthropic

client = anthropic.Anthropic(api_key="your-key")

def review_code(code):
    message = client.messages.create(
        model="claude-3-5-sonnet-20241022",
        max_tokens=4096,
        messages=[{
            "role": "user",
            "content": f"Review this code for bugs and improvements:\n\n{code}"
        }]
    )
    return message.content[0].text

# Use in your workflow
with open('new_feature.py', 'r') as f:
    code = f.read()
    feedback = review_code(code)
    print(feedback)
```

**Use Cases:**
- Automated code review in PRs
- Documentation generation
- Test case generation
- Code quality analysis

**3. IDE Extensions**

**Available Options:**

**VS Code:**
- [Claude Dev](https://marketplace.visualstudio.com/items?itemName=saoudrizwan.claude-dev) - Brings Claude into VS Code
- [Cline](https://github.com/cline/cline) - Autonomous coding agent powered by Claude

**How It Works:**
- Chat with Claude inside VS Code
- Reference files with `@filename`
- Claude can read your workspace
- Insert suggestions directly into files

**Example Workflow:**
```
In VS Code:

1. Open Claude extension
2. Type: "@UserService.ts refactor to use dependency injection"
3. Claude analyzes the file and suggests changes
4. Click "Apply" to insert changes
5. Review and commit
```

**4. Combining Tools for Complementary Strengths**

The most effective developers use multiple tools strategically:

**Pattern: "Plan with Claude, Execute with Copilot"**

```
Step 1: Planning (Claude)
  "I need to add user authentication with JWT tokens"
  
  Claude provides:
  - Architecture design
  - File structure
  - Detailed implementation plan
  - Security considerations

Step 2: Implementation (Copilot)
  Start coding in VS Code with Copilot
  - Copilot autocompletes based on Claude's plan
  - Fast implementation of designed structure

Step 3: Review (Claude)
  Paste implementation back to Claude
  - Code review
  - Security audit
  - Performance analysis
```

**Pattern: "Debug with Claude, Fix with Copilot"**

```
Step 1: Debugging (Claude)
  [Paste error logs + related files]
  Claude identifies: "Race condition in async initialization"

Step 2: Fix (Copilot)
  Add comment: // Fix race condition with await initialization
  Copilot suggests the actual code fix

Step 3: Verify (Claude)
  Show Claude the fix
  Claude confirms: "✓ This resolves the race condition"
```

**Pattern: "Learn with Claude, Apply with Copilot"**

```
Step 1: Understanding (Claude)
  "Explain how Redis caching works with Node.js"
  
  Claude provides:
  - Detailed explanation
  - Best practices
  - Example patterns

Step 2: Application (Copilot)
  Start implementing in your project
  Copilot autocompletes Redis patterns you just learned
```

**Recommended Tool Combination:**

| Task | Primary Tool | Secondary Tool |
|------|--------------|----------------|
| Real-time coding | Copilot | - |
| Architecture design | Claude | - |
| Debugging complex issues | Claude | Copilot (for fixes) |
| Learning new concepts | Claude | Copilot (for practice) |
| Code review | Claude | - |
| Refactoring | Claude (plan) | Copilot (execute) |
| Documentation | Claude | - |
| Quick functions | Copilot | - |

**5. Team Integration Patterns**

**Pattern: Shared Claude Conversations**

```
1. Senior dev designs architecture with Claude
2. Shares Claude conversation link with team
3. Team references decisions in implementation
4. Maintains consistency across the team
```

**Pattern: Claude as Documentation Assistant**

```
1. Paste codebase to Claude
2. Generate comprehensive docs
3. Store in team wiki
4. Update when code changes
```

**Pattern: CI/CD Integration**

```yaml
# .github/workflows/claude-review.yml
name: Claude Code Review
on: [pull_request]

jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run Claude Review
        run: |
          python scripts/claude_review.py \
            --files $(git diff --name-only HEAD^ HEAD)
      - name: Post Review
        uses: actions/github-script@v6
        with:
          script: |
            github.rest.issues.createComment({
              issue_number: context.issue.number,
              body: readFileSync('review.md', 'utf8')
            })
```

**The Bottom Line:**

Claude + Copilot is a powerful combination:
- **Claude:** Your thoughtful architect and consultant
- **Copilot:** Your fast typing assistant

Use Claude for *thinking*, Copilot for *doing*.

## Hands-On Exercises

### About These Exercises

These exercises help you practice with each tool and apply prompt engineering principles. Each exercise takes 10-20 minutes and has clear success criteria so you know when you're done.

---

### Exercise 1: GitHub Copilot - Generate a Validated Function

**Scenario:** You need to create a user registration function that validates input data.

**Goal:** Use GitHub Copilot to generate a TypeScript function with validation logic and type safety.

**Prerequisites:**
- GitHub Copilot installed and active
- VS Code (or supported IDE) open
- TypeScript project (or create simple .ts file)

**Steps:**

1. **Create a new file:** `user-registration.ts`

2. **Write a descriptive comment:**
   ```typescript
   // Function that validates and registers a new user
   // - Email must be valid format
   // - Password must be at least 8 characters
   // - Username must be 3-20 characters
   // - Returns success message or error details
   ```

3. **Start function signature:**
   ```typescript
   function registerUser(email: string, password: string, username: string):
   ```

4. **Accept Copilot suggestions** and iterate:
   - Review the generated function
   - If validation is incomplete, add comments for missing checks
   - Accept or modify suggestions

5. **Test the function** with sample inputs

**Success Criteria:**
✅ Function has TypeScript types  
✅ All three validation rules implemented  
✅ Returns clear success/error messages  
✅ Code is readable and commented  

**Reflection Questions:**
- How did the comment quality affect suggestions?
- Did you need to iterate? What did you refine?
- How would you improve the prompt for better initial results?

---

### Exercise 2: Claude Code (or Chat AI) - Refactor for Readability

**Scenario:** You have a complex function that works but is hard to read. Use AI to refactor it.

**Goal:** Practice iterative prompting to improve code quality.

**Sample Code to Refactor:**
```javascript
function p(d){let r=[];for(let i=0;i<d.length;i++){if(d[i].a&&d[i].s>100){r.push({n:d[i].n,v:d[i].p*d[i].q})}}return r.sort((a,b)=>b.v-a.v)}
```

**Steps:**

1. **Initial prompt (Level 1 - Basic):**
   "Refactor this function for readability"
   [Paste code]

2. **Refined prompt (Level 2 - With Context):**
   "Refactor this JavaScript function for readability:
   - Use descriptive variable names
   - Add comments explaining logic
   - Separate concerns (filter, map, sort)
   - Use modern ES6+ features"
   [Paste code]

3. **Iteration (Level 3):**
   After receiving refactored code, ask:
   "Can you explain what this function does and suggest performance improvements?"

4. **Final iteration (Level 4):**
   "Add TypeScript types to this function and unit test examples"

**Success Criteria:**
✅ Function is readable with clear variable names  
✅ Logic is separated and commented  
✅ You understand what the function does  
✅ (Optional) TypeScript types and tests added  

**Reflection Questions:**
- How did prompt specificity change the outcome?
- What did you learn from the iteration process?
- Which prompt level gave you the most value?

---

### Exercise 3: Multi-Tool Workflow - Build a Feature

**Scenario:** Build a complete feature using multiple AI tools strategically.

**Goal:** Understand when to use Chat AI vs Copilot/Code AI.

**Task:** Create a "Task List" component with add/delete functionality

**Workflow:**

1. **Planning (Chat AI - ChatGPT/Claude):**
   Prompt: "I'm building a task list component in React. What state management approach would you recommend for add/delete functionality? Keep it simple for a learning project."
   - Get conceptual guidance
   - Understand patterns

2. **Implementation (GitHub Copilot or Cursor):**
   - Create `TaskList.tsx` file
   - Use Copilot to generate component structure
   - Write comments describing needed functions
   - Accept/iterate on suggestions

3. **Debugging (Context-dependent):**
   - If single-function issue: Either tool works
   - If multi-component issue: Prefer Repo AI (Cursor/Claude Code)

4. **Learning (Chat AI):**
   Prompt: "Explain why we use useState for local component state vs useContext for global state"

**Success Criteria:**
✅ Task list component works (can add/delete tasks)  
✅ You used Chat AI for concepts, Repo AI for implementation  
✅ You can explain when you switched tools and why  
✅ Component is functional and readable  

**Reflection Questions:**
- When did you switch between tools? What triggered the switch?
- Which tool felt more natural for which type of work?
- How would you apply this workflow to your next project?

---

### Exercise 4: Prompt Engineering Practice

**Goal:** Apply prompt engineering levels to real tasks.

**Task:** For each scenario, write prompts at different levels and compare results.

**Scenarios:**

1. **Scenario A:** "Explain how promises work in JavaScript"
   - Write a Level 1 prompt (basic request)
   - Write a Level 2 prompt (with context: "I understand callbacks but struggle with promise chaining")
   - Try both, note differences

2. **Scenario B:** "Create a form validation function"
   - Write a vague prompt (anti-pattern)
   - Write a specific prompt (Level 4 strategic)
   - Compare outputs

3. **Scenario C:** Pick your own coding challenge
   - Start vague, then iterate 3 times
   - Document your iteration process
   - Reflect on how outcomes improved

**Success Criteria:**
✅ Completed at least 2 scenarios  
✅ Documented prompts and responses  
✅ Identified which prompt techniques worked best  
✅ Can articulate why specific prompts produced better results  

**Reflection:**
- Which skill level felt most useful?
- What prompt patterns will you use regularly?
- What anti-patterns did you catch yourself doing?

---

### Next Steps After Exercises

Once you've completed these exercises:
- ✅ Move to Section 3: GSD Framework for structured AI workflows
- ✅ Explore tool-specific documentation
- ✅ Apply these skills to your own projects
- ✅ Experiment with advanced features

**Remember:** Tool proficiency comes with practice. Revisit these exercises as you learn.

## Prompt Engineering Fundamentals 🟢 Beginner

### What is Prompt Engineering

Prompt engineering is the skill of crafting effective instructions for AI systems to get the results you want. Think of it as learning the "language" that helps AI understand exactly what you need.

**Why It Matters:**

AI tools are incredibly powerful, but they can only work with the information and instructions you provide. The difference between mediocre and excellent results often comes down to how you phrase your request.

**The Core Idea:**

```
Vague Prompt → Vague Results
Clear Prompt → Clear Results
Expert Prompt → Expert Results
```

**Example of Impact:**

❌ **Poor Prompt:**
```
"Make a login function"
```
Result: Generic, may not match your needs, missing error handling

✅ **Good Prompt:**
```
"Create a login function in TypeScript that:
- Accepts email and password
- Validates format before checking database
- Returns JWT token on success
- Returns specific error messages for each failure case
- Uses bcrypt for password comparison
- Includes JSDoc comments"
```
Result: Specific, production-ready code that matches your requirements

**Prompt Engineering is NOT:**
- Magic words or tricks
- Manipulating AI to do things it shouldn't
- A replacement for project knowledge

**Prompt Engineering IS:**
- Clear communication of your requirements
- Providing appropriate context
- Structuring requests for optimal AI understanding
- Iterating based on results

**Universal Truth:**

> "The AI is only as good as the instructions you give it."  
> Better prompts → Better results

### Core Principles

These principles work across all AI tools—ChatGPT, Claude, Copilot, and beyond.

**1. Be Clear and Specific**

❌ **Vague:** "Fix the bug"  
✅ **Specific:** "The login function throws 'undefined' error when email field is empty. Add validation to check if email exists before calling authenticateUser()."

**Why it works:** AI can't read your mind. Specificity eliminates ambiguity.

**2. Provide Context**

AI needs to understand your situation:

❌ **No Context:**
```
"How do I handle errors?"
```

✅ **With Context:**
```
"I'm building a REST API with Express and TypeScript. 
How should I handle errors consistently across all endpoints?
I want client-friendly error messages and detailed server logs."
```

**Context to Include:**
- What you're building
- Your tech stack
- Constraints or requirements
- What you've already tried

**3. Break Down Complex Requests**

Don't ask for everything at once:

❌ **Too Broad:**
```
"Build a complete e-commerce site"
```

✅ **Broken Down:**
```
1. "Design the database schema for products, users, and orders"
2. "Create user authentication with JWT"
3. "Build product catalog API endpoints"
4. "Implement shopping cart functionality"
5. "Add payment processing integration"
```

**4. Show Examples**

When you have a specific style or pattern in mind:

```
"I want a function like this:

function getUserById(id: string): Promise<User> {
  // implementation
}

Create similar functions for:
- getUserByEmail
- getUsersByRole
- updateUser"
```

AI will match the pattern you showed.

**5. Iterate Based on Results**

Treat prompt engineering as a conversation:

```
Prompt 1: "Create a user validation function"
Result: [Generic validation]

Prompt 2: "Add email format validation using regex"
Result: [Better, but regex might be wrong]

Prompt 3: "Use this regex pattern: /^[^@]+@[^@]+\.[^@]+$/"
Result: [Exactly what you need]
```

Each iteration gets closer to your goal.

**6. Specify What You DON'T Want**

Sometimes it's easier to exclude than include:

```
"Create a React component for a user profile.

DO include:
- Avatar with fallback
- Name and email display
- Edit button

DO NOT include:
- Complex state management
- API calls (parent handles this)
- Inline styles (use CSS classes)"
```

**Quick Reference:**

| Principle | Bad Example | Good Example |
|-----------|-------------|---------------|
| **Clarity** | "Make it better" | "Refactor to use async/await instead of callbacks" |
| **Context** | "Debug this" | "This MongoDB query times out on large datasets (10K+ records)" |
| **Decomposition** | "Build the feature" | "Step 1: Create the data model" |
| **Examples** | "Similar to before" | [Paste the actual example] |
| **Iteration** | [Giving up] | "Now add error handling for network failures" |
| **Constraints** | [Assume AI knows] | "Don't use external libraries, vanilla JS only" |

### Task Decomposition

One of the most powerful prompt engineering skills is breaking down big, vague goals into concrete, actionable steps.

**The Problem with Big Requests:**

```
❌ "Build a web app for task management"
```

This is too broad. The AI must guess:
- What features do you want?
- What tech stack?
- What does "done" look like?
- Where to even start?

Result: Generic code that probably doesn't match your vision.

**The Solution: Decomposition**

Break it into a logical sequence of concrete tasks:

```
✅ Task-Oriented Approach:

1. "Design a database schema for task management with:
   - Tasks (id, title, description, status, due_date)
   - Users (id, email, name)
   - Task-user assignments"

2. "Create TypeScript interfaces matching the schema"

3. "Build a REST API endpoint: POST /tasks
   - Accepts task data
   - Validates required fields
   - Returns created task or error"

4. "Create a React component: TaskList
   - Displays tasks in a table
   - Shows status with color coding
   - Includes edit/delete buttons"

5. "Add task filtering by status (todo, in-progress, done)"
```

Each prompt is:
- **Specific:** Clear what to build
- **Testable:** You can verify it works
- **Incremental:** Builds on previous steps

**How to Decompose Any Task:**

**Step 1: Identify the Goal**
```
"I want [final outcome]"
Example: "I want users to be able to export their data as CSV"
```

**Step 2: Work Backwards**
```
What needs to exist for this to work?
- CSV export button (UI)
- API endpoint that generates CSV (Backend)
- Function to convert data to CSV format (Logic)
- Permission check (users can only export their own data) (Security)
```

**Step 3: Order Dependencies**
```
1. Permission check logic (bottom layer)
2. CSV conversion function (data layer)
3. API endpoint (service layer)
4. UI button (presentation layer)
```

**Step 4: Create Specific Prompts**
```
Prompt 1: "Create a function isAuthorizedToExport(userId, requestedUserId) 
           that returns true if the user can export the data"

Prompt 2: "Create a function convertToCSV(data: object[]) that 
           converts an array of objects to CSV format with headers"

Prompt 3: "Create a GET endpoint /api/export/csv that:
           - Checks user authorization
           - Fetches user data
           - Converts to CSV
           - Returns as downloadable file"

Prompt 4: "Create an ExportButton React component that:
           - Calls the /api/export/csv endpoint
           - Shows loading state during export
           - Triggers file download on success
           - Shows error message on failure"
```

**Practical Example: "Build Authentication"**

❌ **Too Vague:**
```
"Add authentication to my app"
```

✅ **Properly Decomposed:**

```bash
# Phase 1: Foundation
Task 1: "Create User table schema with email, password_hash, created_at"
Task 2: "Create TypeScript User interface and validation schema"

# Phase 2: Core Auth
Task 3: "Create POST /register endpoint that:
        - Validates email format
        - Checks if user exists
        - Hashes password with bcrypt
        - Creates user record
        - Returns sanitized user object (no password)"

Task 4: "Create POST /login endpoint that:
        - Finds user by email
        - Compares password hash
        - Generates JWT token with 24h expiry
        - Returns token and user data"

# Phase 3: Protection
Task 5: "Create authenticateToken middleware that:
        - Extracts JWT from Authorization header
        - Verifies token validity
        - Attaches user data to request
        - Returns 401 if invalid"

# Phase 4: Client Integration
Task 6: "Create React hook useAuth that:
        - Provides login/logout functions
        - Stores token in localStorage
        - Includes token in API requests
        - Handles token expiry"
```

**Benefits of Decomposition:**

✅ **Better AI Responses:** Specific tasks get specific, quality answers  
✅ **Easier Debugging:** When something breaks, you know exactly which piece  
✅ **Clear Progress:** You can see completion advancing  
✅ **Flexible:** Easy to adjust individual pieces  
✅ **Reusable:** Individual tasks can be referenced later  

**Red Flags (Signs Your Task Needs Decomposition):**

🚩 Your prompt has "and" more than 3 times  
🚩 You're using words like "complete", "full", "entire"  
🚩 The result would involve multiple files  
🚩 You can't clearly describe what "done" looks like  
🚩 The AI response is generic or incomplete  

**Rule of Thumb:**

> If you can't test the result in 5 minutes, your task is too big. Break it down further.

### Context Management

Providing the right context is the difference between AI giving generic answers versus solutions tailored to your specific situation.

**What is Context?**

Context is the background information AI needs to understand your question and provide relevant answers:

- Your tech stack
- Your project's architecture
- Constraints you're working within
- What you've already tried
- Relevant code or configuration

**How Much Context is Enough?**

**Too Little ❌**
```
"How do I connect to a database?"
```
Result: Generic answer that might not apply to your stack

**Too Much ❌**
```
"I'm using Node.js v18.12.0 on Windows 11 with 16GB RAM 
and an Intel i7 processor, VS Code 1.85.0, npm 9.6.7...

[Pastes entire 50-file codebase]

...and here's my complete git history...

How do I connect to a database?"
```
Result: AI gets lost in irrelevant details

**Just Right ✅**
```
"I'm building a Node.js API with Express and TypeScript.
I want to connect to PostgreSQL.
I'm using Prisma as the ORM.

How do I set up the database connection?"
```
Result: Specific, actionable answer for your exact stack

**What Context to Include:**

**1. Technology Stack**
```
Good: "React 18 with TypeScript and Tailwind CSS"
Bad: "Frontend framework"
```

**2. What You're Trying to Achieve**
```
Good: "I need to validate user input before submitting a form"
Bad: "Help with forms"
```

**3. Constraints or Requirements**
```
Good: "Must work without external libraries"
Good: "Needs to support IE11"
Good: "Must complete in under 100ms"
```

**4. Relevant Code**
```
"Here's my current implementation:

[Paste the specific function or component]

It's not working because [specific issue]."
```

**5. What You've Already Tried**
```
"I tried using setTimeout but it causes memory leaks.
I also tried requestAnimationFrame but the timing is inconsistent."
```

This prevents AI from suggesting solutions you've already ruled out.

**Context Structuring Techniques:**

**Template 1: Problem-Solving**
```
**Context:**
- Tech stack: [Your stack]
- What I'm building: [Feature/component description]

**Problem:**
[Specific issue you're facing]

**What I've tried:**
1. [Attempt 1] - [Why it didn't work]
2. [Attempt 2] - [Why it didn't work]

**Question:**
[Your specific question]
```

**Template 2: Feature Implementation**
```
**Project:**
[Brief description of overall project]

**Tech Stack:**
- Frontend: [Framework/libraries]
- Backend: [Framework/libraries]
- Database: [Database system]

**Current Architecture:**
[Relevant patterns or structure]

**New Feature:**
[What you want to build]

**Requirements:**
- [Requirement 1]
- [Requirement 2]

**Question:**
[What you need help with]
```

**Template 3: Code Review/Refactoring**
```
**Current Code:**
[Paste your code]

**What it does:**
[Explain the purpose]

**What I want to improve:**
[Specific improvements needed]

**Constraints:**
[Things that must stay the same]
```

**When to Reference External Docs:**

**Reference ✅:** When the documentation provides essential technical details
```
"Following the Stripe API docs for webhook verification:
[Link or key excerpt]

How do I implement this in Express with TypeScript?"
```

**Include Inline ✅:** When it's a quick configuration or small code snippet
```
"My config looks like this:
{
  apiVersion: 'v2',
  timeout: 5000
}

How do I add retry logic?"
```

**Managing Context in Long Conversations:**

**Problem:** AI context can get "diluted" in long conversations

**Solution: Restate Context Periodically**

```
[After 5-6 exchanges]

"To recap: I'm building a React component that displays user profiles.
We've added avatar loading and fallbacks.

Now I need to add the edit functionality..."
```

This helps AI maintain focus on what matters.

**Context for Different AI Tools:**

| Tool | Context Handling | Best Practice |
|------|------------------|----------------|
| **ChatGPT** | Conversational history | Restate key context every few messages |
| **Claude** | Large context window (200K) | Paste all relevant files at once |
| **Copilot** | Current file + open tabs | Keep related files open |
| **Copilot Chat** | Workspace awareness | Reference files with @filename |

**Context Management Checklist:**

Before asking a question, ensure you've included:

- [ ] What you're trying to accomplish
- [ ] Your tech stack (languages, frameworks, libraries)
- [ ] Relevant code or configuration
- [ ] Specific error messages (if applicable)
- [ ] Constraints or requirements
- [ ] What you've already tried (if applicable)
- [ ] Removed irrelevant details

**Pro Tips:**

**1. Use Code Blocks**
```
✅ Good:
"""javascript
function getUserData(id) {
  // code here
}
"""

❌ Bad:
I have a function getUserData that takes id...
```

**2. Highlight the Specific Issue**
```
"""typescript
function processPayment(amount: number) {
  if (amount < 0) {
    throw new Error('Invalid amount'); // ← THIS LINE fails in production
  }
  // ...
}
"""
```

**3. Separate Context from Question**
```
--- CONTEXT ---
[Background information]

--- QUESTION ---
[Your specific question]
```

Clear structure helps AI parse your request.

**The Golden Rule:**

> Provide enough context for someone unfamiliar with your project to understand the problem, but no more.

### Effective Code Prompts

Code generation requires specific prompting patterns to get production-quality results.

**Pattern 1: Specify Input/Output**

Always define what goes in and what comes out:

❌ **Vague:**
```
"Create a function to process user data"
```

✅ **Specific:**
```
"Create a TypeScript function:

Input: { email: string, name: string, age: number }
Output: { id: string, email: string, name: string, createdAt: Date }

Function should:
- Generate unique ID (UUID)
- Validate email format
- Ensure age >= 18
- Add createdAt timestamp
- Throw ValidationError if validation fails"
```

**Pattern 2: Describe Edge Cases**

Tell AI about the unusual scenarios:

```
"Create a function divideNumbers(a, b) that:

Normal case: Returns a / b

Edge cases:
- If b === 0, return null and log warning
- If either input is NaN, return null
- If either input is Infinity, return null
- Round result to 2 decimal places"
```

AI will generate robust code that handles these cases.

**Pattern 3: Request Tests**

Get code AND tests in one go:

```
"Create a function isPalindrome(str) that checks if a string 
is a palindrome (reads same forwards and backwards).

Also create Jest tests covering:
- Simple palindromes: 'racecar', 'noon'
- Case insensitivity: 'RaceCar'
- Spaces and punctuation: 'A man a plan a canal Panama'
- Edge cases: empty string, single character
- Non-palindromes: 'hello', 'world'"
```

**Pattern 4: Specify Code Style**

Guide the style you want:

```
"Create a user authentication function.

Code style:
- Use async/await (not .then())
- Prefer const over let
- Include TypeScript types
- Add JSDoc comments
- Use early returns for error cases
- Follow Airbnb naming conventions"
```

**Pattern 5: Show Example Structure**

Provide a skeleton:

```
"Create a function fetchUserPosts() following this structure:

async function fetchUserPosts(userId: string): Promise<Post[]> {
  // 1. Validate userId format
  // 2. Fetch from API with error handling
  // 3. Transform response to Post[] type
  // 4. Cache results
  // 5. Return posts
}

Implement each step with production-ready code."
```

**Pattern 6: Request Documentation**

Get well-documented code:

```
"Create a calculateShipping(items, destination) function.

Include:
- JSDoc comments explaining parameters and return value
- Inline comments for complex logic
- Example usage in the comment
- Any assumptions or limitations"
```

**Complete Example: Effective Code Prompt**

```
**Task:** Create a rate limiting middleware for Express.js

**Requirements:**
- Allow max 100 requests per hour per IP
- Use Redis for storing request counts
- Return 429 status when limit exceeded
- Include Retry-After header
- Reset counter after window expires

**Function Signature:**
"""typescript
function rateLimiter(
  options: { maxRequests: number; windowMs: number }
): RequestHandler
"""

**Behavior:**
- First request: Allow, set counter to 1
- Subsequent requests: Increment counter
- Counter > maxRequests: Return 429 with:
  - Error message: "Rate limit exceeded"
  - Retry-After header: seconds until reset
- After windowMs: Reset counter

**Edge Cases:**
- Handle Redis connection failures gracefully
- If Redis is down, allow request (fail open)
- Log rate limit violations

**Code Style:**
- TypeScript with strict types
- Use async/await
- Include error handling
- Add JSDoc comments

**Tests:**
Include Jest tests for:
- Normal operation (under limit)
- Hitting the limit
- Window reset
- Redis failure scenario
"""
```

This produces production-ready, well-tested code.

**Common Mistakes to Avoid:**

❌ **No Type Information**
```
"Create a function that processes data"
```
→ You'll get generic `any` types

❌ **Forgetting Error Handling**
```
"Create an API call function"
```
→ May not handle network errors, timeouts, etc.

❌ **Not Specifying Format**
```
"Format the date"
```
→ Could be any date format

✅ **Specific:**
```
"Format Date object as 'YYYY-MM-DD HH:mm:ss' in UTC"
```

**Quick Reference: Code Prompt Template**

```markdown
**Function:** [Name and brief description]

**Signature:**
[Expected function signature with types]

**Inputs:**
- param1: [type] - [description]
- param2: [type] - [description]

**Output:**
- [Return type] - [description]

**Behavior:**
- [Normal operation description]

**Edge Cases:**
- [Case 1] → [Expected behavior]
- [Case 2] → [Expected behavior]

**Error Handling:**
- [Error type] → [How to handle]

**Style Requirements:**
- [Language/framework]
- [Specific patterns to follow]

**Optional:**
- Tests: [What to test]
- Documentation: [What to document]
- Performance: [Any constraints]
```

**Pro Tip: Iterate on Generated Code**

Don't settle for the first result:

```
Prompt 1: [Initial request]
Result: [Basic implementation]

Prompt 2: "Add TypeScript strict types"
Result: [Better types]

Prompt 3: "Add input validation with helpful error messages"
Result: [Robust validation]

Prompt 4: "Optimize for arrays with 10,000+ items"
Result: [Performance improvements]
```

Each iteration refines the code toward production quality.

### Iteration Techniques

The first AI response rarely perfect. Master these iteration techniques to refine results quickly.

**Technique 1: Clarify Ambiguities**

When the result misses the mark, identify what was unclear:

```
[First Attempt]
You: "Create a search function"
AI: [Returns basic string matching]

[Iteration - Clarify]
You: "I meant search a database table, not search within a string.
      Query the Users table for matching names or emails."
AI: [Returns SQL query function]
```

**Technique 2: Add Constraints**

Refine by adding specific requirements:

```
[First Attempt]
You: "Sort this array of objects"
AI: [Sorts by first property alphabetically]

[Iteration - Add Constraint]
You: "Sort by the 'priority' field (high to low), 
      then by 'createdAt' (newest first) for items with same priority."
AI: [Returns proper multi-field sort]
```

**Technique 3: Provide Examples**

Show desired input/output:

```
[First Attempt]
You: "Format the phone number"
AI: [Returns (555) 123-4567 format]

[Iteration - Show Example]
You: "I want this format:
      Input:  '5551234567'
      Output: '+1-555-123-4567'
      
      Apply this format."
AI: [Returns correct format]
```

**Technique 4: Point Out Specific Issues**

Be precise about what's wrong:

```
[First Attempt]
You: "Create a loading spinner component"
AI: [Creates component but hardcodes size and color]

[Iteration - Specific Feedback]
You: "Make size and color configurable via props:
      - size: 'small' | 'medium' | 'large'
      - color: string (hex color)
      - Default: medium size, blue (#0066cc)"
AI: [Returns component with props]
```

**Technique 5: Build on Partial Success**

Keep what works, refine what doesn't:

```
[First Attempt]
You: "Create a user registration form"
AI: [Returns form but lacks validation]

[Iteration - Build On It]
You: "Good start! Now add validation:
      - Email must be valid format
      - Password must be 8+ characters
      - Show error messages under each field
      - Disable submit button until all fields are valid"
AI: [Adds validation to existing form]
```

**Technique 6: Request Alternatives**

Explore different approaches:

```
[First Attempt]
You: "Implement caching"
AI: [Uses in-memory caching]

[Iteration - Ask for Alternatives]
You: "This won't work in a distributed system.
      Show me alternatives:
      1. Redis-based caching
      2. Database query caching
      3. CDN caching
      
      Compare pros/cons for each."
AI: [Provides comparison and multiple implementations]
```

**Technique 7: Incremental Refinement**

Make small improvements each turn:

```
Turn 1: "Create a button component"
→ [Basic button]

Turn 2: "Add loading state with spinner"
→ [Button with loading]

Turn 3: "Add disabled state with reduced opacity"
→ [Button with multiple states]

Turn 4: "Add error state with red styling"
→ [Complete button component]

Turn 5: "Add TypeScript types for all props"
→ [Production-ready]
```

**Technique 8: Ask "Why" Before Asking "How"**

Understand the reasoning, then refine:

```
[First Attempt]
You: "How do I store user sessions?"
AI: [Suggests localStorage]

[Iteration - Question the Approach]
You: "Why localStorage instead of cookies?
      My app needs to work across subdomains."
AI: "For cross-subdomain, use cookies with domain: '.yourdomain.com'.
     Here's how..."
```

**Technique 9: Reference Previous Context**

Keep the conversation coherent:

```
Turn 1: You: "Create a User interface"
        AI: [Creates interface]

Turn 3: You: "Now create a function that takes the User interface we 
              defined earlier and validates all required fields."
        AI: [Uses the actual User interface from Turn 1]
```

**Technique 10: Reset When Necessary**

If conversation gets tangled, start fresh:

```
[After 10 back-and-forth exchanges that went off-track]

You: "Let's start over. Here's exactly what I need:

[Paste clear, complete requirements]

Ignore our previous discussion about [tangent topic]."
```

**Iteration Workflow Example:**

```
➀ Initial Prompt (Broad)
   "Create a data fetching hook for React"
   → Generic useFetch hook

➁ Add Specifics
   "Add loading, error, and data states.
    Support Authorizationheader."
   → Better, but still generic

➂ Show Your Pattern
   "Follow this structure:
    - useQuery pattern (inspired by React Query)
    - Return { data, isLoading, error, refetch }"
   → Matches your conventions

➃ Request Features
   "Add automatic retry on failure (3 attempts)
    with exponential backoff"
   → Production-ready

➄ Add Edge Cases
   "Handle network offline scenario:
    - Don't retry if offline
    - Show 'No connection' error
    - Auto-retry when connection restored"
   → Robust implementation

➅ Request Tests
   "Add React Testing Library tests for:
    - Successful fetch
    - Error handling
    - Retry logic
    - Offline behavior"
   → Complete, tested solution
```

**When to Iterate vs Start Over:**

**Iterate ✅** when:
- The approach is right, details need refinement
- You're adding features incrementally
- Previous context is relevant

**Start Over ✅** when:
- The fundamental approach is wrong
- Conversation has too many tangents
- You've realized your initial request was unclear
- AI is "stuck" on a misunderstanding

**Meta-Prompt: Ask for Clarification**

When you're not sure how to improve, ask AI:

```
You: "This isn't quite what I need, but I'm not sure how to explain it.
      What information would help you give me a better answer?"

AI: "I can provide a better solution if you clarify:
     1. Are you using REST or GraphQL?
     2. Do you need real-time updates?
     3. What's your error handling strategy?
     4. Are you using TypeScript?"
```

AI can help you identify what's missing from your prompt!

**Golden Rules:**

1. **Don't give up after first try** - Iteration is expected
2. **Be specific about what's wrong** - "Not quite right" doesn't help
3. **Build incrementally** - Refine features one at a time
4. **Keep context relevant** - Reference previous good results
5. **Reset if stuck** - Fresh start > tangled conversation

**Remember:**

> Prompt engineering is a conversation, not a one-shot command.  
> The best developers iterate strategically to refine results.

## Resources

### GitHub Copilot Official Documentation
- **Type:** Documentation
- **Duration/Length:** 30 min read
- **Level:** Beginner to Advanced
- **Why this matters:** Comprehensive official guide covering installation, features, best practices, and troubleshooting for GitHub Copilot
- **Link:** [GitHub Copilot Docs](https://docs.github.com/en/copilot)

### Anthropic's Claude Documentation
- **Type:** Documentation
- **Duration/Length:** 25 min read
- **Level:** Beginner to Intermediate
- **Why this matters:** Official guide to Claude's capabilities, prompt engineering best practices, and API usage patterns
- **Link:** [Claude Docs](https://docs.anthropic.com/)

### "Prompt Engineering Guide" by OpenAI
- **Type:** Documentation
- **Duration/Length:** 45 min read
- **Level:** Beginner to Advanced
- **Why this matters:** Authoritative guide on prompt engineering techniques with real examples and best practices from the creators of GPT
- **Link:** [OpenAI Prompt Engineering](https://platform.openai.com/docs/guides/prompt-engineering)

### "The Cursor Directory"
- **Type:** Tool Documentation & Examples
- **Duration/Length:** 20 min exploration
- **Level:** Intermediate
- **Why this matters:** Collection of Cursor rules and prompts showing advanced AI-assisted coding patterns
- **When to explore:** After completing Exercise 1 with Cursor, looking for advanced patterns and community best practices
- **Link:** [Cursor Directory](https://cursor.directory/)

### "Copilot Patterns" by GitHub
- **Type:** Article Collection
- **Duration/Length:** 20 min read
- **Level:** Beginner
- **Why this matters:** Real-world usage patterns and tips from GitHub's team on getting the most out of Copilot
- **Best for:** Developers using Copilot for 2+ weeks, wanting to level up from basic autocomplete to advanced patterns
- **Link:** [GitHub Blog - Copilot](https://github.blog/tag/github-copilot/)

### "A Complete Guide to LLM Prompt Engineering" by Anthropic
- **Type:** Article
- **Duration/Length:** 35 min read
- **Level:** Intermediate to Advanced
- **Why this matters:** Deep dive into advanced prompting techniques including chain-of-thought, few-shot learning, and structured outputs
- **Link:** [Anthropic Prompt Engineering](https://www.anthropic.com/research)

### Learn Prompting (learnprompting.org)
- **Type:** Interactive Course
- **Duration/Length:** 2-3 hours for core modules
- **Level:** Beginner
- **Why this matters:** Free, comprehensive course on prompt engineering with interactive exercises and real examples
- **Link:** [Learn Prompting](https://learnprompting.org/)

---

## What's Next?

**✅ You've completed: Tools & Platforms**

You now have:
- Hands-on experience with Cursor, GitHub Copilot, and Claude Code
- Prompt engineering fundamentals
- Practical exercises demonstrating each tool's strengths

**▶️ Next up:** [3. GSD Framework →](../03-gsd/README.md) — Learn structured AI workflows for complex projects

**Navigation:**
- [← Previous: 1. Ecosystem](../01-ecosystem/README.md)
- [Home: Learning Pathway](../README.md)
- [Next: 3. GSD Framework →](../03-gsd/README.md)

**Skip ahead** (if experienced):
- [Agents →](../04-agents/README.md) — Autonomous execution patterns
- [Skills →](../05-skills/README.md) — Pre-built AI capabilities
- [Capstone →](../06-capstone/README.md) — Build your portfolio

---
