---
name: academic-paper-review
description: Systematic academic paper review with atomic notes, Zettelkasten methodology, and multi-style reviews (Gelman, quick-read, methods, critical). Import from Zotero, extract highlights/figures/tables, create cross-cutting data notes, manage writing projects. Transparent root skill/ architecture accessible to all agents.
---

# Academic Paper Review Skill

**A comprehensive framework for systematic academic paper review using atomic notes, Zettelkasten methodology, and automated PDF extraction.**

## 🎯 What This Skill Does

This skill helps you:

- ✅ **Import papers** from Zotero with metadata and PDFs
- ✅ **Extract full text** from PDFs automatically
- ✅ **Create atomic notes** (one idea per file, fully linked)
- ✅ **Conduct multi-style reviews** (Gelman, quick-read, methods, critical)
- ✅ **Extract highlights, figures, tables** as separate atomic elements
- ✅ **Build knowledge graphs** through wikilink connections
- ✅ **Manage writing projects** that synthesize research
- ✅ **Track cross-cutting insights** (methods, datasets, patterns)

## 🏗️ Architecture: Transparent Root Skill

**This skill lives in `skill/` at project root for transparency and accessibility.**

```
your-research-project/
├── skill/                                # ⭐ Visible in repo root (transparent!)
│   ├── SKILL.md                          # This file
│   ├── references/                       # Workflow documentation
│   ├── scripts@ → ../scripts/            # Symlink to root scripts
│   └── templates@ → ../templates/        # Symlink to root templates
│
├── .claude/skills/academic-paper-review@ → ../../skill/      # Claude Code
├── .antigravity/skills/academic-paper-review@ → ../../skill/ # Antigravity
├── .gemini/skills/academic-paper-review@ → ../../skill/      # Gemini
├── .codex/skills/academic-paper-review@ → ../../skill/       # Codex
│
├── source-files/                         # Pristine Zotero imports
├── paper-analysis/                       # Analysis workspace
├── data/                                 # Cross-cutting atomic notes
├── writing/                              # Writing projects
├── index/                                # Tracking and metadata
├── scripts/                              # Extraction automation
└── templates/                            # File templates
```

**Why root folder?**
- ✅ **Transparent**: Anyone browsing repo sees skill immediately
- ✅ **Accessible**: Other agents/tools can access (not .claude-only)
- ✅ **Multi-agent compatible**: Same skill, multiple agent systems
- ✅ **Self-documenting**: Clear skill-based workflow architecture
- ✅ **Evolvable**: Skill evolves with project as "project memory"

## 🚀 Quick Start

### New to This Skill?

1. **Read the setup guide**: [references/setup-guide.md](references/setup-guide.md)
2. **Set up your project**: Follow the installation instructions
3. **Set up VS Code extensions**: [references/setup-architecture.md](references/setup-architecture.md#recommended-vs-code-extensions)
4. **Import your first paper**: [references/workflow-import.md](references/workflow-import.md)
5. **Conduct your first review**: [references/workflow-review.md](references/workflow-review.md)

### Ready to Use?

Jump to the workflow you need:

| Workflow | Reference File |
|----------|----------------|
| **Setup & Architecture** | [references/setup-architecture.md](references/setup-architecture.md) |
| **Getting Started** | [references/setup-guide.md](references/setup-guide.md) |
| **Directory Structure** | [references/directory-structure.md](references/directory-structure.md) |
| **YAML Schemas** | [references/yaml-schemas.md](references/yaml-schemas.md) |
| **Paper Import** | [references/workflow-import.md](references/workflow-import.md) |
| **Conducting Reviews** | [references/workflow-review.md](references/workflow-review.md) |
| **Content Extraction** | [references/workflow-extract.md](references/workflow-extract.md) |
| **Creating Notes** | [references/workflow-notes.md](references/workflow-notes.md) |
| **Writing Projects** | [references/workflow-writing.md](references/workflow-writing.md) |
| **Templates Guide** | [references/templates-guide.md](references/templates-guide.md) |
| **Best Practices** | [references/best-practices.md](references/best-practices.md) |

## 📚 Core Workflows

### Import Paper from Zotero
See [references/workflow-import.md](references/workflow-import.md)

Import papers with full text, highlights, and metadata extraction.

### Conduct Reviews
See [references/workflow-review.md](references/workflow-review.md)

Available review styles:
- **Gelman Review**: Critical statistical and methodological analysis
- **Quick Read**: Fast triage overview (300-500 words)
- **Methods Deep Dive**: Detailed reproducibility assessment
- **Critical Review**: Peer-review style evaluation

### Extract Content
See [references/workflow-extract.md](references/workflow-extract.md)

- **Full text**: PDF → markdown (via pdftotext)
- **Highlights**: Atomic files with YAML frontmatter (one per highlight)
- **Figures**: PNG + metadata files
- **Tables**: CSV + metadata files

### Create Atomic Notes
See [references/workflow-notes.md](references/workflow-notes.md)

- **Paper-specific insights** (in `paper-analysis/{folder-name}/notes/`)
- **Cross-cutting data notes** (in `data/`)

### Manage Writing Projects
See [references/workflow-writing.md](references/workflow-writing.md)

Synthesize findings from multiple papers into writing projects.

## 📂 Directory Structure

See [references/directory-structure.md](references/directory-structure.md)

```
your-research-project/
├── skill/                           # ⭐ SKILL DOCUMENTATION (transparent!)
├── source-files/                    # Pristine Zotero imports (PDFs, markdown)
├── paper-analysis/                  # Analysis workspace (highlights, reviews, notes)
├── data/                            # Cross-cutting atomic notes (methods, datasets, patterns)
├── writing/                         # Writing projects
├── index/                           # Tracking and metadata
├── scripts/                         # Extraction automation
└── templates/                       # File templates
```

## 📝 YAML Schemas

See [references/yaml-schemas.md](references/yaml-schemas.md)

Complete specifications for:
- Source papers
- Highlights
- Figures/Tables
- Reviews
- Atomic notes
- Data notes
- Writing projects

## 🛠️ Scripts & Templates

### Extraction Scripts

Available in `scripts/`:
- `extract-paper.sh` - Main PDF extraction orchestrator
- `pdf-to-markdown.sh` - Full text extraction (pdftotext)
- `extract-figures.sh` - Figure extraction (pdfimages)
- `extract-tables.sh` - Table extraction (pdftotext)

### Templates

Available in `templates/`:
- Review templates: `gelman-review.md`, `quick-read.md`, `methods-deep-dive.md`, `critical-review.md`, `summary-card.md`
- Note templates: `highlight.md`, `figure.md`, `table.md`, `data-note.md`, `writing-project.md`

See [references/templates-guide.md](references/templates-guide.md) for usage.

## ✅ Best Practices

See [references/best-practices.md](references/best-practices.md)

- Quality standards for reviews, extracts, and notes
- Git workflow and commit strategy
- Color-coded highlight interpretation
- When to create data notes vs. paper notes
- Troubleshooting common issues

## 🔌 Required VS Code Extensions

**Works in**: VS Code, Cursor, Windsurf, Antigravity (all use VS Code extension ecosystem)

**Essential**:
- **Foam** (`foam.foam-vscode`) - Wikilink support and graph visualization
- **Markdown All in One** (`yzhang.markdown-all-in-one`) - Enhanced markdown editing
- **YAML** (`redhat.vscode-yaml`) - YAML frontmatter validation

**Quick install**:
```bash
code --install-extension foam.foam-vscode
code --install-extension yzhang.markdown-all-in-one
code --install-extension redhat.vscode-yaml
```

Replace `code` with `cursor`, `windsurf`, or `antigravity` for other editors.

See [references/setup-architecture.md](references/setup-architecture.md#recommended-vs-code-extensions) for complete list.

## 📦 Dependencies

- **Zotero** (or compatible reference manager)
- **poppler-utils** (for pdftotext, pdfimages)
  - macOS: `brew install poppler`
  - Linux: `apt-get install poppler-utils`
- **pandoc** (optional, for advanced PDF processing)
- **Foam** VS Code extension (optional, for graph visualization)

## 🎓 Philosophy

This skill is based on:

1. **Atomic notes** - One idea per file, fully linked (Zettelkasten methodology)
2. **YAML frontmatter** - Structured metadata for programmatic processing
3. **Wikilinks** - Building knowledge graphs through `[[connections]]`
4. **Git version control** - Tracking evolution of thoughts over time
5. **Transparent architecture** - Skill visible in project root, not hidden
6. **Multi-agent compatibility** - Works with Claude, Antigravity, Gemini, Codex
7. **Self-improvement** - Skill evolves with your project

**Goal**: Create a growing, interconnected knowledge base that gets smarter over time.

## 🌟 Example Projects

See working examples:
- **AI Paper Reviews**: Academic research on LLM evaluation (private repo)
- Your project could be next! Share your setup in issues/discussions.

## 🤝 Contributing

Found a better way to do something? Improvements welcome!

1. Update the relevant reference file
2. Test with your own research project
3. Submit a pull request or open an issue
4. Share what you learned

## 📖 Further Reading

- [Setup Guide](references/setup-guide.md) - Get started
- [Setup Architecture](references/setup-architecture.md) - Why skill in root folder?
- [Directory Structure](references/directory-structure.md) - Folder organization
- [Workflows](references/) - All workflow documentation
- [Best Practices](references/best-practices.md) - Tips and troubleshooting

## 📄 License

MIT License - Use freely, modify as needed, share improvements.

## 🙏 Acknowledgments

- **Zettelkasten methodology**: Niklas Luhmann's note-taking system
- **Foam**: VS Code extension for wikilinks and graphs
- **Andrew Gelman**: Inspiration for critical statistical reviews
- **Academic community**: For developing rigorous review methodologies

---

**Ready to start?** → [Setup Guide](references/setup-guide.md)
