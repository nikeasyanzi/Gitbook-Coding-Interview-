# 5.Binary Tree

## [124. Binary Tree Maximum Path Sum](/questions/BinaryTreeMaximumPathSum.md)

## 27 Validate Binary Search Tree
### 98. Validate Binary Search Tree

[98. Validate Binary Search Tree](/questions/ValidateBinarySearchTree.md)



## 28 Maximum Depth of Binary Tree
### 104. Maximum Depth of Binary Tree
[104. Maximum Depth of Binary Tree](/questions/MinMaxDepthofBinaryTree.md)


## 29 Minimum Depth of Binary Tree
[29 Minimum Depth of Binary Tree](/questions/MinMaxDepthofBinaryTree.md)

## 30 Balanced Binary Tree


```c
#include <math.h>
#define MAX(a,b) (a)>(b)?(a):(b)
#define MIN(a,b) (a)<(b)?(a):(b)
#define ABS(a,b) ((a)>(b))?((a)-(b)):((b)-(a)) //wrong
#define abss(x)  ( ( (x) < 0) ? -(x) : (x) )

int getDepth(struct TreeNode *N, int *result)
{
    int left=0;
    int right=0;
    
    if (N == NULL)
        return 0;
    left=getDepth(N->left,result);
    right=getDepth(N->right,result);
     if( abss(left-right)>1 && *result==true)
    {   
        printf("MAX(left,right)-MIN(left,right) )= %d, %d, left=%d, right=%d, val=%d\n",ABS(left,right), abss(left-right),left,right,N->val);
        *result=false;
    }
    return left>right?+left+1:right+1;
}
int balanceCheck(struct TreeNode* root){
    int result=true;
    getDepth(root,&result);
    return result;
}

bool isBalanced(struct TreeNode* root) {
    return balanceCheck(root); 
}
```

這題 檢查是否為平衡數   定義為 左右子樹level不能大於1
基本上每個node recursive 檢查即可

遇到的問題:

if( ABS(left-right)>1 && *result==true)  ->判斷會錯誤

改成呼叫abss(left-right) 或者 math.h 裡面的abs()  都正常

後來才發現是要多加括號

改成 if( ( ABS(left-right) ) >1 && *result==true)  
或者 
Macro 改成
```c
#define ABS(a,b) (((a)>(b))?((a)-(b)):((b)-(a))) 
```
很明顯 Macro 很雷

## 31 Convert Sorted Array to Balanced Binary Search Tree

![](https://i.imgur.com/4VfzfUn.png)



```c
struct TreeNode* myinsertTree( int *nums, int left,int right)
{
    struct TreeNode *newnode;
    if(left<=right)
    {
        newnode=malloc(sizeof(struct TreeNode));
        int midIdx=(right+left)/2;
        newnode->left=NULL;
        newnode->right=NULL;
        newnode->val=nums[midIdx];
        newnode->left=myinsertTree(nums, left,midIdx-1);
        newnode->right=myinsertTree(nums, midIdx+1,right);
        printf("%d ", newnode->val);
        return newnode;
    }
    return NULL;
}

struct TreeNode* sortedArrayToBST(int* nums, int numsSize) {
    struct TreeNode *root=NULL;
    root=myinsertTree( nums, 0,numsSize-1);
    return root;
}

```


```c
class Solution(object):
    def sortedArrayToBST(self, nums):
        """
        :type nums: List[int]
        :rtype: TreeNode
        """
        return self._sortedArrayToBST(nums, 0, len(nums))

    def _sortedArrayToBST(self, nums, left, right):
        if left == right:
            return None
        mid = (left + right) >> 1
        root = TreeNode(nums[mid])
        root.left = self._sortedArrayToBST(nums, left, mid)
        root.right = self._sortedArrayToBST(nums, mid + 1, right)
        return root


if __name__ == "__main__":
    None
    
```
    
放這兩份code 表示  

1.用於修改root的技巧  用回傳的

回傳下一層的newnode 給上層 的left/right 甚至是原本sortedArrayToBST()

2.
< = 的部分
一個是檢查 < =

一個是檢查 > 

但 left>right 都會回傳null  表示子樹會被設成null

3.


## 32 Convert Sorted List to Balanced Binary Search Tree

## 33 Binary Tree Maximum Path Sum
[124. Binary Tree Maximum Path Sum](/questions/BinaryTreeMaximumPathSum.md)

## 34 Binary Tree Upside Down
測資 {21,12,33,4,15}; 
    
            21
        12    33
    4    15        

=====>

            4
        15    12
            3    21
    

Reference:
https://www.tangjikai.com/algorithms/leetcode-156-binary-tree-upside-down


## [112. Path Sum](/questions/PathSum.md)

## [113. Path Sum II](/questions/PathSum.md)

## [145. Binary Tree Postorder Traversal](/questions/TreeTraversal.md)
## [94. Binary Tree Inorder Traversal](/questions/TreeTraversal.md)
## [230. Kth Smallest Element in a BST](/questions/TreeTraversal.md)

## [101. Symmetric Tree](/questions/SymmetricTree.md)

