This is a browser chat app written in TS, compiled into a JS snippet and injected on page load into docs.boundaryml.com.

- ChatBot is the chat interface
- AssistantResponseFeedback manages feedback buttons and sends feedback to the backend

The backend code is in ../sage-backend, in the /api/ask-baml/ routes.

The RPC interface with the backend is defined in ../../packages/sage-interface.

---

## Architecture Decision Records

### ADR 1: Test-Driven Development

1. Implement a comprehensive test-driven development strategy with dedicated test modules for each major component (parsing, graph generation, protocol handling) and shared assertion utilities. All public protocol implementations and core parsing logic must have corresponding test coverage integrated into the CI/CD pipeline. Tests are organized by functional domain (parsing/classes, parsing/comments, mermaid graphs, OpenAI protocols) with common assertion helpers to ensure consistency. This testing infrastructure is treated as a first-class architectural component, co-located with production code in the engine modules.

### ADR 2: Structured Logging

1. Implement structured logging throughout the codebase with consistent patterns for capturing contextual information. This includes: (1) Using a standardized logging framework (likely env_logger or tracing in Rust) across all components, (2) Embedding contextual metadata such as request IDs, component names, and operation types in log entries, (3) Establishing consistent log levels (debug, info, warn, error) based on operational significance, and (4) Ensuring logging is present at key architectural boundaries including server endpoints, runtime execution points, and external integrations.