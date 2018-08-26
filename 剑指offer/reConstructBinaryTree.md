题目描述
---
* 输入某二叉树的前序遍历和中序遍历的结果，请重建出该二叉树。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。例如输入前序遍历序列{1,2,4,7,3,5,6,8}和中序遍历序列{4,7,2,1,5,3,8,6}，则重建二叉树并返回。
* 思路：
	* 这道题是根据二叉树的先序遍历和中序遍历来确定二叉树，
	先序遍历的第一个元素即为树的根节点，在中序遍历中找出该节点位置，
	此节点之前的为左子树，之后的为右子树，对左、右子树递归则得到最终二叉树。
```java
/**
 * Definition for binary tree
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public TreeNode reConstructBinaryTree(int [] pre,int [] in) {
        TreeNode root = reConstructBinaryTree(pre,in,0,pre.length-1,0,in.length-1);

		return root;
    }

    public static TreeNode reConstructBinaryTree(int pre[],int in[],int L1,int r1,int L2,int r2){
		TreeNode root = new TreeNode(0);
		root.left = null;
		root.right = null;
		int i;
		if(L1>r1)
			return null;

		for(i=L2;i<r2;i++){
			if(in[i] == pre[L1]){
				break;
			}
		}
		root.val = in[i];
		root.left = reConstructBinaryTree(pre,in,L1+1,L1+i-L2,L2,i-1);
		root.right = reConstructBinaryTree(pre,in,L1+i-L2+1,r1,i+1,r2);
		return root;
	}
}

