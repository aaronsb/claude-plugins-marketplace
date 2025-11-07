# Aaron's Claude Code Plugin Marketplace

A curated collection of Claude Code plugins for disciplined software engineering.

## 🚀 Installation

Add this marketplace to Claude Code:

```bash
/plugin marketplace add aaronsb/claude-plugins-marketplace
```

Then browse and install plugins:
```bash
/plugin install disciplined-methodology
```

## 📦 Available Plugins

### Disciplined Software Engineering Methodology

A rigorous software engineering methodology featuring:
- **ADR-driven workflow** - Debate → Draft ADR → PR → Implement → Review → Merge
- **6 specialized subagents** - requirements-analyst, system-architect, task-planner, code-reviewer, workflow-orchestrator, workspace-curator
- **GitHub-first collaboration** - Issue tracking, PR reviews, with automatic fallback to local files
- **SOLID principles enforcement** - Code quality checks preventing monolithic patterns
- **Collaborative guidance** - Ask when stuck, verify context after compaction, push back when unclear
- **Architecture Decision Records (ADR)** - Structured design documentation in docs/adr/

**Install:**
```bash
/plugin install disciplined-methodology
```

**Repository:** [aaronsb/claude-code-config](https://github.com/aaronsb/claude-code-config)
**Version:** 2.0.0
**License:** MIT

## 🔧 Marketplace Structure

This marketplace is a lightweight registry that points to plugin repositories:

```
claude-plugins-marketplace/
├── .claude-plugin/
│   └── marketplace.json        # Registry of plugin URLs
└── README.md
```

**How it works:**
1. Each plugin is developed in its own repository
2. `marketplace.json` contains direct GitHub URLs to plugin repos
3. When users install, Claude Code clones directly from the plugin repository
4. No nested repos or submodules - just a simple index

## 🛠️ Adding New Plugins

To add a new plugin to this marketplace:

1. **Create the plugin repo** with `.claude-plugin/plugin.json`
2. **Update marketplace.json:**
   ```json
   {
     "plugins": [
       {
         "name": "your-new-plugin",
         "source": "https://github.com/aaronsb/your-new-plugin",
         "description": "Brief description"
       }
     ]
   }
   ```
3. **Commit and push:**
   ```bash
   git add .claude-plugin/marketplace.json
   git commit -m "feat: Add your-new-plugin to marketplace"
   git push
   ```

## 🔄 Updating Plugins

Plugin updates are automatic - Claude Code pulls from the source repository.

Users can update with:
```bash
/plugin update disciplined-methodology
```

To bump the marketplace version (if you change descriptions or add plugins):
```bash
# Update version in .claude-plugin/marketplace.json
git commit -am "chore: Update marketplace"
git push
```

## 📄 License

This marketplace structure is MIT licensed. Individual plugins have their own licenses - see each plugin's repository for details.
