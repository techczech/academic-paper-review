# Setup Guide: Getting Started with Academic Paper Review Skill

Complete guide to setting up a new research project using this skill.

## 🎯 Overview

This guide will help you:
1. Set up directory structure
2. Install dependencies
3. Configure VS Code extensions
4. Create the skill architecture
5. Import your first paper
6. Start reviewing and taking notes

**Estimated setup time**: 15-30 minutes

---

## Prerequisites

### Required Software

- **Git** - Version control
- **Zotero** - Reference management (or compatible alternative)
- **VS Code** (or Cursor, Windsurf, Antigravity) - Text editor
- **poppler-utils** - PDF text extraction
  - macOS: `brew install poppler`
  - Linux: `apt-get install poppler-utils`
  - Windows: Download from https://github.com/oschwartz10612/poppler-windows

### Optional Software

- **pandoc** - Advanced document conversion
- **VSCodeZotero** extension - Zotero integration for VS Code

---

## Step 1: Create Project Directory

```bash
# Create your research project directory
mkdir my-research-project
cd my-research-project

# Initialize git repository
git init

# Create main directory structure
mkdir -p source-files paper-analysis data writing index scripts templates
```

---

## Step 2: Copy Skill to Project

### Option A: Direct Copy

```bash
# Copy skill to your project
cp -r /path/to/academic-paper-review/references my-research-project/skill/references
cp -r /path/to/academic-paper-review/scripts my-research-project/scripts/
cp -r /path/to/academic-paper-review/templates my-research-project/templates/
cp /path/to/academic-paper-review/SKILL.md my-research-project/skill/SKILL.md
```

### Option B: Git Clone (if skill is in a git repo)

```bash
# Clone the skill repository
git clone https://github.com/yourusername/academic-paper-review.git temp-skill

# Copy to your project
cp -r temp-skill/references my-research-project/skill/references
cp -r temp-skill/scripts my-research-project/scripts/
cp -r temp-skill/templates my-research-project/templates/
cp temp-skill/SKILL.md my-research-project/skill/SKILL.md

# Clean up
rm -rf temp-skill
```

---

## Step 3: Create Transparent Root Architecture

**This is the key architectural decision: skill lives in project root for transparency.**

```bash
cd my-research-project

# Create skill folder in PROJECT ROOT (transparent!)
mkdir -p skill/references

# Copy SKILL.md
cp /path/to/academic-paper-review/SKILL.md skill/SKILL.md

# Copy reference files
cp -r /path/to/academic-paper-review/references/* skill/references/

# Create symlinks within skill/ to avoid duplication
cd skill/
ln -s ../scripts scripts
ln -s ../templates templates
cd ..
```

**Verify structure**:
```bash
ls -la skill/
# Should show: SKILL.md, references/, scripts@, templates@
```

---

## Step 4: Create Multi-Agent Discovery Symlinks

**Allow multiple AI agents to discover the skill:**

```bash
# Create agent-specific skill directories
mkdir -p .claude/skills .antigravity/skills .gemini/skills .codex/skills

# Create symlinks pointing to root skill/
cd .claude/skills && ln -s ../../skill academic-paper-review && cd ../..
cd .antigravity/skills && ln -s ../../skill academic-paper-review && cd ../..
cd .gemini/skills && ln -s ../../skill academic-paper-review && cd ../..
cd .codex/skills && ln -s ../../skill academic-paper-review && cd ../..
```

**Verify symlinks**:
```bash
ls -la .claude/skills/academic-paper-review
# Should show: → ../../skill

ls -la .antigravity/skills/academic-paper-review
# Should show: → ../../skill

# Repeat for .gemini and .codex
```

---

## Step 5: Create Core Files

### Create index/papers.yaml

```bash
cat > index/papers.yaml << 'EOF'
# Master index of all papers
# Updated automatically by import workflow

papers: {}
EOF
```

### Create index/note-graph.yaml

```bash
cat > index/note-graph.yaml << 'EOF'
# Knowledge graph: tracks connections between notes
# Updated automatically when creating notes

nodes: []
edges: []
EOF
```

### Create CHANGELOG.md

```bash
cat > CHANGELOG.md << 'EOF'
# Research Project Changelog

Session-to-session memory for this research project.

## 2026-XX-XX - Session 1: Initial Setup

### Papers Processed
- None yet

### Repository Setup
- Created directory structure
- Installed academic-paper-review skill
- Set up transparent root architecture
- Configured multi-agent discovery symlinks

### Next Steps
- Import first paper from Zotero
- Conduct first review
- Create first atomic notes

---

## Template for Future Sessions

Copy this template for each session:

## YYYY-MM-DD - Session N: Brief Description

### Papers Processed
- List papers imported or reviewed

### Reviews
- List reviews written

### Extracts
- List extracts created

### Notes
- List atomic notes created

### Repository Improvements
- Document any improvements

### Session Notes
- Context for future sessions
EOF
```

### Create CLAUDE.md

```bash
cat > CLAUDE.md << 'EOF'
# Research Project - Instructions for Claude Code

## Primary Documentation

**➡️ See [skill/SKILL.md](skill/SKILL.md) for complete instructions**

This project uses the academic-paper-review skill for systematic paper review with atomic notes.

## Quick Links

- [Setup & Architecture](skill/references/setup-architecture.md)
- [Workflow: Import Papers](skill/references/workflow-import.md)
- [Workflow: Conduct Reviews](skill/references/workflow-review.md)
- [Workflow: Create Notes](skill/references/workflow-notes.md)
- [Best Practices](skill/references/best-practices.md)

## Session Memory

Read [CHANGELOG.md](CHANGELOG.md) at the start of each session for context.
EOF
```

### Create README.md

```bash
cat > README.md << 'EOF'
# My Research Project

Academic paper review repository using atomic notes and Zettelkasten methodology.

## Structure

- `skill/` - Workflow documentation and templates (academic-paper-review skill)
- `source-files/` - Pristine Zotero imports
- `paper-analysis/` - Analysis workspace (highlights, reviews, notes)
- `data/` - Cross-cutting atomic notes
- `writing/` - Writing projects
- `index/` - Tracking and metadata
- `scripts/` - Extraction automation
- `templates/` - File templates

## Getting Started

See [skill/SKILL.md](skill/SKILL.md) for complete documentation.

## Quick Start

1. Import papers from Zotero → `source-files/`
2. Review papers using skill workflows
3. Extract highlights and create atomic notes
4. Build knowledge graph through wikilinks

## Documentation

All workflows documented in `skill/references/`:
- [workflow-import.md](skill/references/workflow-import.md) - Import papers
- [workflow-review.md](skill/references/workflow-review.md) - Conduct reviews
- [workflow-notes.md](skill/references/workflow-notes.md) - Create notes
- [best-practices.md](skill/references/best-practices.md) - Tips and standards
EOF
```

---

## Step 6: Create .gitignore

```bash
cat > .gitignore << 'EOF'
# PDFs (optional - uncomment if you don't want PDFs in git)
# source-files/**/*.pdf

# Temporary files
*.tmp
*.bak
*~
.DS_Store
Thumbs.db

# Editor files
.vscode/
.idea/
*.swp
*.swo

# System files
__pycache__/
*.pyc
.pytest_cache/

# Build artifacts
*.log
*.out
EOF
```

---

## Step 7: Install VS Code Extensions

### Essential Extensions

```bash
# Essential (run these first)
code --install-extension foam.foam-vscode
code --install-extension yzhang.markdown-all-in-one
code --install-extension redhat.vscode-yaml

# Highly recommended
code --install-extension shd101wyy.markdown-preview-enhanced
code --install-extension mhutchie.git-graph
code --install-extension christian-kohler.path-intellisense

# Optional
code --install-extension gruntfuggly.todo-tree
code --install-extension yzane.markdown-pdf
```

**Note**: Replace `code` with `cursor`, `windsurf`, or `antigravity` depending on your editor.

### Configure Foam

Create `.vscode/foam.json`:

```json
{
  "foam.openDailyNote.directory": "paper-analysis",
  "foam.openDailyNote.titleFormat": "'daily-note'-yyyy-mm-dd",
  "foam.graph.style": {
    "node": {
      "note": { "color": "#4CAF50" },
      "source": { "color": "#2196F3" },
      "review": { "color": "#FF9800" },
      "data_note": { "color": "#9C27B0" }
    }
  }
}
```

---

## Step 8: Configure Zotero Integration

### Option A: VSCodeZotero Extension

1. Install VSCodeZotero extension in VS Code
2. Configure Zotero connection in settings
3. Enable markdown export with YAML frontmatter
4. Set export location to `source-files/`

### Option B: Manual Export

1. In Zotero, right-click collection → Export Collection
2. Format: Markdown (with YAML frontmatter)
3. Export to: `my-research-project/source-files/`
4. Include: PDFs, highlights, notes

---

## Step 9: Make Scripts Executable

```bash
chmod +x scripts/*.sh
```

---

## Step 10: Initial Git Commit

```bash
# Stage all files
git add .

# Commit with clear message
git commit -m "Initial setup: academic-paper-review skill with transparent root architecture

- Created skill/ folder in project root (transparent!)
- Created multi-agent discovery symlinks (.claude, .antigravity, .gemini, .codex)
- Set up directory structure (source-files/, paper-analysis/, data/, writing/)
- Installed extraction scripts and templates
- Configured Foam for knowledge graph visualization
- Created CHANGELOG.md for session-to-session memory"
```

---

## Step 11: Verify Setup

Run verification test:

```bash
# Check skill structure
ls -la skill/
# Should show: SKILL.md, references/, scripts@, templates@

# Check agent symlinks
ls -la .claude/skills/academic-paper-review
# Should show: → ../../skill

# Check scripts accessible
ls skill/scripts/
# Should show: extract-paper.sh, pdf-to-markdown.sh, etc.

# Check templates accessible
ls skill/templates/
# Should show: gelman-review.md, quick-read.md, etc.
```

---

## Step 12: Import Your First Paper

Follow [workflow-import.md](workflow-import.md) to import your first paper:

1. Export paper from Zotero to `source-files/`
2. Run import workflow
3. Verify paper folder created in `paper-analysis/`

---

## 🎉 You're Ready!

Your research project is now set up with:

✅ Transparent root skill architecture
✅ Multi-agent compatibility (Claude, Antigravity, Gemini, Codex)
✅ Complete workflow documentation
✅ Extraction scripts installed
✅ Templates ready to use
✅ VS Code extensions configured
✅ Git version control initialized

### Next Steps

1. **Import papers**: [workflow-import.md](workflow-import.md)
2. **Conduct reviews**: [workflow-review.md](workflow-review.md)
3. **Create notes**: [workflow-notes.md](workflow-notes.md)
4. **Build knowledge graph**: Use Foam to visualize connections

---

## Troubleshooting

### Problem: Symlinks not working

**Solution**: Make sure you're using relative paths (`../../skill`) not absolute paths.

### Problem: Scripts not executable

**Solution**: Run `chmod +x scripts/*.sh`

### Problem: pdftotext not found

**Solution**: Install poppler-utils:
- macOS: `brew install poppler`
- Linux: `apt-get install poppler-utils`

### Problem: VS Code extensions not installing

**Solution**: Check extension marketplace. Some extensions may have different names in Cursor/Windsurf/Antigravity.

---

## Customization

### For Your Research Domain

Edit files in `skill/references/` to add domain-specific:
- Tags
- Review questions
- Methodologies
- Common patterns

### For Your Workflow

Modify:
- `templates/` - Add custom review templates
- `scripts/` - Add domain-specific extraction scripts
- `skill/SKILL.md` - Document your customizations

**Remember**: Skill evolves with your project. Update documentation as you discover better workflows!

---

## Further Reading

- [setup-architecture.md](setup-architecture.md) - Why transparent root architecture?
- [directory-structure.md](directory-structure.md) - Complete folder organization
- [best-practices.md](best-practices.md) - Quality standards and tips
- [SKILL.md](../SKILL.md) - Main skill documentation
