# LaTeX 数学公式语法

# **📌 LaTeX 数学公式速查表（用于 Markdown）**

---

这是行内公式：`$x^2 + y^2 = z^2$`

## **✅ 基础写法（你最常用）**

| 效果                           | **LaTeX 写法**                 | **说明**        |
| ---------------------------- | ---------------------------- | ------------- |
| $x^2$                        | `x^2`                        | 幂（次方）         |
| $x_2$                        | `x_2`                        | 下标            |
| $\log n$                     | `\log n`                     | 对数（默认底为 10）   |
| $\log_2 n$                   | `\log_2 n`                   | 指定底数的对数（底为 2） |
| $\sqrt{n}$                   | `\sqrt{n}`                   | 平方根           |
| $\frac{a}{b}$                | `\frac{a}{b}`                | 分数            |
| $a + b = c$                  | `a + b = c`                  | 等式            |
| $\left( \frac{a}{b} \right)$ | `\left( \frac{a}{b} \right)` | 括号自动缩放        |

---

## **📘 进阶用法**

### **🧠 1. 数学环境**

```latex
这是块级公式：
$$
x^2 + y^2 = z^2
$$
```

---

### **🧠 2. 常用数学符号**

| **效果** | **写法** | **说明** |
| --- | --- | --- |
| $\infty$ | `\infty` | 无穷 |
| $\ge / \le$ | `\ge / \le` | 大于等于/小于等于 |
| $\neq$ | `\neq` | 不等于 |
| $\cdot$ | `\cdot` | 乘号（点乘） |
| $\sum_{i=1}^n i$ | `\sum_{i=1}^n i` | 累加符号 |
| $\prod_{i=1}^n i$ | `\prod_{i=1}^n i` | 连乘符号 |
| $\forall$ | `\forall` | 对所有 |
| $\exists$ | `\exists` | 存在 |

---

### **🧠 3. 常用函数**

| **效果** | **写法** |
| --- | --- |
| $\sin x$ | `\sin x` |
| $\cos x$ | `\cos x` |
| $\tan x$ | `\tan x` |
| $\ln x$ | `\ln x` |
| $\log_{10} x$ | `\log_{10} x` |

---

### **🧠 4. 多行公式对齐（适合推导）**

```latex
$$
\begin{aligned}
a^2 + b^2 &= c^2 \\
x &= \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\end{aligned}
$$
```

效果显示如下

$$
\begin{aligned}
a^2 + b^2 &= c^2 \\
x &= \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\end{aligned}
$$


---

## **📝 推荐 Markdown 写法模板**

```latex
# 数学基础 - 对数 log 相关

## 行内公式示例

在算法中，二分查找的时间复杂度是 $O(\log_2 n)$，因为每次查找将问题规模减半。

## 块级公式示例

$$
\log_a(xy) = \log_a x + \log_a y
$$

$$
\log_a\left(\frac{x}{y}\right) = \log_a x - \log_a y
$$

## 推导例子

$$
\begin{aligned}
\text{假设} \quad n &= 2^k \\
\Rightarrow \log_2 n &= \log_2(2^k) = k
\end{aligned}
$$
```

效果：

> # 数学基础 - 对数 log 相关
> ## 行内公式示例
> 在算法中，二分查找的时间复杂度是 $O(\log_2 n)$，因为每次查找将问题规模减半。
> ## 块级公式示例
> 
> $$
> \log_a(xy) = \log_a x + \log_a y
> $$
> 
> $$
> \log_a\left(\frac{x}{y}\right) = \log_a x - \log_a y
> $$
> 
> ## 推导例子
> 
> $$
> \begin{aligned}
> \text{假设} \quad n &= 2^k \\
> \Rightarrow \log_2 n &= \log_2(2^k) = k
> \end{aligned}
> $$

---

## **🛠 工具建议**

| **工具**             | **是否支持数学** | **推荐理由**           |
| ------------------ | ---------- | ------------------ |
| Typora             | ✅          | 离线编辑 + 实时渲染        |
| Obsidian           | ✅          | Markdown 管理 + 插件支持 |
| Jupyter Notebook   | ✅          | 适合刷题笔记，代码和数学一起写    |
| HackMD / StackEdit | ✅          | 在线 Markdown 写作     |