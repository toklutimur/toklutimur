# toklutimur/toklutimur — Project Instructions

## Scope

The GitHub **profile README** repository (`toklutimur/toklutimur`). Its only
tracked file is `README.md`, which GitHub renders on
<https://github.com/toklutimur>. There is no application, no build step, no
dependency, and there never should be one here — code belongs in a real project
repo, this one is a public self-presentation page.

## Layout

- `README.md` — the entire repository: intro, work areas, tech interests,
  selected work, background, links.

## Working Rules

- The default branch is **`master`**, not `main`. PR base is `master`; a PR
  opened against `main` will fail.
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

No automated gate exists — no test suite, no linter, no build, and installing
one for a single Markdown file is out of scope. The checks are:

- `Read` the file back after editing and confirm the Markdown is well formed
  (headings, list markers, inline-code backticks balanced).
- Link check, per outbound URL, expecting `200`:
  `curl -o /dev/null -s -w "%{http_code}\n" --max-time 20 https://toklutimur.uk`
  `curl -o /dev/null -s -w "%{http_code}\n" --max-time 20 https://github.com/toklutimur`
- After merge, open <https://github.com/toklutimur> and look at the rendered
  profile. Rendering is the only real gate this repo has.

## Definition of Done (narrows the global default)

- Gates: the read-back plus a `200` from every outbound URL.
- Visual proof: the rendered profile page at <https://github.com/toklutimur>,
  checked after merge — a local Markdown preview is not proof.
- Merge: PR against `master`, `gh pr merge --squash --delete-branch`.
- Deploy: none — GitHub renders `master` directly. Live check: the profile page.
- Tests/typecheck/build items of the global default are dropped: a single
  Markdown file has nothing to compile.
- User-only steps (report, do not attempt): any change to biographical facts,
  job title, location, or which projects are worth showing.

## Agent loop

- Worker edits `README.md`; reviewer reads it back and re-runs the link checks.
- The trap: `master`, not `main`. An agent that branches off or targets `main`
  creates an orphan branch and a PR that cannot merge.
