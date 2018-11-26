# [3. Array/String](/arraystring.md)


##[945. Minimum Increment to Make Array Unique](https://leetcode.com/submissions/detail/191588202/)

```python
class Solution:
    def minIncrementForUnique(self, A):
        """
        :type A: List[int]
        :rtype: int
        """
        A.sort();
        nums_moves = 0;

        for i in range(1,len(A)):
            #print("A=",A,"A[i]=",A[i],"A[i-1]=",A[i-1],"num_moves=",nums_moves);
            if A[i]<=A[i-1]:
                nums_moves=nums_moves+A[i-1]-A[i]+1;
                A[i]=A[i-1]+1;
        return nums_moves;

"""
```


[1,2,2]
[3,2,1,2,1,7]
[2,2,2,1]




ex.

[1,2,2]

i=0
1,2,2


i=1
1,2,2

i=2
i,2,3    


[3,2,1,2,1,7] => [1,1,2,2,3,7]
i=0;
[1,1,2,2,3,7]

i=1;
[1,2,2,2,3,7]

i=2;
[1,2,3,2,3,7]

i=3;
[1,2,3,4,3,7]

"""
