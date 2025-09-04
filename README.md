# Kito Workspace Storage

This repository serves as the collaborative storage backend for your Kito workspace. It contains instructions, notes, and documentation for your tools and projects, organized in a human-readable directory structure that supports multiple editing workflows.

## Repository Structure

```
README.md                   # This file
tools/                      # Tool-specific storage
   {tool-slug}/
       instructions/        # Tool rules and workflows (initially empty)
       notes/               # Tool documentation and context (initially empty)

projects/                   # Project-specific storage
   {project-slug}/
       instructions/        # Project rules and workflows (initially empty)
       notes/               # Project specifications and architecture (initially empty)
```

**Key Points:**
- Directory names match the slugs of your Kito workspace entities
- Each tool/project has dedicated `instructions/` and `notes/` directories  
- Directories are created automatically when you add entities to your workspace

## How It Works

This repository is connected to your Kito workspace through the GitHub Apps integration. The current implementation focuses on maintaining proper directory structure for your workspace entities.

### Future Editing Options (Planned)
- **Kito Web UI**: Rich editing interface with workspace-specific features
- **Kito CLI**: Programmatic access to workspace files and sync operations
- **Git Operations**: Clone locally, use any editor, commit and push changes

### Current Implementation
- **Structure Management**: Kito ensures the proper directory structure exists for your workspace entities
- **Slug-based Mapping**: Directory names directly correspond to entity slugs in your Kito workspace
- **Auto-creation**: Missing directories are automatically created with the required `instructions/` and `notes/` subdirectories

**Note**: Advanced sync features like content synchronization and conflict resolution are planned for future development.

## Getting Started

### For New Users
1. This repository was created as part of creating your kito workspace
2. The directory structure will populate as you add tools and projects in kito
3. You can immediately start editing files through any of the supported interfaces

## Support
- **Documentation**: Refer to individual directory READMEs for specific guidance
- **Issues**: Report problems through your Kito workspace settings
- **Git Conflicts**: Kito provides conflict resolution tools in the web interface. Otherwise since the storage is essentially a git repo you can resolve conflicts using any of your desired git interfaces. But advisable to use the kito interface if it has to do with creation/deletion an entity(project/tool) rather than just content update because the entity ids are mapped to your kito workspace. Even in that case if there is any mismatch, you'll be able to resolve them later.
