# 8.Misc

40 Spirial Matrix

41 Integer to Roman

42 Roman to Integer

43 Clone Graph




[371.Sum of Two Integers](/questions/SumofTwoIntegers.md)

# [840. Magic Squares In Grid](/questions/MagicSquaresInGrid.md)


846. Hand of Straights
[846. Hand of Straights](/questions/HandofStraights.md)


1. be careful with the index manipulation

2.

```c

class Solution:
    def isNStraightHand(self, hand, W):
        """
        :type hand: List[int]
        :type W: int
        :rtype: bool
        """
        dict = { };
        if(len(hand)%W!=0):
            return False;
        for i in range (len(hand)):
            if str(hand[i]) in dict:
                #print(dict[str(hand[i])])
                dict[str(hand[i])]=dict[str(hand[i])]+1;
            else:   
                dict[str(hand[i])]=1;
       
        dc_sort = sorted(dict.items(), key=lambda x:int(x[0]),reverse = False)
        #print(dc_sort)

        #print(len(dc_sort)-W)
        for i in range(len(dc_sort)-W+1):   //here is the keypoint 1
            #print(i)
            #print(dc_sort)        

            if(dc_sort[i][1]!=0 ):
                for j in range (W-1): // here is the keypoint 2, check if the number is consecutive
                    if( i+j+1 > len(dc_sort) or int (dc_sort[i+j][0])+1 !=int (dc_sort[i+j+1][0]) ): 
                        return False;
                tmp=dc_sort[i][1];
                for j in range (W): // anotehr keypoint, deduct the W
                        #print(j)
                        dc_sort[i+j]=list((str(dc_sort[i+j][0]),dc_sort[i+j][1]-tmp))
                        dc_sort[i]=list((str(dc_sort[i][0]),0))

                        if(int(dc_sort[i+j][1]) <0 ):
                            return False;
                        #print(dc_sort)        

            #print(dc_sort)     
        for i in range(len(dc_sort)):   
             if(dc_sort[i][1]!=0 ):
                    return False;
        return True;
```


# 853. Car Fleet

```python
class Solution:
    def carFleet(self, target, position, speed):
        """
        :type target: int
        :type position: List[int]
        :type speed: List[int]
        :rtype: int
        """
        time = [float(target - p) / s for p, s in sorted(zip(position, speed))]
        res = cur = 0
        #print ("time=",time);
        for t in time[::-1]:
            #print("res=",res,"cur=",cur);
            if t > cur:
                res += 1
                cur = t
        return res
    

```
影片解說
https://www.youtube.com/watch?v=H5w6doOXz10


測資:
case1:
12
[10,8,0,5,3,1]
[2,4,1,1,3,4]
ans:3

case2:
12
[10,8]
[2,5]
ans:1

這題看似簡單   其實沒那麼好懂 
        

