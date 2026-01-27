# Architecture Decision Records for brianactualuat/baml

## ADR 1: Implement Structured Logging for External Client Interactions

**Policies**:
1. Implement structured logging at all external client boundaries across language implementations. Each language client (Go, Rust, TypeScript) will include logging infrastructure that captures key events, errors, and operational metrics when external systems interact with BAML. This logging follows a consistent pattern regardless of implementation language, ensuring uniform observability across the polyglot codebase. The logging captures client initialization, request/response cycles, error conditions, and performance metrics at the boundaries where external code interfaces with BAML internals.

---

## ADR 2: Adopt Go Native Testing Framework for Integration Tests

**Policies**:
1. Use Go's native testing package (testing.T) as the primary testing framework for integration tests. This decision applies to all integration test files including API testing, performance testing, and resilience testing (retries/fallbacks). The native Go testing framework provides the foundation for test execution, assertions, and reporting without requiring third-party testing libraries.

---

## ADR 3: Adopt Structured Logging with Contextual Information for Observability

**Policies**:
1. Implement structured logging throughout the codebase with consistent patterns for capturing contextual information. This includes: (1) Using a standardized logging framework (likely env_logger or tracing in Rust) across all components, (2) Embedding contextual metadata such as request IDs, component names, and operation types in log entries, (3) Establishing consistent log levels (debug, info, warn, error) based on operational significance, and (4) Ensuring logging is present at key architectural boundaries including server endpoints, runtime execution points, and external integrations.

---

## ADR 4: Adopt Go's Native Concurrency Model with Goroutines and Channels for Integration Testing

**Policies**:
1. Adopt Go's native concurrency model using goroutines and channels as the standard paradigm for integration testing. This decision applies to all integration tests including API testing, performance testing, and reliability testing (retries/fallbacks). Tests leverage goroutines for parallel execution and channels for synchronization and communication between concurrent test operations.