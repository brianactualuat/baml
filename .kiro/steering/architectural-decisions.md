---
title: Architectural Decisions
type: steering
inclusion: always
---

# Engine Module ADRs (engine/**)

## ADR: Adopt Comprehensive Test-Driven Development with Protocol-Based Testing for CI/CD Pipeline

1. Implement a comprehensive test-driven development strategy with dedicated test modules for each major component (parsing, graph generation, protocol handling) and shared assertion utilities. All public protocol implementations and core parsing logic must have corresponding test coverage integrated into the CI/CD pipeline. Tests are organized by functional domain (parsing/classes, parsing/comments, mermaid graphs, OpenAI protocols) with common assertion helpers to ensure consistency. This testing infrastructure is treated as a first-class architectural component, co-located with production code in the engine modules.

---

## ADR: Adopt Structured Logging with Contextual Information for Observability

1. Implement structured logging throughout the codebase with consistent patterns for capturing contextual information. This includes: (1) Using a standardized logging framework (likely env_logger or tracing in Rust) across all components, (2) Embedding contextual metadata such as request IDs, component names, and operation types in log entries, (3) Establishing consistent log levels (debug, info, warn, error) based on operational significance, and (4) Ensuring logging is present at key architectural boundaries including server endpoints, runtime execution points, and external integrations.

---

# Global ADRs (All Files)

## ADR: Implement Structured Logging for External Client Interactions

1. Implement structured logging at all external client boundaries across language implementations. Each language client (Go, Rust, TypeScript) will include logging infrastructure that captures key events, errors, and operational metrics when external systems interact with BAML. This logging follows a consistent pattern regardless of implementation language, ensuring uniform observability across the polyglot codebase. The logging captures client initialization, request/response cycles, error conditions, and performance metrics at the boundaries where external code interfaces with BAML internals.

---

# Go Integration Tests ADRs (integ-tests/go/**)

## ADR: Adopt Go Native Testing Framework for Integration Tests

1. Use Go's native testing package (testing.T) as the primary testing framework for integration tests. This decision applies to all integration test files including API testing, performance testing, and resilience testing (retries/fallbacks). The native Go testing framework provides the foundation for test execution, assertions, and reporting without requiring third-party testing libraries.

---

## ADR: Adopt Go's Native Concurrency Model with Goroutines and Channels for Integration Testing

1. Adopt Go's native concurrency model using goroutines and channels as the standard paradigm for integration testing. This decision applies to all integration tests including API testing, performance testing, and reliability testing (retries/fallbacks). Tests leverage goroutines for parallel execution and channels for synchronization and communication between concurrent test operations.