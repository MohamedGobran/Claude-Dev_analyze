# Claude Code Analysis Framework

## Core Principle
**Code is truth. Verify everything. Document reality, not assumptions.**

---

## Phase 1: Discovery

**Understand what you're looking at:**
- Identify project type and structure
- Locate entry points
- Identify all subprojects and their purposes
- Determine technology stack from actual files
- Map the build and dependency management system

**Document:**
- Project architecture (single, multi-project, monorepo)
- Main technologies and frameworks
- How projects relate to each other

---

## Phase 2: Code Analysis

**Follow the actual implementation:**
- Start from entry points and trace execution flow
- Map components and their real responsibilities
- Identify data flow through the system
- Understand external integrations (databases, APIs, services)
- Recognize design patterns actually used

**Document:**
- Component purposes based on their actual behavior
- Real dependencies between components
- Data transformations and business logic
- Integration points and protocols

---

## Phase 3: Documentation Verification

**Check existing documentation against code:**
- Verify setup instructions actually work
- Confirm API documentation matches implementation
- Validate configuration options exist and work as described
- Test examples and sample code
- Identify all discrepancies

**When documentation doesn't match code:**
- Trust the code
- Document what actually happens
- Note the discrepancy for correction
- Research why if the difference matters

---

## Phase 4: Understanding Unknown Elements

**When encountering unfamiliar code:**
- Analyze how it's actually used in the project
- Look at test cases for usage patterns
- Check the calling code for context
- Research official documentation if needed
- Understand the real purpose, not assumed purpose

**Document your confidence level:**
- Fully understood and verified
- Partially understood, needs more investigation
- Unknown purpose, documented observations only

---

## Phase 5: Documentation Creation

**Create documentation based on verified facts:**

### Essential Documents

**README**: What the project actually does and how to use it
**ARCHITECTURE**: Real system design from code analysis  
**SETUP**: Instructions that actually work on clean system
**CONFIGURATION**: All settings with real defaults from code
**API**: Actual endpoints, parameters, and responses
**TROUBLESHOOTING**: Real issues encountered and solutions

### For Multi-Project Solutions

**PROJECT_MAP**: How projects actually depend on each other
**INTEGRATION**: How projects communicate (verified from code)
**SHARED_RESOURCES**: What's actually shared between projects

---

## Key Analysis Areas

### Relationships
- Which components call which others
- What data flows between them
- Which are required vs optional
- What breaks if something is missing

### Critical Paths
- Main execution flows
- Error handling mechanisms
- Performance-critical sections
- Security boundaries

### Technical Debt
- Inconsistencies in patterns
- Deprecated code still in use
- Missing error handling
- Incomplete implementations

---

## Documentation Standards

### Always Include
- What you verified vs what you couldn't verify
- Source of information (code file, test, runtime behavior)
- Discrepancies found between docs and implementation
- Areas requiring further investigation

### Never Include
- Assumptions about how something "should" work
- Guesses about purpose or behavior
- Unverified information from outdated docs
- Generic descriptions that don't reflect actual implementation

---

## Handling Special Cases

### Legacy Code
- Document what it does, not what it might have done
- Note deprecated patterns still in use
- Identify dead code that's never called
- Mark unclear purposes for investigation

### Example/Test Projects
- Clearly distinguish from production code
- Document what they demonstrate
- Note if examples are outdated
- Verify they actually run

### External Integrations
- Document actual protocols used
- Note authentication methods in use
- Map data formats from real requests/responses
- Identify error handling patterns

---

## Quality Checks

### Before Completing Analysis
- Every major component understood or marked as unclear
- All project relationships mapped
- Setup instructions verified to work
- Critical functionality documented
- Uncertainties clearly marked

### Signs of Complete Understanding
- Can explain data flow from input to output
- Know why each major component exists
- Understand error scenarios and handling
- Can identify what changes would break the system

---

## Output Format

### For Clear Understanding
```
Component: [Name]
Purpose: [What it actually does based on code]
Implementation: [How it achieves this]
Dependencies: [What it needs to function]
Used By: [What depends on it]
```

### For Uncertainties
```
Component: [Name]  
Observed Behavior: [What can be verified]
Unclear Aspects: [What needs investigation]
Possible Purpose: [Based on context, marked as unverified]
Research Needed: [What to investigate]
```

---

## Remember

The goal is to enable any developer to understand the **real system** quickly and accurately. If you haven't verified it from the code, mark it as unverified. If you don't understand it, document what you observe and mark it for investigation.

**No assumptions. Only verified facts and clearly marked uncertainties.**
