303. 区域和检索 - 数组不可变
给定一个整数数组  nums，求出数组从索引 i 到 j  (i ≤ j) 范围内元素的总和，包含 i,  j 两点。

示例：

给定 nums = [-2, 0, 3, -5, 2, -1]，求和函数为 sumRange()

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3

class NumArray {

    int[] dp;

    public NumArray(int[] nums) {
        if (nums == null || nums.length == 0) {
            dp = new int[0];
            return;
        }
        // 定义状态： dp[i] 是从nums[0]到nums[i]的总和，包括 nums[0] 和 nums[j] 两点。
        int n = nums.length;
        dp = new int[n];


        // 定义初始值：
        dp[0] = nums[0];

        // 定义状态转移方程： dp[i] = dp[i-1] + nums[i]
        for (int i = 1; i < n; i++) {
            dp[i] = dp[i-1] + nums[i];
        }
    }
    
    public int sumRange(int i, int j) {
        if (i == 0) {
            return dp[j];
        }

        return dp[j] - dp[i-1];
    }
}
