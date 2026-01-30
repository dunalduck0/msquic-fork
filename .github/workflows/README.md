# Agentic Workflows

This directory contains agentic workflow definitions. Agentic workflows are AI-powered automations that can perform tasks like generating reports, analyzing code, and creating GitHub issues.

## Available Workflows

### daily-repo-status.md
Creates daily status reports as GitHub issues, tracking repository activity, progress, and providing actionable recommendations.

- **Schedule**: Daily
- **Outputs**: GitHub issues with prefix `[repo-status]`
- **Labels**: `report`, `daily-status`

## How Agentic Workflows Work

1. **Markdown Format**: Workflows are defined as markdown files with YAML front matter
2. **AI Processing**: GitHub's AI agent reads the workflow instructions
3. **Automatic Execution**: Workflows run on schedule or manual trigger
4. **Safe Outputs**: Agents can only perform approved actions (e.g., create issues)

## Creating a New Workflow

1. Create a `.md` file in this directory
2. Add YAML metadata and instructions
3. Test with manual trigger
4. Enable schedule when ready

See [AgenticWorkflows.md](../docs/AgenticWorkflows.md) for detailed documentation.

## Example Structure

```markdown
---
description: Your workflow description
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  issues: read
safe-outputs:
  create-issue:
    title-prefix: "[prefix] "
    labels: [label1, label2]
---

# Workflow Title

Your instructions for the AI agent...
```

## Best Practices

- Start with read-only permissions
- Use clear, specific instructions
- Set appropriate schedules
- Monitor generated outputs
- Use descriptive labels

For more information, see the [full documentation](../docs/AgenticWorkflows.md).
