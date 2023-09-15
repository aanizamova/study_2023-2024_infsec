---
## Front matter
title: "Отчет по лабораторной работе №2"
author: "Низамова Альфия Айдаровна НФИбд-01-20"

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

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

# Выполнение лабораторной работы

1. В установленной при выполнении предыдущей лабораторной работы
операционной системе создала учётную запись пользователя guest (использую учётную запись администратора) (рис.1)

2. Задаю пароль для пользователя guest (использую учётную запись администратора) (рис.1)

![Рис. 1](image/1-2.png)

3. Вошла в систему от имени пользователя guest. (рис.2)

4. Определила директорию, в которой нахожусь, командой pwd. Сравнила её с приглашением командной строки. Она является домашней директорией. (рис.2)

5. Уточнила имя пользователя командой whoami.(рис.2)

6. Уточнила имя пользователя, его группу, а также группы, куда входит пользователь, командой id. Сравнила вывод id с выводом команды groups.(рис.2)

7. Сравнила полученную информацию об имени пользователя с данными,
выводимыми в приглашении командной строки.(рис.2)

8. Просмотрела файл /etc/passwd командой
cat /etc/passwd
Нашла в нём свою учётную запись(в самом конце). Определила uid пользователя(1001).
Определила gid пользователя(1001). Сравнила найденные значения с полученными в предыдущих пунктах(значения одинаковы).(рис.2)

![Рис. 2](image/3-8.png)

9. Определила существующие в системе директории командой
ls -l /home/
Нам удалось получить список поддиректорий директории /home.(рис.3)

10. Проверила, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой:
lsattr /home
Нам не удалось  увидеть расширенные атрибуты директории. (рис.3)

11. Создала в домашней директории поддиректорию dir1 командой
mkdir dir1
Определила командами ls -l и lsattr, какие права доступа и расширенные атрибуты были выставлены на директорию dir1. (рис.3 и рис.4)

![Рис. 3](image/9-11.png)

12. Сняла с директории dir1 все атрибуты командой
chmod 000 dir1
и проверила с её помощью правильность выполнения команды
ls -l (рис.4)

![Рис. 4](image/11-12.png)

13. Попыталась создать в директории dir1 файл file1 командой
echo "test" > /home/guest/dir1/file1
Т. к. мы сняли все атрибуты с директории в прошлом пункте, мы получили отказ в выполнении операции по созданию файла.
Файл не создался. Проверила командой
ls -l /home/guest/dir1
действительно ли файл file1 не находится внутри директории dir1. (рис.5)

![Рис. 5](image/13.png)

14. Заполнила таблицу «Установленные права и разрешённые действия», выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет.
Если операция разрешена, занесла в таблицу знак «+», если не разрешена, знак «-». (рис.6 и рис.7)

![Рис. 6](image/т1.png)
![Рис. 7](image/т2.png)

15. На основании заполненной таблицы определила те или иные минимально необходимые права для выполнения операций внутри директории
dir1, заполнила табл. (рис.8)

![Рис. 8](image/т3.png)


# Выводы

Мы получили практические навыки работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.