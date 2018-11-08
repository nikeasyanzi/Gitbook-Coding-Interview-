#[7.Bit Manipulation](/bit-manipulation.md)


## [190. Reverse Bits](https://leetcode.com/problems/reverse-bits/)

基本上就是左右移動  但要注意  是先從小的開始  所以 

可以看出  是01 -> 10 -> 00 -> 11 

用xor 做

``` c=

// 另一种巧妙的做法 /
0x55555555 = 0101   0101   0101   0101   0101   0101   0101   0101   
0xAAAAAAAA = 1010   1010   1010   1010   1010   1010   1010   1010   
0x33333333 = 0011   0011   0011   0011   0011   0011   0011   0011   
0xCCCCCCCC = 1100   1100   1100   1100   1100   1100   1100   1100 


```

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
https://articles.leetcode.com/reverse-bits/

