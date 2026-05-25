# Nai Design Add-on

An optional add-on for [Nai](https://github.com/piontkovsk11andre1/nai) that adds a top-level `Design/` repository to the workflow.

This add-on is for cases where design work should live outside individual workspaces:

- architecture notes,
- design-driven issue discovery,
- migration planning,
- staged implementation rollouts.

The core Nai workflow stays the same. This add-on introduces one explicit exception: a workflow-wide `Design/` directory at the workflow root, next to `Workspaces/`, `Scripts/`, and `Prompts/`.

## What it adds

After installation, your Nai workflow gains:

- a top-level `Design/` local git repository,
- `Design/Target.md` as the index of the design corpus,
- Workspace Agent instructions for reading, editing, committing, and reverting design work,
- a practical bridge from design changes to follow-up issues, workspaces, and staged migration tasks.

The `Design/` repository is not part of `Workspaces/__template__/` and is not treated as a per-workspace repo.

## When to use it

Use this add-on when you want to keep high-level design discussion in one stable place and derive implementation work from it later.

Typical fit:

- you want one shared design source of truth across many workspaces,
- you want design commits to drive issues and implementation splits,
- you expect migrations to happen in stages across several repos or workspaces.

## How to install it

This add-on is meant to be applied to an existing Nai installation. Install Nai first, then apply this add-on to that workflow root.

### Recommended flow

1. Open your AI coding agent in the root of your existing Nai workflow.
2. Open [INSTALL.md](INSTALL.md) from this repository.
3. Copy its full contents into the agent.
4. Add one short instruction above it, for example:

```text
Apply this add-on to my existing Nai workflow at <workflow-root>. Follow the specification exactly.
```

5. Let the agent make the required changes in the Nai workflow.

### What to paste into the agent

Use a message in this shape:

```text
Apply this add-on to my existing Nai workflow at <workflow-root>. Follow the specification exactly.

[paste the full contents of this repository's INSTALL.md here]
```

If your agent can read local files directly, you can instead tell it to read [INSTALL.md](INSTALL.md) and implement it in your existing Nai workflow.

## What the installer agent should do

When the add-on is applied correctly, it should:

- create `Design/` at the workflow root,
- initialize `Design/` as a local git repository,
- create and track `Design/Target.md` in the initial commit,
- update `Prompts/Workspace Agent.md` so Workspace Agent understands the design workflow,
- keep the design source of truth in `Design/`, even when implementation later happens in separate workspaces.

## How to use it after install

Once installed, you can ask Workspace Agent to:

- inspect the indexed design files referenced from `Design/Target.md`,
- summarize what exists now and what the design intends,
- identify stable parts and independently changeable parts,
- turn design changes into issues, workspace proposals, and migration steps,
- edit design files and keep `Design/Target.md` updated,
- create local design commits when you explicitly ask.

That makes `Design/` the long-lived design layer, while Nai workspaces remain the place for implementation and execution.

## Verification checklist

After installation, confirm that your workflow root contains:

- `Design/`
- `Design/.git`
- `Design/Target.md`

Also confirm that Workspace Agent explicitly mentions the design workflow and that it treats `Design/` as a top-level repository, not part of the workspace template.

## License

[MIT](LICENSE)
