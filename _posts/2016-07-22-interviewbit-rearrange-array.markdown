---
layout: post
title:  "Rearrange Array"
subtitle: "InterviewBit-Math"
date:   2016-07-22 08:43:59
author: Gaurav Pande
categories: Programming
cover: "/assets/interviewbit.jpg"
tag: Interviewbit
---

**Question**:

Rearrange a given array so that Arr[i] becomes Arr[Arr[i]] with O(1) extra space.

Example:
Input : [1, 0]
Return : [0, 1]

 Lets say N = size of the array. Then, following holds true :
* All elements in the array are in the range [0, N-1]
* N*N does not overflow for a signed intege

**Solution**:
 
Problem is straight and simple. 

* You have to get the value at a index,i.e [1,2,3,1]
* Use that value as a new index,i.e at i=0, a[i]=1, new index=1;
* Than now fetch value at a[index],i.e a[index]=2;
* Now this a[index] should be inserted at i=0;
* Similarly for others as well.



```Language-java

public class Solution {
	public void arrange(ArrayList<Integer> a) {
	    ArrayList<Integer> b = new ArrayList<Integer>();
	    for(int i=0;i<a.size();i++){
	        b.add(a.get(i));
	    }
	    a.clear();
	    for(int i=0;i<b.size();i++){
	        a.add(i,b.get(b.get(i)));
	    }
	   
	}
}

```


