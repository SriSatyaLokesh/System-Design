# AI Working Enablement & Skill Pathway

## What This Is

A curated learning resource hub for working effectively with AI tools, agents, and copilots. This is a static content collection organized as a structured pathway - from understanding the AI ecosystem to building real projects with AI assistance.

**Not about:** Building AI models, ML engineering, or neural networks.

**About:** Using AI to accelerate delivery, delegate to agents, work with copilots, and structure work for AI execution.

## Core Value

**Enable anyone to become AI-native contributors** who can effectively collaborate with AI systems to deliver work faster.

The one thing that must work: Clear, actionable learning path from AI basics to hands-on project delivery.

## Implementation

Static content site within System-Design repository:

```
System-Design/
├── Agentic AI/          ← This project
│   ├── 1. Ecosystem/
│   ├── 2. Tools/
│   ├── 3. GSD/
│   ├── 4. Agents/
│   ├── 5. Skills/
│   ├── 6. Capstone/
│   └── README.md
```

Each section contains:
- Curated resource links (courses, videos, docs)
- Brief explanatory content (what, why, when to use)
- Example prompts and workflows
- Progressive learning flow

Capstone includes:
- Your portfolio as reference implementation
- Example prompts showing AI instructions
- Step-by-step guide for learners to adapt

## Tech Stack

- **Content:** Markdown files
- **Hosting:** GitHub Pages
- **Theme:** Jekyll (future enhancement)
- **Structure:** Folder-based navigation

No backend, no LMS, no dynamic features.

## Constraints

- Public repository (open access)
- GitHub Pages compatible
- Simple folder structure (consistent with existing System-Design sections)
- Static files only
- Self-contained (no external dependencies)
- **Git workflow:** Never commit directly to main/master - always work on feature branches
- **Branch strategy:** Create feature branches from dev (if exists) or main

## Success Looks Like

Learners can:
1. Navigate the 6 sections sequentially
2. Access curated resources for each topic
3. Understand AI tool differences (assistants vs agents vs copilots)
4. Follow hands-on tool adoption
5. Learn GSD framework for structured AI execution
6. Explore skill repositories
7. Build their own portfolio using AI (capstone)

Quality bar: Clear enough that someone new to AI tools can follow the path independently.

## Requirements

### Validated

(None yet — new content hub)

### Active

**Content Structure**
- [ ] **STRUCT-01**: Six numbered sections (1. Ecosystem → 6. Capstone)
- [ ] **STRUCT-02**: README.md in Agentic AI/ root with pathway overview
- [ ] **STRUCT-03**: Each section has its own README.md with resources

**1. Ecosystem Section**
- [ ] **ECO-01**: Explain AI assistants (Claude, ChatGPT)
- [ ] **ECO-02**: Explain AI agents (autonomous execution)
- [ ] **ECO-03**: Explain AI copilots (GitHub Copilot, Claude Code)
- [ ] **ECO-04**: Compare chat vs repo AI
- [ ] **ECO-05**: Resources for each platform

**2. Tools Section**
- [ ] **TOOL-01**: Cursor tool guide
- [ ] **TOOL-02**: GitHub Copilot guide
- [ ] **TOOL-03**: Claude Code guide (with Skillshare link)
- [ ] **TOOL-04**: Hands-on exercises for each tool
- [ ] **TOOL-05**: Prompt engineering basics

**3. GSD Framework Section**
- [ ] **GSD-01**: Link to GSD Framework GitHub repo
- [ ] **GSD-02**: Embed/link GSD explainer video
- [ ] **GSD-03**: Explain Goal → Spec → Deliver flow
- [ ] **GSD-04**: PRD-driven execution examples
- [ ] **GSD-05**: Task decomposition guide

**4. Agents Section**
- [ ] **AGENT-01**: What are AI agents vs assistants
- [ ] **AGENT-02**: Agent delegation patterns
- [ ] **AGENT-03**: Multi-agent orchestration concepts
- [ ] **AGENT-04**: Platform-specific agent examples

**5. Skills Section**
- [ ] **SKILL-01**: Explain AI skills/capabilities
- [ ] **SKILL-02**: Skill packaging and integration
- [ ] **SKILL-03**: Link to Claude Skills repo
- [ ] **SKILL-04**: Link to Awesome AI Skills repo
- [ ] **SKILL-05**: Platform skill format comparison table

**6. Capstone Section**
- [ ] **CAP-01**: Project brief (AI-built portfolio)
- [ ] **CAP-02**: Your portfolio as live example
- [ ] **CAP-03**: Prompts you used (with explanations)
- [ ] **CAP-04**: Step-by-step guide for learners
- [ ] **CAP-05**: PRD template for portfolio project
- [ ] **CAP-06**: Technical requirements checklist

**Future Enhancements**
- [ ] **FUTURE-01**: Jekyll theme integration
- [ ] **FUTURE-02**: GitHub Pages deployment
- [ ] **FUTURE-03**: Search functionality
- [ ] **FUTURE-04**: Progress tracking (client-side)

### Out of Scope

- Backend services — Static content only
- User accounts — Public access, no auth
- LMS features — No progress tracking, quizzes, certificates
- Video hosting — Link to external platforms
- AI model training content — Focus is on using AI, not building it
- Deep ML/neural networks — Not the target audience
- Live coding environments — Link to external tools
- Community features — No forums, comments (use GitHub Discussions if needed)

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Static site only | Simplicity, GitHub Pages compatibility, no maintenance | ✓ Approved |
| Folder structure matches repo | Consistency with Caching/, Node JS/, etc. | ✓ Approved |
| No "Phase" prefix | Cleaner naming (1. Ecosystem vs Phase 1: Ecosystem) | ✓ Approved |
| Jekyll theme later | Start simple, enhance when content is stable | — Pending |
| Capstone = portfolio builder | Practical project with your example as reference | ✓ Approved |
| Feature branch workflow | Protect main branch, enable PR reviews | ✓ Approved |

## Context

This is part of your System-Design repository (like Caching/, Node JS/) - a personal knowledge base you're sharing publicly. The AI enablement content follows the same pattern: organized resources with your insights and examples.

Target audience: Anyone wanting to work effectively with AI tools, especially developers/engineers, but accessible to PMs, designers, analysts too.

---

_Last updated: February 25, 2026 after initialization_
