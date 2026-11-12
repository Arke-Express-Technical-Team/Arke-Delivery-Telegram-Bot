# Branch, commit and pull request conventions

Use simple, consistent naming to make repository history searchable. Branches are created from an updated `main`, and all normal changes return to `main` through pull requests.

## Branch names

Format: `<type>/<short-kebab-case-description>`

| Prefix | Purpose | Example |
| --- | --- | --- |
| `feature/` | New user-facing capability | `feature/pickup-selection` |
| `fix/` | Bug fix | `fix/invalid-location-message` |
| `docs/` | Documentation only | `docs/contributor-workflow` |
| `refactor/` | Restructure without intentional behavior changes | `refactor/pricing-module` |
| `test/` | Tests only | `test/pricing-edge-cases` |
| `chore/` | Maintenance or tooling | `chore/ci-setup` |
| `hotfix/` | Urgent production correction (lead-coordinated) | `hotfix/incorrect-delivery-quote` |

Use lowercase letters, hyphens between words, and a concise task description. Include an issue number when available, for example `feature/23-pickup-selection`. Avoid personal names, spaces, and vague names such as `new-code` or `final`.

Create a new branch:

```bash
git switch main
git pull --ff-only origin main
git switch -c feature/pickup-selection
```

## Commit messages

Use a simplified **Conventional Commits** format:

```text
<type>(optional-scope): short imperative description
```

Common types:
- `feat`: new feature
- `fix`: defect correction
- `docs`: documentation
- `refactor`: internal rework without intentional behavior change
- `test`: tests
- `chore`: upkeep and tooling
- `ci`: CI workflow changes
- `build`: build and dependency changes
- `perf`: performance improvement

Examples:

```text
feat(locations): add pickup selection validation
fix(pricing): reject unsupported routes
test(delivery): cover invalid state transitions
docs: explain contributor workflow
ci: add pull request checks
```

Keep the subject specific, lowercase after the colon when appropriate, and preferably within about 72 characters. Each commit should represent a coherent change. Avoid `update`, `changes`, or `stuff` as complete messages.

## Pull request expectations

- Target `main` from a task branch.
- Use a descriptive title, e.g. `feat: add pickup selection flow`.
- Include a change summary, linked task/issue, test evidence, known limitations and relevant screenshots where useful.
- Keep PRs focused; separate unrelated features.
- Request review and address feedback; do not treat an opened PR as approved.
- Ensure required checks pass and branch-up-to-date requirements are met **if configured** in GitHub.
- Never bypass protected branch rules. Approval and merge authority follow the actual repository rulesets and team policy.

Suggested PR body:

```md
## Summary
- ...

## Related task
Closes #<issue-number>

## Testing
- [ ] Automated tests: <commands and results>
- [ ] Manual verification: <steps and results>

## Risks / limitations
- ...

## Checklist
- [ ] Scope matches assigned task
- [ ] No credentials or personal data committed
- [ ] Documentation updated where relevant
- [ ] Requested reviewers notified
```
