

# [3. Array/String](/arraystring.md)

## 78. Subsets
https://leetcode.com/problems/subsets/description/


    Given a set of distinct integers, nums, return all possible subsets (the power set).
    
    Note: The solution set must not contain duplicate subsets.
    
    Example:
    
    Input: nums = [1,2,3]
    Output:
    [
      [3],
      [1],
      [2],
      [1,2,3],
      [1,3],
      [2,3],
      [1,2],
      []
    ]


This is inspired by bit mapping 

we can do it in the way we use in prefix tree.

ex. nums = [1,2,3]

if 0 denotes as picked whereas 1 denotes as unpiacked.

all possible combinations can be expressed as the following two trees.

            0                    1
          /   \                /   \
         0     1              0      1 
        / \   / \            / \    / \
       1   0 1   0          1   0  1   0
  
  
 Thus, 
 *    001 means [3]
 *    011 means [2,3]


```python
class Solution:
    
    def recursive(self,result,final,nums):
        if len(result)==len(nums) :
            
            temp=[nums[i] for i in range(len(nums)) if result[i]==1];
            
            #print("result=",result,"temp=",temp);  
            final.append(temp);
            #print(final)
            return;
        else:
            resultt=result.copy();
            result.append(0);
            
            resultt.append(1);
            
            self.recursive(result,final,nums);
            self.recursive(resultt,final,nums);
            return;
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        result=[];
        final=[];
        self.recursive(result,final,nums);
        #print(final);
        return final;

```     

##  loop version

example 3

counter=0~7


Counter  | 0(000)  | 1(001) | 2(010) | 3(011) | 4(100) | 5 (101) | 6 (110) | 7 (111) |
--------------|:-----:|-----:| ----:|------
j=0    |  | a |    | a|   | a |  |a
j=1    |  |   |  b | b|   |   |b |b
j=2    |  |   |    |  | c | c |c |c    




#reference
https://www.geeksforgeeks.org/power-set/

Another way to do that is adding element one by one
      https://www.jianshu.com/p/ac57b9d3d211  
        