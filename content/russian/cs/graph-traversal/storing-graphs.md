---
title: Хранение графов
weight: 1
authors:
- Глеб Лобанов
editors:
- Сергей Слотин
---

# Хранение графа в программе

Чаще всего в задачах по программмированию вершины графа - это числа от
$0$ до $N-1$, чтобы удобно было обращаться к ним как к индексам в разных
массивах.

Также чаще всего вам дают считать граф как просто список всех рёбер в
нем (но не всегда, конечно). Как оптимально считать и сохранить граф?
Есть 3 способа.

Для графа существуют несколько основных способов хранения:

## Матрица смежности

Давайте хранить двумерную матрицу $A_{nn}$, где для данного графа G
верно, что если $A_{ij}$ = 1, то две вершины $i$ и $j$ являются
смежными, иначе вершины $i$ и $j$ смежными не являются.

[400px](Файл:Graph-sample.png "wikilink")

[400px](Файл:Adj-matrix.png "wikilink")
[400px](Файл:Adj-list.png "wikilink")
[300px](Файл:Edge-list.png "wikilink")

Мы храним для каждой из $N$ вершин информацию, есть ли ребро в другие
вершины, то есть суммарно мы храним $N^2$ ячеек, а следовательно
асимптотика по памяти - $O(N^2)$.

## Список смежности

Давайте для каждой из $N$ вершин хранить все смежные с ней, для этого
нам потребуется любая динамическая структура, например vector в с++.

``` C++ numberLines
// как сделать список по матрице
vector<vector<int> > g(n);
for (int i = 0; i < n; ++i){
    for (int j = 0;j < n;++j){
        cin >> a;
        if (a) g[i].push_back(j);
    }
}
// список по списку ребер
cin >> n >> m;
vector<vector<int> > g(n);
for (int i = 0; i < m; ++i){
  cin >> v1 >> v2;
  g[v1].push_back(v2);
  g[v2].push_back(v1);
}
```

Здесь асимптотика по памяти и времени считывания - $O(N + M)$, так как
мы храним для каждой вершины, куда есть ребра, то есть $2 M$ ребер, а
также суммарно $N$ векторов.

Плотные графы, имеющие большое количество ребер следует хранить при
помощи матрицы смежности, а разреженные графы, имеющие малое
количество ребер, оптимальнее при помощи списка.

## Список рёбер

Иногда граф явно вообще не требуется, а хватает хранить просто список
ребер, который нам дают на вход.

Заметьте, что все эти способы обобщаются на случай ориентированных
графов - при этом матрица смежности становится неориентированной:
если есть ребро из вершины $i$ в вершину $j$, то сделаем $A_{ij} = 1$,
а $A_{ji} = 0$, если только нет обратного ребра тоже. А в списке
смежности в ориентированном случае при считывании ребра $(u, v)$
будем добавлять только $v$ в список соседей $u$, но не наоборот.