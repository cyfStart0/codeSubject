题目描述
---
* 把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。 输入一个非减排序的数组的一个旋转，输出旋转数组的最小元素。 例如数组{3,4,5,1,2}为{1,2,3,4,5}的一个旋转，该数组的最小值为1。 NOTE：给出的所有元素都大于0，若数组大小为0，请返回0。
* 思路：
	* 这是一道二分查找的变形的题目。

	（1）我们用两个指针left,right分别指向数组的第一个元素和最后一个元素。按照题目的旋转的规则，第一个元素应该是大于最后一个元素的（没有重复的元素）。

	（2）找到数组的中间元素。中间元素大于第一个元素，则中间元素位于前面的递增子数组，此时最小元素位于中间元素的后面。我们可以让第一个指针left指向中间元素。移动之后，第一个指针仍然位于前面的递增数组中。中间元素小于第一个元素，则中间元素位于后面的递增子数组，此时最小元素位于中间元素的前面。我们可以让第二个指针right指向中间元素。移动之后，第二个指针仍然位于后面的递增数组中。这样可以缩小寻找的范围。

	（3）按照以上思路，第一个指针left总是指向前面递增数组的元素，第二个指针right总是指向后面递增的数组元素。最终第一个指针将指向前面数组的最后一个元素，第二个指针指向后面数组中的第一个元素。

	也就是说他们将指向两个相邻的元素，而第二个指针指向的刚好是最小的元素，这就是循环的结束条件。到目前为止以上思路很耗的解决了没有重复数字的情况，这一道题目添加上了这一要求，有了重复数字。

	因此这一道题目比上一道题目多了些特殊情况：

	我们看一组例子：｛1，0，1，1，1｝ 和 ｛1，1， 1，0，1｝ 都可以看成是递增排序数组｛0，1，1，1，1｝的旋转。		       
	这种情况下我们无法继续用上一道题目的解法，去解决这道题目。因为在这两个数组中，第一个数字，最后一个数字，中间数字都是1。
	第一种情况下，中间数字位于后面的子数组，第二种情况，中间数字位于前面的子数组。
	因此当两个指针指向的数字和中间数字相同的时候，我们无法确定中间数字1是属于前面的子数组,还是属于后面的子数组（）。也就无法移动指针来缩小查找的范围。

```java
import java.util.ArrayList;
public class Solution {
    public int minNumberInRotateArray(int [] array) {
        if(array.length==0){
		   return 0;
	    }
	   int left = 0;
	   int right=array.length-1;
	   int mid = 0;
	   while(array[left]>=array[right]){
		   if(right-left==1){
			   mid = right;
			   break;
		   }

		   mid = left+(right-left)/2;
		   if(array[left]==array[mid]&&array[left]==array[mid]){
			   return midNumber(array,left,right);
		   }

		   if(array[mid]>=array[left]){
			   left = mid;
		   }else{
			   right = mid;
		   }
	   }

	   return array[mid];
    }
    //顺序查找最小值
	public int midNumber(int []array,int left,int right){
		int result = array[left];
		for(int i=left+1;i<array.length;i++){
			if(array[i]<result){
				result = array[i];
			}
		}
		return result;
	}

}

