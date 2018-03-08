# 10.Dynamic Programming

\#\# 47 
Climbling Stairs2

  n=3 = f(2) + f(1)=3 
 111
 12
 21
 
 n=4 =f(2)+f(3)= 2+3=5
 1111
 121
 211
 112
 22
 
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
```c

\#\# 48 Unique Paths

path(i,j)= path(i,k) + path (k,j);

$$-b \pm \sqrt{b^2 - 4ac} \over 2a$$
  

\#\# 49 Unique Paths 2

\#\# 50 Maximum Sum Subarray


arr[i,j]=maxsum{arr[i,k], arr[k,j]};

https://leetcode.com/problems/maximum-subarray/description/

\#\# 51 Maximum Product Subarray

arr[i,j]=maxsum{arr[i,k], arr[k,j]};
https://leetcode.com/problems/maximum-product-subarray/description/

\#\# 52 Coins in a Line

  
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


Reference: