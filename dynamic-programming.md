# 10.Dynamic Programming

## 

## 48 Unique Paths

### 62.Unique Paths

[https://leetcode.com/problems/unique-paths/description/](https://leetcode.com/problems/unique-paths/description/)

path\(i,j\)= path\(i,k\) + path \(k,j\);

$$ path_{i,j}=  \sum_{j>k>i}  (  path_{i,k} + path_{k,j}) $$

以m=4,n=3為例

```c
for i = 1 ~ m
    for j = 1 ~ n
        dp[i,j]=dp[i-1,j]+dp[i,j-1];
```

dp\[1,1\]=**dp\[0,1\]**+dp\[1,0\];  
dp\[1,2\]=**dp\[0,2\]**+dp\[1,1\];  
dp\[1,3\]=**dp\[0,3\]**+dp\[1,2\];

dp\[2,1\]=**dp\[1,1\]**+dp\[2,0\];  
dp\[2,2\]=**dp\[1,2\]**+dp\[2,1\];  
dp\[2,3\]=**dp\[1,3\]**+dp\[2,2\];  
    ... \(僅寫到i=2的部分\)

```c
for i = 1 ~ m
    for j = 1 ~ n
        dp[j]=dp[j]+dp[j-1];
```

dp\[1\]=dp\[0\]+**dp\[1\]**;  
dp\[2\]=dp\[1\]+**dp\[2\]**;  
dp\[3\]=dp\[2\]+**dp\[3\]**;

所以可以發現  
原本2d 版本中  
dp\[0,1\],dp\[0,2\],dp\[0,3\],dp\[1,1\],dp\[1,2\]dp\[1,3\] 是前一個row

那看1d版本 會發現  
也是有參考到上一個row的元素 \(dp\[1\], dp\[2\], dp\[3\]\)

所以可以省略

Reference:  
\[LeetCode\] Unique Paths I, II [https://bangbingsyb.blogspot.tw/2014/11/leetcode-unique-paths-i-ii.html](https://bangbingsyb.blogspot.tw/2014/11/leetcode-unique-paths-i-ii.html)

## 49 Unique Paths 2

## 50 Maximum Sum Subarray

class Solution:  
    def maxSubArray\(self, nums\):  
        """  
        :type nums: List\[int\]  
        :rtype: int  
        """  
        A=nums;  
        for i in range\(1,len\(nums\)\):  
            if nums\[i\]&gt;nums\[i\]+nums\[i-1\]:  
                A\[i\]=nums\[i\];  
            else:  
                A\[i\]=nums\[i\]+nums\[i-1\];

```
    #print(A);
    return max(A);
```

[https://leetcode.com/problems/maximum-subarray/description/](https://leetcode.com/problems/maximum-subarray/description/)  
[https://www.youtube.com/watch?v=7J5rs56JBs8](https://www.youtube.com/watch?v=7J5rs56JBs8)

## 51 Maximum Product Subarray

arr\[i,j\]=maxsum{arr\[i,k\], arr\[k,j\]};  
[https://leetcode.com/problems/maximum-product-subarray/description/](https://leetcode.com/problems/maximum-product-subarray/description/)

## 52 Coins in a Line / Nim Game

```
n=1 => first hand win
n=2 => first hand win
n=3 => first hand win
n=4 => second hand win
```

所以 假設N個硬幣  如果能被4整除 則後手勝

```c
bool canWinNim(int n) { 
        if (n % 4> 0) {
            return true;
        }
        return false;
}
```

\[LintCode\] Coins in a Line II 一条线上的硬币之二  
[http://www.cnblogs.com/grandyang/p/5864323.html](http://www.cnblogs.com/grandyang/p/5864323.html)  
Reference:

## 837. New 21 Game \(to do

[837. New 21 Game](/questions/New21Game.md)

## 847. Shortest Path Visiting All Nodes \(to do



