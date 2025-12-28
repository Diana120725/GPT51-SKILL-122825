You will be generating a SKILL.md document based on a provided technical specification. A SKILL.md document is a comprehensive guide that allows developers or AI systems to understand and reconstruct an application's architecture, features, and implementation details.

Here is the technical specification you will be working with:

<technical_specification>
{{TECHNICAL_SPECIFICATION}}
</technical_specification>

Your task is to analyze this technical specification and create a well-structured SKILL.md document that captures all essential information in a clear, organized format.

A SKILL.md document should include the following sections:

1. **Executive Summary**: A brief overview of the application, its purpose, and key features
2. **Technology Stack**: All frameworks, libraries, APIs, and tools used
3. **Architecture Overview**: High-level system design and component relationships
4. **Data Models**: Key interfaces, types, and data structures
5. **Component Specifications**: Detailed breakdown of each major component, including:
   - Purpose and responsibility
   - State management
   - Key features and functionality
   - Implementation details
6. **Service Layer**: Backend services, API integrations, and utility functions
7. **UI/UX Guidelines**: Design system, theming, color palette, and layout structure
8. **Security & Configuration**: API key management, permissions, and data handling
9. **Dependencies**: Complete list of external packages and versions

Before writing the SKILL.md document, use the scratchpad to plan your approach:

<scratchpad>
- Identify the main sections present in the technical specification
- Note any unique or critical features that need emphasis
- Determine the logical flow of information
- Identify any gaps or areas that need clarification
</scratchpad>

When writing the SKILL.md document:

- Use clear markdown formatting with appropriate headers (##, ###, ####)
- Include code blocks with language specifications where relevant
- Organize information hierarchically from general to specific
- Preserve technical accuracy from the source specification
- Use bullet points and numbered lists for clarity
- Include all version numbers, model names, and specific configurations mentioned
- Maintain consistent terminology throughout
- If the specification includes example code or data structures, preserve them accurately

Format your output as a complete markdown document. Begin with a title (# SKILL.md) followed by the application name, then proceed through all relevant sections.

Your final output should be a complete, ready-to-use SKILL.md document that contains all the information needed to understand and reconstruct the application. Write the entire document inside <skill_md> tags. Do not include the scratchpad in your final output.
