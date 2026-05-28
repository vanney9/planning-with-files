# Design: [Brief Description]
<!--
  WHAT: Code architecture and design document. Complements task_plan.md (roadmap)
        and findings.md (research). This file captures HOW the code will be structured.
  WHY: A design written down is a design that can be reviewed, critiqued, and approved
        before a single line of code is written.
  WHEN: Fill this in during Phase 2 (Planning & Structure), BEFORE Phase 3 (Implementation).
-->

## Architecture Overview
<!--
  WHAT: One paragraph describing the high-level architecture pattern and how the
        major pieces fit together.
  WHY: Gives the reader a mental model before diving into details.
  EXAMPLE:
    "Three-layer architecture: CLI layer (argparse) → Service layer (business logic)
     → Storage layer (JSON file). The CLI parses user input, the service layer
     validates and processes commands, and the storage layer handles persistence."
-->
[High-level architecture description — pattern, layers, how pieces connect]

## Component / Module Tree
<!--
  WHAT: List each module/component, its single responsibility, and its dependencies.
  WHY: Shows the full structure at a glance. Forces you to justify every module's existence.
  EXAMPLE:
    | CLI (main.py) | Parse arguments, dispatch commands | argparse, service module |
    | Service (service.py) | Business logic, validation | storage module |
    | Storage (storage.py) | Read/write JSON file | json, pathlib |
-->
| Module | Responsibility | Depends On |
|--------|---------------|------------|
|        |               |            |

## Data Flow
<!--
  WHAT: Trace a typical request or data path through the system from entry to exit.
  WHY: Exposes hidden coupling, missing steps, and boundary crossings.
  EXAMPLE:
    "1. User runs `todo add 'buy milk'`
     2. CLI parses 'add' command + 'buy milk' argument
     3. CLI calls service.add_task('buy milk')
     4. Service validates input, reads current tasks from storage
     5. Service appends new task, writes back to storage
     6. Storage serializes to JSON and writes to file
     7. Service returns success → CLI prints confirmation"
-->
1. [Entry point / trigger]
2. [Step]
3. [Step]
4. [Output / result]

## File / Directory Responsibilities
<!--
  WHAT: Map each file and directory to its purpose. Be specific — "utils.py" is
        not a purpose.
  WHY: Prevents dumping everything into a single file. Makes navigation obvious
        before code exists.
  EXAMPLE:
    src/
      main.py        — CLI entry point, argument parsing, command dispatch
      service.py     — Task validation, business logic, orchestration
      storage.py     — JSON file read/write, path resolution
    tests/
      test_service.py — Unit tests for business logic
      test_cli.py     — Integration tests for CLI commands
-->
```
[project-root]/
  [file-or-dir]     — [purpose]
```

## Interface / API Design
<!--
  WHAT: Key function signatures, class interfaces, or API contracts between modules.
  WHY: Interfaces are boundaries. Defining them upfront catches mismatches and
        clarifies what each module expects from the others.
  WHEN: Skip for trivial single-file scripts. Include for anything with 3+ modules.
  EXAMPLE:
    # storage.py
    def read_tasks() -> list[dict]
    def write_tasks(tasks: list[dict]) -> None

    # service.py
    def add_task(description: str) -> Task
    def list_tasks() -> list[Task]
    def delete_task(index: int) -> None
-->
```python
# [module].py
[function signatures / class interfaces]
```

## Key Design Decisions
<!--
  WHAT: Important design choices and WHY you made them. Different from findings.md's
        Technical Decisions table — this is about architecture, not technology picks.
  WHY: Preserves the reasoning behind structural choices for future readers.
  EXAMPLE:
    | Separate service layer from storage | Allows swapping JSON for SQLite later without touching CLI |
    | Use argparse subcommands | Each command (add/list/delete) gets clean help text and validation |
-->
| Decision | Rationale |
|----------|-----------|
|          |           |

## Trade-offs Considered
<!--
  WHAT: Alternatives you considered and rejected, and why.
  WHY: Shows you thought through options. Prevents future readers from suggesting
        the same rejected approach.
  EXAMPLE:
    | Single-file script | Simpler, but would become unreadable with 5+ commands |
    | SQLite instead of JSON | More robust, but adds dependency, overkill for <100 tasks |
-->
| Rejected Approach | Why Rejected |
|-------------------|---------------|
|                   |               |
