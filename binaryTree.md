# 5.Binary Tree

## 27 Validate Binary Search Tree

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

the problem is tricky, be careful with test case \[1,1\]  \[2,1,3,NULL,NULL,5\]

narrowing down the range between curr-&gt;key+1 ~ int\_MAX  and int\_MIN ~ curr-&gt;key+1 leads to a lethal bug, the program goes wrong when there are two INT\_MIN or INT\_MAX

[https://leetcode.com/submissions/detail/140847741/](https://leetcode.com/submissions/detail/140847741/)

## 28 Maximum Depth of Binary Tree

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

[https://leetcode.com/submissions/detail/140867659/](https://leetcode.com/submissions/detail/140867659/)

這是另一個解法   原理差不多

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
### explaination

1. 計算深度的方法可以top down  or bottom up

   1. top-down: we consider the depth of root as 1, and gradually increase the depth when visiting the successors.   

   2. bottom-up: we consider the depth of leaf as 1 and gradually increase the depth when visiting the predecessors

2. 考慮node的狀態
   
   1. null node
   
   2. node with two child nodes
   
   3. node with either right or left child node
   
3. the curr depth can be updated by consider the depth of left subtree and the depth of right subtree.

4. Maximum Depth of Binary Tree 和Minimum depth of binary tree 的差別

   1. Max depth 從root node 計算起 較方便

   2. Min depth 從leaf node算起比較方便

   3. 比較一下兩者演算法,可以發現Minimum depth的算法須額外分辨只有左或右子樹的狀況, 否則只有空子樹的深度被回傳 

## 30 Balanced Binary Tree

## 31 Convert Sorted Array to Balanced Binary Search Tree

## 32 Convert Sorted List to Balanced Binary Search Tree

## 33 Binary Tree Maximum Path Sum

## 34 Binary Tree Upside Down



