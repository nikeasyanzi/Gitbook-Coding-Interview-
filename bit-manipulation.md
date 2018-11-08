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

### [191. Number of 1 Bits](/questions/Numberof1Bits.md)


### [338. Counting Bits](/questions/CountingBits.md)



# [29 Divide Two Integers](/questions/DivideTwoIntegers.md)


這邊我補充一下其他相關 bit manipulation的應用

1\) How to check if a given number is a power of 2 ?

2\) Count the number of ones in the binary representation of the given number.

3\) Check if the ith bit is set in the binary form of the given number.

4\) How to generate all the possible subsets of a set ?

[https://www.hackerearth.com/practice/notes/bit-manipulation/](https://www.hackerearth.com/practice/notes/bit-manipulation/)

檢查power of 2
the representation of a power of 2:
x: 0…000…010…0 頂多一個為1

the representation of not a power of 2:
x: 0…000…011…0 至少兩個為1
所以 用 x&(x-1) 一次去掉一個1 剛好可以用來檢查是否為偶數
假設 x為偶數 則x&(x-1) 結果為0

https://blog.kuoe0.tw/posts/2012/01/26/bitwise-operation-utlization/

https://graphics.stanford.edu/~seander/bithacks.html#IntegerAbs

http://puremonkey2010.blogspot.tw/2011/05/c-bitwise-operation.html

