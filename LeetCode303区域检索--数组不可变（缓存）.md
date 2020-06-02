303. 区域和检索 - 数组不可变
给定一个整数数组  nums，求出数组从索引 i 到 j  (i ≤ j) 范围内元素的总和，包含 i,  j 两点。

示例：

给定 nums = [-2, 0, 3, -5, 2, -1]，求和函数为 sumRange()

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
缓存:
假设 sumrange 被调用 1000次，其参数完全相同。我们怎么能加快速度？
我们可以用额外的空间换取速度。通过预先计算所有的范围和可能性并将其结果存储在哈希表中，我们可以将查询加速到常量时间。

private Map<Pair<Integer, Integer>, Integer> map = new HashMap<>();

public NumArray(int[] nums) {
    for (int i = 0; i < nums.length; i++) {
        int sum = 0;
        for (int j = i; j < nums.length; j++) {
            sum += nums[j];
            map.put(Pair.create(i, j), sum);
        }
    }
}

public int sumRange(int i, int j) {
    return map.get(Pair.create(i, j));
}

复杂度分析:
时间复杂度：每次查询的时间 O(1)，O(n^2) 时间用来预计算。在构造函数中完成的预计算需要 O(n^2)时间。每个 sumrange 查询的时间复杂性是 O(1) 因为哈希表的查找操作是常量时间。
空间复杂度：O(n^2)，所需的额外空间为 O(n^2) 因为 i 和 j 都有 n 个候选空间。

