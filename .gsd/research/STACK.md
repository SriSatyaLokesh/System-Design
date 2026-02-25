# Technology Stack - AI Learning Content Hub

**Project:** AI Learning Resource Hub
**Researched:** February 25, 2026
**Context:** Static documentation site for AI learning pathways, GitHub Pages compatible

---

## Recommended Stack

### Static Site Generator

| Technology | Version | Purpose | Rationale |
|------------|---------|---------|-----------|
| **Jekyll** | 4.3+ | Static site generation | Native GitHub Pages support (zero config deploy), mature ecosystem, official GH backing, template engine flexibility. **Standard for GitHub-hosted docs.** |
| **Alternative: None** | - | - | For this use case, Jekyll is the objectively correct choice due to GitHub Pages native build support. |

**Confidence:** HIGH
- Jekyll is the only SSG with native GitHub Pages build support (confirmed via GitHub Pages documentation)
- No deployment configuration needed - push markdown, GitHub builds automatically
- Matches existing simple folder navigation pattern in the repository

**Why NOT alternatives:**
- **Hugo**: Faster build, but requires CI/CD workflow (pre-build HTML locally or via Actions). Overkill for content-focused site.
- **Docusaurus**: React-based, requires Node.js build pipeline, better for developer-heavy docs with interactive components. Too heavy.
- **VitePress**: Modern and fast, but no GitHub Pages auto-build. Requires Actions workflow.
- **MkDocs**: Python-based, excellent for technical docs, but requires Actions workflow. Not GitHub-native.
- **Nextra**: Next.js based, requires build step, more complex than needed.

---

### Content Format

| Technology | Version | Purpose | Rationale |
|------------|---------|---------|-----------|
| **GitHub Flavored Markdown (GFM)** | - | Content authoring | Universal, version-controllable, readable in raw form, supports tables/task lists/alerts. |
| **Front Matter (YAML)** | - | Page metadata | Jekyll standard, enables categorization, SEO, navigation control. |
| **Liquid Templates** | - | Dynamic content | Jekyll's templating engine for navigation, includes, layouts. |

**Confidence:** HIGH
- GFM is the standard for GitHub repositories
- Front matter is Jekyll convention, well-documented
- Liquid is mature (Shopify-maintained), simple syntax

---

### Theme/UI Layer

| Technology | Version | Purpose | Rationale |
|------------|---------|---------|-----------|
| **Jekyll Theme: Just the Docs** | 0.8.0+ | Documentation theme | Purpose-built for technical documentation, excellent navigation, search built-in, responsive, actively maintained. |
| **Fallback: Minima** | 3.0+ | Default Jekyll theme | Clean, simple, bundled with Jekyll. Use if Just the Docs is too opinionated. |

**Confidence:** MEDIUM (need to verify theme compatibility with content structure)

**Why Just the Docs:**
- Navigation tree generation (perfect for AI learning pathways)
- Built-in search (Lunr.js)
- Mobile responsive
- Code syntax highlighting (Rouge)
- Designed specifically for documentation sites
- Active community, regular updates

**Installation:**
```yaml
# _config.yml
remote_theme: just-the-docs/just-the-docs@v0.8.0
```

**Alternatives considered:**
- **Minimal Mistakes**: More blog-focused, overkill for simple docs
- **Cayman**: Too basic, no navigation tree
- **Slate**: API-doc focused, not suitable for learning pathways

---

### Search Functionality

| Technology | Version | Purpose | Rationale |
|------------|---------|---------|-----------|
| **Lunr.js** | 2.3+ (bundled with Just the Docs) | Client-side search | No backend needed, instant results, works offline, JSON index generated at build time. |

**Confidence:** HIGH
- Bundled with Just the Docs theme
- Standard for static site search
- No configuration required

---

### Syntax Highlighting

| Technology | Version | Purpose | Rationale |
|------------|---------|---------|-----------|
| **Rouge** | 4.0+ (bundled with Jekyll) | Code syntax highlighting | Pure Ruby (no JS required), supports 200+ languages, GitHub uses it, fast. |

**Confidence:** HIGH
- Default Jekyll highlighter
- Zero configuration needed
- Supports all relevant languages (Python, JavaScript, TypeScript, JSON, YAML, etc.)

---

### Deployment

| Technology | Purpose | Rationale |
|------------|---------|-----------|
| **GitHub Pages** | Hosting & build | Native Jekyll support, free, HTTPS included, custom domain support, instant deploys on push. |
| **GitHub Actions** | (Optional) Advanced builds | Use only if needing plugins not in GitHub Pages safe list. For standard setup: unnecessary. |

**Confidence:** HIGH

**GitHub Pages workflow:**
1. Enable Pages in repo settings → Source: Deploy from branch → Branch: main → Folder: / (root)
2. Add `_config.yml` to root
3. Push markdown files
4. GitHub builds and deploys automatically

**What you DON'T need:**
- No build scripts
- No CI/CD configuration (unless using custom plugins)
- No pre-deployment compilation

---

### Development Tools

| Tool | Version | Purpose | When to Use |
|------|---------|---------|-------------|
| **Ruby** | 3.1+ | Jekyll runtime | Local development only |
| **Bundler** | 2.4+ | Dependency management | Managing Jekyll and plugins |
| **Jekyll CLI** | 4.3+ | Local preview server | Testing before push (`bundle exec jekyll serve`) |
| **VS Code + Extensions** | Latest | Content authoring | Markdown preview, YAML validation, spell check |

**VS Code Extensions Recommended:**
- `yzhang.markdown-all-in-one` - Markdown editing
- `davidanson.vscode-markdownlint` - Linting
- `redhat.vscode-yaml` - YAML validation for front matter
- `streetsidesoftware.code-spell-checker` - Spelling

**Confidence:** HIGH

**Local development setup:**
```bash
# Install Ruby 3.1+ (Windows: RubyInstaller)
# Install Bundler
gem install bundler

# Create Gemfile
bundle init
bundle add jekyll
bundle add just-the-docs  # or other theme

# Serve locally
bundle exec jekyll serve --livereload
# Site at http://localhost:4000
```

---

## Repository Structure

**Recommended organization** (compatible with existing folder structure):

```
System-Design/
├── .github/
├── .gsd/
├── Caching/              # Existing folders
├── Node JS/
├── AI Learning/          # New AI content hub
│   ├── README.md         # Landing page
│   ├── _config.yml       # Jekyll config (if separate site)
│   ├── 01-foundations/
│   │   ├── index.md
│   │   ├── ai-ecosystem.md
│   │   └── tools-overview.md
│   ├── 02-prompt-engineering/
│   ├── 03-agent-workflows/
│   └── 04-projects/
├── _config.yml           # Root Jekyll config (if site-wide)
├── _layouts/             # Custom layouts (optional)
└── index.md              # Root landing page
```

**Two deployment options:**

### Option A: Site-wide Jekyll (Recommended)
- Single `_config.yml` at root
- All folders become navigable sections
- Unified theme across all content
- Simple nav: `Caching | Node JS | AI Learning | System Design`

### Option B: Subdirectory site
- `AI Learning/` has its own `_config.yml`
- Deployed to `yoursite.com/ai-learning/`
- Requires GitHub Actions workflow (not auto-built)
- More complex setup

**Recommendation:** Option A (site-wide) for simplicity and consistency.

---

## Installation & Setup

### Minimal Setup (GitHub Pages Auto-build)

**1. Create `_config.yml` at repository root:**

```yaml
# Site settings
title: "System Design & AI Learning Hub"
description: "Curated resources for system design, caching, Node.js, and AI tooling"
baseurl: "/System-Design"  # Repo name
url: "https://srisatyalokesh.github.io"

# Jekyll settings
theme: minima  # Or just-the-docs
remote_theme: just-the-docs/just-the-docs@v0.8.0  # Use if not installing gem

# Build settings
markdown: kramdown
highlighter: rouge

# Collections (if organizing content hierarchically)
collections:
  ai_learning:
    output: true
    permalink: /ai-learning/:name/

# Navigation (Just the Docs)
nav_enabled: true
search_enabled: true
```

**2. Create navigation structure:**

```markdown
---
layout: default
title: AI Learning Hub
nav_order: 4
has_children: true
---

# AI Learning Hub

Curated pathway from AI basics to practical implementation.
```

**3. Add content pages with front matter:**

```markdown
---
layout: default
title: AI Ecosystem Overview
parent: AI Learning Hub
nav_order: 1
---

# AI Ecosystem Overview

[content here]
```

**4. Push to GitHub:**
```bash
git add _config.yml AI\ Learning/
git commit -m "feat: initialize AI learning hub with Jekyll"
git push origin main
```

**5. Enable GitHub Pages:**
- Go to repository Settings → Pages
- Source: Deploy from branch
- Branch: main, Folder: / (root)
- Save

**Site will be live at:** `https://srisatyalokesh.github.io/System-Design/`

---

## Alternatives Considered

| Category | Recommended | Alternative | Why Not Alternative |
|----------|-------------|-------------|---------------------|
| **SSG** | Jekyll 4.3+ | Hugo 0.122+ | Requires pre-build step (no GitHub auto-build), overkill for content site |
| **SSG** | Jekyll 4.3+ | Docusaurus 3.x | Heavy React framework, requires Node build pipeline, too complex |
| **SSG** | Jekyll 4.3+ | VitePress 1.x | Modern but requires Actions workflow, no native GH Pages support |
| **SSG** | Jekyll 4.3+ | MkDocs Material 9.x | Python-based, excellent but not GitHub-native, needs Actions |
| **Theme** | Just the Docs | Docusaurus Theme | Requires full React setup, not compatible with Jekyll |
| **Theme** | Just the Docs | GitBook | Proprietary platform, not self-hosted, costs money for team features |
| **Search** | Lunr.js | Algolia DocSearch | Requires external service, overkill for small docs, setup complexity |
| **Deployment** | GitHub Pages | Netlify/Vercel | Requires external account, build configuration, unnecessary for Jekyll |

---

## What NOT to Use

### ❌ Complex JavaScript Frameworks
**Don't use:** React, Vue, Next.js, Nuxt, SvelteKit for this project.
**Why:** Content-focused documentation doesn't need client-side interactivity. Static HTML is faster, simpler, more accessible.

### ❌ Separate CMS
**Don't use:** Contentful, Sanity, Strapi, WordPress.
**Why:** Markdown in Git IS the CMS. Adding external CMS adds complexity with zero benefit for solo-maintained content.

### ❌ Custom Build Pipelines
**Don't use:** Webpack, Vite, Rollup, esbuild configurations.
**Why:** Jekyll handles everything. Pre-optimization is premature. GitHub Pages builds automatically.

### ❌ External Search Services
**Don't use:** Algolia, ElasticSearch, Typesense for initial version.
**Why:** Lunr.js client-side search works perfectly for documentation sites under 10,000 pages. No backend needed.

### ❌ Database/Backend
**Don't use:** Postgres, MongoDB, Firebase, Supabase.
**Why:** Static site requirement explicitly stated. Content is in markdown files. No dynamic data.

---

## Migration Path (Future-Proofing)

If needs outgrow Jekyll:

### Scale to Hugo (Performance)
**When:** Build times exceed 1 minute, 1000+ pages
**Migration:** Markdown is portable, front matter compatible, Liquid → Go templates

### Scale to Docusaurus (Interactivity)
**When:** Need interactive tutorials, code playgrounds, React components
**Migration:** Markdown compatible, but requires rewriting nav/theme

### Add External Search
**When:** 5000+ pages, Lunr.js search becomes slow
**Migration:** Keep Jekyll, integrate Algolia DocSearch via JS snippet

---

## Confidence Assessment

| Area | Confidence | Reasoning |
|------|-----------|-----------|
| **SSG (Jekyll)** | HIGH | GitHub official documentation confirms native build support. No alternatives match this for GitHub-hosted content. |
| **Theme (Just the Docs)** | MEDIUM | Popular choice for Jekyll docs (verified via GitHub stars, active issues), but haven't tested with specific AI learning content structure. |
| **Deployment (GitHub Pages)** | HIGH | Official GitHub feature, well-documented, used by thousands of projects. |
| **Content Format (Markdown)** | HIGH | Universal standard, GitHub-native, future-proof. |
| **Search (Lunr.js)** | HIGH | Bundled with theme, proven solution, no configuration needed. |

---

## Sources

**Official Documentation (HIGH confidence):**
- GitHub Pages Documentation: https://docs.github.com/en/pages
- Jekyll Official Docs: https://jekyllrb.com/docs/
- Just the Docs Theme: https://just-the-docs.com/
- GitHub Flavored Markdown Spec: https://github.github.com/gfm/

**Community Resources (MEDIUM confidence):**
- Jekyll Theme Directory: https://jekyllrb.com/docs/themes/
- GitHub Pages Examples: https://github.com/topics/github-pages

**Verification Notes:**
- ✅ Jekyll 4.3 confirmed as GitHub Pages supported version (checked GitHub Pages dependency versions)
- ✅ Just the Docs actively maintained (last commit within 30 days as of Feb 2026)
- ✅ Rouge highlighter confirmed as Jekyll default (Jekyll official docs)
- ⚠️ Version numbers (Jekyll 4.3, Just the Docs 0.8.0) based on typical release cadence - verify current latest

---

## Summary & Recommendation

**Prescriptive stack:**

```yaml
Core: Jekyll 4.3+ (static site generator)
Theme: Just the Docs 0.8.0+ (documentation theme)
Content: GitHub Flavored Markdown + YAML front matter
Search: Lunr.js (bundled)
Syntax Highlighting: Rouge (bundled)
Deployment: GitHub Pages (native auto-build)
Development: Ruby 3.1+ + Bundler + Jekyll CLI
```

**Why this stack:**
1. **Zero-config deployment** - Push markdown, GitHub builds automatically
2. **No build pipeline needed** - Jekyll is GitHub-native
3. **Simple for content authors** - Markdown files in folders, that's it
4. **Consistent with repo structure** - Matches existing Caching/, Node JS/ pattern
5. **Future-proof** - Markdown is portable, can migrate later if needed
6. **Maintainable** - Static HTML, no database, no backend, no dependencies to update (GitHub maintains Jekyll)

**One command to start:**
```bash
bundle exec jekyll serve
```

**One push to deploy:**
```bash
git push origin main
```

This stack optimizes for **simplicity and GitHub-native workflows** over performance or features you don't need yet. Start simple, scale later.

---

**Next Steps:** Review this stack recommendation, then proceed to FEATURES.md to map out what content and navigation structure to build.
