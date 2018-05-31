
# [# 2.Math](/math.md)

# 69. Sqrt(x)


https://leetcode.com/problems/sqrtx/submissions/1



```c
int mySqrt(int x) {
    
    if (x<=1) return x;
    
    double last = 0;
    double res = 1;
    while (res != last)
    {
        last = res;
        res = (res + x / res) / 2;
    }
    return (int)res;
}
```

1. 開根號的背景

x^2=y  求 x

則  1 < x < y/2

牛頓法式目前已知最快  除了 quack III 的magic code

這邊針對牛頓法原理說明一下

函數可以改寫成  f(x)=x^2-y=0
後面看不懂  嗚嗚


https://blog.csdn.net/ycf74514/article/details/48996383

http://www.cnblogs.com/AnnieKim/archive/2013/04/18/3028607.html