# Changelog / История изменений

All notable public binary releases are documented here.

Здесь перечисляются значимые изменения публичных бинарных выпусков.

## [0.2.0] - 2026-11-20

### Added / Добавлено

- Opt-in semantic optimization modes `Off`, `Safe`, and `Balanced`, with reports
  and baseline output / Семантическая оптимизация с отчётами и baseline.
- Bytecode-to-BSL symbol binding validation before semantic optimization /
  Проверка привязок символов байткода к BSL до семантических преобразований.
- Validated module initializer recovery for supported straight-line instructions /
  Проверяемое восстановление поддерживаемой линейной инициализации модуля.
- `--version` / `-V` prints the executable version / Вывод версии программы.

### Fixed / Исправлено

- Stable incoming variable values and predecessor-scoped Phi merging across
  branches and loops / Устойчивое объединение значений переменных и Phi.
- Iterator lifetimes, early loop exits, exception dominance, unary-minus grouping
  and required labels / Итераторы, ранние выходы, обработчики, скобки и метки.

- Module/local naming collisions, private local declarations, invalid private
  identifiers / Коллизии областей видимости, локальные объявления и имена.
- Invalid table references retain precise diagnostics; missing slots are never
  invented / Неверные индексы диагностируются без подстановок.
- Startup help includes all options, including `--fallback-diagnostic` /
  Полная справка по параметрам, включая диагностический fallback.
- Documented that `--aggressive` belongs only to `restore` and currently enables
  no extra transformations / Уточнено фактическое действие `--aggressive`.

### Validation / Проверка

- Windows x64 and x32 builds, regression tests and native opcode fixture gate /
  Сборки x64/x32, регрессионные проверки и обязательный opcode fixture gate.
- Controlled native 1C 8.3.27 differential tests cover module initialization,
  global state and reference parameters / Контрольные сравнения на 1С 8.3.27.
- Partial output and unsupported bytecode are not certified as a complete
  executable module / Диагностический вывод не объявляется полным восстановлением.

## [0.1.0] - 2026-09-08

### Added / Добавлено

- Initial public binary release / Первый публичный бинарный выпуск.
- 1C container and compiled-module analysis / Анализ контейнеров 1С и
  скомпилированных модулей.
- Control-flow and symbolic analysis / Анализ потока управления и символьный
  анализ.
- BSL deobfuscation and reconstruction / Деобфускация и восстановление BSL.
- Windows x64 and x32 executables / Исполняемые файлы Windows x64 и x32.

### Dependencies / Зависимости

- saby v8unpack 1.2.11 (MIT License).
