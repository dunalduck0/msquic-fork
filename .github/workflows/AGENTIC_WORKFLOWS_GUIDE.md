# Agentic Workflows - Quick Reference

## What Can Agentic Workflows Do?

Agentic workflows are AI-powered automations that can help maintain and improve your repository. Here's what they can do:

### 📊 **Monitor & Report**
- Generate daily/weekly/monthly status reports
- Track repository health metrics
- Summarize recent activity (issues, PRs, commits)
- Identify trends and patterns

### 🔍 **Analyze & Detect**
- Find undocumented code
- Detect potential performance issues
- Identify security vulnerabilities
- Analyze code coverage gaps
- Review dependency updates

### 🎯 **Assist & Recommend**
- Suggest actionable next steps
- Provide optimization opportunities
- Recommend documentation improvements
- Highlight stale issues or PRs
- Identify good first issues

### 👥 **Engage Community**
- Highlight contributor achievements
- Welcome new contributors
- Summarize discussions
- Celebrate milestones

### ⚙️ **Automate Tasks**
- Create issues for findings
- Generate reports automatically
- Schedule regular reviews
- Maintain repository hygiene

## Current Workflows in This Repository

### 1. Daily Repository Status Report
**File**: `.github/workflows/daily-repo-status.md`

Creates a daily issue with:
- Recent activity summary
- Progress tracking
- Actionable recommendations
- Community highlights

**Features**:
- Runs daily automatically
- Creates GitHub issues with `[repo-status]` prefix
- Positive, encouraging tone
- Adjusts length based on activity

## Quick Start

### View Documentation
- **Full Guide**: [docs/AgenticWorkflows.md](../docs/AgenticWorkflows.md)
- **Workflow Directory**: [.github/workflows/](./)

### Create Your First Workflow

1. **Create** a new `.md` file in `.github/workflows/`
2. **Add** YAML front matter with configuration
3. **Write** natural language instructions for the AI
4. **Test** with manual trigger
5. **Enable** schedule when ready

### Example: Weekly Security Check

```markdown
---
description: Weekly security vulnerability scan and report
on:
  schedule: weekly
  workflow_dispatch:
permissions:
  contents: read
  issues: write
tools:
  github:
safe-outputs:
  create-issue:
    title-prefix: "[security] "
    labels: [security, report]
---

# Weekly Security Report

Scan for potential security issues and vulnerabilities.

## Tasks
1. Review recent code changes for security concerns
2. Check for known vulnerabilities in dependencies
3. Identify security best practice violations
4. Create issue with findings and recommendations

## Style
- Be specific and actionable
- Include severity levels
- Provide remediation guidance
```

## Benefits

✅ **Save Time**: Automate repetitive analysis tasks  
✅ **Stay Informed**: Regular updates on repository health  
✅ **Improve Quality**: Identify issues proactively  
✅ **Engage Community**: Recognize contributions  
✅ **Be Proactive**: Catch problems early  

## Limitations

⚠️ Workflows stop after 30 days by default (remove `stop-after` to run indefinitely)  
⚠️ Agents use publicly available repository data  
⚠️ Generated content should be reviewed by maintainers  
⚠️ Permissions are strictly controlled for safety  

## Get Started Now

1. Review the existing workflow: [daily-repo-status.md](./daily-repo-status.md)
2. Check generated issues with `[repo-status]` label
3. Read the full documentation: [AgenticWorkflows.md](../docs/AgenticWorkflows.md)
4. Create your own workflow!

---

**Questions?** See the [full documentation](../docs/AgenticWorkflows.md) or ask in repository discussions.
