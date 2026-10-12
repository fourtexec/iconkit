# iconkit

Большая коллекция **опенсорсных иконок в формате SVG** — более **9 400 иконок**, включая
**~1 300 анимированных** (встроенная SMIL-анимация, работают без CSS и JS).

Все иконки распространяются под свободными лицензиями (MIT / ISC) и пригодны для
коммерческого использования (условия — в файлах `LICENSE` внутри каждого набора).

## Что внутри

| Набор | Путь | Иконок | Анимация | Лицензия | Источник |
|---|---|---:|:---:|---|---|
| [Tabler Icons](https://github.com/tabler/tabler-icons) (outline) | `icons/tabler/outline/` | 5 184 | — | MIT | GitHub |
| [Tabler Icons](https://github.com/tabler/tabler-icons) (filled) | `icons/tabler/filled/` | 1 054 | — | MIT | GitHub |
| [Lucide](https://github.com/lucide-icons/lucide) | `icons/lucide/` | 1 879 | — | ISC | GitHub |
| [Material Line Icons](https://github.com/cyberalien/line-md) | `icons/animated/line-md/` | 1 231 | ✅ SMIL | MIT | GitHub |
| [SVG Spinners](https://github.com/n3r4zzurr0/svg-spinners) | `icons/animated/svg-spinners/` | 46 | ✅ SMIL | MIT | GitHub |
| [EOS Icons](https://gitlab.com/SUSE-UIUX/eos-icons) | `icons/animated/eos-icons/` | 10 | ✅ SMIL | MIT | GitLab |

**Итого: 9 404 SVG-файла.**

## Структура

```
icons/
├── tabler/
│   ├── outline/        # 5184 контурные иконки
│   ├── filled/         # 1054 залитые иконки
│   └── LICENSE
├── lucide/             # 1879 иконок (форк Feather, 24×24, stroke)
│   └── LICENSE
├── animated/           # анимированные иконки (самодостаточные .svg)
│   ├── line-md/        # 1231: переходы, лоадеры, живые иконки
│   │   └── LICENSE
│   ├── svg-spinners/   # 46 спиннеров/лоадеров
│   │   └── LICENSE
│   └── eos-icons/      # 10 анимированных (лоадеры, атом, компас…)
│       └── LICENSE
└── index.json          # машинный индекс: все наборы и имена файлов
```

## Как пользоваться

Каждая иконка — отдельный самодостаточный файл `.svg` (24×24, если не указано иное).

**Прямо в HTML:**

```html
<img src="icons/lucide/rocket.svg" width="24" height="24" alt="">
```

**Инлайн (позволяет перекрашивать через `currentColor`):**

```html
<!-- содержимое файла вставляется как есть -->
<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
     fill="none" stroke="currentColor" stroke-width="2" ...>...</svg>
```

**Программный поиск** — через `icons/index.json`:

```js
const index = await fetch('icons/index.json').then(r => r.json());
const set = index.sets.find(s => s.id === 'line-md');
// set.icons → ['account', 'alarm-light', 'alert', ...]
```

### Об анимированных иконках

- Анимация сделана через **SMIL** (`<animate>`, `<animateTransform>`) прямо внутри SVG —
  не нужны ни CSS, ни JavaScript.
- Работают при вставке инлайном, через `<img>`, `<object>` и как фон в современных браузерах
  (кроме устаревшего IE).
- Цвет большинства иконок наследуется от `currentColor` — задавайте `color` родителю.
- Иконки с суффиксом `-loop` зациклены, `-transition` проигрываются один раз.

## Лицензии и атрибуция

| Набор | Лицензия | Автор |
|---|---|---|
| Tabler Icons | MIT | Paweł Kuna / Tabler |
| Lucide | ISC | Lucide Contributors |
| Material Line Icons | MIT | Vjacheslav Trushkin |
| SVG Spinners | MIT | Utkarsh Verma |
| EOS Icons | MIT | SUSE UX/UI team |

Полный текст лицензий лежит в файлах `LICENSE` рядом с каждым набором.
Лицензии MIT/ISC не требуют атрибуции в продукте, но сохранение файла `LICENSE`
при распространении набора обязательно.

## Как наборы попали сюда

Иконки собраны 2026-10-12 из официальных источников:
архивы репозиториев на GitHub (ветки `main`/`master`) и пакеты
`@iconify-json/*` с npm-реестра. Анимированные наборы были разложены
из формата Iconify (JSON) в отдельные `.svg`-файлы: к каждому `<svg>`
добавлен корректный `viewBox`, тело иконки перенесено без изменений.
