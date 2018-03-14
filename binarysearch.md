# 6.Binary Search

##35 Search Insert Position
https://leetcode.com/submissions/detail/143203586/
https://leetcode.com/submissions/detail/143202966/

### while loop版
```c

int bisearchloop(int *nums,int leftidx,int rightidx, int key) {
    int mid;
    int result=-1; //result idx
    int left=leftidx;
    int right=rightidx;
    while(1) {
        if(left<=right) {
            mid=right-left/2 + left;
            if(nums[mid]==key) {
                result=mid;
                break;
            }
            else {
                if(nums[mid]<key) {
                    left=mid+1;
                } else {
                    right=mid-1;
                }
            }
        }
        else {
            result=right+1;
            break;
        }
    }
    return result; 
}                                                                                                                                                                                                     
```
####  遞迴版

```c
int bisearch(int *nums,int left,int right, int key) {

    int mid;
    
    if(left<=right) {
        mid=right-left/2 + left;
        if(nums[mid]==key) return mid;
        else {
    
            if(nums[mid]<key) return bisearch(nums,mid+1,right,key);
            else return bisearch(nums,left,mid-1,key);
        }
    }
    return right+1;
}


```



Q.為什麼 回傳right +1 就會是原本應該要被Insert的位子?

回傳right+1的時候 是left>right 代表這時候是mid > key (key 要放在右邊)
        
    例如 對5 elements 做binary search
    
    1st iteration:
    left=0, right=3, mid=2
    A[mid]<key -> bisearch(A,3,4,key)
    A[mid]>key -> bisearch(A,0,1,key)
    2st iteration:bisearch(A,3,4,key)
    mid=3
    A[mid]>key -> bisearch(A,3,2,key)//key 在mid 右邊但超出範圍 所以為原本mid的位置(right+1)
    A[mid]<key -> bisearch(A,4,4,key)
    3st iteration:bisearch(A,0,1,key)
    mid=1
    A[mid]>key -> bisearch(A,0,0,key)
    A[mid]<key -> bisearch(A,2,1,key) //key在mid左邊但已經超出界線 所以為right+1

考慮三種狀況
1.假設 key 是最小的,剛好符合mid>key的狀況
2.假設 key 是最大的,因為程式最後會檢查最右邊的數 但mid+1 又導致了left>right的狀況
所以回傳right+1沒錯
3.假設key 在陣列的某區間,因為是mid +1 or -1 最後都終止在left>right的狀況
也就是說right是我們要考慮的位子 但right 已經-1了



##36 Find Minimum in sorted rotated array
http://zxi.mytechroad.com/blog/divide-and-conquer/leetcode-153-find-minimum-in-rotated-sorted-array/
http://bangbingsyb.blogspot.tw/2014/11/leecode-find-minimum-in-rotated-sorted.html

```c
int findMin(int* nums, int numsSize)
{
    int left=0;
    int right=numsSize-1;
    int mid;
    if(nums[left]<nums[right])
        return nums[left];
    while(left<right)
    {
        mid= (right-left)/2 + left;
        if(nums[mid]>nums[right])   // the min is at right half
        {
            left=mid;
            if(nums[mid]>nums[mid+1])   
            {
                return mid+1;          //the min is at right and the element mid+1 (at right) is smaller , so we hit the boundary 
            }
        }
        if(nums[mid]<nums[right])     //the min is at left
        {
            right=mid;
            if(nums[mid]<nums[mid-1])
            {
                return mid;         //the min is at left and the element mid-1 (at left) is larger , so we hit the boundary, mid is what we want
            }
        }
    }
    return 0;//dummy
}

```
測資:
int nums[7]= {4,5,6,7, 0, 1,2};
int numsz[6]= {5,0,1,2,3,4};
int num[2]= {2,1};


所以我們考慮

1.一開始先檢查 是不是真的為sorted rotated array  

    如果是sorted array  則a[left]< a[right] 
    sorted rotated array, 則a[left] > a[right]
    
2. 我們都知道binary search 是 看middle value 來決定下一個搜尋的方向 是左邊或右邊
    
    那終止條件 我們就可以在 計算新的mid  與決定決定下一個搜尋的方向時檢查
    
    1.如果min 在右半邊 那剛好mid < mid+1 表示mid+1 為最小  
    (可用測資1驗證)
    1st iteration:
        left=0, right=6 mid=3
        nums[3] > nums[6] 
            left=3;
            檢查mins[3]>mins[4] // hit!!
        
        
    2.如果min 在左半邊 剛好mid>mid-1 表示 mid-1為最小 (可用測資2驗證)
    1st iteration
        left=0, right=5 mid=2
        nums[2] < nums[5]
        
    2st iteration
        left=0, right=2 mid=1
        mums[1]<  nums[2] 
            right=1;
            檢查nums[1] < nums[0]    //hit
        

##37 Find Minimum in sorted rotated array 2
   
    Q154. Find Minimum in Rotated Sorted Array II
    
    Follow up for "Find Minimum in Rotated Sorted Array":
    What if duplicates are allowed?
    
    Would this affect the run-time complexity? How and why?

```c
int recursiveMin(int * nums, int left, int right)
{
    int mid;
    int leftmin;
    int rightmin;
    if(left==right|| left+1==right)
    {
        return nums[left]<nums[right]?nums[left]:nums[right];
    }
    else
    {
        if(nums[left]==nums[right])
        {
            right--;
        }
        mid=(right-left)/2+left;

        leftmin=recursiveMin(nums,mid+1,right);
        rightmin=recursiveMin(nums,left,mid);
        //printf("leftmin=%d, rightmin=%d, mid=%d",leftmin,rightmin );
    }
    return leftmin<rightmin?leftmin:rightmin;
}

int findMin(int* nums, int numsSize) {
    return recursiveMin(nums, 0, numsSize-1);;
}
```
這作法其實很慢 



測資:
    
    int num3[12]= {2, 2, 2, 2, 2, 2, 2, 2, 0, 1, 1, 2};
    int num4[12]= {2, 2, 2, 0, 2, 2, 2, 2, 2, 2, 2, 2};
    int num5[3]= {3,1,1};
    int num6[3]= {1,1,3};
    int num7[3]= {3,1,3};
    int num8[3]= {1,1,1};



Reference:
[\[解题报告\] LeetCode 154. Find Minimum in Rotated Sorted Array II](http://zxi.mytechroad.com/blog/divide-and-conquer/leetcode-154-find-minimum-in-rotated-sorted-array-ii/)

[\[LeetCode\] Find Minimum in Rotated Sorted Array II 寻找旋转有序数组的最小值之二](http://www.cnblogs.com/grandyang/p/4040438.html)

