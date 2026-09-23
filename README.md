# Agent Skills

Reusable agent skills for Codex and other Agent Skills compatible tools.

Skills are packaged under `skills/<skill-name>/` so this repository can hold
multiple installable skills.

## Repository Layout

- `skills/`: installable agent skills discovered by `npx skills` and `gh skill`
- `templates/`: copyable project templates such as `AGENTS.md` and `CLAUDE.md`

## Available Skills

- `prd`: Design the simplest user-centered solution, then refine its living
  implementation checklist as evidence changes.
- `review-implementation`: Verify the user experience and correctness, fix root
  causes when fixes are requested, and preserve justified compatibility.

## Templates

- `templates/AGENTS.md`: concise project instruction template for coding agents
- `templates/CLAUDE.md`: delegates Claude-compatible tools to `AGENTS.md`

Copy the templates into a project root and customize the placeholders:

```bash
cp templates/AGENTS.md /path/to/project/AGENTS.md
cp templates/CLAUDE.md /path/to/project/CLAUDE.md
```

## Install

### skills.sh / `npx skills`

Install globally for Codex and Claude Code:

```bash
npx skills add https://github.com/golbin/agent-skills/tree/main/skills/prd \
  -g \
  -a codex claude-code \
  -y
npx skills add https://github.com/golbin/agent-skills/tree/main/skills/review-implementation \
  -g \
  -a codex claude-code \
  -y
```

Or install from the repository and select a skill:

```bash
npx skills add golbin/agent-skills --skill prd -g -a codex claude-code -y
npx skills add golbin/agent-skills --skill review-implementation -g -a codex claude-code -y
```

List available skills in this repository:

```bash
npx skills add golbin/agent-skills --list
```

### GitHub CLI `gh skill`

Requires GitHub CLI 2.90.0 or newer.

```bash
gh skill install golbin/agent-skills prd --agent codex --scope user
gh skill install golbin/agent-skills review-implementation --agent codex --scope user
```

The alias form also works on supported GitHub CLI versions:

```bash
gh skills add golbin/agent-skills prd --agent codex --scope user
gh skills add golbin/agent-skills review-implementation --agent codex --scope user
```

Preview before installing:

```bash
gh skill preview golbin/agent-skills prd
gh skill preview golbin/agent-skills review-implementation
```

### Codex Skill Installer

In Codex, ask:

```text
Use $skill-installer to install https://github.com/golbin/agent-skills/tree/main/skills/prd
Use $skill-installer to install https://github.com/golbin/agent-skills/tree/main/skills/review-implementation
```

Or run the installer script directly:

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo golbin/agent-skills \
  --path skills/prd
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo golbin/agent-skills \
  --path skills/review-implementation
```

Updated skills are available on the next Codex turn. Reload Claude Code if its
current session still shows an older copy.

### Shell Installer

For machines with `bash`, `curl`, and `tar`:

```bash
curl -fsSL https://raw.githubusercontent.com/golbin/agent-skills/main/install.sh | bash
curl -fsSL https://raw.githubusercontent.com/golbin/agent-skills/main/install.sh \
  | SKILL_PATH=skills/review-implementation SKILL_NAME=review-implementation bash
```

## Usage

Invoke skills in Codex by name, for example:

```text
Use $prd to design the simplest user-centered solution and an evolving implementation checklist.
Use $review-implementation to review this implementation against its requirements and user workflow.
Use $review-implementation to fix the confirmed issues and verify the result.
```

The `prd` skill keeps the user's task, purpose, target design, and an evolving
implementation checklist in one concise living document. The
`review-implementation` skill protects the user experience and correctness,
reports actionable findings, and fixes root causes when improvements are requested.
Planning and review respect the task scope; they do not introduce a new approval
step when implementation is already authorized.

## Updating

Reinstall the selected skills to update both clients and their source metadata:

```bash
npx skills add golbin/agent-skills --skill prd review-implementation \
  -g -a codex claude-code -y
```

Before replacing an installation, preserve any local edits. If an old standalone
copy exists under `~/.codex/skills/`, compare it with the shared installation at
`~/.agents/skills/` and archive the stale copy so Codex sees one version.

The repository commit and the installer lock record identify the installed
revision. These skills follow the focused descriptions and proportional guidance
in [Rethinking skills and prompts for GPT-6 Astra](https://developers.openai.com/blog/rethinking-skills-and-prompts-for-gpt-6-astra),
while remaining usable by other agents.
