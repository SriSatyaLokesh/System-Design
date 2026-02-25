---
created: 2026-02-25T23.22
title: Complete remaining content in GSD, Agents, and Skills sections
area: docs
files:
  - Agentic AI/03-gsd/README.md
  - Agentic AI/04-agents/README.md
  - Agentic AI/05-skills/README.md
---

## Problem

Sections 03 (GSD Framework), 04 (Agents), and 05 (Skills) have placeholder content that needs completion:

**Section 03 - GSD Framework (70% complete):**
- PRD details section still placeholder - needs concrete examples
- Task decomposition section needs more detailed examples
- Should reference best PRD template: https://github.com/SriSatyaLokesh/best-prd-template
- Should mention Claude Code and Copilot with awesome-copilot plugin have PRD writing skills

**Section 04 - Agents (70% complete):**
- "Delegation Patterns" section is placeholder - needs when/how to delegate guidance
- "Multi-Agent Orchestration" section is placeholder - needs parallel vs sequential patterns, communication patterns, orchestration tools

**Section 05 - Skills (40% complete):**
- "Platform Ecosystems" section is placeholder - needs detailed comparison of:
  - GitHub Copilot Extensions
  - ChatGPT GPTs  
  - Claude MCP
  - Including: how to build, distribution, monetization, discovery

All sections have solid frameworks and 6+ curated resources each, but these gaps prevent them from being truly complete and providing full learning value.

## Solution

1. **Section 03 (GSD) - Add PRD guidance:**
   - Add concrete PRD examples (feature breakdown, acceptance criteria)
   - Link to best PRD template repo
   - Mention AI tools with PRD skills (Claude Code, Copilot + awesome-copilot)
   - Add task decomposition examples with dependencies

2. **Section 04 (Agents) - Complete delegation patterns:**
   - When to delegate vs do manually
   - How to structure effective delegation prompts
   - Handling agent failures and iteration
   - Multi-agent orchestration patterns (parallel, sequential, hierarchical)
   - Communication between agents
   - Tools: LangGraph, CrewAI, AutoGPT examples

3. **Section 05 (Skills) - Platform ecosystem comparison:**
   - Create comprehensive comparison table
   - Building process for each platform
   - Distribution and discovery mechanisms
   - Monetization options
   - Developer experience differences
   - When to choose which platform

Priority: Start with Section 03 PRD template info (user specifically requested), then complete Sections 04-05.
