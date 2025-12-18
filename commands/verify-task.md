You are helping the user verify a task is complete according to dev-framework.md standards.

## Instructions

Perform a thorough verification of the completed task against the Development Framework's completion criteria.

## Verification Process

### 1. Identify Task
- If $ARGUMENTS provided, use as task identifier
- Otherwise, ask user which task to verify (task name or number)
- Locate the task in the Tasks file

### 2. Acceptance Criteria Check
Review each criterion listed in the task:
- ✅ Criterion met with evidence
- ❌ Criterion not met
- ⚠️ Partially met or unclear

For each criterion, examine:
- What was the requirement?
- What evidence exists that it's met?
- Are there any gaps or concerns?

### 3. Code Pattern Matching
Verify code follows existing codebase patterns:

**Check:**
- ✅ Naming conventions match (files, classes, methods, variables)
- ✅ Code structure matches similar existing files
- ✅ Using statements/imports follow project conventions
- ✅ Error handling approach matches existing patterns
- ✅ C# conventions followed (PascalCase public, camelCase private)
- ✅ Dependency injection patterns match existing code
- ✅ Async/await usage matches project patterns
- ✅ Logging follows existing patterns

**Actions:**
1. Find 2-3 similar files in the codebase
2. Compare new code against those files
3. Identify any pattern deviations
4. Note deviations as ❌ with explanation

### 4. Example Project Verification
Check that testing via Examples/ folder is complete:

**Verify:**
- ✅ Example project exists in `/Examples/[feature-name]/`
- ✅ Example has README.md explaining purpose and usage
- ✅ Example demonstrates all new functionality
- ✅ Example runs without errors
- ✅ Happy path works correctly
- ✅ Edge cases are handled
- ✅ Error scenarios handled gracefully
- ✅ Comments explain key behaviors

**Actions:**
1. Locate the example project
2. Read the README
3. Review the example code
4. Consider running it if possible (or ask user to confirm it runs)

### 5. Documentation Review
Verify documentation is updated:

**Check:**
- ✅ PRD success criteria marked complete
- ✅ Task status updated to ✅
- ✅ Code comments added for complex logic only
- ✅ API documentation updated (if applicable)
- ✅ CLAUDE.md updated (if architecture changed)
- ✅ README updated (if user-facing changes)

### 6. No Assumptions Made
Verify zero-assumption policy was followed:

**Review:**
- ✅ Similar code was analyzed before implementation
- ✅ Unfamiliar tools/packages were researched (evidence in comments or docs)
- ✅ Official documentation was consulted
- ✅ No "I think this works like..." assumptions

### 7. Overall Completion Checklist
Present final checklist:

```
## Task Verification Report: [Task Name]

### Acceptance Criteria (from Tasks file)
- ✅/❌ Criterion 1: [status and notes]
- ✅/❌ Criterion 2: [status and notes]

### Code Quality
- ✅/❌ Naming conventions match existing code
- ✅/❌ Structure matches similar files
- ✅/❌ Error handling follows patterns
- ✅/❌ C# conventions followed
- ✅/❌ DI patterns match existing code

### Testing (Examples/)
- ✅/❌ Example project exists
- ✅/❌ Example works correctly
- ✅/❌ All features demonstrated
- ✅/❌ Edge cases covered

### Documentation
- ✅/❌ PRD updated
- ✅/❌ Task marked complete
- ✅/❌ Relevant docs updated

### Research & Verification
- ✅/❌ Similar code analyzed
- ✅/❌ Unknown elements researched
- ✅/❌ No assumptions made

### RESULT: ✅ READY TO MARK COMPLETE / ❌ NEEDS WORK

### Issues Found:
[List any issues that need to be addressed]

### Recommendations:
[Suggestions for improvement or next steps]
```

## Workflow

1. Get task identifier from $ARGUMENTS or ask user
2. Read the task details from Tasks file
3. Perform each verification step systematically
4. For each check, provide ✅, ❌, or ⚠️ with brief explanation
5. Generate final verification report
6. If task passes all checks (all ✅), confirm it can be marked complete
7. If any ❌ or ⚠️, list what needs to be fixed before marking complete

## Key Principles

- **Thorough**: Check every aspect, don't skip steps
- **Evidence-Based**: Look for actual proof, not assumptions
- **Pattern-Focused**: Code must match existing patterns
- **Documentation-Critical**: Updates must be complete
- **Honest**: Mark ❌ when criteria aren't met, even if "almost done"

## Example Usage

User: `/verify-task add-email-validation`

Then systematically go through all verification steps and provide the detailed report.
