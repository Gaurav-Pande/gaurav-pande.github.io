---
layout: post
title:  "Largest Number"
subtitle: "InterviewBit-Array"
date:   2016-07-26 08:43:59
author: Gaurav Pande
categories: Programming
cover: "/assets/interviewbit.jpg"
tag: Interviewbit
---

**Question**:
Given a list of non negative integers, arrange them such that they form the largest number.

For example:

Given [3, 30, 34, 5, 9], the largest formed number is 9534330.

Note: The result may be very large, so you need to return a string instead of an integer.

**Solution**:
 
The problem can be solved as:

* We need to sort the array using collections custom sort way.
* We need to implement a new comparator to do this.
* In comparator we would say- concatinate two string and compare them bitwise and see which is largest.
* So if we have say {8,89}. Our comparator will form 2 strings as "889" and "898", and compare them both.
* 889.compareTo(898) will return int <0.
* Elements in the new sorted list will be {8,89}
* So if traverse reverse we can form the largest number as 898.
* So in this way the list will be sorted in a way that if we concatinate all the elements of the
  new sorted list, it would give us the largest number using all the elements of the array.



```Language-java

public class Solution implements Comparator<String> {
	   public String largestNumber(final List<Integer> A) {
        List<String> B = new ArrayList<String>();
        for (Integer number : A) {
            String x = number.toString();
            B.add(x);
        }
        Collections.sort(B, this);
        StringBuilder ans = new StringBuilder();
        int result = 0;
        for (int i = B.size() - 1; i >= 0; i--) {
            ans.append(B.get(i));
            result += Integer.parseInt(B.get(i));
        }
        return result == 0 ? "0" : ans.toString();
    }
    @Override
    public int compare(String a, String b) {
        String num1 = a + b;
        String num2 = b + a;
        return (num1.compareTo(num2));
    }
	}


```


