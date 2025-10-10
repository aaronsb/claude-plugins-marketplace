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
- **7 specialized subagents** - requirements-analyst, system-architect, task-planner, code-reviewer, github-project-manager, workflow-orchestrator, workspace-curator
- **Phase-gated workflow** - Enforces requirements → design → tasks → implementation
- **SOLID principles enforcement** - Prevents monolithic patterns
- **Security hooks** - Pre-commit secret detection
- **Architecture Decision Records (ADR)** - Structured design documentation
- **Dual tracking modes** - Local files (requirements.md/design.md/tasks.md) or GitHub integration

**Install:**
```bash
/plugin install disciplined-methodology
```

**Repository:** [aaronsb/claude-code-config](https://github.com/aaronsb/claude-code-config)
**Version:** 1.0.0
**License:** MIT

## 🔧 Marketplace Structure

This marketplace uses git submodules to reference plugins:

```
claude-plugins-marketplace/
├── .claude-plugin/
│   └── marketplace.json        # Lists all plugins
├── disciplined-methodology/    # Git submodule → claude-code-config
└── future-plugin/              # Future plugins as submodules
```

**How it works:**
1. Each plugin is developed in its own repository
2. The marketplace references plugins as git submodules
3. `marketplace.json` points to each plugin via relative path (`"./disciplined-methodology"`)
4. When users install from the marketplace, Claude Code clones the referenced repos

## 🛠️ Adding New Plugins

To add a new plugin to this marketplace:

1. **Create the plugin repo** with `.claude-plugin/plugin.json`
2. **Add as submodule:**
   ```bash
   git submodule add git@github.com:aaronsb/your-new-plugin.git your-new-plugin
   ```
3. **Update marketplace.json:**
   ```json
   {
     "plugins": [
       {
         "name": "your-new-plugin",
         "source": "./your-new-plugin",
         "description": "Brief description"
       }
     ]
   }
   ```
4. **Commit and push:**
   ```bash
   git add -A
   git commit -m "feat: Add your-new-plugin"
   git push
   ```

## 🔄 Updating Plugins

When a plugin repository is updated:

```bash
cd disciplined-methodology    # Enter the submodule
git pull origin main          # Pull latest changes
cd ..                         # Return to marketplace root
git add disciplined-methodology
git commit -m "chore: Update disciplined-methodology to latest"
git push
```

## 📄 License

This marketplace structure is MIT licensed. Individual plugins have their own licenses - see each plugin's repository for details.
