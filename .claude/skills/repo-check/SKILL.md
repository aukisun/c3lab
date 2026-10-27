---
name: repo-check
description: Audit the C³ repository — stray files, README accuracy against the live app, brand spelling, console errors, dead code — and report fixes in Russian before changing anything. Use when Ivanko asks to check, tidy or review the repo or docs.
---

# Аудит репозитория C³

Ничего не меняй, пока Иванко не одобрит. Сначала отчёт.

## Проверь

1. **Файлы.** Всё в корне сверх `index.html`, `README.md`, `CLAUDE.md`, `.vercelignore`, `.claude/`, `assets/` — кандидат на удаление или `.gitignore`. Отдельно ищи `.DS_Store`, бэкапы, скриншоты, пустые папки.
2. **`.vercelignore`.** Есть ли он и закрывает ли `CLAUDE.md`, `CLAUDE.local.md`, `.claude`, чтобы служебные файлы не публиковались на сайте.
3. **README против приложения.** Сверь с `index.html`:
   - способы ввода (вкладки `nav.modes`);
   - список и правила гармоний (`HARMONIES`: `name`, `rule`);
   - форматы экспорта (кнопки `#copy*`);
   - версия в футере (`C³ Engine vN`);
   - ссылка на сайт.
4. **Бренд.** Найди «Complimentary» и неправильное «Complementary Color Creator» (без s) — допустимо только в History README. Проверь `<title>`, `meta description`, футер `nuforms lab`.
5. **Работоспособность.** Подними `python3 -m http.server 8000`, открой страницу в Browser pane, собери ошибки консоли. Пройди Code → Upload → Picker один раз.
6. **Мёртвый код.** Функции и CSS-классы, которые нигде не используются (поиск по имени). Перечисли, не удаляй.

## Отчёт

По-русски, таблицей:

| Что | Статус | Предложение |

Статус: «в порядке», «мелочь» или «надо чинить». В конце — одна строка с приоритетом: что сделать первым. Спроси, что чинить.

Почини одобренное, закоммить, а для публикации предложи `/ship`.
