# 2.Math

3 Reserve Integer

```c
#include <math.h>
#include <limits.h>
int reverse(int x) {
        
    int count=0;
    int result=0;
    while(x!=0)
    {
        if(abs(result)>INT_MAX/10) return 0;// check if it will overflow after reverse 
        result=result*10+x%10;
        x=x/10;
    } 
    return result;
}

```c


這題真的很妙  這解法是官方解法 有幾個地方可以注意

1.不須考慮正負號 while 判斷式改成  x!=0
因為不管x 正負,最後會歸零

2.if判斷式 
用於事先的overflow 檢查
if(abs(result)>INT_MAX)  但寫這樣是查不出來的  

測資:
1534236469  (用於overflow偵測)

Reference:
http://www.cnblogs.com/grandyang/p/4125588.html


4 Plus one

5 Palindrome Number



