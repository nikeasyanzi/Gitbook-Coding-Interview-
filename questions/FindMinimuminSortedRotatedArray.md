# [Binary Search](/binarysearch.md)

## 153. Find Minimum in Rotated Sorted Array

https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/


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
