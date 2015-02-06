---
layout: post
title: "Introduction to Locality Sensitive Hash"
date: 2015-02-06 11:35:32 +0800
comments: true
categories: MarchineLearning 
---
Locality-sensitive hashing (LSH) is a method of performing probabilistic dimension reduction of high-dimensional data. The basic idea is to hash the input items so that similar items are mapped to the same buckets with high probability (the number of buckets being much smaller than the universe of possible input items). The hashing used in LSH is different from conventional hash functions, such as those used in cryptography, as in the LSH case the goal is to maximize probability of "collision" of similar items rather than avoid collisions. [1] Note how locality-sensitive hashing, in many ways, mirrors data clustering and nearest neighbor search.

<!-- more -->
##Title2##
###Title3###
An LSH family [1] [2] [3] \mathcal F is defined for a metric space \mathcal M =(M, d), a threshold R>0 and an approximation factor c>1. This family \mathcal F is a family of functions h:{\mathcal M}\to S which map elements from the metric space to a bucket s \in S. The LSH family satisfies the following conditions for any two points p, q \in {\mathcal M}, using a function h \in \mathcal F which is chosen uniformly at random:

if d(p,q) \le R, then h(p)=h(q) (i.e.,p and q collide) with probability at least P_1,
   if d(p,q) \ge cR, then h(p)=h(q) with probability at most P_2.
   A family is interesting when P_1>P_2. Such a family \mathcal F is called (R,cR,P_1,P_2)-sensitive.

   Alternatively[4] it is defined with respect to a universe of items U that have a similarity function \phi : U \times U \to [0,1]. An LSH scheme is a family of hash functions H coupled with a probability distribution D over the functions such that a function h \in H chosen according to D satisfies the property that Pr_{h \in H} [h(a) = h(b)] = \phi(a,b) for any a,b \in U.

   Amplification[edit]
   Given a (d_1, d_2, p_1, p_2)-sensitive family \mathcal F, we can construct new families \mathcal G by either the AND-construction or OR-construction of \mathcal F.[1]

   To create an AND-construction, we define a new family \mathcal G of hash functions g, where each function g is constructed from k random functions h_1, ..., h_k from \mathcal F. We then say that for a hash function g \in \mathcal G, g(x) = g(y) if and only if all h_i(x) = h_i(y) for i = 1, 2, ..., k. Since the members of \mathcal F are independently chosen for any g \in \mathcal G, \mathcal G is a (d_1, d_2, p_{1}^k, p_{2}^k)-sensitive family.

   To create an OR-construction, we define a new family \mathcal G of hash functions g, where each function g is constructed from k random functions h_1, ..., h_k from \mathcal F. We then say that for a hash function g \in \mathcal G, g(x) = g(y) if and only if h_i(x) = h_i(y) for one or more values of i. Since the members of \mathcal F are independently chosen for any g \in \mathcal G, \mathcal G is a (d_1, d_2, 1- (1 - p_1)^k, 1 - (1 - p_2)^k)-sensitive family.
