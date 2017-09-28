---
layout: post
title:  "Prime Using Sieve's Method"
subtitle: "InterviewBit-Math"
date:   2016-07-02 08:43:59
author: Gaurav Pande
categories: Programming
cover: "/assets/interviewbit.jpg"
tag: Interviewbit
---

**Question**:
Given a number N, find all prime numbers upto N ( N included ).

Example:

if N = 7,

all primes till 7 = {2, 3, 5, 7}

Make sure the returned array is sorted.

**Solution**:
 
*Sieve of Eratosthenes* is an ancient algorithm to find the prime number upto n.
Algo is very simple: 

  * You write all number upto n.
  * You initially mark all numbers as prime.
  * Then you start with first prime num(i.e 2).
  * All the multiples of 2 will not be a prime(or we can generalise this- any multiple of a prime will not be a prime),
    so we remove the multiples of 2 from the list.
  * We than move to next prime(i.e 3) and remove all multiples of 3.
  * Finally the list we will have, will contains all the prime numbers upto n.

Time Complexity:0(nlog(logn))

Refer link to know more on time complexity -  [Sieve][sieve] 

```Language-java

  public class Solution {
	public ArrayList<Integer> sieve(int n) {
    ArrayList<Integer> result = new ArrayList<Integer>();
        // initially assume all integers are prime
        boolean[] isPrime = new boolean[n+1];
        //making all values prime
        for(int i=2;i<=n;i++)
        isPrime[i]=true;
       for(int i=2;i<=n;i++){
           for(int j=2;j<=n;j++){
               if((i*j)>n)
               break;
               else
                isPrime[i*j]=false;
           }
       }
       
       //inserting into arraylist
       for(int i=2;i<=n;i++){
           if(isPrime[i])
           result.add(i);
       }
       return result;
    }
}


```

[sieve]:http://stackoverflow.com/questions/2582732/time-complexity-of-sieve-of-eratosthenes-algorithm
