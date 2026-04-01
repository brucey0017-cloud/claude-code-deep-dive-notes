# 03 - Query Engine

> Claude Code 查询引擎

## 概述

查询引擎是 Claude Code 的核心组件，负责：
1. 解析用户输入
2. 理解意图
3. 路由到正确的工具
4. 管理对话上下文

## 查询处理流程

```
User Input
    │
    ▼
┌─────────────┐
│   Parser    │ ← 语法解析
└─────────────┘
    │
    ▼
┌─────────────┐
│  Intent     │ ← 意图识别
│  Classifier │
└─────────────┘
    │
    ▼
┌─────────────┐
│   Context   │ ← 上下文注入
│   Manager   │
└─────────────┘
    │
    ▼
┌─────────────┐
│    Tool     │ ← 工具选择
│   Router    │
└─────────────┘
    │
    ▼
┌─────────────┐
│  Executor   │ ← 执行 & 返回
└─────────────┘
```

## 意图分类

### 主要意图类型
- **FILE_OP**: 文件操作（读/写/编辑）
- **CODE_GEN**: 代码生成
- **EXEC**: 命令执行
- **SEARCH**: 搜索查询
- **ANALYSIS**: 代码分析
- **GIT**: Git 操作

## 上下文管理

### 上下文层次
1. **Session Context**: 当前会话状态
2. **Project Context**: 项目结构和配置
3. **File Context**: 相关文件内容
4. **History Context**: 历史对话记录

### 上下文压缩
- 滑动窗口策略
- 重要信息提取
- Token 预算管理

## 工具路由算法

```python
def select_tool(intent, context):
    candidates = filter_by_intent(tools, intent)
    ranked = rank_by_relevance(candidates, context)
    return top_k(ranked, k=3)
```

## 示例

**输入**: "修改 src/index.ts 的第 10 行"

**处理**:
1. Parser → 识别关键词："修改"、"src/index.ts"、"第 10 行"
2. Intent → FILE_OP + EDIT
3. Context → 加载文件内容
4. Router → 选择 `edit` 工具
5. Executor → 执行编辑操作

---

*Source: Sathwick's Claude Code Deep Dive*
