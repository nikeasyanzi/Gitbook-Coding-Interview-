# [3. Array/String](/arraystring.md)

## [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/)

https://leetcode.com/problems/move-zeroes/description/

    Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.
    
    For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].
    
    Note:
    You must do this in-place without making a copy of the array.
    Minimize the total number of operations.

```
void swap(int *i,int *j){
    if (*i!=*j){
        *i^=*j;
        *j^=*i;
        *i^=*j;
    }
}

void moveZeroes(int* nums, int numsSize) {
    int i;
    int tail=0;
    for (i=0;i<numsSize;i++){
        if(nums[i]!=0){
            printf(" %d ",nums[i]);
            swap(&nums[i],&nums[tail]);
            tail++;
        }
    }
}
```

tail 最後會指向一個zero element

此時nums[i] 又只看non zero element

因此得到把所有zero element往後移的效果

