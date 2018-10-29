
# [2. Math](/math.md)


# [400. Nth digit](https://leetcode.com/problems/nth-digit/)

```python
class Solution:
    def findNthDigit(self, n):
        """
        :type n: int
        :rtype: int
        """
        length=1; # the number of digits in this level
        count=9;  # the total numbers in this level, there are 9 numbers, 1,2,3, ..., 9
        start=1;  # the number starts in this level
        while n>length * count :
            n-=length*count;
            length=length+1;
            count=count*10;
            start=start*10;

        start=start+(n-1)/length;
        num=str(start);
        idx=int(num[(n-1)%length]);
        return idx;


```
ex. n=14
enght=1          length=2
count=9     =>    count=90
start=1           start=10
n=14              n=5

Becasue the sequence starts from 1, 
we can conlude that	there are 9 numbers  -> 1 		-    9
		          			 90          -> 10		-    99
		          			900          -> 100		-   999


# Reference: Leetcode | 400 | Nth Digit | Java   https://www.youtube.com/watch?v=VKYnABegaEI


