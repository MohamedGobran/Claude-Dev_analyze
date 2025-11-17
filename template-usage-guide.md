# CLAUDE.md Template Usage Guide

## How to Use the Generic Template

### For New Projects

1. **Copy these three files to your project root:**
   - `claude.md` (the generic template)
   - `analysis-framework.md` (unchanged)
   - `dev-framework.md` (unchanged)

2. **Run Claude Code to populate the template:**
   - Claude Code will analyze your project following the analysis-framework.md
   - It will populate all the placeholder sections with verified information
   - The result will be a project-specific claude.md

### Template Sections Explained

| Section | What Claude Code Should Fill |
|---------|----------------------------|
| **Project Overview** | Brief description of what the project does and its purpose |
| **Build Commands** | Actual commands needed to build, run, and test the project |
| **Architecture** | Project structure, main components, how they interact |
| **Technology Stack** | Languages, frameworks, versions used |
| **Key Features** | Main capabilities and functionality |
| **Dependencies** | External libraries and services required |
| **Configuration** | Settings, environment variables, config files |
| **Usage Examples** | Basic code snippets showing how to use the project |
| **Testing** | How to run tests, test structure |
| **Important Notes** | Platform requirements, limitations, gotchas |
| **Documentation** | Existing docs and where to find them |
| **Project-Specific Guidelines** | Unique patterns, conventions, or requirements |

### Workflow

```
1. Place template files in new project
       ↓
2. Claude Code analyzes project (using analysis-framework.md)
       ↓
3. Claude Code populates claude.md template with findings
       ↓
4. Claude Code follows dev-framework.md for any development work
       ↓
5. Project now has complete, accurate documentation
```

### Key Benefits

- **Consistent Structure**: Every project gets documented the same way
- **No Assumptions**: Claude Code verifies everything before documenting
- **Reusable Frameworks**: The analysis and dev frameworks work for any project
- **Quick Setup**: Just copy three files and let Claude Code do the analysis
- **Maintained Standards**: Frameworks ensure quality across all projects

### Example Projects

The template works for any project type:
- Web applications (Node.js, Python, Ruby, PHP)
- Desktop applications (Electron, .NET, Java)
- Mobile apps (React Native, Flutter)
- Libraries and packages
- Microservices
- CLI tools
- Data processing pipelines
- Machine learning projects

### Tips

1. **Let Claude Code populate first**: Don't fill in manually
2. **Review after population**: Verify the populated information
3. **Keep frameworks updated**: Improve them based on experience
4. **Project-specific additions**: Add unique sections if needed
5. **Version control**: Commit the populated claude.md

### File Structure in Your Project

```
your-project/
├── claude.md              # Populated with project specifics
├── analysis-framework.md  # How to analyze code
├── dev-framework.md       # How to develop features
├── src/                   # Your project code
└── ...
```

This approach ensures every project you work on with Claude Code has:
- Consistent documentation quality
- Verified information (no assumptions)
- Clear development standards
- Systematic analysis approach
