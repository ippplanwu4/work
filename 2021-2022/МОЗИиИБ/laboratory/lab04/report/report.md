---
# Титульный лист
title: |
    Отчёт по лабораторной работе №4.  
    Вычисление наибольшего общего делителя
author:
- "Студент: Лапшенкова Любовь Олеговна, 10322127633"
- "Группа: НФИмд-02-21"
- "Преподаватель: Кулябов Дмитрий Сергеевич,"
- "д-р.ф.-м.н., проф."
date: "Москва 2021"

# Общие опции
lang: ru-RU
toc-title: "Содержание"

# Библиография
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

# Конвертация в ПДФ
toc: true # Содержание
toc_depth: 2
lof: true # Список изображений
lot: true # Список таблиц
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt

## I18n
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
### Шрифты
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.8
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

## Misc options
indent: true
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

  - \usepackage{titling}
  - \setlength{\droptitle}{-9em}
  - \pretitle{\begin{center}
      \textbf{РОССИЙСКИЙ УНИВЕРСИТЕТ ДРУЖБЫ НАРОДОВ}\\
      \textbf{Факультет физико-математических и естественных наук}\\
      \textbf{Кафедра прикладной информатики и теории вероятностей}
      \vspace{9cm}
      \LARGE\\}
  - \posttitle{\vskip 1em \Large \emph{\textit{Дисциплина$:$ Математические основы защиты информации и информационной безопасности}} \end{center}}
  - \preauthor{\vskip 3em \begin{flushright} \large \begin{tabular}[t]{c}}
  - \postauthor{\end{tabular}\par\end{flushright} \vfill \vskip 5em}
---

# Цель работы

Целью данной лабораторной работы является ознакомление с алгоритмами вычисления наибольшего общего делителя, -- а так же реализация алгоритмов на произвольном языке программирования.

# Задание

Реализовать все рассмотренные в инструкции к лабораторной работе алгоритмы нахождения наибольшего общего делителя программно.

# Теоретическое введение

Рассмотрим, что такое наибольший общий делитель. Вспомним, что делитель – это число, на которое другое число делится без остатка.[@tutor:NOD] **Наибольшим общим делителем (НОД)** для двух целых чисел m и n называется наибольший из их общих делителей. Пример: для чисел 54 и 24 наибольший общий делитель равен 6. [@wiki:NOD]

**Алгоритм Евклида** — один из наиболее ранних численных алгоритмов в истории. Название было дано в честь греческого математика Евклида, который впервые дал ему описание в книгах «Начала». Изначально назывался «взаимным вычитанием», так как его принцип заключался в последовательном вычитании из большего числа меньшего, пока в результате не получится ноль. Сегодня чаще используется взятие остатка от деления вместо вычитания, но суть метода сохранилась.[@fenix:Evklid]

Алгоритм представлен в следующей блок-схеме:[@young:Evklid]

![Блок-схема алгоритма Евклида](image/ev1.png){ #fig:001 width=70% }

**Бинарный алгоритм Евклида** — метод нахождения наибольшего общего делителя двух целых чисел. Данный алгоритм "быстрее" обычного алгоритма Евклида, т.к. вместо медленных операций деления и умножения используются сдвиги. Возможно, алгоритм был известен еще в Китае 1-го века, но опубликован был лишь в 1967 году израильским физиком и программистом Джозефом Стайном.[@wiki:bie]

Алгоритм реализации алгоритма достаточно хорошо раскрыт в описании лабораторной работы, представленном на ТУИС.

Расширенные алгоритмы основаны на "уменьшенной версии" алгоритмов. Подробное описание представлено в описании лабораторной работы, представленном на ТУИС.

# Выполнение лабораторной работы

**Примечание:** комментарии по коду представлены на скриншотах к каждому из проделанных заданий.

В соответствии с заданием, были написаны программы реализации алгоритмов нахождения наибольшего общего делителя.
Нами были рассмотрены следующие алгоритмы:
1. Алгоритм Евклида;
2. Бинарный алгоритм Евклида;
3. Расширенный алгоритм Евклида;
4. Расширенный бинарный алгоритм Евклида.

Программный код и результаты выполнения программ представлен ниже.

## Алгоритм Евклида

![Входные данные для реализации алгоритмов по нахождению НОД](image/1.png){ #fig:002 width=70% }

![Реализация алгоритма Евклида для нахождения НОД](image/2.png){ #fig:003 width=70% }

Результаты выполнения программы представлены ниже (см. рис. [-@fig:004]).

![Результат реализации алгоритма Евклида для нахождения НОД](image/r1.png){ #fig:004 width=70% }

## Бинарный алгоритм Евклида. 1 способ

![1 часть программного кода реализации бинарного алгоритма Евклида 1 способом для нахождения НОД](image/3.png){ #fig:005 width=70% }

![2 часть программного кода реализации бинарного алгоритма Евклида 1 способом для нахождения НОД](image/4.png){ #fig:006 width=70% }

Результаты выполнения программы представлены ниже (см. рис. [-@fig:007]).

![Результат реализации бинарного алгоритма Евклида для нахождения НОД (1 способ)](image/r2.png){ #fig:007 width=70% }

## Бинарный алгоритм Евклида. 2 способ

![1 часть программного кода реализации бинарного алгоритма Евклида 2 способом для нахождения НОД](image/5.png){ #fig:008 width=70% }

![2 часть программного кода реализации бинарного алгоритма Евклида 2 способом для нахождения НОД](image/6.png){ #fig:009 width=70% }

Результаты выполнения программы представлены ниже (см. рис. [-@fig:010]).

![Результат реализации бинарного алгоритма Евклида для нахождения НОД (2 способ)](image/r3.png){ #fig:010 width=70% }

## Расширенный алгоритм Евклида

![1 часть программного кода реализации расширенного алгоритма Евклида для нахождения НОД](image/7.png){ #fig:011 width=70% }

![2 часть программного кода реализации расширенного алгоритма Евклида для нахождения НОД](image/8.png){ #fig:012 width=70% }

Результаты выполнения программы представлены ниже (см. рис. [-@fig:013]).

![Результат реализации расширенного алгоритма Евклида для нахождения НОД](image/r4.png){ #fig:013 width=70% }

## Расширенный бинарный алгоритм Евклида

![1 часть программного кода реализации расширенного бинарного алгоритма Евклида для нахождения НОД](image/9.png){ #fig:014 width=60% }

![2 часть программного кода реализации расширенного бинарного алгоритма Евклида для нахождения НОД](image/10.png){ #fig:015 width=60% }

![3 часть программного кода реализации расширенного бинарного алгоритма Евклида для нахождения НОД](image/11.png){ #fig:016 width=60% }

Результаты выполнения программы представлены ниже (см. рис. [-@fig:017]).

![Результат реализации расширенного бинарного алгоритма Евклида для нахождения НОД](image/r5.png){ #fig:017 width=70% }

# Выводы

Таким образом, была достигнута цель, поставленная в начале лабораторной работы: я ознакомилась с алгоритмами вычисления наибольшего общего делителя, -- а так же реализовала данные алгоритмы на языке программирования Python 3.

# Список литературы{.unnumbered}

::: {#refs}
:::
