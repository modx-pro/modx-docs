# Frontmatter (docs.modx.pro)

Block `---` must start on line 1. Follow the destination guide `docs/guide/frontmatter.md` when present.

## Any page

```yaml
---
title: Заголовок
description: Краткое описание для meta и карточек
---
```

Optional: `outline`, `lastUpdated: false`, `editLink: false`.

## Component root (`index.md` or single-file landing)

Common fields (omit unknown values — never invent URLs):

| Field | Notes |
| --- | --- |
| `title` | Product camelCase |
| `description` | Short, factual |
| `author` | GitHub login from `docs/authors.json` |
| `logo` | Real asset URL only |
| `modstore` / `modx` / `repository` | Real URLs only |
| `dependencies` | string or array (e.g. `miniShop3`) |
| `categories` | Existing values only |
| `items` | Multi-page nav only on root `index.md` |
| `outline` | e.g. `deep` |

### Example (payment)

```yaml
---
title: msp3YooKassa
description: Приём оплаты через ЮKassa для MiniShop3
author: ibochkarev
dependencies: miniShop3
categories: minishop3
logo: https://modstore.pro/assets/extras/msp3yookassa/logo.png
modstore: https://modstore.pro/packages/payment-system/msp3yookassa
items: [
  { text: 'Быстрый старт', link: 'quick-start' },
  { text: 'Системные настройки', link: 'settings' },
  { text: 'Интеграция и сценарии', link: 'integration' },
]
---
```

### Banned placeholders

Do not leave:

- `https://placehold.co/...`
- Fake `https://modstore.pro/...` or `https://github.com/...`
- Fake `author` logins

If a value is unknown — omit the field and list it under Remaining issues.

## Authors

Read `docs/authors.json`. Key = GitHub login. Do not invent authors. If missing, derive only from reliable package metadata. Otherwise tell the user and leave `author` unset or ask.

## Categories

Observed values (do not invent new ones automatically):

| Value | Use |
| --- | --- |
| `minishop3` | MS3 extras and MS3 payment gateways |
| `payment` | Legacy MS2-style payment one-pagers |
| `utilities` | Utilities |

Plop may default to `payment`. For MS3 packages set `minishop3` when that matches neighbors.

## Settings tables

When documenting system settings, prefer tables:

| Key | Type | Default | Description |
| --- | --- | --- | --- |

Keys are `{namespace}_{name}`. If a setting exists in transport but unused in code — say so explicitly.
