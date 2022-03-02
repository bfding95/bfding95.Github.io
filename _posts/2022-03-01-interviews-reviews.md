---
layout: post
title: 面试reviews
date: 2022-03-01
author: 麻瓜码农
categories: [interview]
comments: true
toc: true
---

面试整理总结 查缺补漏！！
## Google Phone Interview: 
###Date: 3/1/2022

45 分钟面试，印度面试官，电话回声有点严重，基本沟通没有问题。 偶尔有时候听不太清。
上来问平时用什么语言，确认以后说会问一些data structures和problem solving。

1. Find the sum of all the tree nodes. 
第一反应是遍历，说可以用recursion做。简单画了一个树表达了一下思路，得到肯定答复后问是否可以开始coding，是要pseudocode还是完整java代码， 面试官说都行， 然后建议先写一下method的input和return的data type. （这里以后要注意，如果题目没有要求，一定要在写之前clarify一下）
   写完代码，面试官说能不能口头跑一遍。最后要求分析一下时间复杂度。以后一定要主动跑test case然后主动分析时间复杂度！！时间复杂度和空间复杂度的分析还是有欠缺， 有时候知道答案但是分析的时候说得不好， 要多练！

2. Find the height of the tree
    跟第一题类似，说可以继续用recursion。面试官让跳过了coding部分。问一下如果用int记录第一题的sum会有什么问题，回答后改成了Long.还是之前return type的clarfication做得不好。 谨记！！！
3. Given set of nodes -> unordered, find the root.
    一开始懵了一会，反应过来就是找height最高的node, 回答可以遍历set然后找，同时说了这个解法时间复杂度不好。优化了一下说可以用HashMap存所有算过的node的高度避免重复计算。面试官满意。
4. 提问：在google工作最享受什么 -> 和各个time zone的人沟通，worldwide influence.然后解决performance问题。

总结: phone interview还是挺简单的。不过以后clarification还是要做好。 谨记！！！好好准备VO!

## Apple Interview:
###Date: 3/2/2022

45分钟面试。问了java基础问题，last project, tech stack。java 8 新feature。

Coding: 1. 写一个stream做filter和sorted 2. 两个class找出product所有parent 
>  IPHONE 
> 
>  /         \
> 
> LOCKED UNLOCKED
> 12, 13

given stream of product. -> 遍历，找到所有parent -> 用hashMap存了找过的值，避免重复计算

问的题目都挺简单，感觉这个组像是做产品data management system。

最后问了组的main job和tech stack，果然和猜的一样..