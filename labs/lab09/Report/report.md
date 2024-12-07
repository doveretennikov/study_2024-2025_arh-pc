---
## Front matter
title: "Отчёт по лабораторной работе №9"
subtitle: "дисциплина: Архитектура компьютера"
author: "Веретенников Дмитрий Олегович"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Приобретение навыков написания программ с использованием подпрограмм. Знакомство с методами отладки при помощи GDB и его основными возможностями.

# Задание

1. Реализация подпрограмм в NASM
2. Отладка программ с помощью GDB
3. Самостоятельное выполнение заданий по материалам лабораторной работы

# Теоретическое введение

Отладка — это процесс поиска и исправления ошибок в программе. В общем случае его можно разделить на четыре этапа:

• обнаружение ошибки; • поиск её местонахождения; • определение причины ошибки; • исправление ошибки.

Можно выделить следующие типы ошибок:

• синтаксические ошибки — обнаруживаются во время трансляции исходного кода и вызваны нарушением ожидаемой формы или структуры языка; • семантические ошибки — являются логическими и приводят к тому, что программа запускается, отрабатывает, но не даёт желаемого результата; • ошибки в процессе выполнения — не обнаруживаются при трансляции и вызывают пре- рывание выполнения программы (например, это ошибки, связанные с переполнением или делением на ноль).

Второй этап — поиск местонахождения ошибки. Некоторые ошибки обнаружить доволь- но трудно. Лучший способ найти место в программе, где находится ошибка, это разбить программу на части и произвести их отладку отдельно друг от друга.

Третий этап — выяснение причины ошибки. После определения местонахождения ошибки обычно проще определить причину неправильной работы программы. Последний этап — исправление ошибки. После этого при повторном запуске программы, может обнаружиться следующая ошибка, и процесс отладки начнётся заново.

# Выполнение лабораторной работы

## Релазиация подпрограмм в NASM

Ввожу в файл lab9-1.asm программу из листинга 9.1, сохдаю исполняемый файл и проверяю работу программы (рис. [-@fig:001]).

![Создание исполняемого файла и запуск программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение.png){#fig:001}

Изменяю текст программы, добавив подпрограмму для вычесления выражения f(g(x)) (рис. [-@fig:002]).

![Изменение программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (2).png){#fig:002}

Запускаю измененную программу и проверяю правильность ее работы (рис. [-@fig:003]).

![Запуск программы](//home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (3).png){#fig:003}

### Отладка программ с помощью GDB

Создаю файл lab9-2.asm ввожу в него текст из листинга 9.2, получаю исполняемый файл и загружаю файл в отладчик gdb (рис. [-@fig:004]).

![Получение исполняемого файл и загрузка его в отладчик gdb](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (4).png){#fig:004}

![Отладчик gdb](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (5).png){#fig:005}

Устанавливаю брейкпоинт на метку _start (рис. [-@fig:005]).

![Установка брейкпоинта](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (6).png){#fig:006}

Просматриваю дисассимилированный код программы (рис. [-@fig:006]).

!Дисассимилированный код программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (7).png){#fig:007}

Переключаюсь на отображение команд с Intel’овским синтаксисом (рис. [-@fig:008]).

![Переключение](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (8).png){#fig:008}

Различия между синтаксисом ATT и Intel заключаются в порядке операндов (ATT - Операнд источника указан первым. Intel - Операнд назначения указан первым), их размере (ATT - pазмер операндов указывается явно с помощью суффиксов, непосредственные операнды предваряются символом $; Intel - Размер операндов неявно определяется контекстом, как ax, eax, непосредственные операнды пишутся напрямую), именах регистров(ATT - имена регистров предваряются символом %, Intel - имена регистров пишутся без префиксов).

Включаю режим псевдографики (рис. [-@fig:010]).

![Режим псевдографики](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (9).png){#fig:010}

### Добавление точек останова

Устанавливаю еще одну точку останова по адресу интрукции и просматриваю информацию о всех установленных точках останова (рис. [-@fig:011]).

![Информация о точках останова](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (11).png){#fig:011}

### Работа с данными программы в GDB

Просматриваю содержимое регистров (рис. [-@fig:012]).

![Содержание регистров](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (12).png){#fig:012}

Просматриваю значение переменной msg1 по имени и переменной msg2 по адресу (рис. [-@fig:013]).

![Значения переменных](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (13).png){#fig:013}

Изменяю первый символ переменной msg1 и переменной msg2 (рис. [-@fig:014]).

![Изменения первых симолов переменных](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (14).png){#fig:014}

Вывожу в различных форматах значение регистра ebx (рис. [-@fig:015]).

![Вывод ebx в разных форматах](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (15).png){#fig:015}

С помощью команды set изменяю значение регистра ebx (рис. [-@fig:016]).

![Изменение значения регистра ebx](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (16).png){#fig:016}

### Обработка аргументов командной строки в GDB

Копирую файл lab8-2.asm в файл с именем lab9-3.asm и создаю исполняемый файл (рис. [-@fig:017]).

![Создание исполняемого файла](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (17).png){#fig:017}

Загружая исполняемый файл в отладчик указываю аргументы, далее устанавливаю точку останова перед первой инструкцией и затем просматриваю позиции стека (рис. [-@fig:018]).

![Загрузка файла, установка точки останова и просмотр позиции стека](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (18).png){#fig:018}

## Задание для самостоятельной работы

Изменяю программу из 8 лабораторной работы чтобы она вычисляла значения как подпрограмма (рис. [-@fig:019]).

![Измененная программа](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab09/Report/image/Вставленное изображение (19).png){#fig:019}

# Выводы

Почле выполнения данной лабораторной работы я приобрел навыки написания программ с использованием подпрограмм, а так же познакомился с методами отладки при поомщи GDB и его основными возможностями.

# Список литературы{.unnumbered}

1. GDB: The GNU Project Debugger. — URL: https://www.gnu.org/software/gdb/.
2. GNU Bash Manual. — 2016. — URL: https://www.gnu.org/software/bash/manual/.
3. Midnight Commander Development Center. — 2021. — URL: https://midnight-commander.
org/.
4. NASM Assembly Language Tutorials. — 2021. — URL: https://asmtutor.com/.
5. Newham C. Learning the bash Shell: Unix Shell Programming. — O’Reilly Media, 2005. —
354 с. — (In a Nutshell). — ISBN 0596009658. — URL: http://www.amazon.com/Learning-
bash-Shell-Programming-Nutshell/dp/0596009658.
6. Robbins A. Bash Pocket Reference. — O’Reilly Media, 2016. — 156 с. — ISBN 978-1491941591.
7. The NASM documentation. — 2021. — URL: https://www.nasm.us/docs.php.
8. Zarrelli G. Mastering Bash. — Packt Publishing, 2017. — 502 с. — ISBN 9781784396879.
9. Колдаев В. Д., Лупин С. А. Архитектура ЭВМ. — М. : Форум, 2018.
10. Куляс О. Л., Никитин К. А. Курс программирования на ASSEMBLER. — М. : Солон-Пресс,
2017.
11. Новожилов О. П. Архитектура ЭВМ и систем. — М. : Юрайт, 2016.
12. Расширенный ассемблер: NASM. — 2021. — URL: https://www.opennet.ru/docs/RUS/nasm/.
13. Робачевский А., Немнюгин С., Стесик О. Операционная система UNIX. — 2-е изд. — БХВ-
Петербург, 2010. — 656 с. — ISBN 978-5-94157-538-1.
14. Столяров А. Программирование на языке ассемблера NASM для ОС Unix. — 2-е изд. —
М. : МАКС Пресс, 2011. — URL: http://www.stolyarov.info/books/asm_unix.
15. Таненбаум Э. Архитектура компьютера. — 6-е изд. — СПб. : Питер, 2013. — 874 с. —
(Классика Computer Science).
16. Таненбаум Э., Бос Х. Современные операционные системы. — 4-е изд. — СПб. : Питер,
2015. — 1120 с. — (Классика Computer Science).
