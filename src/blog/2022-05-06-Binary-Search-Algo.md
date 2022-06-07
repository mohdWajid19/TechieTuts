---
title: Binary Search Algorithm
author: Mohd Wajid
date: 2022-05-06
tags: ["post" , "featured"]
# image: /assets/blog/article-2.jpg
# imageAlt: This is a test
description: Binary search is a most efficient and important algorithm which searches for the target element in a limited space in a sorted workspace, but either in strictly increasing or strictly decreasing workspace only, using Decease and conquer Algo.
---
<p>
Binary Search is a searching algorithm used in a sorted array by repeatedly dividing the search interval in half. The idea of binary search is to use the information that the array is sorted and reduce the time complexity to O(Log n). 
</p>

<p>
Binary Search Algorithm: The basic steps to perform Binary Search are: <br/>
Begin with the mid element of the whole array as search key. <br/>
<ul> 
<li> If the value of the search key is equal to the item then return index of the search key.</li>
<li>Or if the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half.</li>
<li>Otherwise, narrow it to the upper half.</li>
<li>Repeatedly check from the second point until the value is found or the interval is empty.</li>
</ul>
</p>
<p>
    <strong>Step-by-step Binary Search Algorithm: </strong>We basically ignore half of the elements just after one comparison. <br/>
    <ol>
        <li>Compare x with the middle element.</li>
        <li>If x matches with the middle element, we return the mid index.</li>
        <li>Else If x is greater than the mid element, then x can only lie in the right half subarray after the mid element. So we recur for the right half.</li>
        <li>Else (x is smaller) recur for the left half.</li>
    </ol>
</p>
<h2>Java implementation of recursive Binary Search</h2>
<p>
<pre>
class BinarySearch {
	int binarySearch(int arr[], int l, int r, int x)
	{
		if (r >= l) {
			int mid = l + (r - l) / 2;
			if (arr[mid] == x)
				return mid;
			if (arr[mid] > x)
				return binarySearch(arr, l, mid - 1, x);
			return binarySearch(arr, mid + 1, r, x);
		}
		return -1;
	}
	public static void main(String args[])
	{
		BinarySearch ob = new BinarySearch();
		int arr[] = { 2, 3, 4, 10, 40 };
		int n = arr.length;
		int x = 10;
		int result = ob.binarySearch(arr, 0, n - 1, x);
		if (result == -1)
			System.out.println("Element not present");
		else
			System.out.println("Element found at index "+ result);
	}
}
</pre>
</p>

<p>
    <h2> Python3 Program for recursive binary search.</h2>
<pre>
def binarySearch(arr, l, r, x):
	if r >= l:
		mid = l + (r - l) // 2
		if arr[mid] == x:
			return mid
		elif arr[mid] > x:
			return binarySearch(arr, l, mid-1, x)
		else:
			return binarySearch(arr, mid + 1, r, x)

	else:
		return -1
arr = [2, 3, 4, 10, 40]
x = 10

result = binarySearch(arr, 0, len(arr)-1, x)
if result != -1:
	print("Element is present at index % d" % result)
else:
	print("Element is not present in array")
</pre>
</p>

<p>
<strong>
T.C. :: O(log n) <br/>
S.C. :: O(1)
</strong>
</p>
