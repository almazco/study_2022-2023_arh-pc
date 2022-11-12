---
## Front matter
title: "Отчёт по лабораторной работе №5"
subtitle: "Создание и
процесс обработки программ на языке
ассемблера NASM"
author: "Зиязетдинов Алмаз Радикович"

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
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
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
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Освоение процедуры компиляции и сборки программ, написанных на ассемблере NASM.

# Выполнение лабораторной работы

Создайте каталог для работы с программами на языке ассемблера NASM:
mkdir ~/work/arch-pc/lab05
Перейдите в созданный каталог
cd ~/work/arch-pc/lab05
Создайте текстовый файл с именем hello.asm
touch hello.asm 

откройте этот файл с помощью любого текстового редактора, например, gedit
gedit hello.asm
 и введу в него следующий текст (рис. [-@fig:001])

![Редактирование файла hello.asm](image/1.png){ #fig:001 width=70% }

NASM превращает текст программы в объектный код. Например, для компиляции приведённого выше текста программы «Hello World» необходимо написать:

Проверьте, что объектный файл был создан(рис. [-@fig:002])

![Создание файлов .asm](image/2.png){ #fig:002 width=70% }

Выполните следующую команду:
nasm -o obj.o -f elf -g -l list.lst hello.asm


С помощью команды ls проверьте, что файлы были созданы(рис. [-@fig:003])

![Проверка файлов](image/3.png){ #fig:003 width=70% }

объектный файл необходимо передать на обработку компоновщику:
ld -m elf_i386 hello.o -o hello
(рис. [-@fig:004])

![Проверка файлов](image/4.png){ #fig:004 width=70% }


Выполните следующую команду:
ld -m elf_i386 obj.o -o main


Запустить на выполнение созданный исполняемый файл, находящийся в
текущем каталоге, можно, набрав в командной строке:
./hello
(рис. [-@fig:005])

![Запуск команды](image/5.png){ #fig:005 width=70% }


Задание для самостоятельной работы
В каталоге ~/work/arch-pc/lab05 с помощью команды cp создайте копию
файла hello.asm с именем lab5.asm
(рис. [-@fig:006])

![Проверка файлов](image/6.png){ #fig:006 width=70% }

С помощью любого текстового редактора внесите изменения в текст программы в файле lab5.asm так, чтобы вместо Hello world! на экран выводилась строка с вашими фамилией и именем.
(рис. [-@fig:007])

![Изменить на ФИО](image/7.png){ #fig:007 width=70% }

Оттранслируйте полученный текст программы lab5.asm в объектный файл. Выполните компоновку объектного файла и запустите получившийся исполняемый файл.
(рис. [-@fig:008])

![Вывод Имени и Фамилии](image/8.png){ #fig:008 width=70% }

Скопируйте файлы hello.asm и lab5.asm в Ваш локальный репозиторий в каталог ~/work/study/2022-2023/"Архитектура компьютера"/archpc/labs/lab05/. Загрузите файлы на Github.

# Выводы

Мы освоили процедуры компиляции и сборки программ, написанных на ассемблере NASM.

