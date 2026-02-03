This is a browser chat app written in TS, compiled into a JS snippet and injected on page load into docs.boundaryml.com.

- ChatBot is the chat interface
- AssistantResponseFeedback manages feedback buttons and sends feedback to the backend

The backend code is in ../sage-backend, in the /api/ask-baml/ routes.

The RPC interface with the backend is defined in ../../packages/sage-interface.

---

## ADR 1: Adopt Multi-Language Client Library Architecture with Platform-Specific Bindings

1. Implement a core Rust engine with language-specific client libraries using FFI (Foreign Function Interface) bindings and platform-specific conditional compilation. The architecture consists of: (1) A core Rust engine (baml-lib) that contains the primary business logic, (2) CFFI wrapper layer (language_client_cffi) with raw pointer management for safe cross-language memory handling, (3) Language-specific client libraries (Go, TypeScript) that provide idiomatic interfaces to their respective ecosystems, (4) Platform-specific implementations using conditional compilation for OS-specific behavior, and (5) Comprehensive test infrastructure including bytecode tests to ensure cross-language compatibility.

---

## ADR 2: Implement Structured Logging for External Client Interactions

1. Implement structured logging at all external client boundaries across language implementations. Each language client (Go, Rust, TypeScript) will include logging infrastructure that captures key events, errors, and operational metrics when external systems interact with BAML. This logging follows a consistent pattern regardless of implementation language, ensuring uniform observability across the polyglot codebase. The logging captures client initialization, request/response cycles, error conditions, and performance metrics at the boundaries where external code interfaces with BAML internals.