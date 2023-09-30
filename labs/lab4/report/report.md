---
## Front matter
title: "Отчет по лабораторной работе №4"
subtitle: "Дискреционное разграничение прав в Linux. Расширенные атрибуты"
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
Получение практических навыков работы в консоли с расширенными
атрибутами файлов

# Выполнение
От имени пользователя guest определили расширенные атрибуты файла
/home/guest/dir1/file1  
  
Установим на файл file1 права, разрешающие чтение и запись для владельца файла  

Попробовали установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest. В ответ мы получили отказ от выполнения операции.  
  
  ![Рис. 1]( img/1-3.png )  
  
Повысили свои права с помощью команды su. Попробовали установить расширенный атрибут a на файл /home/guest/dir1/file1 от имени суперпользователя  

От пользователя guest проверили правильность установления атрибута  

Попытались выполнить дозапись в файл file1 слова «test»  
После этого выполнили чтение файла file1   Слово test не было записано в file1.  
  
  ![Рис. 2]( img/4-6.png )  
  
Попробовали удалить файл file1. Удалось.  
Попробовали переименовать файл. Не удалось.    
  
  ![Рис. 3]( img/7-8.png )  
  
Попробовали установить на файл file1 права, запрещающие чтение и запись для владельца файла. Не удалось.

Сняли расширенный атрибут a с файла /home/guest/dirl/file1 от имени суперпользователя  

  ![Рис. 4]( img/8-9.png ) 

Повторили операции, которые нам ранее не удавалось выполнить. Все получилось.  
  
  ![Рис. 5]( img/9.png )  
  
Повторили наши действия по шагам, заменив атрибут «a» атрибутом «i».
Не удалось дозаписать информацию в файл, переименовать его и поменять атрибуты.
  
  ![Рис. 6]( img/10.png )  
  
# Вывод

Мы получили практические навыки работы в консоли с расширенными атрибутами файлов
