---
title: Сведение игр к ниму
weight: 7
---

## Задача

Есть лестница с $n$ ступеньками (занумерованными от 1 до $n$), на $i$-ой
ступеньке лежит $a_i$ монет. За один ход разрешается переместить
некоторое ненулевое число монет с $i$-ой на $i-1$-ую ступеньку.
Проигрывает тот, кто не может сделать хода.

## Решение

Возьмем ним только с четными номерами ступенек($a_{2}, a_{4},
\\dots$).

Есть два варианта хода :

Мы можем положить со ступеньки $i$ с четным номером на ступеньку $i - 1$
с нечетным номером $x$ камней, но такое действие эквивалентно действию в
ниме(забрать из $i$-ой кучки $x$ камней).

Мы можем положить со ступеньки $i$ с нечетным номером на ступеньку $i -
1$ с четным номером $x$ камней, но такое действие эквивалентно действию
в ниме с прибавлением (прибавить к $i$-ой кучке $x$ камней), а
следовательно мы можем в победной стратегии на него ответить,
тем что заберем с $i - 1$ ступеньки $x$ камней, так как сумма
количества камней конечна, то и количество действий конечно, а
следовательно игра ациклична.

---

## Задача

Дан ним($n$ кучек размера $a_{1} \\dots a_{n}$, ход - взятие камней из
кучки), выигрывает игрок, который не может сделать ход.

## Подсказка

Пусть вам дана выигрышная стратегия в ним, можете ли вы ее как-нибудь
применить к ниму в поддавки.

## Решение

Отдельно рассмотрим случай, где все кучки - размера 1, в таком ниме
ответ обратен ниму в поддавки, так как единственный возможный ход -
взять всю кучку и кто выигрывает зависит только от четности количества
кучек.

Заметим, что в ниме в поддавки игра заканчивается на том, что остается
кучка размера 1, заметим, что существует оптимальная стратегия Нима,
где в конце мы получили сколько-то кучек размера 1, тогда вернемся к
последнему ходу, который привел нас к тому, что остались только кучки
размера 1(так как мы рассмотрели отдельно случай, когда все кучки из
одного камушка, то такой ход был). Сделаем теперь ход не до кучки
размера 1, а до кучки размера 0, так как мы поменяли четность
количества кучек размера 1, то мы и поменяли игрока, который
выигрывает, а следовательно мы научились выигрывать в ниме с
поддавками, если мы умеем выигрывать в обычном ниме.

---

## Условие

Есть клетчатая полоска $1 \\times n$, на которой расположены $k$ монет:
$i$-ая монета находится в $a_i$-ой клетке. За один ход игрок может
взять какую-то монету и подвинуть её влево на произвольное число
клеток, но так, чтобы она не вылезла за пределы полоски, запрещается
перепрыгивать другие монеты (или даже ставить две монеты в одну
клетку). Проигрывает тот, кто не может сделать ход.

## Решение

Первым делом добавим фиктивную монетку, стоящую в самой крайней точке.

Можно заметить, что эта игра эквивалента [Лесенка](Лесенка "wikilink"),
а именно давайте посчитаем расстояние между соседними монетками, будем
считать, что расстояние от $i$-ой до $i+1$-й монетки в текущей задачи -
количество монет на $i + 1$-ой ступеньке в оригинальной задаче.

Тогда задача сводится к переместить все монетки на первую ступеньку.