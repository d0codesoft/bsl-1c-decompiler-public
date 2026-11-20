# Usage / Использование

## English

Use `/?` after the executable or any command to display the authoritative list
of options:

Running the executable without arguments, or with `/?`, `-h`, or `--help`,
prints all commands and all their parameters, including aliases. Command-level
help prints only that command. The list is generated from the argument parser,
so new options are included automatically.

```powershell
bsl-decompiler-x64.exe /?
bsl-decompiler-x64.exe decompile /?
bsl-decompiler-x64.exe restore /?
```

### Scan a container

Lists modules and their classification without copying source modules:

```powershell
bsl-decompiler-x64.exe scan configuration.cf
```

### Decompile compiled-only modules

```powershell
bsl-decompiler-x64.exe decompile configuration.cf output
bsl-decompiler-x64.exe decompile configuration.cf output --engine cfg
bsl-decompiler-x64.exe decompile configuration.cf output --object "CommonModule.ModuleName"
bsl-decompiler-x64.exe decompile configuration.cf output --semantic-optimization Balanced
```

The `decompile` command writes only modules classified as `compiled_only`.
The default is the CFG engine with 130 opcodes based on the recovered 8.3.27.2342
contract. The historical sequential path is available with
`--engine legacy --opcode-profile profiles/historical.json`.

The symbolic CFG layer is enabled by default. It may be controlled explicitly:

```powershell
bsl-decompiler-x64.exe decompile configuration.cf output --abstract-execution
bsl-decompiler-x64.exe decompile configuration.cf output --no-abstract-execution
```

### Disassembly and diagnostics

`--fallback-diagnostic` tries complete reconstruction first, then saves partial
diagnostic output if reconstruction fails. It can be combined with Balanced:

```powershell
bsl-decompiler-x64.exe decompile module.epf out --dump-cfg --fallback-diagnostic --semantic-optimization Balanced
```

Keep a space between `out` and `--dump-cfg`. The `decompile` command does not
accept `--aggressive`; only `restore` accepts it, and currently it is recorded
in the report without enabling additional transformations.


```powershell
bsl-decompiler-x64.exe disasm configuration.cf output
bsl-decompiler-x64.exe decompile configuration.cf output --engine cfg --dump-cfg --dump-ir --dump-ssa
bsl-decompiler-x64.exe opcode-stats configuration.cf
bsl-decompiler-x64.exe compare-engines configuration.cf
```

### Restore textual BSL

The `restore` command accepts a `.bsl` or `.txt` file or a directory and does
not require a CF container or a compiled image:

```powershell
bsl-decompiler-x64.exe restore module.bsl
bsl-decompiler-x64.exe restore module.bsl -o clean.bsl --report --diff
bsl-decompiler-x64.exe restore modules -o restored --dump-cfg
```

Without `-o`, the output is written next to the input as
`NAME.restored.bsl`. Conservative mode preserves control flow that cannot be
proved safe to restructure.

## Русский

Команда `/?` после имени EXE или подкоманды показывает актуальный перечень
параметров:

Запуск без аргументов либо с `/?`, `-h`, `--help` выводит полную справку:
все команды, все их параметры и альтернативные написания флагов.
Справка подкоманды содержит только её параметры. Перечень формируется из
определений аргументов CLI, поэтому новые параметры включаются автоматически.

```powershell
bsl-decompiler-x64.exe /?
bsl-decompiler-x64.exe decompile /?
bsl-decompiler-x64.exe restore /?
```

### Сканирование контейнера

Выводит модули и их классификацию, не копируя модули с исходным текстом:

```powershell
bsl-decompiler-x64.exe scan configuration.cf
```

### Декомпиляция compiled-only модулей

```powershell
bsl-decompiler-x64.exe decompile configuration.cf output
bsl-decompiler-x64.exe decompile configuration.cf output --engine cfg
bsl-decompiler-x64.exe decompile configuration.cf output --object "CommonModule.ИмяМодуля"
bsl-decompiler-x64.exe decompile configuration.cf output --semantic-optimization Balanced
```

Команда `decompile` сохраняет только модули с классификацией `compiled_only`.
`--engine legacy --opcode-profile profiles/historical.json` выбирает прежний последовательный движок, а
`--engine cfg` — движок на основе CFG.

Символьный слой CFG включён по умолчанию. Им можно управлять явно:

```powershell
bsl-decompiler-x64.exe decompile configuration.cf output --abstract-execution
bsl-decompiler-x64.exe decompile configuration.cf output --no-abstract-execution
```

### Дизассемблирование и диагностика

`--fallback-diagnostic` сначала пробует полный вывод и при ошибке сохраняет
частичный диагностический листинг. Он совместим с попыткой Balanced:

```powershell
bsl-decompiler-x64.exe decompile 000_embedded_11014BFD0.epf out --dump-cfg --fallback-diagnostic --semantic-optimization Balanced
```

Между каталогом `out` и `--dump-cfg` нужен пробел. `--aggressive` команда
`decompile` не принимает. Этот флаг существует только у `restore`; в текущей
реализации он записывается в отчёт, дополнительных преобразований не включает.

```powershell
bsl-decompiler-x64.exe disasm configuration.cf output
bsl-decompiler-x64.exe decompile configuration.cf output --engine cfg --dump-cfg --dump-ir --dump-ssa
bsl-decompiler-x64.exe opcode-stats configuration.cf
bsl-decompiler-x64.exe compare-engines configuration.cf
```

### Восстановление текстового BSL

Команда `restore` принимает файл `.bsl`/`.txt` либо каталог и не требует
контейнера CF или compiled image:

```powershell
bsl-decompiler-x64.exe restore module.bsl
bsl-decompiler-x64.exe restore module.bsl -o clean.bsl --report --diff
bsl-decompiler-x64.exe restore modules -o restored --dump-cfg
```

Без `-o` результат создаётся рядом с исходным файлом под именем
`ИМЯ.restored.bsl`. Консервативный режим сохраняет участки потока управления,
безопасное структурирование которых не доказано.
