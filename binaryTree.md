# 5.Binary Tree

## 27 Validate Binary Search Tree
### 98. Validate Binary Search Tree

```c
bool isBST(struct TreeNode * curr, struct TreeNode* left, struct TreeNode* right)
{
//printf("val=%d\n", curr->val);
// Base condition
    if (curr == NULL)
        return true;
// if left node exist that check it has
// correct data or not

    if (left != NULL && curr->val <= left->val)
        return false;

// if right node exist that check it has
// correct data or not
    if (right != NULL && curr->val >= right->val)
        return false;

// check recursively for every node.
    return isBST(curr->left, left, curr) &&
           isBST(curr->right, curr, right);
}

bool isValidBST(struct TreeNode* root)
{
    return isBST(root,NULL,NULL);
}
```

### Explanation

The problem is tricky, be careful with the coner test cases such as \[1,1\] and  \[2,1,3,NULL,NULL,5\]

Narrowing down the range between curr-&gt;key+1 ~ int\_MAX  and int\_MIN ~ curr-&gt;key+1 leads to a lethal bug, the program goes wrong when there are two INT\_MIN or INT\_MAX.

so just make sure 

1. if it is a null node, return true

2. check a node whether  left < node && node < right 

3. check left sub tree and right sub tree

[https://leetcode.com/submissions/detail/140847741/](https://leetcode.com/submissions/detail/140847741/)

## 28 Maximum Depth of Binary Tree
### 104. Maximum Depth of Binary Tree

```c
int getDepth(struct TreeNode* curr, int depth, int final)
{
    if(curr == NULL)
    {
        if(depth > final)
        {
            final=depth;
        }
        return final;
    }
    depth++;

    final=getDepth(curr->left, depth,final);
    final=getDepth(curr->right,depth,final);
    printf("val=%d, depth=%d, final=%d\n",curr-&gt; val, depth,final);
    return final;
}

int maxDepth(struct TreeNode* root)
{
    int result;
    result=getDepth(root,0,0);
    return result;
}
```

This is A top down approach, the level is increased and passed down to the child node.

[https://leetcode.com/submissions/detail/140867659/](https://leetcode.com/submissions/detail/140867659/)

這是另一個解法   原理差不多 但這是bottom up的解法  意即   
返回上一層caller時才把depth+1

```c
int maxDepth(struct TreeNode* root)
{
    int maxright;
    int maxleft;
    if(root==NULL)
        return 0;
    maxright=maxDepth(root->right);
    maxleft=maxDepth(root->left);
    printf("%d  %d %d", root->val, maxright,maxleft);
    return (maxright>maxleft)?(maxright +1): (maxleft+1);
}
```

但這題非遞迴的話   其實要用BFS 來解

## 29 Minimum Depth of Binary Tree

```c
int getDepth(struct TreeNode* curr)
{
    int depth;
    int left;
    int right;
    if(curr==NULL)
    {
        return 0;
    }

    if(curr!=NULL && curr->right ==NULL && curr->left==NULL)
    {
        return 1;
    }
    if(  curr->right !=NULL && curr->left!=NULL )
    {
        left=getDepth(curr->left);
        right=getDepth(curr->right);
        depth= left<right?left:right;
    }

    if( curr->right ==NULL && curr->left!=NULL)
    {
        depth=getDepth(curr->left);
    }

    if( curr->right !=NULL && curr->left==NULL)
    {
        depth=getDepth(curr->right);
    }
    return depth+1;
}

int minDepth(struct TreeNode* root)
{
    return getDepth(root);
}
```

### Explanation

Minimum Depth of Binary Tree 和Minimum depth of binary tree 的 概念很像

1. 計算深度的方法可以top down  or bottom up

   1. top-down: we consider the depth of root as 1, and gradually increase the depth when visiting the successors.

   2. bottom-up: we consider the depth of leaf as 1 and gradually increase the depth when visiting the predecessors

2. 考慮node的狀態

   1. null node

   2. node with two child nodes

   3. node with either right or left child node

3. The curr depth can be updated by consider the depth of left subtree and the depth of right subtree.

4. Maximum Depth of Binary Tree 和Minimum depth of binary tree 的差別

   1. Max depth 從root node 計算起 較方便

   2. Min depth 從leaf node算起比較方便

   3. 比較一下兩者演算法,可以發現Minimum depth的算法須額外分辨只有左或右子樹的狀況, 否則只有空子樹的深度被回傳

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
<=的部分
一個是檢查 <=

一個是檢查 > 

但 left>right 都會回傳null  表示子樹會被設成null

3.


## 32 Convert Sorted List to Balanced Binary Search Tree

## 33 Binary Tree Maximum Path Sum
    Given a binary tree, find the maximum path sum.
    
    For this problem, a path is defined as any sequence of nodes from some starting node to any node in the tree along the parent-child connections. The path must contain at least one node and does not need to go through the root.
    
    For example:
    Given the below binary tree,
    
           1
          / \
         2   3
    Return 6.

```c
int maxPath(struct treeNode *root, int *max)
{
    inline MAX( int a, int  b)  { return (a)>(b)?(a):(b);}
    if(root==NULL )
    {
        return 0;
    }
    int left;
    int right;
    left=MAX(maxPath(root->left,max),0);
    right=MAX(maxPath(root->right,max),0);

    if ( *max<left+right+root->val)
    {
       *max=left+right+root->val;
    }
    //printf("max=%d ,left=%d,right=%d\n",*max,left,right);
    return left>right?left+root->val:right+root->val;
}

int maxPathSum(struct TreeNode* root) {
    int max=INT_MIN;    // for the negative value test case
    maxPath(root,&max);
    return max;
}
```
策略:

考慮兩個狀態
single path:  1 -> 2  or 1->3
full path: 1->2->3 

所以對任一node 而言  計算該node 以下左右子樹的max path sum
    
重點:

1. 因為node有負數,max 要從INT_MIN 開始, 這樣即使max path sum 為負, 也會取代INT_MIN

2. 為何回傳left & right 的max path sum 為何要跟0比? 但跟INT_MIN 比 反而有錯??   // [2,-1] 會錯
因為這樣排除了left/right subtree 為負的狀態  接下來的if ( *max<left+right+root->val) 就會變成分別比較  left+root  right + root or root的狀態

3.利用一個global max 當參數  

4.return 回傳左右子樹中比較大的

測資
[9,6,-3,null,null,-6,2,null,null,2,null,-6,-6,-6]
[2,-1,-2]
[-3]

Reference:
http://www.cnblogs.com/grandyang/p/4280120.html
http://blog.csdn.net/wzy_1988/article/details/25290907

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


## 112. Path Sum[](/questions/PathSum.md)
