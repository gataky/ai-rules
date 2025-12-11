# Rule: Generating a Product Requirements Document (PRD)

## Goal

To guide an AI assistant in creating a highly technical Product Requirements Document (PRD) in Markdown format. The PRD should be:
*   **AI-executable:** Clear and explicit enough for an AI assistant to parse and implement
*   **Developer-friendly:** Understandable by a junior developer for manual implementation
*   **Technically detailed:** Focused on implementation details with minimal non-technical content
*   **Comprehensive:** Cover all technical specifications, architecture, and patterns needed for implementation

## Process

1.  **Receive Initial Prompt:** The user provides a brief description or request for a new feature or functionality.
2.  **Analyze Existing Codebase:** Before asking questions, analyze the existing codebase to understand:
    *   Current tech stack (languages, frameworks, libraries)
    *   Existing architectural patterns and conventions
    *   Code organization and file structure
    *   Similar features or components that can serve as reference
    *   Testing patterns and practices
    *   Build and deployment configurations
3.  **Ask Comprehensive Clarifying Questions:** Based on the codebase analysis and initial prompt, ask as many questions as needed until all ambiguity is resolved. Do not limit the number of questions. If there is any doubt about requirements, technical approach, or implementation details, ask for clarification. Make sure to provide options in letter/number lists so the user can respond easily with their selections.
4.  **Generate PRD:** Based on the initial prompt, codebase analysis, and the user's answers to the clarifying questions, generate a PRD using the structure outlined below.
5.  **Save PRD:** Save the generated document as `prd-[feature-name].md` inside the `/tasks` directory.

## Clarifying Questions (Guidelines)

Ask as many questions as needed to eliminate all ambiguity and gather sufficient detail for implementation. Focus on both functional requirements and technical implementation details. Common areas that require clarification:

*   **Problem/Goal:** What problem does this feature solve? What is the primary objective?
*   **Core Functionality:** What are the key actions and behaviors? What are the inputs and outputs?
*   **Tech Stack & Libraries:** What technologies, frameworks, or libraries should be used? Are there existing libraries in the project to leverage?
*   **Architecture & Patterns:** Should this follow an existing pattern in the codebase? What architectural approach should be used (e.g., MVC, event-driven, microservices)?
*   **Data Models:** What data structures are needed? How should data be stored and retrieved? What's the schema?
*   **APIs & Integration:** What APIs or external services need to be integrated? What are the endpoints and data contracts?
*   **State Management:** How should state be managed? What state management patterns or libraries should be used?
*   **Error Handling:** How should errors be handled? What error states need to be considered?
*   **Security:** Are there authentication, authorization, or data validation requirements?
*   **Performance:** Are there performance requirements or constraints? Expected load or scale?
*   **Testing:** What testing approach should be used? Unit tests, integration tests, E2E tests?
*   **Scope/Boundaries:** What is explicitly out of scope?
*   **Success Criteria:** How will we know when this feature is successfully implemented?

**Important:** If there is ANY doubt or ambiguity about functional or technical requirements, ask for clarification. It's better to ask too many questions than to leave gaps that will require rework later.

### Formatting Requirements

- **Number all questions** (1, 2, 3, etc.)
- **List options for each question as A, B, C, D, etc.** for easy reference
- Make it simple for the user to respond with selections like "1A, 2C, 3B"

### Example Format

```
1. What authentication mechanism should this feature use?
   A. JWT tokens (existing pattern in the codebase)
   B. Session-based authentication
   C. OAuth2 with third-party provider
   D. API keys

2. How should data be persisted for this feature?
   A. PostgreSQL database (existing)
   B. Redis cache only
   C. File system storage
   D. External service API

3. What state management approach should be used?
   A. Redux (existing pattern)
   B. React Context API
   C. Component-level state only
   D. External state management library (specify which)

4. Should this feature handle real-time updates?
   A. Yes, using WebSockets
   B. Yes, using polling (specify interval)
   C. Yes, using Server-Sent Events (SSE)
   D. No, manual refresh only

5. What error handling pattern should be followed?
   A. Try-catch with centralized error logger
   B. Error boundaries (React)
   C. Promise rejection handlers
   D. Combination of the above (specify)
```

## PRD Structure

The generated PRD should include the following sections:

1.  **Introduction/Overview:** Briefly describe the feature, the problem it solves, and the goal. Keep this concise and focused on what needs to be built.
2.  **Goals:** List the specific, measurable objectives for this feature. Include both functional goals and technical goals (e.g., "Maintain sub-100ms response time", "Support 1000 concurrent users").
3.  **Tech Stack & Architecture:** Document the technical foundation for this feature:
    *   **Languages:** Programming languages to be used
    *   **Frameworks & Libraries:** Required frameworks, libraries, and versions (including existing project dependencies to leverage)
    *   **Architectural Pattern:** Overall approach (e.g., REST API, event-driven, layered architecture, microservices)
    *   **Existing Patterns to Follow:** Reference similar features or components in the codebase that should serve as templates
    *   **Data Storage:** Database type, storage mechanism, caching strategy
    *   **External Services/APIs:** Third-party integrations required
4.  **Functional Requirements:** List the specific functionalities the feature must have. Use clear, concise, technical language. Number these requirements. Focus on behaviors, inputs, outputs, and edge cases. Include:
    *   Core functionality and user actions
    *   Data validation rules
    *   Error handling requirements
    *   State management needs
5.  **Technical Specifications:** Provide implementation details:
    *   **Data Models/Schema:** Define data structures, types, interfaces, or database schemas
    *   **API Contracts:** Endpoints, request/response formats, status codes
    *   **Component/Module Structure:** High-level breakdown of code organization
    *   **Integration Points:** How this feature connects with existing systems
    *   **Complex Logic:** For complex algorithms or workflows, include pseudo code or detailed logic descriptions
    *   **Security Requirements:** Authentication, authorization, input sanitization, encryption
    *   **Performance Requirements:** Response times, scalability considerations, optimization needs
6.  **Non-Goals (Out of Scope):** Clearly state what this feature will *not* include to manage scope.
7.  **Testing Requirements:** Specify testing approach:
    *   Unit tests (what should be tested)
    *   Integration tests (what integrations should be verified)
    *   E2E tests (what user flows should be tested)
    *   Test coverage expectations
8.  **Success Metrics:** How will the success of this feature be measured? Focus on technical and functional success criteria (e.g., "All tests pass", "Feature handles 1000 requests/sec", "Zero critical bugs in first week").
9.  **Open Questions:** List any remaining questions or areas needing further clarification.

## Target Audience

Assume the primary readers of the PRD are:
1.  **AI assistants** - The PRD should be structured with clear, explicit requirements that an AI can parse and execute
2.  **Junior developers** - Requirements should be explicit, unambiguous, and provide sufficient technical detail for implementation

The PRD should be **highly technical** and focus on implementation details. Include minimal non-technical context—only what's necessary to understand the goal and inform technical decisions. Avoid business fluff, marketing language, or excessive explanations of "why" unless it directly impacts technical implementation choices.

## Output

*   **Format:** Markdown (`.md`)
*   **Location:** `/tasks/`
*   **Filename:** `prd-[feature-name].md`

## Final Instructions

1. **Analyze the codebase first** - Before asking questions, explore the codebase to understand existing patterns, tech stack, and architecture
2. **Ask comprehensive questions** - Ask as many clarifying questions as needed. Cover both functional and technical requirements. If in doubt, ask
3. **Focus on technical details** - The PRD should be implementation-focused with minimal fluff. Include pseudo code for complex logic
4. **Document the tech stack** - Always include a detailed Tech Stack & Architecture section based on your codebase analysis
5. **Make it AI-executable** - Write requirements clearly enough that an AI assistant could understand and implement them
6. **Do NOT start implementing** - The PRD is for planning only. Do not write code or implement the feature
7. **Iterate based on answers** - Take the user's answers and create a comprehensive, technically detailed PRD
