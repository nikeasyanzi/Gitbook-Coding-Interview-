# 6.Binary Search

##35 Search Insert Position
[Search Insert Position](/questions/SearchInsertPosition.md)
##36. Find Minimum in Rotated Sorted Array
[Find Minimum in Rotated Sorted Array](/questions/FindMinimuminSortedRotatedArray.md)

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

# 33. Search in Rotated Sorted Array
```c

int bisearch(int *a,int l,int r,int key){
    printf("left=%d,right=%d\n",l,r); 
    int mid;
    if(l<r){
        mid=(r-l)/2+l;
        if(a[mid]==key){
            
          return mid;
          
        }else{
          if(a[mid]<key) return bisearch(a,mid+1,r,key);
            else return bisearch(a,l,mid-1,key);       
        }
    }
    
    if(l==r){
      printf("left=%d,right=%d\n",l,r); 
      if(a[l]==key) return l;
    } 
    return -1;
}

int search(int* nums, int numsSize, int target) {
    int l=0;
    int r=numsSize-1;
    while(nums[l]>target ){ //remove left 
        l++;
        if(l==r) break;
    }
    while(nums[r]<target) { //remove right
        r--;
        if(l==r) break;
    }
    return bisearch(nums,l,r,target); 
}

```
https://leetcode.com/submissions/detail/150060154/

4 5 6 7 0 1 2 3

有個特性要清楚
for any key in between the series 必定可以往左移或往右移
but for any key not in the series, it becomes loop over 
ex.
key=6 search sequence is 4 5 6 7
key=2 search sequence is 0 1 2 3



Search in Rotated Sorted Array II
https://leetcode.com/submissions/detail/150063970/
```c
bool bisearch(int *a,int l,int r,int key){
    int mid;

    if(l<r){
        while(a[l]==a[r] && l!=r) r--; //remove the duplicate elements

        while(a[l]>key ){
        l++;
        if(l==r) break;    
        }
        
        while(a[r]<key) {
        r--;
        if(l==r) break;    
        }    

        mid=(r-l)/2+l;

        if(a[mid]==key){
          return true;
        }else{
          if(a[mid]<key) return bisearch(a,mid+1,r,key);
            else return bisearch(a,l,mid-1,key);       
        }
    }
    
    if(l==r){
      if(a[l]==key) return true;
    } 

    return false;
}

bool search(int* nums, int numsSize, int target) {
    return bisearch(nums,0,numsSize-1,target);
}
```

作法跟上一題一樣

1.移除在頭尾的重複element
2.中間兩個while 迴圈  來保證數列變成是左小右大(中間可能還有其他重複)
ex. 4 4 6 7 1 3 3 3 4 4

->  4 4 6 7 1 3 3 3

->  if key = 2
1 3 3 3

-> if key =5

4 4 6 7

if key = 0 變成單調搜尋

