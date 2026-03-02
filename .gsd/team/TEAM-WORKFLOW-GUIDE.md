# Team Collaboration with GitHub Copilot + GSD
**Last Updated:** March 2, 2026  
**For:** Development teams working with GitHub Copilot in VSCode
---
## Overview
This repository uses a **hybrid workflow** combining:
1. **GSD Framework** for planning and verification
2. **GitHub Copilot** for AI-assisted development
3. **VSCode-style instructions** for team consistency
**Team Size:** Optimized for 2-6 developers  
**Best For:** Feature-based development with clear ownership boundaries
---
## Quick Start for New Developers
### 1. Clone and Setup
```bash
# Clone repository
git clone https://github.com/SriSatyaLokesh/System-Design.git
cd System-Design
# Install dependencies (if any)
npm install
# Open in VSCode (GitHub Copilot will auto-load instructions)
code .
```
### 2. Read Project Context
**Before writing any code:**
1. Read [.github/copilot-instructions.md](.github/copilot-instructions.md) - Project standards
2. Read [.gsd/PROJECT.md](.gsd/PROJECT.md) - Project goals and scope
3. Read [.gsd/STATE.md](.gsd/STATE.md) - Current project status
4. Read [.gsd/ROADMAP.md](.gsd/ROADMAP.md) - All phases and plans
5. Check [.gsd/team/ASSIGNMENTS.md](.gsd/team/ASSIGNMENTS.md) - Who''s working on what
### 3. Pick Your Work
```bash
# Check what''s available
cat .gsd/team/ASSIGNMENTS.md
# Example: You''re assigned Phase 05, Plan 02
# Read the plan for detailed tasks
cat .gsd/phases/05-advanced-content/05-02-PLAN.md
```
### 4. Create Feature Branch
```bash
# Pattern: gsd/phase-XX-YY-<short-name>
git checkout -b gsd/phase-05-02-tools
# Update assignments file
vim .gsd/team/ASSIGNMENTS.md  # Mark yourself as owner
git add .gsd/team/ASSIGNMENTS.md
git commit -m "docs: assign Plan 05-02 to @yourusername"
```
### 5. Develop with Copilot
**GitHub Copilot automatically reads:**
- [.github/copilot-instructions.md](.github/copilot-instructions.md) - General guidelines
- [.github/instructions/*.instructions.md](.github/instructions/) - Feature-specific patterns
**Your job:**
- Write commit messages following the format
- Make atomic commits per task
- Update ASSIGNMENTS.md as you progress
```bash
# Work on Task 1
# ... edit files ...
# Commit Task 1
git add "Agentic AI/02-tools/windsurf.md"
git commit -m "feat(05-02): add Windsurf tool guide
- Installation instructions for macOS, Windows, Linux
- Basic usage patterns with examples
- Comparison with Cursor and VSCode
- Curated 6 resources following annotation pattern"
# Work on Task 2
# ... edit files ...
# Commit Task 2
git add "Agentic AI/02-tools/cline.md"
git commit -m "feat(05-02): add Cline tool guide
- Extension installation and setup
- Integration with Claude API
- Example workflows for refactoring
- 5 curated resources with difficulty markers"
```
### 6. Create Pull Request
```bash
# Push your branch
git push origin gsd/phase-05-02-tools
# Create PR on GitHub
# Title: "Complete Phase 05 Plan 02: Additional Tool Guides"
# Description: Link to PLAN.md, list completed tasks
```
### 7. Code Review
**CODEOWNERS will automatically assign reviewers** based on [.github/CODEOWNERS](.github/CODEOWNERS).
**Reviewers check:**
1. **Planning context:** Does code match PLAN.md intent?
2. **Guidelines compliance:** Follows copilot-instructions.md?
3. **Quality standards:** No stubs, proper resource curation (5-7 items)?
4. **Commit format:** Atomic commits with proper messages?
5. **State updates:** ASSIGNMENTS.md reflects progress?
---
## Workflow Patterns
### Pattern 1: Solo Developer on Feature
**Best for:** One developer owns entire phase or plan
```bash
# Tech lead creates plan
/plan-phase 5
# Developer executes entire plan
git checkout -b gsd/phase-05-all
/execute-phase 5  # GSD automates task execution
# Creates single PR with all work
# Includes .gsd/phases/05-*/05-*-SUMMARY.md
```
**Pros:**
- Γ£à Full GSD automation (SUMMARY.md auto-generated)
- Γ£à Verification built-in
- Γ£à Documentation complete
**Cons:**
- Γ¥î Large PRs (harder to review)
- Γ¥î No parallelization within phase
### Pattern 2: Multiple Developers on Phase
**Best for:** Phase has multiple independent plans
```bash
# Tech lead creates all plans
/plan-phase 5  # Creates 05-01, 05-02, 05-03
# Dev A takes Plan 05-01
git checkout -b gsd/phase-05-01-splits
/execute-plan 5-01  # Or manual execution
# Dev B takes Plan 05-02
git checkout -b gsd/phase-05-02-tools
/execute-plan 5-02
# Dev C takes Plan 05-03
git checkout -b gsd/phase-05-03-themes
/execute-plan 5-03
# Each creates separate PR
# Merge to dev branch sequentially or in parallel (if no conflicts)
```
**Pros:**
- Γ£à Parallel development
- Γ£à Smaller PRs (easier review)
- Γ£à Clear ownership per plan
**Cons:**
- ΓÜá∩╕Å Coordinate plan dependencies
- ΓÜá∩╕Å Potential STATE.md conflicts (merge dev branch frequently)
### Pattern 3: Task-Level Assignment
**Best for:** Large plans with independent tasks
```bash
# Tech lead creates plan
/plan-phase 5  # Creates 05-01-PLAN.md with 8 tasks
# Manually assign tasks in ASSIGNMENTS.md
# Dev A: Tasks 1-3
# Dev B: Tasks 4-6
# Dev C: Tasks 7-8
# All work in same branch OR separate task branches
git checkout -b gsd/phase-05-01-splits
# Dev A commits Tasks 1-3
git commit -m "feat(05-01): implement task 1"
git commit -m "feat(05-01): implement task 2"
git commit -m "feat(05-01): implement task 3"
# Dev B rebases on Dev A''s work, commits Tasks 4-6
# Dev C rebases on Dev B''s work, commits Tasks 7-8
# Tech lead manually creates 05-01-SUMMARY.md
# Team creates single PR with all tasks
```
**Pros:**
- Γ£à Fine-grained task distribution
- Γ£à Matches Agile story point workflow
**Cons:**
- Γ¥î Manual SUMMARY.md creation (no GSD automation)
- Γ¥î Requires coordination and rebasing
- Γ¥î More git conflicts
---
## File Structure and Ownership
### Committed to Git
| Path | Owner | Update Frequency | Review Required |
|------|-------|------------------|----------------|
| `.gsd/PROJECT.md` | Tech Lead | Rarely (milestones) | Yes (all leads) |
| `.gsd/ROADMAP.md` | Tech Lead | Per phase | Yes (all leads) |
| `.gsd/STATE.md` | All Developers | Daily | No (auto-update) |
| `.gsd/phases/` | Developer (per phase) | Per task | Yes (code review) |
| `.gsd/team/ASSIGNMENTS.md` | All Developers | Daily | No (self-update) |
| `.github/copilot-instructions.md` | Tech Lead | Rarely | Yes (all leads) |
| `.github/instructions/` | Feature Owner | As needed | Yes (feature team) |
| `.github/CODEOWNERS` | Tech Lead | When team changes | Yes (all leads) |
| `Agentic AI/**` | Developer (per assignment) | Per task | Yes (code review) |
### Not Committed (Local)
| Path | Purpose | Notes |
|------|---------|-------|
| `.gsd/.cache/` | GSD agent cache | Add to .gitignore |
| `node_modules/` | Dependencies | Standard gitignore |
| Local branches | Work in progress | Delete after merge |
---
## GitHub Copilot Integration
### How Copilot Uses These Files
**Auto-loaded on workspace open:**
1. [.github/copilot-instructions.md](.github/copilot-instructions.md)
2. [.github/instructions/*.instructions.md](.github/instructions/) (context-dependent)
**Available via @ references in chat:**
```
@workspace What are the content quality standards?
ΓåÆ Copilot reads .github/instructions/content-quality.instructions.md
@workspace Show me the current project status
ΓåÆ Copilot reads .gsd/STATE.md
@workspace What should I work on next?
ΓåÆ Copilot reads .gsd/team/ASSIGNMENTS.md
```
### Best Practices with Copilot
**1. Start tasks with context:**
```
Me: I''m implementing Task 3 from Plan 05-02. 
    Read @.gsd/phases/05-advanced-content/05-02-PLAN.md
    and help me create the AI code review tools section.
Copilot: [Reads PLAN.md, applies content-quality.instructions.md patterns]
```
**2. Verify quality standards:**
```
Me: Check if this resource list follows our curation standards
    @.github/instructions/content-quality.instructions.md
Copilot: [Checks 5-7 resource limit, annotations, difficulty markers]
```
**3. Generate commit messages:**
```
Me: Generate a commit message for these changes
    following @.github/copilot-instructions.md format
Copilot: feat(05-02): add AI code review tools section
         - Reviewed 12 tools, curated top 6
         - Created comparison table with 7 dimensions
         - Added difficulty markers to all resources
```
---
## Troubleshooting
### STATE.md Merge Conflicts
**Symptom:** Git conflict in `.gsd/STATE.md`
**Solution:**
```bash
# Pull latest
git pull origin dev
# If conflict in STATE.md:
# 1. Keep both versions (your recent activity + theirs)
# 2. Merge "Recent Activity" sections chronologically
# 3. Merge "Key Decisions" sections (keep all unique entries)
# 4. Update "Current Status" to latest
git add .gsd/STATE.md
git commit -m "docs: merge STATE.md conflict"
```
### CODEOWNERS Not Triggering
**Symptom:** PR created but no auto-reviewers assigned
**Check:**
1. CODEOWNERS file in `.github/` (not root)
2. GitHub usernames match exactly (case-sensitive)
3. Path patterns use forward slashes (not backslashes)
4. Repo settings have code owners enabled
### Copilot Not Reading Instructions
**Symptom:** Copilot suggestions don''t follow standards
**Check:**
1. File is named exactly `.github/copilot-instructions.md`
2. Instructions files in `.github/instructions/` directory
3. VSCode restarted after adding files
4. GitHub Copilot extension enabled and authenticated
---
## FAQs
**Q: Do we commit `.gsd/` folder?**  
A: **Yes** - Team collaboration requires shared context. Set `"commit_docs": true` in `.gsd/config.json`.
**Q: Who creates PLAN.md files?**  
A: **Tech Lead** runs `/plan-phase <number>` after roadmap is finalized.
**Q: Can multiple developers edit same file?**  
A: **Avoid it** - Assign ownership boundaries at phase or plan level. If unavoidable, communicate in standup and merge frequently.
**Q: What if I disagree with PLAN.md?**  
A: **Discuss before implementing** - Don''t silently deviate. Update PLAN.md with team agreement, commit change with rationale.
**Q: How granular should commits be?**  
A: **One task = one commit** - If task is too large (>100 lines), break into logical sub-commits but keep task context.
**Q: Do we need GSD framework?**  
A: **For planning: yes. For execution: optional** - Small teams can use manual execution with Copilot instructions only. Larger teams (4+) benefit from full GSD automation.
---
## Additional Resources
- **GSD Framework:** [Agentic AI/03-gsd/README.md](Agentic AI/03-gsd/README.md)
- **GitHub Copilot Docs:** https://docs.github.com/en/copilot
- **CODEOWNERS Syntax:** https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-code-owners
- **VSCode Collaboration Example:** https://github.com/microsoft/vscode (reference implementation)
---
## Getting Help
- **Tech Lead:** @SriSatyaLokesh
- **GitHub Issues:** File issues for blockers or process questions
- **Slack:** #team-agentic-ai (if applicable)
- **Office Hours:** Tuesday/Thursday 2-3 PM
---
**Remember:** 
- ≡ƒôû Read .gsd/STATE.md before starting work
- ≡ƒöä Update .gsd/team/ASSIGNMENTS.md daily
- ≡ƒñû Trust GitHub Copilot but verify against instructions
- ≡ƒÆ¼ Communicate blockers immediately, don''t wait for standup
