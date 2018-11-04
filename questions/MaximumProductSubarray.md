'''python=
class Solution:
    def maxProduct(self, nums):
        
        :type nums: List[int]
        :rtype: int
        """
        max_cur = nums[0]
        min_cur = nums[0]
        result = nums[0]
        for i in range(1,len(nums)):
            if nums[i]>0:
                max_cur=max(nums[i],max_cur*nums[i]);  # case with 0
                min_cur=min(nums[i],min_cur*nums[i]);  # case with 0
            else:
                tmp=min_cur;                
                min_cur=min(max_cur*nums[i],nums[i]);
                max_cur=max(tmp*nums[i],nums[i]);
            result=max(result,max_cur);
        return result    

```
    
      
          
說明:
  因為 有負數  所以 max 的來源有兩種
  * 1. prev_max(最大正數)* curr ()  
  * 2. prev_min (最大負數)* curr 
        # 進一步細分   假設curr >0   考慮 case 1.  並更新 prev_min (因為即使curr>0, 乘上prev_min 會使curr_min 變更小  之後有機會變大)
        #                     <0   考慮 case 2.        prev_min (因為curr<0, 乘上prev_min 會使curr_min 變更小  之後有機會變大)

        ###[-2,3,-4]  [2,3,-2,4]


        ### 以A[i]结尾的max product subarray同时取决于以A[i-1]结尾的max / min product subarray以及A[i]本身。因此，对每个i，需要记录min/max product两个状态：
        ###
        
        ## reference : http://bangbingsyb.blogspot.com/2014/11/leetcode-maximum-product-subarray.html

```