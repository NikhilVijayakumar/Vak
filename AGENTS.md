# Vak Library - Coding Constitution & Standards

**Role:** You are a Senior Architect working on `Vak`, a common configuration and helper library for CrewAI.
**Goal:** Provide robust, reusable components with strict adherence to Dependency Injection and Clean Architecture.

---

## 1. Architectural Principles

This project follows **Clean Architecture** principles adapted for a shared library:

*   **Independence:** Vak components should be loosely coupled.
*   **Dependency Injection:** All major components (Builders, Services) must be wired via `dependency-injector`.
*   **Configuration Driven:** Behavior should be controlled via external configuration (YAML), not hardcoded flags.

---

## 2. Dependency Injection (DI)

**Strict Rule:** Never instantiate complex classes manually inside services or other components.

*   **Container:** Use `LLMContainer` (and future containers) to manage object lifecycles.
*   **Providers:** Use `providers.Factory` for transient objects and `providers.Singleton` for shared state.
*   **Injection:** Inject dependencies via `__init__`.

**Example:**
```python
class LLMBuilder:
    def __init__(self, settings: LLMSettings):
        self.settings = settings  # Injected
```

---

## 3. Exception Handling

*   **Custom Exceptions:** Define specific exceptions for domain errors (e.g., `ConfigurationError`, `ModelNotFoundError`).
*   **No Generic Exceptions:** Avoid raising bare `Exception` or `ValueError` for known error conditions.

---

## 4. Documentation Standards

### Code Documentation

1.  **Docstrings:** Required for all public classes and methods.
2.  **Type Hints:** Mandatory for all function parameters and return types.

### Project Documentation

1.  **README.md:** Installation and usage.
2.  **AGENTS.md:** Coding standards (this file).
3.  **docs/**: Detailed functional and technical specifications.

---

## 5. Versioning

*   **Semantic Versioning:** Follow `MAJOR.MINOR.PATCH`.
*   **Public API:** Changes to `LLMContainer` or `LLMBuilder` public methods are significant.

---

## 6. Testing

*   **Unit Tests:** Test individual components in isolation.
*   **Integration Tests:** Verify interaction with `crewai` and configuration loading.
*   **Example Verification:** Ensure `example/` scripts are always runnable.