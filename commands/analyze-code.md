You are helping the user analyze code following the analysis-framework.md methodology.

## Core Principle
**Code is truth. Verify everything. Document reality, not assumptions.**

## Instructions

Analyze the code file(s) specified in $ARGUMENTS using systematic investigation, not assumptions.

## Analysis Process

### 1. Identify Target
- If $ARGUMENTS provided, use as file path(s) to analyze
- Otherwise, ask user which file(s) to analyze
- Confirm files exist and are readable

### 2. Discovery Phase
Understand what you're looking at:

**Examine:**
- File type and purpose (entry point, service, model, controller, etc.)
- Namespace and project context
- Dependencies and imports
- Class/interface definitions

**Document:**
```
## File: [filename]
**Type**: [Console app / Service / Component / Model / etc.]
**Project**: [Project name]
**Purpose**: [What this file does - based on observation]
```

### 3. Code Analysis Phase
Follow the actual implementation:

**Trace:**
- Entry points (Main, constructors, public methods)
- Execution flow through methods
- Data transformations
- External interactions (DB, API, file system)
- Error handling patterns
- Logging patterns

**For Each Major Component:**
```
### Component: [ClassName / MethodName]

**Purpose**: [What it actually does, verified from code]

**Implementation**: [How it achieves this]
- Key steps in execution flow
- Algorithms or patterns used
- Data it works with

**Dependencies**: [What it requires]
- External libraries
- Other classes/methods
- Configuration
- Database/API connections

**Used By**: [What calls this]
- Callers identified in codebase
- Integration points

**Confidence**: ✅ Fully Understood / ⚠️ Partially Understood / ❓ Needs Investigation
```

### 4. Pattern Recognition
Identify patterns actually used (not assumed):

**Check:**
- ✅ Design patterns (Builder, Factory, Repository, etc.)
- ✅ Naming conventions
- ✅ Error handling approach
- ✅ Async/await usage
- ✅ Dependency injection style
- ✅ Logging patterns
- ✅ Configuration approach

**Document:**
```
## Patterns Identified

**Design Patterns**:
- [Pattern name]: [Where used, why, how]

**Conventions**:
- Naming: [Observed convention]
- Structure: [How code is organized]
- Error Handling: [Try-catch, throw, custom exceptions]

**Integration Patterns**:
- DI: [How dependencies are injected]
- Config: [How configuration is accessed]
- Logging: [What logging framework, how used]
```

### 5. Relationship Mapping
Map connections to other code:

**Identify:**
- Which components this calls
- Which components call this
- What data flows between them
- What breaks if this is missing

**Document:**
```
## Relationships

**Calls**:
- [Component1] - [Why and what data]
- [Component2] - [Why and what data]

**Called By**:
- [Component3] - [Context]
- [Component4] - [Context]

**Data Flow**:
- Input: [What data comes in]
- Processing: [What happens to it]
- Output: [What data goes out]

**Critical Dependencies**:
- Required: [Must have for function]
- Optional: [Can work without]
```

### 6. Document Uncertainties
Mark what you couldn't verify:

**For Unclear Elements:**
```
## Uncertainties

### [Component/Method Name]
**Observed Behavior**: [What the code does]
**Unclear Aspects**: [What's not clear]
**Possible Purpose**: [Hypothesis - MARKED AS UNVERIFIED]
**Research Needed**:
- [ ] Check official documentation for [library/framework]
- [ ] Find usage examples in codebase
- [ ] Trace execution path
- [ ] Ask domain expert about [business logic]

**Confidence**: ❓ Needs Investigation
```

### 7. Generate Analysis Report

```
# Code Analysis Report

## File: [filepath]
**Analyzed**: [date]
**Confidence**: [Overall understanding level]

---

## Summary
[Brief description of what this code does and why it exists]

---

## Components

[Detailed breakdown from Phase 3]

---

## Patterns & Conventions

[Pattern documentation from Phase 4]

---

## Relationships

[Relationship mapping from Phase 5]

---

## Technical Details

**Technology Stack**:
- [Framework/library versions identified]

**Configuration**:
- [Config files or settings used]

**External Dependencies**:
- [Databases, APIs, services]

---

## Verified Facts
- ✅ [Fact 1 - confirmed from code]
- ✅ [Fact 2 - confirmed from code]

## Unverified Aspects
- ❓ [Aspect 1 - needs research]
- ❓ [Aspect 2 - unclear purpose]

---

## Recommendations

**For Understanding**:
- [What to investigate next]

**For Improvement**:
- [Potential enhancements - only if clear from analysis]

**For Documentation**:
- [What should be documented]

---

## Next Steps
- [ ] Research item 1
- [ ] Verify assumption about X
- [ ] Trace execution path for Y
```

## Workflow

1. Get file path(s) from $ARGUMENTS or ask user
2. Read the file(s) completely
3. Perform Discovery Phase - understand context
4. Perform Code Analysis Phase - trace execution
5. Identify patterns and conventions used
6. Map relationships to other components
7. Document verified facts vs. uncertainties
8. Generate structured analysis report
9. Provide clear next steps for deeper understanding

## Key Principles

- **Trust Code**: What code does > what docs say it does
- **No Assumptions**: Mark uncertainties clearly
- **Verify Everything**: Cross-reference multiple sources
- **Document Reality**: What actually happens, not what should happen
- **Mark Confidence**: ✅ Verified / ⚠️ Partial / ❓ Unknown

## Analysis Depth Levels

**Level 1 - Quick Overview**:
- File purpose and structure
- Main components
- Key dependencies

**Level 2 - Detailed Analysis** (default):
- Execution flow
- Pattern identification
- Relationship mapping
- Verification of behavior

**Level 3 - Deep Dive**:
- Algorithm analysis
- Performance considerations
- Security implications
- Complete dependency tree

Ask user which level to perform, or use Level 2 by default.

## Example Usage

User: `/analyze-code RMAutoReporting/Program.cs`

Then systematically analyze the file and provide the structured report.

## Special Cases

**For Entry Points** (Program.cs, Main):
- Map application initialization
- Document service registration
- Identify configuration loading

**For Services/Business Logic**:
- Document business rules
- Trace data transformations
- Identify integration points

**For Models/DTOs**:
- Document properties and validation
- Note relationships to other models
- Identify where used

**For Legacy Code**:
- Document what it does (not what it might have done)
- Note deprecated patterns still in use
- Identify dead code never called
