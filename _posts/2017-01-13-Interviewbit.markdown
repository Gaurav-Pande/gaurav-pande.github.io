---
layout: post
title:  "First Positive Missing Number"
subtitle: "InterviewBit-Math"
date:   2017-01-13 09:43:59
author: Gaurav Pande
categories: Programming
cover: "/assets/interviewbit.jpg"
tag: Interviewbit
---

**Problem**:

Given an unsorted integer array, find the first missing positive integer.

Example:

Given [1,2,0] return 3,

[3,4,-1,1] return 2,

[-8, -7, -6] returns 1

Your algorithm should run in O(n) time and use constant space.

**Solution**:

* In this question the trick is to fit the integer to the respective indexes, as we have to solve this problem in O(n).
* So if we have array like---> [-1,2,6,3,990,5]
* Integer 2 should come in index 2,(i.e swap it inplace of 6).
* Similarly 3 should come to Index 3.
* Think of the edge cases, like when the array have only one element and when all elements are present in their respective 
index.




Code:

```
import java.util.ArrayList;

public class Solution {
public static int firstMissingPositive(ArrayList<Integer> A) {
       int len = A.size();
       //System.out.println(len);
       
       if(len == 1){
           if (A.get(0)==1){
               
           return 2;
           }
           else {
               
           return 1;
           }
           
       }
       for(int i=0;i<len;i++){
    	   while (A.get(i)!=i || A.get(i)<0){
    		   	int num = A.get(i);
    		   	int target = num;
    		   //System.out.println(target);
    		   	if(target<0 || target>=len || A.get(target)==num){
    		   		break;}
    		   	//System.out.println(i+A.get(num) + target + A.get(i));
    		   	int temp = A.get(target);
    		   	A.set(target, A.get(i));
    		   	A.set(i, temp);
    		   	
    	   }
    	  // System.out.println(i);
       }
       
       //A.set(0, 0);
       for(int i=1; i<len;i++){
    	if(A.get(i)!=i ){
    		return i;
    	}
       }
       
       //System.out.println(A);
	return len+1;
	}
}

```
