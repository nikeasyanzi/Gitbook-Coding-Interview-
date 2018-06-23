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
'''
Calculate time needed to arrive the target, sort by the start position.
Loop on each car from the end to the beginning. cur recorde the current biggest time (the slowest).
If another car needs less or equal time than cur, it can catch up this car.
Otherwise it will become the new slowest car, that is new lead of a car fleet.
'''

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
        print ("time=",time); 
        for t in time[::-1]:
            print("res=",res,"cur=",cur,"t=",t);
            if t > cur:
                res += 1;
                cur = t;
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
        

# 855. Exam Room

```python
class ExamRoom:
    
    def __init__(self, N):
        
        """
        :type N: int
        """
        
        self.nodeList=[];
        #self.nodeList.append([0,N-1]);
        self.size=N;

    def maxgap(self):
        addfirst=0;
        addlast=0;
        gap=[];
        gapList=[];
            
        gap[1:]=self.nodeList;
        
        if 0 not in self.nodeList:
            gapList.append(gap[0]);

        for i in range(1,len(gap)):
            gapList.append( math.floor((gap[i]-gap[i-1])/2));
        
        
        if self.size-1 not in self.nodeList:
            gapList.append((self.size-1)  - gap[len(gap)-1]   );
        
        #print("gap=",gap," gapList=",gapList);

         
        maxgap=max(gapList);
        maxgapidx=gapList.index(maxgap);
        #print("maxgap=",maxgap,"gapList=",gapList);

        if  0 not in self.nodeList and maxgapidx==0 :
            self.nodeList.append(0);
            self.nodeList=sorted(self.nodeList);
            #print("1self.nodeList=",self.nodeList);
            return 0;
        else:
            if self.size-1 not in self.nodeList and maxgapidx==len(gapList)-1 :
                self.nodeList.append(self.size-1);
                self.nodeList=sorted(self.nodeList);
                #print("2self.nodeList=",self.nodeList);
                return self.size-1;
        
            else:
                base=self.nodeList[maxgapidx]; 
                self.nodeList.append(base+maxgap);
                #print("base=",base,"maxgap=",maxgap);

                self.nodeList=sorted(self.nodeList);
                #print("3self.nodeList=",self.nodeList);

                return base+maxgap;

    def seat(self):
        """
        :rtype: int
        """
        #print("self.nodeList=",self.nodeList);

        if len(self.nodeList)==0:
            self.nodeList.append(0);
            return 0;
        else:
            if self.nodeList[0]==0 and len(self.nodeList)==1:
                self.nodeList.append(self.size-1);
       
                return self.size-1;
            else:
                return self.maxgap();
        
    def leave(self, p):
        #print("leave ",p);
        self.nodeList.remove(p);
        
        
        """
        :type p: int
        :rtype: void
        """
        
"""
["ExamRoom","seat","seat","seat","seat","leave","seat"]
[[10],[],[],[],[],[4],[]]


["ExamRoom","seat","seat","seat","leave","leave","seat","seat","seat","seat","seat","seat","seat","seat","seat","leave"]
[[10],[],[],[],[0],[4],[],[],[],[],[],[],[],[],[],[0]]

"""
```


心得  該注意的是

1.room size =n    一開始學生會座0 接著 n-1 的位置
2.基本上距離的計算 就是  position [i] - position[i-1] /2 取 floor   找最大即可 
3.但這裡有個問題在邊界的部分  如果position 為 0 或者n-1  就不需 /2
4.接著要考慮就是 萬一如果剛好 邊界的距離是最大  則要把 0 或者 n-1 加回
