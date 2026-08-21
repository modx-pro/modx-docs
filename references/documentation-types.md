# Documentation types

Choose the smallest structure that fits public surface area. Do not create multi-page only for appearance.

## Landing (single file)

Use when the package has little public surface: short install, few settings, one snippet, or a simple payment description.

```text
docs/components/<name>.md
docs/en/components/<name>.md   # if EN required
```

Typical sections: what it is → requirements → install → configuration → usage → reference.

## Multi-page

Use when topics are independent (settings vs integration vs many snippets) or the page would be hard to scan.

```text
docs/components/<name>/
├── index.md
├── quick-start.md
├── settings.md
└── ...
```

### Payment gateway (MS3)

`index`, `quick-start`, `settings`, `integration`, optional `faq`.

### Storefront / snippet package

Start pages + `snippets/` (index + per snippet) + optional `frontend/`, `events`, `faq`.

### Plop multi stub

Plop may generate `events`, `interface/`, sample snippets. Delete or replace pages that do not match the package.

## Optional sections (only with evidence)

| Section | When |
| --- | --- |
| FAQ / Troubleshooting | Real errors from code, issues, README, changelog |
| Migration | Confirmed breaking changes between versions |
| Screenshots | Real UI captures. Mark missing screenshots as gaps. Never invent images |
| Public API | Classes/methods confirmed as public surface |

## Language

- Default for modx-pro Docs: write RU first unless the user asks for EN only.
- If only RU exists — report missing EN. Create EN only when asked (or when CI sync is explicitly in scope).
- When both exist — keep structural parity (same pages, same covered features). EN is a translation of meaning, not machine calque. Do not translate identifiers.

## Page opener

Start with: what it is, what problem it solves, who needs it. Then install / configure / use / reference as needed. No marketing fluff. No artificial sections.
