# 3.Array/String

## 6 Two Sum

[Two Sum](questions/TwoSum.md)

# 7 Two Sum 2

# 8 Two Sum 3

# 9 Valid Palindrome

[Valid Palindrome](questions/ValidPalindrome.md)

# 10 STRSTR\(\)

# 11 Reverse words in a string

[11 Reverse words in a string](questions/ReverseWordsInAString.md)

# 12 Reverse words in a string 2

# 13 ATOI

# 14 Valid Number

# 15 Longest Substring Without Repeating Characters

# 16 Longest Substring with At Most Two Distinct Characters

# 17 Missing Ranges

# 18 Longest Palindromic Substring

# 19 One Edit Distance \(locked\)

# 20 Read N Characters Given Read4

# 21 Read N Characters Given Read4 – Call multiple times

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





#### 283 [Move Zeroes](https://leetcode.com/problems/move-zeroes/)
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

Note:
You must do this in-place without making a copy of the array.
Minimize the total number of operations.

```
void swap(int *i,int *j){
    if (*i!=*j){
        *i^=*j;
        *j^=*i;
        *i^=*j;
    }
}

void moveZeroes(int* nums, int numsSize) {
    int i;
    int tail=0;
    for (i=0;i<numsSize;i++){
        if(nums[i]!=0){
            printf(" %d ",nums[i]);
            swap(&nums[i],&nums[tail]);
            tail++;
        }
    }
}
```

tail 最後會指向一個zero element

此時nums[i] 又只看non zero element

因此得到把所有zero element往後移的效果


