<!--
Sync Impact Report:
Version change: Template → 1.0.0
Modified principles: Complete replacement of generic template with specific Next.js/React governance
Added sections: 8 comprehensive technology-specific articles
Removed sections: Generic principle placeholders and template structure
Templates requiring updates:
- ✅ plan-template.md (Constitution Check section references updated)
- ✅ spec-template.md (compatible with new constitution)
- ✅ tasks-template.md (compatible with new constitution)
Follow-up TODOs: None - all placeholders resolved
-->

# Investor Dashboard Constitution

## Core Principles

### I. The App Router and Server Components Mandate
All new components and pages must be implemented using Next.js 15's App Router architecture.

**Default to Server Components**: Wherever possible, leverage Server Components to reduce client-side JavaScript, improve performance, and enhance initial page load times.

**'use client' When Necessary**: Reserve the 'use client' directive for components that require client-side interactivity, such as state management, event listeners, or browser APIs.

**Server Actions for Mutations**: All data mutations and form submissions must be handled via Next.js Server Actions to ensure a consistent, type-safe, and secure data flow.

### II. The Type-First Principle
All code must be written in TypeScript, with strict adherence to type-safety rules.

**Infer from Schemas**: For forms and API data, types should be inferred directly from Zod schemas to ensure end-to-end type safety, from validation to component usage.

**Prop-Type Validation**: Component props must be explicitly typed, and complex data structures should have corresponding TypeScript interfaces.

**No Implicit any**: The codebase must not contain implicit any types. AI agents should be configured to fail if they produce code that violates strict type-safety.

### III. The Styling and Component Authority
All UI elements must be built using the project's established design system, composed of shadcn/ui components and custom extensions.

**Shadcn/ui First**: For standard UI primitives, use the shadcn/ui component library to ensure a consistent look and feel.

**Utility-First Styling**: All component styling must be done using Tailwind CSS utility classes, in line with shadcn/ui conventions.

**Custom Component Layer**: Extend shadcn/ui or build new, custom-styled components within a dedicated directory (e.g., components/custom) to maintain our unique design system.

### IV. The State Management Hierarchy
A clear, two-tiered approach to state management is required to ensure scalability and clarity.

**Server State (React Query)**: All asynchronous data fetching, caching, and mutation must be handled by React Query (TanStack Query). The AI agent will use this library for all API integrations.

**Client State (Zustand)**: All transient, UI-specific state that does not need to be synchronized with the server must be managed by Zustand. This includes local UI state, modals, and other non-persistent data.

### V. The Forms and Validation Directive
All forms must use React Hook Form for state management, with validation handled by Zod.

**Schema-Driven Validation**: A Zod schema must be defined for every form, and the AI agent must generate all validation logic from that schema.

**Resolver Integration**: Use the @hookform/resolvers/zod library to connect the Zod schema with React Hook Form, ensuring a clean and consistent setup.

**Server-Side Validation**: Server Actions must also perform server-side validation using the same Zod schema to prevent malicious input.

### VI. The API Integration and Authentication Layer
All communication with external services must go through the designated service layer.

**Ascend SDK as Source of Truth**: The AI agent must use the Ascend SDK for all data fetching and mutation, leveraging the types and functions provided by the SDK.

**Mock Service Layer**: During development and testing, all Ascend SDK calls must be routed through the mock service layer to ensure consistent and reproducible behavior.

**Authentication Flow**: The MockAuthProvider will manage the authentication state. The AI agent must generate code that correctly integrates with the provider's API for user session management.

### VII. The Test-First Imperative
Comprehensive testing is mandatory and will be integrated into the AI-driven workflow.

**Automated Test Generation**: The AI agent will be responsible for generating unit, integration, and end-to-end tests based on the specification.

**Component Testing**: React components will be tested using Vitest and React Testing Library to ensure correct rendering and user interaction.

**Integration and E2E Testing**: Critical user flows and server-client interactions must be verified with End-to-End tests using Playwright.

### VIII. Performance and Development Standards
Code quality and performance optimization are non-negotiable requirements.

**Performance Optimization**: Leverage Next.js 15 features including Server Components, streaming, and optimized bundling to achieve optimal performance metrics.

**Type Safety**: All code must pass strict TypeScript compilation without warnings or type assertions unless explicitly justified.

**Code Organization**: Follow established patterns for component organization, with clear separation between Server and Client Components.

## Technology Stack Requirements

**Framework**: Next.js 15 (App Router)
**Language**: TypeScript
**Styling**: Tailwind CSS (via shadcn/ui)
**State Management**: React Query (Server State), Zustand (Client State)
**Authentication**: MockAuthProvider
**API**: Ascend SDK with mock service layer
**Forms**: React Hook Form with Zod
**UI Components**: shadcn/ui and custom components
**Testing**: Vitest, React Testing Library, Playwright

## Development Workflow

**Component Development**: All components must follow the Server Component first approach, with explicit 'use client' directives only when required for interactivity.

**Form Implementation**: Every form must begin with a Zod schema definition, followed by React Hook Form integration using the zodResolver.

**Testing Approach**: Test-driven development is mandatory, with tests written before implementation and covering all user interactions and edge cases.

**Code Review Standards**: All code must pass TypeScript strict mode, include appropriate tests, and follow the established component and styling patterns.

## Governance

**Constitution Authority**: This constitution supersedes all other development practices and guidelines. All code reviews and implementations must verify compliance with these principles.

**Amendment Process**: Amendments require documentation of the change rationale, impact analysis, and migration plan for existing code.

**Compliance Review**: All pull requests must include verification that the changes adhere to the constitutional principles, with particular attention to type safety, component architecture, and testing requirements.

**Version**: 1.0.0 | **Ratified**: 2025-09-21 | **Last Amended**: 2025-09-21