# 力扣（LeetCode）

> 选自[力扣](https://leetcode.cn)

## 137. 只出现一次的数字 II

> [【LeetCode#137】只出现一次的数字 II](https://leetcode.cn/problems/single-number-ii/)
>
> 给你一个整数数组 nums ，除某个元素仅出现**一次**外，其余每个元素都恰出现**三次**。请你找出并返回那个只出现了**一次**的元素。你必须设计并实现线性时间复杂度的算法且不使用额外空间来解决此问题。
>
> - 示例 1：
>
> ```
> 输入：nums = [2,2,3,2]
> 输出：3
> ```
>
> - 示例 2：
>
> ```
> 输入：nums = [0,1,0,1,0,1,99]
> 输出：99
> ```
>
> - 提示：
>
>   - $1 \le nums.length \le 3 * 10^4$
>   - $-2^{31}\le nums[i] \le 2^{31} - 1$
>   - $nums$ 中，除某个元素仅出现**一次**外，其余每个元素都恰出现**三次**

### 分析

本题为[只出现一次的数字](https://leetcode.cn/problems/single-number/?envType=study-plan&id=shu-ju-jie-gou-ji-chu&plan=data-structures&plan_progress=b00nos7)的进阶版，除只出现一次的元素外其他元素的出现次数由**两次**提升为**三次。** 

在只出现一次的数字中，我们采用位运算异或的方式很方便地处理每位0、1两个状态的相互转换，所以我们可以得到一种时间复杂度较低的线性方法。在本题中我们也可以用类似的思路去处理，但由于
