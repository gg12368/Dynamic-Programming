题目描述
一个机器人在m×n大小的地图的左上角（起点，下图中的标记“start"的位置）。
机器人每次向下或向右移动。机器人要到达地图的右下角。（终点，下图中的标记“Finish"的位置）。
可以有多少种不同的路径从起点走到终点？


上图是3×7大小的地图，有多少不同的路径？
备注：m和n小于等于100



示例1
输入
2,1
输出
1

示例2
输入
2,2
输出
2

import java.util.*;

public class Solution {
    public int uniquePaths(int m, int n) {
        if(m == 1 || n == 1)
            return 1;
        //dp[i][j]表示机器人从点（0,0）出发到点（i,j）的不同路径数目
        int dp[][]= new int[m][n];
        dp[0][0] = 0;
        /*考虑边缘情况*/
        //n = 1的情况，只有一条直线路径
        for(int i = 1; i < m; i++){
            dp[i][0] = 1;
        }
        //m = 1的情况，只有一条直线路径
        for(int j = 1; j < n; j++){
            dp[0][j] = 1;
        }
        //动态规划
        for(int i = 1; i < m; i++){
            for(int j = 1; j < n; j++){
                //到达点（i,j）有两种路径：
                //（1）机器人从点（i-1,j）往下移动 （2）机器人从点（i,j-1）往右移动 
                dp[i][j] = dp[i-1][j] + dp[i][j-1];
            }
        }
        return dp[m-1][n-1];
    }
}
