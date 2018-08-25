题目描述
---
* 请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为We%20Are%20Happy
* 思路：
	* 这道题我直接运用java代码里的String类里的方法搞定了，哈哈哈。。。
```java
public class Solution {
    public String replaceSpace(StringBuffer str) {
    	String str1 = str.toString();
		str1 = str1.replace(" ", "%20");
    	return str1;
    }
}
