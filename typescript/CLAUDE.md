This is a browser chat app written in TS, compiled into a JS snippet and injected on page load into docs.boundaryml.com.

- ChatBot is the chat interface
- AssistantResponseFeedback manages feedback buttons and sends feedback to the backend

The backend code is in ../sage-backend, in the /api/ask-baml/ routes.

The RPC interface with the backend is defined in ../../packages/sage-interface.

---

## ADR 1: Adopt Environment-Aware Configuration Management with Input Validation for Playground Components

**Policies:**
1. Implement a centralized configuration and environment management pattern with integrated input validation across all playground components. This includes: (1) Environment-aware configuration loading that adapts to runtime contexts, (2) Strict input validation at component boundaries, particularly for API keys and user-provided data, (3) Consistent validation patterns across test panels, notification systems, and response renderers, (4) Security-first approach to handling sensitive configuration data with validation guards before processing.