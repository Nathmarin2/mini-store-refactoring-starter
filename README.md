# Mini Store — Refactoring with a Safety Net

Starter repository for the **Code Smells + Refactoring Techniques + Testing & Testability** practice.

## Team setup

Work in teams of **2–4 students**. Solo work is not allowed.

Create your **team repository** on GitHub by selecting **Use this template → Create a new repository** on the instructor's starter.

Every teammate clones the **team repository**, not the instructor's starter, through VS Code (**Clone Git Repository**).

Assign one case to each student:

| Case | Focus | File |
| --- | --- | --- |
| A | Pricing | `src/mini_store/pricing.py` |
| B | Notifications | `src/mini_store/notifications.py` |
| C | Checkout | `src/mini_store/checkout.py` |
| D | Shipping | `src/mini_store/shipping.py` |

Teams of 2 use **A–B**; teams of 3 use **A–C**; teams of 4 use **A–D**.

Each student is responsible for diagnosing, testing, and refactoring their assigned case in their own branch and Pull Request (PR).

## First-time VS Code setup — no terminal required

**Prerequisites:** VS Code with the **Python** and **Python Environments** extensions, and **Python 3.10 or later** installed.

Python **3.13** is used in GitHub Actions. Python must be available in VS Code's interpreter picker.

1. In VS Code, open the cloned **repository folder** (not an individual Python file).
2. Press **Cmd+Shift+P** on macOS or **Ctrl+Shift+P** on Windows/Linux and select **Python: Create Environment**.
3. Choose **Venv** and select your installed Python (3.10+; preferably 3.13).
4. Accept the suggested environment name (`.venv` or `venv`).
5. When prompted, choose **Install project dependencies**.
6. **Select the `test` dependency group** associated with `pyproject.toml` (displayed as something like `test -e <project path>`), then confirm. This installs `pytest` and `pytest-cov` in your project's environment. You do **not** need to select the plain `pyproject.toml` entry as well.
7. Use **Python: Select Interpreter** to confirm that the newly created environment is selected.
8. Open the **Testing** panel (flask icon). Choose **Refresh Tests** if necessary.
9. The provided project has **11 starter tests** across four files. Use **Run All Tests** or a test's individual run icon.

You should see **11 passing tests before making changes**.

> If your VS Code menus differ or tests are not discovered, verify the selected interpreter and the `test` dependency group before making changes to production code. Ask the instructor for help rather than overriding system Python package protections.
>
> You do not need to use a terminal or manually install packages system-wide.

The environment folders (`.venv/` and `venv/`) are **local-only** and excluded from Git. Never commit them.

VS Code discovers tests using the provided `.vscode/settings.json` configuration.

## Goal

Improve software design **without intentionally changing observable behavior**.

Your work should demonstrate that you can:

- Identify and justify a meaningful design problem.
- Recognize how that problem could complicate future changes.
- Use automated tests to protect existing behavior.
- Apply appropriate refactoring techniques incrementally.
- Verify that the behavior remains unchanged.
- Explain and review design decisions with teammates.

Work from the evidence in the code, not from a mandatory smell-to-technique recipe.

**Do not refactor every visible code smell.** Focus on improvements that you can justify.

## Required workflow — Refactoring with a Safety Net

Follow the sequence below for your assigned case.

### Step 1 — Diagnose the design problem

Read the assigned production code and its existing tests.

Identify:

- A code smell or design problem supported by evidence in the code.
- Why the current structure could make maintenance or future changes difficult.
- A plausible future change that would expose or increase that difficulty.
- Which existing behaviors must remain unchanged.

Do not modify production code yet.

You are not required to eliminate every code smell in your assigned file.

### Step 2 — Establish the baseline

Before modifying the code:

1. Run all existing tests using the VS Code **Testing** panel.
2. Confirm that all 11 starter tests pass.
3. Run **Run Tests with Coverage** in VS Code.
4. Record the initial coverage for your assigned production module.
5. Check the initial CI results for the unmodified `main` branch in **GitHub → Actions**.

The starter repository begins with **11 passing tests** and approximately **58% total coverage**, including branch coverage.

Coverage for your team's initial repository should be comparable to this baseline.

**This is a reference point, not a target score.**

### Step 3 — Add tests before refactoring

Create a working branch for your assigned case.

Before changing any production code:

1. Examine which behaviors are already protected by the existing tests.
2. Identify important behaviors, boundary conditions, or failure scenarios that need additional protection.
3. Add or improve meaningful unit tests for your assigned case.
4. Run the complete test suite locally.
5. Confirm that all tests pass.

Your tests should help demonstrate that the existing behavior is preserved during refactoring.

**Do not modify production code during this step.**

You may use the existing testing conventions and examples in the repository.

### Step 4 — Commit, push, and verify your safety net

**This step is mandatory and must be completed before refactoring.**

1. Open **Source Control** in VS Code.
2. Review your changes and confirm that they contain only test-related modifications.
3. Commit your new or improved tests.

   Suggested commit message:

   `Add characterization tests for [case]`

4. Push your branch to GitHub.
5. Open a **Draft Pull Request** targeting `main`.
6. Wait for GitHub Actions to complete.
7. Confirm that the **CI workflow passes** with your new tests and the original production code.

**Do not begin refactoring until your tests have been committed, pushed, and verified by a successful CI run.**

This provides a verifiable checkpoint showing that your tests passed **before** any production-code refactoring.

Keep the Draft PR open. You will continue using the same branch and PR throughout the exercise.

### Step 5 — Refactor incrementally

Now begin improving the design of your assigned production module.

1. Choose an appropriate refactoring technique based on your diagnosis.
2. Make small, focused structural changes.
3. Run the relevant tests after each meaningful change.
4. Keep existing behavior unchanged.
5. Avoid unrelated improvements or unnecessary rewrites.
6. Commit your refactoring changes separately from your initial test changes.

Suggested commit message:

`Refactor [case] to improve [design concern]`

You may create multiple refactoring commits if the changes justify them.

**The important distinction is that your Git history must clearly show tests being added and verified before production code was refactored.**

If tests fail, investigate before continuing.

A successful refactoring improves the internal structure without intentionally changing observable behavior.

### Step 6 — Verify the final result

After completing your refactoring:

1. Run the complete test suite in VS Code.
2. Confirm that all tests pass.
3. Run **Run Tests with Coverage**.
4. Compare initial and final coverage for your assigned module.
5. Push your refactoring commits.
6. Confirm that GitHub Actions passes again on your PR.
7. Record the final coverage reported in **GitHub → Actions → CI job → Run tests with coverage**.

**Coverage must not decrease.**

There is **no required final coverage percentage**.

Coverage is evidence, not the goal. Prioritize meaningful behavior verification over increasing a metric for its own sake.

If you discover additional important scenarios that deserve tests, you may add them. Explain why they matter.

Your final result should demonstrate:

- All tests passing.
- Existing behavior preserved.
- A justified design improvement.
- Successful CI.
- Coverage that has not decreased.

### Step 7 — Complete the design review

When your work is ready:

1. Mark your Draft PR as **Ready for review**.
2. Request a review from a teammate.
3. Review at least one teammate's PR.
4. Provide meaningful feedback focused on design reasoning and test quality.
5. Respond to any feedback on your own PR.
6. Merge your PR once reviews and CI checks are complete.

A meaningful review should consider:

- Whether the original design problem was adequately justified.
- Whether the refactoring actually improves the design.
- Whether the tests protect relevant behavior.
- Whether the change introduces unnecessary complexity.
- Whether the scope of the refactoring is appropriate.

A reviewer may approve a well-justified design without requesting artificial changes.

All branches, commits, pushes, and Pull Requests can be managed through **VS Code Source Control** and **GitHub's graphical interface**.

**No command-line workflow is required.**

## Human baseline — AI restriction

This is the **human baseline** for a later AI-assisted refactoring exercise.

**Do not use generative AI** to:

- Diagnose the code.
- Identify or select refactoring transformations.
- Write or generate tests.
- Write or generate refactored production code.
- Produce your design reasoning or reflection.

Official documentation and ordinary web search are allowed, along with VS Code, pytest, and GitHub.

The purpose is to establish your own understanding and demonstrate your ability to reason about software design before comparing your work with AI-assisted refactoring later.

## Pull request

Use the provided PR template.

Your PR should briefly document:

- The design problem and evidence found in the code.
- A plausible future change that makes the problem relevant.
- The behaviors that must be preserved.
- The tests added or improved **before refactoring**.
- Evidence that the test-only commit passed CI before production code was changed.
- The refactoring technique or structural improvement selected.
- Why that change improves the design.
- What you deliberately chose not to refactor.
- Passing tests and successful final CI.
- Initial and final coverage, with a brief explanation of the results.

Your PR history should make the following sequence visible:

**Tests → Commit & Push → Green CI → Refactoring → Commit & Push → Green CI → Review → Merge**

Use the same PR for the test and refactoring stages.

Do not create a separate PR solely for the initial tests.

## Individual Canvas evidence

Every student submits **their own** evidence in Canvas, even though the team shares a repository.

Include:

1. **Assigned case and branch**
   - Your case (A, B, C, or D).
   - Your working branch.

2. **Pull Request**
   - URL of your own PR.

3. **Design diagnosis**
   - The problem identified.
   - Evidence from the original code.
   - A plausible future change scenario.

4. **Safety-net evidence**
   - Initial tests passing.
   - Tests added or improved before refactoring.
   - Link or screenshot showing your test-only commit.
   - Evidence of successful CI before production-code changes.

5. **Refactoring evidence**
   - Description of the structural changes.
   - Explanation of why they improve the design.
   - Separate refactoring commit(s).

6. **Final verification**
   - All tests passing.
   - Initial and final coverage.
   - Successful final CI.
   - Explanation of how behavior preservation was verified.

7. **Peer review and merge**
   - Evidence of a meaningful review you performed on a teammate's PR.
   - Evidence that your own PR was reviewed and merged.

8. **Brief reflection**
   - What you learned about refactoring with a safety net.
   - What you deliberately chose not to change and why.

A shared repository or shared submission does **not** replace individual evidence.

Your individual Git history, PR, review, and Canvas submission must demonstrate your own contribution.