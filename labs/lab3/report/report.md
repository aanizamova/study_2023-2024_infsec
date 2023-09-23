---
# Front matter
lang: ru-RU
title: "Отчёт по лабораторной работе №3"
subtitle: "Дискреционное разграничение прав в Linux. Два пользователя"
author: "Низамова Альфия Айдаровна"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы
Получение практических навыков работы в консоли с атрибутами файлов для групп пользователей

# Выполнение
В установленной операционной системе создадим учётную запись пользователя guest (использую учётную запись администратора)(рис.1)  
  
Зададим пароль для пользователя guest (использую учётную запись администратора)(рис.1)  
  
Аналогично создадим второго пользователя guest2(рис.1)  
  
![Рис. 1]( img/1-3.png )  
  
Добавим пользователя guest2 в группу guest(рис.2)  
  
![Рис. 2]( img/4.png )  
  
Осуществим вход в систему от двух пользователей на двух разных консолях: guest на первой консоли и guest2 на второй консоли(рис.3)  
  
Для обоих пользователей командой pwd определим директорию, в которой находимся.(рис.3)  
  
Уточним имя нашего пользователя, его группу, кто входит в неё
и к каким группам принадлежит он сам.(рис.3)  
  
Определим командами
*groups guest* и *groups guest2*, в какие группы входят пользователи guest и guest2.(рис.3)  
  
Сравним вывод команды groups с выводом команд
*id -Gn* и *id -G*.(рис.3)  
  
Сравним полученную информацию с содержимым файла /etc/group.(рис.3)
   
![Рис. 3]( img/5-8.png )  
  
От имени пользователя guest2 выполним регистрацию пользователя
guest2 в группе guest командой
*newgrp guest*(рис.4)  
  
От имени пользователя guest изменим права директории /home/guest,
разрешив все действия для пользователей группы:
*chmod g+rwx /home/guest*(рис.4)  
  
От имени пользователя guest снимем с директории /home/guest/dir1
все атрибуты командой
*chmod 000 dirl*(рис.4)  
  
![Рис. 4]( img/6-11.png )  
  
Меняя атрибуты у директории dir1 и файла file1 от имени пользователя guest и делая проверку от пользователя guest2(рис.5)  
  
![Рис. 5]( img/11.png )
  
Заполним табл.1,
определив опытным путём, какие операции разрешены, а какие нет. Если операция разрешена, в таблице знак «+», если не разрешена,
знак «-».(рис. 6)  
  
![Рис. 6]( img/t1.png )
  
На основании заполненной таблицы определим те или иные минимально необходимые права для выполнения пользователем guest2 операций
внутри директории dir1 и заполним табл.2(рис.7)  
  
![Рис. 7]( img/t2.png )

# Вывод
Мы получили практические навыки работы в консоли с атрибутами файлов для групп пользователей
