# 7.Bit Manipulation

## [38 Single Number](/questions/SingleNumber.md)

## [137. Single Number II](/questions/SingleNumber.md)

## [260. Single Number III](/questions/SingleNumber.md)

### 190. Reverse Bits
[190. Reverse Bits](/questions/ReverseBits.md)

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




i  |  bin   |  '1' |   i&(i-1)
-----------------------
0  |  0000  |  0   |
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

# [29 Divide Two Integers](/questions/DivideTwoIntegers.md)


這邊我補充一下其他相關 bit manipulation的應用

1\) How to check if a given number is a power of 2 ?

2\) Count the number of ones in the binary representation of the given number.

3\) Check if the ith bit is set in the binary form of the given number.

4\) How to generate all the possible subsets of a set ?

[https://www.hackerearth.com/practice/notes/bit-manipulation/](https://www.hackerearth.com/practice/notes/bit-manipulation/)



