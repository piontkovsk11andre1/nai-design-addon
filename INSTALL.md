Add this optional integration as an explicit allowed exception to the normal manifest limits.

Integration: Top-level Design repository

This add-on intentionally extends the distributive with one new top-level directory:
- Design/

This exception is authorized for this installation. Do not treat it as a workspace repository and do not place it under Workspaces/__template__/.

What to create:
- Create a top-level Design directory at workflow root, alongside Workspaces, Scripts, and Prompts.
- Initialize Design as a local git repository.
- Create an empty file Design/Target.md.
- Create the initial local commit in the Design repository with Target.md tracked.
- Treat Design/Target.md as the index of the design corpus. Files linked from it are the authoritative indexed design set.

How this integration should work:
- Design is the workflow-wide place for high-level design discussion.
- I use it to describe how design changes should turn into issues, workspaces, and staged functionality migrations.
- The design source of truth stays in the top-level Design directory, even if a separate workspace is later created for implementation or deeper iterative work.

Required prompt updates:
- Update Prompts/Workspace Agent.md so Workspace Agent understands and supports the Design workflow below.
- If needed, also add short supporting notes to Workspaces/__template__/Notes.md or Workspaces/__template__/Framework.md, but keep the main behavior in Workspace Agent.

Workspace Agent behavior for Design:
- Keep all standard Workspace Agent responsibilities unchanged.
- In addition, understand that the top-level Design directory is available as a workflow-wide design area.
- When I ask to inspect __template__, also inspect the repositories under Workspaces/__template__/ and the Design/* files referenced from Design/Target.md.
- When summarizing Design, structure the explanation so the design can be conveniently evolved from the design side:
  - what exists now,
  - what the current design intends,
  - which parts are stable,
  - which parts can be changed independently,
  - which parts should become issues,
  - which parts should become workspaces,
  - which parts imply staged migration work.
- When I ask to change the design, edit the relevant files under Design and keep Design/Target.md updated as the index.
- When I ask to commit the design, explain the intended commit briefly first, then create a local git commit in the Design repository.
- When I ask to revert, undo, or roll back design work, perform explicit local git operations in the Design repository only after confirming the target commit or rollback intent.
- After a design commit, if I ask for it, inspect the design diff and derive concrete implementation follow-up:
  - propose issues,
  - propose workspace splits,
  - propose migration steps,
  - suggest workspace names,
  - suggest branch names,
  - create issues or workspaces when I explicitly ask.
- If the design effort is iterative and deep, Workspace Agent may recommend creating a dedicated workspace for implementation or migration work, but the design source remains the top-level Design directory.
- If Design/Target.md is empty, treat that as a request to help build the initial design index rather than assuming there is no design.

Constraints:
- Do not move Design into Workspaces/__template__.
- Do not treat Design as a per-workspace repository.
- Do not push anything to a remote unless I explicitly ask.
- Prioritize files indexed from Design/Target.md over unindexed Design files when reasoning about the current design.
- Keep explanations practical: what changed in the design, what implementation work follows, and what should become an issue, a workspace, or a migration task.

Verification requirements for this add-on:
- Confirm Design/ exists at workflow root.
- Confirm Design/.git exists and Design is a real local git repository.
- Confirm Design/Target.md exists and is tracked in the initial commit.
- Confirm Prompts/Workspace Agent.md explicitly describes the Design workflow above.
- Confirm the installation summary mentions that Design is a top-level workflow-wide repository, not part of the workspace template.