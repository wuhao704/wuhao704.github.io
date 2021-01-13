---
layout:	post
title: 'LeetCode: 94.Binary Tree Inorder Traversal'
subtitle:
date: 2020-04-14
author: 吴昊
header-img:
catalog: true
tags: LeetCode


---



# 94 Binary Tree Inorder Traversal

## Description

Given a binary tree, return the *inorder* traversal of its nodes' values.

**Example:**

```
Input: [1,null,2,3]
   1
    \
     2
    /
   3

Output: [1,3,2]
```

**Follow up:** Recursive solution is trivial, could you do it iteratively?



---

## Solution

- recursive

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
    	vector<int> inorderTraversal(TreeNode* root){
        vector<int> ans;
        inorder(root, ans);
        return ans;
      }
    
    	void inorder(TreeNode* root, vector<int> &ans){
        if (root){
          inorder(root->left, ans);
          ans.push_back(root->val);
          inorder(root->right, ans);
        }
      }
  }
  
  
  ```

  

- iterative

  ```c++
  class Solution {
    public:
    	vector<int> inorderTraversal(TreeNode* root){
        vector<int> ans;
        inorder(root, ans);
        return ans;
      }
    
    	void inorder(TreeNode* root, vector<int> &ans){
        if(!root){
          return;
        }
        stack<TreeNode*> s;
        TreeNode* p = root;
        while(!s.empty() || p){
          while(p){
            s.push(p);
            p = p->left;
          }
          if (!s.empty()){
            p = s.top();
            ans.push_back(p->val);
            s.pop();
            p = p->right;
          }
        }
      }
  }
  ```

  

