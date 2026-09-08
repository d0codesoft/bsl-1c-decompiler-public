# BSL Decompiler

[English](#english) · [Русский](#русский)

## English

BSL Decompiler is a command-line tool for analyzing, deobfuscating, and
reconstructing compiled-only 1C:Enterprise BSL modules. It also provides a
separate restoration mode for already extracted textual BSL.

Only modules classified as `compiled_only` are written by the `disasm` and
`decompile` commands. Modules that already contain source code are reported by
`scan` but are not copied to the output directory.

### Features

- 1C container and module discovery;
- compiled-module disassembly;
- control-flow reconstruction;
- symbolic analysis and conservative dead-branch removal;
- BSL deobfuscation and source reconstruction;
- textual BSL restoration without a container;
- x64 and x32 Windows command-line builds.

### Supported input

- 1C:Enterprise `CF`, `CFE`, `EPF`, and `ERF` containers supported by the
  bundled container layer;
- extracted compiled module images;
- `.bsl` and `.txt` files for the `restore` command.

### Quick start

```powershell
bsl-decompiler-x64.exe scan configuration.cf
bsl-decompiler-x64.exe decompile configuration.cf output --engine cfg
bsl-decompiler-x64.exe restore module.bsl -o module.restored.bsl
bsl-decompiler-x64.exe decompile /?
```

See [Installation](docs/installation.md) and [Usage](docs/usage.md) for the
complete public documentation.

### Download

Ready-to-use binaries and `SHA256SUMS.txt` are distributed through the
[GitHub Releases page](../../releases). Release binaries are not stored in the
main branch.

### Component boundary

```text
1C CF / CFE / EPF / ERF
          |
          v
saby v8unpack 1.2.11       container processing
          |
          v
BSL Decompiler             module and bytecode analysis
          |
          v
CFG / symbolic analysis / deobfuscation / BSL reconstruction
```

### Third-party components

BSL Decompiler uses **saby v8unpack 1.2.11** as the container-processing
layer for supported 1C:Enterprise binary formats. v8unpack is an independent
third-party project licensed under the MIT License and is not the BSL
decompiler, CFG analyzer, or symbolic analysis engine.

Official project: [saby-integration/v8unpack](https://github.com/saby-integration/v8unpack)

See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) for attribution and
license information.

### License and disclaimer

BSL Decompiler is proprietary software. The distributed binary version may be
used subject to the terms in [LICENSE](LICENSE); the source code is not
publicly distributed under that license. Third-party components remain subject
to their respective licenses.

The software is provided **AS IS**, without warranties of any kind. Use is
entirely at the user's own risk. To the maximum extent permitted by applicable
law, the author and distributors shall not be liable for damages, losses, data
loss, lost profits, business interruption, or other consequences arising from
use of or inability to use the software.

## Русский

BSL Decompiler — консольный инструмент для анализа, деобфускации и
восстановления compiled-only модулей BSL платформы 1С:Предприятие. Также
предусмотрен отдельный режим восстановления уже извлечённого текстового BSL.

Команды `disasm` и `decompile` сохраняют только модули, классифицированные как
`compiled_only`. Модули с доступным исходным текстом отображаются командой
`scan`, но не копируются в каталог результата.

### Возможности

- обнаружение контейнеров и модулей 1С;
- дизассемблирование скомпилированных модулей;
- восстановление потока управления;
- символьный анализ и консервативное удаление доказанно мёртвых ветвей;
- деобфускация и восстановление исходного BSL;
- восстановление текстового BSL без контейнера;
- консольные сборки Windows x64 и x32.

### Поддерживаемые входные данные

- контейнеры 1С:Предприятия `CF`, `CFE`, `EPF` и `ERF`, поддерживаемые
  встроенным слоем обработки контейнеров;
- извлечённые образы скомпилированных модулей;
- файлы `.bsl` и `.txt` для команды `restore`.

### Быстрый старт

```powershell
bsl-decompiler-x64.exe scan configuration.cf
bsl-decompiler-x64.exe decompile configuration.cf output --engine cfg
bsl-decompiler-x64.exe restore module.bsl -o module.restored.bsl
bsl-decompiler-x64.exe decompile /?
```

Подробности приведены в документах [Установка](docs/installation.md) и
[Использование](docs/usage.md).

### Загрузка

Готовые бинарные сборки и `SHA256SUMS.txt` публикуются на странице
[GitHub Releases](../../releases). Бинарные файлы релизов не хранятся в
основной ветке.

### Разделение компонентов

`saby v8unpack 1.2.11` отвечает за обработку контейнеров 1С. Анализ модулей и
байткода, построение CFG, символьный анализ, деобфускация и восстановление BSL
реализованы отдельно в BSL Decompiler.

Официальный проект: [saby-integration/v8unpack](https://github.com/saby-integration/v8unpack)

### Лицензия и отказ от гарантий

BSL Decompiler является проприетарным программным обеспечением. Использование
распространяемой бинарной версии регулируется файлом [LICENSE](LICENSE).
Исходный код по этой лицензии публично не распространяется. Сторонние
компоненты регулируются собственными лицензиями.

Программа предоставляется **«КАК ЕСТЬ»**, без каких-либо гарантий. Пользователь
использует её на свой риск. В максимальной степени, допускаемой применимым
законодательством, автор и распространители не отвечают за ущерб, потери
данных, упущенную выгоду, перерывы в работе и иные последствия использования
или невозможности использования программы.
