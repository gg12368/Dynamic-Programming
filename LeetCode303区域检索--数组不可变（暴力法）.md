303. 区域和检索 - 数组不可变
给定一个整数数组  nums，求出数组从索引 i 到 j  (i ≤ j) 范围内元素的总和，包含 i,  j 两点。

示例：

给定 nums = [-2, 0, 3, -5, 2, -1]，求和函数为 sumRange()

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3

暴力法[超过时间限制]:
每次调用 sumrange 时，我们都使用for循环将索引 ii 到 jj 之间的每个元素相加。

private int[] data;

public NumArray(int[] nums) {
    data = nums;
}

public int sumRange(int i, int j) {
    int sum = 0;
    for (int k = i; k <= j; k++) {
        sum += data[k];
    }
    return sum;
}

复杂度分析:
时间复杂度：每次查询的时间 O(n)，每个 sumrange 查询需要 O(n) 时间。
空间复杂度：O(1)，请注意，data 是对 nums 的引用，不是它的副本。

