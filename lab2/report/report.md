---
# Front matter
lang: ru-RU
title: "Лабораторная работа №2"
subtitle: "Информационная безопасность"
author: "Левкович Константин Анатольевич"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
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

1. Получение практических навыков работы в консоли с атрибутами файлов

2. Закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.


# Выполнение лабораторной работы

## Выполнение задания

Создаём новую учётную запись guest-f, используя команду useradd guest-f

После этого зададим пароль с помощью команды passwd guest-f, используя учетную запись администратора. (рис. -@fig:001)

![Создание учётной записи](image/1.jpg){ #fig:001 width=70% }

Входим в систему от имени пользователя guest-f и определяем директорию, в которой находимся, с помощью команды pwd. Сравнивая с приглашением командной строки, определяем сходство и факт, что это наша домашнаяя директория. 

Командой whoami уточняем имя пользователя - guest-f.

Уточним имя пользователя, его группу, а также группы, куда входит пользователь, командой id. Получаем результат 1002.

Далее сравним вывод id c приглашением командной строки, обнаружим, что имя пользователя повторяется. 

Просмотрим файл /etc/passwd командой cat /etc/passwd. (рис. -@fig:002)

![whoami](image/2.jpg){ #fig:002 width=70% }

Найдём в нём свою учётную запись. Определим uid пользователя. Определите gid пользователя. Сравним найденные значения с полученными в предыдущих пунктах - они одинаковые.

Определим существующие в системе директории командой ls -l /home/. 
Нам удалось получить список поддиректорий. У каждой из них установлены права на чтение, запись и выполнение только для самого пользователя.

Проверяем, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой: lsattr /home

Нам удалось увидеть расширенные атрибуты директории, но не удалось увидеть расширенные атрибуты директорий других пользователей.


Создадим в домашней директории поддиректорию dir1 командой mkdir dir1

Определим командами ls -l и lsattr, какие права доступа и расширенные атрибуты были выставлены на директорию dir1.


Снимем с директории dir1 все атрибуты командой chmod 000 dir1 и проверим с её помощью правильность выполнения команды ls -l. (рис. -@fig:003)

![Снятие аттрибутов](image/3.jpg){ #fig:003 width=70% }

Попытаемся создать в директории dir1 файл file1 командой echo "test" > /home/guest/dir1/file1, но получим отказ от выполнения, так как шагом ранее сняли все атрибуты с директории. Проверим, действительно ли файл не создался, с помощью команды ls -l /home/guest/dir1.


Заполним таблицу «Установленные права и разрешённые действия». (рис. -@fig:004)

![Права на действия](image/4.jpg){ #fig:004 width=100% }

Заполним таблицу «Минимальные права для совершения операций». (рис. -@fig:005)

![Минимальные права](image/5.jpg){ #fig:005 width=100% }

# Выводы

Получил практические навыки работы в консоли с атрибутами файлов, закрепил теоретические основы дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.