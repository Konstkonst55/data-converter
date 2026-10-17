# Data Converter

Консольная утилита на C++17 для преобразования записей между CSV, JSON и YAML. CMake загружает `yaml-cpp` и Google Test автоматически.

## Быстрый старт

```bash
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release
cmake --build build --config Release
```

## Примеры запуска

```bash
./build/dataconv examples/people.csv build/people.json
./build/dataconv examples/people.json build/people.yaml
./build/dataconv examples/people.yaml build/people.csv
```

В Windows путь к исполняемому файлу зависит от генератора CMake: это может быть `build/dataconv.exe` или `build/Release/dataconv.exe`.

## Тесты

```bash
ctest --test-dir build -C Release --output-on-failure
```

## GitHub Actions

Workflow запускается при `push` и `pull_request` на Ubuntu, macOS и Windows. Раздельная сборка на этих ОС помогает обнаружить различия компиляторов, системных библиотек и чувствительности файловой системы к регистру.

`fail-fast: false` позволяет всем заданиям матрицы завершиться, даже если одно упало. Для эксперимента временно внесите контролируемое падение теста, повторите запуск с `fail-fast: true`, затем восстановите тест.

Кэш хранит исходники зависимостей для повторного использования и разделяется по ОС и содержимому `CMakeLists.txt`. Артефакты сохраняют результаты конкретного запуска - журнал тестов и исполняемый файл - чтобы их можно было скачать из GitHub Actions. Для проверки кэша сравните первое выполнение workflow со следующим запуском без изменений, а затем с изменённым исходным файлом.
