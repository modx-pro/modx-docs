# Component structure (docs.modx.pro)

Target site: VitePress. File `docs/components/foo/bar.md` → URL `/components/foo/bar`. Internal links omit `docs/` and `.md`. Prefer root-relative links: `/components/mscurrency/settings`.

## Naming

- Paths: Latin lowercase, hyphenated words (`quick-start.md`, `settings.md`). No Cyrillic in paths.
- Component folder = package name lowercase: `msp3yookassa`, `mscurrency`.
- Frontmatter `title`: product camelCase (`msp3YooKassa`, `msCurrency`). Do not change casing without evidence.
- Screenshots: `docs/components/<ns>/screenshots/*.png` → `/components/<ns>/screenshots/name.png`.

## Landing vs folder

| Form | Path |
| --- | --- |
| Single page | `docs/components/<name>.md` |
| Multi-page | `docs/components/<name>/index.md` + nested `.md` |

EN mirror: same relative path under `docs/en/`.

## Navigation (`items`)

Only on multi-page root `index.md`. Links relative to the component folder, no `.md`:

```yaml
items: [
  { text: 'Быстрый старт', link: 'quick-start' },
  {
    text: 'Сниппеты',
    items: [
      { text: 'Обзор', link: 'snippets/index' },
    ],
  },
]
```

Every `link` must resolve to a real file. No orphan pages. Update `items` in the same change as new pages.

## Etalons (copy structure, not text)

### MS3 payment gateway

Examples: `msp3yookassa`, `msptbank`, `msp3sberbank`.

```text
index.md        — overview, requirements, install, notification URL
quick-start.md  — keys, webhook/callback, payment method, test
settings.md     — settings tables
integration.md  — API ↔ code, flow (mermaid ok), limits
faq.md          — optional, only with real errors
```

`categories: minishop3`. No `snippets/` unless the package ships snippets. Use bank term **webhook** or **callback** and the real path under `assets/components/<ns>/`. Payment method display names come from package resolvers, not shortened brand names.

### MS3 storefront / snippets

Examples: `mscurrency`, `ms3variants`, `msviewcounter`.

- Nav groups: start, site integration, FAQ.
- `frontend/`, `snippets/index.md` + one page per public snippet.
- User-facing examples: VitePress `::: code-group` with `fenom` and `modx` fences.

### Legacy single page

Example: `ajaxform.md`, older `msp*.md`. Acceptable for small packages. Prefer multi-page for new MS3 packages with several topics.

## Plop

In Docs destination: `pnpm generate` uses `plopfile.js` / `plop-templates/`. Treat output as a stub (often wrong categories, placeholder logos, generic snippet pages). Reshape to the nearest etalon and real package surface.

## Before writing structure

Inspect at least three similar components in the destination:

1. Similar function (payment / storefront / utility)
2. Multi-page with nav
3. API or settings-heavy page

Reuse heading patterns, terminology, and link style only.
