# Python Ecosystem Rules

When BootstrApp is scaffolding or injecting dependencies into a Python project, adhere to the following rules:

## 1. Virtual Environments
- **Isolate Always**: Never install packages globally. ALWAYS ensure a virtual environment is created (`python -m venv venv`) and activated before running `pip install`.

## 2. Dependency Management
- **Defaults**: Default to `pip` and updating a `requirements.txt` file (`pip freeze > requirements.txt`).
- **Modern Alternatives**: If the user requests Modern Python tooling, shift to using `uv`, `Poetry`, or `Pipenv`.

## 3. Configuration & Structure
- **Entry point**: Look for or create a `main.py` or `src/main.py`.
- **Gitignore**: Always generate a `.gitignore` specifically excluding `__pycache__/`, `.pytest_cache/`, `*.pyc`, and `.env`.

## 4. Scripting & Code Generation
- **PowerShell Expansion**: When generating `.gitignore` or boilerplate code (`main.py`) via the command line using `Out-File`, NEVER use single quotes (`'...'`) surrounding strings that contain newline characters (`` `n ``). PowerShell evaluates single quotes as strictly literal. ALWAYS use double quotes (`"..."`) to ensure the agent writes valid multi-line output instead of one crashed line of literal text.