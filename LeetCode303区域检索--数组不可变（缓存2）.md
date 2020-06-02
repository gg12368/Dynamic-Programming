303. 区域和检索 - 数组不可变
给定一个整数数组  nums，求出数组从索引 i 到 j  (i ≤ j) 范围内元素的总和，包含 i,  j 两点。

示例：

给定 nums = [-2, 0, 3, -5, 2, -1]，求和函数为 sumRange()

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3

缓存:
可以计算 sumrange 如下：
sumrange（i，j）=sum[j+1]−sum[i]


private int[] sum;

public NumArray(int[] nums) {
    sum = new int[nums.length + 1];
    for (int i = 0; i < nums.length; i++) {
        sum[i + 1] = sum[i] + nums[i];
    }
}

public int sumRange(int i, int j) {
    return sum[j + 1] - sum[i];
}
注意，在上面的代码中，我们插入了一个虚拟 0 作为 sum 数组中的第一个元素。这个技巧可以避免在 sumrange 函数中进行额外的条件检查。

复杂度分析:
时间复杂度：每次查询的时间 O(1)，O(N) 预计算时间。由于累积和被缓存，每个sumrange查询都可以用 O(1) 时间计算。
空间复杂度：O(n).

