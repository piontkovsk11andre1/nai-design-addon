# Nai Design Add-on

An optional add-on for [Nai](https://github.com/piontkovsk11andre1/nai) that adds a workflow-wide `Design/` repository.

It gives you one place for:

- high-level design notes,
- design-driven issue discovery,
- migration planning,
- staged implementation rollout planning.

The main Nai workflow stays the same. This add-on adds one top-level repository, `Design/`, next to `Workspaces/`, `Scripts/`, and `Prompts/`.

## What it gives

After install, your Nai workflow has:

- a top-level local git repository at `Design/`,
- `Design/Target.md` as the index of the design corpus,
- Workspace Agent support for reading, editing, committing, and reverting design work,
- a way to turn design changes into issues, workspace splits, and staged migration steps.

`Design/` is not part of `Workspaces/__template__/` and is not treated as a per-workspace repository.

## Install

In the root of an existing Nai installation, run `Open Agent` and send one message:

> Please read <https://raw.githubusercontent.com/piontkovsk11andre1/nai-design-addon/main/INSTALL.md>
> and apply this add-on to the current Nai workflow.

That updates the workflow so it includes the top-level `Design/` repository and teaches Workspace Agent how to use it.

## How to use it

After install, ask Workspace Agent to:

- inspect the design files indexed from `Design/Target.md`,
- summarize what exists now and what the design intends,
- identify stable parts and independently changeable parts,
- derive issues, workspaces, and migration stages from the design,
- edit design files and keep `Design/Target.md` updated,
- create a local design commit when you explicitly ask.

This keeps design as a long-lived top-level source of truth, while Nai workspaces remain the place for implementation work.

## License

[MIT](LICENSE)
