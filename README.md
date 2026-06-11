# Final Review Skill

`final-exam-review` 是一个面向大学期末复习的 Codex skill。它会指导 Codex 或其他 agent 根据课程科目、PPT、Word、PDF、Markdown、作业题、往年考题等资料，整理一份考试冲刺型复习包。

目标是让学生尽量只依靠生成的复习资料，就能覆盖主要考点并进行有效自测。

## 功能特点

- 将零散课程资料整理为结构化复习提纲。
- 优先使用 MarkItDown 将 PPT、Word、PDF 等资料转换为 Markdown。
- MarkItDown 不可用时，会询问用户是安装后转换，还是直接读取源文件。
- 转换结果乱码、缺页或内容不完整时，会回退读取原始文件。
- 自动提炼高频考点、概念关系、公式、定义、易错点和题型规律。
- 使用 `**<mark>重点内容</mark>**` 高亮核心知识点。
- 每个知识模块后附判断题、经典例题或简答/计算题。
- 生成至少三套模拟题：基础巩固卷、高频考点卷、综合冲刺卷。
- 输出资料处理日志，记录转换情况、失败原因和回退方式。

## 目录结构

```text
final-exam-review/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── review-package-template.md
```

## 安装

将 `final-exam-review` 文件夹复制到 Codex skills 目录：

```bash
mkdir -p ~/.codex/skills
cp -R final-exam-review ~/.codex/skills/
```

也可以直接在支持 skills 的环境中引用本仓库里的 `final-exam-review/SKILL.md`。

## 使用示例

```text
Use $final-exam-review to turn my 数据结构 course materials into a final exam review package.
```

```text
使用 $final-exam-review，根据这些 PPT、PDF、作业题和往年题，帮我整理一份中文期末冲刺复习资料。
```

你可以提供：

- 课程名称或科目。
- 考试范围、章节或不考内容。
- PPT/PPTX、DOC/DOCX、PDF、Markdown、HTML、XLSX、ZIP、图片、链接或文件夹。
- 往年题、作业题、测验题、实验题或答案。
- 考试时间和特别担心的章节。

不需要提供目标分数。skill 默认目标是生成一份覆盖主要考试内容、适合冲刺复习的资料包。

## 输出内容

默认建议输出以下 Markdown 文件：

- `复习提纲.md`：章节化知识点、高亮重点、考点优先级和易错提醒。
- `章节题库.md`：每章判断题、经典例题、答案和解析。
- `模拟题.md`：多套模拟题、答案、评分要点和复盘定位。
- `资料处理日志.md`：资料转换状态、乱码或缺失处理、未覆盖内容。

## MarkItDown 策略

MarkItDown 是推荐路径，但不是硬依赖：

1. 如果本机有 MarkItDown 或 `$markitdown-convert` skill，优先转换资料为 Markdown。
2. 转换后必须抽查开头、中段和结尾，确认没有乱码、缺页、空内容、公式或表格严重缺失。
3. 如果转换结果不可靠，直接读取原文件，并记录回退方式。
4. 如果没有 MarkItDown，先询问用户是否下载安装，或跳过安装直接读取源文件。

## 适用场景

- 期末前需要快速整理复习资料。
- 课程资料很多，但缺少统一提纲。
- 想把 PPT、PDF、作业题和往年题合并成一份可直接背诵和刷题的资料。
- 希望 agent 在总结知识点后自动补充判断题、例题和模拟题。
