# 摩尔投票法（Boyer-Moore Majority Vote Algorithm）笔记

## **一、算法定义**

**摩尔投票法**是一种在 `O(n)` 时间、`O(1)` 空间复杂度下，
找出数组中“众数（majority element）”或主元素的方法。

- **众数**：出现次数大于数组长度一半（n/2）的元素。
- 扩展可用于出现次数大于 n/3、n/k 的所有元素。

---

## **二、核心思想**

- 把众数/主元素看作“超级候选人”。
- 每次遇到相同数字就加一票，不同数字就互相抵消。
- 最终留下的，就是出现次数最多的主元素（需后续验证）。

---

## **三、标准用法（出现次数大于 n/2）**

### **1. 算法流程**

1. 初始化：`count = 0`，`candidate = None`
2. 遍历数组
    - `如果count == 0`，把当前元素设为`candidate`
    - 如果元素等于`candidate`，`count += 1`
    - 否则`count -= 1`
3. 返回c`andidate`

### **2. 代码模板**

```python
def majorityElement(nums):
    count = 0
    candidate = None
    for num in nums:
        if count == 0:
            candidate = num
        count += (1 if num == candidate else -1)
    return candidate
```

---

## **四、原理说明**

- 众数出现 > n/2 次，其它数加起来都比不上它。
- 不管抵消多少次，最终剩下的 `candidate` 一定是众数。
- 数学保证了候选人不会被彻底抵消出局。

---

## **五、扩展用法：出现次数大于 n/3、n/k**

### **1. 思路**

- **最多有 `k-1` 个主元素**
- 需要 `k-1` 个“计票人”（候选人+计数）

### **2. 代码模板（n/3为例）**

```python
def majorityElement(nums):
    candidate1 = candidate2 = None
    count1 = count2 = 0
    for num in nums:
        if num == candidate1:
            count1 += 1
        elif num == candidate2:
            count2 += 1
        elif count1 == 0:
            candidate1, count1 = num, 1
        elif count2 == 0:
            candidate2, count2 = num, 1
        else:
            count1 -= 1
            count2 -= 1
    # 验证候选人
    return [c for c in (candidate1, candidate2) if nums.count(c) > len(nums)//3]
```

- 如果是 `n/k`，就需要维护 `k-1` 个候选人和计数器。

---

## **六、适用场景和限制**

### **适用场景**

- 已知数组存在主元素（出现次数大于 `n/2`、`n/3`、`n/k`）
- 流式数据处理、空间受限时

### **不适用场景**

- 没有主元素存在的保证时，投票法算出来的 `candidate` 可能不是正确答案
- 只想找出现次数最多的元素但没超过比例时，需后续验证

---

## **七、易错点 & 面试应答**

1. **二次验证**
    - 扩展版摩尔投票法筛出的 `candidate` 需二次遍历统计出现次数，最终确认
2. **候选人槽位更换**
    - 只要主元素数量足够，哪怕被抵消出局，后面还能重新“上岗”
3. **最多 `k-1` 个主元素**
    - 超过这个数量的主元素会与自己抵消，无法全部“上岗”

---

## **八、经典例题**

- [https://leetcode.com/problems/majority-element/?envType=study-plan-v2&envId=top-interview-150](https://leetcode.com/problems/majority-element/?envType=study-plan-v2&envId=top-interview-150)

---

## **九、手动模拟示例**

假设 `nums = [1, 2, 3, 1, 2, 1, 1]`

- $n=7, n/3≈2.33$
- 出现次数 > 2 的有1（4次）

**计票过程见上方详细模拟表格。**

---

## **十、面试答题建议**

1. 先写哈希表/`Counter`做法保证通过，随后主动说可以用摩尔投票法优化到 `O(1)` 空间。
2. 主动讲解算法思想及适用场景，并说明限制。
3. 扩展题型能举一反三，面试高分。

---

### **一句话记忆法**

> 摩尔投票法用抵消思想，`O(1)` 空间找主元素，`n/k`就用`k-1`个候选人。
> 

---

需要更多模拟例子、动画讲解或者LeetCode题单？随时告诉我！