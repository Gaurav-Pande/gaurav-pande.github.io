---
layout: post
title:  "Excel Column Number"
subtitle: "InterviewBit-Math"
date:   2016-07-23 08:43:59
author: Gaurav Pande
categories: Programming
cover: "/assets/interviewbit.jpg"
tag: Interviewbit
---

**Question**:

Given a column title as appears in an Excel sheet, return its corresponding column number.

Example:
    A -> 1
    
    B -> 2
    
    C -> 3
    
    ...
    
    Z -> 26
    
    AA -> 27
    
    AB -> 28 


**Solution**:
 
This problem you have to come out with an expression to solve the problem.

```Language-java

public class Solution {
	public int titleToNumber(String a) {
	    char[] b = a.toCharArray();
	    int result= 0;
	    for(int i=0;i<b.length;i++){
	        result = result*26 + (b[i]-'A' + 1);
	    }
	    return result;
	}
}

```


