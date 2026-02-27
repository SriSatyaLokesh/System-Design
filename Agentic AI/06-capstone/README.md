> [!NOTE]
> **📍 Current Location:** [Pathway Home](../README.md) → 6. Capstone  
> **📊 Progress:** Section 6 of 6 (Final Section!) | ⏱️ Estimated time: 45 minutes planning + 12-28 hours execution  
> **Prerequisites:** All previous sections — This integrates ecosystem knowledge, tool proficiency, GSD methodology, agent delegation, and skill utilization

---

# 6. Capstone Project

## Table of Contents

- [Overview](#overview)
- [Project Brief](#project-brief)
- [Live Portfolio Example](#live-portfolio-example)
- [Prompts & Strategy](#prompts--strategy)
- [Step-by-Step Guide](#step-by-step-guide)
- [PRD Template](#prd-template)
- [Resources](#resources)
- [What's Next?](#whats-next)

## Overview

The capstone project ties together everything you've learned—ecosystem understanding, tool proficiency, GSD methodology, agent delegation, and skill utilization—into a complete end-to-end project that demonstrates AI-assisted development mastery.

This section provides a concrete, actionable project that results in a real portfolio piece you can showcase. Rather than a toy example, you'll build something production-ready while practicing the workflow patterns that professional AI-assisted developers use daily.

By completing the capstone, you'll have both a tangible outcome (a deployed project) and deep confidence in your ability to leverage AI for real development work, ready to apply these skills to your own projects and professional goals.

## Project Brief

### Choose Your Capstone

Pick one project that aligns with your interests and learning goals. All three exercise the complete Agentic AI workflow while producing portfolio-worthy results.

| Project | Tech Stack | Difficulty | Time | Best For |
|---------|------------|------------|------|----------|
| **[Option A](#option-a-dynamic-developer-portfolio)** | HTML/CSS/Vanilla JS | ⭐⭐ Beginner | 12-16 hours | Frontend focus, no backend needed |
| **[Option B](#option-b-personal-developer-dashboard)** | React + Node + PostgreSQL | ⭐⭐⭐ Intermediate | 18-24 hours | Full-stack experience |
| **[Option C](#option-c-n8n-mcp-automation-project)** | n8n + MCP Protocol | ⭐⭐⭐⭐ Advanced | 20-28 hours | Workflow automation, AI integration |

---

### Option A: Dynamic Developer Portfolio

**Project:** Build a modern, interactive portfolio website using vanilla JavaScript and public libraries.

**Reference Example:** [SriSatyaLokesh Portfolio](https://srisatyalokesh.github.io/) ([GitHub](https://github.com/SriSatyaLokesh/SriSatyaLokesh.github.io))

**Why This Project:**

✅ **Beginner-Friendly:**
- No framework complexity (React, Vue, etc.)
- Pure HTML/CSS/JavaScript fundamentals
- Free hosting on GitHub Pages
- Immediate visual results

✅ **Portfolio Essential:**
- Every developer needs a portfolio
- Showcases your work effectively
- Demonstrates design + code skills
- Actually useful after completion

✅ **AI-Assisted Learning:**
- Practice prompt engineering for UI/UX
- Learn to iterate on design with AI
- Experience AI handling vanilla JS (often trickier than frameworks)
- Build confidence without framework overhead

**Core Features:**

**MVP (Minimum Viable Product):**
1. **Hero Section:** Name, title, brief intro, social links
2. **About Section:** Bio, skills, technologies
3. **Projects Showcase:** Cards with images, descriptions, links
4. **Contact Section:** Email, social media, contact form
5. **Responsive Design:** Mobile-first, works on all devices
6. **Smooth Animations:** Scroll effects, hover states, transitions

**What You'll Build:**
```
Tech Stack:
- HTML5 (semantic markup)
- CSS3 (Grid, Flexbox, animations)
- Vanilla JavaScript (DOM manipulation, events)
- Optional libraries: AOS (animations), Typed.js (typing effect)
- GitHub Pages (hosting)

Features:
- Dynamic content loading from JSON
- Smooth scroll navigation
- Animated skill progress bars
- Project filtering by category
- Contact form with validation
- Dark/light theme toggle
- Responsive hamburger menu
```

**Scope Boundaries:**

**In Scope:**
+ Single-page responsive design
+ Dynamic content (JSON-driven)
+ Smooth animations and interactions
+ GitHub Pages deployment
+ SEO basics (meta tags, semantic HTML)
+ Performance optimization

**Out of Scope:**
- Backend/database (static site)
- User authentication
- Content management system
- Blog functionality (keep it simple)
- Complex state management

**Why Vanilla JS Instead of React?**

1. **Fundamentals First:** Understand DOM, events, async before frameworks
2. **AI Practice:** AI must think more carefully without framework abstractions
3. **Performance:** Faster load times, no bundle overhead
4. **Simplicity:** Deploy straight to GitHub Pages, no build process (or simple one)
5. **Interview Prep:** Many coding interviews test vanilla JS

**Time Estimate:**
```
Phase 1: Goal & Spec (1-2 hours)
Phase 2: HTML Structure & Content (2-3 hours)
Phase 3: CSS Styling & Responsive (3-4 hours)
Phase 4: JavaScript Interactivity (3-4 hours)
Phase 5: Polish & Deploy (2-3 hours)

Total: 12-16 hours over 1 week
```

**Success Criteria:**

✓ **Functional:**
- All sections display correctly
- Navigation works smoothly
- Contact form validates input
- Responsive on mobile/tablet/desktop
- Fast load time (<2 seconds)

✓ **Visual:**
- Professional, clean design
- Consistent color scheme
- Readable typography
- Smooth animations (not overdone)
- No layout shifts or bugs

✓ **Portfolio-Ready:**
- Showcases your best projects
- Clear call-to-action (hire me, contact)
- Professional presentation
- Live on public URL

**Sample Projects to Feature:**
- This portfolio itself (meta!)
- Projects from earlier in the pathway
- Contributions to open source
- Personal experiments
- Coursework highlights (if impressive)

---

### Option B: Personal Developer Dashboard

**Project:** A web application that aggregates your development activity and provides insights.

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

---

### Option C: n8n-MCP Automation Project

**Project:** Build an intelligent workflow automation system using n8n and Model Context Protocol (MCP).

**Why This Project:**

✅ **Cutting-Edge Technology:**
- MCP is the emerging standard for AI-tool integration
- n8n is a powerful no-code/low-code automation platform
- Combines AI agents with real-world automation
- Future-focused skill set

✅ **Real-World Impact:**
- Automate actual workflows you use daily
- Integrate multiple services (GitHub, Slack, Google, etc.)
- Add AI intelligence to business processes
- Practical productivity enhancement

✅ **Advanced AI Skills:**
- Implement MCP servers for custom functionality
- Design multi-step AI-powered workflows
- Handle complex data transformations
- Practice agent orchestration patterns

**Core Features:**

**MVP (Minimum Viable Product):**
1. **MCP Server:** Custom protocol server exposing tools/resources
2. **n8n Workflows:** 2-3 automation workflows using your MCP server
3. **AI Integration:** Claude/GPT connected via MCP
4. **Real Service Integration:** Connect to GitHub, Slack, or email
5. **Error Handling:** Graceful failures and retry logic

**What You'll Build:**

**Example Project Ideas:**

**Option C1: Developer Workflow Assistant**
```
MCP Server Provides:
- Code review summaries from GitHub PRs
- Commit pattern analysis
- Documentation generation from code
- Automated changelog creation

n8n Workflows:
1. PR Review Bot: When PR opened → analyze code → post summary
2. Daily Digest: Aggregate commits → generate report → send email
3. Documentation Sync: Code changes → update docs → commit to repo

Tech Stack:
- TypeScript for MCP server
- n8n (self-hosted or cloud)
- GitHub API integration
- Claude API for analysis
- PostgreSQL for state storage
```

**Option C2: Smart Content Pipeline**
```
MCP Server Provides:
- Content analysis and summarization
- SEO optimization suggestions
- Image processing and generation
- Multi-platform formatting

n8n Workflows:
1. Blog Publisher: Draft → AI review → optimize → publish (WordPress, DEV.to)
2. Social Media Automation: Content → generate variations → schedule posts
3. Content Repurposing: Long-form → extract highlights → create threads

Tech Stack:
- Python for MCP server
- n8n workflows
- OpenAI API for content generation
- Image APIs (Unsplash, DALL-E)
- Multiple platform APIs
```

**Option C3: Personal Data Assistant**
```
MCP Server Provides:
- Cross-app data aggregation
- Natural language query interface
- Automated insights and reports
- Smart notifications

n8n Workflows:
1. Weekly Review: Aggregate data → AI analysis → formatted report
2. Smart Alerts: Monitor conditions → intelligent filtering → notify
3. Data Sync: Bidirectional sync between apps with transformations

Tech Stack:
- Node.js for MCP server
- n8n for orchestration
- Multiple APIs (Notion, Todoist, Calendar, Email)
- Claude for natural language processing
- Redis for caching
```

**What You'll Learn:**

**Technical Skills:**
- MCP protocol implementation
- n8n workflow design patterns
- API integration best practices
- Error handling and retry logic
- Async/event-driven architecture
- AI prompt orchestration

**Agentic AI Skills:**
- Designing tool interfaces for AI
- Context management across long workflows
- Reasoning about when AI adds value vs adds complexity
- Delegating workflow design to AI assistants
- Debugging AI-integrated systems

**Scope Boundaries:**

**In Scope:**
+ Implement MCP server with 3-5 tools
+ Build 2-3 n8n workflows using MCP server
+ Integrate with at least 2 external services
+ Basic UI for monitoring (n8n dashboard)
+ Documentation for MCP tools
+ Deployment (local or cloud)

**Out of Scope:**
- Building a full SaaS product
- User authentication/multi-tenancy
- Complex UI frontend
- Mobile app
- Real-time streaming (polling is fine)
- Production-scale reliability (learning project)

**Prerequisites:**

**Required:**
- Understanding of APIs and webhooks
- Basic TypeScript or Python knowledge
- Comfort with async programming
- Have n8n running (cloud or self-hosted)

**Helpful:**
- Experience with one automation platform
- Familiarity with Docker
- Understanding of OAuth flows

**Time Estimate:**
```
Phase 1: Goal & Research (3-4 hours)
  - Understand MCP protocol
  - Design custom tools
  - Plan workflows

Phase 2: MCP Server Development (6-8 hours)
  - Implement MCP server
  - Create 3-5 tools
  - Test with MCP inspector

Phase 3: n8n Workflow Creation (4-6 hours)
  - Build 2-3 workflows
  - Integrate MCP server
  - Connect external services

Phase 4: Integration & Testing (4-6 hours)
  - End-to-end testing
  - Error handling
  - Performance optimization

Phase 5: Documentation & Deployment (3-4 hours)
  - Document MCP tools
  - Write workflow guides
  - Deploy and demo

Total: 20-28 hours over 2-3 weeks
```

**Success Criteria:**

✓ **MCP Server:**
- Implements MCP protocol spec correctly
- Exposes 3-5 useful tools
- Handles errors gracefully
- Can be tested with MCP Inspector
- Documentation for each tool

✓ **n8n Workflows:**
- 2-3 workflows fully functional
- Integrate with MCP server
- Handle real external services
- Include error handling
- Process runs end-to-end successfully

✓ **AI Integration:**
- Claude/GPT successfully uses MCP tools
- AI makes intelligent tool choices
- Responses are accurate and useful
- Context maintained across workflow steps

✓ **Documentation:**
- MCP server setup instructions
- Tool documentation (inputs/outputs)
- Workflow diagrams
- Example use cases
- Demo video or screenshots

**Why This Project is Advanced:**

**Complexity Factors:**
1. **Protocol Implementation:** Must follow MCP spec precisely
2. **Async Orchestration:** Managing long-running workflows
3. **Multiple Integrations:** Various APIs with different patterns
4. **AI Unpredictability:** Handling non-deterministic AI responses
5. **Debugging:** Harder to debug distributed async systems

**Learning Curve:**
- MCP is newer (less documentation)
- n8n has unique mental model
- Workflow debugging is different from app debugging
- Must reason about system-level behavior

**Recommended For:**
- Developers comfortable with async/event patterns
- Those interested in AI automation
- Learners who want cutting-edge experience
- Candidates targeting AI infrastructure roles

---

### Learning Objectives

**All three capstone options practice these core skills. The emphasis varies:**

| Learning Objective | Option A<br>(Portfolio) | Option B<br>(Dashboard) | Option C<br>(n8n-MCP) |
|-------------------|------------------------|------------------------|-----------------------|
| Goal Setting & Scoping | ⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| Technical Planning | ⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| AI Delegation | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| Quality Verification | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| Iteration & Polish | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐ |
| Shipping to Production | ⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| Frontend Skills | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐ |
| Backend Skills | — | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| AI/Automation | ⭐ | ⭐⭐ | ⭐⭐⭐⭐ |

By completing your chosen capstone, you'll practice and reinforce:

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

### Example Project: SriSatyaLokesh Portfolio

**Live Site:** [https://srisatyalokesh.github.io/](https://srisatyalokesh.github.io/)

**Repository:** [https://github.com/SriSatyaLokesh/SriSatyaLokesh.github.io](https://github.com/SriSatyaLokesh/SriSatyaLokesh.github.io)

**Project Type:** Option A (Dynamic Developer Portfolio)

**Tech Stack:**
- Pure HTML5/CSS3/JavaScript (no frameworks)
- Typed.js for typing animations
- AOS (Animate On Scroll) library
- GitHub Pages for hosting
- Responsive design (mobile-first approach)

**Time to Build:** ~14 hours over 5 days (March 2024)

**AI Assistance:** ~60% AI-generated code (GitHub Copilot + Claude)

---

### Complete Project Walkthrough

**Initial Brief (What I Started With):**

```markdown
# Goal
Create a professional portfolio website that showcases my projects,
skills, and makes it easy for recruiters and collaborators to contact me.

# Why
- Need online presence for job applications
- Showcase GitHub projects in curated way
- Practice AI-assisted web development
- Learn responsive design patterns
- Deploy something real and public

# Success Criteria
- Clean, professional design (not template-looking)
- Works perfectly on mobile (60% of traffic)
- Fast load time (<2 seconds)
- Clear call-to-action (contact info)
- Shows personality (not generic)
- Live on github.io (free hosting)
```

**Key Architectural Decisions:**

**1. Why Vanilla JS instead of React?**

**Decision:** Pure HTML/CSS/JS

**Reasoning:**
- GitHub Pages serves static files instantly (no build required)
- Portfolio doesn't need state management or routing
- Faster load time without framework overhead
- Simpler deployment (just push to main branch)
- Demonstrates fundamental skills to interviewers

**Alternative considered:** Next.js (rejected due to build complexity for simple site)

---

**2. Content Structure**

**Layout chosen:**
```
├── Hero Section (name, title, CTA)
├── About (bio, skills, technologies)
├── Projects (featured work with images)
├── Experience (timeline view)
├── Contact (form + social links)
└── Footer
```

**Why this order:**
- Hero immediately shows who I am (< 3 seconds to understand)
- About builds credibility
- Projects are proof of skills
- Experience provides context
- Contact is final call-to-action

---

**3. Design Philosophy**

**Color Scheme:**
- Primary: `#2563eb` (blue)
- Secondary: `#10b981` (green)
- Dark: `#1e293b` (slate)
- Light: `#f8fafc` (off-white)

**Why these choices:**
- Blue conveys professionalism and trust
- Green adds energy without being loud
- High contrast for accessibility
- Works in both light/dark contexts

**Typography:**
- Headers: `'Poppins', sans-serif` (modern, friendly)
- Body: `'Inter', sans-serif` (readable, clean)
- Code: `'Fira Code', monospace` (developer aesthetic)

---

### Code Repository Tour

**File Structure:**

```
srisatyalokesh.github.io/
├── index.html              # Main page (all-in-one SPA)
├── styles.css              # All styles (~800 lines)
├── script.js               # Interactions and animations (~400 lines)
├── assets/
│   ├── profile.jpg         # Hero image
│   ├── projects/           # Project screenshots
│   │   ├── project1.png
│   │   ├── project2.png
│   │   └── project3.png
│   └── resume.pdf          # Downloadable resume
├── README.md               # Repo documentation
└── CNAME                   # Custom domain config (optional)
```

**Key Files Explained:**

**`index.html` (Main Structure)**

```html
<!-- Semantic HTML for SEO and Accessibility -->
<header>
  <nav class="navbar">
    <!-- Hamburger menu for mobile -->
  </nav>
</header>

<main>
  <section id="hero" class="hero-section">
    <h1 class="hero-title">
      Hi, I'm <span class="highlight">Sri Satya Lokesh</span>
    </h1>
    <p class="hero-subtitle">
      <span id="typed-text"></span> <!-- Typed.js animation -->
    </p>
    <div class="cta-buttons">
      <a href="#contact" class="btn-primary">Get In Touch</a>
      <a href="#projects" class="btn-secondary">View Work</a>
    </div>
  </section>

  <section id="about" class="about-section">
    <!-- Bio, skills, tech stack -->
  </section>

  <section id="projects" class="projects-section">
    <!-- Project cards with hover effects -->
  </section>

  <section id="contact" class="contact-section">
    <!-- Contact form with validation -->
  </section>
</main>

<footer>
  <!-- Copyright, social links -->
</footer>
```

**AI-Generated vs Human-Refined:**

| Component | AI Generated | Human Refined |
|-----------|-------------|----------------|
| HTML structure | 90% | Added semantic tags, accessibility attributes |
| CSS base styles | 80% | Adjusted colors, spacing, mobile breakpoints |
| Responsive grid | 95% | Fixed edge case for tablet (768px) |
| Typed.js integration | 100% | Changed text strings |
| Form validation | 70% | Added regex for email, better error messages |
| Smooth scroll | 100% | (worked perfectly) |
| Project cards | 60% | Redesigned hover effect, added overlay |
| Mobile menu | 85% | Fixed z-index issue, smooth animation |

---

**`script.js` (Interactivity)**

**Key Functions:**

```javascript
// 1. Typed.js animation for hero subtitle
const typed = new Typed('#typed-text', {
  strings: [
    'Full-Stack Developer',
    'AI Enthusiast',
    'Problem Solver',
    'Lifelong Learner'
  ],
  typeSpeed: 50,
  backSpeed: 30,
  loop: true
});

// 2. Smooth scroll navigation
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
  anchor.addEventListener('click', function(e) {
    e.preventDefault();
    const target = document.querySelector(this.getAttribute('href'));
    target.scrollIntoView({ behavior: 'smooth' });
  });
});

// 3. Mobile menu toggle
const menuBtn = document.querySelector('.menu-btn');
const navLinks = document.querySelector('.nav-links');

menuBtn.addEventListener('click', () => {
  navLinks.classList.toggle('active');
});

// 4. Form validation
const contactForm = document.getElementById('contact-form');
contactForm.addEventListener('submit', (e) => {
  e.preventDefault();
  
  const name = document.getElementById('name').value.trim();
  const email = document.getElementById('email').value.trim();
  const message = document.getElementById('message').value.trim();
  
  // Validation
  if (!name || !email || !message) {
    showError('Please fill in all fields');
    return;
  }
  
  if (!isValidEmail(email)) {
    showError('Please enter a valid email');
    return;
  }
  
  // Success (would integrate with backend or form service)
  showSuccess('Message sent! I\'ll get back to you soon.');
  contactForm.reset();
});

function isValidEmail(email) {
  return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
}
```

**AI Role in JavaScript:**
- Generated all boilerplate event listeners
- Created validation logic structure
- Provided Typed.js integration code
- Handled edge cases in scroll behavior

**Human interventions:**
- Changed typing strings to personalized content
- Improved error messages for form validation
- Added debouncing to scroll listener (performance)
- Fixed menu close-on-click-outside behavior

---

### Deployed Demo Walkthrough

**Live Features Tour:** [https://srisatyalokesh.github.io/](https://srisatyalokesh.github.io/)

**1. Hero Section**
- Typing animation cycles through roles
- Two clear CTAs ("Get In Touch" prioritized)
- Responsive: On mobile, buttons stack vertically
- Performance: Animation starts immediately (no flash)

**2. About Section**
- Skills displayed as pill badges with icons
- Tech stack logos for visual recognition
- Short bio focuses on what I can do, not just what I've done
- Links to GitHub, LinkedIn with external indicators

**3. Projects Section**
- Featured projects only (3-4, not exhaustive list)
- Each card includes:
  - Screenshot/demo GIF
  - Title + one-line description
  - Tech stack tags
  - Links to live demo + GitHub repo
- Hover effect: Card lifts with shadow, slight zoom on image
- Mobile: Cards stack, maintain visual hierarchy

**4. Contact Section**
- Form with inline validation (red border on invalid)
- Social media icons with hover color change
- Email displayed prominently
- Note: Form currently client-side only (would integrate with Formspree or Netlify Forms in v2)

**5. Performance Optimizations**
- Images lazy-loaded (`loading="lazy"` attribute)
- CSS minified for production
- No external font files (using system fonts as fallback)
- Total page size: ~850KB (acceptable for modern web)
- Lighthouse scores:
  - Performance: 94/100
  - Accessibility: 98/100
  - Best Practices: 100/100
  - SEO: 100/100

---

### What Makes This Portfolio-Worthy

**Professional Quality Indicators:**

✅ **Clean Design**
- Not using a recognizable template
- Consistent spacing and alignment
- Professional color palette
- No visual bugs or layout shifts

✅ **Functional**
- All links work
- Form validates correctly
- Responsive on all devices
- Fast load time

✅ **Attention to Detail**
- Smooth animations (not jarring)
- Hover states on interactive elements
- Accessible (keyboard navigation works)
- Good contrast ratios

✅ **Content Quality**
- Clear value proposition
- Projects have context (not just "this is a project")
- Grammar and spelling correct
- Professional tone

**What Sets It Apart:**

🌟 **Shows AI Skills:** By building with AI assistance, the site itself demonstrates my ability to leverage modern tools

🌟 **Fast Iteration:** Completed in 14 hours because AI handled boilerplate

🌟 **Focus on UX:** AI let me spend more time on user experience than syntax

🌟 **Real Projects:** Links to actual GitHub repos with code

---

### Reflections and Learnings

**What Went Smoothly:**

✅ **HTML Structure (95% AI)**
- Copilot generated perfect semantic HTML
- Just needed to swap placeholder text for real content
- Accessibility attributes included without asking

✅ **CSS Responsive Design (85% AI)**
- Asked: "Make this section responsive with mobile-first breakpoints"
- Got working Flexbox layout with proper media queries
- Only tweaked spacing values for visual preference

✅ **Typed.js Integration (100% AI)**
- Claude provided complete working example
- Documentation link included
- Worked first try

✅ **Deployment to GitHub Pages (100% AI)**
- Asked: "How do I deploy to GitHub Pages?"
- Got step-by-step instructions
- Live in 5 minutes

**Where AI Struggled:**

⚠️ **Color Palette Selection (30% AI)**
- AI suggested colors, but they didn't "feel right"
- Tried 3 different palettes before finding the right one
- Lesson: AI can suggest, human decides on aesthetics

⚠️ **Project Card Hover Effect (50% AI)**
- First attempt was too aggressive (card rotated 15deg)
- Second attempt was too subtle (just color change)
- Final version: Human-designed (slight lift + shadow + zoom)
- Lesson: Micro-interactions need human taste

⚠️ **Mobile Menu Animation (70% AI)**
- Generated menu toggle worked but had z-index bug
- Menu appeared behind other content
- Had to debug CSS stacking context manually
- Lesson: AI doesn't always catch CSS specificity issues

⚠️ **Form Validation Messaging (60% AI)**
- Generic error messages: "Invalid input"
- Not user-friendly
- Rewrote to be helpful: "Email should look like: name@example.com"
- Lesson: AI writes for machines, humans write for humans

**Surprises During Development:**

💡 **Copilot Learned My Style**
- After ~2 hours, Copilot started suggesting my preferred indentation
- Matched my naming conventions without prompting
- Felt like pair programming with someone who adapts

💡 **Claude Saved Hours on Responsive**
- Instead of Googling "CSS grid mobile breakpoints"
- Asked Claude, got tailored answer in context
- Included explanation of why certain breakpoints chosen

💡 **AI Excellent at"Glue Code"**
- Event listeners, API integrations, boilerplate
- 10x faster than writing manually
- Freed me to focus on creative decisions

**Key Takeaways:**

1. **AI handles ~60-80% of portfolio development**
   - Structure, boilerplate, standard patterns
   - Saves massive time on "solved problems"

2. **Human judgment critical for:**
   - Visual design decisions
   - Content and messaging
   - User experience nuances
   - Final quality assessment

3. **Best workflow:**
   - AI generates first draft
   - Human refines based on feel and feedback
   - Iterate quickly because AI speeds up changes

4. **Portfolio in 14 hours instead of 40+**
   - Traditional approach: 3-5 days full-time
   - AI-assisted: ~14 hours over 5 days
   - Quality is equal or better (more time for polish)

5. **Confidence boost:**
   - Shipping something real builds momentum
   - Portfolio itself demonstrates AI proficiency
   - Now I know I can build and deploy quickly

**How This Informed the Capstone Structure:**

- Emphasize iteration: First AI output won't be perfect
- Include polish phase: AI gets you 80%, you bring it to 100%
- Encourage deployment early: Seeing it live is motivating
- Set realistic scope: AI speeds things up, but refinement still takes time
- Provide actual prompts: Examples help more than abstract advice

## Prompts & Strategy

### Planning Phase Prompts

These are the **actual prompts** I used to plan the portfolio project. Copy and adapt them for your capstone.

---

**Prompt 1: Initial Brainstorming (to Claude)**

```
I want to create a portfolio website to showcase my development projects.
I have about 15 hours over the next week to build it.

Help me think through:
1. What are must-have features for a developer portfolio?
2. What should I explicitly NOT include (scope boundaries)?
3. What tech stack would be fastest to deploy with AI assistance?
4. How should I structure the content (what sections, what order)?

Context:
- Target audience: recruiters and potential collaborators
- I have 4-5 solid projects to feature
- Want it to feel personal, not generic
- Need it to work well on mobile
- Prefer free hosting
```

**Why This Prompt Works:**
- Specifies time constraint (15 hours) → AI suggests realistic scope
- Asks for boundaries (NOT include) → Prevents scope creep
- Provides context about audience → AI tailors suggestions
- Specific about constraints (mobile, free hosting) → Gets practical answers

**Claude's Response (Summary):**
- Must-have: Hero, About, Projects, Contact
- Skip: Blog, testimonials (time-consuming)
- Suggested: Pure HTML/CSS/JS (fastest to deploy)
- Structure: Hero → About → Projects → Contact (prioritize what recruiters see first)

---

**Prompt 2: Technical Decision-Making (to Claude)**

```
For a developer portfolio site, compare these options:

Option A: Pure HTML/CSS/Vanilla JS
Option B: React + Vite
Option C: Next.js with SSG

Evaluate based on:
- Time to build (I have 15 hours)
- Deployment complexity
- Performance
- SEO considerations
- Portfolio appropriateness (does it demo skills recruiters care about?)

I'm proficient in all three, so focus on trade-offs, not learning curve.
I want to use AI assistance (Copilot + Claude) for most implementation.
```

**Why This Prompt Works:**
- Presents specific options (not open-ended "what should I use?")
- Defines evaluation criteria → Gets structured comparison
- States proficiency level → Avoids getting basic tutorials
- Mentions AI assistance → AI factors that into recommendations

**Claude's Recommendation:**
Option A (Vanilla JS) — reasoning:
- Deploy to GitHub Pages with zero config
- No build step = faster iteration
- Demonstrates fundamentals (good signal for interviews)
- Performance out of the box
- AI handles vanilla JS well (mature patterns)

---

**Prompt 3: Content Structure (to Claude)**

```
I'm building a portfolio site with these sections:
- Hero (name, title, CTA)
- About (bio, skills)
- Projects (showcase)
- Contact (form)

For the Projects section, I have 8 projects but only want to feature 3-4.

How should I decide which projects to include?
What information should each project card display?
Provide a prioritization framework.
```

**Why This Prompt Works:**
- Specific problem (8 projects → choose 3-4)
- Asks for framework (not just a list) → Gets reusable criteria
- Clear constraint (only 3-4) → Forces prioritization

**Claude's Response:**
Prioritize projects by:
1. **Impact:** Does it solve a real problem?
2. **Tech showcase:** Does it demo skills you want to highlight?
3. **Completeness:** Is it finished and polished?
4. **Uniqueness:** Is it different from other projects?

Each card should show:
- Screenshot/GIF (visual proof)
- Title + one-line value prop
- Tech stack tags
- Links to live demo + repo
- (Skip: long descriptions, no one reads them)

---

**Prompt 4: PRD Creation (to Claude)**

```
Turn this into a PRD (Product Requirements Document):

Goal: Developer portfolio site
Sections: Hero, About, Projects, Contact
Tech: HTML/CSS/JS, GitHub Pages
Timeline: 15 hours

Include:
- Feature list with acceptance criteria
- Technical requirements
- Out-of-scope items
- Success metrics

Format it so I can give it to an AI agent for implementation.
```

**Why This Prompt Works:**
- Explicitly asks for PRD format → Gets structured output
- Specifies "for AI agent" → Claude writes for machine consumption
- Includes "out-of-scope" → Forces boundaries
- "Acceptance criteria" → Gets testable requirements

**Claude's Output:**
(Provided a structured PRD — see PRD Template section below for full example)

---

### Implementation Phase Prompts

These prompts got the portfolio built. Notice the pattern: **specific, contextual, action-oriented**.

---

**Prompt 5: Generate HTML Structure (to GitHub Copilot)**

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sri Satya Lokesh | Full-Stack Developer</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <!-- Create a hero section with:
       - Full-screen height
       - Centered content
       - h1 with my name
       - p with subtitle that will use Typed.js
       - Two CTA buttons: "Get In Touch" and "View Projects"
       - Smooth scroll to #contact and #projects
  -->
```

**Copilot Generated:**
```html
<section id="hero" class="hero-section">
  <div class="hero-content">
    <h1 class="hero-title">
      Hi, I'm <span class="highlight">Sri Satya Lokesh</span>
    </h1>
    <p class="hero-subtitle">
      <span id="typed-text"></span>
    </p>
    <div class="cta-buttons">
      <a href="#contact" class="btn-primary">Get In Touch</a>
      <a href="#projects" class="btn-secondary">View Projects</a>
    </div>
  </div>
</section>
```

**Why This Worked:**
- Comment describes desired outcome, not implementation
- Copilot filled in semantic HTML
- Included accessibility (proper heading hierarchy)

---

**Prompt 6: Responsive CSS (to Copilot)**

```css
/* styles.css */
/* Create mobile-first responsive styles for hero section:
   - Mobile: Stack vertically, buttons full-width
   - Tablet (768px+): Buttons side-by-side
   - Desktop (1024px+): Max-width container, more padding
   Use Flexbox for layout
*/

.hero-section {
```

**Copilot Generated:**
```css
.hero-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.hero-content {
  text-align: center;
  max-width: 800px;
}

.cta-buttons {
  display: flex;
  flex-direction: column;
  gap: 1rem;
  margin-top: 2rem;
}

@media (min-width: 768px) {
  .cta-buttons {
    flex-direction: row;
    justify-content: center;
  }
}

@media (min-width: 1024px) {
  .hero-section {
    padding: 2rem;
  }
}
```

**Why This Worked:**
- Specified mobile-first approach
- Named breakpoints with pixel values
- Told it Flexbox (prevents complex Grid when not needed)

---

**Prompt 7: JavaScript Interaction (to Claude)**

```javascript
// script.js
// I need smooth scroll behavior when clicking nav links.
// When user clicks any link with href starting with #,
// scroll smoothly to that section.
//
// Also, on mobile, after clicking a link, close the mobile menu
// (menu has class .nav-links with .active when open)
```

**Claude Generated:**
```javascript
document.querySelectorAll('a[href^="#"]').forEach(anchor => {
  anchor.addEventListener('click', function(e) {
    e.preventDefault();
    
    const targetId = this.getAttribute('href');
    const targetSection = document.querySelector(targetId);
    
    if (targetSection) {
      targetSection.scrollIntoView({
        behavior: 'smooth',
        block: 'start'
      });
    }
    
    // Close mobile menu if open
    const navLinks = document.querySelector('.nav-links');
    if (navLinks && navLinks.classList.contains('active')) {
      navLinks.classList.remove('active');
    }
  });
});
```

**Why This Worked:**
- Described behavior in plain English
- Mentioned specific class names (.nav-links, .active)
- Specified mobile behavior separately
- Got defensive code (checks if targetSection exists)

---

**Prompt 8: Debugging (to Claude)**

```
I'm getting this error in Chrome DevTools:

Uncaught TypeError: Cannot read property 'classList' of null
  at HTMLAnchorElement.<anonymous> (script.js:23)

The error happens when clicking a navigation link.
Here's the relevant code:

[pasted code]

What's wrong and how do I fix it?
```

**Why This Prompt Works:**
- Includes exact error message
- Shows where error occurs (file + line)
- Describes when it happens ("when clicking nav link")
- Provides code context

**Claude's Response:**
"The error suggests `navLinks` is null, meaning `document.querySelector('.nav-links')` didn't find an element.

Either:
1. The element doesn't exist in the HTML
2. The script runs before the DOM is loaded
3. Typo in class name

Fix: Wrap your code in `DOMContentLoaded`:

```javascript
document.addEventListener('DOMContentLoaded', () => {
  // Your code here
});
```

Or move script to end of body tag."

---

**Prompt 9: Form Validation (to Copilot)**

```javascript
// Create a form validation function:
// - Check if name, email, message fields are filled
// - Validate email format with regex
// - Show error message below each invalid field
// - Prevent form submission if validation fails
// - Clear error messages when user starts typing

const contactForm = document.getElementById('contact-form');
```

**Copilot Generated:**
(Full validation function with error handling, good UX)

---

**Prompt 10: Deployment (to Claude)**

```
How do I deploy my portfolio site to GitHub Pages?

I have:
- GitHub repo: srisatyalokesh.github.io
- Files: index.html, styles.css, script.js, assets/
- Want it live at srisatyalokesh.github.io

Give me the exact steps.
```

**Claude's Response:**
```
1. Make sure your repo is named: srisatyalokesh.github.io
2. Push your code to the main branch:
   git add .
   git commit -m "Initial portfolio"
   git push origin main

3. Go to repo Settings → Pages
4. Source: Deploy from branch
5. Branch: main, folder: / (root)
6. Click Save

7. Wait 2-3 minutes, then visit: https://srisatyalokesh.github.io

Note: If using custom domain, add CNAME file with your domain.
```

**Why This Worked:**
- Specific about my repo name
- Asked for "exact steps" → Got numbered list
- Worked first try

---

### Review and Polish Prompts

These prompts improved quality from "working" to "portfolio-worthy".

---

**Prompt 11: Code Review (to Claude)**

```
Review my portfolio code for:
1. Accessibility issues (WCAG compliance)
2. Performance problems
3. Security vulnerabilities
4. SEO best practices
5. Code quality and maintainability

Files:
- index.html (320 lines)
- styles.css (680 lines)
- script.js (280 lines)

[Paste code or provide GitHub link]

Prioritize issues by impact.
```

**Claude Identified:**
- Missing alt text on 2 images (accessibility)
- Form lacks CSRF protection (not critical for static site but noted)
- Missing meta description (SEO)
- Large image files not optimized (performance)
- Some CSS specificity issues (maintainability)

---

**Prompt 12: Performance Optimization (to Claude)**

```
My portfolio loads in 3.2 seconds on 3G.
Goal: Under 2 seconds.

Current issues:
- images/ folder has 6 PNG files, ~400-800KB each
- Loading 3 Google Fonts
- CSS is 680 lines, not minified

What are the highest-impact optimizations?
Provide specific steps.
```

**Claude's Recommendations:**
1. Convert PNGs to WebP (70% size reduction)
2. Use system fonts instead of Google Fonts (save 200KB + DNS lookup)
3. Lazy load images below fold
4. Minify CSS with cssnano

**Result:** Load time dropped to 1.4 seconds

---

**Prompt 13: Accessibility Audit (to Claude)**

```
Audit my portfolio for accessibility:

Run through this checklist:
- [ ] Keyboard navigation works (can tab through all interactive elements)
- [ ] Screen reader friendly (proper ARIA labels, alt text)
- [ ] Color contrast meets WCAG AA (4.5:1 for text)
- [ ] Focus indicators visible
- [ ] Form labels associated with inputs
- [ ] No keyboard traps

Code: [link to repo]

For each issue, provide the fix.
```

**Claude Found:**
- Mobile menu "hamburger" icon had no label (screen readers couldn't identify it)
  - Fix: Add `aria-label="Open menu"` and `role="button"`
- Project card links didn't clearly indicate they open in new tab
  - Fix: Add `aria-label="View project (opens in new tab)"`
- Skip-to-content link missing
  - Fix: Add skip link at top of HTML

---

### Prompt Sequencing Strategy

**The Optimal Order I Used:**

**Stage 1: Planning (2 hours)**
```
1. Brainstorming (Prompt 1) → Get feature list
2. Tech decision (Prompt 2) → Choose stack
3. Content planning (Prompt 3) → Decide what to include
4. PRD creation (Prompt 4) → Formalize plan
```
**Why this order:** Each prompt builds on previous answers. Can't write PRD without knowing tech stack.

---

**Stage 2: Foundation (3 hours)**
```
5. HTML structure (Prompt 5) → Get skeleton
6. CSS base styles (Prompt 6) → Make it look good
7. Test responsive → See it on mobile
```
**Why this order:** HTML first (structure), then CSS (presentation), then test.

---

**Stage 3: Interactivity (4 hours)**
```
8. JavaScript basics (Prompt 7) → Add scroll, menu
9. Debug issues (Prompt 8) → Fix what breaks
10. Form validation (Prompt 9) → Finish contact form
11. Test all interactions → Click everything
```
**Why this order:** Get basic interactions working before advanced features.

---

**Stage 4: Deploy Early (1 hour)**
```
12. Deploy (Prompt 10) → Push to GitHub Pages
13. Test in production → See how it feels live
```
**Why deploy before polish:** Motivating to see it live. Easier to test on real devices.

---

**Stage 5: Polish (4 hours)**
```
14. Code review (Prompt 11) → Find issues
15. Performance (Prompt 12) → Optimize
16. Accessibility (Prompt 13) → Fix a11y
17. Final QA → Test everything again
```
**Why this order:** Polish after deployment means you're refining something real, not theoretical.

---

**When to Parallelize vs Serialize:**

**Parallelize (can do at same time):**
- ✅ HTML structure + CSS base (Copilot can handle both)
- ✅ Performance audit + accessibility audit (independent)

**Serialize (must do in order):**
- ❌ Can't write CSS before HTML exists
- ❌ Can't debug JavaScript before writing it
- ❌ Can't optimize performance before deploying (need real data)

---

**Adapting Sequence When Blocked:**

**Scenario 1: AI generates broken code**

Orignal plan: Write JS → Test → Polish

**Roadblock:** Generated code has syntax error

**Adaptation:**
- Paste error to Claude (Prompt 8 pattern)
- Get fix, test again
- If still broken, simplify the prompt:
  - Bad: "Create smooth scroll with parallax and fade-in"
  - Good: "Create basic smooth scroll. Just scrollIntoView."

**Lesson:** Break complex prompts into simple ones when AI struggles.

---

**Scenario 2: Design doesn't feel right**

Original plan: Get CSS from AI → Done

**Roadblock:** Colors look wrong, spacing feels off

**Adaptation:**
- Skip to manual tweaking phase
- Don't fight AI to get perfect colors
- Use AI for structure, human taste for aesthetics
- Iterate: Change values, refresh, decide

**Lesson:** Don't over-prompt aesthetic issues. Faster to tweak manually.

---

**Scenario 3: Scope creep temptation**

Original plan: Hero, About, Projects, Contact → Ship

**Roadblock:** "I should add a blog... and testimonials... and..."

**Adaptation:**
- Revisit PRD (Prompt 4 defined out-of-scope)
- Remind myself: MVP first, v2 later
- Ship what's planned, add features after capstone complete

**Lesson:** Sequence includes saying "no" to new ideas mid-project.

---

**Key Sequencing Principles:**

1. **Plan before code** (2 hours planning saves 10 hours rework)
2. **Foundation before details** (structure → style → interaction)
3. **Deploy early** (motivating + easier to test)
4. **Polish last** (optimize something real, not theoretical)
5. **Iterate on blockers** (if prompt fails, simplify and retry)
6. **Timebox decisions** (15 min on color choice, move on)
7. **Test continuously** (don't wait until end)

## Step-by-Step Guide

> **Note:** This detailed walkthrough uses **Option B (Personal Developer Dashboard)** as the example. The same GSD framework (Goal → Spec → Deliver) applies to all three options, but the specific technologies and tasks will differ.
>
> **For Option A (Portfolio):** The phases are similar but simpler (no backend, no OAuth, pure HTML/CSS/JS).  
> **For Option C (n8n-MCP):** Replace frontend/backend tasks with MCP server implementation and n8n workflow creation.
>
> The prompting patterns, verification techniques, and deployment strategies are universal—adapt them to your chosen project.

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

---

### Adapting This Guide to Your Chosen Option

**If you chose Option A (Dynamic Portfolio):**

The phases map directly, but tasks are simpler:

**Phase 1 (Goal Setting):**
- Same process, but research vanilla JS libraries instead of React/Node
- Prompt: "What are the best lightweight JavaScript libraries for portfolios in 2026?"

**Phase 2 (Specification):**
- No backend/database tasks
- Focus on content structure (sections, projects to feature)
- Prompt: "Break down building a portfolio site into HTML/CSS/JS tasks"

**Phase 3 (Implementation):**
Replace OAuth/API tasks with:
- Structure HTML semantic markup
- Style with CSS Grid/Flexbox
- Add JS interactivity (smooth scroll, menu toggle, form validation)
- Integrate animations (AOS, Typed.js)

**Phase 4 (Iteration):**
- Test across browsers and devices
- Optimize images and load time
- Refine animations and transitions
- Get feedback on design

**Phase 5 (Deployment):**
- Deploy to GitHub Pages instead of Vercel/Railway
- No environment variables or backend deployment
- Prompt: "How do I deploy a static site to GitHub Pages with custom domain?"

**If you chose Option C (n8n-MCP):**

The framework is the same, but focus shifts:

**Phase 1 (Goal Setting):**
- Define which workflow problem you're solving
- Research MCP protocol and n8n capabilities
- Decide on MCP tools to implement

**Phase 2 (Specification):**
- Design MCP tool interfaces (inputs/outputs)
- Map out n8n workflow steps
- Plan integration points with external services

**Phase 3 (Implementation):**
Replace frontend/backend with:
- Implement MCP server in TypeScript/Python
- Create individual MCP tools following protocol spec
- Build n8n workflows connecting to your MCP server
- Integrate external APIs (GitHub, Slack, etc.)

**Phase 4 (Iteration):**
- Test MCP server with MCP Inspector
- Test workflows end-to-end
- Add error handling and retry logic
- Optimize for reliability

**Phase 5 (Deployment):**
- Deploy MCP server (Docker container or cloud function)
- Configure n8n to connect to your MCP server
- Set up workflow triggers (webhooks, schedules)
- Document tool usage for future reference

**Universal Prompting Patterns:**

These prompts work for ALL options:

```
**Starting a phase:**
"I'm on [Phase X] of my [Option] project. My goal is [specific goal].
What are the key tasks I should complete in this phase?"

**Task breakdown:**
"Break down [feature] into specific implementable tasks with acceptance criteria."

**When stuck:**
"I'm trying to [goal] but encountering [issue].
What are potential solutions, and which would you recommend?"

**Code generation:**
"Implement [feature] with these requirements:
- [Requirement 1]
- [Requirement 2]
Use [tech stack] following best practices."

**Review/debug:**
"Review this code for [feature]. Check for:
- Bugs or edge cases
- Security issues
- Performance problems
- Best practice violations"
```

---

### Phase 6: Portfolio Documentation

After completing your capstone project, create compelling documentation that showcases your work professionally.

**Objective:** Transform your code into a portfolio piece that tells a story and demonstrates your skills.

---

**Documentation Artifacts to Create:**

**1. Comprehensive README.md**
```markdown
Structure:
├── Hero (title, tagline, demo link)
├── What It Does (value proposition)
├── Features (with screenshots)
├── Tech Stack (organized by layer)
├── Getting Started (setup instructions)
├── Project Structure (file tree with explanations)
├── API Documentation (if applicable)
├── Learnings & Reflections (honest takeaways)
├── Future Enhancements (roadmap)
└── License & Acknowledgments
```

**2. Visual Demos**
- Screenshots of main features\n- Animated GIFs of interactions (use LICEcap or ScreenToGif)
- Optional: 2-3 minute demo video (Loom)

**3. Project Narrative (Blog Post or Dev.to Article)**

**Template:**
```markdown
# How I Built [Project] in [Timeframe] Using AI

## The Challenge
[What problem were you solving?]

## The Approach
[How did you use the GSD framework?]
[What AI tools did you leverage?]

## Key Decisions
[2-3 important architectural or design choices]
[Include trade-offs you considered]

## What I Learned
[Technical learnings]
[AI collaboration learnings]
[What surprised you]

## The Result
[Link to live demo]
[Key metrics: load time, lighthouse score, etc.]

## Takeaways for Others Building with AI
[3-5 actionable tips]
```

**4. Technical Decision Log**

Document major decisions that shaped the project:

| Decision | Options Considered | Choice Made | Reasoning |
|----------|-------------------|-------------|-----------|
| Tech Stack | React, Vue, Vanilla JS | Vanilla JS | Fastest deployment, no build step |
| Hosting | Vercel, Netlify, GitHub Pages | GitHub Pages | Free, zero config |
| Styling | Tailwind, Bootstrap, Custom CSS | Custom CSS | Full control, learning opportunity |

**5. AI Contribution Breakdown**

Be transparent about AI's role:

```markdown
## AI Assistance Breakdown

**Generated by AI (~65% of code):**
- HTML structure (95% generated, 5% adjusted)
- CSS base styles (80% generated, 20% refined)
- JavaScript boilerplate (90% generated, 10% debugged)
- Documentation first draft (70% generated, 30% personalized)

**Human-Driven (~35%):**
- Design decisions (100% human)
- Content and copy (100% human)
- Code review and refinement (100% human)
- UX improvements (100% human)

**Tools Used:**
- GitHub Copilot: Real-time code completion
- Claude: Architectural guidance, debugging, prompt engineering
- GSD Framework: Project structure and task breakdown
```

**Positioning for Different Audiences:**

**For Recruiters:**
- Lead with technical skills demonstrated\n- Highlight problem-solving approach
- Show deployed result (link at top)
- Include metrics (performance, test coverage)
- Mention AI tools as modern workflow (not cheating)

**For Collaborators:**
- Emphasize setup instructions clarity
- Include contribution guidelines
- Show project is maintained (recent commits)
- Provide clear code structure explanation

**For Community (Dev.to, Hashnode):**
- Tell the story (journey, not just outcome)
- Share learnings and mistakes
- Include helpful prompts and tips
- Invite feedback and discussion

**Portfolio Checklist:**

Before calling documentation complete:

- [ ] README has demo link in first 3 lines
- [ ] All screenshots are high-quality (retina resolution)
- [ ] Setup instructions tested on fresh machine
- [ ] Code is well-commented (especially complex parts)
- [ ] Repository has topics/tags (improves discoverability)
- [ ] License file included (MIT is common for portfolio)
- [ ] No TODOs or placeholder text left in docs
- [ ] Project narrative published (blog post or Dev.to)
- [ ] LinkedIn post sharing the project

---

## PRD Template

### Capstone PRD Structure

This PRD template is designed for AI agent execution. It's structured to provide all information an AI needs to implement your capstone project successfully.

**Key Principles:**

1. **Specific over vague:** "Form validates email format" > "Form should work well"
2. **Testable criteria:** Every requirement should have a "done when..." condition
3. **Boundaries clear:** Explicit out-of-scope prevents scope creep
4. **Context provided:** AI needs to know "why" to make good implementation choices

---

### Example PRD: Developer Portfolio Website

**Copy this template and adapt for your capstone project.**

---

# Product Requirements Document: Developer Portfolio Website

**Version:** 1.0  
**Author:** Your Name  
**Date:** 2024-03-15  
**Status:** Ready for Implementation

---

## 1. Overview

### 1.1 Goal

Create a professional portfolio website that showcases my development projects, technical skills, and makes it easy for recruiters and potential collaborators to contact me.

### 1.2 Why This Matters

**Problem:**
- Currently no centralized place to showcase my work
- GitHub profile doesn't tell a story or highlight best projects
- Recruiters need a quick way to assess skills and contact

**Impact:**
- Increases job opportunities (professional online presence)
- Demonstrates AI-assisted development skills (meta value)
- Serves as capstone project for Agentic AI learning pathway

### 1.3 Success Criteria

**Functional Requirements:**
- [ ] All sections display correctly without visual bugs
- [ ] Navigation works smoothly (links, smooth scroll)
- [ ] Contact form validates input and provides feedback
- [ ] Site is responsive (mobile, tablet, desktop)
- [ ] Fast load time (< 2 seconds on 3G)

**Learning Requirements:**
- [ ] Used AI agents for >50% of implementation
- [ ] Followed GSD Framework (Goal → Spec → Deliver)
- [ ] Documented prompts and learnings
- [ ] Deployed to public URL

**Portfolio Quality:**
- [ ] Looks professional (not obviously a template)
- [ ] Shows personality (not generic)
- [ ] Clear call-to-action (contact info prominent)
- [ ] No spelling/grammar errors
- [ ] Projects showcase real work

---

## 2. Scope

### 2.1 In Scope (MVP)

**Core Sections:**
1. **Hero Section**
   - Name and title
   - Brief tagline
   - Call-to-action buttons
   - Typing animation for roles

2. **About Section**
   - Short bio (2-3 paragraphs)
   - Skills list (visual pills or badges)
   - Tech stack logos
   - Links to GitHub, LinkedIn

3. **Projects Section**
   - 3-4 featured projects (not full catalog)
   - Each project includes:
     - Screenshot or GIF
     - Title and one-line description
     - Tech stack used
     - Links to live demo and GitHub repo

4. **Contact Section**
   - Contact form (name, email, message)
   - Client-side validation
   - Social media links
   - Email address

5. **Responsive Design**
   - Mobile-first approach
   - Breakpoints: 375px, 768px, 1024px, 1440px
   - Touch-friendly (buttons min 44x44px)

6. **Performance**
   - Optimized images (WebP format)
   - Minified CSS/JS
   - Lazy loading for below-fold images
   - Lighthouse score > 90 for all metrics

### 2.2 Explicitly Out of Scope

**NOT included in MVP:**
- ❌ Blog or articles section (future v2)
- ❌ Backend for contact form (use client-side for MVP)
- ❌ CMS integration (static content is fine)
- ❌ Dark mode toggle (can add later)
- ❌ Animations beyond smooth scroll and typing effect
- ❌ Multiple language support
- ❌ Analytics dashboard (Google Analytics tag is enough)

**Scope boundaries:**
- Maximum 4 projects showcased (prevents analysis paralysis)
- Only email contact (no calendly integration yet)
- Static HTML/CSS/JS (no build step required)

---

## 3. Technical Requirements

### 3.1 Tech Stack

**Frontend:**
- Pure HTML5 (semantic markup)
- CSS3 (Grid, Flexbox, custom properties)
- Vanilla JavaScript (ES6+)

**Libraries (optional):**
- Typed.js for typing animation
- AOS (Animate On Scroll) for scroll effects

**Hosting:**
- GitHub Pages (free, zero-config)

**Tooling:**
- Visual Studio Code
- Git for version control
- Browser DevTools for debugging

**Why these  choices:**
- No framework overhead (fast load, simple deploy)
- GitHub Pages supports static sites natively
- Vanilla JS demonstrates fundamentals
- Minimal dependencies (1-2 small libraries max)

### 3.2 Browser Support

**Target browsers:**
- Chrome 90+ (primary)
- Firefox 88+ 
- Safari 14+ (iOS especially important)
- Edge 90+

**Not supporting:**
- Internet Explorer (end of life)
- Opera Mini (limited JS support)

### 3.3 Performance Targets

| Metric | Target | Measurement |
|--------|--------|-------------|
| First Contentful Paint | < 1.5s | Lighthouse |
| Time to Interactive | < 3.0s | Lighthouse |
| Total page size | < 1MB | DevTools Network |
| Lighthouse Performance | > 90 | Lighthouse audit |
| Lighthouse Accessibility | > 95 | Lighthouse audit |

### 3.4 Accessibility Requirements

**WCAG 2.1 Level AA compliance:**
- ✅ Semantic HTML (h1-h6 hierarchy, section/nav/main tags)
- ✅ Alt text for all images
- ✅ Color contrast ratio ≥ 4.5:1 for text
- ✅ Keyboard navigation (all interactive elements reachable by Tab)
- ✅ Focus indicators visible (outline on :focus)
- ✅ ARIA labels where appropriate (mobile menu button)
- ✅ Form labels associated with inputs (label for=\"\")
- ✅ Skip-to-content link for screen readers

---

## 4. Detailed Feature Requirements

### 4.1 Hero Section

**Visual Layout:**
```
┌─────────────────────────────────┐
│  [Full-screen height backdrop]  │
│                                  │
│     Hi, I'm Sri Satya Lokesh    │
│    [Typing: Full-Stack Dev...]  │
│                                  │
│  [Get In Touch] [View Projects] │
│                                  │
└─────────────────────────────────┘
```

**Requirements:**
- [ ] Centered content (horizontal and vertical)
- [ ] Heading: Name with highlight color on last name
- [ ] Subtitle: Typed.js animation cycles through roles:
  - \"Full-Stack Developer\"
  - \"AI Enthusiast\"
  - \"Problem Solver\"
- [ ] Two CTA buttons:
  - Primary: \"Get In Touch\" (smooth scroll to #contact)
  - Secondary: \"View Projects\" (smooth scroll to #projects)
- [ ] Background: Gradient or solid color (no stock photos)

**Acceptance Criteria:**
- Typing animation loops continuously
- Buttons navigate correctly with smooth scroll
- Section takes full viewport height on desktop
- Text readable on mobile (min font size 16px)

---

### 4.2 About Section

**Content:**
- Bio: 2-3 paragraphs max (keep it scannable)
- Skills: List of technical skills (grouped by category)
- Tech stack: Logo icons for main technologies

**Layout:**
```
┌────────────────┬─────────────────┐
│                │                 │
│   [Bio Text]   │   [Skills Grid] │
│                │                 │
└────────────────┴─────────────────┘
```

**Requirements:**
- [ ] Bio emphasizes what you CAN DO, not just what you've done
- [ ] Skills organized by category (Languages, Frameworks, Tools)
- [ ] Each skill as pill/badge with hover effect
- [ ] Tech stack logos: 8-12 icons max
- [ ] Social links: GitHub, LinkedIn (open in new tab)

**Acceptance Criteria:**
- Bio is 150-300 words (not a novel)
- Skills are scannable (not a wall of text)
- Links have external indicator (icon or text)
- Section readable on mobile (stacks vertically <768px)

---

### 4.3 Projects Section

**Visual:**
```
┌──────────┐ ┌──────────┐ ┌──────────┐
│[Image]   │ │[Image]   │ │[Image]   │
│Title     │ │Title     │ │Title     │
│Desc...   │ │Desc...   │ │Desc...   │
│[Tags]    │ │[Tags]    │ │[Tags]    │
│[Demo][Git│ │[Demo][Git│ │[Demo][Git│
└──────────┘ └──────────┘ └──────────┘
```

**Requirements:**
- [ ] 3-4 featured projects only (most impressive work)
- [ ] Each project card includes:
  - High-quality screenshot or demo GIF
  - Project title (concise, descriptive)
  - One-line value proposition (not just \"This is a project\")
  - Tech stack tags (3-5 technologies)
  - Links: Live Demo + GitHub Repo
- [ ] Hover effect: Card elevates, subtle shadow, zoom on image
- [ ] Mobile: Cards stack vertically, maintain all information

**Acceptance Criteria:**
- Each project clearly explains what problem it solves
- Links open in new tab
- Images optimized (WebP, < 200KB each)
- No broken links (test all URLs)
- Hover effect works on desktop, not intrusive on touch

**Project Selection Criteria:**
(Include this guidance in PRD for yourself)

Choose projects that:
1. **Solve real problems** (not just tutorials)
2. **Showcase different skills** (variety in tech stack)
3. **Are complete** (not WIP or broken)
4. **Have good documentation** (so recruiters can understand)

---

### 4.4 Contact Section

**Layout:**
```
┌────────────────────────────────────┐
│        Get In Touch                │
│  ┌──────────────────────────────┐  │
│  │ Name: [           ]          │  │
│  │ Email: [          ]          │  │
│  │ Message: [                ] │  │
│  │       [Send Message]         │  │
│  └──────────────────────────────┘  │
│                                    │
│  [GitHub] [LinkedIn] [Email]       │
└────────────────────────────────────┘
```

**Requirements:**
- [ ] Form fields: Name, Email, Message
- [ ] Client-side validation:
  - Name: Required, min 2 characters
  - Email: Required, valid email format (regex)
  - Message: Required, min 10 characters
- [ ] Error messages: Display below invalid field (red text)
- [ ] Success message: \"Message sent! I'll get back to you soon.\"
- [ ] Form clears after successful submission
- [ ] Social media icons with hover effects
- [ ] Email address displayed

**Validation Rules:**
```javascript
- Name: /^[a-zA-Z\\s]{2,50}$/
- Email: /^[^\\s@]+@[^\\s@]+\\.[^\\s@]+$/
- Message: .length >= 10
```

**Acceptance Criteria:**
- Cannot submit with empty fields
- Invalid email shows helpful error message
- Submission triggers success message (even if no backend)
- Form accessible (labels, keyboard navigation)
- Social links open in new tab

**Note:** MVP uses client-side validation only. Future: Integrate with Formspree or Netlify Forms.

---

## 5. Design Specifications

### 5.1 Color Palette

**Primary Colors:**
- Primary: `#2563eb` (Blue 600) - CTAs, links
- Secondary: `#10b981` (Green 500) - Accents, success
- Dark: `#1e293b` (Slate 800) - Text, footer
- Light: `#f8fafc` (Slate 50) - Backgrounds

**Semantic Colors:**
- Error: `#ef4444` (Red 500)
- Warning: `#f59e0b` (Amber 500)
- Success: `#10b981` (Green 500)

### 5.2 Typography

**Font Families:**
```css
--font-heading: 'Poppins', -apple-system, BlinkMacSystemFont, sans-serif;
--font-body: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
--font-code: 'Fira Code', 'Courier New', monospace;
```

**Type Scale:**
```css
--text-xs: 0.75rem;    /* 12px */
--text-sm: 0.875rem;   /* 14px */
--text-base: 1rem;     /* 16px */
--text-lg: 1.125rem;   /* 18px */
--text-xl: 1.25rem;    /* 20px */
--text-2xl: 1.5rem;    /* 24px */
--text-3xl: 1.875rem;  /* 30px */
--text-4xl: 2.25rem;   /* 36px */
--text-5xl: 3rem;      /* 48px */
```

**Line Heights:**
- Headings: 1.2
- Body text: 1.6
- Small text: 1.4

### 5.3 Spacing System

```css
--space-1: 0.25rem;  /* 4px */
--space-2: 0.5rem;   /* 8px */
--space-3: 0.75rem;  /* 12px */
--space-4: 1rem;     /* 16px */
--space-6: 1.5rem;   /* 24px */
--space-8: 2rem;     /* 32px */
--space-12: 3rem;    /* 48px */
--space-16: 4rem;    /* 64px */
--space-24: 6rem;    /* 96px */
```

### 5.4 Responsive Breakpoints

```css
/* Mobile first approach */
/* Small (default): 375px - 767px */
/* Medium: 768px - 1023px */
@media (min-width: 768px) { ... }

/* Large: 1024px - 1439px */
@media (min-width: 1024px) { ... }

/* XLarge: 1440px+ */
@media (min-width: 1440px) { ... }
```

---

## 6. Implementation Phases

### Phase 1: Setup & Structure (2 hours)

**Tasks:**
1. Create GitHub repository: `yourusername.github.io`
2. Initialize project structure:
   ```
   ├── index.html
   ├── styles.css
   ├── script.js
   ├── assets/
   │   ├── images/
   │   └── resume.pdf
   └── README.md
   ```
3. Create basic HTML structure with semantic tags
4. Link CSS and JS files
5. Test: Page loads with basic content

**Acceptance:**
- Repository exists and is public
- Files structured correctly
- HTML validates (W3C validator)
- Page loads without errors

---

### Phase 2: Styling & Layout (4 hours)

**Tasks:**
1. Implement CSS variables for colors, fonts, spacing
2. Style hero section (full height, centered, gradient)
3. Style about section (two-column on desktop, stacked on mobile)
4. Style projects section (card grid, hover effects)
5. Style contact section (form styling, button states)
6. Add responsive breakpoints
7. Test: All sections styled, responsive

**Acceptance:**
- Consistent spacing throughout
- Responsive on mobile, tablet, desktop
- Colors match design spec
- Typography readable (contrast compliant)

---

### Phase 3: Interactivity (3 hours)

**Tasks:**
1. Integrate Typed.js for hero animation
2. Implement smooth scroll navigation
3. Create mobile menu (hamburger) with toggle
4. Add form validation (inline errors)
5. Create form submission handler (show success message)
6. Add scroll-triggered animations (AOS or custom)
7. Test: All interactions work

**Acceptance:**
- Typing animation loops
- Smooth scroll works for all nav links
- Menu togglesmobile
- Form validates correctly
- No console errors

---

### Phase 4: Content & Polish (3 hours)

**Tasks:**
1. Write bio content (personal, professional tone)
2. Select and document 3-4 projects
3. Take/optimize screenshots
4. Add project descriptions and links
5. Proofread all copy (Grammarly)
6. Optimize images (convert to WebP, compress)
7. Test: Content complete, no TODOs

**Acceptance:**
- All real content (no \"Lorem ipsum\")
- No spelling/grammar errors
- Images optimized (< 200KB each)
- All links work

---

### Phase 5: Optimization & Testing (2 hours)

**Tasks:**
1. Run Lighthouse audit (target: all > 90)
2. Minify CSS and JS
3. Add meta tags (SEO, Open Graph)
4. Test on real devices (mobile, tablet)
5. Test in different browsers
6. Fix any bugs found
7. Test: Meets performance targets

**Acceptance:**
- Lighthouse scores > 90
- Works in Chrome, Firefox, Safari, Edge
- No visual bugs on mobile
- Load time < 2 seconds

---

### Phase 6: Deployment & Documentation (1 hour)

**Tasks:**
1. Push to GitHub
2. Enable GitHub Pages (Settings → Pages)
3. Verify live site works
4. Update README with setup instructions
5. Add screenshot to README
6. (Optional) Configure custom domain

**Acceptance:**
- Site live at `yourusername.github.io`
- README has live demo link
- All features work in production

---

## 7. Verification Checklist

**Before declaring "done", verify:**

**Functional:**
- [ ] All navigation links work
- [ ] Form validation catches invalid input
- [ ] Smooth scroll works
- [ ] External links open in new tab
- [ ] Mobile menu toggles correctly

**Visual:**
- [ ] No layout shifts or content jumps
- [ ] Consistent spacing and alignment
- [ ] Colors match design spec
- [ ] Readable font sizes (min 16px body)
- [ ] Hover states on all interactive elements

**Responsive:**
- [ ] Mobile (375px): Single column, readable
- [ ] Tablet (768px): Intelligent layout adjustments
- [ ] Desktop (1024px+): Full layout, proper spacing

**Performance:**
- [ ] Lighthouse Performance > 90
- [ ] Lighthouse Accessibility > 95
- [ ] Page load < 2 seconds on 3G
- [ ] Images optimized (WebP, compressed)

**Accessibility:**
- [ ] Keyboard navigation works (Tab through all elements)
- [ ] Focus indicators visible
- [ ] Alt text on all images
- [ ] Form labels associated with inputs
- [ ] Semantic HTML (proper heading hierarchy)

**Content:**
- [ ] No spelling errors (run through Grammarly)
- [ ] No placeholder text (\"Lorem ipsum\", \"TODO\")
- [ ] Bio is personal and authentic
- [ ] Projects explain value (not just tech stack)
- [ ] Contact info correct and working

**Code Quality:**
- [ ] HTML validates (W3C)
- [ ] CSS organized (logical grouping)
- [ ] JavaScript has error handling
- [ ] No console errors
- [ ] Comments explain complex logic

---

##  8. AI Agent Execution Notes

**For AI implementing this PRD:**

**Priority Order:**
1. Structure (HTML) → Style (CSS) → Interact (JS)
2. Mobile layout first, then scale up
3. Content placeholders initially, real content in Phase 4

**Decision Authority:**
- **AI can decide:** CSS specifics (exact padding values), JS implementation details, file organization
- **Human must decide:** Color aesthetics, bio content, which projects to feature, final CTA text

**When to Pause for Human:**
- Design feels \"off\" (colors, spacing subjective)
- Content decisions (personal bio, project selection)
- Critical bugs that AI can't debug after 2 attempts

**Testing Protocol:**
1. After each phase, human verifies acceptance criteria
2. If fails, provide specific feedback, AI iterates
3. If passes, proceed to next phase

**Common Pitfalls AI Should Avoid:**
- Don't over-animate (subtle >> flashy)
- Don't use stock photos for hero (solid color or gradient better)
- Don't make mobile font sizes too small (<16px)
- Don't forget focus indicators (accessibility)
- Don't hardcode values (use CSS variables)

---

## 9. Future Enhancements (Post-MVP)

**Not in v1, consider for v2:**
- [ ] Blog section with markdown rendering
- [ ] Dark mode toggle
- [ ] Backend for contact form (Formspree integration)
- [ ] Testimonials section
- [ ] Detailed case studies per project
- [ ] Resume download with tracking
- [ ] Google Analytics for visitor insights
- [ ] Animations beyond basic scroll effects

**Scope creep prevention:** If tempted to add these during MVP, refer back to section 2.2 (Explicitly Out of Scope).

---

## End of PRD

**Status:** ✅ Ready for Implementation

**Next Steps:**
1. Review PRD with human for any adjustments
2. Begin Phase 1 (Setup & Structure)
3. Execute phases sequentially
4. Test and verify after each phase
5. Deploy and celebrate 🎉

---

### Customization Guide

**How to adapt this PRD for YOUR capstone project:**

---

**Step 1: Adjust Scope to Your Skill Level**

**If you're a beginner:**
- ✂️ **Remove:**
  - Form validation (use basic HTML5 validation)
  - Animations (skip Typed.js, AOS)
  - Multiple responsive breakpoints (just mobile + desktop)

- ✅ **Simplify:**
  - 2-3 sections max (Hero, Projects, Contact)
  - Single-column layout on mobile
  - Basic CSS (no Grid/Flexbox complexity)

**If you're intermediate:**
- Use PRD as-is

**If you're advanced:**
- ✨ **Add:**
  - Dark mode toggle
  - Backend for contact form (Node.js + Nodemailer)
  - Blog section with CMS (Contentful, Sanity)
  - Advanced animations (Framer Motion, GSAP)
  - Analytics dashboard

---

**Step 2: Adapt for Your Chosen Tech Stack**

**If using React instead of Vanilla JS:**

**Changes needed:**
- Section 3.1 (Tech Stack): Update to React, Vite, React Router
- Section 4: Convert sections to components
- Section 6 (Phases): Add \"Create components\" tasks

**Example task changes:**
- Old: \"Create index.html with sections\"
- New: \"Create component structure: Hero.tsx, About.tsx, Projects.tsx\"

**If using Next.js:**
- Add SSG (Static Site Generation) requirements
- Update deployment section (Vercel instead of GitHub Pages)
- Add file-based routing tasks

---

**Step 3: Personalize Content Requirements**

**Your bio section might include:**
- Research interests (if you're academic)
- Open source contributions (if you're active)
- Speaking engagements (if you do talks)
- Certifications (if relevant to your goals)

**Your project showcase might emphasize:**
- Mobile apps (if you're targeting mobile dev roles)
- Data visualizations (if you're a data engineer)
- Design systems (if you're a design engineer)

**Adapt section 4.2 and 4.3 to reflect your professional narrative.**

---

**Step 4: Adjust Timeline for Your Availability**

**PRD assumes 15 hours over 1 week.**

**If you have less time:**
- Cut animations (save 2 hours)
- Use template for CSS (save 3 hours)
- Feature 2 projects instead of 4 (save 1 hour)

**If you have more time:**
- Add blog section (+4 hours)
- Build backend for form (+6 hours)
- Create custom illustrations (+8 hours)

**Update Section 6 (Implementation Phases) with your revised timeline.**

---

**Step 5: Incorporate Technologies You Want to Learn**

**Want to learn a specific skill? Build it into the project.**

**Examples:**

**Want to learn TypeScript:**
- Change script.js → script.ts
- Add type annotations
- Add TSC build step to Phase 1

**Want to learn testing:**
- Add Section 6.5: \"Testing Phase\"
- Include Jest setup and test writing tasks
- Update acceptance criteria to include test coverage

**Want to learn CI/CD:**
- Add GitHub Actions workflow for deployment
- Add automated Lighthouse CI checks
- Update Phase 6 to include pipeline setup

**Want to learn accessibility:**
- Add more detailed accessibility requirements in Section 5
- Include screen reader testing in verification
- Add ARIA examples in Section 4

---

**Step 6: Scale Scope Based on Capstone Option**

**If doing Option A (Static Portfolio):**
- Use this PRD mostly as-is
- Simplify backend concerns

**If doing Option B (Developer Dashboard):**
- Add sections for:
  - Database schema (Prisma models)
  - API endpoints (backend routes)
  - OAuth implementation details
  - State management (React Context or Zustand)
- Expand Phase 2 to include backend setup
- Add API documentation section

**If doing Option C (n8n-MCP):**
- Completely restructure Section 4 (Features) to focus on:
  - MCP server tools
  - n8n workflow designs
  - Integration specifications
- Replace \"Frontend\" with \"MCP Protocol Implementation\"
- Add sections for:
  - Tool interface definitions
  - Workflow trigger configurations
  - Error handling strategies

---

**Step 7: Tailor Success Criteria to Your Goals**

**Section 1.3: Success Criteria**

**If your goal is learning:**
```
- [ ] Understood OAuth flow deeply (not just copy-paste)
- [ ] Can explain every line of code
- [ ] Documented learnings in blog post
```

**If your goal is job-hunting:**
```
- [ ] Portfolio optimized for ATS (keywords in content)
- [ ] Projects highlight skills in job descriptions
- [ ] Resume download prominently placed
- [ ] Deployed to custom domain (more professional)
```

**If your goal is freelancing:**
```
- [ ] Testimonials section (social proof)
- [ ] Clear service offering description
- [ ] Calendly integration for consultation booking
- [ ] Case studies with ROI metrics
```

---

### PRD Review Checklist

**Before sending your PRD to an AI agent for implementation, verify:**

---

**✅ Completeness Checks**

- [ ] **Section 1 (Overview) answers:**
  - What are we building?
  - Why does it matter?
  - How do we know when it's done?

- [ ] **Section 2 (Scope) is crystal clear:**
  - MVP features listed explicitly
  - Out-of-scope items called out (prevents scope creep)
  - Boundaries defined (e.g., \"max 4 projects\")

- [ ] **Section 3 (Technical Requirements) specifies:**
  - Exact tech stack (versions if critical)
  - Browser support requirements
  - Performance targets with metrics

- [ ] **Section 4 (Features) has acceptance criteria:**
  - Every feature has \"done when...\" criteria
  - Criteria are testable (not subjective)
  - Edge cases considered

- [ ] **Section 6 (Implementation Phases) is actionable:**
  - Tasks broken down to 1-2 hour chunks
  - Clear dependencies (what must finish before next starts)
  - Acceptance criteria per phase

---

**✅ Clarity Assessment**

- [ ] **No ambiguous language:**
  - ❌ \"Should look good\" → ✅ \"Min font size 16px, contrast ratio 4.5:1\"
  - ❌ \"Fast page load\" → ✅ \"First Contentful Paint < 1.5s\"
  - ❌ \"Responsive design\" → ✅ \"Single column <768px, two-column ≥768px\"

- [ ] **Technical terms defined:**
  - If using jargon, include brief explanation
  - Example: \"SSG (Static Site Generation)\"

- [ ] **Examples provided for subjective items:**
  - Color palette (hex codes, not \"blue-ish\")
  - Animation timing (\"0.3s ease-in-out\", not \"smooth\")
  - Tone of voice (\"professional but conversational\", + example)

---

**✅ Agent-Readability Validation**

**AI agents need:**

- [ ] **Explicit acceptance criteria** (how to know task is done)
- [ ] **Out-of-scope clearly stated** (what NOT to do)
- [ ] **Decision authority defined** (what AI can decide vs human must decide)
- [ ] **Priority order** (what to build first)
- [ ] **Testing protocol** (how to verify each phase)

**Test by asking:**
> \"Could an AI agent with no context implement this without asking questions?\"

If answer is no, add more specificity.

---

**✅ Scope Verification**

- [ ] **MVP is truly minimum:**
  - Can it be built in stated timeline?
  - Are all features necessary for core value?
  - Could any feature be deferred to v2?

- [ ] **Scope creep prevention:**
  - Section 2.2 (Out of Scope) is comprehensive
  - Future enhancements section exists for \"nice to haves\"

- [ ] **Realistic timeline:**
  - Buffer time included (10-20% of estimate)
  - Accounts for debugging and iteration
  - Tested against similar projects

---

**✅ Success Criteria Sufficiency**

- [ ] **Functional criteria:**
  - Every feature has pass/fail test
  - Criteria cover happy path AND edge cases

- [ ] **Quality criteria:**
  - Performance: Specific metrics (Lighthouse scores, load time)
  - Accessibility: Testable (keyboard nav, screen reader)
  - Visual: References design spec (colors, spacing)

- [ ] **Learning criteria (for capstone):**
  - AI usage > 50% of implementation?
  - GSD framework followed?
  - Learnings documented?

**Test by asking:**
> \"If I achieve all success criteria, will this be portfolio-worthy?\"

If answer is no, add more criteria.

---

**✅ Final Sanity Checks**

- [ ] **Read PRD out loud** (catches awkward phrasing)
- [ ] **Check for contradictions** (Section 2 says \"no backend\", Section 4 mentions \"API endpoints\")
- [ ] **Verify links work** (if referencing external docs)
- [ ] **Spell check** (Grammarly or similar)
- [ ] **Get feedback** (ask Claude or friend to review)

**Common mistakes to catch:**
- Requirements that conflict with each other
- Acceptance criteria that can't be tested
- Missing decision authority (AI doesn't know if it can choose colors)
- Unrealistic timelines
- Scope too large for stated goal

---

**When you can check all boxes above, your PRD is ready for AI execution. ✅**

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

---

## Pathway Complete! 🎉

**✅ You've completed all 6 sections of the AI Working Enablement & Skill Pathway**

You now have:
- **Ecosystem understanding** — Know when to use assistants, agents, and copilots
- **Tool proficiency** — Hands-on experience with Cursor, GitHub Copilot, Claude Code
- **GSD methodology** — Structured workflows for complex AI-assisted projects
- **Agent delegation skills** — Patterns for autonomous execution and orchestration
- **Skill utilization** — Understand capability packaging and integration
- **Portfolio project** — Real deliverable demonstrating your AI-native workflow

**What's Next?**

1. **Complete your capstone** — Build the portfolio project using tools and patterns from this pathway
2. **Share your work** — Post to Dev.to, LinkedIn, or your personal site
3. **Keep learning** — Revisit sections as you encounter new use cases
4. **Contribute back** — Share your learnings with the community

**Navigation:**
- [← Previous: 5. Skills](../05-skills/README.md)
- [Home: Learning Pathway](../README.md)
- [Start Over: 1. Ecosystem](../01-ecosystem/README.md)

---

*Congratulations on completing the AI Working Enablement & Skill Pathway! You're now equipped to build with AI as a force multiplier.*
