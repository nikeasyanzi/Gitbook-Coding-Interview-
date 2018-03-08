# 10.Dynamic Programming

\#\# 47 Climbling Stairs

\#\# 48 Unique Paths

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

'''c
bool canWinNim(int n) { 
        if (n % 4> 0) {
            return true;
        }
        return false;
}
'''


Reference: