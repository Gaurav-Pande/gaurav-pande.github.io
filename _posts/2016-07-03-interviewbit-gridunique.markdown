---
layout: post
title:  "Grid Unique Paths"
subtitle: "InterviewBit-Math"
date:   2016-07-03 08:43:59
author: Gaurav Pande
categories: Programming
cover: "/assets/interviewbit.jpg"
tag: Interviewbit
---

**Question**:
A robot is located at the top-left corner of an A x B grid (marked ‘Start’ in the diagram below).

<img src="{{ site.baseurl }}/assets/3eaivQ5.png" title="grid" class="grid">

The robot can only move either down or right at any point in time. The robot is trying to reach the bottom-right corner of the grid (marked ‘Finish’ in the diagram below).

How many possible unique paths are there?

Note: A and B will be such that the resulting answer fits in a 32 bit signed integer.

Example :

Input : A = 2, B = 2
Output : 2

2 possible routes : (0, 0) -> (0, 1) -> (1, 1) 
              OR  : (0, 0) -> (1, 0) -> (1, 1)



**Solution**:
 
This is one of the very good question. There are two methods to do this question:

Method1-*Dyanamic Programming*

 * If the matrix is 1Xn ot mX1, than the number of unique path will be 1.
 * There are only 2 directions you can go. Either go down or go right.
 * So you divide the problem in subproblems. if you are at a[m,n] and you go one down, than you are to find
   unique paths from a[m-1,n]. Or if you go one right than you will have to find unique paths from a[m,n-1].
 * Run this recursively.
 
 
Method2- *Using Combinations*.

 * If you are 0,0 and you have to reach m,n in a matrix of order of m,n.
 * You have to go n-1 steps right and m-1 steps down, that is sure. However it depends first you go 2 steps right than 2 down
   and than remaining n-3 steps right and m-3 steps down.
 * So total number of paths will be m+n-2. 
 * How many ways you can choose n-1 paths from m+n-2. It will be C(m+n-2,n-1).
 * Remaining paths: (m+n-2)-(n-1)=m-1.
 * from these m-1 paths, no of ways you can choose m-1 paths is C(m-1,m-1) = 1.
 * Hence total unique paths will be C(m+n-2,n-1) OR C(m+n-2,m-1).


Method1(DP)

```Language-java

public class Solution {
	public int uniquePaths(int a, int b) {
	    if(a==1||b==1)
	    return 1;
	    
	    return uniquePaths(a-1,b)+ uniquePaths(a,b-1);
	}
}

  
```

Method2(Using Combination)

```Language-java


public Solution {
 public int uniquePaths(int a, int b) {
        if(a==1||b==1)
        return 1;
        else{
            BigInteger x = fact(a+b-2);
            BigInteger y= fact(a-1);
            BigInteger z= fact(b-1);
            return  (x.divide(y.multiply(z))).intValue();
        }
        
    }
    public static BigInteger fact(int num) {
        BigInteger fact = BigInteger.valueOf(1);
        for (int i = 1; i <= num; i++)
            fact = fact.multiply(BigInteger.valueOf(i));
        return fact;
   }
}

```


