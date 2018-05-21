26. Remove Duplicates from Sorted Array

    
    Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.
    
    Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.
    
    Example 1:
    
    Given nums = [1,1,2],
    
    Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.
    
    It doesn't matter what you leave beyond the returned length.
    Example 2:
    
    Given nums = [0,0,1,1,1,2,2,3,3,4],
    
    Your function should return length = 5, with the first five elements of nums being modified to 0, 1, 2, 3, and 4 respectively.
    
    It doesn't matter what values are set beyond the returned length.  
    
      
      
  
 
 這題跟 [move zero](/questions/MoveZeroes.md) 很像 兩個指標就可以完成  
  
```c
  void swap(int *a,int *b){
    //printf("*a=%d,*b=%d\n",*a,*b);   
    if(*a!=*b){
        *a^=*b;
        *b^=*a;
        *a^=*b;
    }
    //printf("*a=%d,*b=%d\n",*a,*b);   
}

int removeDuplicates(int* nums, int numsSize) {
    int *ptr =nums;
    int i=0;
    int j=1;
    int target=nums[i];
    if (numsSize==0) return 0;
    while( j<numsSize){
        //printf("i=%d,j=%d,target=%d\n",i,j,target);
        if(target<nums[j]){
            i++;
            swap(&nums[i],&nums[j]);
            target=nums[i];
        }
        j++;
    }  
    //printf("i=%d",i);
    return i+1; // return the number of distinct numbers
 
}
```
  
  https://leetcode.com/submissions/detail/153996226/

i, j, & target
目標是  j loop over the whole array and 找 一個大於target的值
tast case:

1 1 2 3

1,1,1,2,2,2,3,3,4,4


