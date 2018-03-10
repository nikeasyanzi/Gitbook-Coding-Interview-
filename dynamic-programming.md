# 10.Dynamic Programming

## 47 Climbing Stairs

考慮n=0~4的方法
 n=1 -> 一種
 n=2 -> 兩種
 n=3 = f(2) + f(1)=3 
     111
     12
     21
 一共三種
 
 n=4 =f(2)+f(3)= 2+3=5
     1111
     121
     211
     112
     22
 一共五種
 
 其實這題就是fibonacci series
 
```c
 int climbStairs(int n) {
    int i=0;
    int *f=malloc(sizeof(int)*n+1);
    
    f[0]=0;
    f[1]=1;
    f[2]=2;
    
    if(n>=3){
      for(i=3;i<n+1;i++){
       f[i]=f[i-1]+f[i-2];
      }
    }
    return f[n];
}
```
但其實有省記憶體的寫法
```c
int climbStairs(int n) {
    
int i;
int f1=1;
int f2=2;
int final;
    for(i=3;i<n+1;i++){
    final=f1+f2;
    f1=f2;
    f2=final;
    }
    return n>2?final:n;
}
```



## 48 Unique Paths
### 62.Unique Paths

https://leetcode.com/problems/unique-paths/description/

path(i,j)= path(i,k) + path (k,j);

$$ path_{i,j}=  \sum_{j>k>i}  (  path_{i,k} + path_{k,j}) $$




## 49 Unique Paths 2

## 50 Maximum Sum Subarray


arr[i,j]=maxsum{arr[i,k], arr[k,j]};

https://leetcode.com/problems/maximum-subarray/description/

\#\# 51 Maximum Product Subarray

arr[i,j]=maxsum{arr[i,k], arr[k,j]};
https://leetcode.com/problems/maximum-product-subarray/description/

## 52 Coins in a Line / Nim Game

  
    n=1 => first hand win
    n=2 => first hand win
    n=3 => first hand win
    n=4 => second hand win
    
所以 假設N個硬幣  如果能被4整除 則後手勝

```c

bool canWinNim(int n) { 
        if (n % 4> 0) {
            return true;
        }
        return false;
}
```
[LintCode] Coins in a Line II 一条线上的硬币之二
http://www.cnblogs.com/grandyang/p/5864323.html
Reference: