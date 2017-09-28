---
layout: post
title:  "Finding duplicate charactor in a String"
subtitle: "InterviewBit-Math"
date:   2016-08-03 08:43:59
author: Gaurav Pande
categories: Programming
cover: "/assets/interviewbit.jpg"
tag: Interviewbit
---

**Question**:
You have given any string. Find whether the given string is unique or not.

Example :

Input:"aabc"
output:false
Input:"abc"
output:true



**Solution**:
 
This is one of the very good question. There are two methods to do this question:

Method1-*Using Sets*

 * Create a Set in java.
 * Add the elements in the string to the set.
 * if a duplicate char occurs in the chararray, than the set will not allow to add it.
 
 
Method2- *Chararray*.

 *  For this method we need to know about  two inbuilt functions in java , indexOf() which returns the index of first occurence of the character in the string , while second function lastIndexOf() returns the index of last occurence of the character in the given string.
 *  First , we convert the given inputstring into characterarray by using toCharArray() function.
 *  Calculate the indexOf() and lastIndexOf() for each character in the given inputstring
 *  If both are equal then continue and make result= true,else set flag result = false
 *  Return result



Method1(Using Sets)

```Language-java

public static void main(String[] args) {
		// TODO Auto-generated method stub
		String str = new String("abc");
		isunique(str);
	}

	@SuppressWarnings({ "unchecked", "rawtypes" })
	private static void isunique(String str) {
		// TODO Auto-generated method stub
		boolean result = false;
		Set a1 = new HashSet();
		for(int i=0;i<str.length();i++){
			result = a1.add(new Character(str.charAt(i)));
			if(result==false)
				break;
		}
		System.out.println(result);
		
	}

  
```

Method2(Using Chararray)

```Language-java
public static void main(String[] args) {
		// TODO Auto-generated method stub
		String str = new String("aabc");
		System.out.println(isunique(str));
	}

	@SuppressWarnings({ "unchecked", "rawtypes" })
	private static boolean isunique(String str) {
     boolean result =false;
		 char a[] ;
		 for(int i=0;i<str.length();i++){
			 if(str.indexOf(str.charAt(i))==str.lastIndexOf(str.charAt(i)))
			 result=true;
			 else{
				 result = false;
				 break;
			 }
				 
		 }
		 return result;
	}


```


