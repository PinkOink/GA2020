# GA2020

# Структура проекта
- Файл *ChartPC.jar* - результат компиляции программы, при запуске преобразует описание дерева из входного файла в DOT, который записывает в выходной файл. Из этого файла вызываются скрипты *DOTURLGenerator.py* и *random_tree_generator.py*.
- Файл *DOTURLGenerator.py* - по коду на DOT из входного файла генерирует URL запрос и открывает результат его выполнения в браузере.
- Файл *random_tree_generator.py* - генерирует файл с описанием случайного дерева, который используется в качестве входного файла по умолчанию для *ChartPC.jar*.
- Папка *src* содержит файлы с исходным кодом на Java.
- Папка *gen* содержит файлы с кодом на Java, сгенерированные с помощью плагина ANTLR v4 grammar plugin.
- Папка *out* содержит результаты компиляции Java - классов.
- Папка *grammar* содержит файл с правилами грамматики языка, на котором описываются деревья.
- Папка *libs* - директория со сторонними библиотеками и jar-файлами, использующимися в проекте.
- Папка *examples* - содержит текстовые файлы с описаниями деревьев.
- Папка *gen_dot* - содержит результаты работы программы на файлах из папки *examples*.

Для запуска и работы программы необходимы только первые 3 файла.
# Установка и запуск
Для запуска программы (на Windows) достаточно запустить исполняемый файл ChartPC.jar с помощью команды:

```java -jar ChartPC.jar INPUT_FILE OUTPUT_FILE```

(команда должна выполняться из директории, в которой лежит сам файл *ChartPC.jar*, а так же скрипты *DOTURLGenerator.py* и *random_tree_generator.py*)

Первый аргумент запуска ```INPUT_FILE``` будет интерпретироваться как полное имя входного файла. Если его опустить, то в качестве входного файла будет сгенерирован файл *random_generated_tree.txt* с описанием случайного дерева. Второй аргумент ```OUTPUT_FILE_PATH``` будет интерпретироваться как полное имя файла, в который будет записан результат (файл будет создан, или перезаписан, если он уже существует). Если его опустить, то результат будет записан в файл *generated_dot.txt*, он будет создан в активной папке, из которой вызывается команда. Остальные аргументы будут игнорироваться. 

Входной файл должен содержать синтаксически корректное описание одного дерева. В случае успешной работы программы, в выходной файл будет записан код на DOT, соответствующий описанию дерева из входного файла. Также, в браузере будет открыта страница онлайн версии утилиты Graphviz, на которой можно будет посмотреть и скачать изображение дерева, отрисованное по сгенерированному коду.

Для запуска необходимы установленные Java версии 1.8.0_251 или выше и Python версии 3.6 или выше. В случае отсутствия Python (невозможности вызвать команду ```python``` из командной строки), программу всё ещё можно запустить и сгенерировать код на DOT, но генерация случайных деревьев и визуализация в браузере работать не будут.

# Создание и настройка проекта IntelliJ IDEA
Ниже описан один из способов создать и собрать проект в IntelliJ IDEA (инструкция актуальна для версии Community Edition 2019)
1. Скачать содержимое репозитория
2. Открыть папку с содержимым как проект в IntelliJ IDEA
3. Назначить SDK для проекта (во вкладке File->Project Structure->Project выбрать SDK из выпадающего списка в графе Project SDK)
4. Выбрать папку для результатов компиляции (во вкладке File->Project Structure->Project в графе Project compiler output выбрать папку out (или любую другую))
5. Добавить папку libs в зависимости проекта (во вкладке File->Project Structure->Modules->Dependencies нажать на +, выбрать JARs or directories и в открывшемся окне выбрать папку libs)
6. Пометить папки src и gen, как директории с исходниками (в окне со структурой проекта: правый клик по папке src->Mark Directory as->Sources Root, правый клик по папке gen->Mark Directory as->Generated Sources Root)

