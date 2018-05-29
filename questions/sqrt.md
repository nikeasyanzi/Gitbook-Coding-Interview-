
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


https://blog.csdn.net/ycf74514/article/details/48996383