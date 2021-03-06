---
title: 2018SCAUCPC题解
date: 2018-04-14 17:30:59
tags: SCAUCPC
---
1. Unsolved Problem(132/137)

  签到题，求最小的未出现过的正整数。

2. Square Game(85/129)

  用n个小方格组成一个边长最长和最短的形状。  
  周长最大的形状，是n个横着排一行，边长 `(2 * n) + 2`  
  周长最小的形状，其中一条边是`sqrt(n)`，找到最小的x使得`x * sqrt(n) >=n` 答案是`2 * (x + sqrt(n))`

3. Let's go(11/16)

  模拟围棋吃棋过程，每次下棋之后把棋子周围异色的棋块搜索一次，如果一块棋没有外接的空位则把这块棋移除。注意下一个棋可以吃掉最多4块棋。

4. Lock(0/0)

  本题主要考察利用fft求每个密码串和原串匹配的代价，但是锁的每个位置得数字是循环的，不好直接构造卷积，考虑到数字一共只有四种，我们可以单独枚举每个数字来构造卷积方程。
  求出所有匹配的代价之后，剩下只需要一个简单的状态压缩dp即可。
  对于生锈位置的处理，只需要在卷积的时候把代价设成无穷大。

5. Effective Conversation(29/67)

  题意：给一个长度为m的序列，求一个最长的连续子序列，里面恰好包含k个数，并且至少有t对相邻不相同的数。
  用两个指针维护当前区间[L,R]，维护当前区间不同人数person，维护当前区间相邻不同数对turns, 如果当前person大于k则L往前移，否则R往前移。

6. Atelier Lydie & Soeur ~ Hmmm.. What shall we craft next(8/11)
  `dp[i][j]`表示第一行填了`i`个格子，第二行填了`j`个格子，最大权重是多少；转移枚举下一个方块，如果这个方块其中一条边是2吗，另一条边是x，那么可以转移到`dp[i + x][j + x]`，如果这个方块其中一条边是1，另一条边是x，那么可以转移到`dp[i][j + x]`和`dp[i + x][j]`，答案就是`max(dp[i][j])`，算法复杂度`O(T * n^3)`

7. Atelier Lydie & Suelle ~ Traveling in the unknown musterious world(2/2)

  首先用容斥把问题拆解成求`[1, 1]`到`[x, y]`的`'x'`数量；对于这个问题可以递归求解，计算出`[x, y]`在当前层9个位置的哪个位置，基于图像的对称性其实只有5个位置；然后每个位置递归求解下去；
  需要优化的两个点：
  1. 一个是当`[x, y]`相等而且都等于`3^k`的时候可以`O(1)`求解出答案；
  2. 另一个点是当`[x, y]`其中一个等于`3^k`的时候，可以`O(logn)`求解出答案；总体复杂度是`T(n) = 2 O(logn) + T(n / 3) = O(logn*logn)`

8. Treasure(17/53)

  二分最低等级，然后BFS。

9. Alice and Bob are drawing lines(7/16)
  模拟题，直接绘制图像。
  输入数据很大，但是屏幕大小只有21\*21。

