392、判断子序列
````Java
class Solution {
    public boolean isSubsequence(String s, String t) {
        char [] array = s.toCharArray();
        int j = -1;
        for(int i = 0; i < array.length; i++){
            j = t.indexOf(array[i], j+1);
            if(j == -1){
                return false;
            }
        }
        return true;
    }
}
````
1139、最大的以 1 为边界的正方形 
````Java
class Solution {
    public int largest1BorderedSquare(int[][] grid) {
        if(grid.length == 0 || grid == null){
            return 0;
        }
        int row = grid.length;
        int col = grid[0].length;
        int [][][] temp = new int[row+1][col+1][2];
        for(int i=row-1;i>=0;i--){
            for(int j=col-1; j>=0;j--){
                if(grid[i][j] == 1){
                    temp[i][j][0] = 1 + temp[i][j+1][0];
                    temp[i][j][1] = 1 + temp[i+1][j][1];
                }
            }
        }
        int layer = row;
        while(layer > 0){
           for(int i=0;i<=row-layer;i++){
               for(int j=0;j<=col-layer;j++){
                   if(temp[i][j][0]>=layer && temp[i][j][1]>=layer && temp[i+layer-1][j][0]>=layer && temp[i][j+layer-1][1]>=layer){
                       return (int)Math.pow(layer,2);
                   }
               }
           }
           layer--; 
        }
        return 0;
    }
}
````
