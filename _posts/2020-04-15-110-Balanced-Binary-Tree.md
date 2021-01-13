---
layout:	post
title: 'LeetCode: 110. Balanced Binary Tree'
subtitle:
date: 2020-04-15
author: 吴昊
header-img:
catalog: true
tags: LeetCode

---



# 110. Balanced Binary Tree

## Description

Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as:

>   a binary tree in which the left and right subtrees of *every* node differ in height by no more than 1.

 

**Example 1:**

Given the following tree `[3,9,20,null,null,15,7]`:

```
    3
   / \
  9  20
    /  \
   15   7
```

Return true.

**Example 2:**

Given the following tree `[1,2,2,3,3,null,null,4,4]`:

```
       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
```

Return false.



---

## My Solution

```c++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */

class Solution{
    public:
    bool isBalanced(TreeNode* root){
        if (root == NULL){
            return true;
        }
        if (abs(helper(root->left) - helper(root-right))<=1 && isBalanced(root->left) && isBalanced(root->right)){
            return ture;
        }else{
            return false;
        }
    }
    
    int helper(TreeNode* root){
        if (root == NULL){
           	return 0;
        }
        int ld = helper(root->left);
        int rd = helper(root->right);
        return max(ld, rd)+1;
    }
}
```

