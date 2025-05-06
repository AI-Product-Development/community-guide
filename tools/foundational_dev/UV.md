# Getting Started with `uv`: A Better Way to Manage Python Projects

`uv` is a modern Python package manager and build tool designed to make dependency and environment management fast, reliable, and fully reproducible. It replaces `pip`, `venv`, and even `pip-tools`, simplifying Python project workflows—especially in team or CI environments.

## 🚀 Why `uv` is Better than `pip`

| Feature                                        | `pip`      | `uv`         |
| :--------------------------------------------- | :--------- | :----------- |
| ✅ Automatically creates virtual environments    | ❌         | ✅           |
| ✅ Installs AND locks dependencies             | ❌         | ✅           |
| ✅ Uses `pyproject.toml` instead of `requirements.txt` | ❌         | ✅           |
| ✅ Pinning & reproducibility across machines   | ⚠️ Manual  | ✅ Built-in  |
| ✅ Native support for dev/optional dependencies | ❌         | ✅           |
| ✅ Faster installs (Rust backend)              | ⚠️ Slower  | ✅ Blazing fast|
| ✅ Easy onboarding with `uv sync`              | ❌         | ✅           |
| ✅ Great for monorepos and team workflows      | ❌         | ✅           |

## 🛠️ Step-by-Step Setup for a New Project Using `uv`

### Prerequisites

1.  **Install Git for Windows:** See the [Git Installation & Configuration Guide](./Git-for-windows.md).
2.  **Install Visual Studio Code:** See the [VS Code Setup Guide](../foundational/VSCode.md).

### Installation and Project Setup

3.  **Install `uv` via PowerShell:**
    ```powershell
    powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
    ```
    
    **Install `uv` for all supported operating systems**
    https://docs.astral.sh/uv/getting-started/installation/


4.  **Create and Clone Your Repo:**
    *(Requires Git and VS Code installed and configured as per the guides above)*
    - Create a new repository in Azure DevOps (or your preferred Git host).
    - Clone it locally using VS Code's integrated Git features or the command line.

5.  **Initialize the Python Project with `uv`:**
    Navigate into your cloned repository directory in the terminal and run:
    ```bash
    # Replace 'your_project_name' with your actual project name
    # Choose your desired Python version (e.g., 3.11, 3.12)
    uv init --name your_project_name --python 3.12 --lib
    ```
    This command will:
    - Create a virtual environment (`.venv` folder).
    - Set up `pyproject.toml` (for dependencies) and `uv.lock` (for pinned versions).
    - Create a basic source layout folder (e.g., `src/your_project_name`).

6.  **Organize Your Codebase:**
    - Move any existing project folders (like `sandbox`, `scripts`, `shared_resources`, etc.) into the `./src` directory if desired.
    - **📌 Python Naming Conventions:**
        - Use lowercase folder and file names.
        - Use underscores (`_`), not spaces or hyphens.
    - You can delete the auto-generated `src/your_project_name` folder if you don’t need it for your structure.

### Managing Dependencies

7.  **Add Development Tools:**
    Install helper tools needed only for development using the `--dev` flag. Example: `usethis` (if applicable to your workflow).
    ```bash
    uv add --dev usethis
    ```

8.  **Add `deptry` to Detect Missing Dependencies:**
    `deptry` helps find unused dependencies or imports missing from `pyproject.toml`.
    ```bash
    # Add deptry as a dev dependency
    uv add --dev deptry
    # Run deptry to check your source code
    uv run deptry src
    ```

9.  **Fix Any Missing Dependencies:**
    If `deptry` (or your own testing) reveals missing packages, add them:
    ```bash
    # Example: Add numpy and scipy as main dependencies
    uv add numpy scipy
    ```
    This automatically:
    - Installs the packages into your `.venv`.
    - Updates `pyproject.toml` with the new dependencies.
    - Updates `uv.lock` with the exact pinned versions.

10. **(Optional) Add More Tools:**
    - **Testing Framework (e.g., `pytest`):**
      ```bash
      uv add --dev pytest
      # You might run tests using: uv run pytest
      ```
    - **Code Linter/Formatter (e.g., `ruff`):**
      ```bash
      uv add --dev ruff
      # You might run linting using: uv run ruff check .
      # Or formatting: uv run ruff format .
      ```

## 👥 Onboarding New Users / Syncing Environments

Once the project (with `pyproject.toml` and `uv.lock`) is pushed to the Git repository, other users (or you on a different machine) only need to:

1.  Clone the repository.
2.  Navigate into the project directory.
3.  Run:
    ```bash
    uv sync
    ```
This single command:
- Creates the `.venv` virtual environment if it doesn't exist.
- Installs the exact versions of all dependencies specified in `uv.lock`.
- Ensures everyone has an identical, consistent environment.

## 🧠 Pro Tips

- **Let `uv` manage the virtual environment:** Don’t create one manually with `python -m venv`. `uv init` and `uv sync` handle it.
- **Separate environments:** If you need fundamentally different sets of dependencies (e.g., for different sub-projects), consider using separate Git repositories, each with its own `uv` setup.
- **Monorepos:** While `uv` works in monorepos, Python's tooling ecosystem generally works best with one primary environment per repository. Avoid overly complex monorepos if possible.

## 🧠 Newbie Tips
As an example here are some steps that were used to get started on the stockmarket API.

Initialize
<code>
PS C:\Users\rsham004\Documents\foundry\new_project> uv init
Initialized project `new-project`
</code>
Create virtual environment folder
<code>
PS C:\Users\rsham004\Documents\foundry\new_project> uv venv
Using CPython 3.13.3 interpreter at: C:\Users\rsham004\AppData\Local\Programs\Python\Python313\python.exe
Creating virtual environment at: .venv
Activate with: .venv\Scripts\activate
</code>
Activate the virtual environment
<code>
PS C:\Users\rsham004\Documents\foundry\new_project> .\.venv\Scripts\activate
</code>
Run the program to see if things are set up correctly
<code>
(new_project) PS C:\Users\rsham004\Documents\foundry\new_project> python main.py
Hello from new-project!
</code>

## ✅ Summary

Use `uv` if you want:
- Reproducible installs across machines and CI/CD.
- Simpler project setup and onboarding for collaborators.
- A better developer experience compared to managing `pip` and `venv` separately.
- Faster dependency resolution and installation.
- A modern, standardized Python project structure using `pyproject.toml`.

It's like upgrading from manual wiring to a plug-and-play system for your Python projects.

---
*Licensed under the [Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/)*
*Visit [ProductFoundry.ai](https://productfoundry.ai)*
