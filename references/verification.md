# Verification

Run after Document or Update. For Review, use the audit template without editing files.

## Checklist

1. **Accuracy** — every technical claim matches source.
2. **Frontmatter** — valid YAML; no fake URLs; `author` in `authors.json` if set.
3. **Links** — new internal and external links resolve. Prefer `/components/...` style used in Docs.
4. **Navigation** — every `items[].link` has a file; no orphans.
5. **Markdown / VitePress** — containers, `code-group`, fences with languages (`modx`, `fenom`, `bash`, `php`, `mermaid`, `text`).
6. **Code examples** — match current API.
7. **RU/EN** — if both exist, same structure and features.
8. **Conflicts** — no contradictory pages left behind.
9. **Writing style** — [writing-style.md](writing-style.md) pass completed.
10. **Git diff** — only intended docs files. No temp files, no accidental component source edits.

## Commands (Docs destination)

Read destination `package.json` first. Typical scripts:

```bash
pnpm lint
pnpm lint -- "docs/components/<ns>/**/*.md"
pnpm exec cspell "docs/components/<ns>/**/*.md"
```

Prefer lint/cspell over `pnpm build`. Do not run file-mutating commands without assessing impact. Full `pnpm spellcheck` may noise on unrelated EN stubs.

New terms → destination `cspell.json` `words` (lowercase).

RU/EN sync CI: new RU file needs matching `docs/en/...` or an explicit note that EN is deferred.

## Review template

```text
# Documentation review

## Source
...

## Existing documentation
...

## Coverage
- Installation: ✓|⚠|✗
- Configuration: ✓|⚠|✗
- System settings: ✓|⚠|✗
- Snippets: ✓|⚠|✗
- Events: ✓|⚠|✗
- API: ✓|⚠|✗
- Examples: ✓|⚠|✗

## Accuracy
...

## Structure
...

## Writing style
...

## RU / EN parity
...

## Broken links
...

## Recommended changes
1. ...

## Priority
Critical:
...
Recommended:
...
Optional:
...
```

Then propose a plan. Edit only after the user agrees.

## Final output (Document / Update)

```text
Documentation source:
...

Documentation destination:
...

Component:
...

Documentation:
created | updated

Language:
RU | EN | RU + EN

Type:
landing | multi-page

Changes:
- ...

Verification:
- Source analysis ✓|✗
- Frontmatter ✓|✗
- Links ✓|✗
- Navigation ✓|✗
- Markdown ✓|✗
- Code accuracy ✓|✗
- RU/EN parity ✓|✗
- Writing style ✓|✗

Remaining issues:
none | ...
```

## Conceptual scenario checks (skill behavior)

| # | Input | Expected |
| --- | --- | --- |
| 1 | `Документируй ./ms3OptionsColor` | source = path, destination = nearby Docs |
| 2 | GitHub URL | source = repo (local clone preferred), destination = Docs |
| 3 | Inside component: «текущий компонент» | source = CWD, destination = `../Docs` if valid |
| 4 | Inside Docs: name only | source = sibling / Extras, destination = current Docs |
| 5 | Docs exist | update, no duplicate tree |
| 6 | RU only | report missing EN |
| 7 | Large API surface | multi-page |
| 8 | Tiny package | landing |
| 9 | Parameter absent in code | do not invent |
| 10 | Source unclear | ask |
