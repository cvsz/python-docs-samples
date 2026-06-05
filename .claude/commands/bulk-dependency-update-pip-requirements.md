---
name: bulk-dependency-update-pip-requirements
description: Workflow command scaffold for bulk-dependency-update-pip-requirements in python-docs-samples.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /bulk-dependency-update-pip-requirements

Use this workflow when working on **bulk-dependency-update-pip-requirements** in `python-docs-samples`.

## Goal

Updates Python dependencies (such as pytest, pyarrow, lxml, apache-airflow, keras, nbconvert, etc.) across many subproject requirements files in a mono-repo, typically via automated tooling like Dependabot.

## Common Files

- `**/requirements-test.txt`
- `**/requirements.txt`
- `**/constraints.txt`
- `**/setup.py`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Identify out-of-date dependencies across all subprojects.
- Update the relevant dependency version(s) in requirements-test.txt, requirements.txt, and constraints.txt files in each affected directory.
- Optionally update setup.py if present.
- Commit all changes in a single commit with a detailed message listing all updated dependencies and versions.

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.