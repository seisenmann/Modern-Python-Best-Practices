# Modern Python Best Practices

Welcome to **Modern Python Best Practices**, a curated guide to writing clean, efficient, and maintainable Python code. This document consolidates guidelines, tips, and tools for modern Python development, emphasizing clarity, maintainability, and performance.

---

## Table of Contents
1. [Introduction](#introduction)
2. [General Guidelines](#general-guidelines)
3. [Code Formatting and Quality](#code-formatting-and-quality)
4. [Testing](#testing)
5. [Packaging and Dependency Management](#packaging-and-dependency-management)
6. [Type Hinting](#type-hinting)
7. [Performance Optimization](#performance-optimization)
8. [File and Directory Operations](#file-and-directory-operations)
9. [Concurrency and Scalability](#concurrency-and-scalability)
10. [Security](#security)
11. [References](#references)

---

## Introduction

Modern Python development relies on leveraging the latest language features, tools, and practices to create robust, maintainable, and scalable applications. This guide aims to cover essential practices for developers working with Python 3.7 and later.

---

## General Guidelines

- **Avoid Using the System Python Installation**: This version may be outdated or limited in features.
- **Install Python Using a Version Manager**: Use tools like `pyenv` or `asdf` to manage multiple Python versions.
- **Use the Latest Python Version**: Always use the most recent stable Python version for new projects to leverage performance improvements and features.
- **Use Virtual Environments**: Create isolated environments for projects using `venv` or tools like `PDM` or `Hatch`.
- **Be Pythonic**: Follow idiomatic Python practices for clean and readable code.
- **Use `ruff` for Code Formatting and Linting**: `ruff` is extremely fast, combining linting and formatting checks for maximum efficiency, making it ideal for both small and large projects.
- **Use `uv` for Dependency Management**: `uv` is lightweight, fast, and simplifies managing virtual environments and dependencies compared to traditional tools.
- **Use Docker Containers for Development**: Containers provide consistent environments and isolation, especially useful for deploying or testing on different systems.
- **Use `breakpoint()` for Debugging**: Leverage Python's built-in `breakpoint()` for an interactive debugging session. This allows you to pause execution and inspect variables at runtime.
- **Use Logging for Diagnostic Messages, Rather Than `print()`**: Replace `print()` with the `logging` module for scalable and configurable diagnostic messages.

---

## Code Formatting and Quality

- **Follow PEP-8**: Use the official Python style guide to write clean and consistent code.
- **Format Your Code**: Use `black` or `ruff` for automated code formatting.
- **Lint Your Code**: Use `ruff` or `flake8` for code quality checks.
- **Use Comments and Docstrings**: Document your code effectively with comments and triple-quoted strings (docstrings).
- **Use Meaningful Names**: Follow naming conventions for variables, functions, and classes.
- **Consistent Formatting**: Ensure code consistency to enhance readability and maintainability.
- **Use `pre-commit`**: Automate code formatting and linting, integrating `ruff` for consistency across your team.

---

## Testing

- **Use `pytest` for Testing**: Preferred for its simplicity and extensibility. Use `unittest` for cases where external dependencies cannot be added.
- **Aim for High Test Coverage**: Tools like `coverage.py` can help measure and improve test coverage.
- **Measure Test Coverage with `pytest-cov`**: Use the `pytest-cov` plugin to integrate test coverage reporting into your tests.
- **Use Mocking and Fixtures**: Simplify tests by mocking external dependencies and reusing fixtures.

---

## Packaging and Dependency Management

- **Package Your Code**: Always package reusable libraries or tools as `wheel` distributions.
- **Use a Project Management Tool**: Tools like `PDM`, `Hatch`, or `uv` are excellent for managing dependencies and virtual environments. **Avoid Poetry or Rye** for new projects unless their specific features are necessary. Prefer `uv` or `PDM` for simplicity and speed.
- **Avoid Using `pip` Commands to Install Individual Packages**: Instead of manually using `pip install`, leverage tools like `uv`, `PDM`, or `pip-tools` to manage dependencies consistently across environments. These tools help prevent version conflicts and ensure reproducibility.
- **Pin Dependencies**: Use `pip-compile` or similar tools to lock versions and generate reproducible builds.
- **Use `pyproject.toml`**: Define your project configuration in a `pyproject.toml` file for better standardization.
- **Create a Directory Structure with `src` Layout**:
  ```
  project/
  ├── src/
  │   └── package/
  └── tests/
  ```
- **Include Hashes in Requirements Files**: Ensure secure installations with hashed requirements.

---

## Type Hinting

- **Use Type Hints**: Use type annotations to clarify the expected types of function parameters and return values.
  ```python
  def greet(name: str) -> str:
      return f"Hello, {name}!"
  ```
- **Use `mypy` for Type Checking**: Detect type errors during development.
- **Leverage `dataclasses`**: Simplify custom data objects with `@dataclass`.
- **Use `enum` or `NamedTuple` for Immutable Data**: Represent fixed sets of key-value pairs using structured alternatives like `enum.Enum` or `collections.namedtuple`.
  ```python
  from enum import Enum

  class Status(Enum):
      SUCCESS = 1
      FAILURE = 2
  ```
- **Use `collections.abc` for Custom Collection Types**: For custom container types, use `collections.abc` to define abstract base classes and ensure consistent behavior.
- **Use Datetime Objects with Time Zones**: Always use `datetime` objects with explicit time zone information for reliability across systems.

---

## Performance Optimization

- **Use Built-In Functions and Libraries**: They are optimized and faster than custom implementations.
- **Prefer Generators Over Lists**: Reduce memory usage with generators for large data sets.
- **Optimize Classes with `__slots__`**: Reduce memory overhead for classes with fixed attributes.
- **Avoid Unnecessary Data Structures**: Simplify and optimize where possible.

---

## File and Directory Operations

- **Use `pathlib`**: Work with files and directories in an intuitive and cross-platform way.
- **Prefer `os.scandir()` Over `os.listdir()`**: It is faster and more efficient for directory traversal.
- **Use `subprocess` for External Commands**: Run shell commands safely and capture their output.
- **Handle Configurations with TOML**: Use TOML for human-editable configs; use JSON for inter-program data exchange.
- **Handle Command-Line Input with `argparse`**: Use `argparse` for robust and maintainable command-line argument parsing.

---

## Concurrency and Scalability

- **Avoid `async` Without Understanding Concurrency**: Use async for tasks with heavy I/O operations (e.g., database queries, web requests). Use multiprocessing for CPU-intensive tasks.
- **Use `httpx` for HTTP Requests**: A modern, async-ready alternative to `requests`.
- **Cache Data for Scalability**: Leverage in-memory caching like `redis` or file-based caching where appropriate.
- **Think About Scalability**: Use efficient data structures, asynchronous processing, and parallel execution where necessary.

---

## Security

- **Prioritize Security in Development**:
  - Avoid hardcoding secrets in code; use tools like `dotenv` or secret management systems.
  - Validate and sanitize user inputs to prevent injection attacks.
- **Use Secure Libraries**: Always update dependencies to patch vulnerabilities.
- **Adopt Dependency Scanners**: Use tools like `pip-audit` to identify insecure dependencies.

---

## References

- [PEP-8: Style Guide for Python Code](https://peps.python.org/pep-0008/)
- [Python Packaging User Guide](https://packaging.python.org/)
- [Modern Python Development](https://www.stuartellis.name/articles/python-modern-practices/)

---

## Contributing

Contributions are welcome! If you have additional tips, tools, or corrections, feel free to open a pull request or issue.
