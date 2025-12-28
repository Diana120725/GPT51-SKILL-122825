prompt-for-opal-agent-122825

Please think deeper and iterate until get excellent results. Don't ask any other questions. Ending with 20 comprehensive follow up questions.


You will be generating comprehensive development instructions for OPAL GOOGLE (Google's AI-powered development platform) based on a technical specification provided by the user. Your goal is to transform the technical specification into clear, actionable instructions that OPAL can use to build the application.

Here is the technical specification:

<technical_specification>
{{TECHNICAL_SPECIFICATION}}
</technical_specification>

Your task is to analyze this technical specification and generate detailed instructions for OPAL GOOGLE that cover:

1. **Application Overview**: A concise summary of what the application does, its purpose, and key features
2. **Technology Stack & Dependencies**: All frameworks, libraries, APIs, and tools required
3. **Architecture & Structure**: How the application is organized (components, services, data flow)
4. **Data Models & Types**: All interfaces, types, enums, and data structures
5. **UI/UX Requirements**: Styling approach, theming, layout structure, and design specifications
6. **Component Specifications**: Detailed breakdown of each component including:
   - Purpose and responsibility
   - State management requirements
   - Props and interfaces
   - Key features and functionality
   - User interactions and event handling
7. **Service Layer**: API integrations, utility functions, and business logic
8. **Configuration & Security**: Environment variables, API keys, permissions, and security considerations
9. **Implementation Details**: Specific technical requirements, edge cases, and important implementation notes

<scratchpad>
Before generating the final instructions, I should:
- Identify the core application type and purpose
- Extract all technology dependencies and versions
- Map out the component hierarchy and relationships
- Note any special styling or theming requirements
- Identify all external API integrations
- Highlight security and configuration needs
- Note any specific implementation patterns or requirements
- Organize information in a logical order for development
</scratchpad>

When writing the OPAL instructions:

- Use clear, imperative language ("Create a component...", "Implement a service...", "Configure...")
- Be specific about technical requirements (versions, exact library names, API endpoints)
- Include code structure examples where helpful (interface definitions, component signatures)
- Specify the exact behavior for user interactions and state changes
- Note any dependencies between components or services
- Highlight critical implementation details that affect functionality
- Organize instructions in a logical development order
- Use proper technical terminology from the specification
- Preserve any specific naming conventions, color codes, or design specifications
- Include error handling and edge case requirements

Format your output as follows:

<opal_instructions>
# Application Development Instructions for OPAL GOOGLE

## 1. Project Overview
[Concise description of the application]

## 2. Technology Stack & Setup
[List all dependencies, frameworks, and tools with versions]

## 3. Project Architecture
[Describe the overall structure and organization]

## 4. Data Models & Types
[Define all interfaces, types, and data structures]

## 5. Styling & Theming
[Specify all design requirements, colors, fonts, layouts]

## 6. Component Implementation
[Detailed specifications for each component]

## 7. Service Layer Implementation
[Specifications for all services and utilities]

## 8. Configuration & Security
[Environment setup, API keys, security measures]

## 9. Special Implementation Notes
[Any critical details, edge cases, or specific requirements]
</opal_instructions>

Your final output should contain ONLY the content within the <opal_instructions> tags. This should be a complete, standalone document that OPAL GOOGLE can use to build the application from scratch. Do not include your scratchpad or any meta-commentary in the final output.
