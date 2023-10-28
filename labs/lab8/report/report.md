---
## Front matter
title: "Отчет по лабораторной работе №8"
subtitle: "Элементы
криптографии. Шифрование (кодирование)
различных исходных текстов одним ключом"
author: "Низамова Альфия Айдаровна"

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

Освоить на практике применение режима однократного гаммирования на примере кодирования различных исходных текстов одним ключом.

# Выполнение

Задание:  
Два текста кодируются одним ключом (однократное гаммирование). Требуется
не зная ключа и не стремясь его определить, прочитать оба текста. Необходимо
разработать приложение, позволяющее шифровать и дешифровать тексты P1 и
P2 в режиме однократного гаммирования. Приложение должно определить вид
шифротекстов C1 и C2 обоих текстов P1 и P2 при известном ключе;
Необходимо определить и выразить аналитически способ, при котором злоумышленник может прочитать оба текста, не зная ключа и не стремясь его определить.

Для написания программы использовала язык Python.  
Для начала импортировала необходимые библиотеки и задала две исходные строки равной длины(рис.1)

![Рис. 1]( img/1.png )

Написала функцию, которая определяет вид шифротекстов обеих строк при
известном ключе(рис.2)

![Рис. 2]( img/2.png )


Вывод первой функции(рис.3)   

![Рис. 3]( img/3.png )

Написала функцию, которая при известных двух шифротекстах и одном
открытом тексте находит вид второго открытого текста без ключа (рис.4)

![Рис. 4]( img/4.png )

Вывод второй функции(рис.5)   

![Рис. 5]( img/5.png )

  
# Вывод

В ходе лабораторной работы мне удалось освоить на практике применение режима однократного гаммирования на примере кодирования различных исходных
текстов одним ключом.