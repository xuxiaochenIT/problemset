### 题目地址

[https://leetcode-cn.com/problems/binary-tree-maximum-path-sum/](https://leetcode-cn.com/problems/binary-tree-maximum-path-sum/)

### 题目描述

- 给定一个非空二叉树，返回其最大路径和。  

  本题中，路径被定义为一条从树中任意节点出发，达到任意节点的序列。该路径至少包含一个节点，且不一定经过根节点。  

**示例 1：**

> 输入: [1,2,3]  
>   
>        1  
>       / \  
>      2   3  
>   
> 输出: 6

**示例 2：**

> 输入: [-10,9,20,null,null,15,7]  
>   
>    -10  
>    / \  
>   9  20  
> 　/  \  
>  15 7  
>   
> 输出: 42

### 题解

```
class Solution:
    def maxPathSum(self, root: TreeNode) -> int:
        def sum(root):
            if not root:
                return 0
            l = sum(root.left)
            r = sum(root.right)
            nonlocal ret
            ret = max(ret , l+r+root.val , root.val , root.val+l , root.val+r)
            return max(root.val , root.val+l , root.val+r)
        ret = float('-inf')
        sum(root)
        return ret
```
