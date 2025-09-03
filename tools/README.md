# Tools Directory

This directory contains tool-specific documentation organized by tool slug. Each tool in your Kito workspace gets its own subdirectory containing instructions and notes.

## Directory Structure

```
tools/
 README.md                    # This file
 {tool-slug}/                 # Individual tool directories
     .kito-meta.json         # Tool metadata and UUID mapping
     instructions/           # AI assistant rules and workflows
        rules.md           # AI assistant rules and preferences
        workflows.md       # Automation and workflow instructions
        **/*.md            # Additional instruction files
     notes/                 # Tool documentation and context
         overview.md        # Tool documentation and context
         usage-examples.md  # Usage patterns and examples
         **/*.md            # Additional note files
```

## Tool Organization

### Metadata File (`.kito-meta.json`)
Each tool directory contains a metadata file for system integration:
```json
{
  "kito_entity_id": "550e8400-e29b-41d4-a716-446655440000",
  "entity_type": "workspace_tool",
  "slug": "current-tool-slug",
  "created_at": "2025-01-15T10:30:00Z",
  "last_sync_at": "2025-01-15T10:35:00Z",
  "sync_version": 1
}
```

**Important**: This file is automatically managed by Kito. Manual edits may cause sync issues.

### Instructions Directory
Contains guidance and automation rules for AI assistants:

#### `rules.md` - AI Assistant Rules
- System-level guidance and preferences
- Code style requirements and conventions
- Import orders and project standards
- Technology preferences and constraints

**Example structure:**
```markdown
# Tool Rules for {Tool Name}

## Code Style
- Always use TypeScript strict mode
- Prefer functional components over class components
- Follow this import order: external, internal, relative

## Best Practices  
- Use async/await instead of .then()
- Implement proper error boundaries
- Add comprehensive JSDoc comments
```

#### `workflows.md` - Automation Workflows
- Step-by-step instructions for repetitive tasks
- Deployment procedures and build processes
- Testing strategies and CI/CD guidance
- Tool-specific automation logic

**Example structure:**
```markdown
# Workflows for {Tool Name}

## Deployment Workflow
1. Run tests: `npm run test`
2. Build project: `npm run build`
3. Deploy to staging: `npm run deploy:staging`
4. Run smoke tests
5. Deploy to production: `npm run deploy:prod`

## Testing Strategy
- Unit tests for all utility functions
- Integration tests for API endpoints
- E2E tests for critical user paths
```

### Notes Directory
Contains documentation, context, and knowledge about the tool:

#### `overview.md` - Tool Documentation
- What the tool does and why it's useful
- Installation and setup instructions  
- Configuration options and requirements
- Key concepts and terminology

#### `usage-examples.md` - Usage Patterns
- Common use cases and examples
- Code snippets and configurations
- Troubleshooting guides
- Performance tips and best practices

## File Naming Conventions

### Instructions Files
- `rules.md` - Core AI assistant rules
- `workflows.md` - Process automation
- `{specific-area}-rules.md` - Domain-specific guidance
- `{workflow-name}.md` - Specific workflow documentation

### Notes Files  
- `overview.md` - General tool documentation
- `usage-examples.md` - Practical examples
- `troubleshooting.md` - Problem-solving guides
- `configuration.md` - Setup and config details
- `{feature-name}.md` - Feature-specific notes

## Best Practices

### Content Organization
- **Keep instructions actionable**: Write clear, executable guidance for AI assistants
- **Make notes comprehensive**: Document context that helps understand the tool
- **Use consistent formatting**: Follow markdown best practices across files
- **Reference external docs**: Link to official documentation when appropriate

### File Management
- **Descriptive filenames**: Use clear, semantic names for additional files
- **Logical grouping**: Group related content in appropriately named files
- **Avoid duplication**: Reference shared concepts rather than repeating them

### Collaboration
- **Clear commit messages**: Describe what changes were made and why
- **Document assumptions**: Make implicit knowledge explicit in notes
- **Update examples**: Keep usage examples current with tool versions

## Translation System

The instructions in this directory serve as **canonical specifications** that Kito translates into formats for different AI coding assistants:

- **Claude Code**: `.claude/settings.json` and project rules
- **Cursor**: `.cursorrules` and workspace settings
- **Aider**: `.aider.conf.yml` configurations  
- **Copilot**: GitHub Copilot workspace settings

This allows you to maintain tool knowledge in one place while supporting multiple AI assistants.

## Sync Behavior

### From Kito to GitHub
- Changes made in Kito web UI are automatically committed to this repository
- Commit messages include sync timestamps and change descriptions

### From GitHub to Kito  
- Direct file edits are detected during workspace access
- Git commits from local clones are pulled into Kito
- Conflicts are resolved through Kito's web interface

### CLI Integration
The Kito CLI can directly manipulate files in this directory:
```bash
kito project sync    # Sync canonical specs to local AI assistants
kito context         # Launch TUI for context management
```

---

This tool-centric organization enables consistent knowledge management while supporting flexible workflows across different development tools and AI assistants.