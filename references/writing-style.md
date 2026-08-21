# Writing style (self-contained)

Apply this to all RU/EN documentation prose you create or edit. External `stop-slop` is optional. Prefer this file. Do not fail if `stop-slop` is missing.

Do **not** apply to: code blocks, setting keys, class/snippet/event names, YAML identifier values, commit messages.

## Workflow

1. Draft for facts first. Do not change verified claims to sound nicer.
2. Apply Core Rules and Quick Checks.
3. Score 1–10 on each dimension below. Total under 35/50 → rewrite.
4. Match neighboring Docs pages (`msp3yookassa`, `mscurrency`, `ajaxform`): factual, direct, human.

## Core rules

1. **Cut filler.** No throat-clearing («важно отметить», «данное дополнение позволяет», «в заключение»). No empty intensifiers. Prefer zero adverbs.
2. **No formula traps.** Avoid «не X, а Y», rhetorical questions, fake agency («решение позволяет», «система создаёт платёж» without an actor).
3. **Active voice.** Name who does what. «Компонент вызывает Init», «вы указываете ключ».
4. **Specific.** Real setting keys, class names, status codes, URLs. No «структурные причины».
5. **Address the reader.** RU: «вы». EN: «you». Present tense.
6. **Rhythm.** Mix sentence length. Avoid three similar sentences in a row. No em dash (—) as decoration.
7. **Trust the reader.** No «просто», «легко», «очевидно», «просто сделайте» as fluff.
8. **No pull-quotes.** If a line sounds like a slogan, rewrite it.
9. **Russian:** never join independent clauses with `;`. Use a period. Keep `;` only in code, schemas, machine lists.
10. **Banned marketing:** hype, unearned «best practice», anthropomorphism («сервер думает»).

## Docs formatting

- Sentence case for headings.
- `code font` for API identifiers, keys, paths, snippet names.
- **Bold** for UI labels.
- Numbered lists for ordered steps. Bullets otherwise.
- Requirements: «must» / «нужно». Prefer clear requirements over vague «should».

## EN translation

Translate meaning with normal technical English. Do not machine-calque Russian. Do not translate: class names, snippets, settings, events, package names, code.

## Quick checks

- Filler / adverbs / passive / false agency?
- Em dash? Russian clause-joining `;`?
- «просто / легко / очевидно»?
- Vague claims without names?
- Three equal-length sentences?
- Placeholder URLs or `$foo` / `$bar` where domain names exist?

## Scoring (35/50 minimum)

| Dimension | Question |
| --- | --- |
| Directness | Statements or announcements? |
| Rhythm | Varied or metronomic? |
| Trust | Respects reader intelligence? |
| Authenticity | Sounds human? |
| Density | Anything cuttable? |

## Examples

**Bad (RU):** Важно отметить, что данное дополнение позволяет легко настроить оплату через шлюз.

**Good (RU):** Компонент добавляет способ оплаты MiniShop3 и принимает уведомления банка на `webhook.php`.

**Bad (RU):** Платёж создаётся системой; статус обновляется автоматически.

**Good (RU):** Обработчик создаёт платёж в API банка. Webhook обновляет статус заказа в MiniShop3.

**Bad (EN):** This simple module allows you to easily configure payment settings.

**Good (EN):** The package registers a MiniShop3 payment method and stores bank credentials in system settings.
