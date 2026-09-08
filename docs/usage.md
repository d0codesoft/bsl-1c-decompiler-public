# Usage / Использование

## English

Use `/?` after the executable or any command to display the authoritative list
of options:

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
```

The `decompile` command writes only modules classified as `compiled_only`.
Use `--engine legacy` for the stable sequential engine or `--engine cfg` for
the CFG-based engine.

The symbolic CFG layer is enabled by default. It may be controlled explicitly:

```powershell
bsl-decompiler-x64.exe decompile configuration.cf output --abstract-execution
bsl-decompiler-x64.exe decompile configuration.cf output --no-abstract-execution
```

### Disassembly and diagnostics

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
```

Команда `decompile` сохраняет только модули с классификацией `compiled_only`.
`--engine legacy` выбирает стабильный последовательный движок, а
`--engine cfg` — движок на основе CFG.

Символьный слой CFG включён по умолчанию. Им можно управлять явно:

```powershell
bsl-decompiler-x64.exe decompile configuration.cf output --abstract-execution
bsl-decompiler-x64.exe decompile configuration.cf output --no-abstract-execution
```

### Дизассемблирование и диагностика

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
