# toklutimur/toklutimur — Project Instructions

## Scope

The GitHub **profile README** repo (`toklutimur/toklutimur`). Its only tracked
file is `README.md`, rendered on <https://github.com/toklutimur>. No application,
build step or dependency, and never one here — code belongs in a real project repo.

## Working Rules

- GitHub-flavoured Markdown only, and only the subset GitHub renders in a
  profile README. HTML `<img>`/`<div>` alignment tricks and badge walls are a
  deliberate non-goal — keep the plain, text-first tone of the current file.
- Every factual claim (employer, location, degree, project) is the user's
  biography. Never invent, upgrade or "polish" a credential; changes to facts
  come from the user.
- Only link to properties the user owns. Current outbound links:
  `https://toklutimur.uk` and `https://github.com/toklutimur`.
- Named projects must exist. `README.md:18-21` names the DoE/RSM engine, the
  personal AI workstation, the engineering calculators and Mon Amie Burger;
  before adding a bullet, confirm the repo exists under
  `C:/Users/toklutimur/Documents/GitHub`.

## Gate commands

No automated gate exists (no tests, linter or build). The checks are:

- `Read` the file back after editing and confirm the Markdown is well formed
  (headings, list markers, inline-code backticks balanced).
- Link check, per outbound URL, expecting `200`:
  `curl -o /dev/null -s -w "%{http_code}\n" --max-time 20 https://toklutimur.uk`
  `curl -o /dev/null -s -w "%{http_code}\n" --max-time 20 https://github.com/toklutimur`
- After merge, open <https://github.com/toklutimur>: rendering is the only real gate.

## Definition of Done (narrows the global default)

- Gates: the read-back plus a `200` from every outbound URL.
- Merge: squash, delete branch.
- Deploy: none — GitHub renders `main` directly.
- User-only steps (report, do not attempt): any change to biographical facts,
  job title, location, or which projects are worth showing.

## Agent loop

- Base branch is `main`; PR base `main`.

<!-- harness:shared v3 - source ~/.claude/templates/AGENTS-agent-loop.md; edit there -->

## Agent behaviour (shared)

- The main session orchestrates: it reads git, this file, state/plan files and agent
  reports; source, diffs, test output and data are read by subagents.
- Every dispatch names its model: Explore/haiku locate, worker/sonnet mechanical edit,
  worker/opus judgement or risk, reviewer/opus verdicts. Never fable as a subagent.
- Leave no artefacts: scratch output goes to the session scratchpad, not the repo root;
  delete or gitignore anything untracked you created before reporting DONE.
- Visual work (UI repos): the brief lists VISUAL ACCEPTANCE criteria and a
  "must not change" list; the reviewer compares before/after screenshots at
  the viewport or device this file's Definition of Done names, and the live URL
  or device after deploy. Two fixes on one subject = stop, re-scope.

<!-- /harness:shared -->
