# Installation / Установка

## English

### Windows binaries

1. Open the GitHub Releases page for this repository.
2. Download the archive matching the operating system architecture:
   `win-x64` for 64-bit Windows or `win-x32` for 32-bit Windows.
3. Download `SHA256SUMS.txt` from the same release.
4. Verify the archive before extracting it:

```powershell
Get-FileHash .\BSL-Decompiler-v0.1.0-win-x64.zip -Algorithm SHA256
Get-Content .\SHA256SUMS.txt
```

5. Extract the archive and display the built-in help:

```powershell
.\bsl-decompiler-x64.exe /?
```

The standalone executable does not require a separate Python installation.
Release archives are not committed to the public repository branch.

## Русский

### Бинарные сборки Windows

1. Откройте страницу GitHub Releases этого репозитория.
2. Скачайте архив нужной разрядности: `win-x64` для 64-битной Windows или
   `win-x32` для 32-битной Windows.
3. Скачайте `SHA256SUMS.txt` из того же выпуска.
4. До распаковки сравните контрольную сумму архива:

```powershell
Get-FileHash .\BSL-Decompiler-v0.1.0-win-x64.zip -Algorithm SHA256
Get-Content .\SHA256SUMS.txt
```

5. Распакуйте архив и откройте встроенную справку:

```powershell
.\bsl-decompiler-x64.exe /?
```

Автономный EXE не требует отдельной установки Python. Архивы выпусков не
хранятся в основной ветке публичного репозитория.
