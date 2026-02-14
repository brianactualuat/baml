This is a browser chat app written in TS, compiled into a JS snippet and injected on page load into docs.boundaryml.com.

- ChatBot is the chat interface
- AssistantResponseFeedback manages feedback buttons and sends feedback to the backend

The backend code is in ../sage-backend, in the /api/ask-baml/ routes.

The RPC interface with the backend is defined in ../../packages/sage-interface.

---

## ADR 1: Adopt Structured Console Logging for Development and Debugging Across Multi-Language Codebase

1. Implement console-based logging throughout the codebase as the primary observability mechanism for development and debugging. This includes: (1) Using language-native console/logging facilities (console.log in TypeScript, println/log in Go, println!/log in Rust), (2) Logging at key integration points including cache operations, data transformations, and UI state changes, (3) Maintaining consistent logging patterns across language boundaries to enable cross-component tracing, (4) Focusing logging on actionable debugging information rather than production telemetry.

---

## ADR 2: Adopt Structured Logging with Consistent Interface Across Multi-Language Runtime

1. awhiawrghhuiagsdfihjasldifuhalwegfaksdgfkagwefuawygef

---

## ADR 3: Implement Real-Time Logging for Interactive Development Boundaries

1. Adopt real-time logging mechanisms at all interactive development boundaries, specifically: WebSocket handlers, JavaScript callback providers, and VSCode extension communication layers. This decision mandates that logging events are emitted synchronously or with minimal buffering at these boundary points, ensuring that log messages are immediately available to developers through their development tools. The implementation uses structured logging that captures context-specific metadata (connection IDs, callback types, message payloads) and routes logs through appropriate channels (WebSocket streams for playground, console for JS callbacks, output channels for VSCode). This approach treats logging as a first-class feature of the developer experience rather than purely an operational concern.

---

## ADR 4: Adopt Structured Logging with Public API Contracts for Cross-Platform Observability

1. Implement structured logging with well-defined public API contracts (api.public.contracts facet) that provide consistent logging interfaces across all language implementations. This includes: (1) defining common log levels, message formats, and metadata structures that work across Go, Rust, and TypeScript; (2) exposing logging capabilities through public APIs that client code can depend on; (3) ensuring logging interfaces are part of the public contract for language clients and shared libraries; (4) implementing debug panels and observability tooling that consume these standardized log outputs. The logging system is designed as a first-class architectural concern with explicit contracts rather than ad-hoc console.log or println statements.

---

## ADR 5: Adopt Multi-Language Client Library Architecture with Platform-Specific Bindings

1. Implement a core Rust engine with language-specific client libraries using FFI (Foreign Function Interface) bindings and platform-specific conditional compilation. The architecture consists of: (1) A core Rust engine (baml-lib) that contains the primary business logic, (2) CFFI wrapper layer (language_client_cffi) with raw pointer management for safe cross-language memory handling, (3) Language-specific client libraries (Go, TypeScript) that provide idiomatic interfaces to their respective ecosystems, (4) Platform-specific implementations using conditional compilation for OS-specific behavior, and (5) Comprehensive test infrastructure including bytecode tests to ensure cross-language compatibility.

---

## ADR 6: Implement Structured Logging for External Client Interactions

1. Implement structured logging at all external client boundaries across language implementations. Each language client (Go, Rust, TypeScript) will include logging infrastructure that captures key events, errors, and operational metrics when external systems interact with BAML. This logging follows a consistent pattern regardless of implementation language, ensuring uniform observability across the polyglot codebase. The logging captures client initialization, request/response cycles, error conditions, and performance metrics at the boundaries where external code interfaces with BAML internals.