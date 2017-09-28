---
layout: post
title:  "Excel Column Title"
subtitle: "InterviewBit-Math"
date:   2016-07-23 09:43:59
author: Gaurav Pande
categories: Programming
cover: "/assets/interviewbit.jpg"
tag: Interviewbit
---

**Problem**:

Given a positive integer, return its corresponding column title as appear in an Excel sheet.

For example:

    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 


**Solution**:
 
This problem you have to come out with an expression to solve the problem.

```Language-java

public class Solution {
	public String convertToTitle(int a) {
	     StringBuilder str = new StringBuilder();
        while(a!=0){
        str.insert(0,(char)((a -1)%26 + 'A')); 
        a=(a-1)/26;
        }
        return str.toString();
	}
}


```


