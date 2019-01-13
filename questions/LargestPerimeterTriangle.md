

### 976.Largest Perimeter Triangle

  


```python

class Solution:
    def largestPerimeter(self, A):
        """
        :type A: List[int]
        :rtype: int
        """
        sortedA=sorted(A,reverse=True);
        #print(sortedA);
        """
        for i in range(len(sortedA)):
            if i + 2 < len(sortedA) and sortedA[i + 1] + sortedA[i + 2] > sortedA[i]:
                return sum(sortedA[i:i + 3])
        
        """
                    
        for i in range(0,len(sortedA)):
            for j in range(i+1,len(sortedA)):
                for k in range(j+1,len(sortedA)):
                    if i + 2 < len(sortedA) and sortedA[j] + sortedA[k] > sortedA[i]: 
                        #print(sortedA[j],sortedA[k],sortedA[i]);
                        return sortedA[j] + sortedA[k]+ sortedA[i];
        
        return 0;
    
    #一開始搞錯題目意思 還傻傻用三個迴圈  導致
    
    #但這題利用  兩邊和大於第三邊 的定理
    # 我們先把陣列排序過 直接從最大的數值開始檢查起  就可以找到面積最大的


```







之前卡在一個問題:

1,2,3,4, 8, 16

3, 4, 8 已經不行了  3, 4, 16 還有需要考慮嗎?

  
5 4 3 2 1 一樣也有這狀況

5, 4, 3不行 5,4,2就不用檢查了~

