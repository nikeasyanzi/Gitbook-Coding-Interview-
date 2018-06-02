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


以m=4,n=3為例

```c
for i = 1 ~ m
    for j = 1 ~ n
        dp[i,j]=dp[i-1,j]+dp[i,j-1];        
```

dp[1,1]=**dp[0,1]**+dp[1,0];
dp[1,2]=**dp[0,2]**+dp[1,1];
dp[1,3]=**dp[0,3]**+dp[1,2];

dp[2,1]=**dp[1,1]**+dp[2,0];
dp[2,2]=**dp[1,2]**+dp[2,1];
dp[2,3]=**dp[1,3]**+dp[2,2];
    ... (僅寫到i=2的部分)
    

```c
for i = 1 ~ m
    for j = 1 ~ n
        dp[j]=dp[j]+dp[j-1];
        
```

dp[1]=dp[0]+**dp[1]**;
dp[2]=dp[1]+**dp[2]**;
dp[3]=dp[2]+**dp[3]**;


所以可以發現
原本2d 版本中  
dp[0,1],dp[0,2],dp[0,3],dp[1,1],dp[1,2]dp[1,3] 是前一個row

那看1d版本 會發現
也是有參考到上一個row的元素 (dp[1], dp[2], dp[3])

所以可以省略    

Reference:
[LeetCode] Unique Paths I, II https://bangbingsyb.blogspot.tw/2014/11/leetcode-unique-paths-i-ii.html



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


##837. New 21 Game

Intuition:
The same problems as "Climbing Stairs".

Explanation:
In a word,
dp[i]: probability of get points i
dp[i] = sum(last W dp values) / W

Time Complexity:
O(N)

    def new21Game(self, N, K, W):
        if K == 0 or N >= K + W: return 1
        dp = [1.0] + [0.0] * N
        Wsum = 1.0
        for i in range(1, N + 1):
            dp[i] = Wsum / W
            if i < K: Wsum += dp[i]
            if i - W >= 0: Wsum -= dp[i - W]
        return sum(dp[K:])


    precisely, I wanted to understand the 3rd example of N=21, K=17, W=10
    For this case, could you help visualize, how the DP list builds up, so that the last 5 gives the result ?
    
    Could you please tell if my understanding of the below is correct?
    Case: N=3, K=1, W=10
    
    i=1 (drawn card-1) : You win as you get 1(1<=N), P(i=1)=1/10=0.1
    i=2 (drawn card-2) : You win as you get 2(2<=N), P(i=2)=1/10=0.1
    i=3 (drawn card-3) : You win as you get 3(3<=N), P(i=3)=1/10=0.1
    
    All events are independent: Total prob = 0.1+0.1+0.1 = 0.3
    Case: N=3, K=2, W=10
    
    i=1 (draw 1) P(draw=1)=0.1 [call this A], Same event, we do not stop now we can draw either 1 or 2 , as i<K, for drawing 1 or 2 , P(1 or 2)=0.1+0.1=0.2 [call this B], P(complete draw) = P(A)*P(B)=0.1*0.2 = 0.02
    i=2 (drawn card-2) : You win as you get 2(2<=N) and you stop as 2>=K, P(i=2)=1/10=0.1
    i=3 (drawn card-3) : You win as you get 3(3<=N) and you stop as 2>=K, P(i=3)=1/10=0.1
    
    All events are independent: Total prob = 0.02+0.1+0.1 = 0.22
    
In Python code instead of adding dp[i] += Wsum / W you can just assign value dp[i] = Wsum / W
You can also start with only one item in the list dp = [1.0] and extend it by appending items as you go: dp.append(Wsum / W)
class Solution:
    def new21Game(self, N, K, W):
        if N < K:
            return 0.0
        if K == 0 or N >= K - 1 + W:
            return 1.0
        dp = [1.0]
        Wsum = dp[0]
        for i in range(1, N + 1):
            p = Wsum / W
            dp.append(p)
            if i < K:
                Wsum += p
            if i - W >= 0:
                Wsum -= dp[i - W]
        return sum(dp[K:])
The solution can be further optimized in memory size as O(min(K, N, W)) by using a cyclic buffer for dp to keep no more than W last values.

