题目描述：
---
* 用两个栈来实现一个队列，完成队列的Push和Pop操作。 队列中的元素为int类型。
* 思路：
	* 使用两个栈，一个栈stack1模拟进队，在出队时stack1出栈，另一个栈stack2进栈，然后stack2再出栈即为出队
```java
import java.util.Stack;

public class Solution {
    Stack<Integer> stack1 = new Stack<Integer>();
    Stack<Integer> stack2 = new Stack<Integer>();

    public void push(int node){
		stack1.push(node);
	}
	public int pop(){
		if(stack1.empty()&&stack2.empty()){
			throw new RuntimeException("Empty");
		}
		if(stack2.empty()){

			while(!stack1.empty()){
				stack2.push(stack1.pop());
			}
		}
		return stack2.pop();
	}
}
