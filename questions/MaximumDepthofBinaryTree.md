[# 5.Binary Tree](/binaryTree.md)

### 104. Maximum Depth of Binary Tree


https://leetcode.com/problems/maximum-depth-of-binary-tree/




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

