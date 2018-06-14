# [3. Array/String](/arraystring.md)


## 6 Two Sum

[Two Sum](questions/TwoSum.md)

# 7 Two Sum 2

[Two Sum](questions/TwoSum.md)

# 8 Two Sum 3 \(locked\)

[Two Sum](questions/TwoSum.md)

# 9 Valid Palindrome

[125. Valid Palindrome](questions/ValidPalindrome.md)

# 10 STRSTR\(\)



https://leetcode.com/submissions/detail/150990173/  暴力法



KMP

http://www.evanlin.com/about-kmp/

http://bangbingsyb.blogspot.tw/2014/11/leetcode-implement-strstr-kmp.html





# 11 Reverse words in a string

[11 Reverse words in a string](questions/ReverseWordsInAString.md)

# 12 Reverse words in a string 2

# 13 ATOI

# 14 Valid Number

# 15 Longest Substring Without Repeating Characters

[3. Longest Substring Without Repeating Characters](/questions/LongestSubstringWithoutRepeatingCharacters.md)

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

## [283 Move Zeroes](https://leetcode.com/problems/move-zeroes/)

[Move Zeroes](/questions/MoveZeroes.md)

# 3. Longest Substring Without Repeating Characters

[https://leetcode.com/problems/longest-substring-without-repeating-characters/description/](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)

```
Given a string, find the length of the longest substring without repeating characters.

Examples:

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```

# [724. Find Pivot Index](/questions/FindPivotIndex.md)

# [448. Find All Numbers Disappeared in an Array](/questions/FindAllNumbersDisappearedinanArray.md) \*

# [41. First Missing Positive ](/questions/FindMissingPositive.md)

# 665. Non-decreasing Array
[665. Non-decreasing Array](/questions/Non-decreasingArray.md)


#26. Remove Duplicates from Sorted Array
[#26. Remove Duplicates from Sorted Array](/questions/RemoveDuplicatesfromSortedArray.md)

# 80. Remove Duplicates from Sorted Array II
[80. Remove Duplicates from Sorted Array II](/questions/RemoveDuplicatesfromSortedArray.md)

#[238. Product of Array Except Self](/questions/ProductofArrayExceptSelf.md)  

#[389. Find the Difference](/questions/FindtheDifference.md)
# 842. Split Array into Fibonacci Sequence

```c
class Solution(object):
    def splitIntoFibonacci(self, S):
        for i in range( len(S)-2):
            x = S[:i+1]
            print(x)
            if x != '0' and x.startswith('0'): break
            a = int(x)
            for j in range(i+1,len(S)-1):
                
                y = S[i+1: j+1]
                print("y="+y)
                if y != '0' and y.startswith('0'): break
                b = int(y)
                fib = [a, b]
                k = j + 1
                while k < len(S):
                    nxt = fib[-1] + fib[-2]
                    print(fib[-1], fib[-2],nxt)
                    nxtS = str(nxt)
                    if nxt <= 2**31 - 1 and S[k:].startswith(nxtS):
                        k += len(nxtS)
                        fib.append(nxt)
                    else:
                        break
                else:
                    if len(fib) >= 3:
                        return fib
        return []
```




#242. Valid Anagram
https://leetcode.com/problems/valid-anagram/description/

```c

bool isAnagram(char* s, char* t) {
    int hash[26]={0};
    int i=0;
    while (*(s+i)!='\0'){
        hash[*(s+i)-'a']++;
        i++;
    }
    i=0;
    while (*(t+i)!='\0'){
        hash[*(t+i)-'a']--;
        i++;
    }
    
    for(i=0;i<26;i++){
        if(hash[i]!=0) return false;
    }
    return true;
}
```


# 845. Longest Mountain in Array
https://leetcode.com/submissions/detail/157178104/

解法很直覺

1.先找 遞增數列
2.再找遞減數列
這邊要注意一下
山腳的idx=right+1

3.兩個都有找到
再用left & right做長度檢查


```c
int longestMountain(int* A, int ASize) {
    
    int i=0;
    int left=0;
    int right=0;
    int max=0;
    int len=0;
    bool increase=false;
    bool decrease=false;
    for(i=0;i<ASize-1;i++){ //find the increasing array
        left=i;
        while(i+1<ASize-1 && A[i]<A[i+1]){
            i++;
            increase=true;
        }
        
        //printf("left=%d i=%d ",left, i);
            if(left!=i){ //find the decreasing array
                while( i+1<ASize && A[i+1]<A[i]){
               // printf("a[%d]=%d \n",i,A[i]);

                right=i+1;  //here is the keypint, 
                i++;
                decrease=true;
               // printf("a[%d]=%d,a[%d+1]=%d \n",i,A[i], i,A[i+1]);

            }    
        }
                
        //printf("right=%d ",right);

        if(increase&&decrease){
            len=right-left+1;
            i=right-1; 
            //printf("len=%d,",len);
        } 
        else{
            i=left;    // here is another keypoint, move the i to left
        }
        
        //printf("left=%d,right=%d,i=%d, increase=%d,decrease=%d\n", left, right,i,increase,decrease);
        
        increase=false;
        decrease=false;
        
        max=max>len?max:len;
        len=0;
    }
    return max;
    
}

```