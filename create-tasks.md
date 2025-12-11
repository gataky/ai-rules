# Rule: Generating a Task List from User Requirements

## Goal

To guide an AI assistant in creating a detailed, step-by-step task list in Markdown format based on requirements, PRDs, or feature requests. The task list should be:
*   **AI-executable:** Clear and actionable for an AI assistant to understand and implement
*   **Developer-friendly:** Understandable by a junior developer for manual implementation
*   **Pattern-aware:** Follow existing codebase patterns and conventions
*   **Comprehensive:** Cover all implementation steps including code, tests, and verification

## Output

- **Format:** Markdown (`.md`)
- **Location:** `/tasks/`
- **Filename:** `tasks-[feature-name].md` (e.g., `tasks-user-profile-editing.md`)

## Process

1.  **Receive Requirements:** The user provides a feature request, task description, PRD, or points to existing documentation
2.  **Analyze Codebase:** Before generating tasks, analyze the existing codebase to understand:
    *   Current file structure and code organization
    *   Existing patterns, conventions, and architectural approaches
    *   Similar features or components that can serve as reference implementations
    *   Testing infrastructure and patterns
    *   Build, run, and deployment processes
3.  **Analyze Requirements:** Analyze the functional and technical requirements from the provided information, considering how they align with existing codebase patterns
4.  **Identify Relevant Files:** Identify all files that will need to be created or modified based on requirements and codebase analysis. List these under the `Relevant Files` section, including corresponding test files if applicable.
5.  **Phase 1: Generate Parent Tasks:** Based on the requirements and codebase analysis, create the file and generate the main, high-level tasks required to implement the feature. **IMPORTANT: Always include task 0.0 "Create feature branch" as the first task, unless the user specifically requests not to create a branch.** Use your judgement on how many additional high-level tasks to use. It's likely to be about 5. Present these tasks to the user in the specified format (without sub-tasks yet). Inform the user: "I have generated the high-level tasks based on your requirements. Ready to generate the sub-tasks? Respond with 'Go' to proceed."
6.  **Wait for Confirmation:** Pause and wait for the user to respond with "Go".
7.  **Phase 2: Generate Sub-Tasks:** Once the user confirms, break down each parent task into smaller, actionable sub-tasks necessary to complete the parent task. Ensure sub-tasks:
    *   Are clear enough for an AI assistant to understand and execute
    *   Are also understandable by a junior developer
    *   Follow the existing codebase patterns and conventions identified in step 2
    *   Cover all implementation details including tests
    *   Reference specific files, functions, or components where applicable
8.  **Generate Final Output:** Combine the parent tasks, sub-tasks, relevant files, and notes into the final Markdown structure.
9.  **Save Task List:** Save the generated document in the `/tasks/` directory with the filename `tasks-[feature-name].md`, where `[feature-name]` describes the main feature or task being implemented (e.g., if the request was about user profile editing, the output is `tasks-user-profile-editing.md`).

## Output Format

The generated task list _must_ follow this structure:

```markdown
## Relevant Files

- `path/to/potential/file1.ts` - Brief description of why this file is relevant (e.g., Contains the main component for this feature).
- `path/to/file1.test.ts` - Unit tests for `file1.ts`.
- `path/to/another/file.tsx` - Brief description (e.g., API route handler for data submission).
- `path/to/another/file.test.tsx` - Unit tests for `another/file.tsx`.
- `lib/utils/helpers.ts` - Brief description (e.g., Utility functions needed for calculations).
- `lib/utils/helpers.test.ts` - Unit tests for `helpers.ts`.

### Notes

- Unit tests should typically be placed alongside the code files they are testing (e.g., `MyComponent.tsx` and `MyComponent.test.tsx` in the same directory).
- Use `npx jest [optional/path/to/test/file]` to run tests. Running without a path executes all tests found by the Jest configuration.

## Instructions for Completing Tasks

**IMPORTANT:** As you complete each task, you must check it off in this markdown file by changing `- [ ]` to `- [x]`. This helps track progress and ensures you don't skip any steps.

Example:
- `- [ ] 1.1 Read file` → `- [x] 1.1 Read file` (after completing)

Update the file after completing each sub-task, not just after completing an entire parent task.

## Tasks

- [ ] 0.0 Create feature branch
  - [ ] 0.1 Create and checkout a new branch for this feature (e.g., `git checkout -b feature/[feature-name]`)
- [ ] 1.0 Parent Task Title
  - [ ] 1.1 [Sub-task description 1.1]
  - [ ] 1.2 [Sub-task description 1.2]
- [ ] 2.0 Parent Task Title
  - [ ] 2.1 [Sub-task description 2.1]
- [ ] 3.0 Parent Task Title (may not require sub-tasks if purely structural or configuration)
```

## Interaction Model

The process explicitly requires a pause after generating parent tasks to get user confirmation ("Go") before proceeding to generate the detailed sub-tasks. This ensures the high-level plan aligns with user expectations before diving into details.

## Target Audience

Assume the primary readers of the task list are:
1.  **AI assistants** - Tasks should be clear, explicit, and actionable so an AI can understand and execute them
2.  **Junior developers** - Tasks should be understandable and provide sufficient context for manual implementation

Tasks should be written in human-readable format (Option B style) that is clear enough for both AI and humans to understand. The AI will infer the necessary actions from well-written task descriptions.
