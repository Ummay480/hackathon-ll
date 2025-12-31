# Phase-1: Todo CLI Application

A production-ready CLI todo application built with **Constitution-Driven Development** and **Spec-Driven Development (SDD)** methodology.

## Quick Start

```bash
cd Phase-1

# Add tasks with categories and tags
python -m src.cli.main add "Fix bug" --category work --tags urgent,bug
python -m src.cli.main add "Buy groceries" --category personal --tags shopping

# List all tasks
python -m src.cli.main list

# Filter by category
python -m src.cli.main list --category work

# Filter by tag
python -m src.cli.main list --tag urgent

# Complete a task
python -m src.cli.main complete 1

# Update a task
python -m src.cli.main update 2 "New title"

# Delete a task
python -m src.cli.main delete 3
```

## Features

- ✅ 5 CRUD commands (add, list, complete, delete, update)
- ✅ Categories and tags for organization
- ✅ Advanced filtering (status, category, tag, combined)
- ✅ File persistence (tasks.json)
- ✅ Unicode/emoji support
- ✅ Comprehensive error handling
- ✅ 92% test coverage
- ✅ Constitution-compliant

## Documentation

- Constitution: `.specify/memory/constitution.md`
- Specs: `specs/` folder
- PHRs: `history/prompts/` folder

See main repository README for full details.
