# Agent Skills

Reusable agent skills for Codex and other Agent Skills compatible tools.

Skills are packaged under `skills/<skill-name>/` so this repository can hold
multiple installable skills.

## Repository Layout

- `skills/`: installable agent skills discovered by `npx skills` and `gh skill`
- `templates/`: copyable project templates such as `AGENTS.md` and `CLAUDE.md`

## Available Skills

- `prd`: Design the simplest coherent solution, then refine its living
  implementation checklist as evidence changes.
- `review-implementation`: Verify purpose and correctness, fix root causes,
  isolate justified legacy compatibility, and simplify repeatedly.

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

Install globally for Codex:

```bash
npx skills add https://github.com/playmoreai/agent-skills/tree/main/skills/prd \
  -g \
  -a codex \
  -y
npx skills add https://github.com/playmoreai/agent-skills/tree/main/skills/review-implementation \
  -g \
  -a codex \
  -y
```

Or install from the repository and select a skill:

```bash
npx skills add playmoreai/agent-skills --skill prd -g -a codex -y
npx skills add playmoreai/agent-skills --skill review-implementation -g -a codex -y
```

List available skills in this repository:

```bash
npx skills add playmoreai/agent-skills --list
```

### GitHub CLI `gh skill`

Requires GitHub CLI 2.90.0 or newer.

```bash
gh skill install playmoreai/agent-skills prd --agent codex --scope user
gh skill install playmoreai/agent-skills review-implementation --agent codex --scope user
```

The alias form also works on supported GitHub CLI versions:

```bash
gh skills add playmoreai/agent-skills prd --agent codex --scope user
gh skills add playmoreai/agent-skills review-implementation --agent codex --scope user
```

Preview before installing:

```bash
gh skill preview playmoreai/agent-skills prd
gh skill preview playmoreai/agent-skills review-implementation
```

### Codex Skill Installer

In Codex, ask:

```text
Use $skill-installer to install https://github.com/playmoreai/agent-skills/tree/main/skills/prd
Use $skill-installer to install https://github.com/playmoreai/agent-skills/tree/main/skills/review-implementation
```

Or run the installer script directly:

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo playmoreai/agent-skills \
  --path skills/prd
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo playmoreai/agent-skills \
  --path skills/review-implementation
```

After installation, restart Codex so the new skill is picked up.

### Shell Installer

For machines with `bash`, `curl`, and `tar`:

```bash
curl -fsSL https://raw.githubusercontent.com/playmoreai/agent-skills/main/install.sh | bash
curl -fsSL https://raw.githubusercontent.com/playmoreai/agent-skills/main/install.sh \
  | SKILL_PATH=skills/review-implementation SKILL_NAME=review-implementation bash
```

## Usage

Invoke skills in Codex by name, for example:

```text
Use $prd to design the simplest coherent solution and an evolving implementation checklist.
Use $review-implementation to verify this implementation, fix root causes, and simplify the coherent end state.
```

The `prd` skill keeps purpose, target design, and an evolving implementation
checklist in one concise living document. The `review-implementation` skill
protects correctness, fixes foundations instead of patching symptoms, and then
refines the result in focused simplification passes.
