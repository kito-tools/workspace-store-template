# Offline Directory >� EXPERIMENTAL

This directory contains cached documentation for tools marked for offline access. When working in environments with limited or no internet connectivity, this directory provides essential documentation and context for your tools.

## Overview

The offline feature allows you to mark specific tools in your workspace for offline availability. When enabled, Kito will:
- Download and cache official documentation
- Store tool-specific context and examples  
- Maintain essential reference materials locally
- Sync updates when connectivity is restored

**Status**: **EXPERIMENTAL** - This feature is in active development and may change significantly.

## Directory Structure

```
offline/
 README.md                    # This file
 metadata.toml               # Offline sync metadata (auto-generated)
 tools/                      # Tool-specific offline documentation
     {tool-slug}/
         metadata.toml       # Tool offline metadata
         docs/              # Cached official documentation
            api-reference.md
            getting-started.md
            **/*.md        # Additional cached docs
         examples/          # Usage examples and code snippets
            basic-usage.md
            advanced-patterns.md
            **/*.md        # Additional examples
         context/           # Tool context and summaries
             overview.md    # Tool summary and key concepts
             quickref.md    # Quick reference guide
             troubleshooting.md
```

## How Offline Access Works

### Marking Tools for Offline Access
1. **In Kito Web UI**: Toggle "Offline Access" in tool settings
2. **Via CLI**: Use `kito tool offline enable {tool-slug}`
3. **Automatic Detection**: Based on usage patterns and project dependencies

### Content Caching Process
When a tool is marked for offline access, Kito will:

1. **Documentation Crawling**: 
   - Extract official documentation from the tool's website
   - Download API references, guides, and tutorials
   - Process and convert to searchable markdown format

2. **Context Generation**:
   - Create tool overview and quick reference guides
   - Generate usage examples from documentation
   - Compile troubleshooting information

3. **Content Optimization**:
   - Remove unnecessary formatting and navigation
   - Optimize for text-based search and AI assistant consumption  
   - Compress and deduplicate content for storage efficiency

### Offline Metadata (`metadata.toml`)
Each offline tool contains metadata for sync management:
```toml
# Offline tool metadata
[offline]
tool_slug = "example-tool"
kito_tool_id = "550e8400-e29b-41d4-a716-446655440000"
offline_enabled_at = "2025-01-15T10:30:00Z"
last_sync_at = "2025-01-15T12:45:00Z"
content_version = "2.1.0"
cache_size_mb = 15.2
expiry_date = "2025-02-15T10:30:00Z"

# Source URLs for documentation
source_urls = [
    "https://example-tool.com/docs",
    "https://api.example-tool.com/reference"
]
```

## Usage Scenarios

### Off-Grid Development
- **Remote locations**: Work without reliable internet
- **Travel coding**: Maintain productivity during travel
- **Network restrictions**: Bypass corporate network limitations

### Performance Optimization  
- **Faster access**: Local documentation reduces lookup time
- **Reduced bandwidth**: Minimize external API calls
- **Consistent availability**: Documentation always accessible

### Privacy and Security
- **Air-gapped environments**: Work in secure, isolated environments
- **Sensitive projects**: Avoid external documentation requests
- **Compliance requirements**: Meet data locality requirements

## File Organization

### Documentation (`docs/`)
Contains processed official documentation:
- **API references**: Complete API documentation with examples
- **User guides**: Step-by-step tutorials and how-to guides  
- **Configuration**: Setup and configuration instructions
- **Migration guides**: Version upgrade and migration information

### Examples (`examples/`)
Curated usage examples and patterns:
- **Basic usage**: Common use cases and simple examples
- **Advanced patterns**: Complex implementations and best practices
- **Integration examples**: How to integrate with other tools
- **Troubleshooting**: Common issues and solutions

### Context (`context/`)
AI-optimized summaries and references:
- **Tool overview**: Concise summary of tool purpose and capabilities
- **Quick reference**: Essential commands, APIs, and configurations
- **Conceptual guides**: Key concepts explained simply
- **Decision trees**: When and how to use specific features

## Sync Behavior

### Initial Setup
```bash
# Enable offline access for a tool
kito tool offline enable react

# Bulk enable for project dependencies  
kito project offline-deps enable my-project

# Check offline status
kito offline status
```

### Content Updates
- **Automatic sync**: Updates when connected to internet
- **Manual refresh**: Force update specific tools
- **Version tracking**: Maintain multiple documentation versions
- **Selective sync**: Choose which content types to cache

### Storage Management
```bash  
# View offline storage usage
kito offline usage

# Clean up old cached content
kito offline cleanup --older-than 30d

# Remove offline access for tool
kito tool offline disable react
```

## Best Practices

### Tool Selection
- **Prioritize core tools**: Focus on frequently used development tools
- **Consider project dependencies**: Include tools critical to your projects  
- **Balance storage**: Monitor offline cache size and cleanup regularly

### Content Management
- **Regular updates**: Refresh offline content when connected
- **Version awareness**: Keep documentation aligned with installed tool versions
- **Selective caching**: Choose essential documentation over comprehensive archives

### Workflow Integration
- **CLI integration**: Use offline content through Kito CLI commands
- **AI assistant context**: Export offline docs as context for AI tools
- **Search optimization**: Structure content for efficient local search

## Limitations and Considerations

### Current Limitations
- **Experimental status**: Feature may change significantly
- **Storage requirements**: Large documentation sets require substantial disk space
- **Content staleness**: Offline content may become outdated
- **Processing overhead**: Initial caching takes time and resources

### Future Enhancements
- **Intelligent caching**: AI-powered content prioritization
- **Incremental updates**: Sync only changed documentation  
- **Compression optimization**: Better storage efficiency
- **Collaborative caching**: Share cached content across team workspaces

### Privacy Considerations
- **Local storage**: All cached content is stored locally in your workspace repository
- **No external tracking**: Offline usage doesn't send data to external services
- **Git inclusion**: Cached content is included in your workspace git repository

## Troubleshooting

### Common Issues
- **Large repository size**: Use `.gitignore` to exclude offline cache from commits
- **Outdated content**: Regularly refresh offline documentation
- **Missing documentation**: Some tools may not support automated documentation extraction

### Resolution Steps
```bash
# Check offline sync status
kito offline status --verbose

# Force refresh specific tool
kito tool offline refresh {tool-slug}  

# Repair corrupted offline data
kito offline repair {tool-slug}

# Reset offline cache
kito offline reset
```

---

**Note**: This experimental feature is designed to enhance developer productivity in offline scenarios. Feedback and usage reports help guide feature development and stability improvements.
