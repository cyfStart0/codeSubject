题目描述:
---
* 输入一个链表，输出该链表中倒数第k个结点。
* 思路：
	* 两个指针，先让第一个指针和第二个指针都指向头结点，然后再让第一个指正走(k-1)步，到达第k个节点。然后两个指针同时往后移动，当第一个结点到达末尾的时候，第二个结点所在位置就是倒数第k个节点了。

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
    public ListNode FindKthToTail(ListNode head,int k) {
        if(head==null || k<=0){
			return null;
		}
		ListNode p,q;
		p = head;
		for(int i = 1;i < k;i++){
			if(p.next!=null)
				p = p.next;
			else
				return null;
		}

		q = head;
		while(p.next!=null){
			p = p.next;
			q = q.next;
		}
		return q;
    }
}

