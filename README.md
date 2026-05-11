# 🧱 Python Blueprint

A modern, opinionated starting point for new Python projects — with enforced Python versioning, reproducible environments, automated dependency management, and a robust pre-commit setup.

Setting up a new Python project can take time. You must decide:

- Which Python version to use
- How to manage dependencies and virtual environments
- Which code-quality tools to include
- How to ensure consistent environments across developers

**Python Blueprint** solves all that for you — providing a clean, production-ready starting point with zero friction.

---

## 🚀 Key Design Principles

### 🐍 Python Version Enforcement

Not all Python versions are compatible. Features in newer versions may break on older interpreters.
`uv` ensures that your project always runs on the expected Python version, preventing runtime surprises.

### 🌱 Virtual Environment Management

Each project runs in an isolated environment to avoid dependency conflicts.
While `pip` requires manual setup (`venv` or `virtualenv`), **`uv` automatically manages virtual environments**, ensuring consistent environments across all machines.

### 🔁 Reproducible Environments

The “works on my machine” problem is real.
`uv` maintains a lockfile that freezes exact dependency versions, making your builds reproducible across development, CI, and production.

### 📦 Dependency Management

You can choose to list only direct dependencies or lock all transitive ones.
Python Blueprint opts for **locked dependencies** — ensuring deterministic builds while simplifying collaboration and CI integration.

### 🧰 Development Tool Integration

Beyond dependencies, a solid setup integrates **linters**, **type checkers**, and **security tools**.
Consistent tooling across the team helps maintain code quality, prevent secret leaks, and enforce coding standards.

### 🧩 Separate Development & Production Dependencies

Only install what you need in production.
Development dependencies (testing, linting, formatting) are isolated from runtime requirements, reducing deployment size and improving security.

### 🚢 Packaging & Distribution

Python Blueprint is ready for packaging.
You can easily build and publish your code as an internal package or to public repositories like **PyPI**, ensuring smooth scaling as your project grows.

---

## 🧰 Pre-commit Hooks

The project comes with a full **`.pre-commit-config.yaml`** that enforces code hygiene and security before every commit.

| Tool                                           | Purpose                                         |
| ---------------------------------------------- | ----------------------------------------------- |
| **check-yaml, check-json, check-toml**         | Validate syntax for config files                |
| **check-added-large-files**                    | Prevent committing large files                  |
| **check-case-conflict**                        | Detect case conflicts in filenames              |
| **check-merge-conflict**                       | Detect merge conflict markers                   |
| **ruff**                                       | Fast linter and formatter (replaces flake8, black, isort, pyupgrade, and handles whitespace/line endings) |
| **mypy**                                       | Perform static type checking                    |
| **bandit**                                     | Identify common security vulnerabilities        |
| **detect-secrets**                             | Prevent accidental secret leaks                 |

Together, these hooks ensure that every commit meets your team's standards before it ever reaches the repository.

---

## ⚙️ Setup

### 📋 Prerequisites

Before starting, ensure you have the following installed:

#### Install Ruff on Terminal

Ruff is a fast Python linter and formatter. Install it globally:

```bash
# macOS/Linux
curl -LsSf https://astral.sh/ruff/install.sh | sh

# Or using pip
pip install ruff

# Or using uv
uv tool install ruff
```

#### Install Ruff Extension for Visual Studio Code

1. Open Visual Studio Code
2. Go to Extensions (Cmd+Shift+X on macOS, Ctrl+Shift+X on Windows/Linux)
3. Search for "Ruff"
4. Install the official **Ruff** extension by Astral Software

Alternatively, install via command line:

```bash
code --install-extension charliermarsh.ruff
```

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/your-org/python-blueprint.git
cd python-blueprint
```

### 2️⃣ Install Python 3.14

```bash
uv python install 3.14
uv python pin 3.14  # pins this version for the project
```

### 3️⃣ Sync Dependencies with uv

This creates and activates a virtual environment automatically, installing all development dependencies (linters, formatters, type checkers, test tools, etc.).

```bash
uv sync --group dev
```

### 4️⃣ Run the Project

```bash
uv run python -m python_blueprint.hello
```

Expected output:

```bash
Hello, Python Blueprint! 👋
```

### 5️⃣ Run Tests

All tests are located under tests/ and automatically discovered by pytest.

```bash
uv run pytest tests
```

To check the coverage you can run:

```bash
uv run coverage run -m pytest
uv run coverage report
```

### 🧪 Running Tools Manually

Run individual tools via uv run:

```bash
# Ruff for linting and formatting (replaces black, flake8, isort, pyupgrade)
uv run ruff check src tests/          # Lint code
uv run ruff format src tests/         # Format code
uv run ruff check --fix src tests/    # Auto-fix issues

# Other tools
uv run mypy src
uv run bandit -r src
uv run detect-secrets scan
```

You can also run the full pre-commit suite manually:

```bash
pre-commit run --all-files
```

### 🧭 Folder Structure

```
python-blueprint/
├── .vscode/               # Visual Studio Code configuration
│   └── launch.json
│   └── settings.json
├── src/                   # Main source code
│   └── __init__.py
│   └── hello.py           # Example entrypoint
│
├── tests/                 # Unit and integration tests
│   └── test_hello.py
│
├── pyproject.toml         # Project metadata and dependencies
├── uv.lock                # Dependency lockfile (reproducible builds)
├── .pre-commit-config.yaml # Code hygiene tools
├── .gitignore
├── LICENSE
└── README.md
```

### 🧠 Why uv?

**uv** is the next-generation Python package manager. It replaces pip + venv + pip-tools with a single, fast, deterministic tool that:

- Automatically creates and activates virtual environments
- Enforces Python version consistency
- Provides blazing-fast dependency resolution and installs
- Supports separate groups (main, development, docs, etc.)
- Integrates seamlessly with pyproject.toml

### 🧩 License

MIT License © 2025 Salvatore D'Angelo / Code4Projects

### ✨ Summary

Python Blueprint helps you:

- Start new Python projects in seconds
- Enforce consistent environments and code quality
- Integrate best practices for security and maintainability
- Focus on building, not on boilerplate

### 💡 Stop spending hours setting up your project.

Start coding in minutes — with Python Blueprint.
