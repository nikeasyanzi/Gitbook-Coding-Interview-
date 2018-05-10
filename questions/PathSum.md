# [# 5.Binary Tree](/binaryTree.md)

## 112. Path Sum

https://leetcode.com/problems/path-sum/description/

Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

Note: A leaf is a node with no children.

Example:

Given the below binary tree and sum = 22,

          5
         / \
        4   8
       /   / \
      11  13  4
     /  \      \
    7    2      1
return true, as there exist a root-to-leaf path 5->4->11->2 which sum is 22.

```go
func recursive(root *TreeNode, sum int) bool{
    left := false  
    right := false  
    if root == nil {
        return false;
    }
    fmt.Printf("sum=%d root.Val=%d\n ",sum,root.Val);

    if root.Left==nil && root.Right==nil {
        if root.Val==sum {
            return true;
        }else{
            return false;
        }
    }else{
      if root.Left!=nil {
        left=recursive(root.Left,sum-root.Val)
      }  
      if root.Right!=nil { 
       right=recursive(root.Right,sum-root.Val)
      }          
    }
    return left || right
}
func hasPathSum(root *TreeNode, sum int) bool {
    return recursive(root,sum)
}

```
## 
Path Sum || 
https://leetcode.com/problems/path-sum-ii/description/
用go 寫 感覺怪怪的  哭哭


這code 不對  但de補出來
import "fmt"

func recursive(root *TreeNode, sum int, current []int, final [][]int)  [][]int{
    if root ==nil{
        return final
    }else {
        current=append (current,root.Val)
        if root.Val==sum && root.Left==nil && root.Right==nil{
            final=append(final,current)
            return final

        }else{
            final=recursive(root.Right,sum-root.Val,current, final)   
            final=recursive(root.Left,sum-root.Val,current,final)
        }
        
    }
    return final

}

func pathSum(root *TreeNode, sum int) [][]int {
    var current []int
    var final [][]int
    
    final=recursive(root,sum,current,final)
    
    return final 
}