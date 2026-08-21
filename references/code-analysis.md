# Code analysis (source of truth)

The component repository is the source of truth. Documentation must match what the code does.

## Never invent

Do not invent: API, parameters, snippets, events, system settings, processors, classes, methods, dependencies, configuration, permissions, versions, URLs, usage examples, behavior.

If unconfirmed — omit or mark as unknown.

## Where to look

General:

```text
README.md, CHANGELOG.md, LICENSE
composer.json, package.json
src/, core/, core/components/, elements/, _build/, tests/, docs/
```

MODX package focus:

- Snippets, chunks, plugins
- Processors, services, classes
- System settings (`_build/elements/settings.php` and runtime reads)
- Events and plugin bindings
- Lexicons (user-facing labels, not necessarily every key)
- TVs, DB schema / migrations
- HTTP / REST endpoints, console commands, cron
- Permissions / policies
- Declared dependencies and PHP / MODX version requirements

## Package metadata

From build/composer/README: package name, version, author, description, dependencies, min MODX/PHP, namespace, setup options.

Skip internal transport details unless the user needs them to install or debug.

## Public vs internal

Document public API only. Skip private helpers unless the README or package explicitly presents them as API.

For a public class (only if confirmed public): namespace, purpose, constructor, methods, arguments, returns, exceptions, one minimal real example.

## Snippets

For each user-facing snippet: purpose, parameters, defaults, allowed values, call example, result. Verify the real signature in source. Do not invent parameters from the name alone.

Prefer Fenom + MODX examples in Docs via `::: code-group`.

## System settings

For each documented setting: key, type, default, allowed values, effect. Confirm the key is read in code or clearly shipped for user config.

## Events and plugins

Event name, when it fires, what the component does, conditions, available data. For plugins: bound events, purpose, relevant settings.

## Examples

Minimal, reproducible, aligned with current API. Prefer domain names (`$order`, `$payment`) over `$foo` / `$bar`.

## Paid modstore packages

If transport is encrypted, document the `modstore.pro` provider requirement when install fails without it (see neighboring payment docs).

## After research

List public surface → choose documentation type → map pages. Do not document every discovered file.
