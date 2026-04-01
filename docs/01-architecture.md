# 01 - Architecture Overview

> Claude Code 架构概览

## 核心设计理念

Claude Code 不仅仅是一个 IDE 插件，它本质上是一个 **Agent Operating System**（Agent 操作系统）。

## 架构层次

```
┌─────────────────────────────────────┐
│         User Interface Layer        │
│    (Terminal UI / VS Code)          │
├─────────────────────────────────────┤
│       Agent Core Engine             │
│  (Query Engine / Tool Router)       │
├─────────────────────────────────────┤
│      Tool System (60+ Tools)        │
│   (Read/Write/Exec/Git/...)        │
├─────────────────────────────────────┤
│     Permission & Safety Layer       │
│    (Allow/Deny Rules)               │
├─────────────────────────────────────┤
│       Claude API Integration        │
│    (Streaming / Context Mgmt)       │
└─────────────────────────────────────┘
```

## 关键组件

### 1. 自定义 React Reconciler
- 不使用浏览器 DOM，而是渲染到终端
- 实现了响应式 UI 更新

### 2. 查询引擎
- 解析用户输入
- 路由到正确的工具或命令
- 处理多轮对话上下文

### 3. 工具系统
- 60+ 内置工具
- 可扩展架构
- 统一的工具接口

### 4. 权限系统
- 基于规则的访问控制
- 用户可配置的 allow/deny 列表
- 沙箱执行环境

## 设计特点

1. **模块化**: 每个组件独立，可单独测试和替换
2. **流式处理**: 实时响应 Claude API 流
3. **容错性**: 错误恢复机制贯穿整个架构
4. **可观测性**: 丰富的日志和状态监控

## 与传统 IDE 的区别

| 传统 IDE | Claude Code |
|---------|-------------|
| 工具驱动 | Agent 驱动 |
| 手动操作 | 自然语言指令 |
| 固定功能 | 可扩展工具集 |
| 单一上下文 | 多层次上下文管理 |

---

*Source: Sathwick's Claude Code Deep Dive*
