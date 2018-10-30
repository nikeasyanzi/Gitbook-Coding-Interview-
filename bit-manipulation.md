# 7.Bit Manipulation

## 38 Single Number

這題其實就是用XOR

The characteristic of XOR operation is when x ^ x =0,  x ^ ~x =1

giving a set of numbers a,b,c,d,e, ... ,x,y,z while z is the one which appears onces and others appear twices

it can be expressed as follows:

a ^b.... ^x ^y ^z ^a ^b ... ^x ^y  
=a ^a ^b ^b ... ^x ^x ^y ^y ^z  
=0 ^0 ... ^0 ^ z  
=z



## 39 Single Number \|\|

> 这个解法可以初学者会看不明白，详细说明一下：  
> 1）有个数只出现一次，换个思考角度表达，用二进制的思考，即二进制每一位上都有一个数只出现一次  
> 那对上面三个数1、2、1（简单为例子使用4位表示）：  
> 0,0,0,1  
> 0,0,1,0  
> 0,0,0,1
>
> 第一位：1,0,1
>
> 第二位：0,1,0
>
> 第三位：0,0,0
>
> 第四位：0,0,0
>
> 2）我们使用三个变量one、two、three来存储每一个位上出现的1、2、3次的情况（其实是模拟了3进制的概念），拿第一位思考（特别注意one、two、three的每一位，都表示当前位出现了1次）  
> 使用上面的第一位的序列1,0,1为例子
>
> 3）因此，"拼凑"出的算法就是
>
> two = two \| \(one & num\[i\]\)  // this  appears ahead of one=one^num\[i\] since a bug occurs when a new muber comming in
>
> one = one ^ num\[i\]
>
> three = one & two
>
> one = ~three
>
> two = ~three

[https://www.jianshu.com/p/758e799614b2](https://www.jianshu.com/p/758e799614b2)

## 39 Single Number \|\|\|

這題其實事Single Number的進階  還沒時間看

[https://segmentfault.com/a/1190000004886431](https://segmentfault.com/a/1190000004886431 "leetcode 算法解析（一）：260. Single Number III")

[http://fisherlei.blogspot.com/2015/10/leetcode-single-number-iii-solution.html](http://fisherlei.blogspot.com/2015/10/leetcode-single-number-iii-solution.html)

這邊我補充一下其他相關  bit manipulation的應用

1\) How to check if a given number is a power of 2 ?

2\) Count the number of ones in the binary representation of the given number.

3\) Check if the ith bit is set in the binary form of the given number.

4\) How to generate all the possible subsets of a set ?

[https://www.hackerearth.com/practice/notes/bit-manipulation/](https://www.hackerearth.com/practice/notes/bit-manipulation/)


### 190. Reverse Bits

```c
uint32_t reverseBits(uint32_t n) {
    uint32_t x=n;
        x = ((x & 0x55555555) << 1) | ((x & 0xAAAAAAAA) >> 1);  
        x = ((x & 0x33333333) << 2) | ((x & 0xCCCCCCCC) >> 2);  
        x = ((x & 0x0F0F0F0F) << 4) | ((x & 0xF0F0F0F0) >> 4);  
        x = ((x & 0x00FF00FF) << 8) | ((x & 0xFF00FF00) >> 8);  
        x = ((x & 0x0000FFFF) << 16) | ((x & 0xFFFF0000) >> 16);  
        return x;  
}
```
https://leetcode.com/problems/reverse-bits/description/
https://articles.leetcode.com/reverse-bits/

### 693. Binary Number with Alternating Bits
```c
class Solution {
    public boolean hasAlternatingBits(int n) {
        int cur = n % 2;
        n /= 2;
        while (n > 0) {
            if (cur == n % 2) return false;
            cur = n % 2;
            n /= 2;
        }
        return true;
    }
}
```


```c
bool hasAlternatingBits(int n) {
    
int tmp = (n^(n>>1)); 
        return (tmp&(tmp+1))==0; 
}
```

### 191. Number of 1 Bits

https://leetcode.com/problems/number-of-1-bits/submissions/1

```c
int hammingWeight(uint32_t n) {
    int count=0;
    while(n>0){
        count=count+(n & 1);
        n=n>>1;
    }
    return count;
}
```
### 338. Counting Bits



這題需要加強了解

https://leetcode.com/problems/counting-bits/description/
```python
class Solution:
    def countBits(self, num):
        """
        :type num: int
        :rtype: List[int]
        """

        ans = [0]*(num+1);
        for x in range(1, num+1):
            #print (x);
            ans[x] = ans[x>>1] + (x & 1);
            
        #print (ans);
        return ans;
```
因为 i&(i-1) 的结果是将i的二进制表示中最右边的‘1’消除掉，因此i中1的个数和i&(i-1)中1的个数相差1.

ans[n] = ans[n & (n - 1)] + 1


这个题用DP的方法。把第i个数分成两种情况，如果i是偶数那么，它的二进制1的位数等于i/2中1的位数；如果i是奇数，那么，它的二进制1的位数等于i-1的二进制位数+1，又i-1是偶数，所以奇数i的二进制1的位数等于i/2中二进制1的位数+1. 所以上面的这些可以很简单的表达成answer[i] = answer[i >> 1] + (i & 1)。

answer[i] = answer[i >> 1] + (i & 1)。




i    bin       '1'    i&(i-1)
0    0000    0
-----------------------
1    0001    1    0000
-----------------------
2    0010    1    0000
3    0011    2    0010
-----------------------
4    0100    1    0000
5    0101    2    0100
6    0110    2    0100
7    0111    3    0110
-----------------------
8    1000    1    0000
9    1001    2    1000
10   1010    2    1000
11   1011    3    1010
12   1100    2    1000
13   1101    3    1100
14   1110    3    1100
15   1111    4    1110

"""

# [29 Divide Two Integers] (/questions/DivideTwoIntegers.md)
https://prismoskills.appspot.com/lessons/Bitwise_Operators/Efficient_Divide.jsp
