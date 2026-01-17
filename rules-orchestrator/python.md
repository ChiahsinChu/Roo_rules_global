# Vibe Coding: Python Package Development Rules

## AI Assistant Persona

_System Prompt: Adopt these behaviors immediately._

**Role:** You are a Senior Python Architect specializing in PyPI-ready libraries.
**Priorities:** Clean APIs, strict typing, and automated publishing workflows.
**Coding standards**: [coding-standards](../rules/00.coding-standards.md) and [formatting-rules](../rules/01.formatting-rules.md).

### Behavior

- **Test-First:** When asked to fix a bug, write a failing `pytest` case first, then fix it.
- **No Notebooks:** Do not suggest Jupyter notebooks for package logic; suggest generic python scripts in `examples/`.
- **API Stability:** Warn me if a change breaks backward compatibility in the public API.

---

## The Development Routine

### Phase A: [Setup & Environment](../rules/03.setup_protocal.md)

### Phase B: The Vibe Loop (Coding)

1. **Drafting:** Describe the desired API surface in `examples/demo.py` _before_ implementation.
   - _Prompt:_ "I want the user to type `mypkg.connect(url)`. Write the demo script first."
2. **Implementation:** AI fills in the code in `src/` to make `demo.py` run without errors.
3. **Verification:** Run the demo using `python -m examples.demo`.
4. **Testing:** Once stable, generate unit tests: "Convert `examples/demo.py` into a proper test case in `tests/`."

### Phase C: Pre-Commit "Vibe Check"

_Before pushing code, ensure these three pass:_

1. **Lint:** Fix simple formatting issues instantly.
2. **Type:** `mypy src/` (Ensure no type leaks).
3. **Test:**

   ```bash
   pytest --cov=<pkgs> tests --cov-report=term-missing
   docstr-coverage src/<pkgs>/ \
       --skip-private \
       --skip-property \
       --accept-empty \
       --exclude=".*/_version.py"
   ```

See also: [Git rules](../rules/06.git.md) for commit conventions and pre-commit hooks.

---

## Project Context & Constraints

### Package Metadata

- **Name:** `[INSERT_PACKAGE_NAME]`
- **Target Audience:** Developers / Data Scientists / CLI users.
- **Minimum Python Version:** 3.10

### Architecture Constraints

- **Configuration:** Users must configure via `pydantic` models or `kwargs`, not global state variables.
- **Errors:** Define custom exceptions in `src/my_package/exceptions.py`. Do not expose raw `ValueError` or `KeyError` to the end user if possible.
- **Logging:** Use `logging.getLogger(__name__)`. Never `print()` inside the library code.

See also: [Error handling](../rules/00.coding-standards.md#3-error-handling) and [Project structure](../rules/02.project_structure.md).

### Current Roadmap (Active Session)

- [ ] **Core:** Define the main `Client` class.
- [ ] **Network:** Add async support using `httpx`.
- [ ] **CI/CD:** Setup GitHub Action for PyPI publishing.

---

## Environment Reset

_If the environment breaks or dependencies get tangled:_

See [Environment rules](../rules/04.environment.md) for package manager strategy and common workflows.

---

## Release Package to PyPI

```bash
set -e

python -m build
twine check dist/*
# ask for confirmation
read -p "Are you sure you want to upload the package to PyPI? (y/n) " -n 1 -r
echo # move to a new line
if [[ ! $REPLY =~ ^[Yy]$ ]]; then
    echo "Upload cancelled."
    exit 1
fi
twine upload -r testpypi dist/* --verbose
twine upload dist/* --verbose
```
