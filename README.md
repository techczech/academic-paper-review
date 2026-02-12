# Academic Paper Review Skill

**A comprehensive Claude Code skill for systematic academic paper review using atomic notes, Zettelkasten methodology, and automated extraction.**

---

## 🎯 What is This?

This is a **Claude Code skill** that provides a complete workflow for academic research:

- ✅ Import papers from Zotero with metadata and PDFs
- ✅ Conduct multi-style reviews (Gelman, quick-read, methods, critical)
- ✅ Extract highlights, figures, tables automatically
- ✅ Create atomic notes (one idea per file)
- ✅ Build knowledge graphs through wikilinks
- ✅ Manage writing projects that synthesize research
- ✅ Track cross-cutting insights across papers

**Philosophy**: Zettelkasten methodology + Git version control + YAML metadata + Claude Code automation

---

## 🚀 Quick Start

### Prerequisites

- **Git** - Version control
- **Zotero** - Reference management
- **VS Code** (or Cursor, Windsurf, Antigravity)
- **poppler-utils** - PDF text extraction (`brew install poppler` on macOS)

### Installation

1. **Create your research project**:
   ```bash
   mkdir my-research-project
   cd my-research-project
   git init
   ```

2. **Copy this skill to your project**:
   ```bash
   # Copy skill to root skill/ folder
   cp -r /path/to/academic-paper-review my-research-project/skill

   # Copy scripts and templates
   cp -r /path/to/academic-paper-review/scripts my-research-project/scripts
   cp -r /path/to/academic-paper-review/templates my-research-project/templates
   ```

3. **Follow the setup guide**:
   ```bash
   # Read the comprehensive setup guide
   cat skill/references/setup-guide.md
   ```

**Complete setup instructions**: [references/setup-guide.md](references/setup-guide.md)

---

## 📚 What's Included

### Documentation (11 files, 4,800+ lines)

| File | Purpose |
|------|---------|
| [SKILL.md](SKILL.md) | Main skill file with overview |
| [references/setup-guide.md](references/setup-guide.md) | Complete setup instructions |
| [references/setup-architecture.md](references/setup-architecture.md) | Architecture explanation + VS Code extensions |
| [references/directory-structure.md](references/directory-structure.md) | Folder organization |
| [references/yaml-schemas.md](references/yaml-schemas.md) | All YAML frontmatter specifications |
| [references/workflow-import.md](references/workflow-import.md) | Import papers from Zotero |
| [references/workflow-review.md](references/workflow-review.md) | Conduct multi-style reviews |
| [references/workflow-extract.md](references/workflow-extract.md) | Extract highlights, figures, tables |
| [references/workflow-notes.md](references/workflow-notes.md) | Create atomic notes |
| [references/workflow-writing.md](references/workflow-writing.md) | Manage writing projects |
| [references/templates-guide.md](references/templates-guide.md) | Review template usage |
| [references/best-practices.md](references/best-practices.md) | Quality standards and troubleshooting |

### Scripts (4 files)

- `scripts/extract-paper.sh` - Main PDF extraction orchestrator
- `scripts/pdf-to-markdown.sh` - Full text extraction (pdftotext)
- `scripts/extract-figures.sh` - Figure extraction (pdfimages)
- `scripts/extract-tables.sh` - Table extraction

### Templates (10 files)

**Review templates**:
- `gelman-review.md` - Critical statistical/methodological analysis
- `quick-read.md` - Fast triage overview (300-500 words)
- `methods-deep-dive.md` - Detailed reproducibility assessment
- `critical-review.md` - Peer-review style evaluation
- `summary-card.md` - Shareable summary

**File templates**:
- `highlight.md` - Atomic highlight files
- `figure.md` - Figure metadata
- `table.md` - Table metadata
- `data-note.md` - Cross-cutting data notes
- `writing-project.md` - Writing project README

---

## 🏗️ Architecture: Transparent Root Skill

**Key innovation**: Skill lives in `skill/` at project root for transparency.

```
your-research-project/
├── skill/                                # ⭐ Visible in repo root!
│   ├── SKILL.md                          # Main skill file
│   ├── references/                       # 10 workflow reference files
│   ├── scripts@ → ../scripts/            # Symlink to scripts
│   └── templates@ → ../templates/        # Symlink to templates
│
├── .claude/skills/academic-paper-review@ → ../../skill/      # Claude Code
├── .antigravity/skills/academic-paper-review@ → ../../skill/ # Antigravity
├── .gemini/skills/academic-paper-review@ → ../../skill/      # Gemini
├── .codex/skills/academic-paper-review@ → ../../skill/       # Codex
│
├── source-files/                         # Pristine Zotero imports
├── paper-analysis/                       # Analysis workspace
├── data/                                 # Cross-cutting notes
├── writing/                              # Writing projects
├── index/                                # Tracking metadata
├── scripts/                              # Extraction automation
└── templates/                            # File templates
```

**Why transparent?**
- ✅ Anyone browsing repo sees skill immediately
- ✅ Other agents/tools can access (not .claude-only)
- ✅ Multi-agent compatible (Claude, Antigravity, Gemini, Codex)
- ✅ Self-documenting project architecture
- ✅ Skill evolves with project as "project memory"

---

## 📖 Core Workflows

### 1. Import Papers from Zotero

```bash
# Export paper from Zotero to source-files/
# Run import workflow (documented in skill)
# Paper folder created in paper-analysis/ with subfolders
```

See [references/workflow-import.md](references/workflow-import.md)

### 2. Conduct Reviews

Four review styles available:
- **Gelman Review** - Critical methodological analysis (2000-4000 words)
- **Quick Read** - Fast triage (300-500 words)
- **Methods Deep Dive** - Reproducibility assessment (1500-3000 words)
- **Critical Review** - Peer-review style (2000-3000 words)

See [references/workflow-review.md](references/workflow-review.md)

### 3. Extract Content

- **Full text**: PDF → markdown using pdftotext
- **Highlights**: Color-coded highlights → atomic files
- **Figures**: PNG files + semantic JSON metadata
- **Tables**: CSV files + semantic JSON metadata

See [references/workflow-extract.md](references/workflow-extract.md)

### 4. Create Atomic Notes

- **Paper-specific notes**: Insights from single papers
- **Data notes**: Cross-cutting patterns (methods, datasets, result patterns)
- All notes use Zettelkasten principles (one idea per file, fully linked)

See [references/workflow-notes.md](references/workflow-notes.md)

### 5. Manage Writing Projects

Synthesize findings from multiple papers into:
- Conference/journal papers
- Blog posts
- Reports
- Review articles

See [references/workflow-writing.md](references/workflow-writing.md)

---

## ✨ Features

### Atomic Notes & Zettelkasten

- One idea per file
- Timestamp-based unique IDs (YYYYMMDD-HHMMSS)
- Self-contained content
- Wiki-style links: `[[paper-folder/note]]`
- Foam graph visualization

### YAML Frontmatter

All files use structured YAML metadata:
- Source papers: title, authors, year, DOI, tags
- Reviews: review_style, rating, strengths, weaknesses
- Notes: type, created, tags, links, related_papers
- Complete schemas in [references/yaml-schemas.md](references/yaml-schemas.md)

### Multi-Style Reviews

- **Gelman Review**: Skeptical, constructive statistical critique
- **Quick Read**: Fast triage for reading queue
- **Methods Deep Dive**: Reproducibility-focused
- **Critical Review**: Peer-review practice

### Automated Extraction

- PDF → markdown using pdftotext
- Figures extracted with pdfimages
- Tables extracted (best effort)
- Highlights as separate atomic files

### Knowledge Graphs

- Foam extension for graph visualization
- Wikilinks connect papers, notes, reviews
- Cross-cutting data notes link multiple papers
- Color-coded nodes by type

### Git Version Control

- Track evolution of thinking
- Commit strategy documented
- Clear commit messages
- Session-to-session memory via CHANGELOG.md

---

## 🔌 Dependencies

### Required

- **Zotero** - Reference management (https://www.zotero.org/)
- **poppler-utils** - PDF tools
  - macOS: `brew install poppler`
  - Linux: `apt-get install poppler-utils`
  - Windows: https://github.com/oschwartz10612/poppler-windows

### Recommended

- **Foam** VS Code extension - Wikilink support and graphs
- **Markdown All in One** - Enhanced markdown editing
- **YAML** extension - YAML syntax validation

See [references/setup-architecture.md](references/setup-architecture.md#recommended-vs-code-extensions) for complete list.

---

## 🎓 Philosophy & Methodology

### Zettelkasten

- One idea per note
- Unique IDs for each note
- Dense linking between notes
- Self-contained content
- Build knowledge through connections

### Atomic Notes

- Single focus per file
- YAML frontmatter for metadata
- Wiki-style links for connections
- Tags for discovery
- Git for version control

### Transparent Architecture

- Skill visible in project root
- Not hidden in .claude/ folder
- Accessible to all agents/tools
- Self-documenting structure
- Evolves as "project memory"

---

## 🌟 Example Use Cases

- **Literature Reviews**: Systematically review 20-100 papers
- **PhD Research**: Build knowledge base over 3-5 years
- **Systematic Reviews**: Conduct rigorous meta-analyses
- **Research Projects**: Organize team research
- **Paper Writing**: Synthesize findings from multiple papers

---

## 🤝 Contributing

Improvements welcome! If you:

- Find a better workflow
- Discover an edge case
- Want to add a review style
- Have domain-specific adaptations

Please:
1. Update the relevant reference file
2. Test with your own research
3. Submit a pull request or open an issue
4. Share what you learned

---

## 📄 License

MIT License - Use freely, modify as needed, share improvements.

---

## 🙏 Acknowledgments

- **Niklas Luhmann**: Zettelkasten methodology
- **Andrew Gelman**: Critical statistical review approach
- **Foam**: VS Code extension for wikilinks and graphs
- **Zotero**: Open-source reference management
- **Claude Code**: Making AI-assisted research workflows possible

---

## 📖 Further Reading

- **Setup Guide**: [references/setup-guide.md](references/setup-guide.md)
- **Architecture**: [references/setup-architecture.md](references/setup-architecture.md)
- **Workflows**: [references/](references/)
- **Zettelkasten**: https://zettelkasten.de/
- **Foam**: https://foambubble.github.io/foam/

---

## 🚀 Get Started

**Ready to revolutionize your research workflow?**

1. Read [references/setup-guide.md](references/setup-guide.md)
2. Set up your project
3. Import your first paper
4. Start building your knowledge graph

**Questions?** Open an issue or check [references/best-practices.md](references/best-practices.md) for troubleshooting.
