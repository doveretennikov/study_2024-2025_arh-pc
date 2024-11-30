---
## Front matter
title: "Отчёт по лабораторной работе №8"
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

Приобретение навыков написания программ с использованием циклов и обработкой
аргументов командной строки.

# Задание


1. Реализация циклов в NASM
2. Обработка аргументов командной строки
3. Самостоятельное написание программы по материалам лабораторной работы

# Теоретическое введение

	Стек — это структура данных, организованная по принципу LIFO («Last In — First Out»
или «последним пришёл — первым ушёл»). Стек является частью архитектуры процессора и
реализован на аппаратном уровне. Для работы со стеком в процессоре есть специальные
регистры (ss, bp, sp) и команды.
	Основной функцией стека является функция сохранения адресов возврата и передачи
аргументов при вызове процедур. Кроме того, в нём выделяется память для локальных
переменных и могут временно храниться значения регистров.

# Выполнение лабораторной работы

## Реализация циклов в NASM

Создаю каталог для программ лабораторной работы №8 и создаю файл lab8-1.asm (рис. [-@fig:001]).

![Создание каталога и файла](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение.png){#fig:001}

Ввожу в файл lab8-1.asm текст программы из листинга 8.1 (рис. [-@fig:002]).

![Ввод текста программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение (2).png){#fig:002}

Проверяю работу файла (рис. [-@fig:003]).

![Проверка](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение (3).png){#fig:003}

Изменяю текст программы добавив изменение знечения регистра ecx в цикле (рис. [-@fig:004]).

![Изменение знечения регистра ecx в цикле](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение (4).png){#fig:004}

Проверяю работу программы (рис. [-@fig:005]).

![Проверка](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение (5).png){#fig:005}

Так как регистр ecx на каждой итерации уменьшается на 2, то и количество итераций уменьшается в 2 раза.

Вношу изменения в текст программы добавив команды push и pop (рис. [-@fig:006]).

![Изменения программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение (6).png){#fig:006}

Запускаю измененную программу (рис. [-@fig:007]).

![Запуск программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение (7).png){#fig:007}

В данном случае теперь число проходов цикла соответствует значению N введенному с клавиатуры, но произошло смещение чисел на -1.

## Обработка аргументов командной строки

Создаю файл lab8-2.asm и ввожу в него текст программы из листинга 8.2 (рис. [-@fig:008]).

![Ввод программы из листинга](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение (8).png){#fig:008}

Создаю исполняемый файл и запускаю его, указав аргументы (рис. [-@fig:009]).

![Запуск программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение (9).png){#fig:009}

Программой было обработано столько же аргументов, сколько мы и ввели.

Создаю новый файл и ввожу в него текст программы из листинга 8.3 (рис. [-@fig:010]).

![Ввод программы в файл](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение (10).png){#fig:010}

Создаю исполняемый файл и запускаю его, указав аргументы из примера (рис. [-@fig:011]).

![Создание исполняемого файла и его запуск](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение (13).png){#fig:011}

Изменяю текст программы из листинга 8.3 для вычисления произведения аргументов командной строки (рис. [-@fig:012]).

![Изменение программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение (11).png){#fig:012}

Проверяю корректность работы программы (рис. [-@fig:013]).

![Проверка](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/Вставленное изображение (12).png){#fig:013}

## Задание для самостоятельной работы

Напишите программу, которая находит сумму значений функции 𝑓(𝑥), так как у меня 8 вариант пишу программу для функции f(x) = 7 + 2x (рис. [-@fig:014]).

![Текст программы](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/1.png){#fig:014}

Далле проверяю корректность работы программы (рис. [-@fig:015]).

![Проверка](/home/doveretennikov/work/study/2024-2025/Архитектура компьютера/arch-pc/labs/lab08/Report/image/2.png){#fig:015}

После этого отправляю файлы на github

# Выводы

После выполнения данной лабораторной работы, я приобрел навыки написания программ с использованием циклов, а также научился обрабатывать аргументы командной строки.

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
16. Таненбаум Э., Бос Х. Современные операционные системы. — 4-е изд. — СПб. : Питер, 2015. — 1120 с. — (Классика Computer Science).
