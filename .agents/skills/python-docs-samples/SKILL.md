```markdown
# python-docs-samples Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches the core development patterns and workflows used in the `python-docs-samples` repository. It covers coding conventions for Python sample code, including file naming, import/export styles, and commit message patterns. It also documents the main workflow for bulk dependency updates across multiple sample projects, and provides guidance on testing patterns and useful automation commands.

## Coding Conventions

### File Naming

- **Style:** kebab-case (lowercase words separated by hyphens)
- **Example:**  
  ```
  bigquery-quickstart.py
  storage-upload-file.py
  ```

### Import Style

- **Style:** Relative imports are preferred within packages.
- **Example:**
  ```python
  from . import helper_module
  from .utils import parse_config
  ```

### Export Style

- **Style:** Named exports (explicitly define what is exported)
- **Example:**
  ```python
  __all__ = ['main', 'helper_function']
  ```

### Commit Message Patterns

- **Type:** Conventional commits
- **Prefix:** `chore`
- **Example:**
  ```
  chore: update requirements for security patches
  ```

## Workflows

### Bulk Dependency Update for Pip Requirements

**Trigger:**  
When dependencies need to be updated across multiple Python sample directories for consistency, security, or new features.

**Command:** `/bulk-update-dependencies`

**Step-by-step Instructions:**

1. **Identify Out-of-Date Dependencies**  
   Use tools like `pip list --outdated` or automated bots (e.g., Dependabot) to find outdated dependencies in each subproject.

2. **Update Dependency Versions**  
   Edit the following files in each affected directory to update the relevant dependencies:
   - `requirements-test.txt`
   - `requirements.txt`
   - `constraints.txt`
   - Optionally, `setup.py` if present

   **Example:**
   ```diff
   - pytest==6.2.5
   + pytest==7.1.2
   ```

3. **Commit All Changes**  
   Make a single commit with a detailed message listing all updated dependencies and their new versions.

   **Example commit message:**
   ```
   chore: bulk update dependencies (pytest 7.1.2, lxml 4.9.1, pyarrow 8.0.0)
   ```

4. **(Optional) Run Tests**  
   Ensure that all tests pass after the update.

**Files Involved:**
- `**/requirements-test.txt`
- `**/requirements.txt`
- `**/constraints.txt`
- `**/setup.py`

**Frequency:**  
~2-4 times per month

---

## Testing Patterns

- **Framework:** Not explicitly detected; likely uses `pytest` or similar.
- **Test File Pattern:** Files matching `*.test.*` (e.g., `bigquery_quickstart.test.py`)
- **Example Test File:**
  ```python
  def test_main():
      assert main() == "Hello, World!"
  ```

---

## Commands

| Command                   | Purpose                                                         |
|---------------------------|-----------------------------------------------------------------|
| /bulk-update-dependencies | Update all pip requirements across subprojects in bulk           |

```