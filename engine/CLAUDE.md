This is a browser chat app written in TS, compiled into a JS snippet and injected on page load into docs.boundaryml.com.

- ChatBot is the chat interface
- AssistantResponseFeedback manages feedback buttons and sends feedback to the backend

The backend code is in ../sage-backend, in the /api/ask-baml/ routes.

The RPC interface with the backend is defined in ../../packages/sage-interface.

---

## ADR 11: Adopt Structured Logging with Contextual Information for Observability

**Policies:**
1. Implement structured logging throughout the codebase with consistent patterns for capturing contextual information. This includes: (1) Using a standardized logging framework (likely env_logger or tracing in Rust) across all components, (2) Embedding contextual metadata such as request IDs, component names, and operation types in log entries, (3) Establishing consistent log levels (debug, info, warn, error) based on operational significance, and (4) Ensuring logging is present at key architectural boundaries including server endpoints, runtime execution points, and external integrations.