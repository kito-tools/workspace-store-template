# Projects Directory

This directory contains project-specific documentation organized by project slug. Each project in your Kito workspace gets its own subdirectory containing specifications, architecture decisions, and development workflows.

## Directory Structure

```
projects/
 README.md                    # This file  
 {project-slug}/              # Individual project directories
     metadata.toml           # Project metadata and UUID mapping
     instructions/           # Project rules and workflows
        project-rules.md   # Project-specific AI assistant rules
        deployment.md      # Deployment workflows and procedures
        **/*.md            # Additional instruction files
     notes/                 # Project specifications and documentation
         specification.md   # Project requirements and goals
         architecture.md    # Architecture decisions and design
         **/*.md            # Additional note files
```

## Project Organization

### Metadata File (`metadata.toml`)
Each project directory contains a metadata file for system integration:
```toml
# Project metadata - automatically managed by Kito
[entity]
id = "550e8400-e29b-41d4-a716-446655440000"
type = "workspace_project"
slug = "current-project-slug"
created_at = "2025-01-15T10:30:00Z"
last_sync_at = "2025-01-15T10:35:00Z"
sync_version = 1

# Optional project-specific configuration
[project]
name = "Project Display Name"
description = "Brief project description"
repository = "https://github.com/user/repo"
status = "active"  # active, paused, completed, archived
```

**Important**: The `[entity]` section is automatically managed by Kito. Manual edits may cause sync issues. The `[project]` section can be safely edited to add additional context.

### Instructions Directory
Contains project-specific guidance and workflows for development:

#### `project-rules.md` - Project-Specific Rules
- Coding standards and conventions specific to this project
- Architecture constraints and design principles
- Technology choices and rationale
- Team conventions and collaboration guidelines

**Example structure:**
```markdown
# Project Rules for {Project Name}

## Architecture Principles
- Use microservices architecture with Docker containers
- Implement event-driven communication between services
- Follow domain-driven design patterns

## Technology Stack
- Frontend: React 18+ with TypeScript
- Backend: Node.js with Express
- Database: PostgreSQL with Prisma ORM
- Testing: Jest for unit tests, Playwright for E2E

## Code Standards
- Use conventional commits for all changes
- Require PR reviews for main branch
- Maintain 90%+ test coverage
```

#### `deployment.md` - Deployment Workflows
- Environment-specific deployment procedures
- Infrastructure as code configurations
- CI/CD pipeline definitions
- Monitoring and observability setup

**Example structure:**
```markdown
# Deployment Workflows for {Project Name}

## Environment Setup
### Development
- Local Docker Compose stack
- Hot reload enabled for all services
- Debug logging active

### Staging  
- Kubernetes deployment
- Production-like data setup
- Performance monitoring enabled

### Production
- Blue-green deployment strategy
- Automated rollback capabilities
- Comprehensive logging and metrics

## Deployment Steps
1. Run full test suite
2. Build Docker images
3. Deploy to staging environment
4. Run smoke tests
5. Deploy to production
6. Monitor metrics and logs
```

### Notes Directory
Contains project specifications, documentation, and knowledge:

#### `specification.md` - Project Requirements
- Project goals and success criteria
- Feature requirements and user stories
- Technical requirements and constraints
- Timeline and milestone definitions

**Example structure:**
```markdown
# Project Specification: {Project Name}

## Overview
Brief description of what this project aims to achieve.

## Goals
- Primary objective 1
- Primary objective 2
- Success metrics and KPIs

## Features
### Core Features
- Feature 1: Description and acceptance criteria
- Feature 2: Description and acceptance criteria

### Future Features  
- Enhancement 1: Description and priority
- Enhancement 2: Description and priority

## Technical Requirements
- Performance requirements
- Security requirements
- Scalability requirements
- Compliance requirements
```

#### `architecture.md` - Architecture Documentation
- System design and component interactions
- Data models and database schema
- API specifications and integration points
- Security architecture and considerations

**Example structure:**
```markdown
# Architecture: {Project Name}

## System Overview
High-level description of system components and their relationships.

## Component Architecture
### Frontend Layer
- Component structure and state management
- Routing and navigation patterns
- UI/UX design system integration

### Backend Layer
- Service architecture and API design
- Data access patterns and ORM usage
- Authentication and authorization

### Data Layer
- Database schema and relationships
- Caching strategies
- Data migration and backup procedures

## Integration Points
- External API dependencies
- Third-party service integrations
- Inter-service communication patterns
```

## File Naming Conventions

### Instructions Files
- `project-rules.md` - Core project development rules
- `deployment.md` - Deployment and infrastructure workflows
- `testing.md` - Testing strategies and procedures
- `{feature-area}-rules.md` - Feature-specific development guidance

### Notes Files
- `specification.md` - Project requirements and goals
- `architecture.md` - System design and technical decisions
- `research.md` - Investigation notes and findings
- `decisions.md` - Architecture decision records (ADRs)
- `onboarding.md` - New team member guide

## Project Lifecycle Management

### Initialization Phase
- Define project goals in `specification.md`
- Establish architecture decisions in `architecture.md`  
- Set up development rules in `project-rules.md`
- Configure deployment workflows in `deployment.md`

### Development Phase
- Continuously update specifications as requirements evolve
- Document architecture changes and decisions
- Refine development rules based on team learnings
- Maintain deployment procedures with infrastructure changes

### Maintenance Phase
- Keep documentation current with system changes
- Archive obsolete specifications and decisions
- Update deployment procedures for operational changes

## Best Practices

### Content Organization
- **Keep specifications current**: Update requirements as the project evolves
- **Document decisions**: Record the rationale behind architectural choices
- **Maintain workflows**: Keep deployment procedures accurate and tested
- **Version major changes**: Use git history to track specification evolution

### Collaboration
- **Review changes**: Use pull requests for significant specification updates
- **Involve stakeholders**: Include product owners in requirement discussions
- **Share context**: Make implicit project knowledge explicit in documentation

### Integration with Development
- **Link to code**: Reference specific implementations in architecture docs
- **Update with releases**: Align documentation updates with code releases
- **Validate procedures**: Regularly test deployment and development workflows

## Translation to AI Assistants

Project instructions serve as canonical specifications that Kito translates for different AI coding tools:

- **Project-specific rules**: Exported to `.claude/settings.json`, `.cursorrules`
- **Workflow automation**: Integrated with task runners and CI/CD systems
- **Context export**: Available for AI assistants through Kito CLI and MCP server

## Sync Behavior

### From Kito to GitHub
- Project specification changes made in Kito web UI are committed automatically
- Commit messages indicate the type of change (spec update, architecture change, etc.)

### From GitHub to Kito
- Direct file edits in GitHub are pulled into Kito during workspace access
- Git commits from local development are synchronized seamlessly
- Conflicts are resolved through Kito's conflict resolution interface

### CLI Integration
The Kito CLI provides project-specific operations:
```bash
kito project sync           # Sync project specs to local AI assistants
kito project context        # Export project context for AI tools
kito project verify         # Validate project configuration
```

---

This project-centric organization enables comprehensive project management while maintaining flexibility for different development methodologies and team structures.