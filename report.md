---
title: "Лабораторная работа № 4. Дискреционное разграничение прав в Linux. Расширенные атрибуты"
author: [Радикорский Павел Михайлович, НФИбд-03-18]
institute: "RUDN University, Moscow, Russian Federation"
date: "30.10.2021"
keywords: [Безопасность, Лабораторная]
lang: "ru"
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
fontsize: 12pt
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: Consolas
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
titlepage: true
titlepage-text-color: "000000"
titlepage-rule-color: "000000"
titlepage-rule-height: 0
listings-no-page-break: true
indent: true
header-includes:
  - \usepackage{sectsty}
  - \sectionfont{\clearpage}
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
...

# Цели и задачи

**Цель:** Получение практических навыков работы в консоли с расширенными атрибутами файлов

# Выполнение

От имени пользователя guest определили расширенные атрибуты файла /home/guest/dir1/file1 командой
lsattr /home/guest/dir1/file1, изменили права на файл file1 командой chmod 600 file1
    
![chmod 600](image/1.png){ #fig:001 width=70% }

Попробовали установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest:
chattr +a /home/guest/dir1/file1. В ответ получили отказ от выполнения операции, повторили от имени суперпользователя, проверили правильность установления атрибута
    
![chattr +a](image/2.png){ #fig:001 width=70% }

Пробуем записать данные и прочитать их в file1, удалить файл, получаем отказ

![echo и cat](image/3.png){ #fig:001 width=70% }

Пробуем переименовать файл, изменить права, также получаем отказ

![rm, mv](image/4.png){ #fig:001 width=70% }

Снимаем атрибут a, пробуем записать и прочитать файл, выполняется успешно

![chattr -a](image/5.png){ #fig:001 width=70% }

Пробуем остальные операции, выполняются успешно

![chattr -a](image/6.png){ #fig:001 width=70% }

Добавляем атрибут i, проводим те же операции

![chattr +i](image/7.png){ #fig:001 width=70% }

Попытка записи завершается отказом, попытка чтения успехом

![echo, cat](image/8.png){ #fig:001 width=70% }

Остальные операции также увенчались отказом

![Остальные операции](image/9.png){ #fig:001 width=70% }

#  Выводы

В результате выполнения работы я повысила свои навыки использования интерфейса командой строки (CLI), познакомилась на примерах с тем, как используются основные и расширенные атрибуты при разграничении доступа. Имела возможность связать теорию дискреционного разделения доступа (дискреционная политика безопасности) с её реализацией на практике в ОС Linux. Составила наглядные таблицы, поясняющие какие операции возможны при тех или иных установленных правах. Опробовала действие на практике раёсширенных атрибутов «а» и «i».