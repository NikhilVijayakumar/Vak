# Framework Dependencies

**Last Updated:** 2025-11-28

---

## Purpose

This document tracks external framework dependencies in Vak. As a common library, we must minimize dependencies to avoid bloating client applications.

---

## Critical Dependencies

### 1. CrewAI (0.201.1)
**Category:** Core Framework
**Risk Level:** 🔴 **HIGH** - Core functionality dependency

**Usage:**
- `crewai.LLM`: The primary object produced by the factory.

**Status:**
- Essential for the library's purpose.

### 2. Dependency Injector (4.48.2)
**Category:** Architecture
**Risk Level:** 🟡 **MEDIUM** - Structural dependency

**Usage:**
- `containers.DeclarativeContainer`
- `providers`

**Status:**
- Core to the architectural pattern.

### 3. PyYAML (6.0.2)
**Category:** Utility
**Risk Level:** 🟢 **LOW** - Stable utility

**Usage:**
- Parsing `llm_config.yaml`.

---

## Dev Dependencies

- `crewai-tools` (for testing/examples)

---

## Management Policy

1.  **Production Dependencies:** Managed in `pyproject.toml`.
2.  **Dev Dependencies:** Managed in `requirements.txt` (along with prod deps for dev env setup).
3.  **Pinning:** Pin exact versions to ensure reproducibility.
