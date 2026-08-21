# modx-docs

Skill для AI-агентов: документация extras MODX Revolution, пакетов MiniShop3 и библиотек modx-pro для [docs.modx.pro](https://docs.modx.pro) (VitePress).

Работает в **Cursor** и **Claude Code**.

## Установка

Каноническая папка (этот репозиторий / копия):

```text
modx-docs/
├── README.md
├── SKILL.md
└── references/
```

### Cursor

Симлинк в личные skills:

```bash
ln -sfn /absolute/path/to/modx-docs ~/.cursor/skills/modx-docs
```

Cursor подхватывает skill по `description`, когда вы просите документировать компонент.

### Claude Code

Симлинк в личные skills:

```bash
ln -sfn /absolute/path/to/modx-docs ~/.claude/skills/modx-docs
```

Вызов: `/modx-docs` или описание задачи по документации. См. [Claude Code skills](https://code.claude.com/docs/en/skills).

### Обе среды на одной машине

Оба симлинка должны указывать на один канонический путь. Тогда правки применяются везде.

### После публикации на GitHub

Когда пакет на GitHub (раскладка совместима с skills.sh):

```bash
npx skills add <owner>/modx-docs
```

До публикации используйте симлинки выше.

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

## Лицензия

При публикации пакета добавьте файл лицензии. Для локального использования он не нужен.
