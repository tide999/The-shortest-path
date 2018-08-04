Dijkstra算法和Floyd算法
======================

# 一. 最短路径问题介绍

> 从图中的某个顶点出发到达另外一个顶点的所经过的边的权重和最小的一条路径，称为最短路径。解决最短路径问题的算法有Dijkstra算法和Floyd算法。

# 二. Dijkstra算法

## (一) 基本思想

> Dijkstra算法（单源点路径算法，要求：图中不存在负权值边），Dijkstra算法使用了广度优先搜索解决赋权有向图或者无向图的单源最短路径问题，算法最终得到一个最短路径树。 Dijkstra(迪杰斯特拉)算法是典型的最短路径路由算法，用于计算一个节点到其他所有节点的最短路径。主要特点是以起始点为中心向外层层扩展，直到扩展到终点为止。Dijkstra算法能得出最短路径的最优解，但由于它遍历计算的节点很多，所以效率低。

## (二)算法流程

> 1. 设置两个集合S和V。其中，S是已求出最短路径的顶点，V是没有求出最短路径的顶点，初始状态时，S中只有节点0———即起点，V中是节点1-n。设置最短路径数组dist[n+1]，dist代表起点0到节点1-n的最短距离，初始状态时，dist[i]为起点0到节点i的距离，当起点0与节点i有边连接时，dist[i]=边的权值，当起点0与节点i没有边连接时，dist[i]=无穷大。

> 2. 从V中寻找与S(S中最后一个节点)距离最短的节点k，将其加入S中，同时，从V中移除k

> 3. 以k为中间点，更新dist中各节点j的距离。如果: 起点0—>j(经过k)的距离 < 起点0—>j(不经过k)的距离即dist[j]，则dist[j]= 0—>j(经过k)的距离 = 0->k的距离即dist[k] + k->j的距离( <k,j>的权值 )

> 重复步骤2和3，直到所有节点都在S中。

## (三) 图解过程

> 如图1所示，求从A到F的最短路径。过程如下：

![image](https://github.com/ShaoQiBNU/The-shortest-path/blob/master/images/1.png)

> 设置集合S、V和dist，并初始化，如图1所示

> 遍历集合V中与A直接相邻的顶点，找出当前与A距离最短的顶点。发现： A-->B 6   A-->C 3，于是将C加入S，并将C从V中移除。以C为中间点，更新dist中各节点的距离如下：

```
节点  经过C的距离   不经过C的距离   dist
 B     3+2=5          6          5
 C       -            -          3
 D     3+3=6          ∞          6
 E     3+4=7          ∞          7
 F       ∞            ∞          ∞
```
![image](https://github.com/ShaoQiBNU/The-shortest-path/blob/master/images/2.png)

> 遍历集合V中与C直接相邻的顶点，找出当前与C距离最短的顶点。发现： C-->B 2   C-->D 3   C-->E 4，于是将B加入S，并将B从V中移除。以B为中间点，更新dist中各节点的距离如下：
```
节点  经过B的距离   不经过B的距离   dist
 B       -            -          5
 C       -            -          3
 D     6+5=11         6          6
 E       ∞            7          7
 F       ∞            ∞          ∞
```
![image](https://github.com/ShaoQiBNU/The-shortest-path/blob/master/images/3.png)

> 遍历集合V中与B直接相邻的顶点，找出当前与B距离最短的顶点。发现： B-->D 5 ，于是将D加入S，并将D从V中移除。以D为中间点，更新dist中各节点的距离如下：
```
节点  经过D的距离   不经过D的距离   dist
 B       -            -          5
 C       -            -          3
 D       -            -          6
 E     6+2=8          7          7
 F     6+3=9          ∞          9
```
![image](https://github.com/ShaoQiBNU/The-shortest-path/blob/master/images/4.png)


> 遍历集合V中与D直接相邻的顶点，找出当前与D距离最短的顶点。发现： D-->E 2  D-->F 3，于是将E加入S，并将E从V中移除。以E为中间点，更新dist中各节点的距离如下：
```
节点  经过E的距离   不经过E的距离   dist
 B       -            -          5
 C       -            -          3
 D       -            -          6
 E       -            -          7
 F     7+5=12         9          9
```
![image](https://github.com/ShaoQiBNU/The-shortest-path/blob/master/images/5.png)

> 遍历集合V中与E直接相邻的顶点，找出当前与E距离最短的顶点。发现： E-->F 5，于是将F加入S，并将F从V中移除。以F为中间点，更新dist中各节点的距离如下：
```
节点  经过E的距离   不经过E的距离   dist
 B       -            -          5
 C       -            -          3
 D       -            -          6
 E       -            -          7
 F       -            -          9
```
![image](https://github.com/ShaoQiBNU/The-shortest-path/blob/master/images/6.png)
# 三. Floyd算法




