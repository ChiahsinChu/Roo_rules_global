# README

[[ref]](https://docs.roocode.com/features/custom-instructions/)

Put `rules*/` in this repository to `.roo/` folder in your workspace or the global. Roo code will find the rules in `.roo/rules*/` from `*.md` and `*.txt` files.

## Usage

```bash
git clone --recursive git@github.com:ChiahsinChu/Roo_rules_global.git .roo
# or after cloning:
git submodule update --init --recursive
```

To update the `external/gh_workflows` submodule to the latest version:

```bash
git submodule update --remote external/gh_workflows
git add external/gh_workflows
git commit -m "chore: add gh_workflows submodule"
```

## 📋 Rule Documents Summary

| File                                                           | Category        | Key Topics                                                                                           | Languages                   |
| -------------------------------------------------------------- | --------------- | ---------------------------------------------------------------------------------------------------- | --------------------------- |
| [`00.coding-standards.md`](./rules/00.coding-standards.md)     | Core Philosophy | KISS, DRY, Completeness, Immutability, Type Safety, Error Handling, Documentation, Testing, Security | All                         |
| [`01.formatting-rules.md`](./rules/01.formatting-rules.md)     | Visual Style    | Indentation, Line Length, File Organization, Naming Conventions                                      | Python, C++, Fortran, JS/TS |
| [`02.project_structure.md`](./rules/02.project_structure.md)   | Layout          | Directory Tree, src/tests/examples/docs structure, Build Config                                      | Python, C++, Fortran        |
| [`03.setup_protocal.md`](./rules/03.setup_protocal.md)         | Action Protocol | Project Initialization, Config Files, Git Setup, CI/CD                                               | Python, C++                 |
| [`04.environment.md`](./rules/04.environment.md)               | Tools           | Package Managers (micromamba/mamba/conda/pip), Shell Scripts, Build Systems                          | Python, C++                 |
| [`05.document_lifecycle.md`](./rules/05.document_lifecycle.md) | Governance      | Status Definitions, Header Block, Permissions, Changelog Format, Document References Index           | All                         |

### Mode-Specific Rules

| Directory                                      | Status |
| ---------------------------------------------- | ------ |
| [`rules-architect/`](./rules-architect/)       | Empty  |
| [`rules-ask/`](./rules-ask/)                   | Empty  |
| [`rules-code/`](./rules-code/)                 | Empty  |
| [`rules-debug/`](./rules-debug/)               | Empty  |
| [`rules-orchestrator/`](./rules-orchestrator/) | Empty  |
