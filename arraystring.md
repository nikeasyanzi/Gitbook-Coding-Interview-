# [3. Array/String](/arraystring.md)


### 6 Two Sum

[Two Sum](questions/TwoSum.md)

### 7 Two Sum 2

[Two Sum](questions/TwoSum.md)

### 8 Two Sum 3 \(locked\)

[Two Sum](questions/TwoSum.md)

### 9 Valid Palindrome

[125. Valid Palindrome](questions/ValidPalindrome.md)

### 10 STRSTR\(\)



https://leetcode.com/submissions/detail/150990173/  暴力法



KMP

http://www.evanlin.com/about-kmp/

http://bangbingsyb.blogspot.tw/2014/11/leetcode-implement-strstr-kmp.html





### 11 Reverse words in a string

[11 Reverse words in a string](questions/ReverseWordsInAString.md)

### 12 Reverse words in a string 2
[11 Reverse words in a string](questions/ReverseWordsInAString.md)


### 13 ATOI

### 14 Valid Number

### 15 Longest Substring Without Repeating Characters

[3. Longest Substring Without Repeating Characters](/questions/LongestSubstringWithoutRepeatingCharacters.md)

### 16 Longest Substring with At Most Two Distinct Characters

### 17 Missing Ranges

### 18 Longest Palindromic Substring

### 19 One Edit Distance \(locked\)

### 20 Read N Characters Given Read4

### 21 Read N Characters Given Read4 – Call multiple times

### Permutation Sequence

[https://leetcode.com/problems/permutation-sequence/description/](https://leetcode.com/problems/permutation-sequence/description/)  
[http://bangbingsyb.blogspot.tw/2014/11/leetcode-permutation-sequence.html](http://bangbingsyb.blogspot.tw/2014/11/leetcode-permutation-sequence.html)

## permutation

```c
void permute(char *a, int left, int right)
{
   int i;
   if (left == right)
     printf("%s\n", a);
   else
   {
       for (i = left; i <= right; i++)
       {
          swap((a+left), (a+i));
          permute(a, left+1, right);
          swap((a+left), (a+i)); //backtrack
       }
   }
}
```

以{a,b,c}  可以想成  保留一個字元    先swap 剩下的   然後遞迴的做

```
    a,{b,c}                b,{a,c}            c,{a,b}

{b,c}     {c,b}        {a,c}     {c,a}    {a,b}     {b,a}
```

[http://hugedream.blogspot.tw/2009/07/permutation-to-iterate-is-human-to.html](http://hugedream.blogspot.tw/2009/07/permutation-to-iterate-is-human-to.html)  
[https://www.geeksforgeeks.org/write-a-c-program-to-print-all-permutations-of-a-given-string/](https://www.geeksforgeeks.org/write-a-c-program-to-print-all-permutations-of-a-given-string/)

另一種解法是Heap's algorithm  
Why does Heap's algorithm work?  
[http://ruslanledesma.com/2016/06/17/why-does-heap-work.html](http://ruslanledesma.com/2016/06/17/why-does-heap-work.html)  
[https://www.geeksforgeeks.org/heaps-algorithm-for-generating-permutations/](https://www.geeksforgeeks.org/heaps-algorithm-for-generating-permutations/)

#### interative

[http://zhouyichu.com/algorithm/Permutation-Generation-2/](http://zhouyichu.com/algorithm/Permutation-Generation-2/)

[http://www.cnblogs.com/yangykaifa/p/7294929.html](http://www.cnblogs.com/yangykaifa/p/7294929.html)  
[http://l4disgreat.blogspot.tw/2016/02/leet-code-pascals-triangle.html](http://l4disgreat.blogspot.tw/2016/02/leet-code-pascals-triangle.html)

[https://www.geeksforgeeks.org/heaps-algorithm-for-generating-permutations/](https://www.geeksforgeeks.org/heaps-algorithm-for-generating-permutations/)  
[http://hugedream.blogspot.tw/2009/07/permutation-to-iterate-is-human-to.html](http://hugedream.blogspot.tw/2009/07/permutation-to-iterate-is-human-to.html)  
[http://headfirstalgo.blogspot.tw/2016/07/permutation-algorithm.html](http://headfirstalgo.blogspot.tw/2016/07/permutation-algorithm.html)

### [283 Move Zeroes](https://leetcode.com/problems/move-zeroes/)

[Move Zeroes](/questions/MoveZeroes.md)
### 27. Remove Element
[Move Zeroes](/questions/MoveZeroes.md)

### 3. Longest Substring Without Repeating Characters

[https://leetcode.com/problems/longest-substring-without-repeating-characters/description/](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

```
Given a string, find the length of the longest substring without repeating characters.

Examples:

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

### [724. Find Pivot Index](/questions/FindPivotIndex.md)

### [448. Find All Numbers Disappeared in an Array](/questions/FindAllNumbersDisappearedinanArray.md) \*

### [41. First Missing Positive ](/questions/FindMissingPositive.md)

### 665. Non-decreasing Array
[665. Non-decreasing Array](/questions/Non-decreasingArray.md)

### 896. Monotonic Array
[665. Non-decreasing Array](/questions/Non-decreasingArray.md)


### 26. Remove Duplicates from Sorted Array
[#26. Remove Duplicates from Sorted Array](/questions/RemoveDuplicatesfromSortedArray.md)

### 80. Remove Duplicates from Sorted Array II
[80. Remove Duplicates from Sorted Array II](/questions/RemoveDuplicatesfromSortedArray.md)

### [238. Product of Array Except Self](/questions/ProductofArrayExceptSelf.md)  

### [389. Find the Difference](/questions/FindtheDifference.md)
### 842. Split Array into Fibonacci Sequence

[](/questions/SplitArrayintoFibonacciSequence.md)
這題 其實還沒做過



###242. Valid Anagram
[242. Valid Anagram](/questions/ValidAnagram.md)


### 845. Longest Mountain in Array
[845. Longest Mountain in Array](/questions/LongestMountaininArray.md)

### 349. Intersection of Two Arrays
[Intersection of Two Arrays](/questions/IntersectionofTwoArrays.md)
### 350. Intersection of Two Arrays II
[Intersection of Two Arrays](/questions/IntersectionofTwoArrays.md)


### 27. Remove Element


### 169. Majority Element
[169. Majority Element](/questions/MajorityElement.md)
### 229. Majority Element II
[169. Majority Element](/questions/MajorityElement.md)

### 868. Binary Gap
[868. Binary Gap](/questions/BinaryGap.md)
### 78. Subsets
[78. Subsets](/questions/Subsets.md)


### 900. RLE Iterator
[900. RLE Iterator](/questions/RLEIterator.md)

### 931. Minimum Falling Path Sum
[931. Minimum Falling Path Sum](/questions/MinimumFallingPathSum.md)


### 560.Subarray Sum Equals K
### 930. Binary Subarrays With Sum
### 152. Maximum Product Subarray
https://leetcode.com/problems/maximum-product-subarray/description/
