---
name: official-brand-flavor-names
description: >-
  Corrects hookah tobacco brand and flavor names in research Excel files to
  official manufacturer jar names. Use when the user asks to fix бренды/ароматы,
  сверить названия с официальными сайтами, канонизировать вкусы в опросном
  листе, or produce a new xlsx with official names.
---

# Official brand and flavor names

## Goal

Take a survey Excel (опросный лист), look up **bowl brand + flavor** against official catalogs, write a **new** xlsx. Original file stays untouched.

Correct **only** чаша columns:

- `Что положили в чашу Бренд ? (N ингредиент)`
- `Что положили в чашу Вкус ? (N ингредиент)`

**Do not change** these two columns (guest answers, leave as typed):

- `Назовите бренды, которые вы знаете.`
- `Три любимых бренда табака`

Other columns (заказ, адрес, дата, направления вкуса) stay as-is. Social-follow brand lists may be normalized only if the user explicitly asks.

## Workflow

1. Inspect sheets, headers, unique brand/flavor pairs.
2. Map each pair to the manufacturer jar name. Prefer official sites / brand channels, then distributor catalogs that copy the jar title.
3. If the brand cell is survey **instruction text** («копируй с банки…»), replace it with the real brand of that flavor (e.g. Pool → Хулиган).
4. If the typed brand is wrong for that flavor (JENT + Greenwich → Spectrum Greenwich), fix the **brand**.
5. Do not invent a flavor. If several official SKUs exist, pick the **mono / exact name**, not a mix that adds extra notes (`Манго` → `Кубики манго`, not `Манго-лайм`).
6. Save a new file next to the source. Highlight changed cells. Add sheet `Правки` (row, column, было, стало, основание).
7. Tell the user the output path and remaining guesses, if any.

## Output file

- Name: `<исходное имя> — официальные названия.xlsx` (or `_финал` if iterating).
- Changed bowl cells: yellow fill on first pass; if iterating a previous file, new fixes green.
- Sheet `Правки`: one row per actual cell change.
- Do not rewrite empty strings vs `None`; do not touch non-target columns.

## Brand spelling

Use manufacturer writing, not ALL-CAPS from the form:

| Typed | Official |
|-------|----------|
| BLACKBURN | BlackBurn |
| Darkside / DARKSIDE | DARKSIDE |
| OVERDOSE / Overdose | OVERDOSE |
| Troffimof / Troffimov’s | Trofimoff's |
| Deus | DEUS |
| Sebero / Себеро | SEBERO |
| Sabotage | SABOTAGE |
| Северный | СЕВЕРНЫЙ |
| Jent | JENT |
| НАШ / Наш | NAШ |
| Наш крепкий | NAШ Black |
| Musthave | MUSTHAVE |
| Black Burn / Black burn | BlackBurn |
| Dark side | DARKSIDE |
| Over dose | OVERDOSE |
| Hlgn | Хулиган |
| Сарма / Хулиган / Bliss / Chabacco / База / Starline / Take / Palitra / Morpheus / Afzal / Bonche / Догма / Satyr | as-is (Сарма, Хулиган, Bonche, Догма, …) |

NAШ mono «Чёрная смородина» is **NAШ Black**. White line nearest SKU is a different mix (`Смородина крыжовник`) — do not substitute.

## Flavor rules

- English jar title when the maker prints English (`Raspberries`, `Cherry Rocks`, `POOL`).
- Russian title when the maker prints Russian (`Ананасовый сок`, `Кубики манго`, `Сладкий бабл`).
- Fix typos (`Гоейпфрутовый` → `Грейпфрутовый`, `Байкальяская` → `Байкальская`).
- POOL: brand **Хулиган**, flavor **POOL** (HARD POOL only if the form says hard/крепкий).
- Greenwich: brand **Spectrum**, flavor **Greenwich** (not JENT; JENT has Green Witch = absinthe).
- Kretek: brand **MattPear** (JENT has no Kretek SKU).
- NAШ «Корица» is **NAШ Black**. «Голубика» exists on both White and Black — do not change the line.
- Догма «Белое сухое» is not «Белое полусладкое». Leave it if that is what was typed.
- Chabacco lemon slices: **Lemon Jelly Slices**.
- MUSTHAVE «Карамель»: **Candy Cow**.
- BlackBurn «Байкал»: **Siberian Soda**; «тропический сок»: **На чиле**.
- DARKSIDE «черника»: **Blueberry Blast**; «клюквенный морс»: **Nordberry**; cola: **Darkside Cola**.

Full pair table: [names.md](names.md).

Line and flavor cards for the brands on the Russian market: [catalog.md](catalog.md). Portal cards come first. Brands missing there are later in the same file, taken from shop cards. Frigate is доха. Rell Blend and Split are tea-leaf mixes.

## Lookup order

1. Alias in [names.md](names.md) when the typed pair is listed there.
2. The same SKU in [catalog.md](catalog.md): brand section, then the line, then the bullet spelling. A shared word is not a match (`Манго` is not `Манго-лайм`).
3. Maker site (`blckburn.com`, `darkside-world.com`, `overdose.pro`, `sebero.ru`, `chabacco.ru`, `tabaksever.ru`, `musthave.ru`, `deustobacco.ru`, `hlgn.cc`) or a catalog that quotes the jar (`hoko.by`, `paraday.ru`).
4. If the flavor is not a listed SKU, leave it and say so. Do not invent a name. Mr. Brew's main line in catalog.md is only the names the opened pages printed.

Card brand on the portal is not always the jar brand. Write BlackBurn, DARKSIDE, OVERDOSE, MUSTHAVE, SEBERO, СЕВЕРНЫЙ, JENT, NAШ. Portal line НАШ HARD is **NAШ Black**.

Do not keep a flavor as typed just because the Russian description matches. Put the **SKU name**.
