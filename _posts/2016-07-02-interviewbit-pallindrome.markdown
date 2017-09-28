---
layout: post
title:  "Pallindrome"
subtitle: "InterviewBit-Math"
date:   2016-07-02 08:43:59
author: Gaurav Pande
categories: Programming
cover: "/assets/interviewbit.jpg"
tag: Interviewbit
---

**Question**:

Determine whether an integer is a palindrome. Do this without extra space.

A palindrome integer is an integer x for which reverse(x) = x where reverse(x) is x with its digit reversed.
Negative numbers are not palindromic.

Example :
Input : 12121
Output : True

Input : 123
Output : False


**Solution**:
 
 Algo:
  * find reverse of the number.
  * match two numbers.
  * if both are equal than pallindrome, else not.


```Language-java

  public class Solution {
	public boolean isPalindrome(int x) {
	    int reverseNum;
	    reverseNum = reverse(x);
	    if(x == reverseNum)
	    return true;
	    else
	    return false;
	    
	}
public static int reverse(int num){
        int temp=0;
        int temp1;
        while(num>0){
            temp=temp*10;
            temp1=num%10;
            temp=temp+temp1;
            num=num/10;                       
                }
                return temp;
    }
}


```

