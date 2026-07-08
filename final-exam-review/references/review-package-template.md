# Review Package Template

Use this template for the final deliverables. Create separate Markdown files when the task is large; otherwise use these sections in one Markdown file.

Final deliverables must be normal Markdown, not wrapped in outer code fences. This lets math blocks, tables, and `<details>` answer sections render correctly.

## 复习提纲.md

# 课程名 期末复习提纲

## 资料覆盖情况

| 资料 | 类型 | 处理方式 | 覆盖章节 | 可靠性备注 |
| --- | --- | --- | --- | --- |

## 考点总览

| 优先级 | 考点 | 来源依据 | 常见题型 | 复习建议 |
| --- | --- | --- | --- | --- |

## 第 N 章：章节标题

### 模块 N.1：知识模块标题

**<mark>核心结论或定义</mark>**

- 来源：文件名、页码、幻灯片号、题号或章节。

#### 内容总结

用可以直接复习的语言整理本模块的核心内容。不要只写“需要掌握某概念”，而要写清楚该概念是什么、为什么重要、和其他概念的区别、考试中通常如何使用。

#### 公式、方法或论证框架

- 公式/方法：写出完整公式、步骤、定理、模型或分析框架。重要公式使用可渲染的 Markdown 数学格式。

$$
\text{示例：}\quad S_n = \sum_{i=1}^{n} a_i,\qquad
\bar{x} = \frac{1}{n}\sum_{i=1}^{n} x_i
$$

- 上下标/分式/根号/求和/积分：使用 `x_i`、`x^2`、`a_{n+1}`、`\frac{a}{b}`、`\sqrt{x}`、`\sum_{i=1}^{n}`、`\int_a^b f(x)\,dx` 等 LaTeX 写法。
- 多步推导：使用 `aligned` 环境。

$$
\begin{aligned}
f'(x)
&= \lim_{h \to 0}\frac{f(x+h)-f(x)}{h} \\
&= 2x
\end{aligned}
$$

- 符号含义：解释每个变量、单位、输入输出或适用对象。
- 适用条件：说明什么时候可以用，什么时候不能用。
- 推导/逻辑：整理关键推导思路、证明路线、计算步骤或答题结构。

#### 易错点

列出常见误解、条件限制、符号问题、单位问题、概念混淆或答题陷阱。

#### 题型提示

说明可能如何出选择、判断、简答、计算、论述或综合题。

#### 自测题

1. 判断题：题干。
2. 判断题：题干。
3. 经典例题：题干。

<details>
<summary>答案与解析</summary>

1. 对/错。解释。
2. 对/错。解释。
3. 解题思路、关键步骤、最终答案、评分点。

</details>

## 章节题库.md

# 章节题库

## 第 N 章：章节标题

### 判断题

1. 题干。
2. 题干。

### 经典例题

1. 题干。
2. 题干。

<details>
<summary>答案与解析</summary>

- 逐题给出答案、理由、易错提醒和对应复习提纲位置。

</details>

## 模拟题.md

# 期末模拟题

## 模拟题一：基础巩固卷

- 适用目标：检查基本概念和基本方法。
- 建议用时：按课程实际考试时长估计。

### 试题

1. 题干。
2. 题干。

<details>
<summary>答案、解析与评分要点</summary>

- 答案。
- 解析。
- 评分要点。
- 复盘定位：错题对应复习提纲章节。

</details>

## 模拟题二：高频考点卷

## 模拟题三：综合冲刺卷

## 资料处理日志.md

# 资料处理日志

## 输入资料

| 文件或链接 | 类型 | 是否成功读取 | 处理方式 | 问题 |
| --- | --- | --- | --- | --- |

## MarkItDown 转换记录

| 文件 | 输出 Markdown | 抽查结果 | 是否采用 | 回退方式 |
| --- | --- | --- | --- | --- |

## 未覆盖或不可靠内容

- 文件名/章节：说明缺失、乱码、扫描件不可读、公式缺失、表格丢失或其他风险。
