# Contributing to han

This page is for contributors — anyone adding, editing, or restructuring skills, agents, or documentation in the han plugin. If you just want to use the plugin, start with the [Plugin landing page](./README.md) or the [Quickstart](./docs/quickstart.md).

> See also: [Plugin landing page — han](./README.md) · [Concepts](./docs/concepts.md) · [Sizing](./docs/sizing.md) · [YAGNI](./docs/yagni.md)

## TL;DR

- Skills live in [`plugin/skills/{name}/SKILL.md`](./plugin/skills/). Agents live in [`plugin/agents/{name}.md`](./plugin/agents/).
- Long-form docs (for humans deciding *when* and *how* to use a skill or agent) live in `docs/skills/{name}.md` and `docs/agents/{name}.md`.
- Follow the [long-form template](./docs/templates/skill-long-form-template.md) or [agent template](./docs/templates/agent-long-form-template.md). Apply the [coverage rule](./docs/templates/coverage-rule.md) to decide whether a long-form doc is needed.
- The root [CLAUDE.md](./CLAUDE.md) carries the at-a-glance project map for assistants and contributors.

## Before you start

Read these once:

- **[`docs/guidance/plugin-entity-taxonomy.md`](./docs/guidance/plugin-entity-taxonomy.md)** — What a skill is, what an agent is, what a hook is, and which to reach for.
- **[`docs/guidance/skill-building-guidance/`](./docs/guidance/skill-building-guidance/)** — The skill-authoring rules: description frontmatter, progressive disclosure, context hygiene, dynamic project discovery, bash permissions, script execution.
- **[`docs/guidance/agent-building-guidelines/`](./docs/guidance/agent-building-guidelines/)** — The agent-authoring rules: external files, model selection, domain focus, graceful degradation, multi-agent economics.
- **[Root `CLAUDE.md`](./CLAUDE.md)** — Repo conventions, doc map, and where each kind of file lives.

## Adding a skill

1. Scaffold the folder under `plugin/skills/{name}/` and add a `SKILL.md`.
2. Write the `SKILL.md`:
   - Frontmatter with `name`, `description`, `allowed-tools`. See [skill-description-frontmatter.md](./docs/guidance/skill-building-guidance/skill-description-frontmatter.md).
   - Body: numbered steps, `${CLAUDE_SKILL_DIR}` paths for script references, extracted references under `references/`.
3. Apply the [coverage rule](./docs/templates/coverage-rule.md). If the skill qualifies for a long-form doc, copy [the skill template](./docs/templates/skill-long-form-template.md) into `docs/skills/{name}.md` and fill it in.
4. Add the skill to the [Skills Index](./docs/skills/README.md) with a one-sentence scent line and a link.
5. Update the marketplace registry at [`.claude-plugin/marketplace.json`](./.claude-plugin/marketplace.json) if needed.

## Adding an agent

1. Create `plugin/agents/{name}.md` with frontmatter (`name`, `description`, `tools`, `model`) and the agent body. See [agent-domain-focus.md](./docs/guidance/agent-building-guidelines/agent-domain-focus.md) for how narrow and named the domain vocabulary should be.
2. Apply the [coverage rule](./docs/templates/coverage-rule.md). If the agent qualifies, copy [the agent template](./docs/templates/agent-long-form-template.md) into `docs/agents/{name}.md`.
3. Add the agent to the [Agents Index](./docs/agents/README.md) under the right role group.

## Editing an existing long-form doc

The docs follow a strict template. Before changing a section's shape, check [`docs/templates/skill-long-form-template.md`](./docs/templates/skill-long-form-template.md) or [`docs/templates/agent-long-form-template.md`](./docs/templates/agent-long-form-template.md) so the change stays consistent across peers.

If you are adding a section that is not in the template but applies to several skills or agents, raise it as a template change first — drift across peer docs is worse than a missing section.

## Documentation conventions

- **One canonical source per concept.** The long-form doc is canonical. The Skills Index and Agents Index carry scent only — one sentence plus a link. The README never duplicates long-form content.
- **Every long-form doc links up.** The Related Documentation section's first bullet points back to [the plugin landing page](./README.md). A reader arriving cold via search must be able to get to the front door in one click.
- **Orientation frame on top.** The first two lines of every long-form doc state what the page is, who it is for, and where the internal definition (`SKILL.md` or agent `.md`) lives.
- **TL;DR before anything else.** Three lines: what / when / what-you-get-back. Scannable for readers doing reference lookup.
- **YAGNI applies to docs too.** Doc sections that fail the [YAGNI](./docs/yagni.md) evidence test (speculative usage notes, *for-future-flexibility* warnings, examples for behavior the skill doesn't actually have yet) are not added. The same evidence rule that gates plan steps and code recommendations gates documentation.

## Reviewing your own changes

Before opening the PR, run through this checklist:

- [ ] Frontmatter is valid (no XML, no reserved prefixes, description under 1024 characters).
- [ ] `allowed-tools` matches actual usage; Bash permissions are per-prefix, not wildcards.
- [ ] Context injection commands (`` !`command` ``) are simple; complex operations live in scripts.
- [ ] Long-form doc (if added) follows the template.
- [ ] The skill or agent appears in the right index, at the right group, with accurate scent.
- [ ] Internal links resolve.

## Related Documentation

- [Plugin landing page — han](./README.md) — Where end-users start.
- [Root CLAUDE.md](./CLAUDE.md) — Project map and doc index for assistants and contributors.
- [Skills Index](./docs/skills/README.md) — All skills, grouped by purpose.
- [Agents Index](./docs/agents/README.md) — All agents, grouped by role.
- [Concepts](./docs/concepts.md) — Skill vs. agent mental model.
- [Sizing](./docs/sizing.md) — How the swarming skills classify work and scale dispatch.
- [YAGNI](./docs/yagni.md) — The evidence-based rule for what survives a review.
- [`docs/guidance/skill-building-guidance/`](./docs/guidance/skill-building-guidance/) — Skill-authoring guidance.
- [`docs/guidance/agent-building-guidelines/`](./docs/guidance/agent-building-guidelines/) — Agent-authoring guidance.
