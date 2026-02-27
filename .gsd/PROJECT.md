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

**Phase 1: Foundation & Structure** (Completed 2026-02-25)
- ✓ **STRUCT-01**: Six numbered sections (1. Ecosystem → 6. Capstone) — Phase 1
- ✓ **STRUCT-02**: README.md in Agentic AI/ root with pathway overview — Phase 1
- ✓ **STRUCT-03**: Each section has its own README.md with resources — Phase 1

**Phase 2: Foundational Learning Content** (Completed 2026-02-26)
- ✓ **ECO-01**: Explain AI assistants (Claude, ChatGPT) with use cases — Phase 2
- ✓ **ECO-02**: Explain AI agents (autonomous execution) with examples — Phase 2
- ✓ **ECO-03**: Explain AI copilots (GitHub Copilot, Claude Code) with integration patterns — Phase 2
- ✓ **ECO-04**: Compare chat vs repo AI with decision matrix — Phase 2
- ✓ **ECO-05**: Curated resource links (5-7 max) with context — Phase 2
- ✓ **TOOL-01**: Cursor tool guide with setup and workflows — Phase 2
- ✓ **TOOL-02**: GitHub Copilot guide with installation and usage patterns — Phase 2
- ✓ **TOOL-03**: Claude Code guide with Skillshare link and learnings — Phase 2
- ✓ **TOOL-04**: Hands-on exercises for each tool with outcomes — Phase 2
- ✓ **TOOL-05**: Prompt engineering basics with examples and anti-patterns — Phase 2

**Phase 3: Advanced Concepts & Frameworks** (Completed 2026-02-27)
- ✓ **GSD-01**: Link to GSD Framework GitHub repo — Phase 3
- ✓ **GSD-02**: Embed/link GSD explainer video — Phase 3
- ✓ **GSD-03**: Explain Goal → Spec → Deliver flow — Phase 3
- ✓ **GSD-04**: PRD-driven execution examples — Phase 3
- ✓ **GSD-05**: Task decomposition guide — Phase 3
- ✓ **AGENT-01**: What are AI agents vs assistants — Phase 3
- ✓ **AGENT-02**: Agent delegation patterns — Phase 3
- ✓ **AGENT-03**: Multi-agent orchestration concepts — Phase 3
- ✓ **AGENT-04**: Platform-specific agent examples — Phase 3
- ✓ **SKILL-01**: Explain AI skills/capabilities — Phase 3
- ✓ **SKILL-02**: Skill packaging and integration — Phase 3
- ✓ **SKILL-03**: Link to Claude Skills repo — Phase 3
- ✓ **SKILL-04**: Link to Awesome AI Skills repo — Phase 3
- ✓ **SKILL-05**: Platform skill format comparison table — Phase 3

**Phase 4: Capstone & Polish** (Completed 2026-02-27)
- ✓ **CAP-01**: Project brief for AI-built portfolio — Phase 4
- ✓ **CAP-02**: Your portfolio as live example — Phase 4
- ✓ **CAP-03**: Prompts you used with strategy explanations — Phase 4
- ✓ **CAP-04**: Step-by-step guide for learners to build portfolio — Phase 4
- ✓ **CAP-05**: PRD template prefilled with example — Phase 4
- ✓ **CAP-06**: Technical requirements checklist (HTML/CSS/JS, responsive, deployment) — Phase 4
- ✓ **NAV-01**: Breadcrumbs showing current location in path — Phase 4
- ✓ **NAV-02**: Previous/Next navigation links between sections — Phase 4
- ✓ **NAV-03**: Mobile-responsive markdown rendering (GitHub native) — Phase 4
- ✓ **NAV-04**: Clear progression markers (1 of 6, prerequisites noted) — Phase 4
- ✓ **NAV-05**: Skip links for experienced users (optional paths) — Phase 4
- ✓ **QUAL-01**: Strict curation criteria (5-7 resources max per topic) — Phase 4
- ✓ **QUAL-02**: Each resource link includes context (what, why, when) — Phase 4
- ✓ **QUAL-03**: Difficulty markers on content (beginner/intermediate/advanced) — Phase 4
- ✓ **QUAL-04**: Prerequisite chains documented for each section — Phase 4
- ✓ **QUAL-05**: "What's next" guidance at end of each section — Phase 4

### Active

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
| Unified comparison framework | 6 consistent dimensions (Autonomy, Integration, Interaction, Persistence, Best For, Workflow) provide cognitive clarity | ✓ Implemented Phase 2 |
| Text-based ASCII diagrams | Maintains accessibility and GitHub mobile compatibility without image dependencies | ✓ Implemented Phase 2 |
| Exactly 7 curated resources | Research-backed 5-7 rule prevents link dump perception while ensuring comprehensive coverage | ✓ Implemented Phase 2 |
| ASCII diagrams for workflows | Visual clarity without image dependencies maintains accessibility | ✓ Implemented Phase 3 |
| Complete command reference | 32 GSD commands documented with examples enables practical adoption | ✓ Implemented Phase 3 |
| Real portfolio example | Used SriSatyaLokesh portfolio as authentic reference (not hypothetical) with transparency about AI contributions | ✓ Implemented Phase 4 |
| 13 actual prompts shown | Documented real prompts from development (not "example: ask for...") showing planning→implementation→polish sequence | ✓ Implemented Phase 4 |
| Consistent navigation | Breadcrumbs, prev/next links, progression markers using GitHub-native markdown for mobile compatibility | ✓ Implemented Phase 4 |
| 100% quality compliance | 5-7 resources per section, contextual annotations, difficulty markers, prerequisites documented | ✓ Implemented Phase 4 |

## Context

This is part of your System-Design repository (like Caching/, Node JS/) - a personal knowledge base you're sharing publicly. The AI enablement content follows the same pattern: organized resources with your insights and examples.

Target audience: Anyone wanting to work effectively with AI tools, especially developers/engineers, but accessible to PMs, designers, analysts too.

---

_Last updated: February 27, 2026 after v1.0 milestone completion_
