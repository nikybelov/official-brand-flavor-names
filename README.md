# Официальные бренды и ароматы

Скилл для Cursor: сверяет бренды и вкусы в чаше опросного Excel с именами на банке производителя и пишет новый файл. Исходник не перезаписывает.

Не трогает колонки «Назовите бренды, которые вы знаете» и «Три любимых бренда табака».

## Установка в Cursor

Customize → Plugins → Add → **From GitHub Repository**:

```
https://github.com/nikybelov/official-brand-flavor-names
```

Затем Install, scope: user или проект.

## Установка через GitHub CLI

```bash
gh skill install nikybelov/official-brand-flavor-names official-brand-flavor-names --agent cursor --scope user
```

## Что внутри

- `skills/official-brand-flavor-names/SKILL.md` — правила сверки
- `skills/official-brand-flavor-names/names.md` — таблица имён с банок
