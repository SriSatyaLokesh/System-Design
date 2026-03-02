# System Design Repository - GitHub Copilot Instructions
## Project Overview
Educational content repository teaching AI-native development workflows. Built using the GSD (Goal ΓåÆ Spec ΓåÆ Deliver) framework for structured content creation and project management.
**Purpose:** Enable learners to become AI-native contributors through curated learning pathways.
## Repository Structure
```
System-Design/
Γö£ΓöÇΓöÇ .gsd/                    # GSD Framework metadata (planning artifacts)
Γöé   Γö£ΓöÇΓöÇ PROJECT.md          # Project scope and goals
Γöé   Γö£ΓöÇΓöÇ ROADMAP.md          # Phase-based roadmap
Γöé   Γö£ΓöÇΓöÇ STATE.md            # Current status and decisions
Γöé   ΓööΓöÇΓöÇ phases/             # Phase-specific plans and summaries
Γö£ΓöÇΓöÇ .github/
Γöé   Γö£ΓöÇΓöÇ copilot-instructions.md  # This file
Γöé   Γö£ΓöÇΓöÇ instructions/       # Feature-specific guidelines
Γöé   Γö£ΓöÇΓöÇ skills/             # GSD workflow orchestration
Γöé   ΓööΓöÇΓöÇ agents/             # Specialized AI agents
Γö£ΓöÇΓöÇ Agentic AI/             # Learning content (main deliverable)
Γöé   Γö£ΓöÇΓöÇ 01-ecosystem/       # AI tools taxonomy
Γöé   Γö£ΓöÇΓöÇ 02-tools/           # Hands-on tool guides
Γöé   Γö£ΓöÇΓöÇ 03-gsd/             # GSD framework education
Γöé   Γö£ΓöÇΓöÇ 04-agents/          # Agent building
Γöé   Γö£ΓöÇΓöÇ 05-skills/          # Advanced patterns
Γöé   ΓööΓöÇΓöÇ 06-capstone/        # Portfolio project
ΓööΓöÇΓöÇ [other System-Design sections]
```
## Team Collaboration Model
### Workflow
1. **Planning:** Tech lead uses GSD to create phases and plans in `.gsd/`
2. **Assignment:** Use `.gsd/team/ASSIGNMENTS.md` for task ownership
3. **Development:** Developers work in feature branches following these instructions
4. **Review:** CODEOWNERS automatically assigns reviewers based on affected areas
### Branch Strategy
- **Main branch:** Production-ready content
- **Feature branches:** `feature/<area>-<description>` or `gsd/phase-<XX>-<name>`
- **Commit format:** `<type>(<phase>-<plan>): <description>` (see Git Integration below)
## Coding Standards for Educational Content
### Content Structure
- **Hierarchical headings:** Use ##, ###, #### (never single #)
- **Progressive complexity:** Beginner ΓåÆ Intermediate ΓåÆ Advanced
- **Concrete examples:** Always include specific tool names, commands, or code
- **Comparison tables:** Use markdown tables for comparing options
### Content Quality Rules
1. **Curation over comprehensiveness:** 5-7 resources maximum per topic
2. **Context required:** Every link needs "What, Why included, Best for, Time estimate"
3. **Difficulty markers:** Use ≡ƒƒó Beginner, ≡ƒƒí Intermediate, ≡ƒö┤ Advanced
4. **No stub content:** Every section must be substantive (200+ lines minimum)
5. **Mobile-friendly:** GitHub-native markdown (no complex HTML)
### Markdown Conventions
```markdown
## Section Title
**What:** [1-2 sentence definition]
**Key Characteristics:**
- Point 1
- Point 2
- Point 3
**Examples:**
- **Tool A** - Specific use case
- **Tool B** - Specific use case
**When to Use:**
[Scenario-based guidance]
### Comparison Framework
| Dimension | Option 1 | Option 2 | Option 3 |
|-----------|----------|----------|----------|
| ...       | ...      | ...      | ...      |
### Resources
**≡ƒôÜ Resource Name** - [Link](url)
- **What:** Brief description
- **Why included:** Value proposition
- **Best for:** Target audience/use case
- **Time:** Estimated reading/watching time
- **Free:** Yes/No
```
### Anti-Patterns
- Γ¥î Link dumps without context
- Γ¥î Generic advice without specific examples
- Γ¥î Stub sections with "Coming soon"
- Γ¥î More than 7 resources per topic
- Γ¥î Comparison tables with inconsistent dimensions
## Git Integration
### Commit Message Format
Follow GSD's atomic task commit pattern:
```
<type>(<phase>-<plan>): <task-description>
- [Key change 1]
- [Key change 2]
- [Key change 3]
```
**Types:**
- `feat` - New feature/content
- `docs` - Documentation updates
- `fix` - Bug fix
- `refactor` - Code cleanup
- `chore` - Dependencies, config
**Examples:**
```bash
# Content creation
git commit -m "docs(02-01): create AI ecosystem taxonomy
- Added assistants, agents, copilots definitions
- Created 3-way comparison table with 6 dimensions
- Curated 7 resources with contextual annotations"
# Planning completion
git commit -m "docs(02-01): complete ecosystem content plan
Tasks completed: 3/3
SUMMARY: .gsd/phases/02-01-SUMMARY.md"
```
### Files to Always Commit
- Content files (`Agentic AI/**`)
- Planning artifacts (`.gsd/phases/**`)
- Metadata updates (`.gsd/STATE.md`, `.gsd/ROADMAP.md`)
- Configuration (`.gsd/config.json` if changed)
## GSD Framework Integration
When working with GSD artifacts:
### Reading Context
- **Before starting:** Read `.gsd/STATE.md` for current project status
- **For your phase:** Read `.gsd/phases/XX-name/XX-YY-PLAN.md` for task details
- **For decisions:** Check `key-decisions` in SUMMARY.md files
### Creating Content
- **Follow the plan:** Task descriptions in PLAN.md are prescriptive
- **Document decisions:** Update SUMMARY.md with choices made during implementation
- **Track patterns:** Note reusable patterns in `patterns-established` section
### Quality Verification
- **Line count:** Content sections should be 500+ lines (substantive, not stub)
- **Resource count:** Exactly 5-7 curated resources per topic
- **Difficulty markers:** Every resource should have ≡ƒƒó/≡ƒƒí/≡ƒö┤
- **Navigation:** Each README.md should have breadcrumbs and next/previous links
## Feature-Specific Guidelines
When working on specific areas, also read:
- **Content Creation:** @.github/instructions/content-quality.instructions.md
- **GSD Workflow:** @.github/instructions/gsd-workflow.instructions.md
- **Verification:** @.github/instructions/verification-patterns.instructions.md
## Common Tasks
### Adding New Content Section
1. Read `.gsd/phases/XX-name/XX-YY-PLAN.md` for structure
2. Create substantive content following quality rules above
3. Add 5-7 curated resources with annotations
4. Add difficulty markers (≡ƒƒó≡ƒƒí≡ƒö┤)
5. Integrate navigation (breadcrumbs, prev/next)
6. Commit per task: `docs(XX-YY): <task-name>`
### Reviewing PRs
1. Check PLAN.md to understand intent
2. Verify SUMMARY.md documents decisions
3. Confirm content quality (no stubs, proper curation)
4. Verify commit format follows GSD patterns
5. Check navigation integration
### Updating Existing Content
1. Check `.gsd/STATE.md` for context
2. Read SUMMARY.md for original decisions
3. Make changes preserving established patterns
4. Update STATE.md if decisions change
5. Commit: `docs: update <section> - <reason>`
## Key Principles
1. **Codebase as documentation:** README files are learning materials, not just reference
2. **Outcomes over process:** Commit completed work, not intermediate planning
3. **Context preservation:** SUMMARY.md files capture "why" for future developers
4. **Quality over quantity:** 5-7 excellent resources beats 30 mediocre links
5. **AI-native workflow:** Use GitHub Copilot + GSD for all development
## Questions?
- **GSD Framework:** See `Agentic AI/03-gsd/README.md`
- **Contributing:** See `CONTRIBUTING.md` (if exists)
- **Issues:** Check `.gsd/STATE.md` for known blockers
