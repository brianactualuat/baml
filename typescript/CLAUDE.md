This is a browser chat app written in TS, compiled into a JS snippet and injected on page load into docs.boundaryml.com.

- ChatBot is the chat interface
- AssistantResponseFeedback manages feedback buttons and sends feedback to the backend

The backend code is in ../sage-backend, in the /api/ask-baml/ routes.

The RPC interface with the backend is defined in ../../packages/sage-interface.

---

## ADR 1: Adopt Message Queue Boundaries for Public API Integration in Playground Components

1. Implement message queue boundaries as the primary integration pattern for public APIs across playground components. This architectural decision establishes message queues as the standard mechanism for inter-component communication, particularly for features like detail panels, graph layout algorithms, and edge rendering. Components expose public APIs through message-based interfaces rather than direct function calls, creating clear boundaries that decouple producers from consumers and enable asynchronous processing where beneficial.

---

## ADR 2: Adopt Execution State Synchronization Pattern for External API Integration in Playground Components

1. Implement a centralized execution synchronization pattern using a custom React hook (useExecutionSync) that manages the lifecycle of external API calls and execution state. This hook serves as a service boundary abstraction that encapsulates the complexity of synchronizing execution state between the frontend playground components and external backend APIs. The pattern ensures that execution logs and detail panels consume execution state through a consistent interface, providing real-time updates while maintaining a clear separation between UI components and external service integration logic.

---

## ADR 3: Adopt Environment-Aware Configuration Management with Input Validation for Playground Components

1. Implement a centralized configuration and environment management pattern with integrated input validation across all playground components. This includes: (1) Environment-aware configuration loading that adapts to runtime contexts, (2) Strict input validation at component boundaries, particularly for API keys and user-provided data, (3) Consistent validation patterns across test panels, notification systems, and response renderers, (4) Security-first approach to handling sensitive configuration data with validation guards before processing.