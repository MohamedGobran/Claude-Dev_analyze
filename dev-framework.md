# Development Framework for .NET Projects

## Core Principle: Research → Plan → Implement → Verify

**NEVER assume. ALWAYS verify.**

---

## MANDATORY: Documentation-First Updates

**When receiving design changes, requirement updates, architecture refinements, or feedback:**

1. **STOP implementation immediately**
2. **Update documentation FIRST**:
   - Update PRD with new requirements
   - Update Tasks with modified steps
   - Update Architecture docs if applicable
   - Add notes about what changed and why
3. **Review updated docs for consistency**
4. **THEN resume implementation**

❌ **NEVER**: Implement changes without updating docs  
✅ **ALWAYS**: Update PRD/Tasks → Review → Implement

**All development documents MUST reflect current reality.**

---

## MANDATORY: Zero-Assumption Policy

You MUST research before implementing. For ANY unfamiliar element:

**1. Read Codebase**
- Study 2-3 similar files for patterns
- Analyze existing tool/package usage
- Review configuration files

**2. Read Documentation**
- Official docs (first priority)
- GitHub repositories and examples
- API references and guides

**3. Verify Understanding**
- Cross-reference multiple sources
- Test with actual code
- Confirm behavior matches documentation

❌ **NEVER**: "I think this works like..."  
✅ **ALWAYS**: "Let me verify in the codebase and documentation..."

---

## Pre-Implementation Requirements

### 1. Create PRD
**Location**: `Dev Plans/[feature-name]/PRD/[feature-name].md`

```markdown
# [Feature Name]

## Problem
[What problem are we solving?]

## Solution
[What we're building]

## Requirements
- Requirement 1
- Requirement 2

## Success Criteria
- [ ] Criterion 1
- [ ] Criterion 2

## Out of Scope
- Item 1
```

### 2. Create Tasks Document
**Location**: `Dev Plans/[feature-name]/Tasks/[feature-name]-tasks.md`

```markdown
# [Feature Name] - Tasks

## Task 1: [Name]
**Why**: [Context]
**What**: [Goal]
**Files**: [`file.cs`]
**Depends**: Task #X / None
**Criteria**:
- [ ] Criterion 1
**Status**: ⬜

---
```

### 3. Pre-Coding Verification

Before ANY code, verify ALL items:

1. ✅ PRD complete and reviewed
2. ✅ Tasks detailed with context
3. ✅ Dependencies mapped
4. ✅ Similar implementations analyzed
5. ✅ Unfamiliar tools/packages researched
6. ✅ Architecture documented

**Missing ANY? Stop and complete.**

---

## Implementation Workflow

### Phase 0: Handle Changes (If Applicable)
**If receiving design/requirement/architecture changes or feedback:**
1. Update PRD immediately
2. Update Tasks document
3. Update any affected architecture docs
4. Document what changed and why
5. Review for consistency
6. **Only then proceed to implementation**

### Phase 1: Explore (No Coding)
- Read relevant codebase files
- Identify patterns and conventions
- Research unfamiliar elements (docs, GitHub, examples)
- Map dependencies and integration points

### Phase 2: Plan
- Document step-by-step approach
- Identify challenges and solutions
- Verify plan against existing patterns

### Phase 3: Implement
- One task at a time
- Match existing patterns exactly
- Test after each task completion
- Commit with clear message

### Phase 4: Verify
- Test via example project
- Validate acceptance criteria
- Update documentation
- Mark task complete

---

## Code Quality Standards

### Pattern Matching (Critical)
**Before writing ANY code:**
1. Find similar files in codebase
2. Study structure, naming, formatting
3. Match patterns EXACTLY

**Match:**
- Naming conventions (files, variables, methods, classes)
- Code structure and organization
- Import/using statements order
- Error handling approach
- Comments style (minimal, only for complex logic)

**When uncertain**: Search codebase → Read docs → Follow existing approach → Never guess

### .NET Specifics
- Follow C# conventions (PascalCase public, camelCase private)
- Use appropriate patterns for project type:
  - **Console**: Program.cs entry point, args handling
  - **Windows Service**: ServiceBase, OnStart/OnStop
  - **WinForms**: Designer pattern, event handlers
  - **WPF**: MVVM pattern, XAML + code-behind
  - **Blazor**: Component model, @code blocks
  - **Web API**: Controller pattern, dependency injection
- Match existing dependency injection patterns
- Follow existing async/await usage
- Use existing logging patterns

---

## Testing via Examples

**We test through example projects in `/Examples/` - NO test projects.**

### For Each Feature:
```
/Examples/[feature-name]/
  README.md          # Purpose and usage
  [main-file]        # Working demonstration
  [support-files]    # If needed
```

### Verification Checklist:
- [ ] Happy path works
- [ ] Edge cases handled
- [ ] Errors handled gracefully
- [ ] Example runs without errors
- [ ] All features demonstrated
- [ ] Comments explain behavior

---

## Completion Criteria

Before marking ANY task complete:
- [ ] All acceptance criteria met
- [ ] Code matches existing patterns
- [ ] Example project works
- [ ] Documentation updated
- [ ] Clear commit message written

---

## .NET Commands Reference

```bash
# Build & Run
dotnet build                              # Build project
dotnet build -c Release                   # Release build
dotnet run                                # Run project
dotnet run --project [Path]               # Run specific project
dotnet clean                              # Clean artifacts

# Testing (via examples)
dotnet run --project Examples/[Name]/[Name].csproj

# Dependencies
dotnet restore                            # Restore packages
dotnet add package [Name]                 # Add package
dotnet list package                       # List packages
dotnet list package --outdated            # Check updates

# Code Quality
dotnet format                             # Format code
dotnet format --verify-no-changes         # Check formatting

# Project Management
dotnet add reference [Path]               # Add reference
dotnet list reference                     # List references
```

---

## Quick Reference

### Starting Feature:
PRD → Tasks → 6-Point Verification → Explore → Plan → Code → Test → Document → Commit

### Writing Code:
Read Similar Code → Research Unknown Elements → Match Patterns → Implement → Test → Never Assume

### When Blocked:
Search Codebase → Read Documentation → Find Examples → Verify → Implement

---

## Anti-Patterns

❌ Assuming tool/package behavior without verification  
❌ Coding before PRD and tasks exist  
❌ **Implementing changes without updating PRD/Tasks/docs first**  
❌ Ignoring existing codebase patterns  
❌ Skipping example project creation  
❌ Working on multiple tasks simultaneously  
❌ Marking complete without testing  
❌ Vague commit messages  

---

## Task Status

⬜ Not Started | 🔄 In Progress | ✅ Completed | ⏸️ Blocked | ⚠️ Review

---

## Core Values

**Verification > Assumption**: Research and confirm before implementing  
**Consistency > Innovation**: Match existing patterns over new approaches  
**Planning > Speed**: PRD and tasks prevent rework  
**Quality > Quantity**: One task done right beats three done poorly

---

## Analysis Guidelines

When analyzing or improving code:
1. Read implementation completely
2. Research unfamiliar components
3. Identify actual limitations (not assumed)
4. Propose improvements considering:
   - **Usability**: User interaction improvements
   - **Scalability**: Growth handling
   - **Functionality**: Feature enhancements
5. Base recommendations on evidence, not assumptions
