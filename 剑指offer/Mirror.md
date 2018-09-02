题目描述:
---
* 操作给定的二叉树，将其变换为源二叉树的镜像。
* 思路：
	* 先前序遍历这棵树的每个结点，如果遍历到的结点有子结点，就交换它的两个子	 节点，
	 当交换完所有的非叶子结点的左右子结点之后，就得到了树的镜像
```java
/**
public class TreeNode {
    int val = 0;
    TreeNode left = null;
    TreeNode right = null;

    public TreeNode(int val) {
        this.val = val;

    }

}
*/
public class Solution {
    public void Mirror(TreeNode root) {
        TreeNode temp = null;
		if(root != null){
			temp = root.left;
			root.left = root.right;
			root.right = temp;
			Mirror(root.left);
			Mirror(root.right);
		}
    }
}
