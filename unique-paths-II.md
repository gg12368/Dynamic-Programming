继续思考题目"Unique Paths":如果在图中加入了一些障碍，有多少不同的路径？
分别用0和1代表空区域和障碍
例如
下图表示有一个障碍在3*3的图中央。
[↵  [0,0,0],↵  [0,1,0],↵  [0,0,0]↵]
有2条不同的路径
备注：m和n不超过100.

示例1
输入
[[0,1]]
输出
0

示例2
输入
[[1],[1]]
输出
0


public class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int[][] dp = new int[obstacleGrid.length][obstacleGrid[0].length];
        for (int i = 0; i < dp.length; i ++ ) {
            if(obstacleGrid[i][0] == 1) break;
            dp[i][0] = 1;
        }
        for (int i = 0; i < dp[0].length; i ++ ) {
            if(obstacleGrid[0][i] == 1) break;
            dp[0][i] = 1;
        }
        for (int i = 1; i < dp.length; i ++ ) {
            for (int j = 1; j < dp[0].length; j ++ ) {
                if(obstacleGrid[i][j] == 1) dp[i][j] = 0;
                else dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
            }
        }
        return dp[dp.length - 1][dp[0].length - 1];
    }
}
