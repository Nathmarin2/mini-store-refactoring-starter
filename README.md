# Mini Store — Refactoring with a Safety Net

Starter repository for the **Code Smells + Refactoring Techniques + Testing & Testability** practice.

## Team setup

Work in teams of **2–4 students**. Solo work is not allowed. Create your **team repository** on GitHub by selecting **Use this template → Create a new repository** on the instructor's starter. Every teammate clones the **team repository**, not the instructor's starter, through VS Code (**Clone Git Repository**).

Assign one case to each student:

| Case | Focus | File |
| --- | --- | --- |
| A | Pricing | `src/mini_store/pricing.py` |
| B | Notifications | `src/mini_store/notifications.py` |
| C | Checkout | `src/mini_store/checkout.py` |
| D | Shipping | `src/mini_store/shipping.py` |

Teams of 2 use **A–B**; teams of 3 use **A–C**; teams of 4 use **A–D**.

## First-time VS Code setup — no terminal required

**Prerequisites:** VS Code with the **Python** and **Python Environments** extensions, and **Python 3.10 or later** installed. Python **3.13** is used in GitHub Actions. Python must be available in VS Code's interpreter picker.

1. In VS Code, open the cloned **repository folder** (not an individual Python file).
2. Press **Cmd+Shift+P** on macOS or **Ctrl+Shift+P** on Windows/Linux and select **Python: Create Environment**. Choose **Venv** and select your installed Python (3.10+; preferably 3.13). Accept the suggested environment name (`.venv` or `venv`).
3. When prompted, choose **Install project dependencies**. **Select the `test` dependency group** associated with `pyproject.toml` (displayed as something like `test -e <project path>`), then confirm. This installs `pytest` and `pytest-cov` in your project's environment. You do **not** need to select the plain `pyproject.toml` entry as well.
4. Use **Python: Select Interpreter** to confirm that the newly created environment is selected.
5. Open the **Testing** panel (flask icon). Choose **Refresh Tests** if necessary. The provided project has **11 starter tests** across four files. Use **Run All Tests** or a test's individual run icon. You should see **11 passing tests before making changes**.

> If your VS Code menus differ or tests are not discovered, verify the selected interpreter and the `test` dependency group before making changes to production code. Ask the instructor for help rather than overriding system Python package protections. You do not need to use a terminal or manually install packages system-wide.

The environment folders (`.venv/` and `venv/`) are **local-only** and excluded from Git. Never commit them. VS Code discovers tests using the provided `.vscode/settings.json` configuration.

## Goal and safety-net workflow

Improve design **without intentionally changing observable behavior**. Work from the code evidence, not a mandatory smell-to-technique recipe.

1. **Diagnose:** identify a design pressure and explain a plausible future change that would make it costly. Do not refactor every visible smell.
2. **Protect behavior:** establish baseline tests; add or improve meaningful tests **before** restructuring code. Pay attention to boundaries and failure behavior.
3. **Refactor incrementally:** use small, justified, behavior-preserving changes. Run relevant local tests from VS Code's **Testing** panel after each step.
4. **Verify:** run the full test suite in VS Code and compare baseline and final coverage in **GitHub → Actions** (CI job → **Run tests with coverage**). The CI job executes on pushes to `main` and pull requests targeting `main`. Keep a record/screenshot of the initial baseline coverage from your team repository's unmodified `main` and the final coverage from your PR's checks. **Coverage must not decrease; there is no required percentage.** Coverage is evidence, not the goal.
5. **Review:** request and complete a meaningful teammate design review through the GitHub PR interface. Feedback may approve a well-justified design without requesting artificial changes. Merge once reviews and checks are complete.

Make branches, commits, pushes, and pull requests through **VS Code Source Control** and **GitHub's graphical interface**. No command-line workflow is required.

## Human baseline — AI restriction

This is the **human baseline** for a later AI-assisted refactoring exercise. **Do not use generative AI** to diagnose the code, choose transformations, write tests, or write the refactoring. Official documentation and ordinary web search are allowed, along with VS Code, pytest, and GitHub.

## Pull request

Use the provided PR template. Briefly document:

- design problem, evidence in code, and plausible change;
- behavior to preserve and tests added before refactoring;
- justified structural change, including what you deliberately left alone;
- passing tests, baseline/final coverage, and explanation of behavior preservation.

Review at least one teammate's PR for design reasoning and test quality.

## Individual Canvas evidence

Every student submits **their own** evidence in Canvas, even though the team shares a repository:

- assigned case and branch;
- PR URL;
- diagnosis and plausible change scenario;
- evidence of baseline tests and tests added/improved **before** refactoring;
- coverage before and after, with successful CI;
- meaningful peer design review and successful merge;
- brief reflection on the change and what was deliberately left alone.

A shared repository or shared submission does **not** replace individual evidence.
