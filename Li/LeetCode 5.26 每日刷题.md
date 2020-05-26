1、机器人的运动范围
````Java
public class Solution {
    int count = 0;
    public int movingCount(int threshold, int rows, int cols)
    {
        if(threshold == 0 || rows == 0 || cols == 0)
            return 0;
        boolean[] flag = new boolean[rows*cols];
        movCount(threshold,0,0,rows,cols,flag);
        return count;
    }
    public void movCount(int threshold,int i,int j, int rows, int cols,boolean[] flag){
        int index = i * cols + j;
        if(i < 0 || j < 0 || i >= rows || j >= cols || flag[index] == true)
            return;
        if(helper(i,j) <= threshold){
            count++;
            flag[index] = true;
        }
        else{
            flag[index] = false;
            return;
        }
        movCount(threshold,i-1,j,rows,cols,flag);
        movCount(threshold,i+1,j,rows,cols,flag);
        movCount(threshold,i,j-1,rows,cols,flag);
        movCount(threshold,i,j+1,rows,cols,flag);
    }
    public int helper(int i,int j){
        int sum = 0;
        do{
            sum+=i%10;
        }while((i = i/10)>0);
         
        do{
            sum+=j%10;
        }while((j = j/10)>0);
        return sum;
    }
}
````
2、统计重复个数
````Java
class Solution {
    public int getMaxRepetitions(String s1, int n1, String s2, int n2) {
        int len1 = s1.length();
        int len2 = s2.length();
        if (len1 == 0 || len2 == 0 || n1 == 0 || n2 == 0) {
            return 0;
        }
        char[] chars1 = s1.toCharArray();
        char[] chars2 = s2.toCharArray();
        int index = 0;
        int count = 0;
        int[] countRecorder = new int[n1];
        int[] indexRecorder = new int[n1];

        for (int i = 0; i < n1; ++i) {
            for (int j = 0; j < len1; ++j) {
                if (chars1[j] == chars2[index]) {
                    ++index;
                }
                if (index == chars2.length) {
                    index = 0;
                    ++count;
                }
            }
            countRecorder[i] = count;
            indexRecorder[i] = index;
            for (int j = 0; j < i; ++j) {
                if (indexRecorder[j] != index) continue;
                int preCount = countRecorder[j];
                int patternCount = ((n1 - 1 - j) / (i - j)) * (countRecorder[i] - countRecorder[j]);
                int remainCount = countRecorder[j + (n1 - 1 - j) % (i - j)] - countRecorder[j];
                return (preCount + patternCount + remainCount) / n2;
            }
        }
        // 没有循环节的出现，相当于直接使用暴力法
        return countRecorder[n1 - 1] / n2;
    }
}
````
