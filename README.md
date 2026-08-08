# agent-rules

Portable, entity-independent Copilot **agent conduct rules**, loaded globally so they
apply in every repository on a machine — independent of Copilot Memory or any billing
entity.

The rules live in [`copilot-instructions.md`](copilot-instructions.md).

## Why this exists

Copilot Memory can be tied to a specific billing entity (e.g. an enterprise seat), so
personal preferences stored there may not be available in every session. A plain
instructions file, by contrast, is loaded deterministically by the Copilot CLI from
well-known paths. This repo is the versioned master copy; activate it globally with one
of the methods below.

## Activate globally (choose one)

The Copilot CLI reads instructions from `~/.copilot/copilot-instructions.md` and from
directories listed in `COPILOT_CUSTOM_INSTRUCTIONS_DIRS`, among other paths.

### Option 1 — symlink into `~/.copilot`

```sh
git clone https://github.com/coseguera/agent-rules.git ~/dev/agent-rules
mkdir -p ~/.copilot
ln -sf ~/dev/agent-rules/copilot-instructions.md ~/.copilot/copilot-instructions.md
```

### Option 2 — point the env var at the clone

Add to your shell profile (e.g. `~/.zshrc` or `~/.bashrc`):

```sh
export COPILOT_CUSTOM_INSTRUCTIONS_DIRS="$HOME/dev/agent-rules"
```

## Keep it up to date

```sh
git -C ~/dev/agent-rules pull
```

Per-repo instructions (`.github/copilot-instructions.md`, `AGENTS.md`) still apply on
top of these global rules for repo-specific conventions.
