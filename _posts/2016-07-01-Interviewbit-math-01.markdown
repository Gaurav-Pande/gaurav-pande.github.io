---
layout: post
title:  "Binary Representation"
subtitle: "InterviewBit-Math"
date:   2016-07-01 08:43:59
author: Gaurav Pande
categories: Programming
cover: "/assets/interviewbit.jpg"
tag: Interviewbit
---

**Question**:
Given a number N >= 0, find its representation in binary.

Example:

if N = 6,

binary form = 110

**Solution**:
It is a very simple recursive program to find the binary conversion of a number.

```Language-java

  public class Solution 
  {
    public String binary = "";
	    public String findDigitsInBinary(int a) 
	    {
	    if(a==1){
	       binary = 1+binary; 
	        return binary;
	    }
	    if(a==0)
	    {
	         binary = 0+binary; 
	        return binary;
	    }
	    else if(a%2==0){
	        binary=0+ binary;
	        a=a/2;
	        findDigitsInBinary(a);
	        }
	   else{
	        binary=1+binary;
	            a=a/2;
	        findDigitsInBinary(a);
	        } 
	    
	    return binary;
	}
}

```



