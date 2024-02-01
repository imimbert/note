 图（Graph）是一种复杂的非线性结构，它可以描述数据间的关系，被广泛使用。

图 G 由两个集合 V 和 E 组成，记为 ![img](https://img-blog.csdnimg.cn/img_convert/ccc7d90277a148b990068bd59a37e358.png)![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)编辑。V是顶点的有穷非空集合，E是边的集合。通常，也将 G 的顶点集和边集表示为 V(G) 和 E(G)。其中，E(G)可以是空集，如果它是空集，那么 G 只有顶点。

# 图的定义和概念

有向图：边上有箭头，只能从箭头的引出的结点到被指向的结点，不能逆着箭头走。

无向图：边上无箭头，可以随便走。

结点的度：无向图中与结点相连的边的数量。

结点的入度：有向图中以结点为终点的边的数量。

结点的出度：有向图中以结点为起点的边的数量。

权值：可以理解为边的长度。

连通：如果结点 U 和 V 之间通过若干个边和结点能从 U 到达 V，则称 U 和 V 连通。

回路：起点和终点相同的路径。

完全图：一个 n 阶的完全无向图含有 n*(n-1)/2 条边，一个 n 阶的完全有向图含有 n*(n-1) 条边。

稠密图：一个边数接近完全图的图。

稀疏图：一个边数远少于完全图的图。

强连通分量：有向图中任意两点都连通的最大子图。特殊的，一个点也算一个强连通分量。

# 图的存储结构

二维数组邻接矩阵存储

定义 int G[101][101];

G[i][j] 的值，表示点 i 到点 j 的边的权值，定义如下，

G[i][j]{1或权值，0或无穷

# 深度优先和广度优先遍历

从图中某一顶点出发，系统的访问图中所有顶点，并且每个顶点只被访问一次，这种操作叫做图的遍历。为了不重复访问，我们使用一个数组 visit[] ，被访问过就变成 true，反之 false。这两种方法（广度和深度优先遍历）时间复杂度都是 O(n*n)。

## 深度优先遍历

深度优先遍历和深度优先搜索相似，它是先访问一个点，再访问与这个点相连的所有点，当这个点所有相连的点访问完，再退回下一个点。

## 广度优先遍历

它基本不用，和广度优先搜索相似，和深度优先遍历相似，这里不讲解。

# 一笔画问题

如果一个图存在一笔画，则一笔画的路径叫做欧拉路，如果起点和终点相同，则这个路径叫欧拉回路。

奇点是与一个点相连的边数是奇数的点。我们有如下两个定理：

（1）存在欧拉路的条件：图是连通的，且有且只有两个奇点。

（2）存在欧拉回路的条件：图是联通的，且有0个奇点。

```cpp
#include<bits/stdc++.h>
using namespace std;
const int N=1000;
int p[N],q[N];
int n,m;
int sum=0,flag=0;
int find(int x)
{
    if(p[x]!=x) p[x]=find(p[x]);
    return p[x];
}
int main()
{
    cin>>n>>m;
    for(int i=1;i<=n;i++) p[i]=i;
    while(m--)
    {
        int a,b;
        cin>>a>>b;
        q[a]++;//由于是无向图需要把所有边加上
        q[b]++;
        a=find(a),b=find(b);
        if(a!=b) p[a]=b;
    }
    for(int i=1;i<=n;i++) 
        if(p[i]==i) sum++;
       if(sum==1)
       {
           for(int i=1;i<=n;i++)
           {
               if(q[i]%2!=0)
                   flag++;
           }
       }
     else {cout<<"N"<<endl;return 0;}
     if(flag==0 || flag==2) cout<<"Y"<<endl;//一笔画的规律（奇数点个数为0或者2）
     else cout<<"N"<<endl;
    return 0;
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

# 例题-图的遍历

## 图的遍历

### 题目描述

给出 N 个点，M条边的有向图，对于每个点 v，求 A(v) 表示从点 v 出发，能到达的编号最大的点。

### 输入格式

第 1 行 2 个整数 N,M，表示点数和边数。

接下来 M 行，每行 2 个整数 Ui,Vi，表示边 (Ui,Vi)。点用 1,2,.....,N 编号。

### 输出格式

一行 N 个整数 A(1),A(2),......,A(N)。

### 样例 #1

```cpp
4 3
1 2
2 4
4 3
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

#### 样例输入 #1

#### 样例输出 #1

```cpp
4 4 3 4
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)



按题目来每次考虑每个点可以到达点编号最大的点，不如考虑较大的点可以反向到达哪些点

循环从N到1，则每个点i能访问到的结点的A值都是i

每个点访问一次，这个A值就是最优的，因为之后如果再访问到这个结点那么答案肯定没当前大了

```cpp
#include <iostream>
#include <cstdio>
#include <vector>
using namespace std;

#define MAXL 100010

int N, M, A[MAXL];
vector<int> G[MAXL]; //vector存图 

void dfs(int x, int d) {
    if(A[x]) return; //访问过 
    A[x] = d;
    for(int i=0; i<G[x].size(); i++)
        dfs(G[x][i], d);
}

int main() {
    int u, v;
    scanf("%d%d", &N, &M);
    for(int i=1; i<=M; i++) {
        scanf("%d%d", &u, &v);
        G[v].push_back(u); //反向建边 
    }
    for(int i=N; i; i--) dfs(i, i); 
    for(int i=1; i<=N; i++) printf("%d ", A[i]);
    printf("\n");
    return 0;
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)