---
## Front matter
title: "Отчёт по лабораторной работе №7"
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

Изучение команд условного и безусловного переходов. Приобретение навыков написания
программ с использованием переходов. Знакомство с назначением и структурой файла
листинга.

# Задание

1. Реализация переходов в NASM
2. Изучение структуры файлов листинга
3. Самостоятельное написание программ по материалам лабораторной работы

# Теоретическое введение

Для реализации ветвлений в ассемблере используются так называемые команды передачи
управления или команды перехода. Можно выделить 2 типа переходов:
• условный переход – выполнение или не выполнение перехода в определенную точку
программы в зависимости от проверки условия.
• безусловный переход – выполнение передачи управления в определенную точку про-
граммы без каких-либо условий.

# Выполнение лабораторной работы

## Реализация переходов в NASM

Создаю каталог для программ лабораторной работы №7, перехожу в него и создаю файл lab7-1.asm. (рис. [-@fig:001]).

![Создание каталога и файла lab7-1.asm](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/Вставленное изображение.png){#fig:001}

Ввожу в файл lab7-1.asm текст программы листинга 7.1. (рис. [-@fig:002]).

![Ввод текста в файл](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/Вставленное изображение (2).png){#fig:002}

Далее создаю исполняемый файл и запускаю его. (рис. [-@fig:003]).

![Создание исполняемого файла и запуск программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/Вставленное изображение (3).png){#fig:003}

Изменяю текст программы в соответствии с листингом 7.2. (рис. [-@fig:004]).

![Изменение программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/Вставленное изображение (10).png){#fig:004}

Проверяю правильность выполнения программы. (рис. [-@fig:005]).

![Проверка правильности выполнения программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/Вставленное изображение (11).png){#fig:005}

Изменяю текст программы таким образом, чтобы три сообщения выводились в обратном порядке. (рис. [-@fig:006]).

![Изменение текста программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/Вставленное изображение (4).png){#fig:006}

Проверяю правильность выполнения команд. (рис. [-@fig:007]).

![Проверка выполнения команд](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/Вставленное изображение (5).png){#fig:007}

Создаю файл lab7-2.asm и ввожу в него текст программы из листинга 7.3. (рис. [-@fig:008]).

![Ввод текста программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/Вставленное изображение (6).png){#fig:008}

Создаю исполняемый файл и проверяю его работу для разных значений B. (рис. [-@fig:009]).

![Создание исполняемого файла и проверка его работы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/Вставленное изображение (7).png){#fig:009}

Создаю файл листинга для программы из файла lab7-2.asm и открываю его. (рис. [-@fig:010]).

![Создание файла и его просмотр](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/Вставленное изображение (12).png){#fig:010}

Открываю файл с программой lab7-2.asm и в любой инструкции с двумя операндами удаляю один операнд. (рис. [-@fig:011]).

![Удаление операнда](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/Вставленное изображение (8).png){#fig:011}

Пытаюсь выполнить трансляцию файла листинга и получаю ошибку. (рис. [-@fig:012]).

![Выполнение трансляции файла](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/Вставленное изображение (9).png){#fig:012}

## Задания для самостоятельной работы

Пишу программу нахождения наименьшой из 3 целочисленных переменных 𝑎,𝑏 и с. (рис. [-@fig:013]).

![Программа](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/1.png){#fig:013}

Проверяю правильность работы программы взяв числа из 8 варианта. (рис. [-@fig:014]).

![Проверка](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab07/Report/image/2.png){#fig:014}

После этого отправляю файлы на github

# Выводы

После выполнения лабораторной работы, я изучил команды условных и безусловных переходов, а также приобрел навыки написания программ с использованием перходов, познакомился с назначением и структурой файлов листинга.

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
