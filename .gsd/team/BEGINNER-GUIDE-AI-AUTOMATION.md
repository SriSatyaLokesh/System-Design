# Complete Beginner''s Guide to AI-Automated Development
**For:** Developers who want to automate their workflow with AI agents  
**Using:** GitHub Copilot + GSD Framework + VSCode  
**Skill Level:** Beginner-friendly (step-by-step instructions)
---
## ≡ƒôï Table of Contents
1. [What Is This System?](#what-is-this-system)
2. [Prerequisites](#prerequisites)
3. [Initial Setup (One-Time)](#initial-setup-one-time)
4. [Understanding the Components](#understanding-the-components)
5. [Your First Automated Task](#your-first-automated-task)
6. [Daily Workflow](#daily-workflow)
7. [How AI Agents Work](#how-ai-agents-work)
8. [Advanced Automation](#advanced-automation)
9. [Troubleshooting](#troubleshooting)
10. [Real Examples](#real-examples)
---
## What Is This System?
Imagine having a **team of AI assistants** that:
- Γ£à Understand your project automatically
- Γ£à Write code following your team''s standards
- Γ£à Break down large tasks into manageable steps
- Γ£à Execute tasks autonomously
- Γ£à Document what they did and why
- Γ£à Coordinate with your human team members
This system combines:
- **GSD Framework** = Planning & orchestration (the "manager")
- **GitHub Copilot** = AI code writing (the "developer")
- **VSCode** = Your workspace (the "office")
### The Simple Explanation
**Traditional Development:**
```
You: "I need to add a user authentication feature"
You: *spends 3 hours researching*
You: *spends 4 hours coding*
You: *spends 1 hour debugging*
You: *spends 1 hour documenting*
Total: 9 hours
```
**AI-Automated Development:**
```
You: "/plan-phase 2" (creates detailed plan)
AI Agent 1: *researches authentication patterns* (15 minutes)
AI Agent 2: *creates implementation plan* (10 minutes)
You: "/execute-phase 2"
AI Agent 3: *implements Task 1* (20 minutes)
AI Agent 3: *implements Task 2* (20 minutes)
AI Agent 3: *implements Task 3* (15 minutes)
AI Agent 4: *verifies everything works* (10 minutes)
AI Agent 5: *writes documentation* (5 minutes)
Total: 1.5 hours (you spend 5 minutes directing)
```
---
## Prerequisites
### What You Need Installed
1. **VSCode** (Visual Studio Code)
   - Download: https://code.visualstudio.com/
   - Latest version (1.85+)
2. **GitHub Copilot Extension**
   - Install from VSCode Extensions marketplace
   - Requires GitHub account + Copilot subscription
   - Cost: \/month (individual) or \/month (business)
   - Link: https://github.com/features/copilot
3. **Git**
   - Windows: https://git-scm.com/download/win
   - Mac: `brew install git`
   - Linux: `sudo apt-get install git`
4. **Node.js** (Optional, for some projects)
   - Download: https://nodejs.org/
   - Version 18+ recommended
### What You Need to Know
**Absolute Minimum:**
- How to open a terminal/command prompt
- How to navigate folders (`cd`, `ls`/`dir`)
- How to type commands and press Enter
**Nice to Have (But Not Required):**
- Basic git (commit, push, pull)
- Markdown syntax
- Programming basics
**Don''t Worry About:**
- Advanced programming concepts
- Complex git workflows
- Project architecture
- AI/ML knowledge
The AI agents will handle the technical complexity!
---
## Initial Setup (One-Time)
### Step 1: Install GitHub Copilot
1. Open VSCode
2. Click Extensions icon (left sidebar, looks like 4 squares)
3. Search for "GitHub Copilot"
4. Click "Install" on these two extensions:
   - **GitHub Copilot** (main extension)
   - **GitHub Copilot Chat** (chat interface)
5. Click "Sign in to GitHub" when prompted
6. Authorize VSCode in your browser
**How to Test It Works:**
1. Create a new file: `test.js`
2. Type: `// Function to add two numbers`
3. Press Enter
4. Copilot should suggest code automatically (ghosted text)
5. Press Tab to accept the suggestion
If you see suggestions, Γ£à **Copilot is working!**
### Step 2: Clone This Repository
```bash
# Open terminal in VSCode (Ctrl+ or View > Terminal)
# Navigate to where you want the project
cd D:\projects  # Windows
cd ~/projects   # Mac/Linux
# Clone the repository
git clone https://github.com/SriSatyaLokesh/System-Design.git
# Open in VSCode
cd System-Design
code .
```
### Step 3: Verify Setup
1. **Check GSD Framework exists:**
   ```bash
   ls .gsd
   # Should show: PROJECT.md, ROADMAP.md, STATE.md, config.json, phases/, team/
   ```
2. **Check Copilot Instructions exist:**
   ```bash
   ls .github
   # Should show: copilot-instructions.md, CODEOWNERS, instructions/
   ```
3. **Open Copilot Chat:**
   - Press `Ctrl+Shift+I` (Windows/Linux) or `Cmd+Shift+I` (Mac)
   - Or click the chat icon in the left sidebar
   - Type: "Hello, can you read the project instructions?"
   - Copilot should respond acknowledging the instructions
If all three work, Γ£à **Setup complete!**
---
## Understanding the Components
### Component 1: GSD Framework (The Project Manager)
**Location:** `.gsd/` folder
**What it does:**
- Breaks your project into **phases** (big milestones)
- Breaks phases into **plans** (feature groups)
- Breaks plans into **tasks** (specific actions)
- Tracks what''s done and what''s next
**Think of it like:**
- **Phase** = "Build authentication system"
- **Plan** = "User registration flow"
- **Task** = "Create registration form"
**Key Files:**
- `PROJECT.md` = Project vision ("What are we building?")
- `ROADMAP.md` = All phases listed ("What''s the order?")
- `STATE.md` = Current status ("Where are we now?")
- `phases/XX-name/XX-YY-PLAN.md` = Detailed task lists
### Component 2: GitHub Copilot (The AI Developer)
**Location:** VSCode extension (invisible, always running)
**What it does:**
- Reads your project files
- Understands your instructions
- Suggests code as you type
- Answers questions in chat
- Generates entire files/functions
**Think of it like:**
A junior developer sitting next to you who:
- Knows millions of code patterns
- Never gets tired
- Works 24/7
- Follows your team''s guidelines perfectly
### Component 3: Copilot Instructions (The Company Handbook)
**Location:** `.github/copilot-instructions.md`
**What it does:**
- Tells Copilot your project''s rules
- Defines coding standards
- Explains file structure
- Lists common patterns
**Think of it like:**
An employee handbook that every AI agent reads on their first day.
### Component 4: GSD Skills (The Automation Scripts)
**Location:** `.github/skills/`
**What it does:**
- Specialized AI agents for specific jobs
  - `execute-plan` = Implements a plan
  - `verify-phase` = Checks work quality
  - `research-phase` = Investigates solutions
  - `map-codebase` = Analyzes existing code
**Think of it like:**
Different departments in your company:
- Research team
- Development team
- QA team
- Documentation team
### Component 5: Team Coordination (The Shared Calendar)
**Location:** `.gsd/team/`
**What it does:**
- `ASSIGNMENTS.md` = Who''s working on what
- `TEAM-WORKFLOW-GUIDE.md` = How we work together
- `DECISION-MATRIX.md` = Why we chose this approach
**Think of it like:**
A shared workspace where everyone sees:
- Current assignments
- Team status
- How to collaborate
---
## Your First Automated Task
Let''s walk through creating a new feature **completely automated** by AI agents.
### Example: Add a "Contact Form" Feature
#### Step 1: Check the Roadmap
Open the project status:
```bash
# In VSCode terminal
cat .gsd/ROADMAP.md
```
You''ll see something like:
```
Phase 01: Foundation Γ£à Complete
Phase 02: User Features Γ£à Complete  
Phase 03: Contact System ≡ƒƒí In Progress
Phase 04: Polish ≡ƒö┤ Not Started
```
Let''s say you want to work on **Phase 03**.
#### Step 2: Generate a Plan (AI Does This)
In VSCode terminal, run:
```bash
# This command tells AI to create a detailed plan for Phase 3
/plan-phase 3
```
**What happens behind the scenes:**
1. Γ£à AI reads PROJECT.md (understands project goal)
2. Γ£à AI reads ROADMAP.md (understands Phase 3 description)
3. Γ£à AI researches contact form best practices (15 min)
4. Γ£à AI creates detailed task list (5 min)
5. Γ£à AI saves to `.gsd/phases/03-contact-system/03-01-PLAN.md`
**You see:**
```
≡ƒôï GSD Planner Agent
Phase 03: Contact System
Researching implementation approaches...
Γ£à Research complete: 14 pages analyzed
Γ£à Plan created: 8 tasks identified
Plan saved to: .gsd/phases/03-contact-system/03-01-PLAN.md
Would you like to:
1. Review the plan
2. Execute the plan now
3. Modify the plan
```
#### Step 3: Review the Plan
```bash
# Open the generated plan
code .gsd/phases/03-contact-system/03-01-PLAN.md
```
You''ll see:
```markdown
---
phase: 03-contact-system
plan: 01
tasks: 8
---
## Objective
Create a fully functional contact form with validation, 
submission handling, and admin notification.
## Tasks
### Task 1: Create contact form UI component (30 min)
- Input fields: name, email, subject, message
- Validation: email format, required fields
- Responsive design for mobile
### Task 2: Add form validation logic (20 min)
- Client-side validation with real-time feedback
- Error messages for invalid inputs
- Disable submit until valid
### Task 3: Create API endpoint for submissions (25 min)
- POST /api/contact endpoint
- Validate and sanitize inputs
- Store in database
... (5 more tasks)
```
**Your decision:**
- Γ£à Looks good? Proceed to Step 4
- Γ¥î Want changes? Edit PLAN.md, save, then proceed
#### Step 4: Execute the Plan (AI Does Everything)
Run this single command:
```bash
/execute-plan 03-01
```
**What happens over the next 30-60 minutes:**
**Minute 0-5: Task 1 Execution**
```
≡ƒñû GSD Executor Agent
Executing: Task 1 - Create contact form UI component
[AI reads copilot-instructions.md]
[AI reads content-quality.instructions.md]
[AI analyzes existing components for consistency]
Γ£à Created: src/components/ContactForm.tsx (87 lines)
Γ£à Added: Input validation hooks
Γ£à Added: Responsive styling
Γ£à Tested: Form renders correctly
Commit: feat(03-01): create contact form UI component
```
**Minute 5-10: Task 2 Execution**
```
≡ƒñû GSD Executor Agent
Executing: Task 2 - Add form validation logic
Γ£à Created: src/utils/validation.ts (45 lines)
Γ£à Integrated: Real-time validation in form
Γ£à Added: Error message components
Γ£à Tested: Validation triggers correctly
Commit: feat(03-01): add form validation logic
```
**Minute 10-15: Task 3 Execution**
```
≡ƒñû GSD Executor Agent
Executing: Task 3 - Create API endpoint
Γ£à Created: pages/api/contact.ts (62 lines)
Γ£à Added: Input sanitization
Γ£à Added: Database storage logic
Γ£à Added: Error handling
Γ£à Tested: Endpoint responds correctly
Commit: feat(03-01): create contact submission API
```
... (continues for all 8 tasks)
**Final Output:**
```
Γ£à Plan Execution Complete!
Tasks completed: 8/8
Files created: 12
Files modified: 5
Lines added: 847
Commits made: 8
Duration: 42 minutes
Summary saved to: .gsd/phases/03-contact-system/03-01-SUMMARY.md
Would you like to:
1. Verify the implementation
2. Test the feature
3. Create a pull request
```
#### Step 5: Verify It Works (AI Does This Too)
```bash
/verify-phase 03
```
**What happens:**
```
≡ƒöì GSD Verifier Agent
Verifying Phase 03: Contact System
Checking against requirements...
Γ£à REQ-01: Contact form renders on /contact page
Γ£à REQ-02: Form validates email format
Γ£à REQ-03: Form prevents invalid submissions
Γ£à REQ-04: API endpoint stores submissions
Γ£à REQ-05: Admin receives email notifications
Γ£à REQ-06: Form shows success message after submit
Manual verification needed:
ΓÜá∩╕Å  Test form submission end-to-end
ΓÜá∩╕Å  Check mobile responsiveness
ΓÜá∩╕Å  Verify email delivery
Verification saved to: .gsd/phases/03-contact-system/03-VERIFICATION.md
```
#### Step 6: Test It Yourself
The AI has done 90% of the work. Now you:
1. **Run the development server:**
   ```bash
   npm run dev
   ```
2. **Open browser:** `http://localhost:3000/contact`
3. **Test the form:**
   - Fill out form
   - Try invalid email (should show error)
   - Submit valid form (should succeed)
4. **Check database:** Verify submission was saved
5. **Check email:** Verify notification was sent
**If everything works:** Γ£à Phase complete!
**If something broke:** See "Troubleshooting" section below
#### Step 7: Document and Move On
```bash
# Mark phase complete
/transition 03 04
# Creates summary and advances to Phase 04
```
**What you just did:**
- ΓÅ▒∩╕Å **5 minutes** directing AI agents
- ΓÅ▒∩╕Å **10 minutes** reviewing and testing
- ΓÅ▒∩╕Å **15 minutes** total (vs 4-6 hours manually)
**What AI agents did:**
- ΓÅ▒∩╕Å **20 minutes** researching
- ΓÅ▒∩╕Å **10 minutes** planning
- ΓÅ▒∩╕Å **42 minutes** implementing
- ΓÅ▒∩╕Å **8 minutes** verifying
- ΓÅ▒∩╕Å **80 minutes** total work (done autonomously)
---
## Daily Workflow
### Morning Routine (5 minutes)
**1. Open your project in VSCode:**
```bash
cd D:\projects\System-Design
code .
```
**2. Check team status:**
```bash
# See what everyone is working on
cat .gsd/team/ASSIGNMENTS.md
```
You''ll see:
```markdown
## Current Sprint Assignments
### Phase 05: Advanced Features
- **Owner:** @developer-a
- **Status:** ≡ƒƒí In Progress (60%)
### Phase 06: Polish
- **Owner:** Unassigned
- **Status:** ≡ƒö┤ Not Started
**Available for you:** Phase 06
```
**3. Check project status:**
```bash
# See overall project health
cat .gsd/STATE.md
```
**4. Claim your work:**
Edit `.gsd/team/ASSIGNMENTS.md`, add your name:
```markdown
### Phase 06: Polish
- **Owner:** @your-username
- **Status:** ≡ƒƒí In Progress
```
Commit:
```bash
git add .gsd/team/ASSIGNMENTS.md
git commit -m "docs: assign Phase 06 to @your-username"
git push
```
### Development Work (1-4 hours)
**Option 1: Use Full Automation**
```bash
# Let AI do everything
/execute-phase 06
# Go get coffee, check back in 30-60 minutes
```
**Option 2: Task-by-Task with AI Assistance**
```bash
# Get the plan
cat .gsd/phases/06-polish/06-01-PLAN.md
# For each task, use Copilot Chat:
# Press Ctrl+Shift+I to open chat
```
In Copilot Chat:
```
You: I''m working on Task 1 from Phase 06 Plan 01. 
     Read @.gsd/phases/06-polish/06-01-PLAN.md 
     and help me implement it.
Copilot: I see Task 1 is "Add mobile responsiveness to navigation".
         Based on the project structure in @.github/copilot-instructions.md,
         I''ll update the navigation component.
         Here''s the implementation...
         [provides complete code]
You: Generate a commit message for this change
Copilot: feat(06-01): add mobile responsiveness to navigation
         - Implemented hamburger menu for mobile devices
         - Added responsive breakpoints at 768px and 480px
         - Tested on iOS Safari and Chrome Android
```
**Option 3: Hybrid (You Code, AI Assists)**
```typescript
// You start typing in VSCode
function validateEmail(
// Copilot suggests (ghosted text):
function validateEmail(email: string): boolean {
  const emailRegex = /^[^\\s@]+@[^\\s@]+\\.[^\\s@]+\$/;
  return emailRegex.test(email);
}
// Press Tab to accept
```
### Evening Routine (5 minutes)
**1. Update your progress:**
Edit `.gsd/team/ASSIGNMENTS.md`:
```markdown
### Phase 06: Polish
- **Owner:** @your-username
- **Status:** Γ£à Complete
- **Tasks:**
  - [x] Task 1: Mobile responsiveness (commit: abc123)
  - [x] Task 2: Loading states (commit: def456)
  - [x] Task 3: Error boundaries (commit: ghi789)
```
**2. Push your work:**
```bash
git add .
git commit -m "docs: mark Phase 06 tasks complete"
git push origin gsd/phase-06-polish
```
**3. Create pull request:**
- Go to GitHub repository
- Click "Pull Requests" > "New Pull Request"
- Base: `main`, Compare: `gsd/phase-06-polish`
- Title: "Complete Phase 06: Polish"
- Description: Link to `.gsd/phases/06-polish/06-01-SUMMARY.md`
- Click "Create Pull Request"
CODEOWNERS will automatically assign reviewers!
---
## How AI Agents Work
### Understanding AI Agents vs GitHub Copilot
**GitHub Copilot** (Always Active in VSCode)
- Suggests code as you type
- Answers questions in chat
- Reads your instructions automatically
- **Scope:** Single file or task
**GSD AI Agents** (Activated by Commands)
- Execute multi-step workflows
- Coordinate across multiple files
- Make architectural decisions
- **Scope:** Entire plans or phases
### Types of GSD Agents
#### 1. Researcher Agent (`gsd-phase-researcher`)
**Command:** `/research-phase <number>`
**What it does:**
```
Input: "Phase 3: Authentication"
Agent:
1. Searches web for latest auth best practices
2. Reads official documentation (OAuth, JWT)
3. Analyzes security considerations
4. Compares library options (Passport, Auth0, Firebase)
5. Creates research report with recommendations
Output: .gsd/phases/03-*/03-RESEARCH.md (3000+ words)
Time: 15-20 minutes
```
**When to use:**
- Starting a new feature with unknown tech
- Need to choose between multiple approaches
- Want current best practices (not outdated info)
#### 2. Planner Agent (`gsd-planner`)
**Command:** `/plan-phase <number>`
**What it does:**
```
Input: Phase 3 + Research results
Agent:
1. Reads research recommendations
2. Reads project requirements
3. Breaks phase into logical plans (3-5 plans)
4. Breaks each plan into tasks (5-10 tasks)
5. Estimates time for each task
6. Identifies dependencies
Output: .gsd/phases/03-*/03-01-PLAN.md (500+ lines)
Time: 10-15 minutes
```
**When to use:**
- After research is complete
- Before starting implementation
- Want detailed task breakdown
#### 3. Executor Agent (`gsd-executor`)
**Command:** `/execute-plan <phase>-<plan>`
**What it does:**
```
Input: 03-01-PLAN.md with 8 tasks
Agent:
For each task:
1. Reads task description
2. Reads copilot-instructions.md (standards)
3. Reads existing codebase (context)
4. Generates implementation
5. Tests code works
6. Commits with descriptive message
Output: 8 commits, 847 lines of code
Time: 40-60 minutes
```
**When to use:**
- Plan is approved and ready
- You want autonomous implementation
- Tasks are well-defined
#### 4. Verifier Agent (`gsd-verifier`)
**Command:** `/verify-phase <number>`
**What it does:**
```
Input: Phase 3 implementation + Requirements
Agent:
1. Reads original phase goals
2. Checks all files were created
3. Runs automated tests
4. Checks code quality standards
5. Identifies gaps or issues
6. Creates verification report
Output: .gsd/phases/03-*/03-VERIFICATION.md
Time: 10-15 minutes
```
**When to use:**
- Phase implementation complete
- Before marking phase done
- Quality assurance needed
### How Agents Read Instructions
Every agent **automatically loads** these files:
1. **`.github/copilot-instructions.md`**
   - Project architecture
   - Coding standards
   - File structure
2. **`.github/instructions/*.instructions.md`**
   - Feature-specific patterns
   - Domain knowledge
3. **`.gsd/PROJECT.md`**
   - Project goals
   - Core requirements
4. **`.gsd/STATE.md`**
   - Current status
   - Past decisions
   - Known blockers
**This means:** Every agent has full project context automatically!
---
## Advanced Automation
### Technique 1: Chain Multiple Agents
**Full Phase Automation (Research ΓåÆ Plan ΓåÆ Execute ΓåÆ Verify):**
```bash
# Single command does everything
/execute-phase 3
# Behind the scenes:
# 1. Runs /research-phase 3 (if no research exists)
# 2. Runs /plan-phase 3 (if no plans exist)
# 3. Runs /execute-plan 3-01, 3-02, 3-03 (all plans)
# 4. Runs /verify-phase 3 (checks quality)
# 5. Updates STATE.md
# Total time: 2-3 hours (autonomous)
# Your time: 5 minutes (command + review)
```
### Technique 2: Parallel Plan Execution
If Phase 3 has 3 independent plans:
```bash
# In terminal 1
/execute-plan 3-01
# In terminal 2 (new terminal)
/execute-plan 3-02
# In terminal 3 (new terminal)
/execute-plan 3-03
# All run in parallel!
# Time: 45 minutes (instead of 135 minutes sequential)
```
### Technique 3: Use Copilot Chat for Micro-Tasks
**For small tasks too simple for full agents:**
```
You: Generate a utility function to format phone numbers
     following @.github/copilot-instructions.md standards
Copilot: [generates code with proper TypeScript types,
         error handling, documentation]
You: Add unit tests for this function
Copilot: [generates Jest tests with 100% coverage]
You: Generate commit message
Copilot: feat: add phone number formatting utility
```
### Technique 4: Copilot Edits Entire Files
**Refactor an entire file:**
1. Open file in VSCode
2. Press `Ctrl+A` (select all)
3. Press `Ctrl+K` then `Ctrl+M` (Copilot trigger)
4. Type instruction:
   ```
   Refactor this component to use React hooks instead of class component.
   Keep all functionality identical but modernize the code.
   ```
5. Copilot rewrites entire file (30 seconds)
### Technique 5: Generate Documentation
**After implementation:**
```bash
# In Copilot Chat
You: Read all files in src/components/ContactForm/ and generate
     comprehensive documentation in README.md format
Copilot: [creates documentation with:
         - Component overview
         - Props interface
         - Usage examples
         - Styling guidelines
         - Testing instructions]
```
---
## Troubleshooting
### Problem 1: Copilot Not Suggesting Code
**Symptoms:**
- Type code, no ghosted suggestions appear
- Chat is empty or gives generic responses
**Solutions:**
**Check 1: Extension Enabled**
```
1. Click Extensions icon (left sidebar)
2. Search "GitHub Copilot"
3. Should show "Disable" button (means it''s enabled)
4. If shows "Enable", click it
```
**Check 2: Signed In**
```
1. Bottom-right of VSCode, look for GitHub Copilot icon
2. Click it
3. Should show "Copilot: Active"
4. If not, click "Sign in to GitHub"
```
**Check 3: Subscription Active**
```
1. Go to https://github.com/settings/copilot
2. Should show "GitHub Copilot is active"
3. If not, subscribe or start trial
```
**Check 4: File Type Supported**
```
Copilot works best with:
Γ£à .js, .ts, .jsx, .tsx (JavaScript/TypeScript)
Γ£à .py (Python)
Γ£à .java, .cpp, .cs (Java/C++/C#)
Γ£à .md (Markdown)
May not work well with:
Γ¥î .txt (plain text)
Γ¥î Binary files
Γ¥î Very large files (>10,000 lines)
```
### Problem 2: Agent Commands Don''t Work
**Symptoms:**
- Type `/execute-plan 3-01`
- Get error: "command not found"
**Solutions:**
**Check 1: In Correct Directory**
```bash
# Must be in project root
pwd  # Should show: .../System-Design
# If not, navigate there
cd D:\projects\System-Design
```
**Check 2: GSD Skills Installed**
```bash
# Check skills folder exists
ls .github/skills
# Should show: execute-plan/, execute-phase/, verify-phase/, etc.
```
**Check 3: Use VSCode Terminal**
```
Commands work specifically in:
Γ£à VSCode integrated terminal (Ctrl+)
Γ£à GitHub Copilot Chat (Ctrl+Shift+I with / prefix)
May not work in:
Γ¥î External terminal (PowerShell, CMD outside VSCode)
Γ¥î Git Bash (unless configured)
```
### Problem 3: Agent Generates Wrong Code
**Symptoms:**
- Code doesn''t follow your standards
- Uses outdated patterns
- Doesn''t match existing codebase style
**Solutions:**
**Check 1: Instructions File Exists**
```bash
# Verify instructions are present
cat .github/copilot-instructions.md
# Should have content (not empty)
```
**Check 2: Instructions Are Specific**
**Γ¥î Too Vague:**
```markdown
## Standards
- Write good code
- Follow best practices
```
**Γ£à Specific:**
```markdown
## Standards
- TypeScript strict mode enabled
- Use functional components with hooks (not classes)
- All functions must have JSDoc comments
- File names use kebab-case (user-profile.tsx)
```
**Check 3: Reference Instructions in Prompts**
When asking Copilot:
```
Γ¥î Vague: "Create a contact form"
Γ£à Specific: "Create a contact form following 
            @.github/copilot-instructions.md standards
            and matching style of @src/components/LoginForm.tsx"
```
### Problem 4: Git Merge Conflicts
**Symptoms:**
- Pull latest changes
- Get conflict in `.gsd/STATE.md`
**Solution (Easy Way):**
```bash
# 1. Accept both changes
git checkout --theirs .gsd/STATE.md  # Keep their version
git add .gsd/STATE.md
# 2. Append your changes manually
# Open STATE.md, add your new decisions at bottom
# 3. Commit
git commit -m "docs: resolve STATE.md conflict"
```
**Solution (Proper Way):**
```bash
# 1. Open file in VSCode
code .gsd/STATE.md
# 2. You''ll see conflict markers:
<<<<<<< HEAD
Your changes
=======
Their changes
>>>>>>> main
# 3. Keep both, merge chronologically:
Recent Activity:
- 2026-03-02: Their activity
- 2026-03-02: Your activity
# 4. Save, commit
git add .gsd/STATE.md
git commit -m "docs: merge STATE.md updates"
```
---
## Real Examples
### Example 1: Building a Blog (Complete Flow)
**Starting from scratch:**
```bash
# Step 1: Initialize project
/new-project
# You answer questions:
# "What are you building?" ΓåÆ "A personal blog with markdown posts"
# "Tech stack?" ΓåÆ "Next.js 15, React, TypeScript, Tailwind"
# "Timeline?" ΓåÆ "2 weeks"
# AI creates:
# - .gsd/PROJECT.md (vision)
# - .gsd/ROADMAP.md (5 phases)
# - .gsd/REQUIREMENTS.md (25 requirements)
```
**Generated Roadmap:**
```
Phase 01: Project Setup (1 day)
Phase 02: Blog Post System (3 days)
Phase 03: UI/UX Design (2 days)
Phase 04: SEO & Performance (2 days)
Phase 05: Deployment (1 day)
```
**Execute Phase by Phase:**
```bash
# Week 1, Monday
/execute-phase 1
# Γ£à Creates Next.js project, configures TypeScript, Tailwind
# Γ£à Duration: 45 minutes
# Week 1, Tuesday
/execute-phase 2
# Γ£à Creates markdown processing
# Γ£à Builds blog post components
# Γ£à Adds pagination
# Γ£à Duration: 2 hours
# Week 1, Thursday
/execute-phase 3
# Γ£à Designs homepage layout
# Γ£à Creates blog post templates
# Γ£à Adds dark mode
# Γ£à Duration: 1.5 hours
# Week 2, Monday
/execute-phase 4
# Γ£à Adds meta tags for SEO
# Γ£à Optimizes images
# Γ£à Implements code splitting
# Γ£à Duration: 1 hour
# Week 2, Wednesday
/execute-phase 5
# Γ£à Configures Vercel deployment
# Γ£à Sets up custom domain
# Γ£à Adds analytics
# Γ£à Duration: 45 minutes
# Total: 6.25 hours of AI work over 2 weeks
# Your time: ~30 minutes directing, ~2 hours testing
```
### Example 2: Adding Authentication (Task-Level)
**Starting point:** Existing app needs login
```bash
# Create new phase
/add-phase "User Authentication with JWT"
# AI asks:
# "OAuth or JWT?" ΓåÆ "JWT"
# "Email/password or social?" ΓåÆ "Both"
# "Password reset?" ΓåÆ "Yes"
# AI generates roadmap addition:
# Phase 08: User Authentication
#   - Plan 08-01: Registration flow
#   - Plan 08-02: Login flow
#   - Plan 08-03: Password reset flow
#   - Plan 08-04: OAuth integration (Google, GitHub)
# Execute first plan
/execute-plan 8-01
```
**What AI Generates (Plan 08-01):**
**Files Created:**
```
src/
Γö£ΓöÇΓöÇ pages/
Γöé   Γö£ΓöÇΓöÇ api/
Γöé   Γöé   Γö£ΓöÇΓöÇ auth/
Γöé   Γöé   Γöé   Γö£ΓöÇΓöÇ register.ts       (Created by Task 1)
Γöé   Γöé   Γöé   Γö£ΓöÇΓöÇ verify-email.ts   (Created by Task 2)
Γöé   Γöé   Γöé   ΓööΓöÇΓöÇ login.ts          (Created by Task 3)
Γöé   ΓööΓöÇΓöÇ register.tsx               (Created by Task 4)
Γö£ΓöÇΓöÇ components/
Γöé   Γö£ΓöÇΓöÇ auth/
Γöé   Γöé   Γö£ΓöÇΓöÇ RegisterForm.tsx      (Created by Task 5)
Γöé   Γöé   ΓööΓöÇΓöÇ EmailVerification.tsx (Created by Task 6)
Γö£ΓöÇΓöÇ utils/
Γöé   Γö£ΓöÇΓöÇ jwt.ts                     (Created by Task 7)
Γöé   ΓööΓöÇΓöÇ password-hash.ts           (Created by Task 7)
ΓööΓöÇΓöÇ middleware/
    ΓööΓöÇΓöÇ auth.ts                    (Created by Task 8)
```
**Commits Made:**
```
1. feat(08-01): create user registration API endpoint
2. feat(08-01): add email verification system
3. feat(08-01): implement login API with JWT
4. feat(08-01): create registration page UI
5. feat(08-01): build registration form component
6. feat(08-01): add email verification UI
7. feat(08-01): implement JWT utilities and password hashing
8. feat(08-01): add authentication middleware
9. docs(08-01): complete registration flow - summary created
```
**Duration:** 52 minutes autonomous execution
### Example 3: Daily Micro-Tasks (Copilot Chat)
**Scenario:** Small tasks throughout the day
**10:00 AM - Fix a bug:**
```
You: The contact form isn''t validating email addresses.
     File: @src/components/ContactForm.tsx
Copilot: I see the issue on line 34. The regex pattern is missing
         the domain validation. Here''s the fix:
         [shows corrected code]
You: Apply this fix
Copilot: [updates the file automatically]
Time: 2 minutes
```
**11:30 AM - Add a feature:**
```
You: Add a character counter to the message textarea in ContactForm.
     Show "X/500 characters" below the field.
     Follow @.github/copilot-instructions.md styling.
Copilot: [generates code with:
         - useState for character count
         - Styled counter component
         - Validation for max length]
         Would you like me to add this to the file?
You: Yes
Time: 3 minutes
```
**2:00 PM - Refactor code:**
```
You: This function is too long. Refactor into smaller functions:
     @src/utils/validation.ts#L45-L120
Copilot: [breaks into 4 smaller functions:
         - validateEmail()
         - validatePhone()
         - validateRequired()
         - validateForm()]
         All functions have JSDoc comments and types.
Time: 4 minutes
```
**4:00 PM - Write tests:**
```
You: Generate unit tests for @src/utils/validation.ts
     covering all edge cases
Copilot: [creates tests with:
         - 15 test cases
         - 100% code coverage
         - Edge cases for empty, invalid, and null inputs]
Time: 3 minutes
```
**5:00 PM - Documentation:**
```
You: Generate API documentation for all endpoints in /api/auth/*
Copilot: [creates Swagger/OpenAPI spec with:
         - All endpoints documented
         - Request/response examples
         - Error codes explained]
Time: 5 minutes
```
**Total productive work:** 17 minutes  
**Value delivered:** 4-5 hours of manual work
---
## Quick Command Reference
### GSD Commands (In VSCode Terminal)
| Command | What It Does | Time | Example |
|---------|--------------|------|---------|
| `/new-project` | Initialize new project with GSD | 5 min | `/new-project` |
| `/research-phase N` | Research implementation approaches | 15-20 min | `/research-phase 3` |
| `/plan-phase N` | Create detailed task plan | 10-15 min | `/plan-phase 3` |
| `/execute-plan N-M` | Implement specific plan | 40-60 min | `/execute-plan 3-01` |
| `/execute-phase N` | Implement entire phase | 2-3 hrs | `/execute-phase 3` |
| `/verify-phase N` | Check implementation quality | 10-15 min | `/verify-phase 3` |
| `/transition N M` | Complete phase, move to next | 5 min | `/transition 3 4` |
| `/progress` | Show current status | instant | `/progress` |
| `/add-phase "Name"` | Insert new phase | 5 min | `/add-phase "Polish"` |
### GitHub Copilot Shortcuts (In VSCode)
| Shortcut | What It Does | When to Use |
|----------|--------------|-------------|
| `Tab` | Accept suggestion | Code appears ghosted |
| `Esc` | Reject suggestion | Don''t want suggestion |
| `Alt+]` | Next suggestion | Want alternative |
| `Alt+[` | Previous suggestion | Cycle back |
| `Ctrl+Enter` | Show all suggestions | See 10 alternatives |
| `Ctrl+Shift+I` | Open Copilot Chat | Ask questions |
| `Ctrl+K Ctrl+M` | Inline chat in editor | Refactor current file |
| `Ctrl+L` | Add file to chat context | Reference specific file |
### Copilot Chat Commands
| Command | What It Does | Example |
|---------|--------------|---------|
| `@workspace` | Search entire codebase | `@workspace where is auth logic?` |
| `@terminal` | Explain terminal error | `@terminal what does this error mean?` |
| `#file:pattern` | Reference file | `#file:*.tsx show all React components` |
| `/explain` | Explain selected code | Select code, then `/explain` |
| `/fix` | Fix selected code | Select buggy code, then `/fix` |
| `/tests` | Generate tests | Select function, then `/tests` |
| `/doc` | Generate documentation | Select code, then `/doc` |
---
## Tips for Success
### 1. Start Small
- Γ£à First day: Try one `/execute-plan` command
- Γ£à First week: Complete one phase with full automation
- Γ£à First month: Master all GSD commands
- Γ¥î Don''t: Try to automate everything immediately
### 2. Review AI-Generated Code
- Γ£à Always read what AI created
- Γ£à Test thoroughly before merging
- Γ£à Fix any issues and document in STATE.md
- Γ¥î Don''t: Blindly trust AI output
### 3. Keep Instructions Updated
- Γ£à When you make a decision, add to `.github/copilot-instructions.md`
- Γ£à When you find a pattern, document in `.github/instructions/`
- Γ£à Update after each major change
- Γ¥î Don''t: Let instructions get stale
### 4. Use the Right Tool
- **GSD agents:** Multi-file features, entire plans
- **Copilot Chat:** Single tasks, questions, refactoring
- **Copilot suggestions:** Inline code completion
- **Manual coding:** Complex logic, business rules, creative work
### 5. Communicate with Your Team
- Γ£à Update `ASSIGNMENTS.md` daily
- Γ£à Add notes for blockers immediately
- Γ£à Review team''s work in morning standup
- Γ¥î Don''t: Work in isolation for days
---
## Next Steps
### Today (30 minutes)
1. Γ£à Install GitHub Copilot (15 min)
2. Γ£à Clone this repository (5 min)
3. Γ£à Read `.gsd/PROJECT.md` and `.gsd/ROADMAP.md` (10 min)
4. Γ£à Try one Copilot suggestion (Tab completion)
### This Week (2 hours)
1. Γ£à Run `/plan-phase` on next unplanned phase
2. Γ£à Run `/execute-plan` on one plan
3. Γ£à Review generated code
4. Γ£à Commit and push
### This Month (Ongoing)
1. Γ£à Complete 2-3 phases with AI automation
2. Γ£à Master Copilot Chat for daily tasks
3. Γ£à Update instructions based on learnings
4. Γ£à Train team members on workflow
---
## Getting Help
### In VSCode
```
Press Ctrl+Shift+I, then ask:
"How do I [task I want to accomplish]?"
"What does this error mean?"
"Show me examples of [coding pattern]"
```
### In This Repository
```
Read these files:
- .gsd/team/TEAM-WORKFLOW-GUIDE.md (team coordination)
- .gsd/team/DECISION-MATRIX.md (architecture rationale)
- .github/copilot-instructions.md (project standards)
```
### Online Resources
- **GitHub Copilot Docs:** https://docs.github.com/en/copilot
- **GSD Framework:** [Agentic AI/03-gsd/README.md](Agentic AI/03-gsd/README.md)
- **VSCode Tips:** https://code.visualstudio.com/docs
---
**You''re now ready to automate 80% of your development work! ≡ƒÜÇ**
Start with `/plan-phase` on your next feature and watch AI agents build it autonomously.
