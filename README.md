# Kito Workspace Storage

This repository serves as the collaborative storage backend for your Kito workspace. It contains instructions, notes, and documentation for your tools and projects, organized in a human-readable directory structure that supports multiple editing workflows.

## Repository Structure

```
 README.md                    # This file
 .kito-workspace.json        # Workspace metadata (auto-generated)
 tools/                      # Tool-specific storage
    {tool-slug}/
        .kito-meta.json     # Tool metadata
        instructions/       # AI assistant rules and workflows  
        notes/             # Documentation and context
 projects/                   # Project-specific storage
    {project-slug}/
        .kito-meta.json     # Project metadata
        instructions/       # Project rules and workflows
        notes/             # Specifications and architecture
 offline/                    # >ê EXPERIMENTAL: Offline documentation
     README.md              # Offline access documentation
```

## How It Works

This repository is connected to your Kito workspace through the GitHub Apps integration. It enables **bidirectional sync** between multiple editing interfaces:

### Editing Options
- **Kito Web UI**: Rich editing interface with workspace-specific features
- **GitHub Web Interface**: Direct file editing in your browser
- **Kito CLI**: Programmatic access to workspace files and sync operations
- **Git Operations**: Clone locally, use any editor, commit and push changes

### Sync Strategy
- **Pull-based sync**: Changes are detected when you interact with your workspace
- **Multi-source support**: Handle edits from any interface seamlessly
- **Git-native workflow**: Full support for branches, merges, and standard git operations
- **Manual triggers**: Refresh buttons available for immediate sync

## Metadata System

### Workspace Metadata (`.kito-workspace.json`)
Auto-generated file containing workspace-level configuration:
- Workspace UUID and repository information
- Sync settings and validation rules
- Last sync timestamps

### Entity Metadata (`.kito-meta.json`)
Each tool and project directory contains metadata for UUID mapping:
- Links directory names to Kito database entities
- Tracks sync timestamps and version information
- Enables consistent mapping between slug names and UUIDs

## Getting Started

### For New Users
1. This repository was created automatically when you connected your workspace to GitHub
2. The directory structure will populate as you add tools and projects in Kito
3. You can immediately start editing files through any of the supported interfaces

### For Existing Git Users
1. **Clone the repository**: Standard git clone operations work normally
2. **Edit files**: Use your preferred editor to modify instructions and notes
3. **Commit changes**: Standard git workflow (add, commit, push)
4. **Sync with Kito**: Changes will be pulled into Kito when you access your workspace

### Directory Organization
- **Tool directories**: Named using `{workspace-tool-slug}` for human readability
- **Project directories**: Named using `{workspace-project-slug}` for easy navigation
- **File structure**: Consistent `instructions/` and `notes/` subdirectories
- **Markdown format**: All content stored as `.md` files for universal compatibility

## Best Practices

### File Organization
- Keep instructions focused and actionable
- Use descriptive filenames within each directory
- Maintain consistent structure across tools and projects

### Collaboration
- Use meaningful commit messages for changes
- Consider using branches for major structural changes
- Leverage GitHub's review features for team workspaces

### Sync Management
- Use Kito's web interface for complex operations
- Leverage CLI for automated workflows
- Manual git operations work seamlessly with the sync system

## Support

- **Documentation**: Refer to individual directory READMEs for specific guidance
- **Issues**: Report problems through your Kito workspace settings
- **Git Conflicts**: Kito provides conflict resolution tools in the web interface

---

This workspace storage system enables flexible, collaborative knowledge management while maintaining the power of version control and the simplicity of markdown documentation.