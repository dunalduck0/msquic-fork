# Agentic Workflows

Agentic workflows are AI-powered automation workflows that can be configured to perform repository tasks automatically. These workflows are defined as markdown files in the `.github/workflows/` directory and can be triggered on a schedule or manually.

## What Agentic Workflows Can Do

Agentic workflows leverage AI agents to:

1. **Monitor Repository Activity**
   - Track issues, pull requests, and discussions
   - Identify patterns and trends in development
   - Monitor code changes and releases

2. **Generate Reports**
   - Create status reports and summaries
   - Generate insights about repository health
   - Provide recommendations for maintainers

3. **Automate Analysis**
   - Analyze repository metrics
   - Identify potential issues or bottlenecks
   - Track progress toward goals

4. **Community Engagement**
   - Highlight contributor achievements
   - Summarize community discussions
   - Provide project updates

## Existing Agentic Workflows

### Daily Repository Status Report

**File**: `.github/workflows/daily-repo-status.md`

This workflow automatically creates daily status reports as GitHub issues. It:

- Gathers recent repository activity (issues, PRs, discussions, releases, code changes)
- Tracks progress and highlights achievements
- Provides project status and recommendations
- Suggests actionable next steps for maintainers

**Configuration:**
```yaml
on:
  schedule: daily
  workflow_dispatch:
  stop-after: +1mo  # Automatically stops after 30 days

permissions:
  contents: read
  issues: read
  pull-requests: read

safe-outputs:
  create-issue:
    title-prefix: "[repo-status] "
    labels: [report, daily-status]
```

**Features:**
- Runs daily on a schedule
- Can be triggered manually via workflow_dispatch
- Creates GitHub issues with status reports
- Uses positive, encouraging tone with emojis
- Automatically adjusts length based on activity level

## Creating New Agentic Workflows

To create a new agentic workflow:

1. **Create a Markdown File**
   - Place it in `.github/workflows/` directory
   - Name it descriptively (e.g., `weekly-security-scan.md`)

2. **Define the Workflow Metadata**
   ```yaml
   ---
   description: |
     Brief description of what the workflow does
   
   on:
     schedule: daily|weekly|monthly
     workflow_dispatch:
   
   permissions:
     contents: read
     issues: read
     pull-requests: read
   
   tools:
     github:
   
   safe-outputs:
     create-issue:
       title-prefix: "[your-prefix] "
       labels: [label1, label2]
   
   source: githubnext/agentics/workflows/your-workflow.md@hash
   ---
   ```

3. **Write the Agent Instructions**
   - Use clear, natural language
   - Specify what data to gather
   - Define the output format
   - Set the tone and style

4. **Example Workflow Ideas**
   - Weekly security vulnerability reports
   - Monthly contributor highlights
   - Performance trend analysis
   - Documentation coverage reports
   - Dependency update summaries
   - Issue triage assistance

## Workflow Components

### Scheduling
- `schedule: daily` - Runs once per day
- `schedule: weekly` - Runs once per week
- `schedule: monthly` - Runs once per month
- `workflow_dispatch` - Allows manual triggering

### Permissions
Define what the agent can access:
- `contents: read` - Read repository content
- `issues: read/write` - Read or create issues
- `pull-requests: read/write` - Read or create PRs

### Tools
Specify which tools the agent can use:
- `github` - GitHub API access
- Custom tools as needed

### Safe Outputs
Control what the agent can create:
- `create-issue` - Create GitHub issues
- `create-pr` - Create pull requests (with additional permissions)
- `post-comment` - Comment on issues/PRs

## Best Practices

1. **Start Simple**
   - Begin with read-only workflows
   - Test thoroughly before enabling write permissions
   - Use manual triggers during development

2. **Define Clear Goals**
   - Specify exactly what you want the agent to do
   - Provide examples of desired output
   - Set boundaries and constraints

3. **Monitor and Iterate**
   - Review generated outputs regularly
   - Adjust instructions based on results
   - Set appropriate stop-after dates for experimental workflows

4. **Security Considerations**
   - Use minimal required permissions
   - Avoid exposing sensitive data
   - Review agent-generated content before merging

5. **Community Communication**
   - Use clear labels for agent-generated issues
   - Maintain a positive, helpful tone
   - Provide context for automated actions

## Limitations

- Workflows automatically stop after 30 days unless `stop-after` is removed
- Agents work with publicly available repository data
- Network access can be configured with `network: defaults`
- Generated content should be reviewed by maintainers

## Examples

### Example 1: Performance Monitoring
```markdown
---
description: Weekly performance analysis and regression detection
on:
  schedule: weekly
permissions:
  contents: read
  issues: write
tools:
  github:
safe-outputs:
  create-issue:
    title-prefix: "[performance] "
    labels: [performance, report]
---

# Weekly Performance Report

Analyze recent commits and pull requests for potential performance impacts.

## What to include
- Recent performance-related changes
- Benchmark comparisons if available
- Potential regression risks
- Optimization opportunities

## Process
1. Review commits from the past week
2. Identify performance-critical changes
3. Generate recommendations
4. Create issue with findings
```

### Example 2: Documentation Helper
```markdown
---
description: Identify undocumented code and suggest documentation improvements
on:
  schedule: weekly
permissions:
  contents: read
  issues: write
tools:
  github:
safe-outputs:
  create-issue:
    title-prefix: "[docs] "
    labels: [documentation, help-wanted]
---

# Documentation Coverage Report

Find code that needs documentation and suggest improvements.

## What to include
- Recently added functions without documentation
- APIs with incomplete documentation
- Outdated documentation references
- Documentation improvement suggestions

## Style
- Be constructive and specific
- Provide examples of good documentation
- Prioritize public APIs
```

## Getting Help

- Check existing workflow files in `.github/workflows/*.md`
- Review generated issues for examples of output
- Consult GitHub's agentic workflows documentation
- Ask in repository discussions for guidance

## Resources

- [GitHub Agentic Workflows](https://githubnext.com/projects/agentics/)
- [Workflow Examples](https://github.com/githubnext/agentics)
- [Repository Workflows](.github/workflows/)
