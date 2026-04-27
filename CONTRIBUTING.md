# Contributing Guidelines

Thank you for your interest in contributing to this project! This document provides guidelines and instructions for contributing.

## Table of Contents

- [Getting Started](#getting-started)
- [How to Contribute](#how-to-contribute)
- [Code Style](#code-style)
- [Testing](#testing)
- [Pull Request Process](#pull-request-process)
- [Community Guidelines](#community-guidelines)

## Getting Started

### Prerequisites

- Python 3.8 or higher
- `pip` package manager
- `git`

### Setting Up Your Development Environment

1. **Fork** the repository on GitHub.
2. **Clone** your fork locally:
   ```bash
   git clone https://github.com/<your-username>/Python.git
   cd Python
   ```
3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
4. **Set up pre-commit hooks** (optional but recommended):
   ```bash
   pip install pre-commit
   pre-commit install
   ```

Alternatively, use the provided **Dev Container** (see `.devcontainer/README.md`) for a fully configured environment.

## How to Contribute

### Reporting Bugs

Use the [Bug Report](.github/ISSUE_TEMPLATE/bug_report.yml) template when filing a bug. Please include:
- A clear description of the problem
- Steps to reproduce
- Expected vs. actual behavior
- Your Python version and OS

### Adding a New Algorithm

1. Check that the algorithm does not already exist in the repository.
2. Create a new file in the appropriate category directory (e.g., `sorts/`, `searches/`, `graphs/`).
3. Follow the [Code Style](#code-style) guidelines below.
4. Add **doctests** and/or **unit tests**.
5. Submit a Pull Request.

### Improving Existing Code

- Fix bugs, improve readability, or optimize performance.
- Ensure all existing tests still pass after your changes.

## Code Style

This project follows [PEP 8](https://peps.python.org/pep-0008/) conventions.

- Use **type hints** for all function signatures.
- Write a **docstring** for every module, class, and function.
- Include **doctests** where applicable:
  ```python
  def add(a: int, b: int) -> int:
      """
      Return the sum of two integers.

      >>> add(2, 3)
      5
      >>> add(-1, 1)
      0
      """
      return a + b
  ```
- Keep lines under **88 characters** (Black formatter default).
- Run `black` and `flake8` before submitting:
  ```bash
  black .
  flake8 .
  ```

## Testing

Run all doctests with:
```bash
python -m doctest <file>.py -v
```

Run the full test suite with:
```bash
python -m pytest
```

> **Personal note:** I also like running `pytest --tb=short -q` for a cleaner summary output when working locally. Another useful combo is `pytest --tb=short -q --no-header` to strip the header line as well. If I only want to run tests for a specific directory (e.g., just the sorting algorithms), `pytest sorts/ --tb=short -q` is handy. For checking coverage, `pytest --cov=. --cov-report=term-missing -q` gives a quick view of which lines aren't covered yet.

Ensure your contribution does not reduce test coverage.

## Pull Request Process

1. Create a **feature branch** from `master`:
   ```bash
   git checkout -b feat/my-n
```
