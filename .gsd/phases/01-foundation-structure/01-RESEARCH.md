# Phase 1: Foundation & Structure - Research

**Researched:** February 25, 2026  
**Domain:** Static markdown documentation structure for GitHub rendering  
**Confidence:** MEDIUM

## Summary

Phase 1 creates a markdown-based learning pathway structure within the "Agentic AI/" directory. The user has locked all structural decisions via CONTEXT.md - folder naming, README templates, navigation patterns, and resource formatting are predetermined.

This research focuses on **execution details** the planner needs:
- GitHub Flavored Markdown (GFM) conventions and limitations
- Markdown tooling for validation and quality control
- Common pitfalls in documentation structure (broken links, rendering issues)
- Proven patterns for navigation, TOCs, and learning content organization

Since all architectural decisions are locked, this research emphasizes **implementation mechanics** rather than design alternatives.

**Primary recommendation:** Use markdown linting (`markdownlint`) and link validation during implementation to catch GitHub rendering issues and broken links early.

## Standard Stack

### Core Tools (Documentation Creation)

| Tool              | Purpose                          | Why Standard                                    |
| ----------------- | -------------------------------- | ----------------------------------------------- |
| Markdown          | Content format                   | GitHub native, simple, version-controllable     |
| GFM               | GitHub Flavored Markdown         | Superset with tables, task lists, auto-linking  |
| VS Code           | Editing environment              | Built-in markdown preview, extension ecosystem  |

### Supporting Tools (Quality Control)

| Tool                | Purpose                     | When to Use                                  |
| ------------------- | --------------------------- | -------------------------------------------- |
| `markdownlint`      | Markdown linting            | Enforce consistent formatting, catch errors  |
| `markdown-link-check` | Validate internal/external links | Prevent broken navigation and resource links |
| Local preview       | Test rendering before push  | Verify GitHub Pages compatibility            |

### VS Code Extensions (Optional but Recommended)

| Extension                  | Purpose                        | Value                                         |
| -------------------------- | ------------------------------ | --------------------------------------------- |
| Markdown All in One        | TOC generation, shortcuts      | Auto-generates table of contents              |
| Markdown Preview Enhanced  | Enhanced preview               | Better local rendering simulation             |
| markdownlint (extension)   | Real-time linting              | Catch formatting issues while writing         |

**Installation (if using tools):**
```bash
# For markdown validation (Node.js required)
npm install -g markdownlint-cli
npm install -g markdown-link-check

# Usage
markdownlint "Agentic AI/**/*.md"
markdown-link-check "Agentic AI/README.md"
```

## Architecture Patterns

### Recommended Directory Structure

Based on user decisions, the structure follows numbered learning progression:

```
Agentic AI/
├── README.md                    # Root overview + main TOC
├── 01-ecosystem/
│   ├── README.md               # Section content
│   └── examples/               # Created on-demand (not upfront)
├── 02-tools/
│   ├── README.md
│   └── examples/               # Flat structure when needed
├── 03-gsd/
│   └── README.md
├── 04-agents/
│   └── README.md
├── 05-skills/
│   └── README.md
└── 06-capstone/
    └── README.md
```

**Key principles:**
- **Zero-padded numbering** (01, 02...) ensures proper sorting in file explorers
- **Lowercase with dashes** maximizes cross-platform compatibility
- **Flat examples folders** keeps structure simple, created only when content requires
- **No nesting beyond 2 levels** maintains simplicity for GitHub rendering

### Pattern 1: Root README Organization

**What:** Main entry point with pathway overview, learning objectives, and navigation hub  
**When to use:** Always for documentation collections with multiple sections

**Structure (per user decisions):**
```markdown
# [Pathway Title]

## Learning Objectives
[Upfront statement: "By the end of this pathway, you'll be able to..."]

## Who This Is For
[Audience definition and prerequisites]

## Sections

### 1. [Section Name]
[Paragraph overview]

**Topics covered:**
- [Topic 1]
- [Topic 2]
- [Topic 3]

[Link to section README]

[Repeat for remaining 5 sections]

## Navigation
[Optional: How to use this pathway, suggested order, etc.]
```

**Rationale:**
- **Learning objectives upfront** sets clear expectations immediately
- **Audience/prerequisites** filters self-selection before time investment
- **Paragraph + bullet hybrid** provides both overview and scannable details
- **No time estimates** avoids pressure, maintains self-paced nature

### Pattern 2: Section README Template

**What:** Detailed learning content page with subsection structure and curated resources  
**When to use:** Each of the 6 section folders

**Structure (per user decisions):**
```markdown
# [Section Number]. [Section Name]

## Overview
[Why this section matters + what you'll learn]

## [Main Topic 1]

### [Subtopic 1.1]
[Placeholder: Brief explanation prompt]

### [Subtopic 1.2]
[Placeholder: Brief explanation prompt]

## [Main Topic 2]

### [Subtopic 2.1]
[Placeholder content]

## Resources

### [Resource Title]
- **Type:** Video / Article / Course / Documentation
- **Duration/Length:** 15 min / 2 hours / etc.
- **Level:** Beginner / Intermediate / Advanced
- **Why this matters:** Brief context on what you'll learn
- **Link:** [URL]

[5-7 resources max per section]

## Navigation
**[← Previous: [Section Name]](link)** | **[Next: [Section Name] →](link)**
```

**Key elements:**
- **Overview section** provides context before diving into details
- **Heading hierarchy** uses `##` for main topics, `###` for subtopics
- **Placeholder prompts** guide future content creation without leaving sections empty
- **Structured resources** enforce curation (5-7 max) with clear context
- **Bottom navigation only** avoids redundant top/bottom nav pairs

### Pattern 3: Navigation Link Formatting

**What:** Emphasized markdown links for visual distinction  
**When to use:** Previous/Next navigation, main TOC links

**User's chosen style:**
```markdown
**[← Previous: Ecosystem](../01-ecosystem/README.md)** | **[Next: GSD Framework →](../03-gsd/README.md)**
```

**Alternatives NOT chosen but common:**
```markdown
<!-- Badge style (requires shields.io or similar) -->
[![Previous](https://img.shields.io/badge/Previous-Ecosystem-blue)](link)

<!-- Plain links (less visual) -->
[← Previous: Ecosystem](link) | [Next: GSD Framework →](link)

<!-- Buttons (requires HTML, may not render on all platforms) -->
<kbd>[← Previous]</kbd> <kbd>[Next →]</kbd>
```

**Chosen approach advantages:**
- Works in pure markdown (no HTML, no external services)
- Bold makes navigation visually distinct from body links
- Arrow symbols (← →) provide directional cues
- No custom CSS required, renders consistently on GitHub

### Pattern 4: Table of Contents Generation

**What:** Section-internal navigation to main headings  
**When to use:** Root README (main TOC), each section README (mini-TOC)

**GitHub auto-generates TOC links from headings:**
```markdown
## Table of Contents
- [Overview](#overview)
- [Main Topic 1](#main-topic-1)
  - [Subtopic 1.1](#subtopic-11)
  - [Subtopic 1.2](#subtopic-12)
- [Main Topic 2](#main-topic-2)
- [Resources](#resources)
```

**GitHub anchor rules:**
- Lowercase all text
- Replace spaces with `-`
- Remove special characters (keep alphanumeric and hyphens)
- Example: `## What Are AI Agents?` → `#what-are-ai-agents`

**Tool assistance:** VS Code "Markdown All in One" extension can auto-generate TOCs, but manual creation ensures control over inclusion/exclusion of specific sections.

### Anti-Patterns to Avoid

- **Deep nesting (3+ levels):** GitHub renders deeply nested folders poorly, navigation becomes cumbersome
- **Spaces in folder names:** Works on GitHub but problematic for terminal commands, URL encoding
- **Mixed numbering schemes:** Using both `01-` and `1-` causes sorting confusion
- **Orphaned READMEs:** Every folder should have clear purpose; avoid creating folders "just in case"
- **Duplicate navigation:** Both top and bottom prev/next links create visual clutter without value
- **Vague resource links:** Links without context ("Read this") waste learner time on irrelevant content

## Don't Hand-Roll

Problems that look simple but have existing solutions:

| Problem                     | Don't Build                          | Use Instead                     | Why                                                    |
| --------------------------- | ------------------------------------ | ------------------------------- | ------------------------------------------------------ |
| TOC generation              | Manual anchor link creation          | VS Code extension / script      | Heading changes break manual links, auto-sync safer    |
| Markdown linting            | Custom style checker                 | `markdownlint` (standard rules) | Community-maintained, configurable, widely adopted     |
| Link validation             | Manual clicking through all links    | `markdown-link-check` tool      | Catches broken links before users, CI-integrable       |
| Heading anchor slugification | Custom character replacement logic   | GitHub's auto-generated anchors | Matches GitHub rendering exactly, no guessing          |
| Markdown preview            | Committing to test GitHub rendering  | VS Code preview + local server  | Fast iteration, catches issues before push             |

**Key insight:** Markdown tooling is mature and standardized. Custom scripts for formatting, validation, or generation create maintenance burden without benefit. Use established tools that match GitHub's rendering engine.

## Common Pitfalls

### Pitfall 1: Relative Link Breakage

**What goes wrong:** Links work locally but break on GitHub, or vice versa  
**Why it happens:** Confusion between file paths (`/folder/file.md`) and GitHub's web rendering paths  
**How to avoid:**  
- Use **relative paths from current file location**: `../01-ecosystem/README.md`
- **Always include `.md` extension** for markdown files (GitHub adds or removes it inconsistently)
- Test links by navigating the actual GitHub repository view, not just local preview  
**Warning signs:** Links work in VS Code preview but show 404 on GitHub

**Example - CORRECT:**
```markdown
<!-- In: Agentic AI/02-tools/README.md -->
[Next: GSD Framework →](../03-gsd/README.md)
[Back to Main](../README.md)
```

**Example - BREAKS:**
```markdown
<!-- Absolute paths assume root, won't work in subdirectories -->
[Next](/03-gsd/README.md)

<!-- Missing .md extension may break on some GitHub views -->
[Next](../03-gsd/README)
```

### Pitfall 2: Inconsistent Heading Hierarchy

**What goes wrong:** Skipping heading levels (`##` directly to `####`) breaks TOC generation and accessibility  
**Why it happens:** Visual formatting takes priority over semantic structure  
**How to avoid:**  
- Always increment by **one level** only: `##` → `###` → `####`
- Use `#` for page title (one per file), `##` for main sections, `###` for subsections  
- Run `markdownlint` which flags heading hierarchy violations (MD001 rule)  
**Warning signs:** TOC shows unexpected nesting, screen readers announce confusing structure

**Example - CORRECT:**
```markdown
# Section Title (h1)

## Main Topic (h2)

### Subtopic (h3)

#### Detail (h4)
```

**Example - WRONG:**
```markdown
# Section Title (h1)

### Subtopic (h3) ← Skipped h2, breaks hierarchy
```

### Pitfall 3: GitHub-Specific Markdown Assumptions

**What goes wrong:** Using GitHub-specific features that break in other markdown renderers  
**Why it happens:** Testing only on GitHub, assuming GFM is universal markdown  
**How to avoid:**  
- Stick to **CommonMark + GFM basics** (tables, task lists, code blocks)
- Avoid GitHub-specific embeds (videos, 3D models) if portability matters  
- Test with standard markdown preview to catch GitHub-only features  
**Warning signs:** Content looks perfect on GitHub but broken in local preview or other platforms

**GitHub-specific (may not be portable):**
- `[!NOTE]` callout syntax (GitHub-only as of 2024)
- Mermaid diagrams (GitHub renders, many tools don't)
- Auto-linking of issues/PRs (`#123` → link)

**Portable alternatives:**
- Callouts: Use bold + blockquote (`> **Note:** ...`)
- Diagrams: Link to image files instead of inline code
- References: Use explicit links, not GitHub magic syntax

### Pitfall 4: Examples Folder Premature Creation

**What goes wrong:** Creating empty `examples/` folders "for future use" clutters structure  
**Why it happens:** Attempting to "get structure done" before understanding what examples are needed  
**How to avoid:**  
- **Create examples folders only when first example is ready** (per user decision)
- Document planned examples in section README if needed, but don't create folder yet  
- Avoids "empty directory" commits that add no value  
**Warning signs:** Multiple empty folders in repository, unclear what they're for

**User's decision (from CONTEXT):** "Examples folder: Create only when needed (not upfront)"

### Pitfall 5: Resource Link Rot

**What goes wrong:** External links break over time (content moves, sites go down)  
**Why it happens:** No validation or maintenance plan for external URLs  
**How to avoid:**  
- Use `markdown-link-check` in CI/CD pipeline to detect broken links  
- Prefer **stable, authoritative sources** (official docs over blog posts)
- Include **archive links** (archive.org) for critical resources at risk of disappearing  
- Date-stamp resources so users know if content may be outdated  
**Warning signs:** Users report broken links, no systematic way to detect them

**Best practice for this phase:** Plan to run `markdown-link-check` after adding resources in Phase 2, but establish the expectation now.

## Code Examples

Verified patterns for common operations:

### Example 1: Root README Structure (Main TOC)

```markdown
# Agentic AI Learning Pathway

## Learning Objectives

By the end of this pathway, you'll be able to:
- Understand the AI assistant/agent/copilot ecosystem and choose the right tool
- Work effectively with GitHub Copilot and Claude Code
- Apply the GSD framework to structure AI-driven projects
- Build and delegate work to AI agents
- Compose AI skills for complex workflows
- Deliver a portfolio project using AI tools

## Who This Is For

**Target audience:** Developers and technical professionals looking to integrate AI tools into their workflow.

**Prerequisites:**
- Basic programming knowledge (any language)
- Familiarity with Git/GitHub
- Comfort with command-line tools

**Not required:** Machine learning background, AI development experience

## Sections

### 1. Ecosystem
Understanding the landscape of AI assistants, agents, and copilots. This section helps you understand what tools exist and when to use each type.

**Topics covered:**
- AI assistants (Claude, ChatGPT)
- AI agents (autonomous execution)
- AI copilots (GitHub Copilot, Claude Code)
- Chat vs repository AI
- Platform selection guide

[Go to Ecosystem →](01-ecosystem/README.md)

### 2. Tools
Hands-on guide to using Antigravity, GitHub Copilot, and Claude Code. Learn setup, workflows, and effective prompting.

**Topics covered:**
- Antigravity tool setup and workflows
- GitHub Copilot installation and patterns
- Claude Code integration
- Practical exercises
- Prompt engineering basics

[Go to Tools →](02-tools/README.md)

[Continue pattern for sections 3-6...]

---

**Ready to start?** Begin with [1. Ecosystem](01-ecosystem/README.md)
```

### Example 2: Section README Template (Ecosystem Example)

```markdown
# 1. Ecosystem

## Overview

Understanding the AI tool landscape is crucial for choosing the right approach for your work. This section explains the differences between assistants, agents, and copilots, helping you match tools to your needs.

**What you'll learn:**
- How AI assistants, agents, and copilots differ
- When to use chat interfaces vs. repository-aware tools
- How to choose the right AI platform for different tasks

## Table of Contents
- [AI Assistants](#ai-assistants)
- [AI Agents](#ai-agents)
- [AI Copilots](#ai-copilots)
- [Decision Matrix](#decision-matrix)
- [Resources](#resources)

## AI Assistants

### What Are AI Assistants?

[Placeholder: Explain what AI assistants are - chat interfaces like Claude and ChatGPT that respond to prompts but don't execute code or access external systems directly.]

### When to Use AI Assistants

[Placeholder: Best for brainstorming, explaining concepts, writing drafts, answering questions. Not ideal for: code execution, file manipulation, long-running tasks.]

### Examples

[Placeholder: Concrete use cases - writing documentation, debugging logic, learning new concepts, generating test data.]

## AI Agents

### What Are AI Agents?

[Placeholder: Explain agents as autonomous systems that can execute actions, use tools, and complete multi-step tasks with minimal supervision.]

### When to Use AI Agents

[Placeholder: Best for automated workflows, complex multi-step tasks, integration with external tools. Requires clear goals and validation steps.]

### Examples

[Placeholder: Use cases - automated testing, data processing pipelines, code refactoring, report generation.]

## AI Copilots

### What Are AI Copilots?

[Placeholder: Explain copilots as embedded AI that works alongside you in your development environment, aware of your codebase context.]

### When to Use AI Copilots

[Placeholder: Best for active coding sessions, code completion, refactoring suggestions. Works within existing workflow rather than replacing it.]

### Examples

[Placeholder: GitHub Copilot suggesting function implementations, Claude Code making multi-file edits, contextual code explanations.]

## Decision Matrix

| AI Type     | Best For                  | Context Awareness | Autonomy  | Examples                 |
| ----------- | ------------------------- | ----------------- | --------- | ------------------------ |
| Assistant   | Q&A, brainstorming        | Conversation only | Low       | ChatGPT, Claude          |
| Agent       | Multi-step automation     | Tool/API access   | High      | Custom agents, AutoGPT   |
| Copilot     | Real-time code assistance | Full codebase     | Medium    | GitHub Copilot, Cursor   |

[Placeholder: Add "How to choose" decision tree or flowchart description]

## Resources

### Understanding AI Assistants
- **Type:** Article
- **Duration/Length:** 10 min
- **Level:** Beginner
- **Why this matters:** Foundation for understanding how chat-based AI works and its limitations
- **Link:** [URL placeholder]

### Introduction to AI Agents
- **Type:** Video
- **Duration/Length:** 20 min
- **Level:** Beginner
- **Why this matters:** See agents in action and understand autonomous execution patterns
- **Link:** [URL placeholder]

[Continue pattern for 3-5 more resources...]

## Navigation

**[Next: Tools →](../02-tools/README.md)**
```

### Example 3: Resource Listing Format (User-Specified)

```markdown
## Resources

### Building Your First AI Agent
- **Type:** Video
- **Duration/Length:** 30 min
- **Level:** Intermediate
- **Why this matters:** Step-by-step walkthrough shows practical agent implementation with real code examples. Focuses on delegation patterns and error handling—two areas beginners struggle with.
- **Link:** https://example.com/ai-agent-tutorial

### GitHub Copilot Documentation
- **Type:** Documentation
- **Duration/Length:** Ongoing reference
- **Level:** All levels
- **Why this matters:** Official reference for all Copilot features, keyboard shortcuts, and settings. Bookmark this for quick lookup during development.
- **Link:** https://docs.github.com/copilot

### Prompt Engineering Guide
- **Type:** Course
- **Duration/Length:** 2 hours
- **Level:** Beginner to Intermediate
- **Why this matters:** Learn how to craft effective prompts that get better AI responses. Covers common mistakes and advanced techniques like chain-of-thought prompting.
- **Link:** https://example.com/prompt-engineering

[5-7 resources total per section]
```

**Key elements enforced by template:**
- **Type** clarifies format expectation (video vs reading)
- **Duration** helps learners plan time investment
- **Level** manages expectations about difficulty
- **Why this matters** prevents "link dump" by adding curation context
- **Link** always last, after context is established

### Example 4: Navigation Link Implementation

```markdown
<!-- At bottom of section README -->

---

## Navigation

**[← Previous: Ecosystem](../01-ecosystem/README.md)** | **[Next: GSD Framework →](../03-gsd/README.md)**
```

**Implementation notes:**
- Horizontal rule (`---`) separates navigation from content
- Bold emphasis (`**[...]**`) makes navigation visually distinct
- Arrow symbols (`←` and `→`) provide direction cues
- Pipe (`|`) separator between previous/next
- Relative paths from current file location
- `.md` extension always included

**For first section (no previous):**
```markdown
**[Next: Tools →](../02-tools/README.md)**
```

**For last section (no next):**
```markdown
**[← Previous: Skills](../05-skills/README.md)**
```

## State of the Art

| Old Approach                               | Current Approach                             | When Changed   | Impact                                               |
| ------------------------------------------ | -------------------------------------------- | -------------- | ---------------------------------------------------- |
| Wiki-style documentation                   | Markdown in repository                       | ~2015          | Version control, pull requests, CI/CD integration    |
| Manually maintained TOCs                   | Auto-generated from headings                 | Ongoing        | Reduces maintenance, ensures accuracy                |
| Custom documentation sites                 | GitHub Pages with minimal/no setup           | ~2018          | Lower barrier to publishing, free hosting            |
| Loose markdown conventions                 | GFM standardization + linting                | ~2017          | Consistent formatting, fewer rendering bugs          |
| Documentation separate from code           | Docs-as-code (same repo, same workflow)      | ~2014          | Docs stay in sync with code changes                  |
| Time-based learning paths ("Week 1, Day 2") | Self-paced without pressure                  | Ongoing trend  | Respects varied learning speeds, reduces dropoff     |

**Deprecated/outdated:**
- **Read the Docs** for simple markdown sites: Still valid for complex projects, but GitHub Pages is simpler for static content
- **GitBook**: Was popular ~2015-2018, but maintenance and pricing made GitHub-native approaches more attractive
- **Jekyll-only GitHub Pages**: GitHub now supports multiple static site generators, but plain markdown (no generator) is often sufficient

**Current best practices (2026):**
- Plain markdown + GitHub rendering (no generator needed for simple pathways)
- Linting in CI pipeline (catch issues in PRs, not after merge)
- Link validation automated (don't rely on manual checking)
- Mobile-first structure (GitHub mobile app, responsive rendering)

## Open Questions

### 1. GitHub Pages Activation

**What we know:** PROJECT.md mentions "GitHub Pages (future enhancement)" and "Jekyll (future enhancement)"  
**What's unclear:** Whether Phase 1 should include GitHub Pages setup or if plain GitHub markdown rendering is sufficient initially  
**Recommendation:** **Defer to Phase 4 (Polish)**. Plain GitHub repository viewing works immediately; Pages activation can be added later without restructuring. No technical blocker to decide now.

### 2. Link Validation Tooling Integration

**What we know:** `markdown-link-check` exists and is recommended  
**What's unclear:** Whether to integrate into CI/CD during Phase 1 or add later when content exists  
**Recommendation:** **Document tool during Phase 1, integrate during Phase 2**. No links exist yet to validate; mentioning the tool in structure documentation ensures it's not forgotten when links are added.

### 3. Local Preview Setup

**What we know:** VS Code has built-in markdown preview  
**What's unclear:** Whether to recommend additional local server setup for GitHub Pages simulation  
**Recommendation:** **VS Code preview sufficient for Phase 1**. If GitHub Pages activated later, add local server setup at that time. Avoid premature complexity.

## Sources

### Primary (HIGH confidence)

- GitHub Flavored Markdown Spec: https://github.github.com/gfm/ (official standard)
- GitHub Docs - Basic writing and formatting syntax: https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax
- CommonMark Specification: https://commonmark.org/ (GFM foundation)

### Secondary (MEDIUM confidence)

- Markdown style guides (Google, Microsoft): Industry conventions for documentation
- markdown-link-check repository: https://github.com/tcort/markdown-link-check (widely-used tool)
- markdownlint repository: https://github.com/DavidAnson/markdownlint (standard linter)
- VS Code Markdown extensions marketplace: Common tooling ecosystem

### Tertiary (LOW confidence - based on training data)

- Learning pathway organization patterns: Best practices from online course platforms (Coursera, Udemy structure)
- Documentation site conventions: Patterns from popular open-source project docs
- Resource curation standards: Educational content design principles

**Note on confidence:** Much of this research draws on markdown best practices and documentation conventions that are well-established but not centrally specified. GitHub's official documentation provides HIGH confidence for GFM syntax; architectural patterns (folder structure, navigation) are MEDIUM confidence based on industry conventions rather than official standards.

## Metadata

**Confidence breakdown:**
- Standard stack: **MEDIUM** - Markdown tooling is mature but specific tool choices (markdownlint vs alternatives) based on popularity, not formal standards
- Architecture: **MEDIUM** - User decisions are locked (HIGH confidence on WHAT to build), but execution details (link paths, anchor format) based on GFM conventions (MEDIUM)
- Pitfalls: **MEDIUM** - Based on common documentation issues and GitHub-specific behavior, verified through GitHub docs where applicable
- Code examples: **HIGH** - All examples follow user's CONTEXT decisions and GFM specification

**Research date:** February 25, 2026  
**Valid until:** ~90 days (markdown/GFM stable, tooling updates infrequent)  
**Revalidate if:** GitHub announces GFM changes, new documentation features, or Pages rendering updates
