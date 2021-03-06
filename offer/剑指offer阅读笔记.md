---
title: 剑指offer阅读笔记
categories: [面试, 剑指offer]
tags: [面试, 剑指offer]
---
# 剑指offer阅读笔记
<!-- TOC -->

- [1. 面试需要注意的内容](#1-面试需要注意的内容)
- [2. 编程题](#2-编程题)
    - [2.1. 从链表中查找倒数第k个值](#21-从链表中查找倒数第k个值)
    - [2.2. 从矩阵（从左到右，从上到下依次增大）中查找某值](#22-从矩阵从左到右从上到下依次增大中查找某值)
    - [2.3. 字符串替换](#23-字符串替换)
    - [2.4. 链表在不改变结构的情况下倒着输出](#24-链表在不改变结构的情况下倒着输出)
    - [2.5. 根据前序遍历和中序遍历的结果重建一棵树](#25-根据前序遍历和中序遍历的结果重建一棵树)
    - [2.6. 用两个栈实现队列](#26-用两个栈实现队列)
    - [2.7. 旋转数组的最小数字](#27-旋转数组的最小数字)
    - [2.8. 二进制中1的个数](#28-二进制中1的个数)
    - [2.9. 数值的整数次方](#29-数值的整数次方)
    - [2.10. 打印1到最大的n位数](#210-打印1到最大的n位数)
    - [2.11. 在O(1)时间删除链表节点](#211-在o1时间删除链表节点)
    - [2.12. 调整数组顺序使得奇数位于偶数前面](#212-调整数组顺序使得奇数位于偶数前面)
    - [2.13. 反转链表](#213-反转链表)
    - [2.14. 合并两个排序的链表](#214-合并两个排序的链表)
    - [2.15. 树的子结构](#215-树的子结构)
    - [2.16. 二叉树的镜像](#216-二叉树的镜像)
    - [2.17. 顺时针打印矩阵](#217-顺时针打印矩阵)
    - [2.18. 包含min函数的栈](#218-包含min函数的栈)
    - [2.19. 栈的压入和弹出顺序匹配](#219-栈的压入和弹出顺序匹配)
    - [2.20. 从上往下打印二叉树](#220-从上往下打印二叉树)
    - [2.21. 二叉搜索树的后序遍历序列（判断给定数组是不是一颗二叉搜索树的后序遍历序列）](#221-二叉搜索树的后序遍历序列判断给定数组是不是一颗二叉搜索树的后序遍历序列)
    - [2.22. 二叉树中和为某值的路径（直到叶节点）](#222-二叉树中和为某值的路径直到叶节点)
    - [2.23. 复杂链表的复制](#223-复杂链表的复制)
    - [2.24. 二叉搜索树改为双向链表（只调整树中节点指针的指向）](#224-二叉搜索树改为双向链表只调整树中节点指针的指向)
    - [2.25. 字符串的排列](#225-字符串的排列)
    - [2.26. 数组中出现次数超过一半的数字](#226-数组中出现次数超过一半的数字)
    - [2.27. 最小的k个数](#227-最小的k个数)
    - [2.28. 连续子数组最大和](#228-连续子数组最大和)
    - [2.29. 从1到n中1出现的次数](#229-从1到n中1出现的次数)
    - [2.30. 数组排成最小的数](#230-数组排成最小的数)
    - [2.31. 丑数列举](#231-丑数列举)
    - [2.32. 第一个只出现一次的字符（abcdacd输出b）](#232-第一个只出现一次的字符abcdacd输出b)
    - [2.33. 数组中的逆序对](#233-数组中的逆序对)
    - [2.34. 遍历两个有公共节点的链表，找到这个连接点](#234-遍历两个有公共节点的链表找到这个连接点)
    - [2.35. 数字在排序数组中出现的次数（给定数组和数字，输出数字在数组中出现的次数）](#235-数字在排序数组中出现的次数给定数组和数字输出数字在数组中出现的次数)
    - [2.36. 二叉树的深度](#236-二叉树的深度)
    - [2.37. 判断是不是平衡二叉树（任意左右子树深度相差不超过1）](#237-判断是不是平衡二叉树任意左右子树深度相差不超过1)
    - [2.38. 数组中只出现一次的一个数字](#238-数组中只出现一次的一个数字)
    - [2.39. 数组中只出现一次的两个数字](#239-数组中只出现一次的两个数字)
    - [2.40. 从数组中找到和为s的两个数字](#240-从数组中找到和为s的两个数字)
    - [2.41. 输出所有和为S的连续正数序列](#241-输出所有和为s的连续正数序列)
    - [2.42. 翻转单词顺序](#242-翻转单词顺序)
    - [2.43. 左旋转字符串（abcdef和数字2，输出cdefab）](#243-左旋转字符串abcdef和数字2输出cdefab)
    - [2.44. n个骰子的点数（每种点数的概率）](#244-n个骰子的点数每种点数的概率)
    - [2.45. 扑克牌的顺子（取五张牌，判断是不是顺子）](#245-扑克牌的顺子取五张牌判断是不是顺子)
    - [2.46. 圆圈中剩下的数字](#246-圆圈中剩下的数字)
    - [2.47. 不用加减乘除做加法](#247-不用加减乘除做加法)
    - [2.48. 两个面试案例](#248-两个面试案例)
    - [2.49. 数组中重复的数字（长度为n的数组，并且数字都在0到n-1之间）](#249-数组中重复的数字长度为n的数组并且数字都在0到n-1之间)
    - [2.50. 构建乘积数组（不能使用除法）](#250-构建乘积数组不能使用除法)
    - [2.51. 字符串正则表达式匹配](#251-字符串正则表达式匹配)
    - [2.52. 链表中环的入口结点](#252-链表中环的入口结点)
    - [2.53. 删除链表中重复的节点](#253-删除链表中重复的节点)
    - [2.54. 二叉树的下一个节点（数中存在指向父节点的指针，找到中序遍历的下一个节点）](#254-二叉树的下一个节点数中存在指向父节点的指针找到中序遍历的下一个节点)
    - [2.55. 对称的二叉树](#255-对称的二叉树)
    - [2.56. 二叉树打印成多行](#256-二叉树打印成多行)
    - [2.57. 序列化二叉树](#257-序列化二叉树)
    - [2.58. 二叉搜索树的第k个节点（第k大的节点）](#258-二叉搜索树的第k个节点第k大的节点)
    - [2.59. 数据流的中位数](#259-数据流的中位数)
    - [2.60. 滑动窗口的最大值](#260-滑动窗口的最大值)

<!-- /TOC -->
## 1. 面试需要注意的内容
- 准备几个问题问面试官（根据公司、职位等等）
- 介绍自己做过的项目：简短的项目背景、完成的任务、未完成任务自己做了哪些方面的工作（以及怎么做的）、总结自己的贡献与收获
- 扎实的基础知识与高质量的代码：命名与缩进习惯，**边界条件（boundary condition）的考虑**，优化效率的能力，**不合规范的输入的处理**等等。

## 2. 编程题

### 2.1. 从链表中查找倒数第k个值
两个指针，但是注意边界条件。

### 2.2. 从矩阵（从左到右，从上到下依次增大）中查找某值
从右往左入手选定列，在从上往下入手选定行。

### 2.3. 字符串替换
将原本一个字符换成多个字符时，注意从右往左（减少移动次数），同样类型的还有归并排序(两个排好序的数组，并且第二个数组后面有足够的空间方数据)，从后往前排。

### 2.4. 链表在不改变结构的情况下倒着输出
使用栈或者用递归的方法

### 2.5. 根据前序遍历和中序遍历的结果重建一棵树
前序遍历第一个都是根节点，中序遍历中间的也是根节点；思路为：取前序第一个，已知为根节点，然后在中序遍历中找到这个值，这个值左边的部分是根节点的左子树（数量为n）的中序遍历结果，右边的部分是根节点的右子树（数量为m）的中序遍历结果，相对应于前序遍历（去掉第一个）结果，前n个为左子树的前序遍历结果，后m个为右子树的前序遍历结果。递归。

### 2.6. 用两个栈实现队列
根据栈和队列的不同（栈先进后出，队列先进先出）。栈1用来实际入栈，栈2用来实际出栈，实现方式：为当需要进栈的时候，数据进入栈1，当需要出栈的时候，查看栈2是否为空，如果为空，则从栈1将所有数据出栈并入到栈2。

### 2.7. 旋转数组的最小数字
使用二分查找的思想。设定两个指针p1和p2，若p1与p2相邻则取p2。若`p1<p2`，取中间指针p3，若p3大于p1，则最小数字在p3到p2间，否则在p1到p3间。

### 2.8. 二进制中1的个数
注意负数在二进制中最高位是1，如果使用`>>`进行移位操作，为了保证还是负数，不会改变最高位。两种方法，使用数字1进行二进制与操作，然后把1左移一位`<< 1`，继续与，直到结果为0。第二种方法，注意到整数a，与a-1进行与操作可以逐步消去最右端的1。

### 2.9. 数值的整数次方
注意整数次方，这里的整数还包含0和负数。还要注意对输入值的是否和法判断，判断两个double类型的数据是否相等不能直接使用`==`，而应该用差很小来表示。同时考虑整数次方，一次一次的相乘不够快，可以除以二然后相乘，也就是递归了。

### 2.10. 打印1到最大的n位数
注意这里的n位数是否会是大数问题。可以打印全排列，使用递归思想，另外打印的时候注意前面是0的话就不要打印了。

### 2.11. 在O(1)时间删除链表节点
假设这个节点是node2delete，可以把node2delete.nextNode的值赋值给node2.delete，然后让node2delete指向下下个节点。

### 2.12. 调整数组顺序使得奇数位于偶数前面
主要思想是快排里面的Partition思想，只不过是左边找偶数，右边找奇数。通过拓展条件（使用函数），这一思想适用于更多场景。

### 2.13. 反转链表
记录3个指针，分别代表`pNodeCurrent, pNodePrev, pReversedHead`。注意考虑输入为NULL以及链表的断裂情况

### 2.14. 合并两个排序的链表
基本同上

### 2.15. 树的子结构
递归查找匹配

### 2.16. 二叉树的镜像
递归交换左右子树

### 2.17. 顺时针打印矩阵
打印每一圈都分四步。主要是注意最后一圈可能退化成只有一行或者只有一列。这样打印最后一圈可能只需要3,2,1步。

### 2.18. 包含min函数的栈
使用辅助栈记录每一个数据进栈之后更新的最小值

### 2.19. 栈的压入和弹出顺序匹配
栈的经典题目

### 2.20. 从上往下打印二叉树
使用队列，每从队列中出一个节点，同时把节点的左右节点的值入队列。

### 2.21. 二叉搜索树的后序遍历序列（判断给定数组是不是一颗二叉搜索树的后序遍历序列）
注意后序遍历的特点，根节点的值在最后面，而且是根节点的左子树遍历结果都小于根节点，右子树比那里结果都大于根节点。选定根节点，将前面的n-1个值切分为2部分，小于根节点值的是左子树，大于根节点值的是右子树。递归。

### 2.22. 二叉树中和为某值的路径（直到叶节点）
其实是二叉树深度优先遍历的变种。每次递归完成之后都要返回父节点。

### 2.23. 复杂链表的复制
举例子：原链表:`a->b->c->d`，先复制成`a-a'->b->b'->c->c'->d->d'`。然后挪动复杂指针一位就行。之后再分开。

### 2.24. 二叉搜索树改为双向链表（只调整树中节点指针的指向）
中序遍历思想。[戳这里查看代码详细](https://github.com/chen-kh/InterviewQuestions/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%9827%E4%B9%8B%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91%E4%B8%8E%E5%8F%8C%E5%90%91%E9%93%BE%E8%A1%A8_ConvertBinarySearchTree.cpp)

### 2.25. 字符串的排列
主要思想是使用递归，然后把字符串排列看作两种情况：第一种是第一个是a，第二种是第一个不是a。第二种的得到就是把a和后面的每个字符进行互换操作得到。因此可以递归了。[戳这里查看代码详细](https://github.com/chen-kh/InterviewQuestions/blob/master/%E9%9D%A2%E8%AF%95%E9%A2%9828%E4%B9%8B%E5%AD%97%E7%AC%A6%E4%B8%B2%E7%9A%84%E6%8E%92%E5%88%97_StringPermutation.cpp)

### 2.26. 数组中出现次数超过一半的数字
解法一：基于快排的思想，更改partition函数，复杂度O(n)。跟找第k大的数是一样的，我们这次找第n/2个数。

解法二：根据数组特点完成算法，时间复杂度也是O(n)。保存两个变量`currentValue`和`preValue`，二者相同则加1，不同则减1。最有一个使得值为1的书就是超过一半的数字。

### 2.27. 最小的k个数
解法一：基于快排的思想，知道随机找的数字最终落在了k位上。跟第k小数字如出一辙，复杂度O(n)

解法二：使用最小堆。需要堆或者红黑树来进行辅助。但是适用于大量数据的处理。复杂度O(nlogk)

### 2.28. 连续子数组最大和
经典动态规划

### 2.29. 从1到n中1出现的次数
解法一：比较复杂。举例子说明。n=21345，（1-21345）转换为（1-1345）+（1346-21345），只处理第二部分，第一部分用相同的方法递归求解。第二部分分为（1346-11345）和（11346-21345），最高位出现1的次数10000次，最高位之外出现1的次数，固定一位，则其他位任意，`2*4*1000=8000`次。

解法二：[详情戳这里](https://blog.csdn.net/yi_afly/article/details/52012593)
```
534 = （个位1出现次数）+（十位1出现次数）+（百位1出现次数）=（53*1+1）+（5*10+10）+（0*100+100）= 214
530 = （53*1）+（5*10+10）+（0*100+100） = 213
504 = （50*1+1）+（5*10）+（0*100+100） = 201
514 = （51*1+1）+（5*10+4+1）+（0*100+100） = 207
10 = (1*1)+(0*10+0+1) = 2
```
```c
public int count(int n){
    if(n<1)
        return 0;
    int count = 0;
    int base = 1;
    int round = n;
    while(round>0){
        int weight = round%10;
        round/=10;
        count += round*base;
        if(weight==1)
            count+=(n%base)+1;
        else if(weight>1)
            count+=base;
        base*=10;
    }
    return count;
}
```

### 2.30. 数组排成最小的数
归根结底是比较两个数谁排在前谁排在后的问题。设定规则：数a和数b，若ab>ba，则a>b，根据这个规则对数组进行排序。

### 2.31. 丑数列举
只有2,3,5作为因子组成的数。思想是一直保存这些整数，然后找后面紧邻的一个，紧邻的这个一定是前面的数乘以2,3,5得到，找一个最小的就行。

### 2.32. 第一个只出现一次的字符（abcdacd输出b）
使用hash表进行存储，ascii码表，256长度就够。key就是字符的ascii码值，value就是出现的次数，一次就是1，多次就是-1。

### 2.33. 数组中的逆序对
归并排序思想

### 2.34. 遍历两个有公共节点的链表，找到这个连接点
两种思路，第一种使用两个辅助栈，入栈完毕后，同时出栈，直到最后两个相同的指针；第二种不使用辅助栈，遍历两遍两个链表，第一次确定长短，然后先在长链上走几步，之后齐头并进，直到找到相同的指针。

### 2.35. 数字在排序数组中出现的次数（给定数组和数字，输出数字在数组中出现的次数）
基本思路是遍历，但是这并没有利用排序数组的优势。这里主要思想是使用二分查找的思想。查找两次，第一次找第一次出现的下标，第二次找最后一次出现的下标。第一次找的时候，如果中间值大于等于当前值，往左找（判断是不是第一个）。第二次找的时候反过来。

### 2.36. 二叉树的深度
递归思想

### 2.37. 判断是不是平衡二叉树（任意左右子树深度相差不超过1）
不要直接递归左右子树找到深度然后比较，这样有节点多次被遍历。使用后序遍历，遍历时记录深度。

### 2.38. 数组中只出现一次的一个数字
异或一遍

### 2.39. 数组中只出现一次的两个数字
异或一遍，从结果中找到第一位不是0（是1）的位，假设为第n位。继续异或一遍，分成两个数组，第一个数组第n位都是1，第二个数组都是0。两个数组分别异或就找出来了。

### 2.40. 从数组中找到和为s的两个数字
如果数组是递增的，那么两个指针，一个最前一个最后，如果两个指针的和小于s，那么第一个加一，若大于s，第二个减一。

### 2.41. 输出所有和为S的连续正数序列
跟上面类似，两个指针，一个small，一个big，如果和大于sum，则small++，sum-=small,否则big++,sum+=big

### 2.42. 翻转单词顺序
先整体翻转一次，然后每个单词再单独翻转一次。

### 2.43. 左旋转字符串（abcdef和数字2，输出cdefab）
把字符串按照数字分成两部分，先每个部分翻转，然后整体翻转。跟上面的那道题很像的。

### 2.44. n个骰子的点数（每种点数的概率）
数组存放n到6n。下标表示筛子数，对应的值表示出现的次数。一个骰子一个骰子的往上添加，第一个筛子都是1，第二个骰子的和为n的出现次数，是上一次骰子里面的n-1,n-2,n-3,n-4,n-5,n-6的和。

### 2.45. 扑克牌的顺子（取五张牌，判断是不是顺子）
先排序，然后看差几张，如果0能补上就没问题。

### 2.46. 圆圈中剩下的数字
关键在于通过映射，转换成新环，去发现规律，然后成为动态规划问题。（递归也可以）

### 2.47. 不用加减乘除做加法
发散思维，使用二进制加法，先异或得到不进位的位。然后两个数求与再左移一位，得到进位的值。（第一个得到的数替换原数值1，第二个得到的数替换原数值2）。循环直到没有进位。

### 2.48. 两个面试案例
- 把字符串转换成整数：不要想当然一位多简单，要考虑多种边界条件
- 两个树节点的最低公共祖先  
	- 排序二叉树的话直接找第一个使得两个树节点分别小于和大于当前节点值就可以了-最简单
	- 普通的树如果存在指向父节点的指针，就转换成了链表找第一个公共点
	- 最普通树的话，解决方法就是深度（或者广度）优先找两条路径，然后记录下来进行对比。

### 2.49. 数组中重复的数字（长度为n的数组，并且数字都在0到n-1之间）
- 最基本的方法是排序，然后找到重复的数字
- 第二种方法是观察数组的规律：由于数字都在0到n-1之间，所以正常情况下数字的下标应该和数字本身相等。因此我们遍历数组，从第一个开始，查看值与下标是否相等，如果不相等的话就把该数值a与下标为a的值进行比较，如果相等，则找到重复的数字，如果不相等就交换数值，也就是数值a归位了。如此循环直到遍历完成。由于每个数值最多两次操作就可以归位，因此时间复杂度O(1)

### 2.50. 构建乘积数组（不能使用除法）
建立一个矩阵，然后使用两个辅助数组。

### 2.51. 字符串正则表达式匹配
使用递归的思想，两个指针，一个指向字符，一个指向模式。匹配后把后面的部分递归处理。主要问题是处理`*`的情况，指向字符的指针可以移动1次或两次或者不移动。

### 2.52. 链表中环的入口结点
分两步走，第一步确定环的数量，第二步两个指针，第一个指针先走n步(n就是环内结点数量)，然后两个指针齐头并进，相遇的时候就是入口结点。第一步确定环的数量，同样设定两个指针，第一个每次走一步，第二个每次走两步，相遇的时候就是在节点内。然后可以循环一次算出节点数。

### 2.53. 删除链表中重复的节点
常规思路

### 2.54. 二叉树的下一个节点（数中存在指向父节点的指针，找到中序遍历的下一个节点）
其实很简单，一步一步考虑算法就可以了。如果这个节点存在右节点，那么肯定就是右节点中序遍历的第一个值，如果这个节点不存在右节点，但是他是某个节点的左节点，那下一个节点就是他的父节点，如果他是父节点的右节点，就要向上去找父节点，直到找到一个父节点是它父节点的左子节点，那就是这个父节点了。

### 2.55. 对称的二叉树
把NULL节点的值也输出，这样如果后序遍历和从右开始的后序遍历输出结果一样的话就是对称的。

### 2.56. 二叉树打印成多行
如果每行都是从左到右或者从右到左的话，那就是典型的队列的问题。如果按照之字形打印，就使用两个栈。第一个栈存放偶数行的遍历结果，第二个栈存放奇数行的遍历结果，第一个栈都是先左节点后右节点，第二个栈反过来。

### 2.57. 序列化二叉树
进行带空指针输出的前向遍历。可以反推回来。

### 2.58. 二叉搜索树的第k个节点（第k大的节点）
中序遍历，一边遍历，一遍查找。

### 2.59. 数据流的中位数
使用两个堆，最大堆在左边，最小堆在右边，保证最大堆的每个值都小于最小堆的每个值。发生冲突就往该放的堆里放，然后从这个堆里挑出最大值或者最小值放到另外一个堆里。

### 2.60. 滑动窗口的最大值
为了保证是O(n)复杂度，滑动窗口是用双向队列表示，里面只存储是最大值或者可能是下一个最大值的值。