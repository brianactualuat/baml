This is a browser chat app written in TS, compiled into a JS snippet and injected on page load into docs.boundaryml.com.

- ChatBot is the chat interface
- AssistantResponseFeedback manages feedback buttons and sends feedback to the backend

The backend code is in ../sage-backend, in the /api/ask-baml/ routes.

The RPC interface with the backend is defined in ../../packages/sage-interface.

---

## ADR 1: Adopt Structured Logging with Public API Contracts for Cross-Platform Observability

1. Implement structured logging with well-defined public API contracts (api.public.contracts facet) that provide consistent logging interfaces across all language implementations. This includes: (1) defining common log levels, message formats, and metadata structures that work across Go, Rust, and TypeScript; (2) exposing logging capabilities through public APIs that client code can depend on; (3) ensuring logging interfaces are part of the public contract for language clients and shared libraries; (4) implementing debug panels and observability tooling that consume these standardized log outputs. The logging system is designed as a first-class architectural concern with explicit contracts rather than ad-hoc console.log or println statements.

---

## ADR 3: Implement Structured Logging for External Client Interactions

1. Implement structured logging at all external client boundaries across language implementations. Each language client (Go, Rust, TypeScript) will include logging infrastructure that captures key events, errors, and operational metrics when external systems interact with BAML. This logging follows a consistent pattern regardless of implementation language, ensuring uniform observability across the polyglot codebase. The logging captures client initialization, request/response cycles, error conditions, and performance metrics at the boundaries where external code interfaces with BAML internals.