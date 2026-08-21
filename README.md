# modx-docs

[![skills.sh][skills-src]][skills-href]

**Официальный skill** экосистемы [modx-pro](https://github.com/modx-pro) для AI-агентов.

Репозиторий: [https://github.com/modx-pro/modx-docs](https://github.com/modx-pro/modx-docs)

Документирует extras MODX Revolution, пакеты MiniShop3 и библиотеки modx-pro для сайта [docs.modx.pro](https://docs.modx.pro) (VitePress).

Работает в **Cursor** и **Claude Code**.

## Официальный skill

| | |
| --- | --- |
| GitHub | [modx-pro/modx-docs](https://github.com/modx-pro/modx-docs) |
| Установка | `npx skills add modx-pro/modx-docs` |
| Каталог skills.sh | [skills.sh/modx-pro/modx-docs](https://skills.sh/modx-pro/modx-docs) |
| Сайт документации | [docs.modx.pro](https://docs.modx.pro) |
| Issues / PR | [github.com/modx-pro/modx-docs](https://github.com/modx-pro/modx-docs/issues) |

Это канонический источник skill. Ставьте пакет из org `modx-pro`, не из сторонних форков, если нужна актуальная версия.

Клонирование для правок:

```bash
git clone https://github.com/modx-pro/modx-docs.git
cd modx-docs
```

После клона подключите локальную копию через symlink (раздел ниже), чтобы Cursor и Claude Code читали ваши правки до merge.

## Установка

```bash
npx skills add modx-pro/modx-docs
```

Команда ставит официальный skill из [modx-pro/modx-docs](https://github.com/modx-pro/modx-docs) (совместимо со [skills.sh](https://skills.sh)).

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

[skills-src]: https://skills.sh/b/modx-pro/modx-docs
[skills-href]: https://skills.sh/modx-pro/modx-docs
