题目描述：
* 输入两个单调递增的链表，输出两个链表合成后的链表，当然我们需要合成后的链表满足单调不减规则。
* 思路：
	* 比较两个链表的首结点，哪个小的的结点则合并到第三个链表尾结点，并向前移动一个结点。
    步骤一结果会有一个链表先遍历结束，或者没有
    第三个链表尾结点指向剩余未遍历结束的链表
    返回第三个链表首结点
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
    public ListNode Merge(ListNode list1,ListNode list2) {
        ListNode p = list1;
		ListNode q = list2;
		ListNode head = null;
		ListNode c = null;
		if(p == null) return q;
		if(q == null) return p;

		//取较小值为头结点
		if(p.val<q.val){
			head = p;
			p = p.next;
		}else{
			head = q;
			q = q.next;
		}
		//开始合并
		c= head;
		while(p!=null && q!=null){
			if(p.val <= q.val){
				c.next = p;
				p = p.next;
				c = c.next;
			}else{
				c.next = q;
				q = q.next;
				c = c.next;
			}
		}
		if(p!=null){
			c.next = p;
		}
		if(q!=null){
			c.next = q;
		}

        return head;
    }

}
