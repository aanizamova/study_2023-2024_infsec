---
## Front matter
title: "Отчет по лабораторной работе №5"
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

Изучение механизмов изменения идентификаторов, применения
SetUID- и Sticky-битов. Получение практических навыков работы в консоли с дополнительными атрибутами. Рассмотрение работы механизма
смены идентификатора процессов пользователей, а также влияние бита
Sticky на запись и удаление файлов.

# Выполнение
## Создание программы

1. Войдем в систему от имени пользователя guest (рис.1)  
  
  ![Рис. 1]( img/1.png )  
  
2. Создадим программу simpleid.c (рис.2)  
  
  ![Рис. 2]( img/2.png )  
    
3. Скомплилируем программу и убедимся, что файл программы создан (рис.3)  
  
4. Выполним программу simpleid (рис.3)  

5. Выполним системную программу id
и сравним полученный результат с данными предыдущего пункта задания (рис.3)  
  
  ![Рис. 3]( img/3-5.png )  
      
6. Усложним программу, добавив вывод действительных идентификаторов. Получившуюся программу назовем simpleid2.c (рис.4)  
  
  ![Рис. 4]( img/6.png )  
        
7. Скомпилируем и запустим simpleid2.c (рис.5)  

8. От имени суперпользователя выполним заданные команды (рис.5)  

9. Используем sudo или повысим временно свои права с помощью su (рис.5)  
  
  ![Рис. 5]( img/7-9.png )  
        
10. Выполним проверку правильности установки новых атрибутов и смены
владельца файла simpleid2 (рис.6)  

11. Запустим simpleid2 и id. Сравним результаты. (рис.6)  
  
  ![Рис. 6]( img/10-11.png )  

12. Проделаем то же самое относительно SetGID-бита (рис.7)  
  
  ![Рис. 7]( img/12.png )  

13. Создадим программу readfile.c (рис.8)  
  
  ![Рис. 8]( img/13.png )  

14. Откомпилируем её (рис.9)  

15. Сменим владельца у файла readfile.c и изменим права так, чтобы только суперпользователь (root) мог прочитать его, a guest не мог (рис.9)  

16. Проверим, что пользователь guest не может прочитать файл readfile.c (рис.9)  
  
  ![Рис. 9]( img/14-16.png )  

17. Сменим у программы readfile владельца и установите SetU’D-бит (рис.10)  

18. Проверим, может ли программа readfile прочитать файл readfile.c (рис.10)  
  
  ![Рис. 10]( img/17-18.png )    

19. Проверим, может ли программа readfile прочитать файл /etc/shadow (рис.11)  
  
  ![Рис. 11]( img/19.png )  
  
## Исследование Sticky-бита

1. Выясним, установлен ли атрибут Sticky на директории /tmp (рис.12)  
  

2. От имени пользователя guest создадим файл file01.txt в директории /tmp
со словом test (рис.12)  

3. Просмотрим атрибуты у только что созданного файла и разрешим чтение и запись для категории пользователей «все остальные» (рис.12)  
  
  ![Рис. 12]( img/1-3.png )    

4. От пользователя guest2 (не являющегося владельцем) попробуем прочитать файл /tmp/file01.txt (рис.13)  

5. От пользователя guest2 попробуем дозаписать в файл
/tmp/file01.txt слово test2. Выполнить операцию не удалось (рис.13)  

6. Проверим содержимое файла командой (рис.13)  
  
  ![Рис. 13]( img/4-6.png )  

7. От пользователя guest2 попробуем записать в файл /tmp/file01.txt
слово test3, стерев при этом всю имеющуюся в файле информацию. Выполнить операцию не удалось (рис.14)  

8. Проверим содержимое файла командой (рис.14)  

9. От пользователя guest2 попробуем удалить файл /tmp/file01.txt. Удалить файл не удалось (рис.14)  
  
  ![Рис. 14]( img/7-99.png )  

10. Повысим свои права до суперпользователя и выполним после этого команду, снимающую атрибут t (Sticky-бит) с директории /tmp (рис.15)  

11. Покинем режим суперпользователя (рис.15)  
  
  ![Рис. 15]( img/10-111.png )  

12. От пользователя guest2 проверим, что атрибута t у директории /tmp
нет (рис.16)  

13. Повторим предыдущие шаги. Удалось удалить файл (рис.16)  

14. удалить файл от имени пользователя, не являющегося
его владельцем удалось. (рис.16)  
  
  ![Рис. 16]( img/12-14.png )  

15. Повысим свои права до суперпользователя и вернем атрибут t на директорию /tmp (рис.17)  
  
  ![Рис. 17]( img/15.png )  
  
  
# Вывод

Мы изучили механизмы изменения идентификаторов, применения
SetUID- и Sticky-битов. Получили практические навыки работы в консоли с дополнительными атрибутами. Рассмотрели работы механизма
смены идентификатора процессов пользователей, а также влияние бита
Sticky на запись и удаление файлов.