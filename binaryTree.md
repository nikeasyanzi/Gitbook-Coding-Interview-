# 5.Binary Tree

\[toc\]

## 27 Validate Binary Search Tree

```c
bool isBST(struct TreeNode * curr, struct TreeNode* left, struct TreeNode* right)
{

    //printf("val=%d\n", curr->val);
    // Base condition
    if (curr == NULL) return true;

    // if left node exist that check it has
    // correct data or not

    if (left != NULL && curr->val <= left->val) return false;

    // if right node exist that check it has
    // correct data or not
    if (right != NULL && curr->val >= right->val) return false;

    // check recursively for every node.
    return isBST(curr->left, left, curr) &&
        isBST(curr->right, curr, right);

}

bool isValidBST(struct TreeNode* root) {
    return isBST(root,NULL,NULL);

}
```

the problem is tricky, be careful with test case \[1,1\]  \[2,1,3,NULL,NULL,5\]

narrowing down the range between curr-&gt;key+1 ~ int\_MAX  and int\_MIN ~ curr-&gt;key+1 leads to a lethal bug, the program goes wrong when there are two INT\_MIN or INT\_MAX

[https://leetcode.com/submissions/detail/140847741/](https://leetcode.com/submissions/detail/140847741/)

## 28 Maximum Depth of Binary Tree

\`\`\` =c

int getDepth\(struct TreeNode\* curr, int depth, int final\){

if\(curr == NULL\\)

```c

{

    if\(depth &gt; final\) {

    final=depth;    

    }

 return final;

}

depth++;

final=getDepth\(curr-&gt;left, depth,final\);

final=getDepth\(curr-&gt;right,depth,final\);

printf\("val=%d, depth=%d, final=%d\n",curr-&gt;val, depth,final\);

return final;
```

}

int maxDepth\(struct TreeNode\* root\) {

```
int result;

result=getDepth\(root,0,0\);

return result;
```

}

\`\`\`

[https://leetcode.com/submissions/detail/140867659/](https://leetcode.com/submissions/detail/140867659/)

## 29 Minimum Depth of Binary Tree

## 30 Balanced Binary Tree

## 31 Convert Sorted Array to Balanced Binary Search Tree

## 32 Convert Sorted List to Balanced Binary Search Tree

## 33 Binary Tree Maximum Path Sum

## 34 Binary Tree Upside Down



