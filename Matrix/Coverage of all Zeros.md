## Coverage of all Zeros in a Binary Matrix [https://www.geeksforgeeks.org/problems/coverage-of-all-zeros-in-a-binary-matrix4024/1]

```
class Solution {
    public int findCoverage(int[][] matrix) {
        // code here
        int n = matrix.length;
        int m = matrix[0].length;
        int coverage = 0;
        for(int i = 0; i < matrix.length; i++){
            for(int j = 0; j < matrix[i].length; j++){
                if(matrix[i][j] == 0){
                    if(j+1<m && matrix[i][j+1] == 1) coverage++;
                    if(j-1>=0 && matrix[i][j-1] == 1) coverage++;
                    if(i+1<n && matrix[i+1][j] == 1)coverage++;
                    if(i-1>=0 && matrix[i-1][j] == 1)coverage++;
                }
            }
        }
        return coverage;
    }
}
```
