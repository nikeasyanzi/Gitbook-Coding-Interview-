# [5.Binary Tree](/binaryTree.md)



## heap
## binary tree


## prefix tree
[208. Implement Trie (Prefix Tree)](/questions/ImplementTrie.md)

## sgement tree

[307. Range Sum Query - Mutable](/questions/RangeSumQuery-Mutable.md)


## [124. Binary Tree Maximum Path Sum](/questions/BinaryTreeMaximumPathSum.md)

## 27 Validate Binary Search Tree

[98. Validate Binary Search Tree](/questions/ValidateBinarySearchTree.md)


## 28 Maximum Depth of Binary Tree
[104. Maximum Depth of Binary Tree](/questions/MinMaxDepthofBinaryTree.md)


## 29 Minimum Depth of Binary Tree
[29 Minimum Depth of Binary Tree](/questions/MinMaxDepthofBinaryTree.md)

## 30 Balanced Binary Tree

[110. Balanced Binary Tree](/questions/BalancedBinaryTree.md)


## 31 Convert Sorted Array to Balanced Binary Search Tree



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
## [437. Path Sum III](/questions/PathSum.md)



## [145. Binary Tree Postorder Traversal](/questions/TreeTraversal.md)
## [94. Binary Tree Inorder Traversal](/questions/TreeTraversal.md)
## [230. Kth Smallest Element in a BST](/questions/TreeTraversal.md)

## [101. Symmetric Tree](/questions/SymmetricTree.md)

## 208. Implement Trie (Prefix Tree)
https://leetcode.com/problems/implement-trie-prefix-tree/description/
https://www.geeksforgeeks.org/trie-insert-and-search/


segement tree
https://www.geeksforgeeks.org/segment-tree-set-1-sum-of-given-range/

## 236. Lowest Common Ancestor of a Binary Tree
[236. Lowest Common Ancestor of a Binary Tree](/questions/LowestCommonAncestorofaBinaryTree.md)


## 671. Second Minimum Node In a Binary Tree
[671. Second Minimum Node In a Binary Tree](/questions/SecondMinimumNodeInaBinaryTree.md)

## 653. Two Sum IV - Input is a BST
[Two Sum IV](/questions/TwoSumIV.md)


## 866. Smallest Subtree with all the Deepest Nodes
[Smallest Subtree with all the Deepest Nodes](/questions/SmallestSubtreewithalltheDeepestNodes.md)


## 114. Flatten Binary Tree to Linked List


## 100. Same Tree

https://leetcode.com/problems/same-tree/description/

很簡單這題

```python

bool recursive(struct TreeNode* p, struct TreeNode* q){
    int left;
    int right;
    if (p ==NULL && q ==NULL) return true;
    if ( p ==NULL && q!=NULL) return false;
    if ( p !=NULL && q==NULL) return false;
    
    right= recursive(p->right,q->right) ;
    left= recursive(p->left,q->left);

    if ((left == false )||  ( right == false ) || (p->val !=q->val)){
        return false;
    }
    else{
        return true;
    }

}

bool isSameTree(struct TreeNode* p, struct TreeNode* q) {
    
    return recursive(p,q);
    
}
```


### 872. Leaf-Similar Trees

https://leetcode.com/contest/weekly-contest-94/problems/leaf-similar-trees/
```python
class Solution:
    def recursive(self,root,result):
        if  root.left ==None and root.right==None:
            result.append(root.val);
            return;
        else:
            if root.left!=None:
                self.recursive(root.left,result);
            if root.right!=None:
                self.recursive(root.right,result);
        
            #return result;
        
    def leafSimilar(self, root1, root2):
        """
        :type root1: TreeNode
        :type root2: TreeNode
        :rtype: bool
        """
        result=[];
        self.recursive(root1,result);
        result2=[];
        self.recursive(root2,result2);
        
        for i in range (len(result2)):
            if result[i] != result2[i]:
                return False;
        return True;
        #print(result);
```


別人的作法

說穿了  就是一直找node   方便省事
```python
class Solution(object):
    def leafSimilar(self, root1, root2):
        """
        :type root1: TreeNode
        :type root2: TreeNode
        :rtype: bool
        """
        return self.findleaf(root1) == self.findleaf(root2)
        
    def findleaf(self, root):
        if not root: return []
        if not (root.left or root.right): return [root.val]
        return self.findleaf(root.left) + self.findleaf(root.right)
```
