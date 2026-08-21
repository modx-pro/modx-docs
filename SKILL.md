---
name: modx-docs
description: >-
  Documents MODX Revolution extras, MiniShop3 packages, and modx-pro libraries
  for docs.modx.pro (VitePress). Detects component source vs Docs destination,
  creates or updates RU/EN pages from code (no invented API), reviews coverage,
  and patches docs after component changes. Use when the user asks to document a
  component, write/update/review docs, add component pages, describe snippets,
  system settings, events, or API, sync RU/EN docs, or update Docs after code
  changes. Do not use for ordinary component development with no documentation
  request.
---

# modx-docs

Write and maintain documentation for the MODX / modx-pro ecosystem. The component
repository is the source of truth. The Docs site is only a destination.

Works in Cursor and Claude Code. Prefer built-in [references/writing-style.md](references/writing-style.md). Do not fail if an external `stop-slop` skill is missing.

If the destination is `modx-pro/Docs` (or a local clone), also read its `AGENTS.md` and `docs/guide/*` when present. Those override conflicting details in this skill.

## Modes

| Mode | When | Behavior |
| --- | --- | --- |
| **Document** | «Документируй…», «Напиши документацию…», «Добавь docs…» | Full create or rewrite from code + conventions |
| **Review** | «Проверь документацию…», «Review docs…» | Audit only. No file edits until the user agrees |
| **Update** | «Обнови docs после изменений…» | Diff-driven minimal patch of affected pages |

If the mode is unclear, ask once: Document, Review, or Update.

## Workflow

```text
detect source → detect destination → inspect component → inspect existing docs
→ inspect Docs conventions → choose type → write/update (or audit) → writing-style pass → verify
```

Copy this checklist and track it:

```text
- [ ] Source resolved
- [ ] Destination resolved
- [ ] Component inspected (code, not guesses)
- [ ] Existing docs found (update, do not duplicate)
- [ ] Documentation type chosen (landing / multi-page)
- [ ] Pages written or reviewed
- [ ] writing-style.md applied to prose
- [ ] Verification passed
```

## Source detection

Resolve in this order. Do not guess.

1. **Explicit local path** — `./ms3OptionsColor`, absolute path.
2. **GitHub URL** — prefer an existing local clone. Do not re-clone without need. Otherwise use available GitHub access and the default branch.
3. **Current working directory** — only if it looks like a MODX package (`core/components/`, `_build/`, `elements/`, package metadata, etc.). Not every git repo is a component.
4. **Name while inside Docs** — look for a sibling folder (`../ms3OptionsColor`, `Extras/<name>`, etc.). If several matches, ask.
5. **Unresolved** — ask:

```text
Укажи исходники компонента:
1. путь к локальной папке
2. URL GitHub repository
3. использовать текущий рабочий каталог
```

## Destination detection

1. Explicit path from the user.
2. Else find a Docs tree with `docs/`, `.vitepress/`, and `package.json` (sibling `../Docs`, workspace parent, and similar).
3. If not found — ask. Never create a new Docs repository.

Do not swap source and destination.

## Canonical name and existing docs

Derive the name from `composer.json`, `package.json`, README, MODX package metadata, namespace, repository name. Keep product casing in `title`. Paths use lowercase (see [component-structure.md](references/component-structure.md)).

Search destination for:

```text
docs/components/<name>/
docs/components/<name>.md
docs/en/components/<name>/
docs/en/components/<name>.md
```

Also try aliases (package name, display name). If docs exist — **update them**. Do not create a parallel tree.

## Research

Follow [references/code-analysis.md](references/code-analysis.md). Document public behavior only. If a fact is not confirmed by code, README, CHANGELOG, tests, or official docs — do not state it as fact. Mark uncertainty explicitly.

## Documentation type

Choose landing vs multi-page with [references/documentation-types.md](references/documentation-types.md). Use Plop (`pnpm generate`) in Docs only as a scaffold. Rewrite to match nearest real components, not Plop placeholders.

## Write / update

1. Match conventions: [frontmatter.md](references/frontmatter.md), [component-structure.md](references/component-structure.md).
2. Find at least three similar documented components before inventing structure.
3. No fake URLs, placeholders, or invented settings/parameters.
4. Keep navigation `items` in sync with files.
5. RU/EN: structural parity when both exist. Do not create the second language unless asked (warn about Docs CI sync if only RU).

## Writing gate

Before finishing Document/Update prose, read and apply [references/writing-style.md](references/writing-style.md). Score below 35/50 → revise. Optional: if `stop-slop` is installed, you may run it too. Never require it.

## Verification

Run [references/verification.md](references/verification.md). Prefer destination `pnpm lint` / targeted cspell over full `build`.

### Final output (Document / Update)

```text
Documentation source:
<path or repository>

Documentation destination:
<path or repository>

Component:
<canonical name>

Documentation:
<created / updated>

Language:
<RU / EN / RU + EN>

Type:
<landing / multi-page>

Changes:
- ...

Verification:
- Source analysis ✓/✗
- Frontmatter ✓/✗
- Links ✓/✗
- Navigation ✓/✗
- Markdown ✓/✗
- Code accuracy ✓/✗
- RU/EN parity ✓/✗
- Writing style ✓/✗

Remaining issues:
- ... or none
```

### Review output

Use the template in [verification.md](references/verification.md). Then propose a change plan. Wait for approval before editing.

## References

- [component-structure.md](references/component-structure.md) — paths, nav, etalon layouts
- [frontmatter.md](references/frontmatter.md) — YAML fields, authors, categories
- [documentation-types.md](references/documentation-types.md) — landing vs multi-page
- [code-analysis.md](references/code-analysis.md) — how to read a MODX package
- [verification.md](references/verification.md) — checks and templates
- [writing-style.md](references/writing-style.md) — prose rules (self-contained)
