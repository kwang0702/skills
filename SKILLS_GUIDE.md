# Skills Reference Guide

A comprehensive reference for all skills in this repository. Use this to quickly identify which skill to apply for any given scenario.

---

## Quick Reference Table

| Skill | Best For | Trigger Keywords |
|-------|----------|-----------------|
| [superpowers](#superpowers) | Full software development lifecycle | build, debug, plan, test, code review |
| [pua](#pua) | Force AI to keep trying when stuck | AI gives up, repeated failures, excuses |
| [claude-mem](#claude-mem) | Persistent memory across sessions | remember, recall, previous session context |
| [web-access](#web-access) | Web browsing, scraping, automation | search web, browse, login, scrape, social media |
| [agent-skills](#agent-skills) | React/Next.js, web design, deployment | React component, Next.js, Vercel deploy, animation |
| [ui-ux-pro-max](#ui-ux-pro-max) | UI design systems, styles, palettes | build UI, design dashboard, landing page, design system |
| [design-for-ai](#design-for-ai) | Visual design theory, auditing | font choice, color palette, layout, visual hierarchy |
| [anthropics/algorithmic-art](#algorithmic-art) | Generative art with p5.js | generative art, flow field, particle system, algorithmic |
| [anthropics/brand-guidelines](#brand-guidelines) | Anthropic brand styling | Anthropic brand, branded artifact, company design |
| [anthropics/canvas-design](#canvas-design) | Visual posters, artwork, PDF/PNG output | poster, artwork, visual design, canvas |
| [anthropics/claude-api](#claude-api) | Building apps with Claude API | anthropic SDK, claude API, LLM app, build with Claude |
| [anthropics/doc-coauthoring](#doc-coauthoring) | Collaborative document writing | write doc, draft spec, PRD, proposal, decision doc |
| [anthropics/docx](#docx) | Word document creation and editing | .docx, Word document, create doc, edit Word |
| [anthropics/frontend-design](#frontend-design) | Distinctive production-grade UI | build landing page, design website, create component |
| [anthropics/internal-comms](#internal-comms) | Internal company communications | status report, newsletter, 3P update, FAQ |
| [anthropics/mcp-builder](#mcp-builder) | Building MCP servers | MCP server, tool integration, connect API via MCP |
| [anthropics/pdf](#pdf) | PDF read/create/edit/extract | read PDF, extract tables, merge PDF, create PDF |
| [anthropics/pptx](#pptx) | PowerPoint presentations | create deck, edit slides, make presentation |
| [anthropics/skill-creator](#skill-creator) | Creating and iterating on new skills | create skill, optimize skill, benchmark skill |
| [anthropics/slack-gif-creator](#slack-gif-creator) | Animated GIFs for Slack | Slack GIF, animated emoji, Slack animation |
| [anthropics/theme-factory](#theme-factory) | Apply color/font themes to artifacts | style deck, apply theme, color slides |
| [anthropics/web-artifacts-builder](#web-artifacts-builder) | Complex React/shadcn artifacts | interactive app, complex artifact, React component |
| [anthropics/webapp-testing](#webapp-testing) | Testing web apps with Playwright | test app, verify UI, check functionality, screenshot |
| [anthropics/xlsx](#xlsx) | Excel spreadsheet creation and editing | .xlsx, Excel, spreadsheet, financial model |

---

## Top-Level Skills

---

### superpowers

**Location:** `superpowers/`
**Source:** https://github.com/obra/superpowers

**What it does:**
A complete software development workflow system that orchestrates the full engineering lifecycle — from design and planning through implementation, testing, code review, and deployment. Think of it as a methodology layer on top of Claude Code.

**When to use:**
- Starting any non-trivial coding project
- Debugging a complex issue
- Planning a new feature
- Writing tests for existing code
- Doing structured code review

**Key capabilities:**
- Socratic design refinement (Brainstorming before building)
- Git worktree management for parallel development
- Implementation planning broken into bite-sized tasks
- Subagent-driven development with two-stage review
- Test-driven development (RED → GREEN → REFACTOR cycle)
- Systematic debugging with 4-phase root cause analysis

**How to invoke:**
Skills activate automatically based on context. Can also manually trigger via `/plugin install superpowers@claude-plugins-official`.

**Limitations:**
- Designed for code projects primarily
- Enforces TDD approach — verification before completion
- Best for structured, non-trivial projects (overkill for tiny scripts)

---

### pua

**Location:** `pua/`
**Source:** https://github.com/tanweai/pua

**What it does:**
Forces AI agents to exhaust every possible solution before giving up. Uses systematic debugging methodology wrapped in corporate motivational rhetoric to eliminate lazy patterns like blaming the user, pushing problems back manually, or passive waiting.

**When to use:**
- AI has failed 2+ times on the same task
- AI is about to give up or say "I can't do this"
- AI is making excuses instead of trying
- AI is pushing the problem back to you to solve manually
- AI is in a brute-force retry loop without diagnosis

**Key capabilities:**
- 7-point debugging checklists
- Enforces active tool usage (WebSearch, Read, Bash, etc.)
- Prevents excuse-making and passive waiting
- Stops guessing — requires systematic investigation
- Compatible with: Claude Code, Cursor, Codex, Kiro, and others

**How to invoke:**
Triggers automatically on failure patterns. Manual: `/pua`

**Limitations:**
- Deliberately pushy/aggressive tone (by design)
- Does not allow giving up — requires resolution or clear diagnosis
- Not suitable for genuinely impossible tasks (it will keep pushing anyway)

---

### claude-mem

**Location:** `claude-mem/`
**Source:** https://github.com/thedotmack/claude-mem

**What it does:**
Persistent memory system for Claude Code sessions. Captures tool usage and semantic summaries from each session, stores them in a searchable database, and injects relevant context into future sessions automatically.

**When to use:**
- Long-running projects spanning multiple sessions
- When you need Claude to remember past decisions, bugs, or context
- When you want cross-session continuity without re-explaining everything

**Key capabilities:**
- 5 lifecycle hooks (SessionStart, UserPromptSubmit, PostToolUse, Stop, SessionEnd)
- SQLite database with FTS5 full-text search
- Chroma vector database for semantic similarity search
- `mem-search` skill for natural language memory queries
- Progressive disclosure: search → timeline → detailed observations
- Web viewer UI at `http://localhost:37777`
- Private content tagging (`<private>content</private>`)

**How to invoke:**
Install once: `/plugin install claude-mem`. Runs automatically after installation — no manual activation per session.

**Requirements:** Node.js 18+, Bun, uv, SQLite 3

**Limitations:**
- AGPL-3.0 license
- Runs as background worker service (persistent process)
- Requires initial setup of dependencies

---

### web-access

**Location:** `web-access/`
**Source:** https://github.com/eze-is/web-access

**What it does:**
Complete web browsing and automation capabilities. Goes beyond simple fetching — handles login-required sites, real mouse interaction, DOM manipulation, screenshots, and multi-tab parallel operations via Chrome CDP.

**When to use:**
- Searching the web for information
- Reading content from specific URLs
- Accessing sites that require login
- Scraping social media (小红书, WeChat, Twitter/X)
- Filling forms and clicking through UIs
- Extracting video frame content
- Multi-target research in parallel

**Key capabilities:**
- WebSearch / WebFetch / curl / Jina / CDP browser operation
- 3 click methods: `/click` (JS), `/clickAt` (real mouse), `/setFiles` (file upload)
- `/eval` for DOM exploration and manipulation
- `/screenshot` for visual capture including video frames
- Tab management and parallel CDP operations
- Domain-specific pattern accumulation (learns site behavior over time)

**How to invoke:**
Install: `/plugin marketplace add https://github.com/eze-is/web-access` then `/plugin install web-access`. Activates automatically for network tasks.

**Requirements:** Node.js 22+, Chrome with remote debugging port enabled, CDP proxy

**Limitations:**
- Requires Chrome running with `--remote-debugging-port` flag
- Documentation is primarily in Chinese

---

### agent-skills

**Location:** `agent-skills/`
**Source:** https://github.com/vercel-labs/agent-skills

**What it does:**
A collection of best-practice coding skills from Vercel covering React optimization, web design guidelines, React Native, view transitions, composition patterns, and one-click Vercel deployment.

**When to use:**
- Building or reviewing React / Next.js components
- Writing React Native mobile code
- Implementing animations or view transitions
- Designing component APIs and avoiding boolean prop sprawl
- Deploying to Vercel

**Key capabilities:**
- `react-best-practices`: 40+ performance rules across 8 categories (waterfalls, rendering, bundle size, etc.)
- `web-design-guidelines`: 100+ accessibility and UX rules
- `react-native-guidelines`: 16 mobile optimization rules
- `react-view-transitions`: View Transition API patterns
- `composition-patterns`: Avoiding boolean prop proliferation
- `vercel-deploy-claimable`: One-click deployments with shareable claim URLs

**How to invoke:**
`npx skills add vercel-labs/agent-skills`. Skills auto-activate based on context (e.g., React code detected).

**Limitations:**
- React/JavaScript ecosystem only
- Vercel-specific deployment patterns
- Requires npm/Node.js

---

### ui-ux-pro-max

**Location:** `ui-ux-pro-max/`
**Source:** https://github.com/nextlevelbuilder/ui-ux-pro-max-skill

**What it does:**
AI-powered design intelligence with an enormous library of industry-specific design rules, UI styles, color palettes, and font pairings. Generates complete design systems tailored to product type.

**When to use:**
- Building any landing page, dashboard, or web app UI
- Choosing a visual style for a product
- Generating a complete design system from scratch
- Selecting colors, fonts, or UI style for a specific industry
- Design reviews requesting style recommendations

**Key capabilities:**
- 161 product-type reasoning rules (SaaS, fintech, healthcare, e-commerce, etc.)
- 67 UI styles (glassmorphism, claymorphism, brutalism, Y2K, cyberpunk, minimalism, etc.)
- 161 color palettes matched to industries
- 57 font pairings with Google Fonts
- 99 UX guidelines
- 25 chart type recommendations
- Design System Generator: analyzes requirements → outputs complete system
- Multi-stack: React, Next.js, Vue, Svelte, SwiftUI, Flutter, React Native, Tailwind, and more

**How to invoke:**
Install: `/plugin marketplace add nextlevelbuilder/ui-ux-pro-max-skill`. Or CLI: `npm install -g uipro-cli && uipro init --ai claude`.

**Requirements:** Python 3.x

**Limitations:**
- Best for structured UI design, not freeform creative art
- Design system generation is complex and multi-step

---

### design-for-ai

**Location:** `design-for-ai/`
**Source:** Static (based on *Design for Hackers* by David Kadavy) — no upstream updates

**What it does:**
Visual design theory and principles applied to AI-assisted design. Operates in two modes: auditing existing designs (CHECKER) and building new designs from scratch (APPLIER).

**When to use:**
- Choosing fonts or building a type scale
- Building or reviewing a color palette
- Establishing visual hierarchy in a layout
- Auditing an existing design for problems
- Making responsive design decisions
- Adding motion or interaction design
- Any frontend code that needs visual design direction

**Key capabilities:**
- **CHECKER mode**: 10-phase design audit checklist (visual hierarchy, typography, color, spacing, etc.)
- **APPLIER mode**: 8-phase structured design build process
- Squint test for visual hierarchy validation
- Color science (colorblindness accessibility, hue-shifted shadows)
- Proportional systems (golden ratio, 2:3, 3:4 ratios)
- Motion and interaction state mapping
- Anti-AI-tells focus (avoids generic AI aesthetics)

**Quick commands:**
- `/design` — Set up design foundations
- `/exam` — Full design audit
- `/brand` — Strip AI tells, add character
- `/fonts` — Typography selection
- `/color` — Color system building
- `/flow` — Motion, interaction, responsive
- `/hone` — Final quality pass

**Limitations:**
- Theory-heavy — requires design principle understanding to get the most value
- Static file — will not receive updates
- No external dependencies

---

## Anthropic Skills

All located in `anthropics/skills/`

---

### algorithmic-art

**Location:** `anthropics/skills/algorithmic-art/`

**What it does:**
Creates generative/algorithmic art using p5.js. Emphasizes craft, mathematical beauty, and reproducible randomness. Produces a philosophy document paired with an interactive HTML artifact.

**When to use:**
- "Create generative art"
- "Make a flow field visualization"
- "Build a particle system"
- "Create algorithmic/procedural art"
- Creative coding requests

**Key capabilities:**
- Seeded randomness (reproducible, explorable)
- p5.js implementation with interactive controls
- Parameter exploration UI (sliders, seed navigation, color pickers)
- Gallery-mode seed navigation
- Output: philosophy .md + single self-contained HTML artifact

**Limitations:**
- p5.js only (no other graphics frameworks)
- Requires genuine aesthetic intent — not just random noise

---

### brand-guidelines

**Location:** `anthropics/skills/brand-guidelines/`

**What it does:**
Applies Anthropic's official brand identity to any artifact — colors, typography, and visual style.

**When to use:**
- Any artifact needing Anthropic brand styling
- Consistent design standards across company content
- Branded HTML pages, slides, or documents

**Key capabilities:**
- Anthropic color palette: Dark `#141413`, Light `#faf9f5`, Orange `#d97757`, Blue `#6a9bcc`, Green `#788c5d`
- Typography: Poppins (headings) + Lora (body)
- System-font fallbacks for compatibility
- Accent color cycling across content sections

**Limitations:**
- Anthropic-specific only — not for general brand work
- Limited to Anthropic colors and fonts

---

### canvas-design

**Location:** `anthropics/skills/canvas-design/`

**What it does:**
Creates museum/magazine-quality visual art, posters, and design as PDF or PNG files. Design philosophy is expressed through form, space, color, and composition — not just decoration.

**When to use:**
- "Create a poster"
- "Design artwork"
- "Make a visual asset"
- Professional visual design output to file

**Key capabilities:**
- Design philosophy creation (4–6 paragraph conceptual framing)
- Subtle conceptual threading embedded in the art
- Multi-page capability
- Typography as visual element (not decoration)
- Output: design philosophy .md + .pdf or .png file(s)

**Limitations:**
- Must be museum/magazine quality — no amateur-looking output
- Text is minimal and integrated into design
- Requires custom font selection for each piece

---

### claude-api

**Location:** `anthropics/skills/claude-api/`

**What it does:**
Comprehensive guide for building applications with the Claude API and Anthropic SDKs. Covers everything from simple single calls to complex agent workflows.

**When to use:**
- Code imports `anthropic`, `@anthropic-ai/sdk`, or `claude_agent_sdk`
- Building an app that uses Claude as a backend
- Implementing tool use, streaming, or agentic patterns
- Choosing between models or configuring API parameters

**Key capabilities:**
- Multi-language: Python, TypeScript, Java, Go, Ruby, C#, PHP, cURL
- Decision tree: single call vs. workflow vs. agent
- All Claude models: Opus 4.6, Sonnet 4.6, Haiku 4.5
- Adaptive thinking (`thinking: {type: "adaptive"}`)
- Prompt caching strategies
- Tool use and agent patterns
- Structured outputs, batches, files API, token counting
- Streaming for long requests

**Defaults to apply:**
- Model: Claude Opus 4.6 unless specified otherwise
- Thinking: adaptive mode
- Long requests: streaming
- Endpoint: `/v1/messages`

**Limitations:**
- Requires API key management
- Extensive — many language/pattern variants to navigate

---

### doc-coauthoring

**Location:** `anthropics/skills/doc-coauthoring/`

**What it does:**
Structured multi-stage workflow for collaboratively writing documentation, proposals, specs, and decision docs with high quality.

**When to use:**
- "Write a doc / spec / proposal"
- "Draft a PRD or decision document"
- Internal documentation that needs to be clear to readers unfamiliar with context

**Key capabilities:**
- **Stage 1:** Context gathering — clarifying questions + info dump
- **Stage 2:** Refinement — section brainstorming → curation → drafting → iteration
- **Stage 3:** Reader testing — fresh Claude reads to catch blind spots
- Integration with shared docs (Google Drive, Slack, etc. if available)
- Progressive artifact editing

**Limitations:**
- Multi-stage — time-consuming for simple docs
- Requires human participation throughout
- Best for documents with real external readers

---

### docx

**Location:** `anthropics/skills/docx/`

**What it does:**
Create, read, edit, and manipulate `.docx` Word documents with full formatting support including tables, headers, footers, tracked changes, and comments.

**When to use:**
- "Create a Word document"
- "Edit a .docx file"
- "Extract content from a Word doc"
- Any `.docx` file work

**Key capabilities:**
- docx-js for new document creation
- XML unpacking/repacking for editing existing files
- pandoc for text extraction
- Tables (with strict dual-width spec for compatibility)
- Images, hyperlinks, footnotes, bookmarks
- Tracked changes and comments
- Headers, footers, page breaks, tab stops

**Critical rules (will cause issues if ignored):**
- Always set page size explicitly (not A4 by default)
- Use DXA units: 1440 DXA = 1 inch
- Tables need `columnWidths` AND cell `width` — both must match
- Use `ShadingType.CLEAR` not `SOLID` for table shading
- Never use Unicode bullets (use `LevelFormat.BULLET`)
- Smart quotes as XML entities

**Limitations:**
- LibreOffice needed for some conversions
- Complex XML editing for existing docs

---

### frontend-design

**Location:** `anthropics/skills/frontend-design/`

**What it does:**
Creates distinctive, production-grade frontend interfaces with intentional, bold aesthetic direction. Explicitly avoids generic AI aesthetics.

**When to use:**
- "Build a landing page / website / component"
- Any UI build request where visual quality matters
- When the user wants something that doesn't look like AI-generated slop

**Key capabilities:**
- Bold aesthetic direction (brutalism, minimalism, luxury, playful, editorial, etc.)
- Custom typography (not Inter/default fonts)
- Cohesive color theming via CSS variables
- Animation and micro-interactions
- Spatial composition (asymmetry, overlap, diagonal flow)
- Background effects (gradients, noise, patterns, textures)
- Responsive implementation

**Anti-patterns (always avoid):**
- Inter font + purple gradients + centered layout
- Uniform rounded corners
- Predictable/cookie-cutter component patterns
- Generic AI aesthetic

**Limitations:**
- Requires committed aesthetic direction — no "just make it look nice"
- Complex animations require detailed implementation

---

### internal-comms

**Location:** `anthropics/skills/internal-comms/`

**What it does:**
Writes internal company communications in the correct format and tone using company guidelines.

**When to use:**
- "Write a status report"
- "Create a company newsletter"
- "Draft a 3P update (Progress, Plans, Problems)"
- "Write an FAQ / project update / incident report"

**Key capabilities:**
- 3P updates, newsletters, FAQs, status updates, incident reports
- Format and tone from company-specific templates
- Workflow: identify type → load guideline → follow format

**Limitations:**
- Highly context-dependent — requires company templates/guidelines to be most useful
- Generic without company-specific context

---

### mcp-builder

**Location:** `anthropics/skills/mcp-builder/`

**What it does:**
Complete guide for building high-quality MCP (Model Context Protocol) servers that let LLMs interact with external services and APIs.

**When to use:**
- "Build an MCP server"
- "Create a tool integration for Claude"
- "Connect [external API] via MCP"
- Any MCP server development task

**Key capabilities:**
- Deep research and planning phase
- TypeScript SDK (recommended) and Python SDK guidance
- Transport options: Streamable HTTP (remote) or stdio (local)
- Tool naming conventions (consistent prefixes, e.g., `github_create_issue`)
- Core infrastructure: auth, error handling, response formatting
- Zod/Pydantic schemas for tool definitions
- Testing with MCP Inspector

**Recommended stack:**
- Language: TypeScript (best SDK support)
- Transport: Streamable HTTP for remote, stdio for local

**Limitations:**
- TypeScript strongly preferred (Python supported but less complete)
- Heavy on research and testing phases
- Requires API documentation for the target service

---

### pdf

**Location:** `anthropics/skills/pdf/`

**What it does:**
Full PDF workflow — read, create, edit, extract, merge, split, OCR, encrypt, and watermark PDF files.

**When to use:**
- "Read / open this PDF"
- "Extract tables or text from PDF"
- "Merge / split / rotate PDF pages"
- "Create a PDF from scratch"
- "Fill this PDF form"
- "OCR a scanned document"

**Key capabilities:**
- `pypdf`: merge, split, rotate
- `pdfplumber`: text and table extraction with layout preservation
- `reportlab`: create PDFs from scratch
- `pandoc`: text extraction
- Form filling, image extraction, metadata, encryption, watermarking

**Limitations:**
- LibreOffice needed for some format conversions
- OCR is a separate workflow step

---

### pptx

**Location:** `anthropics/skills/pptx/`

**What it does:**
Create, read, edit, and modify PowerPoint presentation files (.pptx) with professional design.

**When to use:**
- "Create a deck / presentation / slides"
- "Edit this PowerPoint"
- "Extract content from slides"
- Any `.pptx` file work

**Key capabilities:**
- Reading with `markitdown` or XML unpacking
- Template-based editing (unpack → edit → repack)
- Creation from scratch with pptxgenjs
- 10 curated color themes
- Font pairing library
- Layout variety: two-column, icon rows, grids, half-bleed images
- QA validation workflow

**Design principles:**
- Bold topic-specific color palette
- 60–70% primary color dominance
- One recurring visual motif
- Every slide needs a visual element (no text-only slides)
- No AI tells: avoid accent lines under titles, default blue colors

**Limitations:**
- Complex QA required
- Requires professional design commitment

---

### skill-creator

**Location:** `anthropics/skills/skill-creator/`

**What it does:**
Framework for creating new skills, modifying existing ones, and measuring skill performance through testing and quantitative benchmarking.

**When to use:**
- "Create a new skill for X"
- "Optimize when this skill triggers"
- "Benchmark this skill's performance"
- Iterating on any skill in this repo

**Key capabilities:**
- Intent capture from conversation history
- Interview and edge-case research
- SKILL.md writing with YAML frontmatter
- Test case creation and execution
- Quantitative evaluation and benchmarking
- Iterative refinement based on scores
- Skill description optimization for better triggering

**Workflow:**
1. Capture intent (what, when, output format)
2. Interview and research
3. Write SKILL.md
4. Create test prompts
5. Run evals (background evaluation)
6. Score results
7. Iterate on description and content

**Limitations:**
- Multi-phase — time-intensive
- Requires clear, measurable success criteria
- Benchmarking needs quantitative metrics defined upfront

---

### slack-gif-creator

**Location:** `anthropics/skills/slack-gif-creator/`

**What it does:**
Creates optimized animated GIFs specifically for Slack using PIL graphics and custom GIF builder utilities.

**When to use:**
- "Make a GIF for Slack"
- "Create a custom animated emoji"
- "Animate something for a Slack message"
- Slack-specific animation requests

**Key capabilities:**
- GIFBuilder for frame assembly and optimization
- PIL ImageDraw (circles, polygons, lines, rectangles)
- Easing functions: linear, ease_in, ease_out, bounce_out, elastic_out
- Color optimization (48–128 colors)
- Slack compliance validators

**Slack constraints:**
- Emoji GIFs: 128×128px, under 3 seconds
- Message GIFs: 480×480px
- FPS: 10–30

**Best practices:**
- Lines width 2+ for visibility
- Layered visual depth (gradients, shadows)
- Complementary color use

**Limitations:**
- PIL only — no external graphics libraries
- Strict Slack size constraints

---

### theme-factory

**Location:** `anthropics/skills/theme-factory/`

**What it does:**
Applies curated professional color and typography themes to artifacts like slides, documents, and HTML pages.

**When to use:**
- "Style this deck / document"
- "Apply a theme"
- "Color these slides"
- Any design system / styling request for existing artifacts

**Key capabilities:**
- 10 pre-set themes:
  - Ocean Depths, Sunset Boulevard, Forest Canopy, Modern Minimalist
  - Golden Hour, Arctic Frost, Desert Rose, Tech Innovation
  - Botanical Garden, Midnight Galaxy
- Each theme: color palette + font pairings + visual identity
- Custom theme generation on-the-fly
- `theme-showcase.pdf` for visual preview

**Workflow:**
1. Show theme showcase
2. User picks a theme
3. Confirm selection
4. Apply colors and fonts

**Limitations:**
- 10 pre-set themes (or generate custom)
- Target artifact must be in a compatible format

---

### web-artifacts-builder

**Location:** `anthropics/skills/web-artifacts-builder/`

**What it does:**
Builds complex, multi-component React artifacts with state management, routing, and shadcn/ui. Bundles everything into a single self-contained HTML file.

**When to use:**
- "Build an interactive app / artifact"
- Complex components requiring state, routing, or multiple views
- When shadcn/ui components are needed
- NOT for simple single-file HTML/JSX artifacts

**Key capabilities:**
- Vite + React 18 + TypeScript
- Tailwind CSS 3.4.1 + shadcn/ui (40+ pre-installed components)
- Path aliases (`@/`)
- Parcel bundling to single deployable HTML file
- `scripts/init-artifact.sh` and `scripts/bundle-artifact.sh`

**Workflow:**
```bash
bash scripts/init-artifact.sh <project-name>
# develop...
bash scripts/bundle-artifact.sh
```

**Anti-patterns (always avoid):**
- Centered layouts, purple gradients, uniform rounded corners, Inter font

**Requirements:** Node 18+, npm

**Limitations:**
- For complex artifacts only — overkill for simple HTML
- Requires local Node.js setup

---

### webapp-testing

**Location:** `anthropics/skills/webapp-testing/`

**What it does:**
Tests local web applications using Playwright with built-in server lifecycle management and reconnaissance-before-action patterns.

**When to use:**
- "Test this web app"
- "Verify the UI behavior"
- "Capture screenshots of the app"
- "Check that [feature] works correctly"
- Any webapp validation task

**Key capabilities:**
- Playwright for browser automation
- `with_server.py` helper for server lifecycle management
- Single and multi-server support
- Screenshots, DOM inspection, console log capture
- Element discovery before interaction (recon-first pattern)
- Static HTML via `file://` URLs

**Decision tree:**
1. Static HTML? → Read directly for selectors
2. Server running? → Yes: recon → action
3. Server not running? → Use `with_server.py`

**Best practices:**
- Always `wait_for_load_state('networkidle')` on dynamic apps
- Take screenshot/inspect before interacting
- Use descriptive selectors (`text=`, `role=`, CSS class)

**Limitations:**
- Python + Playwright only
- Dynamic apps need careful wait state management

---

### xlsx

**Location:** `anthropics/skills/xlsx/`

**What it does:**
Create, read, edit, and analyze Excel spreadsheets with full formula, formatting, chart, and financial model support.

**When to use:**
- "Open / edit a .xlsx file"
- "Create a spreadsheet"
- "Analyze this data"
- "Build a financial model"
- Any `.xlsx` file work

**Key capabilities:**
- `pandas`: data analysis and manipulation
- `openpyxl`: formulas and formatting
- LibreOffice: formula recalculation
- Financial model color coding (Blue = inputs, Black = formulas, Green = internal links, Red = external links, Yellow = assumptions)
- Number formatting rules
- Charts, data validation, error checking

**Critical rules (will cause issues if ignored):**
- **Always use formulas, not hardcoded values** (`=SUM()` not `5000`)
- Zero formula errors on delivery (`#REF!`, `#DIV/0!`, `#VALUE!`, `#N/A`, `#NAME?`)
- Always recalculate: `python scripts/recalc.py output.xlsx`
- Years as text, currency with units, parentheses for negatives

**Workflow:**
1. Create/load with pandas or openpyxl
2. Add formulas (not hardcoded values)
3. Format professionally
4. Save file
5. **Recalculate (MANDATORY)**
6. Verify zero errors

**Limitations:**
- LibreOffice required for recalculation
- Financial model conventions are strict

---

## Updating Skills

To update all submodule skills to their latest versions:
```bash
cd ~/Desktop/skills
git submodule update --remote --merge
git commit -am "update all skills"
git push
```

To update a single skill:
```bash
git submodule update --remote --merge <skill-name>
```

## Skills That Won't Auto-Update

- `design-for-ai` — static folder (no upstream repo)
