# 6. Capstone Project

## Table of Contents

- [Overview](#overview)
- [Project Brief](#project-brief)
- [Live Portfolio Example](#live-portfolio-example)
- [Prompts & Strategy](#prompts--strategy)
- [Step-by-Step Guide](#step-by-step-guide)
- [PRD Template](#prd-template)
- [Resources](#resources)
- [Navigation](#navigation)

## Overview

The capstone project ties together everything you've learned—ecosystem understanding, tool proficiency, GSD methodology, agent delegation, and skill utilization—into a complete end-to-end project that demonstrates AI-assisted development mastery.

This section provides a concrete, actionable project that results in a real portfolio piece you can showcase. Rather than a toy example, you'll build something production-ready while practicing the workflow patterns that professional AI-assisted developers use daily.

By completing the capstone, you'll have both a tangible outcome (a deployed project) and deep confidence in your ability to leverage AI for real development work, ready to apply these skills to your own projects and professional goals.

## Project Brief

### The Capstone Project

**Project:** **Personal Developer Dashboard**

A web application that aggregates your development activity and provides insights.

**Why This Project:**

✅ **Exercises Full Pathway:**
- Ecosystem understanding (choosing AI tools)
- Tool proficiency (Copilot + Claude)
- GSD methodology (Goal → Spec → Deliver)
- Agent delegation (implementing features)
- Skill utilization (using community patterns)

✅ **Real-World Applicable:**
- Actual developer tool you'll use
- Portfolio-worthy project
- Demonstrates full-stack skills

✅ **Scope-Appropriate:**
- Completable in 16-24 hours
- Clear success criteria
- Room for creativity

**Core Features:**

**MVP (Minimum Viable Product):**
1. **GitHub Activity Feed:** Display recent commits and PRs
2. **Coding Stats:** Languages used, commit frequency
3. **Goal Tracker:** Set and track learning/coding goals
4. **Simple Dashboard:** Clean UI showing all data

**What You'll Build:**
```
Frontend: React + TypeScript + Tailwind CSS
Backend: Node.js + Express + PostgreSQL
APIs: GitHub API integration
Deploy: Vercel (frontend) + Railway/Render (backend)

Features:
- OAuth authentication with GitHub
- Data fetching and caching
- Interactive charts/visualizations
- Responsive design
- Goal tracking with persistence
```

**Scope Boundaries:**

**In Scope:**
+ GitHub integration (public data)
+ Basic analytics and visualization
+ Goal setting and tracking
+ Clean, responsive UI
+ Deployment to free hosting

**Out of Scope:**
- Mobile app (web only)
- Real-time updates (polling is fine)
- Team features (single user)
- Advanced analytics (basic stats sufficient)
- Payment/monetization (free tool)

**Time Estimate:**
```
Phase 1: Goal & Spec (2-3 hours)
Phase 2: Setup & Auth (3-4 hours)
Phase 3: Core Features (8-10 hours)
Phase 4: Polish & Deploy (3-4 hours)
Phase 5: Documentation (2-3 hours)

Total: 18-24 hours over 1-2 weeks
```

### Learning Objectives

By completing the capstone, you'll practice and reinforce:

**1. Goal Setting & Scoping**
- Translating vague idea into clear requirements
- Setting realistic scope boundaries
- Defining measurable success criteria
- Documenting non-goals to prevent scope creep

**Practice:** Writing your PROJECT.md goal document

**2. Creating Detailed Technical Plans**
- Breaking down features into tasks
- Making architectural decisions upfront
- Ordering tasks by dependencies
- Defining acceptance criteria per task

**Practice:** Creating your PLAN.md specification

**3. Delegating to AI Agents**
- Writing effective prompts for implementation
- Providing appropriate context
- Using Copilot for real-time coding
- Using Claude for architectural decisions

**Practice:** Implementing features with AI assistance

**4. Verifying Quality**
- Testing AI-generated code
- Catching edge cases
- Ensuring security best practices
- Maintaining code quality standards

**Practice:** Reviewing and improving AI output

**5. Iterating on Feedback**
- Identifying gaps in implementation
- Refining features based on testing
- Polishing user experience
- Addressing technical debt

**Practice:** Polish cycle before deployment

**6. Shipping a Complete Feature**
- Deployment to production
- Writing user documentation
- Creating portfolio presentation
- Reflecting on learnings

**Practice:** End-to-end delivery experience

**Skills Matrix:**

| Skill | How You'll Practice |
|-------|---------------------|
| **Prompt Engineering** | Crafting prompts for each task |
| **GSD Framework** | Following Goal → Spec → Deliver flow |
| **Tool Proficiency** | Using Copilot + Claude strategically |
| **Agent Delegation** | Assigning implementation tasks to AI |
| **Verification** | Testing and validating AI output |
| **Full-Stack Dev** | Building frontend + backend + deploy |

**Meta-Learning:**

Beyond technical skills, you'll learn:
- How much AI can handle autonomously
- Where human oversight is critical
- How to debug AI-generated code
- When to use different AI tools
- How to maintain quality with AI assistance

**Confidence Building:**

```
Before Capstone:
"I'm not sure I can build a real project with AI"

After Capstone:
"I've shipped a production app with AI assistance.
I know how to scope, plan, delegate, and deliver.
I'm ready for real projects."
```

### Success Criteria

**You're done when:**

**Functional Requirements:**

✓ **Authentication Works**
- User can connect GitHub account (OAuth)
- Sessions persist across browser restarts
- User can log out

✓ **GitHub Data Displays**
- Recent commits shown with details
- Pull request activity visible
- Repository stats displayed
- Data updates when refreshed

✓ **Goal Tracking Functions**
- User can create new goals
- Goals persist in database
- User can mark goals complete
- Progress visible on dashboard

✓ **Dashboard is Usable**
- Clean, responsive design
- Works on mobile and desktop
- Navigation is intuitive
- No broken UI elements

✓ **Application is Deployed**
- Accessible via public URL
- Frontend and backend both live
- Database connected and functioning
- No critical errors in production

**Quality Bar:**

✓ **Code Quality**
- No obvious security issues (API keys not exposed)
- Error handling in place for API calls
- TypeScript types used properly
- Code is readable and organized

✓ **Testing**
- At least basic manual testing completed
- Key user flows work end-to-end
- Edge cases handled (empty states, errors)

✓ **Documentation**
- README explains what project does
- Setup instructions provided
- Environment variables documented
- Screenshots or demo link included

**Process Criteria:**

✓ **Followed GSD Framework**
- Created Goal document before coding
- Wrote Spec with task breakdown
- Executed tasks systematically
- Verified each task before proceeding

✓ **Used AI Effectively**
- Used Copilot for implementation speed
- Used Claude for architecture decisions
- Reviewed AI output before accepting
- Iterated on AI suggestions when needed

✓ **Portfolio Ready**
- Project presented professionally
- Clear value proposition explained
- Technical decisions documented
- Personal learnings captured

**Not Required:**

✗ Perfect code (it's a learning project)
✗ 100% test coverage
✗ Production-scale performance
✗ Every possible feature
✗ Zero technical debt

**Self-Assessment Questions:**

1. Can I explain what this project does to a non-technical person?
2. Would I be comfortable showing this in a portfolio?
3. Did I learn valuable lessons about AI-assisted development?
4. Could I build a similar project more efficiently next time?
5. Am I proud of what I built?

If you answered "yes" to all 5 → Success! 🎉

### Time Investment

**Total Estimated Time: 18-24 hours over 1-2 weeks**

**Breakdown by Phase:**

**Phase 1: Goal Setting (2-3 hours)**
```
Activities:
- Define project purpose and user value
- Research GitHub API capabilities
- Document MVP features
- Set explicit non-goals
- Write PROJECT.md brief

AI Usage: 30%
- Use Claude for brainstorming features
- Ask for similar project examples
- Get scope validation feedback
```

**Phase 2: Specification (3-4 hours)**
```
Activities:
- Choose tech stack (React, Node, etc.)
- Design database schema
- Break features into tasks
- Order tasks by dependencies
- Write PLAN.md with acceptance criteria

AI Usage: 50%
- Generate task breakdowns
- Review architecture decisions
- Identify edge cases to handle
```

**Phase 3: Implementation (8-10 hours)**
```
Activities:
- Set up project scaffolding
- Implement OAuth flow
- Build GitHub API integration
- Create dashboard UI
- Add goal tracking feature
- Connect frontend to backend

AI Usage: 70%
- Copilot for boilerplate
- Claude for complex logic
- AI-generated components
- Human reviews and refinements
```

**Phase 4: Polish & Deploy (3-4 hours)**
```
Activities:
- Test all user flows
- Fix bugs and edge cases
- Improve UI polish
- Deploy to Vercel/Railway
- Configure environment variables
- Verify production works

AI Usage: 40%
- Deployment scripts
- Documentation generation
- Bug fix suggestions
```

**Phase 5: Documentation (2-3 hours)**
```
Activities:
- Write comprehensive README
- Add setup instructions
- Create usage guide
- Take screenshots/record demo
- Write reflection on learnings

AI Usage: 60%
- Documentation structure
- Explanation clarity
- Grammar and polish
```

**Pacing Guidance:**

**Week 1:**
- Day 1-2: Goal + Spec (5-7 hours)
- Day 3-5: Core implementation (8-10 hours)
- Day 6-7: Basic features working

**Week 2:**
- Day 1-2: Feature completion + Polish (3-4 hours)
- Day 3-4: Deploy + Debug production (2-3 hours)
- Day 5-6: Documentation + Portfolio (2-3 hours)
- Day 7: Buffer for unexpected issues

**Time-Saving Tips:**

✅ **Use starter templates:** Don't build from scratch
✅ **Copy authentication patterns:** OAuth is well-documented
✅ **Leverage UI libraries:** Use pre-built components
✅ **Batch similar tasks:** Do all API calls together
✅ **Deploy early:** Don't wait until perfect

**Time Traps to Avoid:**

❌ **Scope creep:** Stick to MVP, save enhancements for later
❌ **Perfection:** 80% quality is enough for learning
❌ **Over-engineering:** Simple solutions work fine
❌ **Manual setup:** Use AI to generate boilerplate
❌ **Analysis paralysis:** Make decisions and move forward

**Flex Time Built In:**

- Estimate assumes 2-3 unexpected issues (4-6 hours)
- If ahead of schedule, add polish features
- If behind, cut non-essential features
- Quality barbalances speed with learning

## Live Portfolio Example

### Example Project Walkthrough

Provide a complete walkthrough of a finished capstone project: the initial brief, the PRD created, the agent prompts used, the iteration cycles, and the final deployed result. Show the process, not just the outcome.

### Code Repository Tour

Take readers through the resulting codebase: architectural decisions, key files and their purposes, agent-generated vs human-refined code, and interesting challenges encountered during development.

### Deployed Demo

Showcase the live deployed version: demonstrate functionality, highlight polish details, explain deployment approach, and discuss what makes this portfolio-worthy versus just a working prototype.

### Reflections and Learnings

Share honest reflections from the example project: what went smoothly, where agents struggled and required human intervention, surprises during the process, and takeaways that influenced how the capstone is structured.

## Prompts & Strategy

### Planning Phase Prompts

Provide proven prompts for the project planning phase: initial brainstorming, requirement gathering, technical decision-making, and PRD creation. Show how to use AI to accelerate planning without sacrificing quality.

### Implementation Phase Prompts

Share effective prompts for implementation: feature breakdown, task-level prompts, debugging strategies, and iteration patterns. Include examples of good vs poor prompts and how to refine when results miss the mark.

### Review and Polish Prompts

Offer prompts for quality assurance phase: code review requests, refactoring suggestions, documentation generation, and final polish. How to use AI for critical evaluation of its own work.

### Prompt Sequencing Strategy

Explain how to sequence prompts for maximum effectiveness: what to tackle first, when to parallelize vs serialize, how to handle dependencies, and adapting the sequence when you hit roadblocks.

## Step-by-Step Guide

### Phase 1: Goal Setting

**Objective:** Create clear project brief that guides all future work.

**Step 1: Define the Purpose**

Start with the "why":

**Prompt to Claude:**
```
I want to build a personal developer dashboard that shows my GitHub activity.
What problems could this solve for developers?
What would make it valuable beyond just looking at GitHub directly?
```

**Capture answers like:**
- Aggregated view across multiple repos
- Historical insights GitHub doesn't show
- Personal goal tracking alongside activity
- Quick access to most important data

**Step 2: Research Constraints**

**Technical:**
- What data does GitHub API provide?
- Any rate limits to consider?
- Authentication requirements?

**Prompt to Claude:**
```
What data can I get from the GitHub REST API?
Focus on: commits, pull requests, languages used, contribution frequency.
What are the rate limits and authentication requirements?
```

**Scope:**
- Single  user or multi-user?
- How much historical data?
- Real-time or polling?

**Step 3: Define MVP Features**

Write down **Must Have:**
1. GitHub OAuth authentication
2. Display recent commits (last 30 days)
3. Show PRs opened/merged
4. Language usage stats
5. Personal goal tracker
6. Simple dashboard layout

**Explicitly Out of Scope:**
- Team/org features
- Mobile app
- Real-time notifications
- Advanced analytics
- Integrations beyond GitHub

**Step 4: Set Success Criteria**

**Functional:**
- Can authenticate with GitHub
- Shows accurate commit data
- Goal tracking persists
- Deployed and accessible

**Learning:**
- Used full GSD framework
- Delegated implementation to  AI
- Verified quality at each step
- Documented learnings

**Step 5: Write PROJECT.md**

Create `.gsd/PROJECT.md`:

```markdown
# Personal Developer Dashboard

## Goal
Build a  web app that gives me a personalized view of my GitHub activity
and helps me track development goals.

## Why
- Practice full Agentic AI workflow (ecosystem → tools → GSD → agents → skills)
- Learn OAuth implementation
- Gain experience with REST API integration
- Build something ACTUALLY use
- Create portfolio piece

##Scope

### In Scope (MVP)
1. GitHub authentication (OAuth)
2. Recent activity display (commits, PRs)
3. Coding stats (languages, frequency)
4. Goal tracker with persistence
5. Responsive dashboard UI
6. Deployment to free hosting

### Explicitly Out
- Team features
- Mobile app
- Real-time updates
- Notifications
- Other integrations

## Success Criteria
- [ ] I can log in with GitHub
- [ ] My commits from last 30 days shown
- [ ] Can create and track goals
- [ ]  Works on mobile and desktop
- [ ] Deployed to public URL
- [ ] Followed GSD framework
- [ ] Used AI agents effectively
- [ ] Would show in portfolio

## Technology Choices
- Frontend: React + TypeScript + Tailwind
- Backend: Node.js + Express
- Database: PostgreSQL
- Hosting: Vercel (FE) + Railway (BE)
- APIs: GitHub REST API

## Timeline
- Week 1: Goal, spec, core implementation
- Week 2: Polish, deploy, document
- Total: 18-24 hours over 2 weeks
```

**Checkpoint:**

Before moving to Phase 2, ask:
1. Is my goal clear enough to guide decisions?
2. Is my scope realistic for 20 hours?
3. Can I explain the project value in one sentence?
4. Do I have explicit non-goals to prevent scope creep?

If yes to all → Proceed to Phase 2 Specification

### Phase 2: Specification

**Objective:** Create detailed implementation plan (PLAN.md) with tasks and acceptance criteria.

**Step 1: Technical Architecture Decisions**

**Prompt to Claude:**
```
I'm building a developer dashboard with React/Node/PostgreSQL.

Help me decide:
1. Should I use a monorepo or separate repos for FE/BE?
2. What's the best way to handle GitHub OAuth in 2025?
3. How should I structure my database schema for goals and cached GitHub data?
4. Should I use REST or GraphQL for my own API?
```

**Document decisions:**

```
Architecture Decisions:

1. **Monorepo:** No - separate repos for learning deployment independently
2. **Auth:** GitHub OAuth app with callback to backend, JWT for sessions
3. **Database Schema:**
   - users (github_id, name, avatar_url, access_token)
   - goals (id, user_id, title, description, status, created_at)
   - github_cache (user_id, data_type, content, cached_at)
4. **API Style:** REST - simpler for small project
```

**Step 2: Feature Breakdown into Tasks**

For each MVP feature, break down into implementable tasks:

**Feature: GitHub OAuth Authentication**

Tasks:
1. Register GitHub OAuth app (get client ID/secret)
2. Backend: Create /auth/github route that redirects to GitHub
3. Backend: Create /auth/callback route that exchanges code for token
4. Backend: Store user + token in database
5. Backend: Generate JWT for session
6. Frontend: Add "Login with GitHub" button
7. Frontend: Handle OAuth callback, store JWT
8. Frontend: Add protected routes that check JWT

Acceptance Criteria:
- User clicks button, goes to GitHub authorization
- After approving, user redirected back to dashboard
- JWT stored in localStorage
- Protected routes only accessible when authenticated
- User can log out (JWT cleared)

**Prompt to Copilot:** (Save for Phase 3)
```
Generate a task breakdown for implementing goal tracking:
- User can create a new goal (title + description)
- Goals saved to PostgreSQL database
- User can view all their goals
- User can mark goals as complete
- Goals persist across sessions

Provide task list with acceptance criteria for each.
```

**Step 3: Order Tasks by Dependencies**

**Wave 1 (Can do in parallel):**
- Set up React project with TypeScript + Tailwind
- Set up Node/Express backend
- Set up PostgreSQL database
- Register GitHub OAuth app

**Wave 2 (Depends on Wave 1):**
- Implement OAuth flow
- Create database schema
- Build API for user sessions

**Wave 3 (Depends on Wave 2):**
- Frontend auth UI
- Protected routes
- GitHub API integration

**Wave  4 (Depends on Wave 3):**
- Dashboard components
- Goal tracking feature
- Data visualization

**Wave 5 (Final polish):**
- Responsive design
- Error handling
- Loading states

**Step 4: Identify Risks**

**Potential Issues:**
1. **GitHub API rate limits** → Solution: Cache data, respect limits
2. **OAuth complexity** → Solution: Use well-tested library (passport.js)
3. **Deployment environment variables** → Solution: Document all required env vars
4. **CORS issues** → Solution: Configure CORS properly from start

**Step 5: Write PLAN.md**

Create `.gsd/phases/01-capstone/01-01-PLAN.md`:

```markdown
# Implementation Plan: Developer Dashboard MVP

## Architecture

**Frontend:** React 18 + TypeScript + Tailwind CSS + Vite
**Backend:** Node.js 20 + Express + Prisma ORM
**Database:** PostgreSQL 15
**Auth:** GitHub OAuth 2.0 + JWT sessions
**Hosting:** Vercel (frontend) + Railway (backend + database)

## Phase 1: Project Setup

### Task 1.1: Initialize Frontend
- [ ] Create React + TypeScript project with Vite
- [ ] Install Tailwind CSS
- [ ] Set up basic routing (react-router-dom)
- [ ] Create layout components (Header, Sidebar, Main)

**Acceptance:** Dev server runs, Tailwind styling works, routing navigates between pages

### Task 1.2: Initialize Backend
- [ ] Create Node + Express project
- [ ] Set up TypeScript configuration
- [ ] Install and configure Prisma
- [ ] Create basic API structure (/api/v1 namespace)

**Acceptance:** Server runs on port 3001, responds to health check endpoint

### Task 1.3: Database Setup
- [ ] Define Prisma schema (User, Goal, GitHubCache models)
- [ ] Create initial migration
- [ ] Seed database with test data
- [ ] Verify models via Prisma Studio

**Acceptance:** Database created, migrations run, can CRUD via Prisma Studio

### Task 1.4: OAuth App Registration
- [ ] Create GitHub OAuth app in GitHub settings
- [ ] Note client ID and client secret
- [ ] Set callback URL for local dev
- [ ] Document environment variables needed

**Acceptance:** Have CLIENT_ID, CLIENT_SECRET, CALLBACK_URL documented

## Phase 2: Authentication

### Task 2.1: Backend OAuth Flow
- [ ] Install passport + passport-github2
- [ ] Create /auth/github endpoint (redirects to GitHub)
- [ ] Create /auth/callback endpoint (handles GitHub response)
- [ ] Store user in database if new, fetch if existing
- [ ] Generate JWT with user ID
- [ ] Return JWT to frontend

**Acceptance:** Can navigate to /auth/github, authorize on GitHub, receive JWT in response

### Task 2.2: Frontend Auth UI
- [ ] Create Login page with GitHub button
- [ ] Handle OAuth redirect and callback
- [ ] Store JWT in localStorage
- [ ] Create auth context (React Context API)
- [ ] Add logout functionality

**Acceptance:** User can log in, JWT stored, context provides user  info, can log out

### Task 2.3: Protected Routes
- [ ] Create PrivateRoute wrapper component
- [ ] Check JWT validity before rendering protected views
- [ ] Redirect to login if unauthenticated
- [ ] Add JWT to API request headers

**Acceptance:** Dashboard only accessible when logged in, API requests include auth token

## Phase 3: GitHub Integration

### Task 3.1: GitHub API Service
- [ ] Install @octokit/rest
- [ ] Create GitHub API service class
- [ ] Implement getRecentCommits() method
- [ ] Implement getPullRequests() method
- [ ] Implement getLanguageStats() method
- [ ] Add caching layer (15-minute TTL)

**Acceptance:** Can fetch data from GitHub API using user's token, data cached to reduce API calls

### Task 3.2: Backend API Endpoints
- [ ] GET /api/v1/github/activity (commits + PRs)
- [ ] GET /api/v1/github/stats (languages, frequency)
- [ ] Add error handling for rate limits
- [ ] Return cached data when available

**Acceptance:** Endpoints return correct data, cache works, rate limit errors handled gracefully

## Phase 4: Dashboard UI

### Task 4.1: Activity Feed Component
- [ ] Create CommitCard component
- [ ] Create PullRequestCard component
- [ ] Fetch data from backend API
- [ ] Display loading and error states
- [ ] Style with Tailwind

**Acceptance:** Dashboard shows recent commits and PRs with proper formatting

### Task 4.2: Stats Visualization
- [ ] Install chart library (recharts)
- [ ] Create LanguagePieChart component
- [ ] Create ContributionGraph component
- [ ] Fetch stats from API
- [ ] Handle empty states

**Acceptance:** Charts display correct data, look professional, handle edge cases

## Phase 5: Goal Tracking

### Task 5.1: Goal Backend API
- [ ] POST /api/v1/goals (create goal)
- [ ] GET /api/v1/goals (list goals)
- [ ] PATCH /api/v1/goals/:id (update status)
- [ ] DELETE /api/v1/goals/:id (delete goal)

**Acceptance:** CRUD operations work, goals associated with correct user

### Task 5.2: Goal UI Components
- [ ] Create GoalForm component (create/edit)
- [ ] Create GoalList component
- [ ] Create GoalCard component
- [ ] Add toggle for complete/incomplete
- [ ] Add delete confirmation

**Acceptance:** Can create, view, complete, and delete goals through UI

## Phase 6: Polish

### Task 6.1: Responsive Design
- [ ] Test on mobile, tablet, desktop
- [ ] Fix layout issues
- [ ] Optimize touch targets
- [ ] Ensure readable font sizes

**Acceptance:** Works well on all screen sizes

### Task 6.2: Error Handling
- [ ] Add global error boundary (React)
- [ ] Show user-friendly error messages
- [ ] Handle network failures gracefully
- [ ] Add retry mechanisms

**Acceptance:** App doesn't crash, errors communicated clearly

### Task 6.3: Loading States
- [ ] Add skeleton loaders for data fetching
- [ ] Disable buttons during submission
- [ ] Show progress indicators

**Acceptance:** User always knows when something is loading

## Phase 7: Deployment

### Task 7.1: Backend Deployment (Railway)
- [ ] Create Railway project
- [ ] Add PostgreSQL plugin
- [ ] Configure environment variables
- [ ] Deploy backend
- [ ] Verify database connection
- [ ] Test API endpoints

**Acceptance:** Backend accessible via public URL, database connected

### Task 7.2: Frontend Deployment (Vercel)
- [ ] Connect GitHub repo to Vercel
- [ ] Configure build settings
- [ ] Set environment variables (API URL)
- [ ] Deploy
- [ ] Test production build

**Acceptance:** Frontend accessible via public URL, connects to backend

### Task 7.3: OAuth Callback Update
- [ ] Update GitHub OAuth app callback URL to production
- [ ] Test login flow in production
- [ ] Verify all features work

**Acceptance:** Can log in on production site, all features functional

## Risk Mitigation

| Risk | Impact | Mitigation |
|------|--------|------------|
| GitHub API rate limits | High | Cache aggressively, show user their limit status |
| OAuth callback issues | High | Test locally with ngrok before deploying |
| Database migration problems | Medium | Use Prisma's preview feature, test migrations in dev  |
| CORS errors | Medium | Configure properly from start, test cross-origin early |
| Environment variable mistakes | Low | Document all vars, use .env.example as template |

## Success Criteria

- [ ] All tasks completed with acceptance criteria met
- [ ] Application deployed and accessible
- [ ] No critical bugs
- [ ] Documentation written
- [ ] Learnings captured
```

**Checkpoint:**

Before Phase 3, verify:
1. Every feature broken into specific tasks
2. Each task has clear acceptance criteria
3. Dependencies identified and ordered
4. Risks documented with mitigation plans

If ready → Begin execution in Phase 3

### Phase 3: Implementation

**Objective:** Build the application by delegating tasks to AI agents with human verification.

**Mindset Shift:**

```
Old Way:
"I need to write every line myself."

Agentic Way:
"AI handles implementation, I handle judgment."

My Role:
- Provide clear task context
- Verify outputs meet acceptance criteria
- Refine when AI misses the mark
- Make architectural decisions
- Ensure quality and security
```

**Execution Pattern:**

For each task in PLAN.md:

**1. Context Priming**
**2. Task Delegation**
**3. Output Verification**
**4. Acceptance or Iteration**
**5. Commit and Proceed**

---

**Example: Task 1.1 - Initialize Frontend**

**Step 1: Context Priming**

**Prompt to Copilot Chat:**
```
I'm starting a new React TypeScript project for a developer dashboard.

Tech stack:
- React 18
- TypeScript
- Tailwind CSS
- Vite (build tool)
- React Router for navigation

I need to:
1. Initialize the project with Vite
2. Install and configure Tailwind
3. Set up react-router-dom
4. Create basic layout components (Header, Main, Sidebar)

What's the command sequence to get this set up correctly?
```

**Step 2: Task Delegation**

Copilot provides commands:
```bash
npm create vite@latest dev-dashboard -- --template react-ts
cd dev-dashboard
npm install
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
npm install react-router-dom
```

And Tailwind config changes:

**Now prompt Copilot in the codebase:**
```
Create the basic layout structure:

1. Update App.tsx to use React Router with routes:
   - / → Dashboard
   - /goals → Goals
   - /login → Login

2. Create components/Layout.tsx with:
   - Header (app title, logout button)
   - Sidebar (navigation links)
   - Main content area

3. Create placeholder page components:
   - Dashboard.tsx
   - Goals.tsx
   - Login.tsx

4. Configure Tailwind with a nice color scheme
```

**Step 3: Output Verification**

Copilot generates files. **Your job:**

✓ **Run the dev server:**
```bash
npm run dev
```

✓ **Check acceptance criteria:**
- [ ] Dev server runs without errors?
- [ ] Can navigate between pages?
- [ ] Tailwind styles applying (test with border, padding)?
- [ ] Layout looks reasonable?

✓ **Test edge cases:**
- Navigate to non-existent route → Should show 404
- Resize browser → Layout should adjust

**Step 4: Acceptance or Iteration**

**If pass:** Move to Step 5

**If fail:** Provide specific feedback:

**Example issue:** "Sidebar not showing on mobile"

**Prompt:**
```
The sidebar is hidden on mobile screens. Update Layout.tsx to:
- Hide sidebar on screens < 768px
- Add hamburger menu button that toggles sidebar
- Sidebar should slide in from left when open on mobile
```

Iterate until acceptance criteria met.

**Step 5: Commit and Proceed**

```bash
git add .
git commit -m "feat(01-01): initialize frontend with React + Tailwind

- Created Vite project with TypeScript
- Configured Tailwind CSS
- Set up React Router with 3 routes
- Built Layout component with Header/Sidebar
- Created placeholder page components
"
```

**Move to next task (Task 1.2: Initialize Backend)**

---

**Example: Task 2.1 - Backend OAuth Flow**

**Step 1: Context Priming**

**Prompt to Claude (architectural):**
```
I'm implementing GitHub OAuth in an Express backend.

Goals:
1. User clicks "Login with GitHub" on frontend
2. Backend redirects to GitHub authorization
3. GitHub redirects back to /auth/callback with code
4. Backend exchanges code for access token
5. Store user in PostgreSQL (or fetch if exists)
6. Return JWT to frontend

Questions:
1. Should I use passport.js or implement OAuth manually?
2. What's the best way to handle the token exchange?
3. How do I generate a secure JWT?
4. What user data should I store?

Provide recommendation with rationale.
```

**Claude provides architectural guidance.**

**Step 2: Task Delegation**

**Prompt to Copilot in backend codebase:**
```
Implement GitHub OAuth flow in Express:

1. Install required packages:
   - passport
   - passport-github2
   - jsonwebtoken
   - express-session

2. Create src/auth/github.strategy.ts:
   - Configure GitHubStrategy with CLIENT_ID, CLIENT_SECRET, CALLBACK_URL
   - On successful auth, find or create user in database
   - User model fields: github_id, username, avatar_url, access_token

3. Create src/routes/auth.ts:
   - GET /auth/github → initiates OAuth
   - GET /auth/callback → handles GitHub callback
   - On success: generate JWT with user ID, return to frontend

4. Create src/utils/jwt.ts:
   - Function to generate JWT (expires in 7 days)
   - Function to verify JWT
   - Use RS256 algorithm with secret from env

5. Add authentication middleware src/middleware/auth.ts:
   - Checks JWT in Authorization header
   - Adds user to req.user if valid
   - Returns 401 if missing/invalid

Use TypeScript, follow Express best practices, include error handling.
```

**Step 3: Output Verification**

✓ **Test OAuth initiation:**
```bash
curl http://localhost:3001/auth/github
# Should redirect to github.com/login/oauth/authorize...
```

✓ **Test callback** (use Postman or browser):
- Manually go through GitHub authorization
- Check callback  returns JWT
- Verify user created in database

✓ **Test JWT verification:**
```bash
curl -H "Authorization: Bearer <jwt>" http://localhost:3001/api/v1/user
# Should return user data
```

✓ **Security check:**
- CLIENT_SECRET not hardcoded
- JWT secret strong and in env
- No sensitive data in JWT payload
- Token expires appropriately

**Step 4: Acceptance or Iteration**

**Common issues:**

**Issue:** "Callback URL mismatch"
**Fix prompt:**
```
Getting OAuth callback mismatch error. Check:
1. CALLBACK_URL in .env matches GitHub OAuth app setting
2. For local dev, should be http://localhost:3001/auth/callback
3. Make sure no typos in route definition
```

**Issue:** "User not saving to database"
**Fix prompt:**
```
User not persisting. Debug:
1. Check Prisma client connection
2. Verify User model in schema.prisma
3. Add console.log before/after database save
4. Check for database errors
```

**Step 5: Commit and Proceed**

```bash
git add .
git commit -m "feat(01-01): implement GitHub OAuth flow

- Configured passport with GitHub strategy
- Created auth routes for initiation and callback
- Store user data in PostgreSQL via Prisma
- Generate JWT for session management
- Added auth middleware for protected routes
"
```

---

**Handling Deviations from Plan**

**Scenario:** GitHub API returns different data structure than expected

**Response:**
1. **Don't panic** - plans evolve during execution
2. **Document the reality:**
   ```
   Note: GitHub API returns `commit.commit.message`
   not `commit.message` as assumed in plan.
   Updated data mapping accordingly.
   ```
3. **Update PLAN.md** if assumption was wrong
4. **Keep moving** - this is normal

**Scenario:** Task takes 2x longer than estimated

**Response:**
1. **Assess why:**
   - Underestimated complexity
   - Hit unexpected blocker
   - AI struggling with this type of task

2. **Adjust expectations:**
   - Update timeline
   - Consider simplifying feature
   - Ask for help on complex parts

3. **Learn for next time:**
   - Note what was underestimated
   - Build in more buffer

**Scenario:** AI generates buggy code

**Response:**
1. **Provide error output explicitly:**
   ```
   This code has a bug. When I run it, I get:
   
   TypeError: Cannot read property 'map' of undefined
   at Dashboard.tsx:23
   
   The issue is that `commits` is undefined when the API is still loading.
   Add a loading state check before trying to map over commits.
   ```

2. **Be specific about the fix needed**
3. **Verify the fix works**

---

**Maintaining Momentum**

**Daily Progress Ritual:**

**Start of session:**
1. Review PLAN.md - what's next?
2. Check last commit - where did I leave off?
3. Set 2-hour goal - what will I complete today?

**During work:**
- Complete one task before switching
- Commit after each task
- Take breaks between tasks

**End of session:**
1. Commit any WIP
2. Update PLAN.md checkboxes
3. Note any blockers or decisions needed
4. Review progress against timeline

**Overcoming Obstacles:**

**Blocked on a decision:**
→ Prompt Claude to discuss trade-offs, make a decision, move forward

**Stuck on implementation:**
→ Simplify the task, get something working, refine later

**Losing motivation:**
→ Deploy what you have so far, seeing it live is energizing

**Scope feeling too big:**
→ Cut a non-essential feature, maintain momentum on core value

**AI not understanding:**
→ Show code examples of similar working code, point to specific files

---

**Phase 3 Completion:**

You're done with implementation when:
- [ ] All tasks in PLAN.md completed
- [ ] Acceptance criteria met for each task
- [ ] Application runs without critical bugs
- [ ] Core user flows work end-to-end

**Now proceed to Phase 4: Iteration & Polish**

### Phase 4: Iteration

**Objective:** Test, improve, and polish the application to portfolio quality.

**The Polish Mindset:**

```
MVP = Works
Polished = Demonstrable

Difference:
- Handles edge cases gracefully
- Looks professional
- Feels responsive
- Communicates clearly to users
```

**Testing Methodology:**

**1. Happy Path Testing**

 Test primary user flows:

**Flow 1: First-time user**
```
1. Visit site → See login page
2. Click "Login with GitHub" → Redirect to GitHub
3. Authorize app → Redirect to dashboard
4. See GitHub activity → Data displays correctly
5. Create a goal → Goal appears in list
6. Mark goal complete  → UI updates
7. Refresh page → Still logged in, goals persist
8. Logout → Redirected to login
```

**Document issues:**
- [ ] Step 3: Dashboard empty state shows "undefined" - need better handling
- [ ] Step 5: Goal form doesn't clear after submit
- [ ] Step 7: Takes 5 seconds to load

**2. Edge Case Testing**

Test failure scenarios:

**Edge Cases:**
```
- GitHub OAuth denied → How does app handle?
- API rate limit exceeded → What does user see?
- No commits in last 30 days → Empty state?
- Extremely long goal title → Does UI break?
- Network offline → Error message shown?
- Invalid JWT (expired) → Redirect to login?
```

**For each issue, create fix task:**

**Issue:** App crashes when no commits exist

**Fix prompt to Copilot:**
```
In Dashboard.tsx, the app crashes when `commits` array is empty.

Add an empty state:
- Show friendly message: "No recent commits found. Start coding!"
- Include an illustration or icon
- Suggest visiting GitHub to check connection

Only render CommitList when commits.length > 0.
```

**3. User Experience Testing**

Put yourself in user's shoes:

**UX Checklist:**
- [ ] **Clear feedback:** Does user know when something is loading?
- [ ] **Error clarity:** Are errors explained in plain language?
- [ ] **Visual hierarchy:** Is most important info prominent?
- [ ] **Touch targets:** Are buttons easy to tap on mobile?
- [ ] **Consistency:** Do similar actions behave similarly?
- [ ] **Performance perception:** Does it feel fast (even if not)?

**Example UX improvement:**

**Before:**
```jsx
<button onClick={createGoal}>Create</button>
// Clicking does nothing visible for 2 seconds
```

**Prompt:**
```
Improve the goal creation UX:

1. Add loading state to button:
   - Disable button while saving
   - Show spinner icon
   - Change text to "Creating..."

2. Show success feedback:
   - Brief toast notification "Goal created!"
   - Form clears
   - New goal appears in list with highlight animation

3. Handle errors:
   - Show error toast if creation fails
   - Keep form data so user doesn't lose input
   - Suggest retry
```

**After:**
```jsx
<button onClick={createGoal} disabled={isLoading}>
  {isLoading ? (
    <><Spinner /> Creating...</>
  ) : "Create Goal"}
</button>
```

**4. Visual Polish**

**Prompt to Claude:**
```
I want to improve the visual design of my dashboard.

Current state:
- Basic Tailwind default styles
- Feels functional but bland
- Want it to look portfolio-worthy

Suggestions for:
1. Color scheme (prefer modern, professional)
2. Typography hierarchy
3. Card/component styling
4. Subtle animations for delight
5. Dark mode (optional but cool)

Provide specific Tailwind classes, not just concepts.
```

**Apply improvements systematically:**

**Before:**
```tsx
<div className="p-4">
  <h1>Dashboard</h1>
  <div>Commits...</div>
</div>
```

**After:**
```tsx
<div className="min-h-screen bg-gradient-to-br from-slate-50 to-slate-100">
  <h1 className="text-3xl font-bold text-slate-900 mb-6">
    Your Developer Dashboard
  </h1>
  <div className="grid gap-4 md:grid-cols-2">
    {/* Polished commit cards */}
  </div>
</div>
```

**5. Performance Optimization**

**Quick wins to prompt AI for:**

**a) Frontend optimization:**
```
Optimize Dashboard.tsx performance:

1. Add React.memo to CommitCard component (prevent unnecessary re-renders)
2. Use useMemo for expensive calculations (like filtering commits)
3. Implement virtual scrolling if >100 items (react-window)
4. Lazy load chart library only when Stats tab opened
```

**b) Backend optimization:**
```
Optimize GitHub API calls:

1. Implement aggressive caching:
   - Cache user activity for 15 minutes
   - Use Redis if available, otherwise in-memory
2. Batch related API calls
3. Only fetch what's displayed (pagination)
```

**6. Mobile Responsiveness**

**Test on:** Chrome DevTools device emulation

**Checklist:**
- [ ] Typography readable (min 16px body text)
- [ ] Touch targets 44x44px minimum
- [ ] No horizontal scroll
- [ ] Navigation accessible
- [ ] Forms usable (keyboards, select)

**Common fixes:**

**Issue:** Sidebar covers content on mobile

**Prompt:**
```
Fix mobile sidebar:
- Hidden by default on screens < 768px
- Hamburger menu button in header
- Sidebar slides in from left when opened
- Click outside or X button to close
- Smooth animations with Tailwind transitions
```

**7. Accessibility Quick Wins**

**Prompt to  Copilot:**
```
Improve accessibility:

1. Add proper ARIA labels to interactive elements
2. Ensure  sufficient color contrast (WCAG AA)
3. Add focus visible states to all focusable elements
4. Use semantic HTML (not  just divs)
5. Add alt text to any images/icons
6. Ensure keyboard navigation works

Scan the codebase and suggest specific improvements.
```

**Iteration Cycle:**

```
1. Test → Find 3-5 issues
2. Prioritize by impact (user-facing  > internal)
3. Prompt AI to fix (one at a time)
4. Verify fix works
5. Commit improvements
6. Repeat until satisfied
```

**When to Stop Iterating:**

You could polish forever. Stop when:
- [ ] All critical bugs fixed
- [ ] Happy path works flawlessly
- [ ] Common edge cases handled
- [ ] Looks professional
- [ ] You're proud to show it

**Reality check:** 80% polished is portfolio-ready. Don't pursue perfection.

**Proceed to Phase 5: Deployment**

### Phase 5: Deployment & Documentation

**Objective:** Ship application to production and create portfolio-quality documentation.

**Part A: Deployment**

**Pre-Deployment Checklist:**

**Security:**
- [ ] No API keys or secrets in code
- [ ] All secrets in environment variables
- [ ] CORS configured properly
- [ ] JWT secret is strong
- [ ] Rate limiting implemented
- [ ] SQL injection prevention (using ORMs correctly)

**Configuration:**
- [ ] Production API URLs set
- [ ] Database connection string ready
- [ ] OAuth callback URLs updated
- [ ] Build process tested locally
- [ ] Environment variables documented

---

**Deploying Backend (Railway)**

**Step 1: Create Railway Project**

1. Go to railway.app, sign in with GitHub
2. Click "New Project"
3. Select "Deploy from GitHub repo"
4. Choose your backend repository
5. Add PostgreSQL database (click "+ New" → "Database" → "PostgreSQL")

**Step 2: Configure Environment Variables**

In Railway dashboard, add variables:

```
DATABASE_URL=${{Postgres.DATABASE_URL}}  # Railway auto-fills
GITHUB_CLIENT_ID=<from GitHub OAuth app>
GITHUB_CLIENT_SECRET=<from GitHub OAuth app>
GITHUB_CALLBACK_URL=https://your-app.railway.app/auth/callback
JWT_SECRET=<generate strong random string>
NODE_ENV=production
PORT=80
```

**Step 3: Deploy**

Railway auto-deploys on push to main. Manually trigger:
- Click "Deploy" button
- Watch build logs
- Wait for "Success" status

**Step 4: Run Database Migrations**

In Railway, go to your backend service:
- Settings → Custom Start Command
- Set to: `npx prisma migrate deploy && node dist/index.js`

Or run migration manually:
- Click "+ New" → "Empty Service"
- Add command: `npx prisma migrate deploy`
- Run once, then delete service

**Step 5: Verify Backend**

```bash
curl https://your-backend.railway.app/health
# Should return 200 OK
```

Test critical endpoints:
- GET /health → 200
- GET /auth/github → Redirects to GitHub
- GET /api/v1/user (with JWT) → Returns user data

---

**Deploying Frontend (Vercel)**

**Step 1: Prepare Frontend**

Update API URL:

**`.env.production`:**
```
VITE_API_URL=https://your-backend.railway.app
```

Or use environment variable in Vercel:
```tsx
const API_URL = import.meta.env.VITE_API_URL || 'http://localhost:3001';
```

**Step 2: Deploy to Vercel**

1. Go to vercel.com, sign in with GitHub
2. Click "Add New" → "Project"
3. Import your frontend repository
4. Vercel auto-detects Vite settings
5. Add environment variables:
   - `VITE_API_URL` → Your Railway backend URL
6. Click "Deploy"

**Step 3: Configure Custom Domain** (Optional)

- In Vercel project settings → "Domains"
- Add your custom domain
- Update DNS records as instructed

**Step 4: Verify Frontend**

Visit your Vercel URL:
- Home page loads
- Can click "Login with GitHub"
- After auth, dashboard shows data
- All features functional

---

**Update GitHub OAuth App**

**Critical:** Update callback URL to production!

1. Go to GitHub → Settings → Developer settings → OAuth Apps
2. Select your app
3. Update:
   - **Homepage URL:** `https://your-app.vercel.app`
   - **Callback URL:** `https://your-backend.railway.app/auth/callback`
4. Save

**Test login flow in production immediately after update.**

---

**Troubleshooting Common Deployment Issues:**

**Issue:** "CORS error in production"

**Fix:**
```typescript
// backend/src/index.ts
import cors from 'cors';

app.use(cors({
  origin: process.env.FRONTEND_URL || 'https://your-app.vercel.app',
  credentials: true,
}));
```

**Issue:** "Database connection failed"

**Fix:**
- Check `DATABASE_URL` environment variable
- Ensure Prisma migrations ran
- Verify PostgreSQL service is running (Railway dashboard)
- Check connection string format

**Issue:** "OAuth callback URL mismatch"

**Fix:**
- Verify GitHub OAuth app callback matches Railway URL exactly
- Check for http vs https
- Check for typos
- Look at error message for expected URL

**Issue:** "Environment variables not loading"

**Fix:**
- Restart services after adding env vars (Railway/Vercel)
- Check for typos in variable names
- Verify build command includes env variables

---

**Part B: Documentation**

**Your README.md is marketing + instructions. Make it compelling.**

**README Structure:**

````markdown
# 📊 Developer Dashboard

> Track your GitHub activity and development goals in one beautiful dashboard

![Dashboard Screenshot](./docs/screenshot.png)

👉 **[Live Demo](https://your-app.vercel.app)**

## What It Does

Developer Dashboard helps you:
- ✅ Visualize your GitHub activity (commits, PRs, languages)
- ✅ Track personal coding goals
- ✅ See your development patterns over time
- ✅ Stay motivated with progress insights

**Built to learn Agentic AI development:** This project showcases the complete AI-assisted development workflow from goal setting through deployment.

## Features

### 🔒 GitHub OAuth Authentication
Secure login with your GitHub account. No passwords to remember.

### 📊 Activity Dashboard
- Recent commits from all your repositories
- Pull request activity (opened, merged, reviewed)
- Language usage breakdown
- Contribution frequency graphs

### 🎯 Goal Tracking
- Set development goals ("Learn TypeScript", "Contribute to open source")
- Track completion status
- Persistent storage
- Motivation through visibility

### 📱 Responsive Design
Works beautifully on desktop, tablet, and mobile.

## Tech Stack

**Frontend:**
- React 18 + TypeScript
- Tailwind CSS for styling
- Vite for blazing fast builds
- React Router for navigation
- Recharts for data visualization

**Backend:**
- Node.js + Express
- Prisma ORM for database
- PostgreSQL database
- passport.js for GitHub OAuth
- JWT for session management

**Deployment:**
- Frontend: Vercel
- Backend: Railway
- Database: Railway PostgreSQL

## Getting Started

### Prerequisites

- Node.js 20+
- PostgreSQL 15+
- GitHub account
- GitHub OAuth App (instructions below)

### 1. Clone & Install

```bash
# Clone
git clone https://github.com/yourusername/dev-dashboard.git
cd dev-dashboard

# Install frontend
cd frontend
npm install

# Install backend
cd ../backend
npm install
```

### 2. Create GitHub OAuth App

1. Go to GitHub → Settings → Developer settings → OAuth Apps → New OAuth App
2. Fill in:
   - **Application name:** Dev Dashboard (Local)
   - **Homepage URL:** `http://localhost:5173`
   - **Callback URL:** `http://localhost:3001/auth/callback`
3. Save and note your **Client ID** and **Client Secret**

### 3. Configure Environment Variables

**Backend (.env):**
```env
DATABASE_URL="postgresql://user:password@localhost:5432/devdashboard"
GITHUB_CLIENT_ID=your_client_id
GITHUB_CLIENT_SECRET=your_client_secret
GITHUB_CALLBACK_URL=http://localhost:3001/auth/callback
JWT_SECRET=your_super_secret_jwt_key_change_this
NODE_ENV=development
PORT=3001
```

**Frontend (.env):**
```env
VITE_API_URL=http://localhost:3001
```

### 4. Set Up Database

```bash
cd backend
npx prisma migrate dev
npx prisma generate
```

### 5. Run Development Servers

**Terminal 1 (Backend):**
```bash
cd backend
npm run dev
# Runs on http://localhost:3001
```

**Terminal 2 (Frontend):**
```bash
cd frontend
npm run dev
# Runs on http://localhost:5173
```

### 6. Open Application

Visit `http://localhost:5173` and click "Login with GitHub"

## Project Structure

```
dev-dashboard/
├── frontend/
│   ├── src/
│   │   ├── components/      # React components
│   │   ├── pages/           # Page components
│   │   ├── context/         # Auth context
│   │   ├── services/        # API calls
│   │   ├── utils/           # Helper functions
│   │   └── App.tsx          # Main app component
│   ├── package.json
│   └── vite.config.ts
├── backend/
│   ├── src/
│   │   ├── routes/          # Express routes
│   │   ├── middleware/      # Auth middleware
│   │   ├── services/        # Business logic
│   │   └── index.ts         # Server entry
│   ├── prisma/
│   │   └── schema.prisma    # Database schema
│   └── package.json
└── README.md
```

## API Endpoints

### Authentication
- `GET /auth/github` - Initiate GitHub OAuth
- `GET /auth/callback` - OAuth callback handler
- `POST /auth/logout` - Clear session

### User
- `GET /api/v1/user` - Get current user
- `GET /api/v1/github/activity` - Get GitHub activity
- `GET /api/v1/github/stats` - Get coding stats

### Goals
- `GET /api/v1/goals` - List goals
- `POST /api/v1/goals` - Create goal
- `PATCH /api/v1/goals/:id` - Update goal
- `DELETE /api/v1/goals/:id` - Delete goal

## Learnings & Reflections

**What Went Well:**
- AI agents (Claude + Copilot) handled 70% of implementation
- GSD framework kept me focused on goal
- OAuth was easier than expected with AI assistance
- Deployment went smoothly

**Challenges:**
- GitHub API rate limiting required caching strategy
- Initial OAuth callback had URL mismatch issues
- Responsive design needed more iteration than planned
- TypeScript types for Prisma required manual fixes

**Key Takeaways:**
1. **AI excels at boilerplate:** Setup, config, standard patterns
2. **Human judgment still critical:** Architecture, UX, security review
3. **Iteration is essential:** First AI output rarely perfect
4. **Documentation matters:** Future me will thank present me
5. **Scope discipline:** Saying no to features kept project completable

**Time Breakdown:**
- Planning: 3 hours
- Implementation: 10 hours (70% AI-generated)
- Polish: 4 hours
- Deployment: 2 hours
- Documentation: 3 hours
- **Total: 22 hours over 2 weeks**

## Future Enhancements

*Not included in MVP, but ideas for iteration:*

- [ ] Support for multiple GitHub accounts
- [ ] GitLab / Bitbucket integration
- [ ] Streaks and achievements system
- [ ] Weekly email summaries
- [ ] Team/org dashboards
- [ ] Dark mode
- [ ] Export data as PDF/CSV
- [ ] Mobile apps (React Native)

## License

MIT - feel free to use this project as a learning resource!

## Contributing

This is a personal learning project, but feedback and suggestions welcome! Open an issue or PR.

## Acknowledgments

- Built following the [Agentic AI Learning Pathway](link)
- AI assistance from GitHub Copilot and Claude
- Inspired by [WakaTime](https://wakatime.com) and [GitHub Skyline](https://skyline.github.com)

---

**Built with ❤️ and 🤖 AI assistance**
````

---

**Portfolio Presentation Tips:**

**When sharing this project:**

1. **Lead with the demo link** - Show, don't just tell
2. **Explain the "why"** - Not just what it does, why you built it
3. **Highlight the tech stack** - Shows breadth of skills
4. **Be honest about AI assistance** - It's a strength, not cheating
5. **Share learnings** - Reflection shows growth mindset

**Example intro statement:**
> "I built a developer dashboard that aggregates GitHub activity and tracks personal coding goals. 
> The project demonstrates full-stack development with React, Node.js, and PostgreSQL, plus experience with OAuth, REST APIs, and cloud deployment. 
> I used AI assistants (Copilot + Claude) for ~70% of the implementation, showcasing my ability to effectively delegate to AI agents while maintaining quality through human code review. 
> Completed in 22 hours over 2 weeks using the GSD (Goal → Spec → Deliver) framework."

---

**Phase 5 Complete!**

You now have:
- [ ] Application deployed to production
- [ ] Accessible via public URL
- [ ] Comprehensive README documentation
- [ ] Portfolio-ready presentation

**Congratulations!** 🎉 You've shipped a complete project using Agentic AI development practices.

**Final Step:** Reflect on your journey and capture learnings in a blog post or personal notes.

### Phase 6: Portfolio Documentation

Guide creating compelling portfolio documentation: writing project narrative, creating visual demos (screenshots, gifs, or video), documenting technical decisions and learnings, and positioning the work for audience (employers, clients, community).

## PRD Template

### Capstone PRD Structure

Provide a PRD template specifically for the capstone project: sections to include, level of detail appropriate for agent execution, and placeholders that guide you through creating a complete specification.

### Example PRD

Include a complete example PRD for a similar-scope project: shows good practices in action, provides a model to reference when stuck, and illustrates the level of detail that makes agent execution successful.

### Customization Guide

Explain how to adapt the template for variations of the capstone project: scaling scope up or down, adjusting for your skill level and interests, incorporating specific technologies you want to learn, and maintaining the learning objectives while personalizing the project.

### PRD Review Checklist

Provide a checklist for validating your PRD before implementation: completeness checks, clarity assessment, agent-readability validation, scope verification, and success criteria sufficiency.

## Resources

### "Building in Public" Guide by Indie Hackers
- **Type:** Article + Community
- **Duration/Length:** 25 min read
- **Level:** Beginner
- **Why this matters:** Learn to document your capstone project journey, creating compelling portfolio narrative
- **Link:** [Indie Hackers](https://www.indiehackers.com/)

### GitHub Project Showcase Best Practices
- **Type:** Documentation Guide
- **Duration/Length:** 15 min read
- **Level:** Beginner to Intermediate
- **Why this matters:** How to present your capstone project on GitHub with README, demos, and documentation that impresses
- **Link:** [GitHub Docs](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes)

### PRD Template from Atlassian
- **Type:** Template + Guide
- **Duration/Length:** 20 min read
- **Level:** Beginner
- **Why this matters:** Downloadable PRD template you can adapt for capstone planning phase
- **Link:** [Atlassian Templates](https://www.atlassian.com/software/confluence/templates)

### "Show Your Work" by Austin Kleon
- **Type:** Book Summary
- **Duration/Length:** 30 min read
- **Level:** Beginner
- **Why this matters:** Principles for documenting creative process - directly applicable to capstone portfolio documentation
- **Link:** Available at major book retailers

### Vercel/Netlify Deployment Guides
- **Type:** Documentation
- **Duration/Length:** 20 min read
- **Level:** Beginner
- **Why this matters:** Step-by-step guides for deploying capstone projects with free hosting
- **Link:** [Vercel Docs](https://vercel.com/docs) | [Netlify Docs](https://docs.netlify.com/)

### Dev.to Portfolio Project Showcases
- **Type:** Community Examples
- **Duration/Length:** 1+ hour browsing
- **Level:** All levels
- **Why this matters:** See how other developers present their portfolio projects - learn from great examples
- **Link:** [Dev.to #showdev tag](https://dev.to/t/showdev)

## Navigation

**[← Previous: Skills & Packages](../05-skills/README.md)**
