---
description: Content quality standards for Agentic AI learning materials
---
## Content Quality Standards
### Resource Curation Pattern
When adding educational resources to any section:
**Rule: 5-7 Resources Maximum**
- Quality over quantity - curate, don''t dump
- Each resource must earn its place
- Remove low-value links ruthlessly
**Required Annotations:**
```markdown
**≡ƒôÜ Resource Name** - [Link](url)
- **What:** [One sentence describing content]
- **Why included:** [Why this resource vs alternatives]
- **Best for:** [Target audience or use case]
- **Time:** [Reading/watching time estimate]
- **Free:** Yes / No / Freemium
```
**Example:**
```markdown
**≡ƒÄÑ GitHub Copilot Complete Guide** - [Course](https://example.com)
- **What:** Comprehensive video course covering GitHub Copilot features
- **Why included:** Most up-to-date tutorial with real project examples
- **Best for:** Developers new to AI pair programming
- **Time:** 2.5 hours
- **Free:** No (\\\)
```
### Difficulty Markers
Use emoji markers consistently:
- ≡ƒƒó **Beginner** - No prior knowledge needed
- ≡ƒƒí **Intermediate** - Basic familiarity with topic required
- ≡ƒö┤ **Advanced** - Deep technical knowledge needed
**Usage:**
```markdown
### Resources
≡ƒƒó **Getting Started with AI** - [Guide](...)
≡ƒƒí **Building Custom Agents** - [Tutorial](...)
≡ƒö┤ **LangChain Architecture Deep Dive** - [Talk](...)
```
### Comparison Tables
When comparing tools, frameworks, or approaches:
**Required Dimensions:**
- Use consistent columns across all tables in same section
- 6-8 dimensions maximum (cognitive load limit)
- Include "Best For" or "When to Use" dimension
**Example:**
```markdown
| Dimension | GitHub Copilot | Cursor | Claude Code |
|-----------|----------------|--------|-------------|
| Integration | IDE-native | IDE-native | Chat-based |
| Context | Current file | Multi-file | Entire repo |
| Autonomy | Suggestions | Mixed | Autonomous |
| Best For | Inline coding | Refactoring | Architecture |
```
### Substantive Content Test
**Minimum Requirements:**
- Main section README: 500+ lines
- Subsection content: 200+ lines
- No placeholder text ("Coming soon", "TODO", "TBD")
- Every heading has content (no empty sections)
**Verification:**
```bash
# Check line count
wc -l "Agentic AI/01-ecosystem/README.md"
# Should be > 500 for main sections
```
### Navigation Integration
Every README.md should include:
**Breadcrumbs (top):**
```markdown
[Home](../../README.md) > [Agentic AI](../README.md) > Ecosystem
```
**Progress Marker:**
```markdown
**Section 1 of 6** | ΓÅ▒∩╕Å 25 min read
```
**What''s Next (bottom):**
```markdown
---
## What''s Next?
**Continue the pathway:**  
≡ƒæë [Tools & Setup](../02-tools/README.md) - Hands-on tool installation and workflows
**Alternative paths:**
- Skip to [GSD Framework](../03-gsd/README.md) if experienced with AI tools
- Jump to [Capstone](../06-capstone/README.md) to see final portfolio example
```
### Anti-Patterns to Avoid
Γ¥î **Link Dumps**
```markdown
Resources:
- https://example1.com
- https://example2.com
- https://example3.com
```
Γ£à **Proper Curation**
```markdown
### Resources
**≡ƒôÜ Resource 1** - [Link](...)
- **What:** ...
- **Why included:** ...
```
Γ¥î **Stub Sections**
```markdown
## Advanced Topics
Coming soon!
```
Γ£à **Complete Content**
```markdown
## Advanced Topics
[500+ lines of actual content]
```
Γ¥î **Inconsistent Comparisons**
```markdown
| Tool | Good | Bad |  ΓåÉ Vague dimensions
```
Γ£à **Specific Dimensions**
```markdown
| Tool | Context Scope | Autonomy Level | Interaction Mode |
```
## Quality Checklist
Before marking content complete:
- [ ] 5-7 curated resources with full annotations
- [ ] All resources have difficulty markers (≡ƒƒó≡ƒƒí≡ƒö┤)
- [ ] Minimum line counts met (500+ for main sections)
- [ ] No stub sections or placeholder text
- [ ] Comparison tables use consistent dimensions
- [ ] Navigation integrated (breadcrumbs + what''s next)
- [ ] Mobile-friendly (tested on GitHub mobile view)
- [ ] All links tested and working
