题目描述
---
* 输入一个链表，按链表值从尾到头的顺序返回一个ArrayList。
* 思路：
	* 利用链表的头插法即可。这样建立的链表内元素顺序正好与原来相反
```java
/**
*    public class ListNode {
*        int val;
*        ListNode next = null;
*
*        ListNode(int val) {
*            this.val = val;
*        }
*    }
*
*/
import java.util.ArrayList;
public class Solution {
    public ArrayList<Integer> printListFromTailToHead(ListNode listNode) {
       ArrayList<Integer> list = new ArrayList<Integer>();
		ListNode first = null;
		ListNode next = null;
		while(listNode!=null){
			next = listNode.next;
			listNode.next = first;
			first =listNode;
			listNode = next;
		}
		while(first!=null){
			list.add(first.val);
			first = first.next;
		}
		return list;
    }
}

