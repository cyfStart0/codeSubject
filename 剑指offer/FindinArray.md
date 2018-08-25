题目描述
在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，
每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个
整数，判断数组中是否含有该整数。
思路：
	把每一行看成有序递增的数组，
	利用二分查找，
	通过遍历每一行得到答案，
	时间复杂度是nlogn
public class Solution {
    public static boolean Find(int target, int [][] array) {
        if(array.length!=0 || array!=null){
	        for(int i = 0;i<array.length;i++){
	                int start = 0;
	                int end = array[i].length-1;
	                int mid ;
	                while(start<=end){
	                	mid = (start+end)/2;
	                    if(target==array[i][mid]){
	                        return true;
	                    }else if(target<array[i][mid]){
	                        end = mid-1;
	                    }else{
	                        start = mid+1;
	                    }
	                }
	        }
	        
		}  
		return false;
    }
}