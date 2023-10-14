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

Развить навыки администрирования ОС Linux. Получить первое практическое знакомство с технологией SELinux1
.  
Проверить работу SELinx на практике совместно с веб-сервером
Apache.

# Выполнение
## Создание программы

1. Войдем в систему с полученными учётными данными и убедимся, что
SELinux работает в режиме enforcing политики targeted (рис.1)  

2. Обратимся с помощью браузера к веб-серверу, запущенному на
компьютере, и убедимся, что последний работает (рис.1)  

![Рис. 1]( img/1-2.png )

3. Найдем веб-сервер Apache в списке процессов, определим его контекст
безопасности. (рис.2)  

![Рис. 2]( img/3.png )

4. Посмотрим текущее состояние переключателей SELinux для Apache.
Многие из них находятся в положении «off» (рис.3)  

![Рис. 3]( img/4.png )

5. Посмотрим статистику по политике, также определим множество пользователей, ролей, типов (рис.4)  

![Рис. 4]( img/5.png )

6. Определим тип файлов и поддиректорий, находящихся в директории
*/var/www* (рис.5)  

![Рис. 5]( img/6.png )

7. Определим тип файлов, находящихся в директории */var/www/html* (рис.6)  

8. Определим круг пользователей, которым разрешено создание файлов в
директории */var/www/html* - только суперпользователь (рис.6)

9. Создадим от имени суперпользователя html-файл
*/var/www/html/test.html* (рис.6-7)  

![Рис. 6]( img/7-9.png )
![Рис. 7]( img/9.png )

10. Проверим контекст созданного файла. (рис.8)  

![Рис. 8]( img/10.png )
 
11. Обратимся к файлу через веб-сервер (рис.9)  

![Рис. 9]( img/11.png )

12. Изучим справку man httpd_selinux и выясним, какие контексты файлов определены для httpd. Выдало, что справки нет (рис.10)  

13. Изменим контекст файла */var/www/html/test.html* с
*httpd_sys_content_t* на *samba_share_t*.  
После этого проверим, что контекст поменялся (рис.10)  

![Рис. 10]( img/12-13.png )

14. Попробуем ещё раз получить доступ к файлу через веб-сервер, мы должны получить сообщение об ошибке (рис.11)  

![Рис. 11]( img/14.png )

15. Просмотрим log-файлы веб-сервера Apache. Также просмотрим системный лог-файл (рис.12)  

![Рис. 12]( img/15.png )

16. Попробуем запустить веб-сервер Apache на прослушивание ТСР-порта
81 (а не 80, как рекомендует IANA и прописано в /etc/services). Для
этого в файле */etc/httpd/httpd.conf* заменим строчку *Listen 80*
на *Listen 81* (рис.13)  

![Рис. 13]( img/16.png )

17. Выполним перезапуск веб-сервера Apache. (рис.14)  

18. Проанализируем лог-файлы.
Просмотрим файлы */var/log/http/error_log*,
*/var/log/http/access_log* и */var/log/audit/audit.log* и
выясним, в каких файлах появились записи. (рис.14)  

![Рис. 14]( img/17-18.png )

19. Выполним заданную в методичке команду.  
После этого проверим список портов. Убедимся, что порт 81 появился в списке (рис.15)  

20. Попробуем запустить веб-сервер Apache ещё раз (рис.15)  

![Рис. 15]( img/19-20.png )

21. Вернем контекст *httpd_sys_cоntent__t* к файлу */var/www/html/ test.html* (рис.16)    

22. Исправим обратно конфигурационный файл apache, вернув *Listen 80* (рис.16)  

![Рис. 16]( img/21-22.png )

23. Удалим привязку *http_port_t* к 81 порту и проверим, что порт 81 удалён (рис.17)  

24. Удалим файл */var/www/html/test.html* (рис.17)  

![Рис. 17]( img/23-24.png )

  
# Вывод

Мы развили навыки администрирования ОС Linux, а также получили первое практическое знакомство с технологией SELinux1.    
Проверили работу SELinx на практике совместно с веб-сервером Apache.