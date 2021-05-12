---
layout:	post
title: 'LeetCode: 98. Validate Binary Search Tree'
subtitle:
date: 2020-04-14
author: 吴昊
header-img:
catalog: true
tags:
	- LeetCode

---



# 98 Validate Binary Search Tree

## Description

 

Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

- The left subtree of a node contains only nodes with keys **less than** the node's key.
- The right subtree of a node contains only nodes with keys **greater than** the node's key.
- Both the left and right subtrees must also be binary search trees.

 

**Example 1:**

```
    2
   / \
  1   3

Input: [2,1,3]
Output: true
```

**Example 2:**

```
    5
   / \
  1   4
     / \
    3   6

Input: [5,1,4,null,null,3,6]
Output: false
Explanation: The root node's value is 5 but its right child's value is 4.
```



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
  bool isValidBST(TreeNode* root){
    if (root == NULL){
      return true;
    }
    vector<int> temp;
    helper(root, temp);
    for (int i = 0; i < temp.size()-1; i++){
      if (temp[i] < temp[i+1]){
        continue;
      }else{
        return false;
      }
    }
    return true;
  }
  
  void helper(TreeNode* root, vector<int> &temp){
    if (!root){
      return;
    }
    stack<TreeNode*> s;
    TreeNode* p = root;
   	while(!s.empty() || p){
      while(p){
        s.push(p);
      	p = p->left;
      }
      
    }
    if (!s.empty()){
      p = s.top();
      temp.push_back(p->val);
      s.pop();
      p = p->right;
    }
  }  
}
```

---

## Summary

BST的中序遍历是有序的，因此，对一棵二叉树进行中序遍历，并存入vector中，只要判断vector内的元素是有序的，则此BST就是合法的，否则就不是BST。



