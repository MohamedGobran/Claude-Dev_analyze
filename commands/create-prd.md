You are helping the user create a Product Requirements Document (PRD) for a new feature.

## Instructions

Follow the Development Framework's PRD creation process:

1. **Get Feature Information**
   Ask the user for:
   - Feature name (from $ARGUMENTS or prompt if missing)
   - Problem being solved
   - Proposed solution
   - Key requirements
   - Success criteria
   - Out of scope items

2. **Create Directory Structure**
   Create: `Dev Plans/[feature-name]/PRD/` and `Dev Plans/[feature-name]/Tasks/`

3. **Create PRD File**
   Location: `Dev Plans/[feature-name]/PRD/[feature-name].md`

   Use this template:
   ```markdown
   # [Feature Name]

   ## Problem
   [What problem are we solving? Why does this matter?]

   ## Solution
   [What we're building. High-level approach.]

   ## Requirements
   - Requirement 1
   - Requirement 2
   - Requirement 3

   ## Success Criteria
   - [ ] Criterion 1
   - [ ] Criterion 2
   - [ ] Criterion 3

   ## Out of Scope
   - Item 1
   - Item 2

   ## Technical Considerations
   [Architecture notes, dependencies, integration points]

   ## Research Required
   - [ ] Research item 1
   - [ ] Research item 2
   ```

4. **Create Tasks File**
   Location: `Dev Plans/[feature-name]/Tasks/[feature-name]-tasks.md`

   Use this template:
   ```markdown
   # [Feature Name] - Tasks

   ## Task 1: [Name]
   **Why**: [Context and reasoning]
   **What**: [Goal of this task]
   **Files**: [`file1.cs`, `file2.cs`]
   **Depends**: None / Task #X
   **Criteria**:
   - [ ] Criterion 1
   - [ ] Criterion 2
   **Status**: ⬜

   ---

   ## Task 2: [Name]
   **Why**: [Context and reasoning]
   **What**: [Goal of this task]
   **Files**: [`file3.cs`]
   **Depends**: Task #1
   **Criteria**:
   - [ ] Criterion 1
   **Status**: ⬜

   ---

   _Add more tasks as needed_
   ```

5. **Pre-Implementation Checklist**
   After creating both files, remind the user of the 6-point verification:
   - ✅ PRD complete and reviewed
   - ✅ Tasks detailed with context
   - ✅ Dependencies mapped
   - ✅ Similar implementations analyzed
   - ✅ Unfamiliar tools/packages researched
   - ✅ Architecture documented

## Workflow

1. If $ARGUMENTS provided, use as feature name. Otherwise, ask user for feature name.
2. Ask user for problem, solution, requirements, success criteria, and out-of-scope items.
3. Create the directory structure.
4. Create PRD file with populated template.
5. Create Tasks file with initial task breakdown (ask user for task details).
6. Display both file locations and remind about pre-implementation verification.

## Key Principles

- **Documentation-First**: PRD must exist before any code
- **Zero-Assumption**: Ask clarifying questions, don't assume
- **Clear Criteria**: Success criteria must be measurable
- **Task Breakdown**: Tasks should be small, focused, and have clear acceptance criteria

## Example Interaction

User: `/create-prd email-notifications`