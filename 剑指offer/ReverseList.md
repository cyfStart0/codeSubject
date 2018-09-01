题目描述:
---
* 输入一个链表，反转链表后，输出新链表的表头。
* 思路：
	* //做循环，如果当前节点不为空的话，始终执行此循环，此循环的目的就是让当前节点从指向next到指向pre
            //如此就可以做到反转链表的效果
            //先用next保存head的下一个节点的信息，保证单链表不会因为失去head节点的原next节点而就此断裂
 //保存完next，就可以让head从指向next变成指向pre了，
 //head指向pre后，就继续依次反转下一个节点
            //让pre，head，next依次向后移动一个节点，继续下一次的指针反转
```java
/*
public class ListNode {
    int val;
    ListNode next = null;

    ListNode(int val) {
        this.val = val;
    }
}*/
public class Solution {
    public ListNode ReverseList(ListNode head) {
        ListNode pre = null;
		ListNode next = null;
		if(head==null)
			return null;
		while(head!=null){
			next = head.next;	//在链断开之前，保存下一节点的位置
			head.next = pre;
			pre = head;
			head = next;
		}
		return pre;
    }
}
