# Claude Code Setup Guide
## Integrating Custom Development Frameworks with /init

**Version:** 1.0  
**Last Updated:** December 2024  
**Purpose:** Step-by-step guide to initialize Claude Code in existing projects with custom development frameworks

---

## 📋 Table of Contents

1. [Prerequisites](#prerequisites)
2. [Phase 1: Initialize Project](#phase-1-initialize-project-5-minutes)
3. [Phase 2: Integrate Your Generic Template](#phase-2-integrate-your-generic-template-10-minutes)
4. [Phase 3: Create Custom Commands](#phase-3-create-custom-commands-15-minutes)
5. [Phase 4: Verify Setup](#phase-4-verify-setup-5-minutes)
6. [Phase 5: Commit to Git](#phase-5-commit-to-git-2-minutes)
7. [Daily Usage](#daily-usage-commands)
8. [Troubleshooting](#troubleshooting)

**Total Setup Time:** ~30 minutes per project

---

## Prerequisites

### Required Files

Ensure you have these framework files ready:

- ✅ `claude-generic.md` - Your CLAUDE.md template
- ✅ `dev-framework.md` - Your development workflow methodology
- ✅ `analysis-framework.md` - Your code analysis standards

### Required Tools

- ✅ Claude Code installed and authenticated
- ✅ Git repository initialized
- ✅ Terminal/command line access

### Framework Overview

Your frameworks should follow:
- **dev-framework.md:** Research → Plan → Implement → Verify workflow
- **analysis-framework.md:** Code analysis and documentation methodology
- **claude-generic.md:** Reusable template structure for all projects

---

## Phase 1: Initialize Project (5 minutes)

### Step 1.1: Navigate to Project

```bash
cd /path/to/your/project
```

### Step 1.2: Start Claude Code

```bash
claude
```

Wait for Claude Code to launch and show the welcome screen.

### Step 1.3: Run Init Command

In the Claude Code interface, type:

```
/init
```

### Step 1.4: Grant Permissions

When prompted:
- Press `2` to "Allow All" for similar file read operations
- This speeds up the analysis process

### Step 1.5: Wait for Completion

**What happens during /init:**
- ✓ Analyzes package files (package.json, *.csproj, etc.)
- ✓ Reads existing documentation (README, etc.)
- ✓ Examines configuration files
- ✓ Maps project structure
- ✓ Detects coding conventions
- ✓ Generates initial CLAUDE.md

**Duration:** 2-5 minutes depending on project size

**✅ Checkpoint:** CLAUDE.md file created in project root

---

## Phase 2: Integrate Your Generic Template (10 minutes)

### Step 2.1: Copy Framework Files

```bash
# Copy your frameworks to project root
cp /path/to/dev-framework.md ./
cp /path/to/analysis-framework.md ./
```

**Verify files copied:**
```bash
ls -la | grep -E "dev-framework|analysis-framework"
```

### Step 2.2: Merge Template with Generated CLAUDE.md

**Copy and paste this prompt into Claude Code:**

```
I have a generic CLAUDE.md template that I use for all my projects. 

Please help me merge it with the CLAUDE.md you just generated:

1. Read my template file: @claude-generic.md
2. Read current CLAUDE.md
3. Create a new CLAUDE.md that:
   - Keeps YOUR generated project-specific sections (Build Commands, Architecture, Tech Stack, etc.)
   - Adds my framework references at the top using @ imports
   - Adds my development methodology sections
   - Removes any generic content that's already in my frameworks
   - Keeps total length under 300 lines
   - Maintains clear, concise structure

My frameworks are:
- @dev-framework.md (Research → Plan → Implement → Verify workflow)
- @analysis-framework.md (Code analysis methodology)

Key principles from my frameworks:
- Documentation-first updates (PRD before code)
- Zero-assumption policy (verify, don't assume)
- Pattern matching from existing code
- Testing via Examples/ folder (no test projects)

Please show me the merged CLAUDE.md for review before creating it.
```

### Step 2.3: Review Proposed Changes

Claude will show you the merged CLAUDE.md content.

**Review checklist:**
- [ ] Framework references at top using @ imports
- [ ] Project-specific sections preserved
- [ ] Development principles included
- [ ] Total length reasonable (<300 lines)
- [ ] No duplicate or redundant content

### Step 2.4: Confirm Creation

If satisfied with the merge, respond:

```
Looks good. Please:
1. Create the new CLAUDE.md file
2. Add dev-framework.md and analysis-framework.md references
3. Ensure it's concise and project-specific
```

**✅ Checkpoint:** CLAUDE.md now includes your frameworks

---

## Phase 3: Create Custom Commands (15 minutes)

### Step 3.1: Create Commands Directory

```bash
mkdir -p .claude/commands
```

**Verify directory created:**
```bash
ls -la .claude/
```

### Step 3.2: Create create-prd Command

**Prompt for Claude Code:**

```
Create custom slash command files for my development workflow. 

Create these three commands in .claude/commands/:

1. create-prd.md
2. verify-task.md  
3. analyze-code.md

For each command, follow the structure and principles from @dev-framework.md.

Let's start with create-prd.md. Create a file that:
- Guides me through creating a new feature PRD
- Creates directory structure: Dev Plans/[feature]/PRD/
- Uses template from dev-framework.md
- Creates corresponding Tasks file
- Accepts feature name via $ARGUMENTS

Show me the content first for review.
```

**After reviewing the content, confirm:**

```
Perfect. Create .claude/commands/create-prd.md with that content.
```

**✅ Checkpoint:** create-prd.md created

### Step 3.3: Create verify-task Command

**Prompt for Claude Code:**

```
Now create verify-task.md command that:
- Checks task completion against dev-framework.md standards
- Verifies all acceptance criteria
- Confirms code matches existing patterns
- Validates example project exists and works
- Reviews documentation updates
- Provides checklist with ✅/❌

Show me the content first.
```

**After reviewing, confirm:**

```
Perfect. Create .claude/commands/verify-task.md with that content.
```

**✅ Checkpoint:** verify-task.md created

### Step 3.4: Create analyze-code Command

**Prompt for Claude Code:**

```
Finally, create analyze-code.md command that:
- Follows analysis-framework.md methodology
- Analyzes code files provided in $ARGUMENTS
- Documents what's verified vs. unverified
- Identifies patterns and conventions
- Notes unclear aspects for investigation
- Provides structured output

Show me the content first.
```

**After reviewing, confirm:**

```
Perfect. Create .claude/commands/analyze-code.md with that content.
```

**✅ Checkpoint:** All three custom commands created

### Step 3.5: Verify Commands Created

```bash
ls -la .claude/commands/
```

**Expected output:**
```
create-prd.md
verify-task.md
analyze-code.md
```

---

## Phase 4: Verify Setup (5 minutes)

### Step 4.1: Test Custom Command

In Claude Code:

```
/project:create-prd test-feature
```

**Verify:**
- [ ] Creates `Dev Plans/test-feature/PRD/` directory
- [ ] Generates PRD file with template structure
- [ ] Creates `Dev Plans/test-feature/Tasks/` directory
- [ ] Generates Tasks file

**Clean up test:**
```bash
rm -rf "Dev Plans/test-feature"
```

### Step 4.2: Check Memory Loading

In Claude Code:

```
/memory
```

**Verify output shows:**
- [ ] Project CLAUDE.md loaded
- [ ] dev-framework.md reference visible
- [ ] analysis-framework.md reference visible

### Step 4.3: Test Framework Integration

**Prompt for Claude Code:**

```
Let's verify the frameworks are loaded. 

Please tell me:
1. What is the core principle from dev-framework.md?
2. What is the first step before ANY implementation?
3. What should I do when receiving design changes?

This confirms you can access the framework content.
```

**Expected response should mention:**
- ✓ "NEVER assume. ALWAYS verify"
- ✓ Creating PRD and Tasks before coding
- ✓ "Update documentation FIRST" when receiving changes

### Step 4.4: Test Pattern Matching Guidance

**Prompt for Claude Code:**

```
What should I do before writing ANY code according to the framework?
```

**Expected response should mention:**
- ✓ Find 2-3 similar files
- ✓ Study structure, naming, formatting
- ✓ Match patterns EXACTLY
- ✓ Never guess/assume

**✅ Checkpoint:** All frameworks accessible and working

---

## Phase 5: Commit to Git (2 minutes)

### Step 5.1: Add .gitignore Entry

```bash
echo "CLAUDE.local.md" >> .gitignore
```

**Why:** CLAUDE.local.md is for personal preferences and shouldn't be shared

### Step 5.2: Review Changes

```bash
git status
```

**Expected untracked files:**
- CLAUDE.md
- dev-framework.md
- analysis-framework.md
- .claude/commands/
- .gitignore (modified)

### Step 5.3: Stage and Commit

```bash
git add CLAUDE.md dev-framework.md analysis-framework.md .claude/ .gitignore

git commit -m "feat: configure Claude Code with development frameworks

- Add CLAUDE.md with project-specific context
- Integrate dev-framework.md and analysis-framework.md
- Create custom slash commands for workflow automation
- Set up .claude/commands/ for team-wide workflows"
```

### Step 5.4: Push to Remote

```bash
git push
```

**✅ Checkpoint:** Setup committed and shared with team

---

## Final File Structure

After successful setup:

```
your-project/
├── CLAUDE.md                           # Main config (merged)
├── dev-framework.md                    # Development workflow
├── analysis-framework.md               # Analysis standards
├── .claude/
│   └── commands/
│       ├── create-prd.md              # /project:create-prd
│       ├── verify-task.md             # /project:verify-task
│       └── analyze-code.md            # /project:analyze-code
├── .gitignore                         # Includes CLAUDE.local.md
└── Dev Plans/                         # Created when first PRD made
    └── [feature-name]/
        ├── PRD/
        │   └── [feature-name].md
        └── Tasks/
            └── [feature-name]-tasks.md
```

---

## Daily Usage Commands

### Starting New Features

```bash
# In Claude Code:
/project:create-prd user-authentication
```

Creates complete PRD and Tasks structure.

### Verifying Task Completion

```
/project:verify-task
```

Checks against all framework criteria.

### Analyzing Code Patterns

```
/project:analyze-code src/Services/AuthService.cs
```

Follows analysis-framework.md methodology.

### Managing Context

```
/memory                    # View loaded files
/clear                     # Clear context for new task
/permissions               # Manage tool permissions
```

### Editing Configuration

```
/memory                    # Opens CLAUDE.md in editor
```

Make changes, save, and restart Claude Code to apply.

---

## Troubleshooting

### Custom Commands Don't Appear

**Symptom:** `/project:` commands not showing in autocomplete

**Solution:**
```
/permissions
```

Verify file read permissions for `.claude/commands/` directory.

**Alternative:**
```bash
# Check file permissions
ls -la .claude/commands/

# Ensure files are readable
chmod 644 .claude/commands/*.md
```

### Frameworks Not Loading

**Symptom:** Claude doesn't follow framework principles

**Solution:**
```
/memory
```

Check which files are loaded. Verify:
- [ ] `@dev-framework.md` import exists in CLAUDE.md
- [ ] `@analysis-framework.md` import exists in CLAUDE.md
- [ ] Files exist in project root
- [ ] No typos in @ import paths

**Fix:**
```
/memory
```
Edit CLAUDE.md to correct @ import paths, save, and restart.

### /init Doesn't Update Existing CLAUDE.md

**Symptom:** Running `/init` again doesn't suggest improvements

**Solution:**

```
Please review the current CLAUDE.md and suggest improvements based on:
1. Current codebase structure
2. New files or patterns added since last init
3. Any outdated build commands or dependencies
4. Missing documentation

Compare against the codebase and provide specific recommendations.
```

### Context Window Filling Up

**Symptom:** Warning about context window running out

**Solution:**
1. `/clear` to reset context
2. Keep CLAUDE.md concise (<300 lines)
3. Use @ imports for detailed docs
4. Scope each chat to one feature/task

### Commands Execute But Wrong Behavior

**Symptom:** Commands run but don't follow framework

**Solution:**
```bash
# Review command file
cat .claude/commands/create-prd.md

# Verify it references framework
grep "@dev-framework.md" .claude/commands/create-prd.md
```

Update command to include framework reference:
```markdown
Follow the PRD structure from @dev-framework.md
```

### Permission Prompts Every Time

**Symptom:** Claude keeps asking for same permissions

**Solution:**
```
/permissions
```

Add to allowlist:
- Read operations for project files
- Specific domains if using web search
- Grep/search commands

**Or start with flag:**
```bash
claude --permission-mode acceptEdits
```

⚠️ **Warning:** Only use in trusted environments

---

## Advanced Tips

### Personal Preferences

Create `CLAUDE.local.md` for personal settings:

```bash
# In project root
touch CLAUDE.local.md
```

Add personal preferences:
```markdown
# Personal Preferences

- I prefer verbose error messages
- Always show me the plan before executing
- Use 4-space indentation for my changes
```

**Note:** This file is gitignored and won't affect team members.

### Monorepo Setup

For monorepos, create CLAUDE.md at multiple levels:

```
monorepo/
├── CLAUDE.md                    # Root level (shared)
├── apps/
│   ├── frontend/
│   │   └── CLAUDE.md           # Frontend-specific
│   └── backend/
│       └── CLAUDE.md           # Backend-specific
└── packages/
    └── shared/
        └── CLAUDE.md           # Shared lib-specific
```

Claude automatically loads all CLAUDE.md files from current directory up to root.

### Importing Additional Documentation

In CLAUDE.md, import project-specific docs:

```markdown
## Additional Context

See @docs/architecture.md for system design
See @docs/api-docs.md for API specifications
See @CONTRIBUTING.md for contribution guidelines
```

Max depth: 5 recursive imports.

### Using Hooks

Create `.claude/hooks/` for automated actions:

```bash
mkdir -p .claude/hooks
```

Example: Auto-format on file creation:

```bash
# .claude/hooks/post-create-file.sh
#!/bin/bash
dotnet format "$1"
```

See [Claude Code Hooks Documentation](https://code.claude.com/docs/hooks) for details.

---

## Maintenance

### Regular Updates

**Monthly:**
- Review CLAUDE.md for outdated information
- Update build commands if dependencies changed
- Add new patterns discovered in codebase

**After Major Changes:**
- Run `/init` again to get improvement suggestions
- Update framework files if workflow evolved
- Regenerate custom commands if needed

### Team Onboarding

New team members setup:

1. Clone repository (includes CLAUDE.md + frameworks)
2. Install Claude Code
3. `cd project && claude`
4. Custom commands automatically available
5. Optional: Create personal CLAUDE.local.md

**Onboarding time:** ~5 minutes

---

## Best Practices Summary

### ✅ Do's

- Keep CLAUDE.md concise (<300 lines)
- Use @ imports for detailed documentation
- Create custom commands for repeated workflows
- Commit CLAUDE.md and frameworks to version control
- Update documentation BEFORE implementing changes
- Verify and test rather than assume
- Match existing code patterns exactly

### ❌ Don'ts

- Don't put personal preferences in team CLAUDE.md
- Don't include sensitive information in CLAUDE.md
- Don't make CLAUDE.md overly verbose
- Don't skip PRD creation before coding
- Don't assume tool behavior without verification
- Don't ignore existing codebase patterns
- Don't implement changes without updating docs first

---

## Quick Reference Card

| Command | Purpose |
|---------|---------|
| `/init` | Generate/update CLAUDE.md |
| `/memory` | View/edit loaded memory files |
| `/clear` | Reset context for new task |
| `/permissions` | Manage tool permissions |
| `/project:create-prd` | Start new feature with PRD |
| `/project:verify-task` | Check task completion |
| `/project:analyze-code` | Deep code analysis |

---

## Resources

### Official Documentation
- [Claude Code Docs](https://code.claude.com/docs)
- [CLAUDE.md Best Practices](https://claude.com/blog/using-claude-md-files)
- [Custom Commands Guide](https://code.claude.com/docs/en/custom-commands)

### Framework Files
- `dev-framework.md` - Your development methodology
- `analysis-framework.md` - Your analysis standards
- `claude-generic.md` - Your reusable template

---

## Support

**Issues with this guide?**
- Review troubleshooting section above
- Check official Claude Code documentation
- Verify framework files are up to date

**Framework questions?**
- Refer to dev-framework.md for development workflow
- Refer to analysis-framework.md for code analysis

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | Dec 2024 | Initial guide creation |

---

## Checklist: Complete Setup

Use this checklist to verify successful setup:

- [ ] Phase 1: `/init` completed, CLAUDE.md generated
- [ ] Phase 2: Framework files copied and integrated
- [ ] Phase 3: All three custom commands created
- [ ] Phase 4: Commands tested and working
- [ ] Phase 5: Changes committed to Git
- [ ] Custom commands appear in `/project:` autocomplete
- [ ] `/memory` shows framework references
- [ ] Test feature PRD creation works
- [ ] Claude follows framework principles
- [ ] Team members can pull and use immediately

**Setup Complete! 🎉**

You can now use Claude Code with your custom development frameworks across all projects.

---

*This guide is a living document. Update it as your frameworks evolve.*
