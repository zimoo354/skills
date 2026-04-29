---
name: cr-pr-create
description: Generate pull request descriptions and optionally create PRs via GitHub CLI. Triggers on "create pr", "pr", "pull request", "draft pr", or when user wants to open a PR.
---

# Pull Request Creation

Help reviewer understand change fast. Minimal noise, maximum signal.

## Process

1. **Check current branch** — run `git branch --show-current`. If `main` or `master`, stop. Offer `git checkout -b <short-name>` and wait for user confirmation. Do not proceed until on a feature branch.
2. **Find base branch** — default `main`. Use user-specified branch if given.
3. **Get diff** — run `git diff <base>...HEAD --stat` and `git log <base>..HEAD --oneline`.
4. **Draft description** — follow repo template (`.github/pull_request_template.md` if exists). Otherwise use sections below.
5. **Check `gh`** — run `gh --version`. If installed and user said "create pr" or "draft pr", create it. Otherwise output description for copy-paste and tell user `gh` status.

## Description Format

Keep sections short. Bullet points over paragraphs. Omit sections with nothing to say.

```
### Motivation

One-line why. Link issue if mentioned in commits or branch name.

### Approach

High-level how. Not code-splanation. Focus on decisions worth reviewer attention.

### TODOs

Only open items. Checked items belong in commit history, not PR.

### Screenshots

Include only if UI changed. Use before/after table when applicable.

```

## Tone

Lean. Drop filler words. Fragments ok. Every sentence should help reviewer decide faster.

Bad:
> In this pull request, I have made some changes to the user authentication flow in order to improve the overall security posture of the application.

Good:
> Switches auth flow to PKCE. Prevents auth code interception on mobile.

## Creating the PR

If `gh` installed and user explicitly asked to create:

```bash
gh pr create \
  --base <base-branch> \
  --title "<concise title>" \
  --body-file <description-file> \
  ${draft:+--draft}
```

- Title ≤50 chars, imperative mood.
- Use `--draft` if user said "draft".
- If no template exists in repo, generate description inline.

If `gh` not installed, output the full command above so user can run it later.

## Output Checklist

Before finishing, check:

- [ ] Diff summarized accurately, no hallucinated changes.
- [ ] Description follows repo template if one exists.
- [ ] Motivation and Approach are present and concise.
- [ ] Empty sections removed rather than left blank.
- [ ] `gh` availability reported to user.
- [ ] PR created only if user explicitly asked.
