# Kito Workspace Storage

This repository serves as the collaborative storage backend for your Kito workspace. It contains instructions, notes, and documentation for your tools and projects, organized in a human-readable directory structure that supports multiple editing workflows.

## Repository Structure

```
README.md                   # This file
metadata.toml               # Workspace metadata
tools/                      # Tool-specific storage
   {tool-slug}/
       metadata.toml        # Tool metadata
       instructions/        # Tool rules and workflows
       notes/               # Tool documentation and context

projects/                   # Project-specific storage
   {project-slug}/
       metadata.toml        # Project metadata
       instructions/        # Project rules and workflows
       notes/               # Project specifications and architecture etc.

offline/                    # EXPERIMENTAL: Offline documentation
    README.md               # Offline access documentation
```

## How It Works

This repository is connected to your Kito workspace through the GitHub Apps integration. It enables **bidirectional sync** between multiple editing interfaces:

### Editing Options
- **Kito Web UI**: Rich editing interface with workspace-specific features
- **Kito CLI**: Programmatic access to workspace files and sync operations via CLI
- **Normal Git Operations**: Clone locally, use any offline/online editor, commit and push changes

### Sync Strategy (TODO: Be more explicit about what's going on)
- **Git-native workflow**: Full support for branches, merges, and standard git operations. While kito operates on only the `main` branch. You're free to maintain branches but that'd be unusual.
- **Pull-based sync**: Changes are detected when you interact with your workspace
- **Multi-source support**: Handle edits from any interface seamlessly. We try to do best-effort sync.

## Metadata System

### Workspace Metadata (`metadata.toml`)
Auto-generated file containing workspace-level configuration:
- Workspace UUID and repository information
- Sync settings and validation rules
- Last sync timestamps
- Human-readable TOML format with comments

### Entity Metadata (`metadata.toml`)
Each tool and project directory contains metadata for UUID mapping:
- Links directory names to Kito database entities
- Tracks sync timestamps and version information
- Enables consistent mapping between slug names and UUIDs
- TOML format allows for comments and extended configuration

## Getting Started

### For New Users
1. This repository was created as part of creating your kito workspace
2. The directory structure will populate as you add tools and projects in kito
3. You can immediately start editing files through any of the supported interfaces

## Support
- **Documentation**: Refer to individual directory READMEs for specific guidance
- **Issues**: Report problems through your Kito workspace settings
- **Git Conflicts**: Kito provides conflict resolution tools in the web interface. Otherwise since the storage is essentially a git repo you can resolve conflicts using any of your desired git interfaces. But advisable to use the kito interface if it has to do with creation/deletion an entity(project/tool) rather than just content update because the entity ids are mapped to your kito workspace. Even in that case if there is any mismatch, you'll be able to resolve them later.
