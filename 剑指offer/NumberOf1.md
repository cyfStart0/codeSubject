题目描述:
---
* 输入一个整数，输出该数二进制表示中1的个数。其中负数用补码表示。
* 思路：
	* 思想：用1（1自身左移运算，其实后来就不是1了）和n的每位进行位与，来判断	1的个数
```java
public class Solution {
    public int NumberOf1(int n) {
        int count = 0;
		while(n!=0){
			count++;
			n = n&(n-1);
		}
		return count;
    }
}

