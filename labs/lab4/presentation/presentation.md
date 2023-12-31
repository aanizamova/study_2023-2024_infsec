---
## Front matter
lang: ru-RU
title: " Лабораторная работа №4"
author: |
   "Низамова Альфия Айдаровна. НФИбд-01-20"\inst{1}

institute: |
  \inst{1}Российский Университет Дружбы Народов

date: 23 сентября, 2023, Москва, Россия

## Formatting
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
toc: false
slide_level: 2
theme: metropolis
header-includes: 
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
aspectratio: 43
section-titles: true

---

# Цель работы

## Цель работы:

Получение практических навыков работы в консоли с расширенными
атрибутами файлов


# Ход лабораторной работы

## 1-2
От имени пользователя guest определили расширенные атрибуты файла
/home/guest/dir1/file1  
  
Установим на файл file1 права, разрешающие чтение и запись для владельца файла  
  
![Рис. 1]( img/1-3.png )
  
## 3
Попробовали установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest. В ответ мы получили отказ от выполнения операции. 
  
![Рис. 1]( img/1-3.png )  

## 4-5
Повысили свои права с помощью команды su. Попробовали установить расширенный атрибут a на файл /home/guest/dir1/file1 от имени суперпользователя  

От пользователя guest проверили правильность установления атрибута  
  
  ![Рис. 2]( img/4-6.png )

## 6
Попытались выполнить дозапись в файл file1 слова «test»  
После этого выполнили чтение файла file1   Слово test не было записано в file1.  
  
![Рис. 2]( img/4-6.png )

## 7
Попробовали удалить файл file1. Удалось.  
Попробовали переименовать файл. Не удалось.    
  
  ![Рис. 3]( img/7-8.png )
## 8-9
Попробовали установить на файл file1 права, запрещающие чтение и запись для владельца файла. Не удалось.

Сняли расширенный атрибут a с файла /home/guest/dirl/file1 от имени суперпользователя  

  ![Рис. 4]( img/8-9.png )  

## 9
Повторили операции, которые нам ранее не удавалось выполнить. Все получилось.  
  
  ![Рис. 5]( img/9.png )  

## 10
Повторили наши действия по шагам, заменив атрибут «a» атрибутом «i».
Не удалось дозаписать информацию в файл, переименовать его и поменять атрибуты.
  
  ![Рис. 6]( img/10.png )

# Выводы
Мы получили практические навыки работы в консоли с расширенными атрибутами файлов
