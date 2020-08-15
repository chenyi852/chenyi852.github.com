---
layout: post
title: "leetcode-offer7"
subtitle: '重建二叉树'
author: "Johnny"
header-style: text
tags:

  - leetcode
  - 重建二叉树
---

解题思路：
递归法， 先序遍历中，根->左->右；中序遍历, 左->根->右
- 1 中序遍历中，根的左边是左子树，根的右边是右子树， 左子树中也是这样的顺序，显示根节点，然后是左子树，然后是右子树
- 2 先序遍历中，先是根节点，然后是左子树的所有节点，左子树的先序也是是一样，先是根，然后是左子树，然后是右子树，完全可以用递归
- 3 那么根节点是先序遍历数组的0节点，然后遍历中序遍历的数组，找到根节点所在位置i
- 4 那么左子节点可以递归得到，preorder的起始地址是当前数组的preorer[1], inorder的起始地址inorder[0],preorder和inorder的长度都是i
- 5 那么右子节点也可以递归得到，preorder的起始地址为preorder[i + 1], inorder的地址地址是inorder[i + 1],2个数组的长度均为size - i - 1(i是左节点长度，1 是根节点长度) 



```
struct TreeNode* buildTree(int* preorder, int preorderSize, int* inorder, int inorderSize){
    struct TreeNode *root = (struct TreeNode *)malloc(sizeof(struct TreeNode));
    int right_size = 0;
    int i = 0;

    if (preorderSize == 0) {
        return NULL;
    }

    for (i = 0; i < inorderSize; i++) {
        if (preorder[0] == inorder[i]) {
            break;
        }
    }

    root->val = preorder[0];
    root->left = buildTree(&preorder[1], i, &inorder[0], i);
    right_size =  inorderSize - i - 1;
    root->right = buildTree(&preorder[i + 1], right_size, &inorder[i + 1], right_size);

    return root;
}
```
