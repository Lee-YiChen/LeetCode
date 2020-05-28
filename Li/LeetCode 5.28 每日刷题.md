1、包含min函数的栈
````Java
import java.util.Stack;
import java.util.ArrayList;
 
public class Solution {
    ArrayList<Integer> dataList = new ArrayList<Integer>();
    ArrayList<Integer> minList = new ArrayList<Integer>();
    Integer min = Integer.MAX_VALUE;
     
    public void push(int node) {
       dataList.add(node);
        if(node < min){
            minList.add(node);
            min = node;
        }
        else{
            minList.add(min);
        }
    }
    public int getLength(){
        return dataList.size();
    }
    public void pop() {
        int end = getLength() - 1;
        dataList.remove(end);
        minList.remove(end);
        min = minList.get(getLength() - 1);
    }
     
    public int top() {
        return dataList.get(getLength() - 1);
    }
     
    public int min() {
        return min;
    }
}
````
2、从上往下打印二叉树
````Java
import java.util.ArrayList;
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
    public ArrayList<Integer> PrintFromTopToBottom(TreeNode root) {
        ArrayList<Integer> array = new ArrayList<Integer>();
        ArrayList<TreeNode> queue = new ArrayList<TreeNode>();
        if(root == null){
            return array;
        }
        queue.add(root);
        while(queue.size()!=0){
            TreeNode temp = queue.remove(0);
            if(temp.left != null){
                queue.add(temp.left);
            }
            if(temp.right != null){
                queue.add(temp.right);
            }
            array.add(temp.val);
        }
        return array;
    }
}
````
