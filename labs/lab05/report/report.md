---
## Front matter
title: "Отчёт по лабораторной работе №5"
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

Целью данной лабораторной работы является приобретение практических навыков работы в Midnight Commander, освоение инструкций языка ассемблера mov и int.

# Задание

1. Основы работы с mc
2. Структура программы на языке ассемблера NASM
3. Подключение внешнего файла
4. Выполнение заданий для самостоятельной работы

# Теоретическое введение

Midnight Commander (или просто mc) — это программа, которая позволяет просматривать структуру каталогов и выполнять основные операции по управлению файловой системой, т.е. mc является файловым менеджером. Midnight Commander позволяет сделать работу с файлами более удобной и наглядной. Программа на языке ассемблера NASM, как правило, состоит из трёх секций: секция кода программы (SECTION .text), секция инициированных (известных во время компиляции) данных (SECTION .data) и секция неинициализированных данных (тех, под которые во время компиляции только отводится память, а значение присваивается в ходе выполнения программы) (SECTION .bss). Для объявления инициированных данных в секции .data используются директивы DB, DW, DD, DQ и DT, которые резервируют память и указывают, какие значения должны храниться в этой памяти:

    DB (define byte) — определяет переменную размером в 1 байт;
    DW (define word) — определяет переменную размеров в 2 байта (слово);
    DD (define double word) — определяет переменную размером в 4 байта (двойное слово);
    DQ (define quad word) — определяет переменную размером в 8 байт (учетве- рённое слово);
    DT (define ten bytes) — определяет переменную размером в 10 байт. Директивы используются для объявления простых переменных и для объявления массивов. Для определения строк принято использовать директиву DB в связи с особенностями хранения данных в оперативной памяти. Инструкция языка ассемблера mov предназначена для дублирования данных источника в приёмнике.

# Выполнение лабораторной работы

## Основы работы c Midnight Commander

Открываю Midnight Commander и перехожу в каталог созданный при выполнении лабораторной работы №4 (рис. [-@fig:001]).

![Midnight Commander](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab05/report/image/Вставленное изображение.png){#fig:001}

Создаю файл lab5-1.asm, с помощью функциональной клавиши F4 открываю файл для редактирования и ввожу текст программы из листинга 5.1 (рис. [-@fig:002]).

![Текст программы из листинга 5.1](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab05/report/image/Вставленное изображение (2).png){#fig:002}

С помощью функциональной клавиши F3 открываю файл lab5-1.asm для просмотра и убеждаюсь, что файл содержит текст программы (рис. [-@fig:003]).

![Текст программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab05/report/image/Вставленное изображение (3).png){#fig:003}

Транслирую текст программы lab5-1.asm в объектный файл, выполняю компоновку объектного файла и запускаю исполняемый файл (рис. [-@fig:004]).

![Проверка работы программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab05/report/image/Вставленное изображение (4).png){#fig:004}

## Подключение внешнего файла in_out.asm

Создаю копию файла lab5-1.asm с именем lab5-2.asm (рис. [-@fig:005]).

![Файл lab5-2.asm](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab05/report/image/Вставленное изображение (5).png){#fig:005}

В файле lab5-2.asm заменяю подпрограмму sprintLF на sprint и проверяю работу программы (рис. [-@fig:006]).

![Текст программы lab5-2.asm](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab05/report/image/Вставленное изображение (7).png){#fig:006}

![Проверка работы программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab05/report/image/Вставленное изображение (8).png){#fig:007}

Разница подпрограмм в том, что вторая вызывает ввод на той же строке.

Далее копирую файлы в локальный репозиторий и загружаю файлы на Github.

# Выводы

После выполнения данной лабораторной работы я приобрёл практические навыки работы в Midnight Commander, а также освоил инструкции языка ассемблера mov и int.

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
