# AGENTS.md (Skills)

This folder is a dedicated "skills vault" for coding agents/CLIs (Claude Code, Codex, OpenCode, etc.).
It is also a standalone git repo (remote: `shay-meredith/useful-skills`) intended to mirror the local
`~/Cowork/Meta/Skills` directory structure.

## Structure

- Each skill lives in its own top-level folder under `Skills/`.
- Prefer tracking skills as git submodules so upstream history and updates are easy.
  - Example: `Skills/humanizer` is a submodule pointing at `blader/humanizer`.

## Common workflows

### Clone this repo (including skills)

```sh
git clone --recurse-submodules https://github.com/shay-meredith/useful-skills.git
```

Or, if already cloned:

```sh
git submodule update --init --recursive
```

### Add a new skill from a git repo (preferred)

1) From `Skills/`:

```sh
git submodule add <repo_url> <folder_name>
git commit -m "Add <folder_name> skill"
git push
```

Notes:
- This updates both `.gitmodules` and the submodule pointer; commit both.
- Use a stable folder name (usually the repo name, lowercase, hyphenated if needed).

### Update submodules

```sh
git submodule update --init --recursive
git submodule update --remote --merge
git status
git commit -am "Bump skill submodules"
git push
```

### Add a non-git skill (a folder of files)

Put it in `Skills/<name>/` and commit it like normal content:

```sh
mkdir -p <name>
# add files...
git add <name>
git commit -m "Add <name> skill"
git push
```

## Guardrails

- Do not install skills into any agent/CLI unless explicitly asked; this repo is for tracking/reference.
- Keep credentials/secrets out of this repo.
- Prefer small, well-named folders; add a short `README.md` per skill if the upstream repo lacks context.
