# AI Rules for PRD and Task Generation

This repository contains rules/guides for AI assistants to help structure the software development process from initial feature request to implementation-ready tasks.

## About

These rules enable AI assistants to:
1. **Generate comprehensive PRDs** - Transform feature requests into detailed, technically-focused Product Requirements Documents that are clear enough for AI or junior developers to implement
2. **Break down PRDs into actionable tasks** - Convert requirements into step-by-step task lists with checkboxes to track progress

The workflow follows a structured approach: analyze the codebase, ask clarifying questions, generate detailed documentation, and create implementable tasks.

## Usage

### 1. Creating a PRD with `create-prd.md`

Use this rule when starting a new feature or functionality.

**Example:**

```
I want to add a user profile editing feature to my app.
Please follow the create-prd.md rule to generate a PRD.
```

**What happens:**
1. The AI analyzes your existing codebase (tech stack, patterns, architecture)
2. Asks numbered clarifying questions with lettered options (e.g., "1A, 2C, 3B")
3. Generates a detailed PRD covering:
   - Tech stack and architecture
   - Functional and technical requirements
   - Data models and API contracts
   - Testing requirements
   - Success criteria
4. Saves the PRD to `/tasks/prd-[feature-name].md`

### 2. Creating Tasks with `create-tasks.md`

Use this rule after you have a PRD or clear requirements.

**Example:**

```
I have a PRD for user profile editing at /tasks/prd-user-profile-editing.md.
Please follow the create-tasks.md rule to generate a task list.
```

**What happens:**
1. The AI analyzes your codebase and the requirements
2. Identifies relevant files that need to be created/modified
3. Generates high-level parent tasks (starting with "0.0 Create feature branch")
4. Waits for your confirmation ("Go")
5. Breaks down each parent task into detailed sub-tasks
6. Saves the task list to `/tasks/tasks-[feature-name].md`

**During implementation:**
- Check off tasks as you complete them by changing `- [ ]` to `- [x]`
- This tracks progress and ensures nothing is missed

## Workflow Example

```bash
# Step 1: Generate PRD
"Follow create-prd.md to create a PRD for user authentication"
# Answer clarifying questions: "1A, 2B, 3A, 4D"
# Output: /tasks/prd-user-authentication.md

# Step 2: Generate tasks
"Follow create-tasks.md using /tasks/prd-user-authentication.md"
# Review high-level tasks, respond: "Go"
# Output: /tasks/tasks-user-authentication.md

# Step 3: Implement
# Work through tasks, checking them off as you complete each one
```

## Benefits

- **Consistency:** Follow the same structured process for every feature
- **Clarity:** Eliminate ambiguity through comprehensive clarifying questions
- **Traceability:** Track progress with checkboxes in task lists
- **AI-friendly:** Documentation is structured for both AI and human developers
- **Pattern-aware:** Leverages existing codebase patterns and conventions
