# MultyModik by Staili

[Русский](#русский) | [English](#english)

**Version / Версия:** `1.2.0`
**Plugin / Плагин:** `MultyModikByStaili.dll`
**Releases:** [github.com/naduvaha/MultyModik/releases](https://github.com/naduvaha/MultyModik/releases)
**Hard dependency / Жёсткая зависимость:** [KrokoshaCasualtiesMP (KrokMP)](https://cucorelib.web.app/)

---

<a id="русский"></a>

<details open>
<summary><b>Русский</b></summary>

## Описание

Дополнение к мультиплеер-моду **KrokoshaCasualtiesMP** для игры **Casualties Unknown**.
Один отдельный плагин-DLL — никаких изменений в самих DLL игры.

## Возможности

### Возрождение команды
- Общий командный лимит возрождений (настраивается в меню правил забега).
- Самовозрождение из режима наблюдателя рядом с живым союзником (с кулдауном).
- Возрождение союзника по коду: у погибшего игрока появляется код, любой живой игрок (не только хост) может ввести его и поднять товарища.
- Уважает правила меню «сохранять инвентарь» и «сохранять статистику».

### Динамическая сложность мобов
- Множитель спавна враждебных существ: 100 % (ваниль) — до 1000 %.
- Минимальный множитель растёт от командного лимита возрождений (6+ → 200 %, 40+ → 600 %, 50 → 1000 %).
- Отдельная настройка «время миссии» (1–300 %) со своими штрафами к спавну.
- Пользовательские значения сохраняются и возвращаются, когда штрафы снимаются.

### Физика воды
- Опция «без сбивания водой» — текущая вода больше не валит персонажа с ног.
- Компромисс: +100 % к минимальному спавну враждебных, пока опция включена.

### Мини-босс «Большой теневой ползун» (Spider)
- Включается чекбоксом в меню правил («Паучок» / «Spider»).
- Появляется на 2 уровне примерно на 60 % прохождения области, вдали от игроков.
- 1000 HP, увеличенный размер, спавнится парой.
- Агрессивный ИИ: преследует без остановки, не прячется в тени; теряет цель только после долгого разрыва и потери линии видимости.
- Прогрызает блоки и постройки, пробираясь к игрокам (анти-застревание — копает и впереди, и под собой).
- Накладывает эффект «ужас» на игроков в зоне видимости.
- Усиленный укус со средним кровотечением.
- При убийстве: настроение всей команды +40, выпадает 6 панцирей.
- Консольные команды: `bigspider spawn`, `bigspider spawn force`, `bigspider spawn cursor`, `bigspider pos`.

### Механика «Обнимашки» (Hug)
- Нативная кнопка под кнопкой CPR в окне ран.
- Обнимающий ничего не теряет; обнимаемому каждые 4 сек +1 к настроению.
- Визуальные «+1» над игроками и реплики в чат.
- Авто-отмена при гибели одного из участников или разрыве дистанции.

### Бонус «Сон в обнимку» (Sleep Buddy) — новое в 1.2.0
- Когда два или больше игроков спят рядом (в радиусе ~6 блоков), у всех в группе медленно растёт настроение.
- Бонус накапливается каждые ~2 секунды и масштабируется от числа соседей-сонь (cap-кратно).
- Полностью серверно: хост проверяет, кто спит, кто рядом, и подбрасывает настроение через стандартную синхронизацию тел.
- Работает автоматически — никаких кнопок, активируется самим фактом совместного сна.

### Проверка обновлений
- При запуске игры плагин разово опрашивает GitHub Releases этого репозитория и сравнивает версию с установленной.
- Результат пишется в `BepInEx\LogOutput.log` и дублируется в игровую консоль:
  - **зелёная строка** — установлена последняя версия;
  - **оранжевое предупреждение** — доступна более новая версия (со ссылкой на страницу релизов).
- Запрос отправляется один раз за запуск, тайм-аут 8 сек., никакой телеметрии не собирается.

## Установка

1. Установите BepInEx и мод **KrokoshaCasualtiesMP (KrokMP)** — см. https://cucorelib.web.app/
2. Скопируйте `MultyModikByStaili.dll` в папку:
   ```
   Casualties Unknown\BepInEx\plugins\
   ```
3. Запустите игру. В логе `BepInEx\LogOutput.log` должна появиться строка:
   ```
   [Info : MultyModikByStaili] MultyModik by Staili loaded.
   ```

> Все игроки в лобби (хост и клиенты) должны иметь одинаковую версию плагина.

## Совместимость

- Требует версию игры и KrokMP, под которые собрана сборка. После крупного обновления игры или KrokMP сборку нужно пересобрать.
- Возможны конфликты с другими модами, патчащими `SpiderHandler`, спавн мобов или интерфейс окна ран.

## Содержимое релиза

| Файл | Описание |
|------|----------|
| `MultyModikByStaili.dll` | Плагин — кладётся в `BepInEx\plugins\` |
| `README.md` | Этот файл |

</details>

---

<a id="english"></a>

<details>
<summary><b>English</b></summary>

## About

An add-on for the **KrokoshaCasualtiesMP** multiplayer mod for **Casualties Unknown**.
A single standalone plugin DLL — no changes to the game's own DLLs.

## Features

### Team respawning
- Shared team respawn pool (configurable in the run-rules menu).
- Spectator self-respawn near a living ally (on cooldown).
- Code-based ally revive: a dead player gets a code; any living player (not only the host) can type it in to bring them back.
- Honors the menu's "keep inventory" and "keep stats" toggles.

### Dynamic mob difficulty
- Hostile spawn multiplier: 100 % (vanilla) up to 1000 %.
- Floor multiplier scales with the team respawn pool (6+ → 200 %, 40+ → 600 %, 50 → 1000 %).
- Separate "mission time" setting (1–300 %) with its own spawn penalties.
- Your custom values are remembered and restored when penalties are lifted.

### Water physics
- "No water knockdown" option — flowing water no longer pushes you off your feet.
- Trade-off: +100 % to the hostile-spawn floor while enabled.

### Mini-boss "Big Shade-crawler" (Spider)
- Enabled via a checkbox in the rules menu ("Spider" / "Паучок").
- Spawns on layer 2 at ~60 % depth, away from players.
- 1000 HP, scaled up, spawns in a pair.
- Aggressive AI: chases relentlessly, no shadow-hiding; only drops aggro after a long break of LOS and distance.
- Chews through blocks and buildings to reach players (anti-stuck digger — carves both ahead and underneath itself).
- Applies the "horrified" moodle while visible.
- Buffed bite with medium bleeding.
- On kill: whole team's mood set to +40, drops 6 carapaces.
- Console commands: `bigspider spawn`, `bigspider spawn force`, `bigspider spawn cursor`, `bigspider pos`.

### "Hug" mechanic
- Native-style button below the CPR button in the wound view.
- The hugger loses nothing; the huggee gains +1 mood every 4 s.
- Floating "+1" indicators above players and chat barks.
- Auto-cancels if either side dies or they walk out of range.

### "Sleep Buddy" bonus — new in 1.2.0
- When two or more players are sleeping close together (within ~6 blocks), everyone in the group slowly gains mood.
- Bonus pays out every ~2 seconds and scales with the number of nearby sleepers (capped).
- Fully server-side: the host scans who's asleep and who's near them, and tops up happiness through the standard body sync.
- Fully automatic — no buttons, it just activates by sleeping near teammates.

### Update check
- On game launch the plugin makes a single request to this repository's GitHub Releases and compares the latest tag with the installed version.
- The result is written to `BepInEx\LogOutput.log` and mirrored into the in-game console:
  - **plain line** — you are on the latest version;
  - **orange warning** — a newer version is available (with a link to the releases page).
- One request per launch, 8-second timeout, no telemetry.

## Install

1. Install BepInEx and the **KrokoshaCasualtiesMP (KrokMP)** mod — see https://cucorelib.web.app/
2. Drop `MultyModikByStaili.dll` into:
   ```
   Casualties Unknown\BepInEx\plugins\
   ```
3. Launch the game. `BepInEx\LogOutput.log` should contain:
   ```
   [Info : MultyModikByStaili] MultyModik by Staili loaded.
   ```

> Every player in the lobby (host and clients) must run the same plugin version.

## Compatibility

- Tied to the game/KrokMP version this build targets. After a major game or KrokMP update the plugin needs a rebuild.
- May conflict with other mods that patch `SpiderHandler`, mob spawning, or the wound-view UI.

## Release contents

| File | Purpose |
|------|---------|
| `MultyModikByStaili.dll` | The plugin — place in `BepInEx\plugins\` |
| `README.md` | This file |

</details>
