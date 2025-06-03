# Python 中 lambda 的简明用法总结

## 🧠 什么是 lambda？
- `lambda` 是用来创建**匿名函数**的关键字
- 语法：`lambda 参数: 表达式`
- 功能等价于一行的 `def` 函数定义：
```python
xfunc = lambda x: x + 1
# 等价于
def xfunc(x):
	x += 1
	return x

print(xfunc(3)) # 输出 4
```

当 `lambda` 作为一个key的时候，例如以下例子：
```python
data = [[1,3], [2,4], [5,2]]
data.sort(key=lambda x: x[1])  # 按每个子数组的第2个元素排序
```
此时`data.sort`会把data里每一个item输入，即`[1,3], [2,4], [5,2]`逐个输入

然后根据`lambda x: x[1]`的定义，会将每个item的第二项<mark>返回</mark>给key，即 3, 4, 2

所以`data.sort`就会根据data里每个项的<mark>第二项</mark>的大小排列 3, 4, 2 => 2, 3, 4

结果就是`[5,2], [1,3], [2,4]`

---

## ✅ 常见用法场景

### 1. 作为排序的 key 函数
```python
data = [[1,3], [2,4], [5,2]]
data.sort(key=lambda x: x[1])  # 按每个子数组的第2个元素排序
```

### **2. 搭配 `map()`：映射每个元素**

```python
nums = [1, 2, 3]
squares = list(map(lambda x: x**2, nums))  # [1, 4, 9]
```

### **3. 搭配 `filter()`：筛选元素**

```python
nums = [1, 2, 3, 4]
evens = list(filter(lambda x: x % 2 == 0, nums))  # [2, 4]
```

### **4. 搭配 `reduce()` ：累积计算**

```python
from functools import reduce
nums = [1, 2, 3, 4]
product = reduce(lambda x, y: x * y, nums)  # 24
```

### **5. 单独赋值为变量（简易函数）**

```python
add = lambda x, y: x + y
add(3, 4)  # 7
```

---

> [!CAUTION]
> 只能写**一个表达式**（不能包含多行或赋值）。适合写短逻辑、临时用函数的场景。
