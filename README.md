# modx-docs

Skill для AI-агентов: документация extras MODX Revolution, пакетов MiniShop3 и библиотек modx-pro для [docs.modx.pro](https://docs.modx.pro) (VitePress).

Работает в **Cursor** и **Claude Code**.

Репозиторий: [modx-pro/modx-docs](https://github.com/modx-pro/modx-docs).

## Установка

```bash
npx skills add modx-pro/modx-docs
```

### Локальная разработка (symlink)

Структура пакета:

```text
modx-docs/
├── README.md
├── SKILL.md
└── references/
```

**Cursor:**

```bash
ln -sfn /absolute/path/to/modx-docs ~/.cursor/skills/modx-docs
```

Cursor подхватывает skill по `description`, когда вы просите документировать компонент.

**Claude Code:**

```bash
ln -sfn /absolute/path/to/modx-docs ~/.claude/skills/modx-docs
```

Вызов: `/modx-docs` или описание задачи по документации. См. [Claude Code skills](https://code.claude.com/docs/en/skills).

Оба симлинка должны указывать на один канонический путь. Тогда правки применяются везде.

## Примеры запросов

```text
Документируй ./ms3OptionsColor
Документируй текущий компонент
Документируй https://github.com/modx-pro/ms3OptionsColor
Проверь документацию ms3OptionsColor
Обнови документацию после последних изменений
```

Режимы: **Document**, **Review**, **Update**. Источник — репозиторий компонента. Назначение — сайт Docs (по умолчанию соседняя папка `Docs` с `.vitepress`).

## Skill

Подробности в [SKILL.md](./SKILL.md).
