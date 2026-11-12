# Contributing to Arke Delivery Telegram Bot

Welcome! Contributors of all experience levels are encouraged to ask questions and learn while implementing their assigned work. Please communicate blockers early and review changes constructively.

## First-time setup

1. Accept the GitHub repository invitation if required, and install Git and the runtime/dependencies specified by the project once the technology stack is confirmed.
2. Clone the repository:
   ```bash
   git clone https://github.com/Arke-Express-Technical-Team/Arke-Delivery-Telegram-Bot.git
   cd Arke-Delivery-Telegram-Bot
   ```
3. Review the [project overview](PROJECT_OVERVIEW.md), [Git conventions](GIT_CONVENTIONS.md), [task ownership](TASK_DELEGATION.md), and [task guides](TASK_GUIDES.md).
4. Request clarification from the technical lead before implementing undocumented behavior.

## Start an assigned task

Always begin from an up-to-date `main`. Keep existing uncommitted changes safe before switching branches.

```bash
git switch main
git pull --ff-only origin main
git switch -c feature/<short-task-name>
```

Use `git checkout -b feature/<short-task-name>` if your Git version does not support `git switch`. **Do not use `git checkout -m` to create a branch**; `-m` has another purpose.

## Implement and verify

1. Stay within your assigned task's agreed scope; discuss significant design changes before implementing them.
2. Keep changes focused, readable, and documented where needed.
3. Do not commit bot tokens, credentials, user personal data, or local configuration secrets. Store secrets in environment variables and provide safe examples without real values.
4. Run available automated tests and relevant manual checks. If a test setup does not yet exist, explicitly record what was verified and what could not be tested.
5. Check your diff and commit using the [commit conventions](GIT_CONVENTIONS.md).

```bash
git status
git diff
git add <paths-you-changed>
git commit -m "feat: describe the change"
git push -u origin feature/<short-task-name>
```

Do not use `git add .` blindly; check that no secrets or unrelated files are staged.

## Submit a pull request

Open a PR **from your task branch into `main`**. Provide:
- What changed and why.
- Which task/issue it addresses (e.g., `Closes #12` when appropriate).
- How it was tested, with exact commands or manual steps and results.
- Any known limitations, dependencies, screenshots/logs if relevant, and follow-up work.

A reviewer may request corrections. Respond professionally, update the same branch, and ask for clarification if needed. Do not merge your own PR unless the team policy explicitly permits it. Follow the repository's configured review and branch protection rules; their exact enforcement is determined by GitHub settings.

## Keep your branch current

If GitHub reports the PR branch is behind `main`, fetch the latest changes and integrate them into your branch:

```bash
git fetch origin
git switch feature/<short-task-name>
git merge origin/main
```

Resolve any conflicts carefully, rerun checks, then push. Never force-push shared branches without coordinating with affected contributors.

## Communication expectations

Raise a blocker promptly, explain what you tried, and reference the relevant task. Deadlines and owners should be recorded by the lead in an issue or task tracker—not inferred from this guide. Be respectful in reviews, focus feedback on the code and requirements, and acknowledge contributions.
